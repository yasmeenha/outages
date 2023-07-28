
Eagle-I Power Outage data challenge

This project aims to address the challenge questions in 
{Challenge 7: EAGLE-I Outage Data 2014-2022}'' of 2023 SMC Data Challenge
In particular, we are targeting three major questions: analyzing restoration times (Question 1), correlation with relevant datasets (Question 2),  power outage prediction model  (Question 5), and temporal patterns and trends in outages during 2014-2022 (Question 6). 
Our solutions and major findings for each question are summarized below.

{Question 1: Analyzing Restoration Times}}
Electricity is a vital commodity. This makes power outage events highly destructive, with economic losses compounding the longer the outage lasts. For this reason restoration analysis has been studied extensively, particularly on the EAGLE-I dataset. The challenge in analyzing this dataset is the lack of labels beyond the aggregated number of customers without power and the timestamp when the outages occurred. This makes it hard to identify large individual outages, since multiple outages can occur at the same time and some can occur as typical fluctuations under normal circumstances.
For this reason, identifying power outage events, especially in large counties, is subjective. 

To analyze restoration times, we tested the efficacy of anomaly detection and thresholding. Because EAGLE-I does not have semantic labelling, we chose thresholding as a more predictable method for identifying power outages.
In our time series analysis, we found that extracting the trend component using seasonal decomposition from the statsmodels Python package with a period of 4 hours and using a threshold from  gave us reliable segments of large outages without significantly reducing the dataset's resolution.


Question 2: Correlation with Relevant Datasets
After obtaining the restoration times, we find correlations between power outages and socioeconomic indicators and weather events.
Our approach utilizes official warnings and advisories from the National Weather Service. Since EAGLE-I and the NWS Watches, Warnings and Advisories datasets are updated in real-time, this provides the potential for monitoring power outages alongside a wide-range of weather events. It has been documented \cite{kar_repowerd_2022} that extreme weather events are responsible for the majority of power outages. We found sudden peaks of power outages especilly during Hurricane Irma in Florida in 2017 september,and during deep freeze in Texas in mid-february 2021. 


Question 5: Forecasting power outage model
Based on 8 years of historic power outage data, a power outage model was implemented using LSTM, XGBoost Regressor, and prophet libraries for the daily outages of San diego county. The power outage for 30 days for San Diego was forecasted using prophet library and the power outage for 140 days was forecasted using LSTM with a test root mean square error  of 40139.51.


Question 6: A detailed time series analysis was done on the daily outage of San Diego County using Arima, Darts and prophet libraries and the trends in the power outages for eight years have been plotted and observed. In our findings, we found that there was a reduction in power outages  from an average of 5000 to 2000 outages in Sandiego from 2021 to 2023 based on the prophet library and the highest power outages where found on Fridays and Saturdays with round 600 outages.The temporal patterns can be studied in the code provided as the GitHub link.
