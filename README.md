# Loan Default Prediction
## Table of contents
* Overview
* Technical Aspect
* Installation
## Overview
Whenever an individual/corporation applies for a loan from a bank (or any loan issuer), their credit history undergoes a rigorous check to ensure that whether they are capable enough to pay off the loan.The issuers have a set of models and rules in place which take information regarding their current financial standing, previous credit history and some other variables as input and output a metric which gives a measure of the risk that the issuer will potentially take on issuing the loan. The measure is generally in the form of a probability and is the risk that the person will default on their loan (called the probability of default) in the future. Based on the amount of risk that the issuer is willing to take (plus some other factors) they decide on a cutoff of that score and use it to take a decision regarding whether to pass the loan or not. This is a way of managing credit risk. The whole process collectively is referred to as underwriting. 
This project aims to develop a robust module to predict loan default in future based on the data that is available during loan application.
## Technical Aspect
### Train Test split
The dataset consists of 855969 rows and 73 columns. The data is divided into train (June 2007 - May 2015) and out-of-time test (June 2015 - Dec 2015) data using the variable 'issue_d'. The training data is used to build models and finally apply it to test data to measure the performance and robustness of the models. 
### Preprocessing the Training data
Performed the following steps for precprocessing of training data:
#### Identified and dropped unique columns
#### Dealing with missing values
checked the percentage of nan values present in each feature and listed out the features which has missing values. 
Dropped features with more than 75% NAs.
#### Length of credit history in years
Credit history length is one of the important deciding factors and seven years is deemed a reasonable amount of time to establish a good credit history. A longer credit history shows you have more experience using credit, and this helps lenders be more accurate in the level of risk they take when lending to you.
  df['cred_hist_len_years']=df['issue_d'].dt.year-df['earliest_cr_line'].dt.year
#### Exploratory Data Analysis


After analysing the features with missing values I found that next_pymnt_d has null values and it should be null for fully paid off loans and non null for defaulters.But there are some null values in next_pymnt_d for defaulters which means these are charged off loans. Hence for default_ind=1 we have 2 subcategoreies- default and charged off loans. Similarly for default_ind=0 we have two subcategories- non default and current loans
