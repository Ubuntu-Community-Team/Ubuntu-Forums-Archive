---
title: "Samsung R730 and wifi"
date: 2014-07-07
forum: Networking &amp; Wireless
---

### Post by thepro2 on 2014-07-07
Ok guys first off , I am a Noob to ubuntu server. 

Now let me start off , so i have a Minecraft server i plan to install on the Ubuntu server. 

If you want the specs here you go : 

Laptop 

Samsung R730

Intel Core i3 (2 Cores)  @ 2.10 Ghz

Ram : 8gb

I am sure that is plenty enough to run the server.

Now i need to connect it to Wifi , that is what i plan hosting it off of. I have good internet @ 35 MBPS up And 25 MBPS down.
So can one of you nice people tell me how to connect it to Wifi ? It is not connected to internet at the moment and i can not connect it without Wifi.
By the way if i did not say it before This is a Ubuntu Server version 14.04 .

Thank you guys and sorry if i am not posting the right section :)

---

### Post by Vladlenin5000 on 2014-07-07
Hi, welcome.

You posted in the correct section. However, the forum users most likely to help you can be found at "Gaming & Leisure".

Now, before actually answering your question let me tell you that you can - and probably should - use the Ubuntu desktop instead of server. The server version is meant to run headless servers as in no graphical environment whatsoever. Using the desktop version gives you the same thing (minus a small detail not at all relevant for your project) and a desktop environment from which you can connect to wireless networks from a dropdown menu, as easy or even easier than in Windows. That depends, of course, on the WiFi card/USB dongle being correctly detected and using the proper driver. If not both server and desktop version will require the same troubleshooting but when up and running you'd still have to use command line to manually configure the connexion to a given wireless network in server version whereas you'd be doing it graphically in the desktop version.

---

### Post by mastablasta on 2014-07-07
of all the specs you mentioned you didn't mention the most important one and that is the wi-fi chip. so which one is it? you may need to install drivers for it. oh and you will probably need a network manager to connect with it via wi-fi.

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

[http://ubuntuforums.org/showthread.php?t=2125242](http://ubuntuforums.org/showthread.php?t=2125242)

...

---

### Post by Bucky Ball on 2014-07-07
> **Vladlenin5000 said:**
> 

You posted in the correct section. However, the forum users most likely to help you can be found at "Gaming & Leisure".



This is a wifi issue and belongs here:

*Thread moved to **Networking & Wireless**.*

This will improve your chances of getting help and, as you're new, people will be gentle. Just ask if you don't understand something. ;)

Please open a terminal and provide us with the output of:

```
sudo lshw -C network
```

(Actually, you've probably only got a terminal.) From what you're saying you can't access wired ethernet? Make things a LOT easier if you can. We'll wait to see the details of what you already have, though.

---

### Post by thepro2 on 2014-07-07
> **mastablasta said:**
> of all the specs you mentioned you didn't mention the most important one and that is the wi-fi chip. so which one is it? you may need to install drivers for it. oh and you will probably need a network manager to connect with it via wi-fi.

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

[http://ubuntuforums.org/showthread.php?t=2125242](http://ubuntuforums.org/showthread.php?t=2125242)

...

My Chip is A Qualcomm Atheros AR9285 Wireless network adapter.

I have heard a few bad things about it but i do not care :p

---

### Post by thepro2 on 2014-07-07
> **Vladlenin5000 said:**
> Hi, welcome.

You posted in the correct section. However, the forum users most likely to help you can be found at "Gaming & Leisure".

Now, before actually answering your question let me tell you that you can - and probably should - use the Ubuntu desktop instead of server. The server version is meant to run headless servers as in no graphical environment whatsoever. Using the desktop version gives you the same thing (minus a small detail not at all relevant for your project) and a desktop environment from which you can connect to wireless networks from a dropdown menu, as easy or even easier than in Windows. That depends, of course, on the WiFi card/USB dongle being correctly detected and using the proper driver. If not both server and desktop version will require the same troubleshooting but when up and running you'd still have to use command line to manually configure the connexion to a given wireless network in server version whereas you'd be doing it graphically in the desktop version.

I am using the server version because i heard it can give a little boost in performance.

---

### Post by Vladlenin5000 on 2014-07-07
> **thepro2 said:**
> I am using the server version because i heard it can give a little boost in performance.

I'm sure you heard it as it is quite often repeated by performance obsessed people, the same ones that turn off each and every one of the graphical environment enhancements standard in Windows Vista/Seven - making it look even worse than Windows 2000 - just to squeeze out a couple of FPS more. The same logic doesn't apply to a game server and for your specific project I seriously doubt you can notice any difference provided you have 2GB of RAM or more.

However I must concede that a quick Google search about it turned out many results/tutorials where people are indeed using server. So, from now on just ignore my ramblings, keep the server and focus on getting your wifi up an running. Everything else should be straightforward.

---

### Post by varunendra on 2014-07-07
> **thepro2 said:**
> My Chip is A Qualcomm Atheros AR9285 Wireless network adapter.

I have heard a few bad things about it but i do not care :p

I have that very same wireless card in my Asus X54C laptop, and it is fantastic. Only its driver has become a little bad in recent kernel versions. I am still on kernel 3.2.0-36, and the driver in it (ath9k) is working great!

As for getting connected to Internet without GUI, I think the links provided by mastablasta, especially [this]("http://ubuntuforums.org/showthread.php?t=2125242") one, should be sufficient. :)

---

### Post by Bucky Ball on 2014-07-07
> **varunendra said:**
> 

As for getting connected to Internet without GUI, I think the links provided by mastablasta, especially [this]("http://ubuntuforums.org/showthread.php?t=2125242") one, should be sufficient. :)

Indeed. Read chilli555's instructions carefully and try them.

---

