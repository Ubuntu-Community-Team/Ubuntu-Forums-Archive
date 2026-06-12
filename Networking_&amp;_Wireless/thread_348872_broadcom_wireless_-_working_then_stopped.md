---
title: "broadcom wireless - working then stopped"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by Packman5280 on 2007-01-29
I went through all the fun of getting a broadcom 4306 working using ndiswrapper, and all was good.  it worked for a couple days last week, now I noticed that it stopped working today.  The card shows up and says that drivers are present, but I cannot connect to any wireless networks.  Any ideas where to start, do I need to do the driver install again?  If I need to install drivers again, does anyone have a link to a really complete guide for making the 4306 work?  there are many incomplete guides, and when I got it working the first time I'm not exactly sure which one I used.  it was likely some combination of several.  oops.

TIA

---

### Post by taosaur on 2007-01-29
I went through quite an ordeal with my BCM 4318 card, and [this thread]("http://ubuntuforums.org/showthread.php?t=185174") got me up and running in under 5 minutes.  It recommends a reinstall if you've been messing with ndiswrapper, but I just completely removed ndiswrapper-utils with Synaptic Package Manager (System>Administration) and blacklisted it just in case.

---

### Post by Packman5280 on 2007-01-29
Thank you.

I want to avoid FWCutter because I want to be able to use 802.11g speeds, not just 802.11b (54 vs 11 Mbps).

Still looking for a way to make this work.  I have looked at all the guides I can find, and cannot make this thing work again.  It shows up when I do ifconfig, just without an IP addy.  iwconfig shows it as wlan0, network manager shows it as wireless connection, and wifi radar sees it but cannot get an IP address.  my radius infrastructure even shows that it is requesting an address and the radius logs show that it allowed access.

i feel dumb, this should be working.

---

