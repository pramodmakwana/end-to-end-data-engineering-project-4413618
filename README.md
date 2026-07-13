# Ecommerce ELT Pipeline — Airbyte, dbt, Dagster

An end-to-end ELT (Extract, Load, Transform) pipeline that ingests raw ecommerce data, loads it into a cloud data warehouse, transforms it into analytics-ready models, and orchestrates the whole workflow — built using the modern open-source data stack.

## What this project does

1. **Extract & Load** — [Airbyte](https://airbyte.com/) pulls raw ecommerce data and loads it into cloud storage
2. **Store** — Data lands in **Google Cloud Storage** and is loaded into **BigQuery** as the analytics warehouse
3. **Transform** — [dbt](https://www.getdbt.com/) models raw tables into clean, tested, analytics-ready tables (staging → intermediate → marts)
4. **Orchestrate** — [Dagster](https://dagster.io/) schedules and monitors the pipeline end to end, so each stage runs in the right order and failures are visible

```
Raw Ecommerce Data → Airbyte (Extract & Load) → GCS / BigQuery → dbt (Transform) → Analytics-Ready Tables
                                                                        ↑
                                                              Orchestrated by Dagster
```

## What I actually built and debugged

This project is based on the LinkedIn Learning course *"End-to-End Data Engineering Project"* by Thalia Barrera, which I used as a structured starting point to learn the modern data stack hands-on. On top of following the course, I:

- Set up and troubleshot a **local Airbyte deployment via `abctl`** on Windows — including resolving connection and container startup issues not covered in the course walkthrough
- Configured **GCP service account authentication** to connect Airbyte to Google Cloud Storage and BigQuery
- Ran the full pipeline end-to-end locally and validated data landing correctly at each stage (raw → warehouse → transformed models)
- Reviewed and adapted the dbt models and Dagster orchestration jobs to understand how each layer of the stack fits together

## Tech stack

| Layer | Tool |
|---|---|
| Ingestion | Airbyte |
| Storage / Warehouse | Google Cloud Storage, BigQuery |
| Transformation | dbt |
| Orchestration | Dagster |
| Language | Python |

## Why I built this

I come from a financial-services data analytics background (SQL, Python, reporting) and wanted hands-on experience with the tools that sit "upstream" of analytics — ingestion, warehousing, and orchestration — to move toward data engineering. This project was my way of getting real, working experience with Airbyte, dbt, and Dagster rather than just reading about them.

## Next steps

- [ ] Swap in a real public dataset (e.g. a financial/investment dataset) in place of the course's sample ecommerce data
- [ ] Add custom dbt models and data-quality tests (`unique`, `not_null`, `relationships`)
- [ ] Add a simple architecture diagram
- [ ] Deploy the pipeline to run on a schedule in the cloud rather than locally

## Credit

Original course structure and starter code: [LinkedIn Learning — End-to-End Data Engineering Project](https://www.linkedin.com/learning/end-to-end-data-engineering-project) by Thalia Barrera.

