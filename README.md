# Payment Mode Prediction for Chicago dataset

### Data
https://data.cityofchicago.org/Transportation/Taxi-Trips/wrvz-psew/data

### Objective
The cost of a taxi ride is frequently a surprise, as it is determined by a variety of factors that cannot be predicted in advance. Customers pay in a variety of ways depending on a variety of factors.

In this research, my goal is to use this dataset to forecast the typical payment mode for a trip using just information available ahead of time. Because this is a learning project, I will only use data from the year 2013 within 25 miles.

### Data Description
1. (Trip ID)
2. (Taxi ID)
3. (Trip Start Timestamp) 
          -- Trip start time  
4. (Trip End Timestamp)
          -- Trip end time
5. (Trip Seconds) 
6. (Trip Miles) 
7. (Pickup Census Tract) (Uniquely numbered in each county with a. numeric code)
          -- Pickup tract code
8. (Dropoff Census Tract) ((Uniquely numbered in each county with a. numeric code)
          -- Dropoff tract code
9. (Pickup Community Area)
10. (Dropoff Community Area)
11. (Fare) 
12. (Tips) 
13. (Tolls) 
14. (Extras) 
15. (Trip Total)
          -- Fare + Tips + Tolls + Extras  
16. (Payment Type)
17. (Company)
          -- Car manufacturer
18. (Pickup Centroid Latitude) 
          -- Pickup latitude  
19. (Pickup Centroid Longitude) 
          -- Pickup longitude  
20. (Pickup Centroid Location)
         -- Pickup location  
21. (Dropoff Centroid Latitude)
         -- Dropoff latitude  
22. (Dropoff Centroid Longitude)
         -- Dropoff longitude   
23. (Dropoff Centroid  Location)
         -- Dropoff location  
         
# Exploratory Data Analysis
I assume that a trip is considered valid if it has non zero miles.  
Found big number of observation having a distance of 0m. This is likely to be bad data, so have removed those rows.  
Many fares surpass 55; this is a significant outlier, thus it has been eliminated.   

# Feature Selection
* Since we are restricting the problem data to that which can be obtained before taking a taxi, we are gonna drop all but those variables.  

* We have two factors derived from the location: census and community area. Because for privacy reasons some census tracks are missing, we are not going to use that factor.  

* As for the target variable, we are only considering the 'Payment Type'.

# Model Comparision
![alt text](https://github.com/pragathi1234/ChicagoTaxiTrips/blob/main/images/Screenshot%202021-12-14%20at%207.39.57%20PM.png)
- I have choosen AUC metric because, here each and every class in the target variable plays major role with their own importance. Ex: Some people still use cash as they wont trust on credit cards and some others only prefer online banking or credit card like they are not interested to carry cash every time. Hence I have choosen AUC metrics.

# Final model selection
Decision Tree is selected as the final model as we got 97% accuracy. 
- Even though we had 97% accuracy, it only worked correctly for 43% of the data.

# Summary
- Decision Tree performed best over Logistic Regression and SVM
- Though accuracy score is high for decision tree, R2 score is 47%
- Majority of the journeys are cheap
- On weekdays, the most journeys are made
- The majority of the trips are starting from 10 a.m
- Most of the payments were done by cash or credit card

# Further Exploration
- A typical approach to improve a model is to use more data. In this case, I have used data of the year 2013, but including data from other years could improve the overall score. 
- We could experiment with different algorithms, such as a complex neural network, though this may imply other issues and is a bit overkill.
- Performance of the model can also be improved by tuning with different hyper parameters.

# References
https://www.kaggle.com/fevsea/how-much-will-it-cost-me-pre-ride-regression  
https://scikit-learn.org/stable/auto_examples/model_selection/plot_roc.html#sphx-glr-auto-examples-model-selection-plot-roc-py  
https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html  
https://scikit-learn.org/stable/modules/tree.html  
https://scikit-learn.org/stable/modules/generated/sklearn.svm.SVC.html  
