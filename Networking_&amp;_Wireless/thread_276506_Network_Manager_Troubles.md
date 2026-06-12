---
title: "Network Manager Troubles"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by Noah0504 on 2006-10-13
I may be going out of town for a few days, and I want to be able to search for and connect to wireless networks.  For some reason, I'm not able to get Network Manager to work properly when I install it.  Are there any other alternatives to be able to connect to available wireless networks?

---

### Post by techrush on 2006-10-13
wifi-radar

---

### Post by KingArthur10 on 2006-10-13
You may also check (via gedit or something of the sort) /etc/network/interfaces to make sure that everything but the lo lines are commented out.  That helps NM work on many machines.

Edit: Make sure you restart for it to potentially work.

---

### Post by Noah0504 on 2006-10-13
WiFi-Radar works perfectly.

---

