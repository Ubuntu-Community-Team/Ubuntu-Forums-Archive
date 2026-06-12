---
title: "RT2500USB &amp; Feisty"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by cbarboza on 2007-11-14
I've recently gotten my USB wireless working under a fresh install of Feisty.  I've done this by blacklisting my built in wireless (R8180) and blacklisting all the RT drivers that I could think of with the exception of RT2500USB.  Gnome Network Manager works with roaming enabled.  The actual connection speed is very fast, I was amazed.  Network manager shows the connection being a low connection rate though.

After a fresh Feisty install and getting the wireless up and running, I allow the update manager to install all the updates that pop up.  After installing the updates and rebooting, my wireless doesn't work anymore.

Can someone tell me what update to avoid so that this doesn't happen?  I've had problems trying to get this working in Gutsy and gave up, although I believe I was able to get it working using Ndiswrapper.

As far as the mechanics of it, would someone know if I would get better results using the native driver rather than using ndiswrapper?

---

### Post by bobz086 on 2007-11-14
I'd be interested in what you finally discover is the correct way. I can't get mine to work either.

---

### Post by cbarboza on 2007-11-21
Well, surprisingly enough it all turned out good with some playing around.  I reinstalled a fresh copy of Feisty, installed all of the automatic updates, blacklisted my built in wireless card, blacklisted all of the RT drivers except RT2570.  My USB wireless device is working great!  When I check IWCONFIG, it now reads as RAUSB0 & RT2500USB WLAN.  I've removed Gnome Network Manager and replaced it with WICD.  It's all good!

---

