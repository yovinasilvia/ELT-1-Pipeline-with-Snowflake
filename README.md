# Building an ELT Pipeline: Integrating Snowflake, DBT, and Airflow for Data Transformation

## The tools used in the ELT pipeline process are:
* Snowflake: Used as both the data source and the data warehouse. It handles the storage and initial loading of data.
* Airflow: Used for orchestration and automation of the ELT workflow, managing the scheduling and execution of tasks in the pipeline.
* DBT (Data Build Tool): Used for data transformation, cleaning, and modeling. It transforms raw data in the data warehouse into a format ready for analysis.

## Step 1: Set Up Environment in Snowflake
### Set the Role to ACCOUNTADMIN:
```
use role accountadmin;
```
This sets the role used to ACCOUNTADMIN, which is the role with the highest level of access in Snowflake.
### Create the Warehouse:
```
create warehouse if not exists dbt_wh with warehouse_size='x-small'; 
```
Creates a warehouse named dbt_wh with an x-small size if it does not already exist.
### Create the Database:
```
create database if not exists dbt_db;
```
### Create the Role:
```
create role if not exists dbt_role;
```
Creates a role named dbt_role if it does not already exist. The role is used to manage user access permissions in Snowflake.
### Show Grants on the Warehouse:
```
show grants on warehouse dbt_wh;
```
This helps verify who has access to the dbt_wh warehouse.
### Grant Usage Rights on the Warehouse to the Role:
```
grant usage on warehouse dbt_wh to role dbt_role;
```
Grants usage rights for the dbt_wh warehouse to the dbt_role role.
### Grant the Role to the User:
```
grant role dbt_role to user "yovinasilvia";
```
Grants the dbt_role role to the user named yovinasilvia.
### Grant All Permissions on the Database to the Role:
```
grant all on database dbt_db to role dbt_role;
```
Grants all permissions on the dbt_db database (such as SELECT, INSERT, UPDATE, DELETE) to the dbt_role role.
### Change the Current Role to dbt_role:
```
use role dbt_role;
```
Changes the current role to dbt_role, so that subsequent commands are executed with the permissions granted to this role.
### Create the Schema:
```
create schema dbt_db.dbt_schema;
```
Creates a schema named dbt_schema within the dbt_db database. The schema is used to organize tables and other objects within the database.
### The display and result in Snowflake are as follows:
![setup-env-in-snowflake](documentations/setup-env-in-snowflake.png)






