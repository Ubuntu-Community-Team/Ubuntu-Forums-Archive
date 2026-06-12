---
title: "Lossing connection after an hour uptime"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by Blackie_Chan on 2007-01-04
I use a network adapter (D-Link DWL-G122) to connect to my router. The adapter has 2 LED on it: Act (flashes when there's internet activity) and Lnk (which is on indicating there's a link to the router).  

The odd thing is after having my computer on for more than about an hour, the Lnk light turns off (so there's no connection to the router), and I can't access the internet. I have to restart my computer in order to get internet access again. 

I have a dual-boot machine (Ubuntu Dapper Drake and Windows XP), the problem doesn't happen in windows. 

Can someone tell me why the connection dies by itself? How can I fix the problem?

---

### Post by Fully216 on 2007-01-05
You might need to provide the way you connect you your router (example - ndiswrapper with my proxim wireless card).  Check iwconfig to see if there are any problems after the connection is dropped.

---

### Post by Blackie_Chan on 2007-04-30
Even though, I'm currently on Feisty Fawn, I still had the same problem. 
Until I disabled usb 2.0. See Feisty Fawn Ubuntu Guide. Apparently usb devices have an habit of disconnecting themselves.

---

