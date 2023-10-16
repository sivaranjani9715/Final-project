# Final-project

This repository features a range of projects related to social media.

The First project, 'Ratings of Guvi Courses', is focused on helping the Guvi company 
predict the ratings that their courses will receive from learners. By doing so, the company
can identify areas where improvements are needed to enhance the overall learning experience
for their learners.

Lastly, the 'Instagram Influencers' project consists of a series of questions that can help
improve various data processing techniques.

Overall, this repository provides a valuable resource for anyone interested in exploring 
the intersection of social media and data analytics. Each project offers unique insights 
and tools for analyzing and optimizing your social media strategy.


# Ratings of GUVI Courses

# INTRODUCTION:

    This model to predicts the ratings given by the learners to the course based 
    on various factors like price, number of suscribers, number of reviews, 
    course subject, content duration
    
# DATA CLEANING:

    Load the dataset
        Dataset contains 3680 rows and 11 columns
        
    Handling missing values
        Dataset contains negligible(< 0.1%) valus so deleting them don't effect
        the dataset and no loss of information
        
    Checking for duplicates
        No duplicate values present 
        
    Removing irrelevant columns
        I have deleted irrelevent columns that do not effect target column are 
        course_id, course_title,url,published_timestamp
        
    Plottings
        Plottings between different features are plotted to find the nature 
        of columns, outliers and correlation
        
    Encoding categorical variables
        Categorical data is encoded since ML works with numbers, here I 
        have used label encoder
        
    Handling outliers
        There are outliers present in the data that are detected using various
        plots like box plot,histogram and scatter plot, more than 10 % data contains
        outliers, inorder to handle these outliers I have used log tansformation
        
    Multicolliniarity
        After finishing the entire dataset I have checked for multicolliniarity, 
        found that the vif score of the columns is very high(10 to 20) that 
        need to be handled while model tuning
MODEL TRAINING, TESTING EVALUATING AND TRY NEW VALUES:

Importing the necessary libraries

Splitting the data into training and testing sets:

Train_test_split() function is used to randomly split the data into training 
and testing sets.

'test_size' parameter specifies the proportion of the data to be used for testing.

'random_state' parameter is used for reproducibility of the results.
Defining the preprocessing steps for numerical and categorical features:

Two separate pipelines are defined for numerical and categorical features.
num_transformer pipeline has two steps:
i. SimpleImputer with 'median' strategy to fill missing values in numerical 
features with the median of the column.
ii. StandardScaler to standardize the values of numerical features.

cat_transformer pipeline also has two steps:
i. SimpleImputer with 'most_frequent' strategy to fill missing values in 
categorical features with 
the most frequent value in the column.
ii. OneHotEncoder to one-hot encode the categorical features.
Combining the preprocessing steps using ColumnTransformer:

a. ColumnTransformer combines the num_transformer and cat_transformer pipelines.
b. transformers parameter specifies the pipeline for each type
of feature (numerical or categorical).
c. The 'transformers' parameter takes a list of tuples. Each tuple 
specifies the name of the pipeline, the pipeline itself, and 
the names of the columns to be transformed.
Defining the Random Forest regression model:

a. RandomForestRegressor is defined with 100 decision trees and random state 42.
Creating the pipeline:

a. Pipeline is created with the 'preprocessor' and 'regressor' steps.
b. 'preprocessor' is the ColumnTransformer object that preprocesses the data
before feeding it to the model.
c. 'regressor' is the RandomForestRegressor object that predicts the target variable.
Fitting the pipeline on the training data:

a. fit() method is called on the pipeline object to train the model on the training data.
Making predictions on the test data:

a. predict() method is called on the pipeline object to make predictions on the test data.
Evaluating the model performance:

a. r2_score() function is used to evaluate the model performance
