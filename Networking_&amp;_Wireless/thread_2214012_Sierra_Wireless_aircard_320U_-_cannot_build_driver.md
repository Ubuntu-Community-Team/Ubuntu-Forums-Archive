---
title: "Sierra Wireless aircard 320U - cannot build drivers without errors in make"
date: 2014-03-29
forum: Networking &amp; Wireless
---

### Post by mts2 on 2014-03-29
Using ubuntu desktop 13.10

I cannot get the sierra wireless drivers to compile without errors. At the moment my sierra wireless 320U usb modem is working using ppp however I cannot get it to start using network manager. The problem is with the sierra.ko and sierra_net.ko drivers and not the modem itself. Also all the settings I am using are correct or I wouldn't be connected with ppp.

$ modinfo sierra_net gives v.2.0 which are very old.
I am supposed to be able to build v.3.2 according to the sierra_net.c file but the drivers will not build without errors.
Some results from google searches show that others have built these two drivers ok but I cannot get a successful build.

If anyone has managed to get this modem to work with network manager after compiling the newer drivers I would love to hear how you managed it.

---

### Post by mts2 on 2014-04-06
bump

---

### Post by mts2 on 2014-04-18
Have installed Trusty Tahr 14.04 and the modem now works using the network manager to set it up.
No need to build modules as it now works out of the box. :D

---

