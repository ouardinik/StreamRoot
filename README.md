# StreamRoot

Exercice Streamroot :

1- For this exercise I used Python (version 2 .7).  I used the pandas library for the data frame manipulation and matplotlib and seabron for the data visualization part. I focused all my work on one single Jupyter Notebook that provides an interactive environement for visualization of plots. ( You will find this notebook in the github under the name Streamroot.ipynb)

First, I printed out the dataframe and started exploring it. Two different tools were useful to extract knowledge from the data and identify simple patterns in the data :
•	The first one is the the seaborn object seaborn.countplot that counts the number of instances with respect to one attribute of the dataframe and displays it in a histogram. Since each line refers to a unique user that can have a different isp, brower or stream number, this was a very useful tool to visualize the distribution of the users in different conditions.
•	Metrics and percentages.

I - GENRAL ANALYSIS :

In this first part, I split the data in subset and visualized it. Visualizing the data early was useful  to me, as it allows me to get a sense of the data, and gives me ideas  for more complex analysis.

![Figure1](/figure1.png)
![Figure1](/figure2.png)

Thanks to these plots we can quickly get some preliminary observations :
•	The streams #1, 3 and 7 are the busiest (number of users). The stream #6 is the least used.
•	We can seperate the Internet Service Providers in two classes. The busy ones are BTP, Arange and Fro while Datch Telcam and Olga have a lower use rate
•	Same thing for the browsers : Iron and EarthWolf are heavily used while Vectrice and Swamp account for less than 50,000 number of users which is less than the tenth of the total number of users. ( I asked Igor, and he confirmed that the the ISP or Streamroot have no influence on the choice of the browser, but we can hypothesize on the reasons of this difference)
•	The total number of user is 534,954. Among those users, 485,753 are connected to streamroot’s backend. We can also notice that if a user is not connected, that the the data downloaded through p2p is always zero. « Not connected » users can only downlad through cdn, thus directly using the isp’s line. However, if a user is connected it does not necessarly means that he is downloading through peer to peer : 10% of the users are not connected but 35% are downloading only through cdn. A user could be on a stream with not enough users trying access to same content ,thus limiting the p2p shares.


II- Further Analysis

In this part, I selected smaller subsets of the data fame and went through a more specific analysis.

1-	Streams :

Percentage of connected users for each streams 

![Figure1](/figure3.png)

The stream number 7 immediately stands out as all the other streams have high percentages of connected the users. During the general analysis, we saw that the stream #7 was the third busiest  stream. Let’s take a closer look.

![Figure1](/figure4.png)

Datch Telecam provides for the majority of the users in stream7 which means that the number of connected users for that isp might be low as well. Indeed, 80% of Datch telecam users are not connected to streamroot backend. Even worse, only 0.43% of the users are actually receiving data through p2p. These elements make Datch telecam a very strategic target for streamroot in the hunt for potential clients. 


2-	Connection to the back end :

To confirm the observations made for stream #7, let’s have a look at the distribution of  non connected of users over the Internet Service Providers and the Browsers. 

![Figure1](/figure5.png)

This plot rapidly confirms our previous observations for Datch Telecam. Morover Once again ce can observe that the two browsers Vectrice and Swamp have very low levels of connected users. The choice of the browser is solely based on the user’s preference.


3-	Data :
In this section,  I will focus on the size of data downloaded by the users to show the benefits of the p2p. If there’s one, it should reflect on the data. Indeed, I am assuming that combining cdn and peer to peer should allow users to download larger siwe of data ( better quality videos)

One simple way to get a sense of what the peer to peer brings to the table is to compute the average size of the data downloaded by connected and not connected users. Connected users download in average around 3 times more data (20 Mo) than the non connected users (6 Mo). 

In this last part, we will be only interested in the large amount the data downloaded. I selected two subset of dataset : the first subset corresponds to all the users who downloaded more than 100Mo of data in total through peer to peer and cdn. The second corresponds to the users who downloaded more than 100Mo only through cdn. Once again, I plotted the distribution of both set of users with respect to ISPs and the browsers :


![Figure1](/figure6.png)
![Figure1](/figure7.png)

From the first two figures, we can immediately see that the concentration of users that downloaded more than 100 Mo of data is a lot higher for the users who are using peer to peer on top of the cdn. Less than 10,000 users downloaded more than 100 Mo of data only through CDN.  We can also notice :
•	That BTP as the highest rate of users (around 17500). After verification, this ISP also has the highest rate of connected users (99.9%)
•	Unsurprisingly, Datch Telecam (which had the lowest rate of connected users), also has the lowest rate of voluminous data downloaded by the users. 
These 2 observations definitely prove the correlation between the use of peer to peer and the size of the data that a user can download which is also related to the quality of the content since the files are videos.
•	Olga, another ISP also has a low rate of users according to the first figure. However, 92% of its users are connected to the back-end, and 34% of the users are actually downloading through peer to peer. On the second figure, we can also see Olga also has the lowest rate of users for the users downloading through cdn only. We can hypothetize that the leased lines of Olga do not allow high speed downloads, or the transfer of important sizes of data.

For the browsers, we can recognize the same two groups we identified during the general analysis. EarthWolf and Iron were the most used browsers and the figure 3 might explain why. These two browsers probably allow users to download better quality videos. EarthWolf and Iron both have the highest rate of users downloading through p2p and cdn ( > 60%) , so it might also be because those browers are suited for peer to peer sharing. Vectrice for instance, has less tha 1% of users downloading through p2p. 





