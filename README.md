# Dynamic Ride-Hailing Pricing in Chicago

This project investigates how trip characteristics, ride demand, location, and weather conditions affect ride-hailing fares in Chicago using 2025 Transportation Network Provider trip data.

---

## Project Overview

Ride-hailing fares can vary depending on when and where a trip occurs, how far the trip travels, local demand, and external conditions such as weather. This project uses 2025 ride-hailing data from the City of Chicago to explore these relationships and develop models for predicting fare variation. NOAA weather data will also be incorporated into later stages of the analysis.

Preliminary exploratory analysis shows that ride demand and average fares vary substantially throughout the day and across Chicago community areas. High-demand periods do not always correspond to the highest average fares, suggesting that other factors such as trip distance and duration also play an important role.

- **Objective:** Investigate how trip characteristics, demand, location, and weather conditions affect ride-hailing fares in Chicago.
- **Domain:** Transportation / Dynamic Pricing
- **Key Techniques:** Data cleaning, exploratory data analysis, geospatial visualization, statistical analysis, feature engineering, and predictive modeling.

---

## Project Structure

```text
├── data/                                      # Trip and geographic data
│   ├── parquet/                               # Monthly 2025 trip data in Parquet format
│   ├── processed/                             # Locally generated cleaned data
│   └── reference/                             # Chicago community area geographic data
├── code/                                      # Jupyter notebooks
│   ├── 01_data_ingestion.ipynb                # Data ingestion and CSV-to-Parquet conversion
│   ├── 02_data_cleaning.ipynb                 # Data cleaning and preparation
│   └── 03_eda.ipynb                           # Exploratory data analysis
├── reports/                                   # Generated reports and visualizations
├── requirements.txt                           # Dependencies
└── README.md                                  # Project documentation
```

---

## Data

- **Source:** City of Chicago Data Portal, Transportation Network Providers Trips 2025
- Source Link: [https://data.cityofchicago.org/Transportation/Transportation-Network-Providers-Trips-2025-/6dvr-xwnh/about_data](https://data.cityofchicago.org/Transportation/Transportation-Network-Providers-Trips-2025-/6dvr-xwnh/about_data)
- Analysis Period: 2025
- Clean Dataset: Approximately 55 million ride-hailing trips after data cleaning.
- **Description:** The main variables used in the analysis include:
  - trip_start_timestamp: trip pickup date and time
  - trip_seconds: trip duration in seconds
  - trip_miles: trip distance in miles
  - pickup_community_area: Chicago community area where the trip started
  - dropoff_community_area: Chicago community area where the trip ended
  - fare: base trip fare
  - tip: passenger tip
  - additional_charges: additional trip charges
  - trip_total: total trip cost

Chicago community area geographic boundary data is also used to visualize trip demand and average fares across the city's 77 community areas.

Weather data from the NOAA National Centers for Environmental Information will be incorporated during later stages of the project. Variables may include temperature, precipitation, and snow.

---

## Analysis

The main analysis is contained in:

`code/01_data_ingestion.ipynb`  
`code/02_data_cleaning.ipynb`  
`code/03_eda.ipynb`

Major steps completed so far include:

- Downloading and converting monthly Chicago ride-hailing data to Parquet format
- Converting variables to appropriate data types
- Handling missing fare and trip-duration observations
- Identifying missing pickup community areas using geographic data
- Representing drop-offs outside Chicago separately from Chicago community areas
- Comparing ride demand across Chicago community areas
- Comparing average fares across Chicago community areas
- Examining ride demand and average fare by hour of day
- Examining the relationship between trip distance and fare
- Comparing hourly trip demand with average fare
- Investigating fare distributions and potential outliers

Additional analysis will incorporate weather, calendar effects, and predictive modeling.

---

## Results

Preliminary exploratory analysis found that:

- Ride demand varies substantially throughout the day and is highest around the evening commute period.
- The highest average fares occur during early morning hours even though ride demand is relatively low.
- Early-morning trips tend to travel longer distances, suggesting that distance and duration may help explain the higher fares.
- Pickup demand varies substantially across Chicago community areas.
- O'Hare shows distinct demand and fare patterns compared with many other community areas.
- Trip distance has a clear positive relationship with fare.
- Hourly trip demand and average fare do not show a simple positive relationship.

These preliminary findings suggest that demand alone does not explain ride-hailing fare variation. Later analysis will control for trip characteristics, time, location, weather, and other relevant factors.

---

## Project Files

Data ingestion and conversion:

- [`code/01_data_ingestion.ipynb`](https://github.com/tphan356/chicago-rideshare-pricing/blob/main/code/01_data_ingestion.ipynb)

Data cleaning:

- [`code/02_data_cleaning.ipynb`](https://github.com/tphan356/chicago-rideshare-pricing/blob/main/code/02_data_cleaning.ipynb)

Exploratory data analysis:

- [`code/03_eda.ipynb`](https://github.com/tphan356/chicago-rideshare-pricing/blob/main/code/03_eda.ipynb)

---

## Authors

- Kelsie McCall
- William Dang
- Patrick Phan

---

## License

This project is developed for academic purposes. Source datasets remain subject to the terms and conditions of their respective data providers.

---

## Requirements

This project was developed in Python using Jupyter Notebook. The main libraries used are:

- DuckDB
- pandas
- NumPy
- Plotly
- Matplotlib
- GeoPandas
- scikit-learn

All required Python packages are listed in:

`requirements.txt`

---

## Acknowledgements

- City of Chicago Data Portal
- NOAA National Centers for Environmental Information (NCEI)
- Python
- DuckDB
- pandas
- NumPy
- Plotly
- Matplotlib
- GeoPandas
- scikit-learn
