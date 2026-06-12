---
title: "ndiswrapper vs. bcm43xx: differences in sensitivity"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by debernardis on 2006-07-19
I have tried both, finding that ndiswrapper makes my wi-fi card more sensitive than bcm43xx. With bcm43xx, I lose signal at a few meters from the base station, while ndiswrapper catches the wi-fi waves at several meters.
I tried to tweak the sens parameter of iwconfig but with no results.
So, I am sticking to ndiwrapper.

My network controller is a Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02).

Anybody noticed the same behavior?

---

### Post by jawrat on 2006-07-19
my broadcom 4306 built into my dell 5150 just generally sucks all around as far as reception.  it's crappy in windows too.  probably something to do with the fact that it's a minipci card built into the case with no external antenna.  i have an old ibm laptop that i use with a netgear ma401 pcmcia card (802.11b) which gets waaay better reception than this one. 

so, the short answer is, mine sucks too, and ndiswrapper was no better.

---

