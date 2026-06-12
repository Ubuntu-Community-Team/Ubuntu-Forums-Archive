---
title: "Networking issue"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by gerald charlemagne on 2008-04-10
I’m on 7.10 on a Sony’s vaio PCG-F540 with a Netgear FA410 PCMCIA network card.
My router is a Linksys WAP 802.11b (I know it’s very old, but it’s working for now).
I’ve got my network drive and the wireless printer on the network with several computers been networked together. My problem with Ubuntu is when I have the network setting set either in “Enable roaming mode” or DHCP automatic. I would be able to have access to the internet but would not see anything of my devices on the network and that would happen if I have a static IP address and the “Gateway address”. When I remove the gateway address I would be able to see all the devices on my network, but I would not have access to the internet. Thank you for any help for I’ve working on this for weeks now.

---

### Post by dstew on 2008-04-11
Could it be a firewall setting problem? Maybe the DHCP address you get is prohibited from accessing the network devices by the firewall, but the static is OK. Look at the DHCP address range. I can't figure out why the static address + gateway won't work until the gateway address is removed. Could the gateway address use trigger some other firewall protection of the network devices? Just guessing...

---

### Post by Iowan on 2008-04-11
Each network machine connects to the router - or is there a hub/switch somewhere in the circuit?  Almost sounds like a weirdness in the routing (if all machines connect to router.)

---

### Post by gerald charlemagne on 2008-04-11
All of my computers and the printer are wireless and my network drive and the Sony's viao(Ubuntu) are the only devices that's connected directly to the router.
Iowan I am thankful for helping with this problem

---

### Post by Iowan on 2008-04-11
Unfortunately, wireless is not my forte.

---

### Post by gerald charlemagne on 2008-04-11
> **dstew said:**
> Could it be a firewall setting problem? Maybe the DHCP address you get is prohibited from accessing the network devices by the firewall, but the static is OK. Look at the DHCP address range. I can't figure out why the static address + gateway won't work until the gateway address is removed. Could the gateway address use trigger some other firewall protection of the network devices? Just guessing...

Dstew; I don't think that it's the router, but could be a setting for the router that could be the problem.
The router is pretty old and it doesn't have a firewall protection.

---

