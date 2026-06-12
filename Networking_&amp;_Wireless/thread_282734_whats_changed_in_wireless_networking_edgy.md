---
title: "whats changed in wireless networking edgy"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by blackest_knight on 2006-10-23
whats different about wireless in edgy eft?

I upgraded a dapper install to edgy and found 2 new wireless interfaces and one missing 
now there is wlan0 , wmaster0, and missing is rausb0 (uses rt73 chipset)

why 2 wireless connections and which should i use? 
it's all very confusing, I don't know if using the methods for getting wireless working in dapper will work. 

Is anyone willing to write a brief introduction to wireless on edgy?

---

### Post by geeper6 on 2006-10-28
I have the same issue. edgy messed it all up. I use an airlink+ card which usually shows up as ra0, now I have two that show up that dont seem to work. wlan0 and wmaster0. 

Can anyone help?

---

### Post by Henry Rayker on 2006-10-29
my rausb0 connection works just fine, but my ra0 doesn't. The rausb0 is rt2500-usb chipset, the ra0 is rt61 chipset. I'm going to look into the rt61 (I predict that's similar to your card, geeper (as mine is airlink too).

Okay, a quick update. My rt2500-usb card works okay, but the network strength meter is busted. I have 0% signal strength, even when my connection is working just fine.

Secondly, my rt61 (also called rt2600, I believe) is detected as a wired connection called wlan0. Connecting to a network via this adapter doesn't work.

I think that, either something broke in the drivers (and one driver broke "less" than the other) or it may be something bigger. I'm going to try recompiling the drivers for the rt61 device and see if I can make any ground.

---

### Post by Henry Rayker on 2006-11-10
I compiled the drivers myself, but still couldn't get the interface to come up. I think the problem with the rt61 chipset is that the drivers have binary parts to them. Support for that may have wavered in the update (that's my story and I'm sticking to it!:mrgreen: )

I'll keep updating on this until I (or someone else) figure something out.

---

