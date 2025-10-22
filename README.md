# F1 Race Performance Analysis (2021–2024)

This project analyzes the relationship between **qualifying positions** and **final race results** in Formula 1 seasons (2021–2024).  

It explores what are factors, also why & how influence drivers' performance。

The next step I will build predictive models to forecast race outcomes.

---

## Project Overview

**Data Sources:**  
- Kaggle Formula 1 Dataset (https://www.kaggle.com/datasets/rohanrao/formula-1-world-championship-1950-2020/data)
- Includes data on races, results, qualifying sessions, drivers, constructors, and status codes.

---

## Methods & Techniques

**Data Pipeline (SQLite):**

- Instead of in-memory processing with pandas, this project uses a database-first approach for efficiency and scalability:

1. Load: All raw CSV files from the F1dataset directory are loaded into a local SQLite database (f1_project.db) using a Python script (with glob, os, and pandas.to_sql).

2. Transform: A single, comprehensive SQL script (create_tables_script) is executed. This script Joins six core tables (races, results, drivers, constructors, qualifying, status).

Materializes this joined data into a new, clean "master" table (master_analysis_data).

Creates a second, pre-filtered table (master_finished_analysis_data) for easier analysis.

3. Analyze: The main Jupyter Notebook (F1_Analysis.ipynb) now reads directly from this clean, pre-processed database using pandas.read_sql_query.

**Exploratory Data Analysis (EDA):**

- Visualized correlations and distributions using matplotlib and seaborn.

- Analyzed position changes (grid - racePosition), incident frequencies, and performance by circuit type.

---

## Key Findings

- A strong positive correlation exists between qualifying position and race finish position.

- Most drivers finish close to their starting position. The median position change is slightly positive (+1.00), suggesting a tendency for drivers to gain positions.

- High-speed circuits (e.g., Monza) show a slightly higher average position gain than medium or low-speed circuits.

- Certain drivers and circuits show a significantly higher frequency of incidents (Accidents, Collisions, etc.).

---

## Tech Stack

- **Languages**: Python, SQL

- **Data Stack**: Pandas, NumPy, SQLite

- **Visualization**: Matplotlib, Seaborn

- **Modeling** (WIP): Scikit-learn

- **Tools**: Jupyter Notebook, Git, GitHub, SQLite Database

---

## Author

**Yicong Yang**  
Undergraduate Student in Computer Science @ University of Virginia  
Email address: sekiroy21@gmail.com

---
