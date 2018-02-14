# Analysis of Road Traffic Fine Management Process using Prom Lite

# Introduction

- This is a short analysis exploratory analysis of the event log of a Road Traffic Fine Management Process using Prom Lite.  

- The data consist of an event log, recording the processing of road traffic fines. 

- The task of this analysis is to deduct all the related information from the data in the event log.

# Data Acquisition

- The data is already in a proper format and ready to use in Prom Lite. 

- There is no need to prepare the data before the analysis. 

# Dataset

- First, we have to import our data into Prom Lite by simply using the import function.

- The data which we have imported is in CSV format, so first we have to convert that CSV format to XES format. 

- Pom Lite supports importing data files which adhere to the XES standard. 

- We can simply use a plugin (Convert CSV to XES) which converts CSV to XES. After converting we will get XES event log summary.

# Data Exploration

### Event log visualization: Fig 1

![alt text](https://github.com/rahulbhat44/Process-Mining-using-Prom-Lite/blob/master/Images/Figure_1.png "Description goes here")

- In the above visualization, we can see that there are 150370 cases. These cases are the total number of fines which are processed.  

- There are total 561470 events, where 2 is the minimum and 20 is the maximum events processed per case. 

- We have 11 event classes in our dataset and there is only 1 type of event. 

- There are between 2 and 10 different event classes per case.

We can also go to the summary option on the left-hand side of the visualisation panel and check the summary of the dataset. 

### Summary of Event Log: Fig 2

![alt text](https://github.com/rahulbhat44/Process-Mining-using-Prom-Lite/blob/master/Images/summary.png)

In the above image, we can see that detailed summary of the dataset such as how many fines are created, how many payments are done, how many penalties are added and how many have appealed to judge etc. 

# Data Analysis using Visualisation

let's do some data analysis using some visualization in Prom Lite. let's see what we will find from visualizing the dataset.

Let's go step by step in the list of visualization in Prom Lite and see what we will find. So, the first in the list is "explore event log (trace variant) visualization". Below you can see the visualization. 

### Explore Event Log (trace variant) Visualization: Fig 3

![alt text](https://github.com/rahulbhat44/Process-Mining-using-Prom-Lite/blob/master/Images/Fig_3.png)

The above visualization shows the first 9 traces and below we can see the description. The description shows the total number of traces, events, classes, attributes, variants and events per trace.  

### From the visualization we can see that:

- The data has been collected between 2000 and 2013, it means we have data of fourteen years.

- The first five traces covered about 90% of cases and none of them went to court. 

- We can also see that in the first nine traces about 44% of cases end with payment. 

- In the first nine traces, 53.79% cases end in non-payment. 

- 38,57% went for credit collection. 

- The question which comes in mind is what about the cases which are ended in non-payment, are these cases lost or still in progress. 

- We can see that from the visualization that the payments can also be done in instalments. 

- Penalties are also added for late payment and the important thing is after adding penalty 15% payments are quickly done.

- The most of the cases ended with "payment" and "send to credit collection". 

- We can see that in the second last row i.e 8th row that the event ended with "send appeal to prefecture" and we know that this can not be the end event of a trace, there should be an event "payment" or "send to credit collection" so from this we can conclude that 2,497 cases are still pending. 

### Dotted Chart with Color Attribute: Index in Trace: Fig 4

Next visualization is a dotted chart in which the X-axis is a timestamp and Y-axis is event name and the colour represents the index. Below you can see that visualization. 

![alt text](https://github.com/rahulbhat44/Process-Mining-using-Prom-Lite/blob/master/Images/Fig_5.png)

- The first thing we can notice from the visualization is that the data is from 2000 to 2013.

- There are 11 event types and If we see the visualizations carefully, we can see that these events typically are in a particular order, we can also notice this ordered events from the last visualization i.e Fig 3.

The order is:

### 1st Order

1: create fine
2: send fine
3: insert fine notification
4: add penalty 
5: payment

### 2nd Order

6: send appeal to prefecture
7: insert date appeal to prefecture
8: receive results appeal to prefecture
9: notify results appeal to offender
10: appeal to judge

### 3rd Order
11: send for credit collection

- The events are happening in the ordered show above. 

- We can see that there is a solid line for the events 1, 2 and 3. From this solid line, we can say that these events occur almost everytime. 

- For the events 1, 2 and 3, we can also see that there is no mix up i.e no other lines are mixed with their lines  (multicoloured) because they have constant colour. As we have mentioned above that the colour represents the index of the event in the trace i.e the first, second, third, etc. event in the trace. So, it means that these three events are processed in a fixed sequence. 

- The fourth event whose colour is solid after the events 1, 2 and 3 are "add penalty" which is event number 4. We can say that the event 4 "add penalty also" occurs more frequently because of the solid line. 

- We have also discussed and seen above in fig 3 that the payment is done (event 5) soon after adding the penalty. So we can say that the most fines are paid in the end and these five events are in order. Probably payment is the last step in most traces.

- We can also see that the event "send for credit collection" only contains few dots, it means "send for credit collection" is happening very rarely. From this, we can also conclude that the payment is occurring frequently because if the payment is not done then only the event send for credit collection occurs.  

### Dotted Chart with Colour Attribute: Event name: Fig 5

We can also see the visualization without multicolour. A single colour for each event. This will happen if we colour by event name shown below. 

![alt text](https://github.com/rahulbhat44/Process-Mining-using-Prom-Lite/blob/master/Images/Fig_4.png)

In the above figure, we can see which colour represents which event.

###  Dotted Chart with Colour Attribute: Event name: Fig 6

In the visualization below we changed the Y-axis to index by time and the rest is same as the above dotted chart. 

![alt text](https://github.com/rahulbhat44/Process-Mining-using-Prom-Lite/blob/master/Images/Fig_6.png)

- The index position 0 shows the event 1 (create fine). 

- The index position 1 shows that after creating a fine the event payment (5) is done or after the event send fine (3) the event payment (5) soon happens. 

- this shows that some fines are paid early i.e 1 -> 5 and 1 -> 2 -> 5. 

- The index position 2 shows that after the event insert fine notification (3) the payment is done and so on. 
We can see that events are occurring in the same order we shown above (1 -> 2 -> 3 -> 4 -> 5).

- We can also figure out that there are two types of cases:

(a) Cases without appeal i.e events 1,2,3,4 and 5. 
(b) Cases with the appeal because where there is appeal the events are occurring in this way i.e 6,7,8,9 and 10. 

- We have already discussed above in the fig. 1 that the maximum number of events per case is 20 and the above figure shows that the maximum index goes until 12 only where two cases happened but no cases occur after the index 12. 

- We can also notice that which is quite strange is that there are no cases at index 10 and 11 but two cases at index 12.

- From this we can assume that this visualization doesn't show the whole dataset, it is possible that this visualization shows only the sample dataset. 

### Dotted chart: trace processing in time (colour represents event name)

![alt text](https://github.com/rahulbhat44/Process-Mining-using-Prom-Lite/blob/master/Images/Fig_14.png)

- We know that when the cases are entered and are processed there would be line around the main diagonal and a diagonal line is clearly visible here, but there is much more.

- The dark green vertical stripes are credit collection events, that are performed once each year.

- We can see that there are many blue dots in the year 2012. These dots are "send appeal to prefecture". 


### Fuzzy process model - Fig 7

We have created a fuzzy model by using a plug-in "mine for fuzzy model" and we got the figure shown below. Let's see what this model is showing.

![alt text](https://github.com/rahulbhat44/Process-Mining-using-Prom-Lite/blob/master/Images/Fig_7.png)

- We can see that the events are ordered as (create fine -> send fine -> Insert fine notification -> Add penalty) but according to our analysis from the above figures, this order should end with an event "Payment". But this model doesn't show a direct link to Payment.  

- There is one more unusual thing happening in the model and that is there is a direct link between create fine and appeal to judge, which is not possible. Appeal to judge can only occur after the event "send appeal to prefecture". 

- An event "Notify results Appeal to offender" is also missing which should be the event before "Appeal to Judge". 

- We discussed above that an event "send appeal to prefecture" cannot be the end stage, the end event should be payment or send for credit collection. But in this model, we found that there is a payment loop and a transition to an event "send for credit collection".

### mine Petri net with inductive miner - Fig 8

We created a "mine Petri net with inductive miner" visualization which produced a more detailed preliminary model and has very good features. The figure is shown below. 

![alt text](https://github.com/rahulbhat44/Process-Mining-using-Prom-Lite/blob/master/Images/Fig_8.png)

- We can see that there are a lot of black boxes in the figure and these black boxes are parallel to every event except create fine and add penalty.

- The black boxes parallel to an event means that event can be skipped or bypassed. So, it means each and every event can be bypassed except two events i.e create fine and add penalty. 

- This figure also shows that there is no connection between add penalty and payment and according to our analysis from the above visualizations that around 10% of the cases ended from add penalty to payment. 

- We can also see that there is no loop around payment, it means that payment can only happen once per trace. 

### Conformance Analysis - Fig 9

We created a conformance analysis by using a plugin "replay a log on Petri-net for Conformance Analysis" which helps us to check how well our Petri-net can reproduce the traces in the input event-log. 

![alt text](https://github.com/rahulbhat44/Process-Mining-using-Prom-Lite/blob/master/Images/Fig_9.png)

Above figure, we can see our conformance analysis which shows the global statistics for the match.

![alt text](https://github.com/rahulbhat44/Process-Mining-using-Prom-Lite/blob/master/Images/Fig_10.png)

The traces in the event-log and the Petri-net match very well, the agreement is about 99.1%.

### Performance Analysis - Fig 10

We also produced a performance analysis of a Petri model by using a plug-in "replay a log on a Petri-net for performance/conformance analysis" shown below.

![alt text](https://github.com/rahulbhat44/Process-Mining-using-Prom-Lite/blob/master/Images/Fig_11.png)

Let's see the global statistics of our performance model.

- We can see that the average case Throughput time is 11.39 months.

- We can also see that the minimum time is 0 months, from this we can conclude that some cases probably dismissed in the early stage i.e at first step.

- Third, we see that some cases take 145.73 months. 

- Forth we can see that out of 150370 cases 8179 cases are not perfectly fitting i.e 1.8% cases.

- In the above figure, we can see that one activity and one node is coloured red, this means that there is a possible performance problem.

### Performance statistics for an event "send for credit collection" shown below.

![alt text](https://github.com/rahulbhat44/Process-Mining-using-Prom-Lite/blob/master/Images/Fig_12.png)

- We can see that the average waiting time is 17.52 months, but some cases take 111.03 months.

- The waiting time is the time it takes the credit collecting agency to collect. Many fines could have been collected much earlier i.e 1.13 months.
