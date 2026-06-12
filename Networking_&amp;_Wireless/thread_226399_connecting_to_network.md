---
title: "connecting to network"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by linuksamiko on 2006-07-31
Saluton everyone,

my brother needs to connect to a accesspoint near to his house but ubuntu allways connects to the wrong accesspoint (which is not public). 

I know by now (after searching the forum) that you can do a "iwlist [interface] scan" but nobody says how to connect to one of the found networks.

He can't install a wifimanager since he hasn't internet yet. How can he choose the right network using progs that are shiped with ubuntu?

---

### Post by stupidkid on 2006-08-01
iwconfig <interface> essid <essid>
iwconfig <interface> key <key>

---

