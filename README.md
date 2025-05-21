# Fake Store API ETL Pipeline with Microsoft Fabric

---

## Overview

This project demonstrates an end-to-end ETL pipeline built in **Microsoft Fabric**, using the **Fake Store API** as the data source. The architecture follows a modern data engineering pattern: **Landing → Staging → Presentation**, using Fabric components like **Notebooks, Pipelines, Lakehouse, Warehouse**, and **Dataflows**.

The main objective is to showcase Fabric’s capability to ingest API data, transform it into curated tables, and prepare it for downstream reporting via Power BI.

---

## Architecture

![Architecture Diagram](link_to_your_image_if_any)

---

## Components

### 1. Fake Store API

- **Source**: [https://fakestoreapi.com](https://fakestoreapi.com)
- **Entities**: Products, users, carts, categories, etc.
- **Format**: JSON

---

### 2. Landing Layer – Lakehouse (JSON Files)

- **Tool**: Microsoft Fabric Notebook (PySpark)
- **Functionality**:
  - Extracts data from the Fake Store API
  - Stores raw JSON into Lakehouse `/Files/landing/` folder
  - Organized by entity (e.g., `products`, `users`, `carts`)

---

### 3. Staging Layer – Fabric Warehouse

- **Tool**: Data Pipeline (Set Variable → Copy Data → Stored Procedure)
- **Functionality**:
  - Reads JSON files from Lakehouse
  - Transforms and cleans data using SQL
  - Loads structured tables into the staging schema in Fabric Warehouse

---

### 4. Presentation Layer – Fabric Warehouse

- **Tool**: Dataflow Gen2 (triggered in a Data Pipeline)
- **Functionality**:
  - Applies business rules (e.g., calculated columns, joins)
  - Loads final curated tables into the presentation schema in the same warehouse
  - Optimized for reporting and semantic model creation

---

## Key Features

- API ingestion using notebooks
- Pipeline-based transformation with reusable logic
- Layered architecture: Landing, Staging, and Presentation
- Integration-ready with Power BI semantic models
- Fully built within Microsoft Fabric

---

## Future Enhancements

- Create a Semantic Model connected to the presentation layer
- Build Power BI dashboards using a shared dataset
- Add monitoring/alerting for pipeline failures
- Automate daily refresh with recurrence triggers


---

## License

This project uses public data from [Fake Store API](https://fakestoreapi.com) and is intended for educational and demonstration purposes only.

