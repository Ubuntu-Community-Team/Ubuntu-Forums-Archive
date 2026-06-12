---
title: "Cannot get multicast to work"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by BBQNinja on 2006-12-20
Two ubuntu machines, both are running:
-Ubuntu 6.10
-No custom packages (all from main/rest/uni/multi)
-Fully updated

I'm attempting to get multicast working but cannot seem to get the response I expected.

Steps I followed (all as root) on BOTH machines
-ip route add 224.0.0.0/4 dev eth0
-echo 1 > /proc/sys/net/ipv4/ip_forward

then to test:
-ping -t 1 -c 1 224.0.0.1

I SHOULD get machineA responding when I ping from machineB, and vice versa (as well as ALL other multicast-capable devices on the network).

Instead, I get a single response from my wireless access point.

Any ideas?

[SIZE="1"]*For reference, my ROOT problem is that I'm attempting to get UPnP to work from mythtv .20 in ubuntu, and I've tracked it down to multicast not being enabled/working, so I figure "one step at a time".*[/SIZE]

---

