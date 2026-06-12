---
title: "Linksys wmp54g...works but reeealy slow!!!"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by asintu on 2008-05-22
I've installed 8.04 64bit and recognized my linksys WMP54G model right away. The only thing I had to do was to input the WEP 128bit hexadecimal password (to connect to my linksys router and internet)
The thing is my speed is much slower than in Windows (really slow firefox and about 20kbs when downloading the updates as compared to 170kbs in windows). 
Is this a known problem?
Any suggestions?
Thanx.

---

### Post by asintu on 2008-05-22
I have partially solved the problem. Apparently it's speed defaults to 1M so I ran this command: "sudo iwconfig wlan0 rate 54M". Two problems:
1. have to write this line everythime i start ubuntu
2. speed is going to max and then back down and then up again its' oscillating. Any ideas?

---

### Post by asintu on 2008-05-22
i have also ran this:
"sudo apt-get install linux-backports-modules-hardy-generic"
anybody know what it does?
seems like my internet is constant good speed now so everything is fine except it somehow disabled my video card driver.
is there a way to run the above line without influencing anything else besides the network card?

---

### Post by tir109xo on 2008-05-26
I've got the same problem on my ASUS WL107g card (RaLink 2500 chipset).  I can connect to my network, but my DL speeds are super slow (10 KiB/s).  Speed spikes as soon as I connect (~300 KiB/s) but then drops back to around 10.  Upload speeds are unaffected and are fine. 

You said that you by installing that you got it to download faster.  Was this the speed what you were expecting when you connected to your network?  Where did you learn of that install?

---

### Post by asintu on 2008-05-26
> **tir109xo said:**
> I've got the same problem on my ASUS WL107g card (RaLink 2500 chipset).  I can connect to my network, but my DL speeds are super slow (10 KiB/s).  Speed spikes as soon as I connect (~300 KiB/s) but then drops back to around 10.  Upload speeds are unaffected and are fine. 

You said that you by installing that you got it to download faster.  Was this the speed what you were expecting when you connected to your network?  Where did you learn of that install?

you have to change the rate from 1Mb/s to 54Mb/s. It defaults to 1 when ubuntu loads up. search up fro the command. i forgot it. Anyways, I got a wda-2320 d-link card and it's much more friendlier with ubuntu and pretty fast.

---

