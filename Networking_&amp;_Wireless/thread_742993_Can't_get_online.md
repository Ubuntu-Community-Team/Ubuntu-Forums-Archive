---
title: "Can't get online"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by roobee on 2008-04-02
Hi there, 
I hope someone can help me out with getting online please....

I'm running Gutsy and it works fine getting online on my home network - both wireless and ethernet. 
I get into work, plug in the ethernet and...nothing happens. I'm offered wireless connections but none of them are mine to jump on to. My work connection is ethernet. 

Any ideas? I've checked the boxes, I've tried DHCP and fixed IP. The command line side of things says my eth1 and eth0 aren't configured - but I can't click on the config option when i try to change this. In any case, everything works at home. 

I've followed the instructions on the official docs site and tried a lot of what's been suggested here. But no joy. I can't pinpoint what I'm doing wrong, so if anyone has any ideas....

Thanks very much, 
Ruby

---

### Post by The Cog on 2008-04-02
The first step must be to run ifconfig at work and look at the output. You are looking for RUNNING after the UP BROADCAST flags, which tells you the cable is in and working. Then look at the transmit and receive counters to see if traffic is going in and out. 

**sudo dhclient eth0** should at least generate a few outgoing packets.

---

### Post by roobee on 2008-04-03
Thanks very much for that. I'll give it a go when I'm back on-site on Monday and fingers crossed it works.

---

