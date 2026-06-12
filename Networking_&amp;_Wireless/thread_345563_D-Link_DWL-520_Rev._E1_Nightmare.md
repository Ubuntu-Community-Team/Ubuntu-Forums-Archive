---
title: "D-Link DWL-520 Rev. E1 Nightmare"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by MrPlank on 2007-01-24
Has anyone gotten this card to run under Ubuntu 6.10 successfully yet? I've spent many hours this week with zero success. I can't even get the card recognized let alone configured.

I followed the guide in the Wiki, and then updates in the forum. Help :confused:

---

### Post by MrPlank on 2007-01-25
Or can someone (who is really Ubuntu knowledgeable) on IRC, AIM, MSN, YAHOO walk me through this install procedure? Guidance is much appreciated fellow Linux users.

---

### Post by MakLeod on 2007-01-29
/bump

I've been trying to get the same card working.

---

### Post by ofh on 2007-01-29
Hi just to stay sad (UBUNTU + wireless = #-o )
Have tryed whit D-Link DWL-AG660
No luck either.

Just want to get WPA1 tkip to work, but very difficult !!

BR
OFH

---

### Post by MrPlank on 2007-02-10
With just about 30 minutes of work and effort I was able to get this wifi card working under the latest 2.13 Puppy Linux. How? All from the help of one guy that packaged the needed hostap package, firmwares, and scripts into Puppy's DotPup packaging system. If this can be done that easily, some Wifi guru working with the Ubuntu team surely can get this working in Edgy Eft. Please help guys!

---

### Post by gradedcheese on 2007-02-10
> **MrPlank said:**
> With just about 30 minutes of work and effort I was able to get this wifi card working under the latest 2.13 Puppy Linux. How? All from the help of one guy that packaged the needed hostap package, firmwares, and scripts into Puppy's DotPup packaging system. If this can be done that easily, some Wifi guru working with the Ubuntu team surely can get this working in Edgy Eft. Please help guys!

This is the thing: I'd love to help with this or at least do something similar to what that guy did, but I don't have that hardware so I wouldn't be able to troubleshoot/test it.  And this is part of the reason that it takes a while to get these things right: the right person (by that I mean someone would could work it out and package it) has to happen to have that WiFi card to fix.  I bet that, although they have that one working, there are some other ones they've never gotten to work because they never tried them, and so on.  

I guess the best solution is, whenever anyone solves one of these problems with any card, write a HOWTO or wiki entry about it.

---

### Post by I. T. Sme on 2007-03-04
So far the card I've found that's pretty much bulletproof is a Cisco Aironet 350.  It's a PCMCIA card that comes in it's own PCI adapter.  I'm using it now in my Windows XP box and used it recently in my Ubuntu box.  Drivers are in the OS for both, and configuration was a snap.  Only two downsides is it doesn't support WPA and is "only" a wireless B card--but I've never seen the point in needing faster cards for home use unless you like swapping massive files between your machines all day long.

I recently was trying to get a Linksys WMP11 Ver. 4 working, in Ubuntu it was pretty much useless, and even in XP it disconnects every five minutes, so it looks like I'll be getting another Cisco.

---

