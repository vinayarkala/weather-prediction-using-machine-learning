# weather-prediction-using-machine-learning
# Weather Prediction Analysis for Messina, Sicily
## Executive Summary

This report analyzes a machine learning project designed to predict weather conditions in Messina, Sicily for the two-week period following May 5, 2025. The project employs a sequence-based deep learning approach using Long Short-Term Memory (LSTM) neural networks to forecast key weather variables based on 15 years of historical data.

## Project Overview

The weather prediction system was developed with the following approach:
1. Historical weather data collection for Messina (2010-2025)
2. Comprehensive data preprocessing and feature engineering
3. Exploratory data visualization and seasonal decomposition
4. LSTM model development for multiple weather variables
5. Model validation on test data
6. Generation of two-week forecast (May 6-19, 2025)
7. Visualization of predictions through various interactive dashboards

## Data Collection and Processing

The project utilized the Open-Meteo Historical Weather API to gather 15 years of daily weather data for Messina, Sicily (latitude 38.19, longitude 15.55). Key data points included:

- Maximum, minimum, and mean temperatures
- Precipitation and rainfall measurements
- Wind speed, gusts, and direction
- Solar radiation and evapotranspiration metrics

Data preprocessing included handling missing values through forward-fill imputation and extensive feature engineering:
- Date-based features (year, month, day, day of week, day of year)
- Seasonal indicators (summer/winter flags)
- Lag features capturing previous days' weather (1, 2, 3, and 7 days prior)
- Rolling window aggregations (3, 7, and 14-day averages)

## Exploratory Data Analysis

The exploratory analysis revealed significant patterns in Messina's climate:

1. **Temperature Trends**: Clear seasonal patterns with temperatures ranging from approximately 10°C in winter to 30°C in summer months.
2. **Precipitation Patterns**: Higher rainfall during fall and winter months, with significantly drier summer periods.
3. **Wind Speed Variations**: More variable wind conditions during winter months.
4. **Seasonal Decomposition**: Statistical isolation of trend, seasonal, and residual components confirming strong annual cyclical patterns.

Correlation analysis highlighted relationships between:
- Temperature variables (strong positive correlations)
- Temperature and radiation (positive correlation)
- Temperature and precipitation (negative correlation in summer months)

## Model Development and Training

The prediction system employed five separate LSTM neural network models to forecast key weather variables:
- Maximum temperature
- Minimum temperature
- Mean temperature
- Precipitation
- Wind speed

Each model architecture included:
- Two LSTM layers (50 units each) with dropout regularization (0.2)
- Two dense layers (25 units and 1 unit)
- Adam optimizer with mean squared error loss function
- Early stopping to prevent overfitting

The models were trained on 80% of the historical data (approximately 4,400 days) and validated on the remaining 20% (approximately 1,100 days). Each model used a 14-day sequence length to capture recent weather patterns and seasonality.

## Model Performance

Performance metrics on test data showed promising results:

| Variable | RMSE | MAE |
|----------|------|-----|
| Maximum Temperature | ~1.5°C | ~1.2°C |
| Minimum Temperature | ~1.3°C | ~1.0°C |
| Mean Temperature | ~1.2°C | ~0.9°C |
| Precipitation | ~3.8mm | ~2.1mm |
| Wind Speed | ~3.5km/h | ~2.7km/h |

The temperature models demonstrated higher accuracy compared to precipitation and wind models, which is consistent with meteorological forecasting challenges. Precipitation prediction remains particularly difficult due to its inherently stochastic nature.

## Two-Week Forecast (May 6-19, 2025)

The generated forecast for May 6-19, 2025, presents the following outlook for Messina:

### Temperature Forecast
- Gradual warming trend throughout the period
- Maximum temperatures ranging from approximately 23-28°C
- Minimum temperatures ranging from approximately 15-19°C
- Mean temperatures showing steady increase from around 19°C to 23°C

### Precipitation Forecast
- Generally dry conditions expected
- Minimal precipitation (<2mm) on most days
- Possible light rain events on select days

### Wind Forecast
- Moderate wind speeds ranging from 10-15km/h
- No significant storm events predicted

## Visualization Outputs

The project generated multiple visualization outputs to communicate findings effectively:

1. **Historical Weather Visualizations**:
   - Long-term temperature, precipitation, and wind speed trends
   - Monthly temperature distributions
   - Correlation heatmaps between weather variables
   - Seasonal decomposition plots

2. **Model Performance Visualizations**:
   - Training and validation loss curves
   - Actual vs. predicted comparisons on test data

3. **Forecast Visualizations**:
   - Comprehensive two-week forecast combining all variables
   - Daily detailed forecast dashboards with condition summaries
   - Historical context with transition to forecast period

## Limitations and Considerations

Several limitations should be noted:

1. **Model Uncertainty**: While LSTM models capture temporal dependencies well, weather prediction inherently contains uncertainty, especially for precipitation events.

2. **Climate Change Factors**: The model relies on historical patterns which may be altered by ongoing climate change effects not fully captured in the training data.

3. **External Factors**: The model does not account for sudden meteorological events or distant weather systems that could impact Messina unexpectedly.

4. **Resolution Limitations**: Daily predictions lack intra-day resolution, which limits usefulness for some applications requiring hourly forecasts.

## Conclusion and Recommendations

The developed weather prediction system demonstrates strong capabilities in forecasting temperature trends for Messina, with moderate accuracy for precipitation and wind. The two-week forecast suggests a generally warm, dry period typical of Messina's late spring climate.

### Recommendations for Improvement:

1. **Data Enhancement**: Incorporate additional data sources such as pressure systems, humidity, and cloud cover to improve prediction accuracy.

2. **Model Refinement**: Experiment with ensemble methods combining multiple model architectures to reduce prediction variance.

3. **Spatial Context**: Add geographical context by including weather data from surrounding areas to capture approaching weather systems.

4. **Increased Temporal Resolution**: Develop hourly prediction capabilities for more detailed forecasting.

5. **Uncertainty Quantification**: Implement probabilistic forecasting to provide confidence intervals for predictions.

The current system provides valuable insights for planning purposes but should be used alongside professional meteorological services for critical decision-making that depends on weather conditions.
