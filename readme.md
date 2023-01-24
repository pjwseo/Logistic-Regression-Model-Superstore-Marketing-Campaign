# Building Logistic Regression Model Demo
---
## By Junwon Seo
---

### Purpose:
A superstore is planning to re-launch a year-end promotion for a gold membership. The management feels that the best way to reduce the cost of the campaign is to make a predictive model which will classify customers who might purchase the offer. The superstore wants to predict the likelihood of the customer giving a positive response and wants to identify the different factors which affect the customer's response. You need to analyze the data provided to identify these factors and then build a prediction model to predict the probability of a customer will give a positive response.

### Dataset:
This dataset and challenge can be found on: https://www.kaggle.com/datasets/ahsan81/superstore-marketing-campaign-dataset
This dataset contained 2,240 rows with 22 columns pertaining to each customers' demographic data, recent shopping experience, and conversion status from last campaign. The data was relatively very clean with a few minor clean ups: 1) Null income data for a small portion of users, which were dropped from the study. 2) Consolidating education background and marital status data by pooling similar statuses together (Ex. 'Single' & 'Alone'). 3) Translating customer registration date, a datetime data, into 'account_age' int field, making it easier to work with.

### Summary of Findings:
Logistic Regression was performed to predict 'response', a binary data field where 1 = conversion and 0 meant no conversion.
StatsModels Logit was used. Variables with p greater than or equal to 0.05 were removed and model was re-built with the following findings:
* intercept = 0.09395 (probability that a completely new customer with no attached family will sign up for the promotion)
* kidhome = e^0.4118 = Every one more kid in the family increases the likelihood of customer converting by 1.509 times, ceteris paribus.
* teenhome = 1/e^-0.9173 = Every one less teen in the family increases the likelihood of customer converting by 2.503 times, ceteris paribus.
* recency = 1/e^-0.0261 = Every one less day since the customer shopped increases the likelihood of customer converting by 1.026 times, ceteris paribus.
* wine = e^0.0018 = Every wine purchase increases the likelihood of customer converting by 1.002 times, ceteris paribus.
* meat = e^0.0015 = Every meat purchase increases the likelihood of customer converting by 1.002 times, ceteris paribus.
* fish = 1/e^-0.0033 = Each one less fish purchase increases the likelihood of customer converting by 1.003 times, ceteris paribus.
* gold = e^0.0029 = Every gold purchase increases the likelihood of customer converting by 1.003 times, ceteris paribus.
* web_purchase = e^0.1051 = Every purchase made on the web increases the likelihood of customer converting by 1.111 times, ceteris paribus.
* catalog_purchase = e^0.0863 = Every catalog purchase increases the likelihood of customer converting by 1.090 times, ceteris paribus.
* store_purchase = 1/e^-0.1955 = Each one less in-store purchase increases the likelihood of customer converting by 1.216 times, ceteris paribus.
* account_age = e^0.0023 = Each day since registration increases the likelihood of customer converting by 1.002 times, ceteris paribus.

In order to assess the model, we take a look at the following classification metrics: Accuracy, Precision, Recall, and ROC (Receiver Operating Characteristic)
* The accuracy of the logistic regression model is 0.85
* The precision of the logistic regression model is 0.77 (Macro Avg)
* The recall of the logistic regression model is 0.60 (Macro Avg)
* The AUC (Area Under Curve) of the ROC curve is 0.84

### Conclusion:
I was able to build a logistic regression model to help determine which customers the superstore should spend their campaign budget on. A specific improvement that could be made in the future is a better balanced dataset. In this dataset we used, the ratio between 0 and 1 is about 5 to 1. However, we should be able to improve the performance of the marketing campaign and hence the dataset in the subsequent run with the model I built today. This should help us build a stronger model for the next run of the campaign, improving classification metrics overall, especially precision and recall.