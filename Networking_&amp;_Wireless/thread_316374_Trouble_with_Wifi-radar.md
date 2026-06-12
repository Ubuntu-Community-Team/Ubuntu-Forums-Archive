---
title: "Trouble with Wifi-radar"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by Elvish Legion on 2006-12-10
I dunno if this has been brought up, didn't see anything, but I seem to have the hardest time connecting using wifi-radar....is there maybe a better program for connecting (gnome-network manager doesn't detect my wifi card even after ensuring its on)

---

### Post by Snakiej on 2006-12-10
> **Elvish Legion said:**
> I dunno if this has been brought up, didn't see anything, but I seem to have the hardest time connecting using wifi-radar....is there maybe a better program for connecting (gnome-network manager doesn't detect my wifi card even after ensuring its on)

gnome-network-manager has a bug on 6.10, only showing up the wired connections.

what is your wireless connection? eth1?

Goto /etc/wifi-manager.conf -> eth0 -> eth1

---

