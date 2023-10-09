# Churn Prediction model using Logistic Regression
October 2023

## Objective
Develop a statistical model to predict customer churn

## Business Understanding
In the fiercely competitive landscape of the telecommunications industry, customer churn poses a significant challenge. The ability to predict and mitigate customer churn is a strategic imperative for telecommunication companies seeking to sustain growth and maintain a loyal customer base. This endeavor necessitates the development of sophisticated churn prediction models that harness the power of advanced analytics and machine learning. By leveraging historical customer data, usage patterns, demographic information, and other relevant factors, these predictive models aim to forecast which customers are at risk of leaving the service. Such insights enable proactive retention strategies, personalized customer engagement, and ultimately, the preservation of customer relationships critical to the long-term success and vitality of the telecommunications business. In this context, the analysis presents an in-depth exploration of a churn prediction model using logistic regression tailored to address the unique challenges and dynamics of the telecommunications sector, aiming to equip companies with actionable insights to reduce churn and enhance customer satisfaction.

## Data Understanding and Analysis
### Source of Data
The main source of data is database provided by the syriatel on its existing and past customers.

### Description of Data
The data set is contained 3333 records of past and existing customers. The data set with 21 columns of information of each customer such as current status, duration with the company, phone no, area codes, messages,call usage and call charges related information. It contained 16 numeric data colums, 4 categorical data columns and 1 boolean data column.

### Method
Started the analysis understanding the data and premilinary EDA for better understanding the behaviour of the data set. As this is a classification problem to predict to churn or not, the model used is ####Logistic regression with binary response.

first categorized the precdictive variable and explanatory variables. 
Predictive variable - Churn column
Explanatory variables - All other columns except for phone number.

Then segregate the data set into training set to train the models and test set to measure model performance on the unseen data.

Then pipeline was defined and column transferred for imputation, scaling and onehotencoding.

The approach was to start with the base line dummy model and move towrds complex models while evaluating the model effectiveness based on train score, test score, log loss on training and test data, crossvalidation(with F1 scoring), precision, recall accuracy and F1 score.

####Fitted models are 
1. Dummy model
2. Logistic Regression without SMOTE
3. Logistic Regression with SMOTE
4. Logistic Regression with polynomial Features
5. Logistic Regression with polynomial Features hyperparameter tuned(gs Model)

###Results

1. Model effectiveness indicators summary
<img width="527" alt="Model Effectiveness" src="https://github.com/yasiSriLanka/dsc-Phase-3-Solo-Project/assets/141664072/6ccbfcb0-d3ff-400f-8d94-6754f0fbe991">



2. Confusion Matrix
<img width="890" alt="Confusion Matrix" src="https://github.com/yasiSriLanka/dsc-Phase-3-Solo-Project/assets/141664072/651a9fb2-10a2-4efa-bcba-b927f9b72b9c">



3. Area Under the Receiver Operating Characteristic Curve
<img width="434" alt="ROC curve" src="https://github.com/yasiSriLanka/dsc-Phase-3-Solo-Project/assets/141664072/bd2227df-6a70-4cbf-a3cd-cc6412ad5289">


###Recommendation

Based on the above indicators Logistic Regression with polynomial Features hyperparameter tuned(gs Model) perform well over other models. Reported highest train and test scores of 0.91 and 0.89 respectively while minimizing the logloss in the training dataset to 0.23 and test data it is 0.32. Highest CV with F1 score reported for this model is 0.59. On the other indicators highest F1 score of 0.67, precision of 0.61 and recall rate of 0.74 showed with Logistic Regression with polynomial Features hyperparameter tuned(gs Model). It is evident in confusion matrix with lowest false clasification and highest area under the cureve of ROC curve. Therefore it is recommended to use Logistic Regression with polynomial Features with following parameters.

Imputer strategy : mean, 
Degree of Polynomial :3, 
C = 1, Solver = liblinear, 
Tolerance : 0.0001, 
No of iterations = 100
