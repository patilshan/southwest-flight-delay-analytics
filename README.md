# ✈️ Southwest Airlines Flight Delay Analytics

> Analyzing Southwest Airlines' on-time performance vs. industry peers using Google BigQuery for cloud data warehousing, Python for statistical analysis, and Looker Studio for interactive dashboards.

<p align="left">
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/BigQuery-4285F4?style=flat-square&logo=googlebigquery&logoColor=white" alt="BigQuery"/>
  <img src="https://img.shields.io/badge/Looker%20Studio-4285F4?style=flat-square&logo=google&logoColor=white" alt="Looker Studio"/>
  <img src="https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white" alt="Pandas"/>
  <img src="https://img.shields.io/badge/dbt-FF694B?style=flat-square&logo=dbt&logoColor=white" alt="dbt"/>
  <img src="https://img.shields.io/badge/GCP-4285F4?style=flat-square&logo=googlecloud&logoColor=white" alt="GCP"/>
</p>

---

## Problem

Airlines face significant costs from flight delays — both operationally and in customer satisfaction. This project investigates Southwest Airlines' delay patterns compared to the rest of the industry to answer: How often is Southwest delayed? How much time does Southwest recover in-flight? What proportion of delays are within Southwest's control?

## Data & Infrastructure

- **Source**: US flight operations data loaded into **Google BigQuery**
- **Data pipeline**: Transformed using **dbt** (data build tool) with a final table at `msba-test-1.dbt_spatil.flights_final`
- **Analysis**: Python notebook querying BigQuery directly via `%%bigquery` magic
- **Dashboard**: Interactive visualizations built in **Google Looker Studio**

## Approach

- Queried the full flights dataset from BigQuery into a Pandas DataFrame
- Segmented data into Southwest Airlines vs. all other carriers
- Computed key delay metrics:
  - Percentage of Southwest flights with arrival delay ≥ 15 minutes
  - Average arrival delay for Southwest vs. industry
  - Proportion of delays within Southwest's control (carrier-caused)
  - Average time Southwest recovers in-flight (departure delay minus arrival delay)
  - Estimated cost savings from in-flight time recovery
- Built a Looker Studio dashboard for interactive exploration of delay trends

## Key Results

| Metric | Value |
|---|---|
| **Southwest flights delayed ≥ 15 min** | 42.8% |
| **Southwest flights on-time or minor delay** | 57.2% |
| **Average in-flight time recovery** | 3.63 minutes per flight |
| **Comparison** | Southwest's average arrival delay benchmarked against all other carriers |
| **Controllable delays** | Identified the share of delays caused by carrier operations vs. external factors |

## How to Run

```bash
# Clone the repo
git clone https://github.com/patilshan/southwest-flight-delay-analytics.git
cd southwest-flight-delay-analytics

# The notebook requires Google Cloud access with BigQuery
# Install dependencies
pip install pandas google-cloud-bigquery jupyter

# Launch the notebook
jupyter notebook Cloud_Project.ipynb

# Note: Requires GCP project credentials and access to the BigQuery dataset
```

## Project Structure

```
├── Cloud_Project.ipynb       # Python analysis notebook (queries BigQuery)
├── flights_project.pdf       # Looker Studio dashboard snapshot
└── README.md
```

## Architecture

```
Raw Flight Data → BigQuery (warehouse) → dbt (transformation) → Python (analysis) → Looker Studio (dashboard)
```

## What I Learned

- How to build an end-to-end cloud analytics pipeline using GCP services (BigQuery + Looker Studio)
- Using dbt for data transformation and modeling inside the warehouse before analysis
- Querying BigQuery directly from Jupyter notebooks for seamless cloud-to-notebook workflows
- Translating raw delay metrics into business-relevant insights (cost of recovered time at $80.2/minute)

---

<p align="center">
  <a href="https://github.com/patilshan">← Back to profile</a>
</p>
