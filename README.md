# NYC_GreenTaxi_Analysis

The Green_Taxi_Analysis notebook included in this repository contains the code that explores the Green Taxi dataset made publicly available on http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml to answer some interesting questions and do some predictive analytics.
This document will make it easier for the reader to understand the code that has been included as part of the submission.

The Notebook contains the following sections:
• Introduction.
• Importing the libraries needed.
If the libraries are not present on your system, you can choose to do
“pip install <package_name>” or “conda install <package name>.”
Depending upon the Python version installed, either of the two install statements will allow you to install the packages desired.
• Load the dataset : The original data is at https://s3.amazonaws.com/nyc-tlc/trip+data/green_tripdata_2015-09.csv. You can download the dataset and keep it in the same folder as the notebook. If the file is present, the notebook will read the data file locally. Else it will read the data from the server and create a new local copy.
• Exploration: I have done the following things:
- No of rows and columns
- Snippet of the Data
- Datatypes
- Check for null values
• Data Cleaning: This section explains the different steps I have taken to clean the data to make it easy to use and read.
• Answering Analytical Questions: I am answering questions related to :
- Distribution of Trip Distance
- Mean and Median Trip Distances by Hour of the day.
• Building model to predict :
To replicate the model results, please follow the steps:
1. Provide data having similar values as Green Taxi data present on https://s3.amazonaws.com/nyc-tlc/trip+data/green_tripdata_2015-09.csv.
By similar, I mean having identical columns and datatypes.
Shruti Sankolli
Capital One Coding Challenge
2. Create Derived Variables: Pick_up_hour and Drop_off hour from 'lpep_pickup_datetime' and 'Lpep_dropoff_datetime' variables respectively as:
data["Pick_up_hour"]=pd.to_datetime(data['lpep_pickup_datetime']).dt.hour
data["Drop_off_hour"]=pd.to_datetime(data['Lpep_dropoff_datetime']).dt.hour
3. Data Cleaning:
- Check for null values using data.isnull().any(). If any column shows null as TRUE, either drop all such rows or replace the null values with the median/mean/ frequently used value depending upon the relevancy. I have used frequently used value to replace the nulls that I encountered in Trip_type and RateCodeID columns.
- Check for negative values in the amount related fields. I have used the absolute values for any such negative values. Also for all trips where Total Amount is less than 2.5$ I have dropped it as the base minimum rate is 2.5$.
4. Build predictors and target variables:
- Predictors: Drop off 'Ehail_fee','Store_and_fwd_flag','lpep_pickup_datetime','Lpep_dropoff_datetime' columns from the predictors as they are not relevant to the percentage tip. Additionally, also drop Percentage_tip as it is the target variable that we wish to predict.
- Target: Percentage_tip
5. Split into train and test splits: I have used Python skicit's train_test_split to randomly split the data into 80:20 train-test ratio.
6. Instantiate the RandomForestRegressor.
7. Fit the instantiatied model to the data.
8. Predict the tip percentage.
9. Plot the result.
• Building up a hypothesis to test whether average speed over a course of a trip depends on the time of the day or week of the month.
• Future Work
• Conclusion.
