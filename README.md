# 🧠 Parametric ETL Prototype — NiFi + PySpark Medallion Architecture

This project demonstrates an end-to-end **ETL pipeline** using **Apache NiFi** for orchestration and **PySpark** for data transformation — designed around the **Medallion Architecture (Bronze → Silver → Gold)**.  
It was built as part of a data engineering learning project for **Parametric’s Data Management pipeline** simulation.

---

## 🌍 Architecture Overview

<p align="center">
  <img src="nifi/nifi_flow_screenshot.png" alt="NiFi Flow" width="850">
</p>

The pipeline automates ingestion, cleansing, transformation, and aggregation of financial data.  
It replicates how modern data engineering teams process and refine datasets for analytics and machine learning.

---

## 🧩 Key Components

| Layer | Tool | Purpose |
|:------|:-----|:--------|
| **Bronze** | Apache NiFi | Ingests raw `.csv` data (Holdings, Prices, Reference Tickers) from `data/raw/` |
| **Silver** | PySpark | Cleanses, validates, and standardizes the data (`02_silver_spark.py`) |
| **Gold** | PySpark | Aggregates and produces analytics-ready datasets (`03_gold_sql.py`) |
| **Storage** | Local Parquet files | Stored in `data/silver/` and `data/gold/` |
| **Orchestration** | NiFi | Automates the entire data flow using `ExecuteStreamCommand` & `PutFile` |

---

## 📂 Project Structure
Parametric_ETL_Prototype/
│
├── src/
│ ├── 02_silver_spark.py # Cleans and transforms to Silver
│ ├── 03_gold_sql.py # Aggregates to Gold
│
├── data/
│ ├── raw/
│ │ ├── holdings_seed.csv
│ │ ├── prices_seed.csv
│ │ └── reference_tickers_seed.csv
│
├── nifi/
│ ├── nifi_flow_screenshot.png # NiFi pipeline canvas
│
├── requirements.txt
├── .gitignore
└── README.md

🧠 Concepts Demonstrated

Medallion architecture (Bronze/Silver/Gold)

ETL orchestration using NiFi

PySpark transformations (schema casting, null handling)

Aggregations with Spark SQL

File-based data pipelines

Data quality enforcement (valid vs invalid holdings)

Reproducibility with virtual environments

🧱 Future Improvements

Integrate Delta Lake for versioned tables

Add AWS S3 layer for cloud-based ingestion

Include Airflow DAG orchestration alternative

Automate NiFi template deployment using API
