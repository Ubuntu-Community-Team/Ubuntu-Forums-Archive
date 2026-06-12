---
title: "WPA/WPA2 troubles with Broadcom BCM4311"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by Tom101 on 2008-01-26
Hey, I'm very new to linux so you may have to explain how to do some simple things, because in all honesty I don't have a clue what I'm doing most of the time.

I have just installed gutsy (7.10) onto my Compaq presario C500 laptop, and I'm trying to get the wireless to work. Unfortunately it contains the "lovely" broadcom bcm4311 (rev 01) wireless card. What I have done so far is installed the driver from the restricted drivers list and downloaded bits from the default web page provided. Now it will connect to an unsecured network fine. No problems. However when trying to connect one that uses WPA or WPA2 it tries to connect then gets stuck. If you hover over the network manager it pops up "waiting for network key".

I've tried all sorts thats been suggested on the Internet, and half of the time I don't know I've done, but it hasn't worked. I have just reinstalled ubuntu as I tried removing network manager in favour of wicd, and couldn't get it back.

Thanks for any help advanced! :)

---

### Post by kevdog on 2008-01-26
Couple things you could try

#1. Try manually connecting at the command line (see my sig).  This will bypass network manager and tell us if wpa is even possible
#2. Im not sure about that broadcom restricted driver.  I fear you will probably have to go to ndiswrapper route.  Try #1 and lets see what your results are.

---

### Post by extremx on 2008-04-10
my 2 cents...

I have been trying to get wpa2 working for a while... i could connect on occasion to the schools network.  Now i tried the command line way of connecting that you (kevdog) suggested.  Lo and behold, its up and working! 

So far (15 minutes) it has worked perfectly.  So i guess i have a couple questions.

1. Is network manager the issue? if so what is to be done about it? (some say something about roaming mode...)
2. Assuming there is no fix for the network manager issue, could i just drop all those commands into a shell script and just run it every time i need to connect?

Thanks


Ubuntu 7.10
Broadcom 4311 wireless card
bcm43xx driver
nm-applet 0.6.5

---

