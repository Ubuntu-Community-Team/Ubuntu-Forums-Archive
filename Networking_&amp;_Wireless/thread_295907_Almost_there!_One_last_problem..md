---
title: "Almost there! One last problem."
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by FiberOptix on 2006-11-08
Hey all,

After installing Ubuntu and setting up my wireless broadcom card I've been trying to connect to my wireless router. At first I tried  using WPA but it seems that in edgy there isn't very good support for it yet, so after configuring the router to use WEP I now nolonger see my eth1 status as disconnected but rather "idle" - a step in the right direction I guess. Now, I've configured my wireless eth1 interface to use the proper ESSID and WEP key at which point I notice that I get a few packets received after sending many out. However, I still can't access web pages, I get a "network unreachable" when trying to ping the router, and the computer isn't showing up on the DHCP table of my router. Yes, I've added the wireless interface MAC address to my filter list too.

I've been scratching my head for a little while now over this, someone please help!

---

### Post by FiberOptix on 2006-11-08
I just solved my problem! I accidentally had it set up for Ad-Hoc mode, silly me!

Still, if anybody's gotten a similar setup working for WPA please let me know.

---

