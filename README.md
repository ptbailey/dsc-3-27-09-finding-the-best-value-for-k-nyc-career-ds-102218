
# Finding the Best Value for K

## Introduction

In this lesson, we'll discuss how changing the value for K can affect the performance of our model, and how we can use this to find the best value for K.

## Objectives

* Understand and explain how the KNN model reacts as K grows larger
* Conduct a parameter search to find the optimal value for K

## Finding the Optimal Number of Neighbors

By now, you've got a strong understanding of how the K-Nearest Neighbors algorithm works, but you likely have at least one lingering question--**_what is the best value to use for K_**? There's no set number here that works best everything. If there was, it wouldn't be called **_K_**-nearest neighbors. The best value to use for K isn't going to be immediately obvious. However, there are some strategies that we can use to help us select the best strategy for K. Before we do that, let's examine the relationship K has with the overall fit of our model. 

## K, Overfitting, and Underfitting

In general, the smaller K is, the more our tighter the "fit" of our model. Recall that with supervised learning, we want to fit the data as closely as possible without **_overfitting_**.  If our model pays too much attention to every little detail and makes a very complex decision boundary, then our model has **_overfit_**. Conversely, if our model does not pay much attention to the data, then our model may **_underfit_** the data. 

<img src="fit.png">

When k is small, any given prediction only takes into account a very small number of points around it to make the prediction. If k is too small, this can end up with a decision boundary that looks like the overfit picture on the right. 

Conversely, as k grows larger, it takes into account more and more points, that are farther and farther away from the point in question, increasing the overall size of the region taken into account. If k grows too large, then the model begins to underfit the data. 

It's important to try to find the best value for K by iterating over a multiple values and comparing performance at each step. 

<img src='best_k.png'>

As we can see from the image above, `k=1` and `k=3` will provide different results! 

## Iterating Over Values of K

Since the model arrives at a prediction by voting, it makes sense that we should only use odd values for k, to help us avoid ties.  In this way, our model will never be evenly split between two classes--one of them will always win out. But how do we figure out which odd number to use?

The best way to find an optimal value for K is to choose a minimum and maximum boundary and try them all! In practice, this means:

1. Fitting a knn classifier for each value of K.
2. Creating predictions with that model. 
3. Calculating and evaluating a performance metric using the predictions the model made.
4. Compare the results for every model and find the one with the lowest overall error, or highest overall score!

<img src='knn_plot.png'>

A common way to do find the best value for k at a glance is to plot the error for each value of K. Find the value for K where the error is lowest. If this graph continued into higher values of K, we would likely see the error numbers go back up as K increased. 

## KNN and The Curse of Dimensionality

Note that KNN isn't the best choice for extremely large datasets, and/or models with high dimensionality. This is because the time complexity (what computer scientists call "Big O") of this algorithm is exponential. As we add more data points to our dataset, the number of operations needed to complete all the steps of the algorithm grows exponentially! KNN often works suprisingly well, given the simplicity of the overall algorithm. However, if your dataset contains millions of rows and thousands of columns, you may want to choose another algorithm, as the algorithm may not run in any reasonable amount of time--it could quite literally take years to complete! 

## Summary

Great! we're approaching the end of this section. In what's next, you'll learn how you perform KNN algorithms easily using Scikit-Learn!
