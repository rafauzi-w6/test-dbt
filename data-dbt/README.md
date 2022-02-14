## Waresix dbt project: `data_dbt`

`data_dbt` is dbt project transforms raw data direct to datawarehouse.


## DBT

**[dbt](https://www.getdbt.com/)** enables data analysts and engineers to transform their data using the same practices that software engineers use to build applications.

![architecture](https://raw.githubusercontent.com/dbt-labs/dbt-core/6c6649f9129d5d108aa3b0526f634cd8f3a9d1ed/etc/dbt-arch.png)

## Understanding dbt

Analysts using dbt can transform their data by simply writing select statements, while dbt handles turning these statements into tables and views in a data warehouse.

These select statements, or "models", form a dbt project. Models frequently build on top of one another – dbt makes it easy to [manage relationships](https://docs.getdbt.com/docs/ref) between models, and [visualize these relationships](https://docs.getdbt.com/docs/documentation), as well as assure the quality of your transformations through [testing](https://docs.getdbt.com/docs/testing).



## Getting started

- [Install dbt](https://docs.getdbt.com/docs/installation)
```
pip install dbt
```
- Clone repository https://github.com/waresix/data-dbt
```
git clone https://github.com/waresix/data-dbt
```
- Add your profile.yml to data-dbt directory
```
waresix_dbt:  # this needs to match the profile: in your dbt_project.yml file
  target: dev
  outputs:
    dev:
      type: postgres
      host: "{{ env_var('HOST_DWH') }}"
      user: "{{ env_var('USER_DWH') }}"
      pass: "{{ env_var('PASS_DWH') }}"
      port: 54324
      dbname: pg_raw 
      schema: dbt_dev
      threads: 1
      keepalives_idle: 0
    prod:
      type: postgres
      host: "{{ env_var('HOST_DWH') }}"
      user: "{{ env_var('USER_DWH') }}"
      pass: "{{ env_var('PASS_DWH') }}"
      port: 54324
      dbname: pg_gold 
      schema: dbt_prod
      threads: 1
      keepalives_idle: 0
```
- Run
```
dbt run --profiles-dir /{Project_Path}/data-dbt  --target dev --models tag:{tag_name}
```
- Test
```
dbt test --profiles-dir /{Project_Path}/data-dbt  --target dev --models tag:{tag_name}
```

## Join the dbt Community

- Be part of the conversation in the [dbt Community Slack](http://community.getdbt.com/)
- Read more on the [dbt Community Discourse](https://discourse.getdbt.com)

## Reporting bugs and contributing code

- Want to report a bug or request a feature? Let us know on [Slack](http://community.getdbt.com/), or open [an issue](https://github.com/dbt-labs/dbt-core/issues/new)
- Want to help us build dbt? Check out the [Contributing Guide](https://github.com/dbt-labs/dbt-core/blob/HEAD/CONTRIBUTING.md)

## Code of Conduct

Everyone interacting in the dbt project's codebases, issue trackers, chat rooms, and mailing lists is expected to follow the [dbt Code of Conduct](https://community.getdbt.com/code-of-conduct).