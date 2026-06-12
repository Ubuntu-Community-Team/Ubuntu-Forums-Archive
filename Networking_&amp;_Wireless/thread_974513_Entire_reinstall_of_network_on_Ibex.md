---
title: "Entire reinstall of network on Ibex?"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by twent4 on 2008-11-07
I ran into some odd issues last night on a vanilla install of kubuntu ibex:
NetworkManager seems to lock up every 1-2 seconds, for about half a second. I mean everything freezes, mouse stops, key hits get missed, audio stutters... when NM is running, it wont connect to my basic DHCP setup with my router (wired). Killing NM gives me my computer back, but obviously i lose my precious interwebs.

I've tried reinstalling network-manager and network-manager-kde by purging them, rebooting, and reinstalling from dvd. Can someone recommend either an alternate network manager which would be found on the 8.10 DVD, or a way to completely reinstall and reconfigure the manager to resemble clean install state?

---

### Post by cariboo on 2008-11-07
You may be running into problems because you are running both network manager and knetwork manager, get rid of one of them if you are running Gnome, get rid of knetwork manager, if you are running KDE get rid of network manager, the are functionally the same.

Jim

---

### Post by twent4 on 2008-11-07
that's what i thought at first too, but isn't knetwork manager a frontend for the networkmanager daemon? or am i missing something?

Shutting down NetworkManager makes knetwork manager show a "network manager is not running" notification, and stop working altogether (once again tho, the computer stops glitching). Adept also installs NM as a dependency for KNM...

additional info: rightclicking knetworkmanager globe with NM running displays a "no carrier" notice. Tried other ethernet cables including the one im using on the machine im typing this up on, no change. The LED on the nic is blinking slowly and steadily. And, very oddly, the process monitor doesn't list KNM when i look for it, but i see that it's running in the systray, and when i try to shut it does it asks "really shut down **knetwork manager**?". what's going on here?

---

### Post by destierro on 2008-11-18
I'm getting this same issue, when unplugging an ethernet cable the entire desktop locks up for 1-5 seconds. I'm running an upgraded-to-ibex x86_64 install with compiz / gnome as my desktop environment. I had no problems with network-manager before the upgrade... Anyone know what's wrong? 

Cheers,
Nathan

---

