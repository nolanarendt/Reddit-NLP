# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Web APIs & NLP

## Problem Statement
Using various models with different vectorizers, I want to determine if a model can accurately predict a users maturity/age by analyzing the words that they use in different subreddits. I will collect 5,000 rows of data from each subreddit, r/Teenagers and r/Adulting, and use that data to train my Naive Bayes and KNN models. I aim to identify key words that are used in either of the two subreddits, create stop words, and determine the best hyperparameters in my models.

## Contents & Data Used
Notebooks (In Order)
  - Data Collection
    - Adulting_DataCollection.ipynb
    - Teenagers_DataCollection.ipynb
  - Preprocessing
    - Preprocessing.ipynb
  - Modeling
    - KNN.ipynb
    - NaiveBayes.ipynb

## Workflow
1. Data Collection
    - Using PushShift API.
    - Collection of 5,000 posts per subreddit.    
2. Data Cleaning & EDA
    - Combine title and body of reddit post to create one column "user_post".
    - Remove null posts.    
3. Preprocessing & Modeling
    - Adding stop words and combining with English stop words.
    - Balancing of classes (51% Teenagers, 49% Adults).
    - Naïve Bayes and KNN Models
      - Two Transformers : CountVectorizer and TfidfVectorizer    
4. Evaluation
    - Present best scoring model.
    - Compare training/testing scores between each model.    
5. Conclusions & Recommendations
    - Naïve Bayes was my best scoring model.
    - TfidfVectorizer scored best on Naïve Bayes model.
    - CountVectorizer scored best on KNN model.
    
## Summary of Analysis
From the data that was pulled, and after the creation of visualizations, there seemed to be a noticeable difference between the words that were used by Teenagers versus Adults. It seems that teenagers seemed to talk a lot about relationships, school, love, etc. When analyzing the most common words for adults, we see that they talk most about stress factors, such as work, rent, money, apartments, etc. This is a prediction that I had going in because most of the most occuring words in the adults subreddit were things that teenagers did not have to worry about, as most teenagers are supported by their families until they are adults.

![Teenager Common Words](https://github.com/nolanarendt/Reddit-NLP/blob/main/images/teenagers_common_words.png)

![Adult Common Words](https://github.com/nolanarendt/Reddit-NLP/blob/main/images/adults_common_words.png)

Based off of the data that I collected from subreddits Teenagers and Adulting, my best performing model had a 0.947 Training Score and a 0.925 Testing Score. Reflecting on these scores, I believe that my model was successful in accurately predicting what subreddit a post was from by analyzing the words that were used. When looking at misclassifications, I saw that we had a specificity score of 92.9%, and only 139 misclassifications. Of the words that were misclassified, it was clear that they are common words that are relevant no matter what age you are, so this is explainable.

![Misclassifications](https://github.com/nolanarendt/Reddit-NLP/blob/main/images/misclassified_words.png)

## Conclusion & Recommendations 
I believe that this model would be very effective for any marketing company that is looking to target users on a social media platform such as reddit. Through the use of my model, a company would be able to identify which users are teenagers, and advertise the most popular items that teenagers like. Likewise, a company would be able to identify adults, and market more adult specific items. Most adults also have an income, therefore, they would be more likely to spend money on a given item. I would recommend using a Naive Bayes model with a TfidfVectorizer to accurately predict what subreddit a post is from. Removing features, gathering more data, and feature engineering could possibly reduce overfitting.

For future research, I would dive into more age specific subreddits, such as different generations, different decades, and so on. I think my model would score a bit lower because of the amount of classes we would be trying to differentiate between, but over time I think we could improve our score by collecting data continously. Next, I would like to include comments into my analysis and see if comments have any value in predicting a comments subreddit. The one issue I had with comments was that any single post could have thousands of comments, and the data collection of those would take a large amount of time. Lastly, I would like to look at geographical common words and using them to compare the difference between teenagers on the east coast versus the west coast, and same for adults. Going forward, I also think that I could add in more stopwords and see how many misclassifications I would run in to, and maybe remove stopwords to see if my model would have less misclassifications.

## Sources
  1. Subreddit Adulting
 - https://www.reddit.com/r/Adulting/
  2. Subreddit Teenagers
 - https://www.reddit.com/r/Teenagers/
  3. PushShift API
 - https://github.com/pushshift/api
