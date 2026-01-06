## Introduction
To master time series prediction like an expert, you have to move beyond simple linear regression. 
You aren't just predicting $y$ based on $x$; 
you are predicting $y_{t+1}$ based on the historical patterns, seasonal pulses, and "shocks" found in $y_{t-n}$.

Here is the expert roadmap to mastering time series forecasting

1. Understand the DNA of the your data.Never skip **Exploratory Data Analysis (EDA)**
2. Stationarity: Most statistical models require the data to be stationary (mean, variance, and covariance are constant over time).
     If your data has a trend, it’s non-stationary. Tool: Use the **Augmented Dickey-Fuller (ADF)** test.
     If $p > 0.05$, you likely need to "difference" your data (subtracting the previous value from the current one).
3. Autocorrelation (ACF) and Partial Autocorrelation (PACF): These plots tell you how much today’s value correlates with yesterday’s, or the day's before that.This helps you determine the **"lags"** to include in your model.


### Classical toolkits 

|Model	 | Best Use Case
---------|----------------
|ARIMA (*AutoRegressive (AR) Integrated (I) Moving Average (MA)*)	| Univariate data with a clear trend but no strong seasonality
SARIMA	|Adds a "Seasonal" component to ARIMA (e.g., monthly sales spikes).
Exponential Smoothing (ETS)|	Great for data where recent observations are more weighted than older ones.
Prophet (Meta)|	Handles holidays, outliers, and missing data beautifully. Very "plug-and-play."


### The Modern Approach: Machine Learning & Deep Learning

1. Tree-Based Models (XGBoost/LightGBM): You must "featurize" the time (e.g., creating columns for day_of_week, is_holiday, rolling_mean_7d).
2. Recurrent Neural Networks (LSTM/GRU): Designed to "remember" long-term dependencies in sequences.
3. Transformers (N-BEATS, TFT): The current state-of-the-art. They use attention mechanisms to look at different parts of the past simultaneously.

#### The Expert's "Secret Sauce": Validation
In time series, this is a cardinal sin. You cannot use the future to predict the past.

Time Series Split (Backtesting): You must use a "sliding window" or "expanding window" approach. You train on January, test on February. Then train on January–February, test on March.

Evaluation Metrics:
- MAE: Mean Absolute Error (easy to explain).

- RMSE: Penalizes large outliers more heavily.

- sMAPE: Symmetric Mean Absolute Percentage Error (useful when dealing with different scales).


In this Project, lets try to be creative with various models 
