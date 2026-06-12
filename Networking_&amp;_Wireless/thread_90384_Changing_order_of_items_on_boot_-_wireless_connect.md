---
title: "Changing order of items on boot - wireless connection"
date: 2005-11-14
forum: Networking &amp; Wireless
---

### Post by MrNamjama on 2005-11-14
Hi all

My laptop is generally connected only by a wireless connection (using wpa_supplicant), the ethernet cable sees very little use.

The problem is that at the moment wpa_supplicant gets started on bootup, but I manually do a ifconfig eth0 up (eth0 is the wireless card and it has a static config) once I log in. This means that firstly, the mapped nfs shares over the network do not get loaded and secondly that I have to ctrl-c the 'synchronising time with server' process during the bootup, to prevent it from taking half an hour to discover that it cannot sync.

Can I ensure somehow that the nfs shares from fstab get mapped AFTER wpa_supplicant and eth0 are initialised? What about the time synchronisation?

Can someone suggest another approach to this that might be more elegant?

---

### Post by MrNamjama on 2005-11-16
no ideas at all?

---

### Post by MrNamjama on 2006-02-01
If anyone ever wants to do the same thing, the issue was basically the fact that eth1 was being automatically started by /etc/network/interfaces and on the same ip range as eth0. This creates a conflict, as both network cards go on the same subnet. Once I disabled eth1 auto start eth0 could be auto configured and everything worked as expected and in the right order.

---

