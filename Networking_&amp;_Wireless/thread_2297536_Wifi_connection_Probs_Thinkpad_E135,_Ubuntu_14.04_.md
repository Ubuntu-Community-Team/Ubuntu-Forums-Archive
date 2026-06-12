---
title: "Wifi connection Probs Thinkpad E135, Ubuntu 14.04 (trusty) - i am lost."
date: 2015-10-04
forum: Networking &amp; Wireless
---

### Post by korn3 on 2015-10-04
Hello,

i am moving around quite much and have my Thinkpad E135 with me. Unfortunately i have more and more Wifi probs with it and i want to solve it. I am totally lost, where to begin and what to do. I got alot of "Connection Refusal" messages those days. I created the wireless-info.txt, read it and i don´t know, what to do with this information. Shall i post the full report here?

Following problems occur:

-No connection to the router. When password protection the router might accept the password, but does not let me in. Stucks in communication. If i restart the router, most of the time (not always) it works. <--- This problem i had alot during my travels!

-Connection to the router, but no internet (occured once).

-Connection to the router and Internet works fine. If i connect a second time, i get "connection refusal" errors. If i restart the router, everything works fine. I can not enter some websites, others work. Some are crashed. F.e.: No fotos are displayed in Facebook, but i can see the text and chat is working. <--- This problem is my actual issue. 

Usually i try to fix my problems by doing research. But Ubuntu (i am new, yes) is sometimes very complicated for me and i don´t understand much of what i am doing here. I think my Wifi configuration is somehow really bad. I hope i can find help here.

Cheers,

Korn

---

### Post by jeremy31 on 2015-10-04
You can paste the info from the wireless-script at paste.ubuntu.com and post the URL here

---

### Post by korn3 on 2015-10-04
Okay, done. 

[http://paste.ubuntu.com/12686260/](http://paste.ubuntu.com/12686260/)

Btw. now Internet seems to work again normal. I guess we might have some conflict with other devices. Can i get blocked out, when certain device are in the same network?

---

### Post by jeremy31 on 2015-10-04
paste the wireless-info.**txt** file the file you pasted is the script itself, there can be issues if two devices try to use the same IP on the wifi router

---

### Post by korn3 on 2015-10-04
Oh, i am so sorry. Thought both files where the same. Here is the right one.

[http://paste.ubuntu.com/12687401/](http://paste.ubuntu.com/12687401/)

---

### Post by korn3 on 2015-10-06
mhm....

---

### Post by jeremy31 on 2015-10-07
You do have an older version of the driver [http://packages.ubuntu.com/trusty-updates/amd64/bcmwl-kernel-source/download](http://packages.ubuntu.com/trusty-updates/amd64/bcmwl-kernel-source/download) might work better

---

### Post by korn3 on 2015-10-10
Okay, i installed this and observed my wifi during the last days. Can´t really say if it is better or worser. But the problem we got in the place here is, that some people connecting with their Tablets and Android Devices and this might cause some problem within the network. Is there any configuration i could do, to go around this?

I also observed in public networks, that my Wifi gets crashed as soon as some people enter and start surfing with their phone or tablet.....

---

### Post by korn3 on 2015-10-11
Okay, i got into our actual router and i can play a little with the options.

I am very sure, if my friend logs in Facebook Messenger with his Android phone, im gonna get problems and my connection for certain sites breaks down. (i observed this)

We have a linksys router. I have 3 different suggestions, but not sure. The router Security Options for Filter IDENT(Port 113) and Filter Multicast are enabled. maybe thats the problem? Also Mac Adress Clone is disabled. Could i enable/disable any of those options to overcome the problem?

Our wireless channel is on 2,437Ghz and we have no Mac Filter disabled. Also the Wifi has no password.

---

### Post by korn3 on 2015-10-12
I changed the DNS-Servers to 8.8.8.8 and 8.8.4.4. It is better now, but the problem still exists. 

Mac Address clone might help?

I am not sure what the heck i am doing here. Just try to figure something out. Any help appreciated. :)

---

