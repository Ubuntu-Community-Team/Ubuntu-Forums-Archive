---
title: "2nd optional external eth card"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by RikoW on 2007-12-12
Dear all,

one of the internet services I use issued what they call a usb internet stick. This stick apparently serves as some sort of eth card, connecting via the active
network connection to a particular IP address for authentification. When plugging in the stick, it appears at eth2 (eth0=lan, eth1=wlan) and can be configured
with the normal network tools. The resulting /etc/network/interfaces files looks like:

```

 # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid xxxx
wireless-key xxxx

iface eth2 inet dhcp
auto eth2

```

However, when I reboot my computer and the eth2 stick is not plugged in, the network setup fails:

```

> sudo /etc/init.d/networking start
 * Configuring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.

```

Obviously, the missing eth2 is the problem. How do I set-up interfaces so that eth2 is brought up automatically when inserted
but is not tried, when not there. 

If I take out the ```
auto eth2
``` piece, network starts correctly, however I don't know if eth2 would then start later (can't test
because I don't have that stick with me at the moment ....)

Thanks,

                 Riko

---

### Post by RikoW on 2007-12-12
Hi folks,

seems like taking out the 

```
auto eth2
```

line from /etc/network/interfaces does the job!

Thanks for listening,

                   Riko

---

