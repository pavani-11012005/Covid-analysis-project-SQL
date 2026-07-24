# COVID-19 Data Exploration (SQL)

## 📌 Overview
This project explores global COVID-19 case, death, and vaccination data using **SQL Server (T-SQL)**. The goal is to uncover trends in infection rates, mortality, and vaccination rollout across countries and continents.

## 🗂️ Dataset Summary
- **Source:** Public COVID-19 dataset (Our World in Data)
- **Tables used:**
  - `CovidDeaths` – case counts, death counts, population, and demographic/health indicators by country and date
  - `CovidVaccinations` – testing and vaccination data by country and date
- **Records:** ~85,000 rows per table, covering 219 countries/locations from January 2020 to April 2021

## 🛠️ Tech Stack
- **SQL Server / T-SQL** – all data exploration and transformation
- **Excel** – raw source data (`CovidDeaths.xlsx`, `CovidVaccinations.xlsx`)

## 🔍 Skills Demonstrated
- Joins (multi-table joins on location + date)
- Common Table Expressions (CTEs)
- Temp Tables
- Window Functions (`SUM() OVER (PARTITION BY ... ORDER BY ...)`)
- Aggregate Functions (`MAX`, `SUM`)
- Data type conversion (`CONVERT`, `CAST`)
- Creating Views

## 🔄 Analysis Workflow
1. **Initial Data Exploration** – Reviewed `CovidDeaths` table structure, filtering out rows with null continent values to keep country-level analysis clean.
2. **Total Cases vs. Total Deaths** – Calculated a `DeathPercentage` metric to estimate the likelihood of dying if infected with COVID-19 in a given country.
3. **Total Cases vs. Population** – Calculated `PercentPopulationInfected` to understand what share of each country's population had been infected over time.
4. **Highest Infection Rate by Country** – Identified countries with the highest infection rate relative to population size, using `MAX()` and `GROUP BY`.
5. **Highest Death Count by Country & Continent** – Aggregated total death counts at both the country and continent level to identify the hardest-hit regions.
6. **Global Numbers** – Calculated global totals for cases and deaths, and an overall global death percentage.
7. **Population vs. Vaccinations (Rolling Count)** – Joined `CovidDeaths` and `CovidVaccinations` on location and date, then used a window function to calculate a rolling count of people vaccinated per country over time.
8. **CTE for Rolling Calculations** – Used a CTE (`PopvsVac`) to perform percentage calculations on top of the window function output.
9. **Temp Table Alternative** – Recreated the rolling vaccination logic using a temporary table (`#PercentPopulationVaccinated`) as an alternative approach.
10. **View Creation** – Created a SQL View (`PercentPopulationVaccinated`) to persist the final query logic for reuse.

## 📊 Key Findings
- Global COVID-19 death rate: **2.11%** across 150M+ recorded cases
- Highest infection rate relative to population: **Andorra, Montenegro, Czechia** (15–17% of population infected)
- Highest total death counts: **United States (576K), Brazil (404K), Mexico (217K)**
- Fastest vaccine rollout relative to population: **Gibraltar, Israel, UAE**

## 📁 Repository Structure
├── COVID_Portfolio_Project_-_Data_Exploration.sql   # All SQL queries
├── CovidDeaths.xlsx                                  # Raw cases/deaths dataset
├── CovidVaccinations.xlsx                             # Raw vaccinations dataset
└── README.md

## 🚀 Key Takeaways
- Death and infection rates vary significantly by country, driven by differences in population, healthcare capacity, and reporting practices.
- Rolling vaccination totals (via window functions) provide a clearer picture of vaccine rollout speed than single-day snapshots.
- Structuring queries with CTEs, temp tables, and views makes complex multi-step calculations reusable for future analysis.

## 👤 Author
**Panga Pavani**
