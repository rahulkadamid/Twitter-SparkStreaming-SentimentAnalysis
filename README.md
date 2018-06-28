# Twitter-SparkStreaming-SentimentAnalysis

Real time streaming twitter sentiment analysis application built using Twitter | Spark Streaming | Redis | Java Swing

</br>

## Introduction

Sentiment Analysis is the process of determining whether a piece of writing is positive, negative or neutral. It's also known as opinion mining, deriving the opinion or attitude of a speaker. knowing this, companies and brands can leverage the information to alter their communication strategy or to recognize events that may need to be addressed before it becomes a full-blown crisis. On the other hand, companies can, in various ways, capitalize on things that seem to be creating more positive buzz within their target audience.

Sentiment Analysis answers to questions like below:

  How do your customers feel about your brand?

  What is the opinion about your brand against your competitors?

  What are the latest trends related to your brand?


Need more information about sentiment click below URL

https://www.lexalytics.com/technology/sentiment

</br>

## Goal

• The goal is to analyse and visualize sentiment of tweets in real-time on given trending topics while running the application. 

• The project was developed using Twitter 4j, Spark Streaming(Scala), Redis, Java Swing

</br>

## Architecture

![alt text](https://github.com/RepakaRamateja/Twitter-SparkStreaming-SentimentAnalysis/blob/master/images/arch.png)


• Application streams data from twitter using Spark Streaming and then sends them to another layer which uses spark MLlib (machine learning module) and 
  does classification machine learning module making use of broker redis to communicate with the dashboard (Java Swing application).

• Application acts like a pipeline for sentiment and emotion analysis of real time tweets of trending topics and also having a extra capability of view 
  the results of the sentiment analysis in a dashboard. 
  
</br>

## Technology stack

![alt text](https://github.com/RepakaRamateja/Twitter-SparkStreaming-SentimentAnalysis/blob/master/images/stack.png)


</br>    


<table>
<thead>
<tr>
<th>Area</th>
<th>Technology</th>
</tr>
</thead>
<tbody>
    <tr>
        <td>Front-End</td>
        <td> Java swing </td>
    </tr>
    <tr>
        <td>Cluster Computing Framework</td>
        <td>Apache Spark Streaming using Scala (extension of the core Spark API) </td>
    </tr>
    <tr>
        <td>Machine learning </td>
        <td>MLlib library (Apache Spark's scalable machine learning library)</td>
    </tr>
    <tr>
        <td>In-Memory Caching / Datastore</td>
        <td>Redis</td>
    </tr>
    <tr>
        <td>Other APIs Used</td>
        <td>Twitter streaming using Twitter 4j api</td>
    </tr>
</tbody>
</table>

</br>   

## Use Cases

Sentiment Analysis can be applied to variety of Use cases:

1) Predict the success of a political/social campaign

2) Decide whether to invest in a certain company

3) Targeted advertizing

4) Product and service review

5) Research in sociology and psychology

6) Discover how people feel about a particular topic

</br>

## Configuring Environment

</br>

Installation of Cloudera quickstart VM

Redis Data Store

Jar file stanford-corenlp-3.5.2-models.jar

After downloading jar file place it in spark-twitter-sentiment-analysis

Later Configuring Scala Runtime to Cloudera QuickStart VM

Watch the below video for more information 

https://www.youtube.com/watch?v=SFJsuo2XISs

Similarly add redis to the path as well

</br>

## Execution Instructions

start the redis server 

Command:

    redis-server


start the redis client

Command:

    redis-cli


subscribe to channel tweet_results

Command:

    SUBSCRIBE tweet_results



Navigate to the folder twitterstream-sent-app 

clean the package

Command:

    sbt clean package 



submit spark job

Command:

    spark-submit --packages org.apache.spark:spark-streaming-twitter_2.10:1.6.0,edu.stanford.nlp:stanford-corenlp:3.5.2,redis.clients:jedis:2.9.0 --jars ../stanford-corenlp-3.5.2-models.jar --class Main target/scala-2.10/twitter-streaming-and-sentiment-analysis-app_2.10-1.0.jar trending topic name

trending topic name can be any example cnn

Now in the redis client screen you can see streaming sentiments in real time (please refer to Screen shots)

clean and  build the dash board application 

import the project(twitter-analysis-dashboard) into netbeans or eclipse 

then clean and build the application

Finally execute the below command to view the dashboard by navigating to folder witter-analysis-dashboard

Command:

    java -jar target/twitter-analysis-dashboard-1.0-SNAPSHOT.jar


</br>

## Screen shots

Redis messages recieved from Mllib layer

![alt text](https://github.com/RepakaRamateja/Twitter-SparkStreaming-SentimentAnalysis/blob/master/images/redisresults.png)

</br>

Negative sentiments in dashboard

![alt text](https://github.com/RepakaRamateja/Twitter-SparkStreaming-SentimentAnalysis/blob/master/images/negative.png)

</br>

Neutral and Negative sentiments but not positive

![alt text](https://github.com/RepakaRamateja/Twitter-SparkStreaming-SentimentAnalysis/blob/master/images/nopostive.png)

</br>

Postive sentiments 

![alt text](https://github.com/RepakaRamateja/Twitter-SparkStreaming-SentimentAnalysis/blob/master/images/positivestarted.png)

</br>

After some time

![alt text](https://github.com/RepakaRamateja/Twitter-SparkStreaming-SentimentAnalysis/blob/master/images/best.png)

![alt text](https://github.com/RepakaRamateja/Twitter-SparkStreaming-SentimentAnalysis/blob/master/images/final.png)

</br>

## Further Enhancements

we will persist the streamed data in data store from SparkStreaming

Build the classifer models by using the persisted data in data store

Now persist the model and look up the model when ml lib spark library starts up

spark streaming will use that loaded model to classify live streams

now positive negative and neutral sentiments are send to the message broker redis

Finally Java swing application will be consuming that messages from redis and modify the dashboard real time.







