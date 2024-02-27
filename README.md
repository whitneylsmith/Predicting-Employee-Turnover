# Predicting Employee Turnover
Dataset: https://www.kaggle.com/datasets/jacksonchou/hr-data-for-analytics <br>
Analysis instructions and code adapted from Google Advanced Data Analytics Certificate on Coursera. <br>

## Introduction
* Employee turnover is “a measure of permanent separation from the organization” (Gatewood et al., 2008, p. 672).
* This dataset and company are fictional, but turnover is a very real concern for companies. Due to the cost to hire and train new employees, having a high employee turnover rate can get expensive. 
* Additionally, important institutional knowledge can be lost when an experienced employee leaves. This can have its own costs, such as decreased productivity.

## Questions to Answer
* How do we predict individual employee turnover?
* What influences attrition?
* How do we improve employee retention?
## What predictors are in the dataset?
* Satisfaction ratings
* Score on last evaluation
* Number of projects
* Hours worked per month
* Employee tenure
* Work accidents
* Promotions
* Department
* Salary Range

## Developing a Prediction Model
* When predicting a binary outcome, we can use a Logistic Regression Model or a Tree-Based Model, such as a Random Forest Model.
* For this project, I chose to use both Logistic Regression and Random Forest methods and compare their performance.


## Logistic Regression Model Performance Summary
* What wasn't included?
  * Evaluation scores and number of hours worked per month were removed as predictors because they were too highly correlated to other predictors (known as multicollinearity).
* Performance Metrics:
    * Accuracy: 0.818711
    * Precision: 0.390625
    * Recall: 0.206612
    * F1 Score: 0.270270
    * AUC: 0.572039
* The Logistic Regression model has good Accuracy, but the remaining performance metrics are poor. This means that the model is poor at predicting which specific employees will leave.

## Random Forest Model I Performance Summary
* I first created a Random Forest Model with all predictor variables included.
* Performance Metrics:
    * Accuracy: 0.985
    * Precision: 0.987
    * Recall: 0.995
    * F1 score: 0.991 
    * AUC score: 0.962 
* This model performs better than the Logistic Regression model. However, such high scores (close to 1) may indicate that there is an issue with data leakage. Data leakage occurs when data is included in a model that may not be available when the model is used. It is unlikely that a company will have satisfaction scores for all of their employees, since not all employees fill out satisfaction surveys.

### Random Forest Model II Summary
* For an attempt at a more realistic model, I created a random forest model without the satisfaction data.
* Performance Metrics
    * Precision: 0.981 
    * Recall: 0.990
    * F1 score: 0.986
    * AUC score: 0.943
* This is still a highly performing model, but it is less likely to have data leakage than the original random forest model.
* Of the three models created, this second Random Forest Model best balances predictive performance with only using predictors that will be available to predict on. This is the model that I would recommend using.


## Most Important Predictors of Turnover
* Here are the most important predictors of turnover in our selected Random Forest Model, in order of most to least important:
    * Number of projects
    * Hours worked per month
    * Tenure
    * Score on last evaluation


## Additional Insights
* The largest department by number of employees is Sales, followed by technical and support departments.
* The majority of employees have been at the company between 2 and 5 years.
* Very few employees at Salifort Motors have been promoted in the last 5 years. Employees feeling like they can't grow their careers at their current company can lead them to pursue career opportunities elsewhere.
* Few employees have salaries in the high range. Most have low or medium salaries. The company may want to review their compensation model to ensure they are providing competitive and fair salaries.
* The exploratory data analysis showed a bimodal distribution for both number of projects and average hours worked, meaning that people who leave the company tend to work either high or low numbers of hours and have few or very many projects, with a dip in the middle. It may be the case that some employees who leave are not being given enough responsibility to grow in their career, or it may be that these are underperforming employees who will be let go due to performance issues. To investigate this further, I would recommend getting data about which employees left voluntarily compared to those who left involuntarily.


## Recommendations and Actionable Steps:
* Benchmark turnover rates against comparable companies. This will give Salifort Motors an idea of how their turnover rates compare to similar companies.
* Conduct detailed employee satisfaction survey and focus groups to identify ways to improve satisfaction. Even though we didn't include satisfaction in our final model, in the first Random Forest Model, it was the most important indicator of turnover.
* Pay attention to how many hours employees are logging and how many projects are assigned to each employee. If an employee is working over the expected number of hours, consider reassigning some of their projects to get to a more manageable workload. It may also be useful to analyze the number of projects associated with full-time hours and set that as a cap for number of projects assigned to each employee.
* Collect additional data about which employees left voluntarily compared to those who left involuntarily. Employees leave for very different reasons, so it will give more insights to see how the patterns differ between employees who leave for better opportunities compared to those who are asked to leave.


## Citations
* Gatewood, R. D., Feild, H. S., & Barrick, M. R. (2008). Human resource selection. Cengage Learning.


## Assumption Made About the Data:
* Voluntary and involuntary attrition are both included
