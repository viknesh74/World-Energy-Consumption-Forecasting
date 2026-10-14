# World Energy Consumption Forecasting Using LSTM

## 1. Project Overview

World Energy Consumption Forecasting is a machine learning project that predicts a country's future energy consumption using historical energy data. The project uses a Long Short-Term Memory (LSTM) neural network to learn patterns from previous years and forecast the following year's energy consumption.

The project is implemented using Python in Google Colab.

## 2. Problem Statement

An energy research organisation wants to predict a country's future energy consumption using historical data. The World Energy Consumption dataset is used to select a country with sufficient yearly records, preprocess the data, create time-series sequences, train a recurrent neural network, and evaluate its forecasting performance.

## 3. Objectives

- Load and explore the World Energy Consumption dataset.
- Select a country with sufficient historical records.
- Handle missing values and duplicate records.
- Normalize the numerical energy-consumption data.
- Sort observations chronologically.
- Create sequences using the previous five years to predict the next year.
- Build and train an LSTM model using TensorFlow/Keras.
- Evaluate the model using Mean Absolute Error (MAE) and Root Mean Squared Error (RMSE).
- Visualize actual and predicted energy consumption.

## 4. Dataset

**Dataset Name:** World Energy Consumption

**Source:** Kaggle

**Dataset URL:** https://www.kaggle.com/datasets/patricklford/world-energy-consumption

**Selected Country:** United States

**Target Variable:** `primary_energy_consumption`

**Time Period:** Based on the available yearly records for the selected country.

The dataset contains historical energy-related information for countries and regions. The selected country's annual energy-consumption records are used for forecasting.

## 5. Technologies Used

- Python
- Google Colab
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- TensorFlow
- Keras

## 6. Methodology

### Step 1: Load the Dataset

The CSV dataset is uploaded to Google Colab and loaded using Pandas.

### Step 2: Data Preprocessing

- Select the United States from the dataset.
- Convert the year and energy-consumption columns to numeric values.
- Remove records with missing target values or years.
- Handle duplicate yearly records.
- Sort the records chronologically.
- Check for gaps between consecutive years.

### Step 3: Data Normalization

MinMaxScaler is used to scale energy-consumption values to a range between 0 and 1. The scaler is fitted only on the training period to prevent data leakage.

### Step 4: Sequence Creation

A sliding window of five consecutive years is created. The previous five years form the input, and the following year is the prediction target.

Example:

| Input Years | Target Year |
|---|---|
| 2015–2019 | 2020 |
| 2016–2020 | 2021 |
| 2017–2021 | 2022 |
| 2018–2022 | 2023 |

The actual sequences depend on the available records in the dataset.

### Step 5: Train-Test Split

The observations are divided chronologically:

- Training set: approximately 80% of the observations.
- Testing set: approximately 20% of the observations.

The records are not randomly shuffled because the order of years is important in time-series forecasting.

### Step 6: LSTM Model Implementation

An LSTM model is developed using TensorFlow/Keras.

The model consists of:

- Input layer with five time steps.
- LSTM layer with 32 units.
- Dense hidden layer with 16 units and ReLU activation.
- Output Dense layer with one unit.

The Adam optimizer is used, and mean squared error is used as the training loss function.

### Step 7: Model Training

The model is trained using historical sequences. Early stopping is used to monitor validation loss and reduce overfitting.

### Step 8: Model Evaluation

The model's predictions are converted back to the original energy-consumption scale. Performance is evaluated using MAE and RMSE.

### Step 9: Visualization

Graphs are generated to compare actual and predicted energy consumption and to show training and validation loss.

### Step 10: Future Forecasting

The last five consecutive annual observations are provided to the trained model to estimate energy consumption for the next year.

## 7. Why LSTM?

LSTM (Long Short-Term Memory) is a type of recurrent neural network designed to learn dependencies in sequential data. It is suitable for experimenting with energy-consumption forecasting because historical observations may contain trends and temporal relationships.

A relatively small LSTM network is used because annual datasets often contain fewer training examples than daily or hourly datasets. Its performance should be compared with a simple baseline to determine whether it provides useful forecasting accuracy.

## 8. Evaluation Metrics

### Mean Absolute Error (MAE)

MAE measures the average absolute difference between actual and predicted energy consumption.

MAE = Mean of |Actual − Predicted|

### Root Mean Squared Error (RMSE)

RMSE measures prediction error while penalizing larger errors more heavily.

RMSE = Square root of the mean of (Actual − Predicted)²

Lower MAE and RMSE values generally indicate better predictions. Both metrics are calculated in the original target variable's units.

## 9. Expected Outputs

The project produces:

- Dataset summary and missing-value report.
- Historical energy-consumption graph.
- Trained LSTM model.
- MAE and RMSE evaluation results.
- Actual-versus-predicted graph.
- Training-versus-validation loss graph.
- Next-year energy-consumption forecast.
- CSV file containing actual and predicted test values.

**Note:** Actual metric values and forecasts are generated when the notebook is executed. They depend on the dataset and training results.

## 10. How to Run the Project

1. Open Google Colab: https://colab.research.google.com/
2. Create a new notebook.
3. Upload the downloaded Kaggle CSV file.
4. Execute the notebook cells in order.
5. Inspect the dataset and verify the country and target column.
6. Preprocess the data and create five-year sequences.
7. Build and train the LSTM model.
8. Evaluate the model using MAE and RMSE.
9. View the graphs and next-year forecast.
10. Download the generated results CSV.

## 11. Project Limitations

- The forecast is based on historical energy-consumption patterns.
- Missing years may reduce the number of usable training sequences.
- A small number of yearly observations can limit model reliability.
- The model does not explicitly account for future economic changes, energy policies, population changes, or technological developments.
- Forecast accuracy is not guaranteed and should be assessed using test-set results and baseline comparisons.

## 12. Conclusion

This project demonstrates how an LSTM neural network can be applied to time-series forecasting using historical world energy-consumption data. The data is cleaned, normalized, and converted into five-year sequences before training the model. MAE and RMSE are used to evaluate forecasting performance. The resulting predictions can support exploratory energy analysis, although real-world forecasting requires additional variables and careful validation.

## 13. Author

**Project:** World Energy Consumption Forecasting

**Implementation:** Python, TensorFlow/Keras, Google Colab

**Dataset Source:** Kaggle — World Energy Consumption
