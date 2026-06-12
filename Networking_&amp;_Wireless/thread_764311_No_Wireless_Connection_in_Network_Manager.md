---
title: "No Wireless Connection in Network Manager"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by zer0knowhow on 2008-04-23
I just recently installed Ubuntu and have been trying to set up an Internet connection, but have been having troubles.  

First off, I use a Linksys Wireless USB (I believe the model is WUSB54GSC) and I'm using a laptop (HP Pavilion dv2125nr).  I've read other forums that have helped to get the wireless connection working, but my initial problem is that there is no option for wireless network in my Network Manager.  It only shows me "wired connection" and "modem."  How do I get it to give me the option of having a wireless connection?

---

### Post by asanti on 2008-04-23
same issue here.  i have a belkin network card i would like to install the driver also.  and there is nothing in the manager. i would also like to piggy back of your request.

---

### Post by Chbuntu on 2008-06-06
bump

---

### Post by mringer on 2008-06-07
I had a similar problem (with diffferent h-ware). I believe that (on my PC)
the cause was that the S-ware was unable to drive the card (one of these
*** beloved *** Broadcom cards). Try

sudo lshw -C network

If the card is listed as UNCLAIMED  I believe that means no device driver.

I dont know what to do about this. If you read the forum talk about 
broadcom cards, various people have produced incompatible solutions.
What worked for me (part way) was  ndiswrapper, see

[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

---

