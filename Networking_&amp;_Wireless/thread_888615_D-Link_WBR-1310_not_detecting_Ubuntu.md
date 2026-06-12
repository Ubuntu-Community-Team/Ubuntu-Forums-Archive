---
title: "D-Link WBR-1310 not detecting Ubuntu"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by digitally404 on 2008-08-13
Hi,

I just replaced my old Linksys router that died on me yesterday with a D-Link WBR-1310 router (Firmware fully updated). I have disabled wireless temporarily, and have set up Wired connections between my 3 computers (XP, XP, Ubuntu). Internet worked on ALL computers (i.e. Ubuntu) prior to replacement.

DLink is DHCP Server enabled. The XP boxes had no problem connecting to the internet automatically. My Ubuntu box was having trouble (absolutely no network detection.) DLink isn't even detecting it (Yes, I checked the physical connections).

Under **Network Settings** I disabled Roaming Mode and for the Wired Connection I set the configuration to **Automatic Configuration (DHCP)**.

I was unable to ping my router at 192.168.0.1 (Destination Host Unreachable).

I'm not sure what to do, but I suspect it may be the DHCP client settings in Ubuntu.. But I'm not sure how to do manual configuration of that.

Any help would be greatly appreciated!

---

### Post by digitally404 on 2008-08-20
I'm an idiot, apparently we have two identical looking ethernet cables, and I thought the one connected was connected to Ubuntu, but turned out it was connected to nowhere.

Too many cables, too many problems.

Everything works now. The D-Link WBR-1310 router has no issues with Ubuntu, and I'm really happy with it. In fact, the DLink router has a physical connection debugging utility that I used to solve my problem.

Before you blame Ubuntu, make sure there is in fact a physical connection. Logging into the router, goto **Tools -> System Check** and click **More Info** under the LAN# connection corresponding to your linux box. It let me know that there was a termination point at X number of meters from the cable (and why I suspected the cable was damaged, and ultimately led me to find that there were two identical cables, neither connected anywhere).

Argh, I'm still mad at myself that I didn't see this problem sooner.

---

### Post by dragonbeast25 on 2009-05-05
I have the same problem i got the same router 2, anyone help us?

---

