# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import the necessary packages using import statement.

2.Read the given csv file using read_csv() method and print the number of contents to be displayed using df.head().

3.Import KMeans and use for loop to cluster the data.

4.Predict the cluster and plot data graphs.

5.Print the outputs and end the program

## Program:
```
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: PRITHIV S
RegisterNumber: 212224020043
```
```
import pandas as pd
import numpy as np
from sklearn.cluster import KMeans
from sklearn.metrics.pairwise import euclidean_distances
import matplotlib.pyplot as plt
data = pd.read_csv("/content/Mall_Customers.csv")
data
X = data[['Annual Income (k$)' , 'Spending Score (1-100)']]
X
plt.figure(figsize=(4,4))
plt.scatter(data['Annual Income (k$)'], data['Spending Score (1-100)'])
plt.xlabel('Annual Income (k$)')
plt.ylabel("Spending Score (1-100)")
plt.show()
k = 5
kmeans = KMeans(n_clusters=k)
kmeans.fit(X)
centroids = kmeans.cluster_centers_
labels = kmeans.labels_
print("Centroids: ")
print(centroids)
print("Label:")
# define colors for each cluster
colors = ['r', 'g', 'b', 'c', 'm']

# plotting the controls
for i in range(k):
  cluster_points = X[labels == i]
  plt.scatter(cluster_points['Annual Income (k$)'], cluster_points['Spending Score (1-100)'], color=colors[i], label=f'Cluster {i+1}')

  #Find minimum enclosing circle
  distances = euclidean_distances(cluster_points, [centroids[i]])
  radius = np.max(distances)

  circle = plt.Circle(centroids[i], radius, color=colors[i], fill=False)
  plt.gca().add_patch(circle)

#Plotting the centroids
plt.scatter(centroids[:, 0], centroids[:, 1], marker='o', s=200, color='k', label='Centroids')

plt.title('K-means Clustering')
plt.xlabel("Annual Income (k$)")
plt.ylabel('Spending Score (1-100)')
plt.legend()
plt.grid(True)
plt.axis('equal') 
plt.show()
```

## Output:
![image](https://github.com/harini1006/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/113497405/de1e047c-8fc0-4e7e-88e3-250bd28ba8c6)

![image](https://github.com/harini1006/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/113497405/84fd0614-b594-4265-8dec-243ec7f7acc8)
![image](https://github.com/harini1006/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/113497405/a1c6c16d-8bc7-4cd8-bc3d-cebde586281a)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
