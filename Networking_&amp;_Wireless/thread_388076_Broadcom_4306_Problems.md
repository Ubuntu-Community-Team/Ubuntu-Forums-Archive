---
title: "Broadcom 4306 Problems"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by Sly_R on 2007-03-19
My broadcom wireless card was working fine until upgrading to Edgy.  Now, when I "trip" the wireless card somehow, either by running modprobe or unchecking/checking the "enable connection" button in the networking program, the wireless indicator light on my laptop comes on for a few seconds, then off.  At no time does the wireless connection appear in the network manager applet.

I have gone through all the troubleshooting steps and configuration steps that I could find online.  Can someone assist please?

---

### Post by teaker1s on 2007-03-19
check you have latest "ndiswrapper-utils" installed think it's 1.8 or 1.9 depending on ubuntu version your using

---

### Post by Sly_R on 2007-04-03
I have 1.18, which synaptic claims is the latest version.

---

### Post by teaker1s on 2007-04-03
should have asked you-are you using native driver or ndiswrapper, secondly please use this command and post output
```
iwconfig
```

---

### Post by SactoBob on 2007-04-03
I think teaker's question about using the native driver versus ndiswrapper is the key.
I had some problems at first setting up my BCM 4306 card with Edgy.

Edgy comes with the bcm43xx driver, which will load by default.  However, you have to download and install the firmware for it to work.  Edgy expects you to do this I guess, since the bcm43xx driver is loaded by default.  You could confirm this with lsmod.

If you go the other way, using ndiswrapper (which is higher performance), you have to make sure that you blacklist the bcm43xx driver and reboot - otherwise the bcm43xx driver will grab your device and prevent ndiswrapper from using it.

So whichever way you go with Edgy, you have a bit of work to do.  Using the native driver, you must install the firmware.  Using ndiswrapper, you must blacklist the bcm43xx module.

---

