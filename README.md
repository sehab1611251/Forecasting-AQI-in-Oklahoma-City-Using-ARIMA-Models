# Forecasting Air Quality Index (AQI) in Oklahoma City

This project forecasts the Air Quality Index (AQI) in Oklahoma City using ARIMA models. By analyzing historical AQI data alongside meteorological variables (e.g., temperature, precipitation, wind speed, humidity), the study explores the relationships between air quality and weather conditions. The workflow includes data preprocessing, exploratory data analysis (EDA), ARIMA model development, and forecasting evaluation.

## Datasets

- **Air Quality Data**  
  [Download Daily Air Quality Data](https://www.epa.gov/outdoor-air-quality-data/download-daily-data)

- **Meteorological Data**  
  [Download Weather Data](https://www.visualcrossing.com/weather/weather-data-services)

## Workflow Summary

1. **Data Loading and Preprocessing**
   - Load and merge air quality and meteorological datasets by date.
   - Standardize date formats, remove missing values, and adjust AQI values (increment by 1) to enable the Box-Cox transformation.
   - Apply Box-Cox (and log for the Near Road site) transformation to stabilize variance.

2. **Exploratory Data Analysis (EDA)**
   - Create line plots to visualize trends in AQI and meteorological variables.
   - Compute a 30-day rolling mean and variance to assess stationarity.
   - Calculate correlation coefficients to explore relationships between AQI and weather factors.

3. **Time Series Decomposition and ARIMA Modeling**
   - Decompose the AQI time series using STL (Seasonal-Trend Decomposition using Loess) to extract trend, seasonal, and residual components.
   - Analyze ACF/PACF plots to guide ARIMA model order selection.
   - Fit candidate ARIMA models (ARIMA(1,0,1), ARIMA(0,0,1), ARIMA(1,0,0)) with meteorological variables as exogenous regressors.
   - Select the ARIMA(0,0,1) model based on AIC, BIC, and residual diagnostics (Ljung-Box test).

4. **Forecasting and Evaluation**
   - Generate forecasts for 7, 15, and 30-day horizons with 95% confidence intervals.
   - Evaluate forecast performance using MAE and RMSE metrics.
   - Visualize actual versus forecasted AQI values to assess model accuracy.

## Key Insights and Future Work

- **Model Performance:** The ARIMA(0,0,1) model provided robust forecasts with acceptable error metrics.
- **Feature Insights:** While meteorological variables improve forecasting, additional factors (e.g., traffic or industrial emissions) could further enhance model performance.
- **Future Directions:** Explore advanced time series techniques or machine learning methods to further improve forecast accuracy.

