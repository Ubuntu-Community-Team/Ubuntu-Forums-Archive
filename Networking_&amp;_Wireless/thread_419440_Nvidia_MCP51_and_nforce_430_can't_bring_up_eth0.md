---
title: "Nvidia MCP51 and nforce 430: can't bring up eth0"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by mfeif on 2007-04-23
I see that some other folks have had trouble with this comibnation with the onboard ethernet.

I just got an Asus M2NPV-VM and am moving an older Dapper-based install to it. The Dapper LiveCD boots up fine, and the network card even works! But when I boot my "real install" (based originally on the same Dapper CD) it won't see the network card.

When trying to bring up eth0: "ifup eth0" I got a "No such device" error.

Following advice in these forums, I installed the latest Feisty kernel (2.6.20-15-server) and booted, but still had the same problem.

Poking through dmesg, it looked like forcedeth tries to associate with eth0, but it didn't work. Poking in lshw, I noticed that the ethernet device was associated with eth2 for some reason!

This makes me uneasy, as I have no other network devices in the box, and I'm afraid that the id might jump around when I put my other two NICs in there, which would be hard to trouble shoot. I'd like to track this down, so if anyone can help, I'd appreciate it. 

But in case I can't I wanted a record of what I found to be in here for others. I've enclosed relevant files for those of you smarter than me. :)

---

