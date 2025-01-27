# SpeedDating_ML
Researching into the best features and models that can effectively predict speed dating

## Introduction

Dating is hard. Especially in the modern age where everyone is overloaded with information but time poor. Many companies and startup try to make this problem easier with matching services. Dating apps have grown to be a large and lucrative industry. Therefore optimizing the user experience is essential to be successful in being ahead of everyone else. 

## Goal
So the two things people consider when using an app.

1. Save time
2. Finding a right match
Our aim with this project is to identify correct matches for participants. Since no one likes to fill out forms. Especially about intimate information. We will try to identify a list of 10 - 20 most important questions required for the machine learning models to be accurate. We would like to model with as small number of inputs from the participants as possible and still achieve a good accuracy.

Therefore, our goal in this project is find

What is the best type of model to predict a match for the speed dating data
What are the best set of criterias to predict if two people will be a match.

## Methodology
We will be testing out four machine learning models on the numerical data. Since we want to evaluate the models equally.We will loose too much information if we transform the categorical data into numerical.

The models we will evaluate will come from 3 different categorires. They are:

Distance based model - K Nearest Neighbours(KNN)
Probability based model - Gaussian Naive Bayes (NB)
Information based model - Decision Tree (DT) and Random Forrest (RF)
The reason we are choosing these models is for their training speed. Since social patterns will change constantly, the data will need to be constantly updated. Hence speed is important.

Another reason to choose these models are they are base representatives of their specific type of model. By evaluating the base models, we can gain an understanding on what is the best type of model to use for prediction. When we determined the particular model type, we can apply more advanced models from that type to improve accuracy. However that will be beyond the scope of this project.

We will split the data into 'Train' and 'Test' set. Since we have a big enough data set (8378 rows) we split the train and test data 70% and 30%. We will perform all hyperparameter tuning on the Train set to get the optimal parameters. Only then will the model will be used on the test set. This will ensure zero information leakage between the train and test. This can also best evaluate the model performance.

We will be using the F1 score as our model evaluation metric. F1 score is the harmonic score of precision and recall. We are using this score because our data is imbalanced. Optimising F1 score is best when we have class imbalancce

### For each model:

Create a pipeline and list of parameters, run a cross validation and find the best parameters that optimize the F1 score.

Conduct feature selection via the F Score method and the Random Forrest Classifier features selection method to determine which set of features are required for match prediction.

Using the classifiers from both feature selection methods to predict both the training and test set. Then look at the results to see of overfitting takes place.

Evaluate models by the confusion matrix, receiver operation characteristics (ROC) curve.

Check which feature selection method is better by conducting a paired t-test on the cross validation results from two selection methods. This will be used to determine which set of features is better for predicting. If there is no significant difference, the the smaller set of features will be used and recommended.

### Rabbit hole

Since we know that decision tree models work better on categorical data. And since the data comes already with numerical features binned into categorical data. We can also test if there is significant improvments in using categorical data on decision tree based models.

### Evaluation

Once all the models with their cross validation results are obtained. We will then compare the cross validation results of all of the models to determine with is the best model to use.

The best model will be recommended with the set of features. The final set of features is then the best set of features to be used with the final model to predict match for speed dating.

## Data ¶
The data is from OpenML was gathered from participants in experimental speed dating events from 2002-2004. During the events, the attendees would have a four-minute "first date" with every other participant of the opposite sex. At the end of their four minutes, participants were asked if they would like to see their date again. They were also asked to rate their date on six attributes: Attractiveness, Sincerity, Intelligence, Fun, Ambition, and Shared Interests. The dataset also includes questionnaire data gathered from participants at different points in the process. These fields include: demographics, dating habits, self-perception across key attributes, beliefs on what others find valuable in a mate, and lifestyle information.

# Summary
In this project we wanted to find

What is the best type of model to predict a match for the speed dating data
What are the best set of criterias to predict if two people will be a match.

### In the final comparison of

Distance based model - KNN
Probability based model - NB
Information based model - DT and RF
We find that Probability based model Gaussian naïve Bayes (NB) perform best. We see from the paired t-test and box plot that the cross validation results is significantly better than other models. We find with the probability model, selecting 20 features with random forrest selector in this preliminary study have yielded the best resultsl.

While we did have high hopes for the information based model, we found that it under performed. When categorical data is applied we found the model performed worse on prediction but better on overfitting. From this result we can infer that although binning the data into categories can make the data gathering process simpler, it comes at a cost of accuracy.

Finally we can conclude for the project that speed dating match results are best modelled with Probability based models with top 20 features.

We can see from the categories, liking the other party comes first followed by funny, mutual attractiveness and shared interest.

It is interesting to note that intelligence, sincerety, age difference, same race, matter much less in contributing to a match result. Although these attributes may be essential for long term relationships, it shows that at the end, humans are still emotional creatures. Being funny and being attractive can gain attention and good rapport fast. Much faster than other attributes.

This is probably why most people write in their dating app profile that they want someone who makes them laugh?

## Further steps
Since we have identified probability based models outperform other model types in modelling this speed dating data. We can improve upon the accuracy of predictions by:

Feature engineering - combine, or augment some of the top selection features under supervision of human behaviour specialist to creat better features from the responses.

Apply more advanced probability based models.

Explore ways to deal with class imbalance in the data. In this study we only managed class imbalance by selecting F1 score as the optimising score since we are only trying to determine the best type of model and resulting features. More advanced techniques can be used to deal with class imbalance when training the model. This can be implemented in the next step.

The above three points are just some of the steps to further optimise speed dating modeling results. This project is just a beginning. There are more future research we could do.

# Reference
Speed Dating datset from OpenML
https://www.openml.org/d/40536

Optimising score selection
https://towardsdatascience.com/accuracy-recall-precision-f-score-specificity-which-to-optimize-on-867d3f11124

FeaturesSelection.com
https://www.featureranking.com/tutorials/machine-learning-tutorials/sk-part-3-cross-validation-and-hyperparameter-tuning/

Code taken from RMIT MATH2319 Tutorial on SK5

Mutiple comparison ttest from : https://pythonhealthcare.org/2018/04/13/55-statistics-multi-comparison-with-tukeys-test-and-the-holm-bonferroni-method/
