# Bayes' Theorem - Lab

## Introduction

In this lab, you'll practice Bayes' Theorem in some simple word problems. 

## Objectives
In this lab you will be able to: 

- Use Bayes' theorem to determine the probability of specific events 

## Define a custom function for Bayes' theorem

To start, write a function, `bayes()`, which takes in the probability of A, the probability of B, and the probability of B given A. From this, the function should then return the conditional probability of A, given that B is true.


```python
def bayes(P_a, P_b, P_b_given_a):
    # Your code here
    P_a_given_b = (P_b_given_a * P_a) / P_b
    return P_a_given_b
```

## Skin Cancer

After a physical exam, a doctor observes a blemish on a client's arm. The doctor is concerned that the blemish could be cancerous, but tells the patient to be calm and that it's probably benign. Of those with skin cancer, 100% have such blemishes. However, 20% of those without skin cancer also have such blemishes. If 15% of the population has skin cancer, what's the probability that this patient has skin cancer? 

> Hint: Be sure to calculate the overall rate of blemishes across the entire population.


```python
# Your code here
P_blemish_given_skin_cancer = 1
P_blemish_not_skin_cancer = .2
P_skin_cancer = 0.15
P_not_skin_cancer  =  0.85
#P_cancer_given_blemish = ? , cancer = a, blemish = b  P(A|B)
P_blemish = (P_blemish_given_skin_cancer * P_skin_cancer) + (P_blemish_not_skin_cancer *  P_not_skin_cancer)
bayes(P_skin_cancer, P_blemish,  P_blemish_given_skin_cancer)
```




    0.46875



## Children (I) 

A couple has two children, the older of which is a boy. What is the probability that they have two boys?


```python
# Your solution P(2boys|older child is a boy) - A=2boys, B=older boy 
P_ob_given_2b = 1
P_ob = 0.5
P_2b = P_ob *  P_ob
bayes(P_2b, P_ob, P_ob_given_2b)
```




    0.5



## Children  (II)

A couple has two children, one of which is a boy. What is the probability that they have two boys?


```python
# Your solution P(2boys|1 of 2 children is a boy),  A =2boys, B=1of2
P_2b
P_1of2 = 3/4 #G|B + B|B + B|G (G|G )  
P_1of2_given_2b = 1
bayes(P_2b, P_1of2, P_1of2_given_2b)
```




    0.3333333333333333



## A diagnostic test

A diagnostic test is advertised as being 99% accurate 

* If a patient has the disease, they  will test positive 99% of the time 

* If they don't have the disease, they will test negative 99% of the time  

* 1% of all people have this disease 

If a patient tests positive, what is the probability that they actually have the disease?


```python
# Your solution P(Disease | positive test) A=disease, B=pos
P_pos_given_disease  = 0.99 #(P(B|A))
P_pos_not_given_disease =  0.01  
P_disease = 0.01 #P(A)
P_not_disease = 0.99 
P_pos = P_pos_given_disease * P_disease + P_pos_not_given_disease * P_not_disease #P(B)
bayes(P_disease, P_pos, P_pos_given_disease)
```




    0.5



## Summary 

In this lab, you practiced a few simple examples of Bayesian logic and how you can add prior information to update your beliefs about the chance of events.
