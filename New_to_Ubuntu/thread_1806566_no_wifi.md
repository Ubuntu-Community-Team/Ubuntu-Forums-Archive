---
title: "no wifi"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by bosstech13 on 2011-07-17
Is there a laptop version my computer has the newest desktop version and I cant use my wifi ?

---

### Post by Cybie257 on 2011-07-17
Try going to:

System -> Administration -> Additional Drivers

Many times I have found that WIFI drivers exist here and get you online.

Let us know if that does anything for you as it is the simplest way to begin.

-Cybie

---

### Post by bosstech13 on 2011-07-17
I tried that the additional driver box is empty does that mean I should re-download Ubuntu or try to get the IEEE80211 driver working in the Terminal?

---

### Post by ubudog on 2011-07-17
Any luck? 

If not, can you please post the output of:
```
lspci
```
(run that command in a terminal, Applications>Accessories>Terminal)

---

### Post by bosstech13 on 2011-07-17
I have a 80211g how do active it in the terminal

---

### Post by bosstech13 on 2011-07-17
the terminal says i have a 80211g

---

### Post by bosstech13 on 2011-07-17
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by ubudog on 2011-07-17
Ok, try this:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by bosstech13 on 2011-07-18
thank-you so much Im no longer tethered to my modem Iv got a lot to learn about how the terminal works. A completely new language.

---

### Post by ubudog on 2011-07-18
No problem, let us know if you have any questions!  :-)

---

