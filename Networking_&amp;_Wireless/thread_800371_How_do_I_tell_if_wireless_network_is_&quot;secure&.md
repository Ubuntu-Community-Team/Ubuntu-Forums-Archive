---
title: "How do I tell if wireless network is &quot;secure&quot;?"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by crash369 on 2008-05-19
In winXP, if I am connected to a wireless network, I can hover my mouse over the connection icon, and it will say something like "connected to <name> (secure)".

In hardy, when I hover over the nm-applet icon, it says something like "connection to network <name> (100%)" -- nothing about security.  looking at "connection information" shows me all the DNS stuff, but again, nothing about security.  ifconfig and iwconfig also come up blank.

So... is there any way I can check to see if my currently-connected wireless network is using some sort of security algorithm?

---

### Post by Monicker on 2008-05-19
If you connected to a wireless network without entering any WEP or WPA information, then it would have to be insecure.  

On Hardy I see a little blue icon next to any available networks which are secure.  If I attempt to connect to them, it tells me that encryption is required.  I do use WPA for my own router, and when I right click on Network Manager, I can see the type of security by selecting "Edit Wireless" and highlighting my SSID on the left.  It shows "WPA Personal" for my home wireless.

---

### Post by Deeta on 2008-05-19
@windows telling you networks are secure: I always need to lol if I see windows declaring Networks using WEP as 'secure' :D

Viewed from a security perspective it is a likely a good thing that it does not declare networks as 'secure' :D can only be a false sense of security one is lulled into :D

(Though WPA2 with a strong PSK is ok for home networks I guess :D

---

### Post by crash369 on 2008-05-19
The problem is that my school has several networks -- some secure and some not.  And since I can never remember which one's which based on SSID, it makes for a mess.

I guess I'll try to see if the names have little blue icons next to them :)

---

