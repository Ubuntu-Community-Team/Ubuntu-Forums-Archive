---
title: "Use second NIC for shaping purposes, no default route?"
date: 2015-01-25
forum: Networking &amp; Wireless
---

### Post by Aacron on 2015-01-25
Okay, been working on this and I see that it should be able to be done but the guides I've seen are a bit confusing and generally don't explain what the commands mean -- they just give the commands and say 'hey do this and it works' -- but they don't apply to my specific issue.  I tried to do this with the network connections tool, and it doesn't work at all.  Seems that it just doesn't add the route.

So on to the issue; I want to use transmission, and be able to run it unlimited bandwidth. I've successfully used other clients to do this, and they work because they support outbound port mapping.  The issue is that the clients I used before are either windows clients, or they're not supported by some of the other clients/trackers due to issues with recent updates.

Transmission is also very lightweight.  So I've settled on using it, but since it doesn't support binding to specific outbound ports, I can't shape the traffic with my bsd firewall.  I do not want to limit the rates in transmission - I want it to use all bandwidth that the router allows it (QoS is being used so if I get a voice call, or watch netflix, is reduces lower priority traffic when needed)

After mulling over it I noticed that like many linux programs, it does support binding to a specific interface.  I can use this as the motherboard has two eth ports.  I have the ports set up with 192.168.1.15 (main, not low priority) and 192.168.1.14 (for any low priority traffic).

The issue I've now hit is that I noticed transmission is running, set to seed a few linux ISOs, but.... it can't connect to the trackers.  I tested and it seems the issue is that eth1(..14) can't ping outside the local network.
```
liath@ubuntu ~ $ ping -I eth1 google.com
PING google.com (74.125.137.102) from 192.168.1.14 eth1: 56(84) bytes of data.
From ubuntu_2.some.network (192.168.128.14) icmp_seq=1 Destination Host Unreachable

```From what I gather, package iproute can do what I need it to.  But I don't quite get how to set this up.  So I am asking if anyone could shed some light on this and help me to understand how exactly to set this up -- all the pages I've seen on how to do it don't handle the issue of having the same default gateway on the same network on two seperate interfaces.
I'm *thinking* that what needs to be done is add 192.168.1.1 as the default gateway for eth1, but with a high metric (cost), so that generally it doesn't want to use that interface to get out, but since transmission is bound to the interface, it HAS to use that interface.
Only other idea I have is to use a virtual interface, bridged to eth0, but... I get the feeling that I'd end up with the same exact issue.
Thank you in advance for any help!
-edit-
If there is a better way to do this usign a vitrual interface instead of a physical one, I'm all ears too. Currently the box has two NICs but I can see times where I may not have both of those NICs (the computer in question is quite old and needs an upgrade)

---

