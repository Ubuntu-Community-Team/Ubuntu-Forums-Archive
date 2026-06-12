---
title: "VPN to ipcop router"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by NiksaVel on 2007-03-04
Hey all,


I was wondering if anyone has any experience with setting up a VPN connection to a ipcop router comp?

I have wireless on the red zone and would like to access files from the green zone...

---

### Post by helidude20 on 2007-03-17
Green Zones - Trusted (Wired)
Blue Zones - Wireless or Second Green Zone
Red Zones - Untrusted networks AKA The Internet (This is what it protects you against)
Orange Zones - DMZ (No DHCP via IPCOP) 

[www.ipcops.com](www.ipcops.com)
[www.ipcop.org](www.ipcop.org)

You would need to configure port forwarding and/or external access for this to work. But, it sounds like your configuration is incorrect.

---

### Post by NiksaVel on 2007-03-17
no no... it HAS to be this way, because I do not own a regular Access Point that I could plug in to use as Blue Zone...   my AP is integrated on the DSL modem...  henceforth it HAS to be in the red zone...


Shouldn't make a difference since you should be able to do VPN connections from the internet...  wireless or not...

---

