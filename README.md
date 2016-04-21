# rfq-sql


CREATE VIEW 
v1_machine_rate
AS
SELECT
id,
 `category`,`item_seq`,`machine_model`,


`day_capacity`,

ROUND(`day_capacity`/22) `hr_capacity` ,
`machine_cost`,

ROUND(`machine_cost`*0.3) yr_depreciation_interest,
ROUND(`machine_cost`*0.3/12/22) day_depreciation_interest,


`utilization_rate`,
ROUND(`machine_cost`*0.3/12/22/22/ utilization_rate) machine_fee,

`square_meter`,
ROUND(  `square_meter`*20/22/22)  site_fee,




`avg_product`,
`energy_consumption` energy_fee

 FROM `machine_rate` 









CREATE VIEW 
v2_machine_rate
AS
SELECT 
`id`,
`category`,
`item_seq`,
`machine_model`,
`machine_fee`+`site_fee`+ energy_fee machine_rate,
ROUND((`machine_fee`+`site_fee`+ energy_fee)/`hr_capacity`,1) shot_rate,
`day_capacity`,
`hr_capacity`,
`machine_cost`,
`yr_depreciation_interest`,
`day_depreciation_interest`,
`utilization_rate`,

`machine_fee`,
`square_meter`,
`site_fee`,
`avg_product`,
 energy_fee


 FROM `v1_machine_rate`

 WHERE 1
