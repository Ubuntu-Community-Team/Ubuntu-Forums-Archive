---
title: "Help Installing  QSTalker charting programm"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by Looey on 2011-06-05
:confused:
 
I am a new user , I installed Ubuntu 11.4 in last week. I installed qSTalker charting software, I also downloaded the TA-Lib packages. Here is the problem, candle stick signals are not being displayed, Bar charts, that portion of the programm is not working,
 
There are a few  good things, the stochastic indicators are working , Macd is working , price , (I can see all those indicators on my screen)
 
How do I get the main windows screen to display a chart .?
 
 
I would like to see candle sticks chart.!
I would like to see MOving averages .!
 
 
2. I would tried to install AIOTRADE , with the help OF WINEHQ. It does not work.

---

### Post by Old_Grey_Wolf on 2011-06-05
I'm using Qtstalker with Ubuntu 10.04. I have a screenshot attached that may give you a clue. Note what buttons are pressed; such as, Working with charts.

Edit: I also downloaded Qtstalker from the Ubuntu repos. The reason I mention the Ubuntu repos is that I didn't have to install TA-Lib packages separately. 

Edit: I tried to check it out with 11.04; however, my virtual machine of 11.04 just keeps crashing and won't boot. :)

---

### Post by Looey on 2011-06-05
:cry:

I would like to say thank you for responding. My version of qstalker is missing the candle stick section. I can not find it on the tool bar. I would like to ask you if you know or anyone in this forum knows how to add the section where the candle sticks are supposed to be.  I have Daily= D W= weekly M= Monthly then I have the paper trading section. and that is it . 
Also thank you for supplying the photo. The software is missing something parts. I down loaded the  software for the Ubuntu software center.

best regards.

---

### Post by Looey on 2011-06-06
Is there any way that I c oud run this program in Ubuntu 11.4. Help:P

---

### Post by Old_Grey_Wolf on 2011-06-06
You definitely have a newer version of Qtstalker than I have. Mine is from April 2010 (Ubuntu 10.04), one drawback of staying with LTS releases thus older software versions.

The current Qtstalker user manual starts here [http://qtstalker.sourceforge.net/toc.html](http://qtstalker.sourceforge.net/toc.html). 

One page of interest is the use of a Qtstalker repository at [http://www.zwets.com/qtstalker/](http://www.zwets.com/qtstalker/).

I normally wouldn't just reference a manual; however, I don't have the version of Qtstalker you have, and I doubt very many people on this forum use Qtstalker. It is for technical analysis of stock trends and oscillators similar to Metastock, Supercharts, and Tradestation; which, are not used by most of the average non-professional stock investors. Looking at polls, where I can get some idea of the demographic of the forum users, I don't think that most people on this form are invested enough in the stock market to know what I am talking about. This reduces the likelihood that you will find a solution on this forum; however, someone may show up to surprise me.

---

### Post by Old_Grey_Wolf on 2011-06-06
> **Looey said:**
> Is there any way that I c oud run this program in Ubuntu 11.4. Help:P

Just a passing thought, I doubt it will make any difference, but have you tried running Qtstalker using a Classic Gnome session rather than Unity?

---

### Post by Looey on 2011-06-07
I un-installed qstalker, Here is what happened as I was trying to re-install , I got the message saying the Dependencies could not be RESolve!!! so as of right now I am not able to re-install ERROR Message. There needs to be an update for ubuntu 11.4:(:(:(:(:(:(
I would like to thank you for responding to my messages. you are of great help to this community , I wish there were more human beings like you.
!
Best Regards,

---

### Post by jtarin on 2011-06-07
> **Looey said:**
> 
I would like to thank you for responding to my messages. you are of great help to this community , I wish there were more human beings like you.
!
Best Regards,Yes I myself wish there were more human beings like this. There are not enough  QSTalker users in this forum.:p

---

### Post by Old_Grey_Wolf on 2011-06-07
> **Looey said:**
> I un-installed qstalker, Here is what happened as I was trying to re-install , I got the message saying the Dependencies could not be RESolve!!! so as of right now I am not able to re-install ERROR Message. There needs to be an update for ubuntu 11.4:(:(:(:(:(:(
I would like to thank you for responding to my messages. you are of great help to this community , I wish there were more human beings like you.
!
Best Regards,

If you post the error with the dependencies, then someone my be able to help you with installing the packages that Qtstalker has dependencies on.

---

### Post by Looey on 2011-06-07
Problem reads : not able to download packages

               check your internet connection 


solutions pleass :(:(

---

### Post by Old_Grey_Wolf on 2011-06-08
> **Looey said:**
> Problem reads : not able to download packages

               check your internet connection 


solutions pleass :(:(

That error suggest that you have a problem with the mirror you are downloading from or there is an error in the servers in your sources.list file; however, you posted "I got the message saying the Dependencies could not be RESolve *[I assume this is Resolved]*!!! "

If you can, post the errors from the sudo update and sudo upgrade commands showing the dependency errors so that someone can help you resolve the dependencies.

---

### Post by Looey on 2011-06-11
I need help I need to delete the shared library LIBQSTALKERO and I also need to Delete LIBQTSTAKERO-DEV,. I do not know how to delete a shared library. please Help!! thank you . :p:p:p

---

### Post by Looey on 2011-06-12
I was able to re-install Qtstalker , from what I can see the portion that was missing on the main tool bar is working Candle stick, line :p :p :p I clicked on the quote portion of the software, I added the following symbols GOOG IBM Veco, JNPR. The update was successful, MY question is how do I open a chart in the software, The section where the chart should be is one big blue screen, Thank you for your participation.

---

### Post by Looey on 2011-06-13
I would like to thank everyone in here for helping me with the installation. The program is working great!! I can see the charts, candle. 
A big thanks to Old_Wolf for guiding me on the right direction. You have  been of great help. The program is working on my computer now.:D:D:D

:popcorn: Thank you all.

---

### Post by Looey on 2011-07-03
> **Old_Gray_Wolf said:**
> I'm using Qtstalker with Ubuntu 10.04. I have a screenshot attached that may give you a clue. Note what buttons are pressed; such as, Working with charts.

Edit: I also downloaded Qtstalker from the Ubuntu repos. The reason I mention the Ubuntu repos is that I didn't have to install TA-Lib packages separately. 

Edit: I tried to check it out with 11.04; however, my virtual machine of 11.04 just keeps crashing and won't boot. :)
How do I place  a moving average line on the chart itself?

---

### Post by Old_Grey_Wolf on 2011-07-03
> **Looey said:**
> How do I place  a moving average line on the chart itself?

I select "New Indicator" from the Edit menu then select "MA" for the "Indicator" and "Main" for the "Plot Type" in the window that opens. Then I have to select the moving average "Period" like 21 if I want 21 days.

---

### Post by Old_Grey_Wolf on 2011-07-03
One more thing, after the Indicator is added to the Main Chart you can click on the icon that looks like the square root of *X* [[IMG]http://upload.wikimedia.org/math/2/d/a/2daa5f53f1bccd91041fe1506cc9f47e.png[/IMG]]. It will display the Indicators overlayed on the Main Chart. You can turn each indicator on or off by double clicking it. The icon will also display the Stacked indicators (Plot Type = Stacked), or the ones in the rows at the bottom of the display. Double clicking those will display or hide the Stacked indicators as well. You will see the Stacked indicators in the screenshot I attached 4 weeks ago; such as, the MACD indicator at the very bottom of my screenshot. 

I haven't found a use for the Plot Type of Tabbed; however, you might. It makes something that looks like the Stacked indicators; however, you have to click on the tabs on the bottom of the display to see each of the indicators. I guess it saves screen space for people with small monitors, laptops, or netbooks.

Let me know if this is helpful.

Thanks.

---

### Post by Looey on 2011-07-04
Thank you very much for your help.! I have another question, The next question is about the fibonacci lines . How do I flip the fibonacci lines,around  for example  I would start by flipping the 100% to the bottom from the low. let's say the low is zero. I would like to place the 100% next to the low (lowest stock price) and move it up. On a upward direction I would like to see: starting from the lowest low first 100% 61.8% 50% 38.2% , I will use it to calculate the Gartley pattern.  thank you very much . :popcorn::popcorn:

---

### Post by Old_Grey_Wolf on 2011-07-04
Try clicking the [[IMG]http://upload.wikimedia.org/math/2/d/a/2daa5f53f1bccd91041fe1506cc9f47e.png[/IMG]] icon; then right click on the indicator and select Edit Indicator. See if it will let you edit it to get what you want. I doubt it though.

Edit, that won't work because the fibonacci lines do not show up as indicators.

---

### Post by Looey on 2011-07-04
Yes , I have one more question. I having problems with the time Frames . How do I set it up for the 3 months time periods the 6 months and 1 years. I am not sure as to how to set my time frame periods. Thank you:popcorn:

---

### Post by Old_Grey_Wolf on 2011-07-04
> **Looey said:**
> Yes , I have one more question. I having problems with the time Frames . How do I set it up for the 3 months time periods the 6 months and 1 years. I am not sure as to how to set my time frame periods. Thank you:popcorn:

I really  don't know what you are asking about with this one. There is a manual for Qtstalker. This is a support forum for Ubuntu so we really are off topic for this forum. Helping you get Qtstalker working on Ubuntu was OK.

---

