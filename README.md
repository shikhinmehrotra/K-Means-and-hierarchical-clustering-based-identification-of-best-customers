# K-Means-and-hierarchical-clustering-based-identification-of-best-customers
This project builds a K-means and a hierarchical clustering model to predict the best customers for an online retail store using the Recency, Frequency, Monetary (RFM) segmentation technique.

# Data set
The data set consists of customer data which includes features such as customer ID, invoice date, stock code, description of the item bought, quantity, price of one unit and country. This describes purchases made by customers at the online retail store. The data set comprises of 54,109 entries.

# Data preprocessing
The data is checked for null values and about 24% of values of Customer ID are null and some values in the description column are also null. Since customer ID is crucial for any further task, all null values are dropped.

## RFM analysis
In this project, three new features are added viz. Recency, Frequency and Monetary. Recency refers to how recent was the last purchase at the store by a customer. Frequency refers to how many times has a particular customer purchased goods at the online store till date. Monetary refers to the cumulative value of goods purchased by a customer till date. These three metrics help identify the most profitable customers for the store. 

## Outlier treatment
Boxplots for Recency, Frequency and Monetary are plotted and outliers are visualised. To treat outliers, values ranging from Q1 - 1.5xIQR and Q3 +1.5xIQR are retained, where Q1, Q3 and IQR refer to 1st quartile, 2nd quartile and inter-quartile distance respectively.

## Standardisation
Subsequently, all of the data is standardised using sklearn's StandardScaler() class.

# Model building
Before building the K-means model, a a custome function is defined to calculate the Hopkin's statistic which is a metric for calculating the cluster tendency.

## Hopkin's statistic
The Hopkins statistic, is a statistic which gives a value which indicates the cluster tendency, in other words: how well the data can be clustered.

-If the value is between {0.01, ...,0.3}, the data is regularly spaced.
-If the value is around 0.5, it is random.
-If the value is between {0.7, ..., 0.99}, it has a high tendency to cluster.

## Building K-means model
K-means model is built using Kmeans() sub-class of SkLearn's cluster() class. The model uses a value of k=5 to find 5 clusters of the data.

# Evaluation of KMeans model
The KMeans model is evaluated using the following:

## Silhouette analysis
Silhouette score = p-q/max(p,q)

Where,
p is the mean distance to the points in the nearest cluster that the data point is not a part of
q is the mean intra-cluster distance to all the points in its own cluster

The value of the silhouette score range lies between -1 to 1.

A score closer to 1 indicates that the data point is very similar to other data points in the cluster,
A score closer to -1 indicates that the data point is not similar to the data points in its cluster.

A plot of the Silhouette score is plotted for different values of k and the highest score is observed for a value of k=3.

## Sum of squared distances
The sum of squared distances is plotted for different values of k and it is seen that the sum of squared distances decreases as teh number of clusters is increased.

## Bar plots of mean values of different clusters
Mean values of Recency, Frequency and Monetary columns is plotted for different clusters created by the KMeans model for visualising the differences between the clusters.

# Hierarchical clustering
A dendrogram is created and a cluster cut value of 5 is used to arrive at 5 clusters. The plots of mean values of Recency, Frequency and Monetary columns for each of the clusters thus formed is plotted.
