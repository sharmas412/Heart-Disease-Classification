# Heart Disease Classification - UCI Dataset

## Introduction

This project aims to predict the presence of heart disease in patient.  According to the Centers for Disease Control and Prevention (CDC), heart disease is the ‘leading cause of death for men, women and people of most racial and ethnic group in the US.’  Heart disease death accounts for about 25% of total deaths in the US as about 647,000 Americans die each year from heart disease. Furthermore, the cost of health care services, medicines and lost productivity due to death from heart diseases is about $219 billion each year. In addition, more than 18 million adults age 20 and older have coronary heart disease. As a result, it is important to correctly predict heart diseases early on that could prevent loss of life and reduce cost related to heart disease. 

In this project, I use dataset from the UCI Machine Learning Repositories Cleveland dataset and apply random forest and gradient boosting to classify patients with heart disease. Although I use various scoring measures, I tune my models to increase recall as I believe it is important to minimize false negatives so that we minimize classifying people with heart disease as not having one.  I find that random forest performs better than gradient boosting. I tune the hyper parameters first by randomsearch and then by a gridsearch to improve the recall. I then use the wrapper feature selection method which improved recall to 0.846, which is an increase of almost 24 percent. 


## Data
The data comes from the UCI Machine Learning Repository Cleveland dataset. The dataset has 303 observations and 13 features. The dataset has the following features: age, sex, chest pain type (cp), resting blood pressure(trestbps), fasting blood sugar(fbs), thallium stress test maximum heart rate achieved (thalach), exercise induced angina(exang), ST depression induced by exercise relative to rest(oldpeak), the slope of the peak exercise ST segment(slope), the number of major vessels colored by flourosopy(ca), and exercise thallium scintigraphic defects (thal).

## Modeling
I use the random forest and gradient boosting to classify heart disease patients. For the initial models, with 5 fold cross-validation, the accuracy of both the models were around 0.79 compared to 0.55 of the dummy classifier. However, the random forest model performed better in precision and accuracy but the gradient boosting performed better in recall, so I’ll tune hyper parameters for both the models. The table below shows the various scores for the models.

![FirstTable] (https://github.com/sharmas412/Heart-Disease-Classification/blob/master/images/Table1.PNG)

I first use the RandomSearchCV to narrow down the search of the hyperparameters so that I can fine tune them using the GridSearchCV.  Here, it is clear that the random forest does a much better job as it scores consistently higher across all evaluation metrics. The recall increases by about 9 percent compared to the initial random forest model. The table below shows the scores for the models.

![SecondTable] (https://github.com/sharmas412/Heart-Disease-Classification/blob/master/images/Table3.PNG)

### Wrapper Feature Selection
The graph below shows the variable importance based on the random forest model that maximizes recall. 

![ImpFeatures] (https://github.com/sharmas412/Heart-Disease-Classification/blob/master/images/Figure.PNG)

Given the variable importance, I choose a subset of column that are more important to the model. I then run the model on this subset of features which further improves the recall , precision and accuracy of the model, which is shown in the table below. 

![ThirdTable] (https://github.com/sharmas412/Heart-Disease-Classification/blob/master/images/Table4.PNG)
