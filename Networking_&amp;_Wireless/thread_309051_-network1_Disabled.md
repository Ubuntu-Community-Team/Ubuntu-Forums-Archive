---
title: "-network:1 Disabled"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by johnmxg12 on 2006-11-29
Hey guys, i'm new here, and i apologize if i'm posting an old question but i tried searching and couldnt find information specific to my laptop model. 

I just installed Ubuntu onto my HP L2000 and i went through the wireless troubleshooting guide, Ubuntu recognizes my hardware and i  basically got to step 4.2.5 "Driver looks ok, device disabled."

when i ran lshw, among the information given this came up:

*- network:1 Disabled.  

So i'm guessing that all i need to do is turn on my wireless device since the OS recognizes the driver.  I have a broadcom 802.11 b/g.  i hope i gave enough information, and again, i apologize if i'm posting old information. :)

---

### Post by johnmxg12 on 2006-11-29
I have a wireless button on my laptop but its turned off in Ubuntu, works fine in XP.  I guess i'm just looking for a way to manually turn on the wireless device.  

i checked on this other thread from a few days ago and i tried enabling the device using :

sudo ifup eth1

and it said it was already configured.

sudo dhclient eth1
and it said no network detected. and it went on for a bit but nothing was happening. 

anyone with HP's out there that can help me out?

---

