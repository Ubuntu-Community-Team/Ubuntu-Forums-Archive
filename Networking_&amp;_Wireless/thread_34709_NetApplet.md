---
title: "NetApplet"
date: 2005-05-16
forum: Networking &amp; Wireless
---

### Post by en00ne on 2005-05-16
:? 

Guys, hi all!
I have a problem with the netapplet to select wireless network. Don't know if any of you has experienced the same...

at boot netapplet scans for networks and finds mine. I click on the name and it connects. Problem: netapplet still scans over and over and at every scan I lose connection with my wireless router.

Problem is with netapplet because if I stop netdaemon and connect with by hand

ifconfig ath0 up
iwconfig ath0 essid ...
iwconfig ath0 enc ...
dhclient ath0

all works without any interruption. I got the the best performance setting in the router beacon interval = 20ms to reset the network every 20ms!
But cannot play even streming music!!

Is there a way to spot netapplet scanning when it connects?

Mine is a thinkpad t41 with Atheros (i.e. madWiFi).

Thanks to all!

---

