# Monsoon-CreditTech-assessment


# Approach


## 1. Data Preprocessing

    a. Null Values
        1. Some cols have more than 81% of the values as null. Cannot fill these values without knowing about the cols. (with backfill for sequence, etc.)
        2. Some cols have ~13% of the values as null.
        Not considering removing rows, since data points are less.

        data1 : Dropping cols with more than 80% null. And filling the rest. Median for Numeric, mode for cat.
        data2 : Dropped the cols with more than 80% null and filling the rest with KNN imputer for cat cols and simple imputer for Numeric cols.

    b. Outlier Removal 
        Removed the outlier using IQR 

    c. Imbalanced Dataset
        data1 : Oversampling using SMOTE
        
    d. Feature Scaling 
        Scaled the features for algos requiring feature scaling using Min Max Scaler.
    
    e. Feature Selection 
        There exists multicollinearity between the features. 
        Hence removed the multicollinearity using VIF with a threshold of 10.
        So if the VIF score is more than 10, the feature is removed.

Performed an experiment, where I took 2 types of training data for model building as in Null Values section in data preprocessing.

## 2. Model Building
    Build models using 5-Folds Cross Validation and Grid Search CV for parameter tuning.

    a. Logistic Regression and SVM and Decision Tree
        Performed an experiment to see how these models would perform on both the data (data1, and data2)
    
    But the performance of Logistic Regression and SVM was not great also because the relationship of the features and the distribution of data was not linear.
    Also, since the data size was less, so the potential issue that can occur is bias as well as variance. 
    Hence Ensemble approach was required.

    b. Random Forest and XGBoost
        Oversampled the data using SMOTE and trained the model on 3 different data.
        data1 : Data with imputed null values
        data2 : Data with imputed null values and oversampled using SMOTE
        data3 : Data with filled null values using mode for cat cols and median for numerical cols.

        Both the Random forest model and XGBoost model performed well on Data2.
        And the XGBoost model was performing slightly better.
        Hence trained a final XGBoost model.


Constraints and Limitations : Due to hardware/software limitations, could not tune the parameters to its highest potential.



    

    


