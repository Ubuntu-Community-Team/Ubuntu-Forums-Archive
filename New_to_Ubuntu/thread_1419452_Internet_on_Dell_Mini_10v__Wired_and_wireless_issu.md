---
title: "Internet on Dell Mini 10v?  Wired and wireless issues"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by abdullahajj on 2010-03-01
I bought a Dell Mini 10v stock off of amazon.com

I just installed Ubuntu Netbook Remix 9.10 and Wifi did NOT work out of the box, so I figured it would just be a driver, so I plugged it into Ethernet hoping that I could fix the issue by just going to System>Hardware Drivers but this was no the case. The 10v recognizes the Ethernet but won't connect to it. It attempts to connect for about 30 seconds before saying that it's disconnected. 

Could a Dell/UNR expert help me please?

---

### Post by bkratz on 2010-03-01
You might want to look at posts 3 and 5 of this thread, it may affect you.

[http://ubuntuforums.org/showthread.php?t=1414946&highlight=dell-laptop](http://ubuntuforums.org/showthread.php?t=1414946&highlight=dell-laptop)

---

### Post by abdullahajj on 2010-03-01
That does not seem to be the problem, but thank you anyway!  :)

---

### Post by abdullahajj on 2010-03-01
bump?
:popcorn:

---

### Post by abdullahajj on 2010-03-01
Anyone know anything else that might help?

---

### Post by walt.smith1960 on 2010-03-02
I don't know if this will help or if it will break your system. When I installed Jaunty on an EeePC, I had the same situation--no wired or wireless internet.  I was fortunate enough to have a USB wireless adapter that worked with Jaunty (TrendNet TEW424UB Version 3.x using a RealTek chip set. The version # was important; version 2.x used an SiS chipset and did not work out of the box.) Anyway, once I got a wireless connection, I did this:

First, make sure you got all your files up to date. Type in a terminal:

sudo apt-get update

Let that run, and once its done, type into terminal:

sudo apt-get upgrade

Only run the above sudo apt-get commands if you are running the most recent version of Karmic. Ignore them if you are running Jaunty.

Once that finished, restart your computer.  Again open up terminal and type:

sudo apt-get install linux-backports-modules-karmic. 

 Again, substitute jaunty for karmic if appropriate.  It seems that installing backports fixes many systems and breaks some, so no guarantees. I assume you could uninstall if your machine gets worse instead of better.

---

### Post by jpl888 on 2010-03-02
I have installed Ubuntu Netbook Remix on Dell Mini 10Vs and have never had an issue with either the wired or wireless connections. 

The wireless card should be a BCM4312 rev 01 which works with the Broadcom STA driver (available from system -> administration -> hardware).

Perhaps you could post the output of ```
lspci
``` and ```
lsusb
``` so that we can check your hardware over.

---

### Post by shihkster1015 on 2010-03-02
> **abdullahajj said:**
> I bought a Dell Mini 10v stock off of amazon.com

I just installed Ubuntu Netbook Remix 9.10 and Wifi did NOT work out of the box, so I figured it would just be a driver, so I plugged it into Ethernet hoping that I could fix the issue by just going to System>Hardware Drivers but this was no the case. The 10v recognizes the Ethernet but won't connect to it. It attempts to connect for about 30 seconds before saying that it's disconnected. 

Could a Dell/UNR expert help me please?

If you're using a PPPOE connection, go to terminal and type  ```
 pppoeconf 
```
This way you'll be able to connect to the internet

---

### Post by snowpine on 2010-03-02
In addition to all the excellent advice above :) it is worth going into the computer's BIOS (it should be an option when you first turn on the computer) and making sure the network card is enabled. Sounds obvious but sometimes it is the simple things! :)

I believe the Mini 10v uses a Broadcom wireless card. Since this is a proprietary card, you will indeed need to install the restricted hardware driver.

---

### Post by Alabamaschalk on 2010-03-02
Hi!
I have karmic and lucid installed on a Dell mini 10 v (not the NBR). The only thing is to get the wireless working like discribed in 
[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)
The wired connection worked out of the box.
May be it is an NBR issue?

---

### Post by Alabamaschalk on 2010-03-02
Sorry about the silly icon.

---

### Post by abdullahajj on 2010-03-02
Nope, none of that worked...

I tried installing 9.04 because everything worked back then, but it wouldn't even boot!  Bleck.  I miss the days of Ubuntu working right.  :p

---

### Post by TheBuda on 2010-03-02
okay so to summurize, you had a working 9.04 setup.  You installed 9.10.  Beside the usual wireless issues, you have a wired internet issue as well.  Going back to 9.04 you're still all broken.

---

### Post by abdullahajj on 2010-03-02
Correct, but in the last hour I've finally got 9.04 working pretty well.  I guess I'll try an upgrade install to 9.10?

---

