---
title: "Lubuntu Does not Connect to... Anything"
date: 2014-04-10
forum: Networking &amp; Wireless
---

### Post by louis7 on 2014-04-10
I am running Lubuntu 12.10 on a Dell Vostro 1000. After some finagling, I was able to install that dreaded Broadcom driver, and was able to connect to WiFi for a few days without a problem.
However, I have been unable to connect to the internet since. I am able to see WiFi networks, and able to enter passwords to try to access them, but nothing happens when I do (the window closes). Even ethernet connections now no longer work -  I plugged in an ethernet cable and the status is "Error".
Help?

---

### Post by Hadaka on 2014-04-10
Hi, let's take a look at some stuff.
please do and post..
```
lspci -n |  egrep '0200|0280'
lsmod | egrep -i 'wl|ndis|b43'
```
remove your ethernet cable and look very closely
at both ends for broken wire also at the connection point.
power down the router while you inspect the cable.
thanks

---

