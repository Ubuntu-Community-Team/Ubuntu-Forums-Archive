---
title: "Wireless Madness"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by clemkonan on 2010-09-02
Can I please get a series of instructions that will allow me to install a D-link wireless N 150 USB adapter so that I can connect remotely to the internet? I am using the most recent version of Ubuntu.

Do I install the drivers - I assume they would be useful for windows only
If I need Ndiswrapper I need instructions.

A lot of new non technical folks are being forced to go back to Bill Gates because this is where the rubber meets the road and the technical folks scratch they heads and head off in one direction wondering  "why  we cannot get something so simple" and Bill says "not to worry you should not have left in the first place , see how simple I make life for you"

Sorry but its the truth!

---

### Post by dca on 2010-09-02
What you're looking for is what chipset the wireless adapter uses (Marvell, Ralink, Broadcom, Intel, etc)
 
When plugged in to computer, try sudo lsusb in Terminal and see if it references chipset...
 
...from there, once chipset is discovered, you should be able to search forums for a how-to.

---

### Post by Jazzy_Jeff on 2010-09-02
> **clemkonan said:**
> Can I please get a series of instructions that will allow me to install a D-link wireless N 150 USB adapter so that I can connect remotely to the internet? I am using the most recent version of Ubuntu.

Do I install the drivers - I assume they would be useful for windows only
If I need Ndiswrapper I need instructions.

A lot of new non technical folks are being forced to go back to Bill Gates because this is where the rubber meets the road and the technical folks scratch they heads and head off in one direction wondering  "why  we cannot get something so simple" and Bill says "not to worry you should not have left in the first place , see how simple I make life for you"

Sorry but its the truth!

It is simple if you buy hardware that has support for Linux. When I buy any new item for my computer I always check for this. 

Most of the time it does not take much to get your wireless up and running. It just takes asking a question here on the forums and then following the instructions.

---

### Post by bkratz on 2010-09-02
It appears to actually be the DWA-125.

If when you do your lsusb you find that the following ID is determined ( usb.id of [COLOR="Red"]07d1:3c0d[/COLOR] ) here is an excellent thread to look at 

[http://art.ubuntuforums.org/showthread.php?t=1425564&page=4](http://art.ubuntuforums.org/showthread.php?t=1425564&page=4)

Especially post 37.

---

### Post by clemkonan on 2010-09-02
Thanks I missed it  is DWA-125. I will run lsusb from terminal and see what I get

---

