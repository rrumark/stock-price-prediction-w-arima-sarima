# "Stock Price Prediction Using Time Series Analysis
![image](https://github.com/user-attachments/assets/ebfd3751-b79f-4296-90fa-c10565e46022)

This project includes code for forecasting stock prices using several time series models. It utilizes historical stock data from NSE-TATAGLOBAL for analysis. The project covers steps such as data preprocessing, checking for stationarity, and implementing various forecasting techniques, including Moving Average, ARIMA, and SARIMA models.

## Data Import and Preprocessing

1. Import Dataset

```python
data = pd.read_csv(r'C:\Users\admin\Downloads\NSE-TATAGLOBAL.csv')
```
2. Convert Date Column and Reverse Data
```python
data['Date'] = pd.to_datetime(data.Date, format='%Y-%m-%d')
data = data.iloc[::-1]
```
3. Set Date Column as Index
```python
data.set_index('Date', inplace=True)
```
## Stationarity Check
The stationarity of the time series is evaluated using the Augmented Dickey-Fuller (ADF) test. To achieve stationarity, the series undergoes a logarithmic transformation followed by differencing.
```python
def test_stationarity(timeseries):
    # Transformation to make the data stationary
    timeseries_log = np.log(timeseries)
    timeseries_log_diff = timeseries_log.diff().dropna()
    
    # Plot rolling statistics and perform ADF test
    ...
```
## Model Fitting
### Moving Average
This part utilizes the moving average technique for making predictions. The model's effectiveness is assessed by calculating the Root Mean Squared Error (RMSE)
```python
def moving_avg_prediction(data):
    ...
```
### ARIMA
Auto ARIMA is used for forecasting stock prices. The model automatically selects the best parameters for ARIMA.
```python
def arima_prediction(data):
    ...
```
### SARIMA
The Seasonal ARIMA (SARIMA) model is used to capture seasonality in the time series. The model is fitted with parameters for both non-seasonal and seasonal components.
```python
def sarima_prediction(data):
    ...
```
## Usage
1. Load Data 
```python
data = pd.read_csv('your_data.csv', parse_dates=True, index_col='Date')
```
2. Run Forecasting Models
```python
moving_avg_prediction(data)
arima_prediction(data)
sarima_prediction(data)
```