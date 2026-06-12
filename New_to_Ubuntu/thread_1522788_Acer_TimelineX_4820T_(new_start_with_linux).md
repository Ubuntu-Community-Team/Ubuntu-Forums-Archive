---
title: "Acer TimelineX 4820T (new start with linux)"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by Elysius on 2010-07-02
Hi, I'm not very good at linux and just receive my new Acer TimelineX 4820T.  Of course I wanna run Ubuntu on it (10.04 64bit), but after the installation I don't have any network connections. :sad:

I did a little bit of searching and found out that these are my network cards (both wireless and wired don't work).

Wired: Atheros Communcations AR8151 v1.0 Gigabit Ehternet
Wireless: Broadcom Corporation Device (doesn't say any version number)

System -> Administration -> Hardware Drivers, just gives me the message "Downloading package indexes failed, please check your network status. Most drivers will not be available. Then it's searching for drivers and says there are no proprietary drivers on this system.
 
Could anyone tell me how I can get this installed? :D

---

### Post by okplayer02 on 2010-07-03
Well there is some hope for your wired network connection i did find two threads how to get it working 

[http://ubuntuforums.org/showthread.php?t=1476231](http://ubuntuforums.org/showthread.php?t=1476231)
[http://www.uluga.ubuntuforums.org/showthread.php?t=1495123](http://www.uluga.ubuntuforums.org/showthread.php?t=1495123)

i could not yield any resuls for your wireless

run this command from the CLI

```
lshw
```

this show all the hardware on your machine.

---

### Post by Elysius on 2010-07-03
Hi, okplayer02. I stumbled upon the first thread as well, worked flawlessly for me! Thanks for pointing that out, I'll read out the second thread.

I've downloaded and installed the updates, now in system - administration - hardware drivers I'm also able to download the broadcom wireless drivers.

---

### Post by scorpio2002 on 2011-04-07
Can you confirm that this laptop works good with Linux? I'm going to buy it very soon...

---

