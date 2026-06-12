---
title: "Routing between subnets"
date: 2016-05-07
forum: Networking &amp; Wireless
---

### Post by canoemoose on 2016-05-07
Hi all.

I have a Ubuntu box currently acting as a router, interfaces as follows:
eth1 connected to LAN. Static IP, 192.168.12.1/24
eth0 connected to Huawei HG612
eth0:1, static IP, 192.168.1.2/24

PPPoE connection built on eth0.  NAT taken care of by Firehol.

The idea of the virtual eth0:1 interface is that the HG612 presents a web/Telnet/other fun data and is accessible on 192.168.1.1.

Everything "normal" works - LAN hosts have internet etc.

I'm trying to route from the LAN subnet (192.168.12.0/24) to the HG612's subnet (192.168.1.0/24) so LAN clients can access the fun data presented by the HG612.  The router machine is able to ping/telnet/whatever the HG612 so I'm reasonably sure the interfaces are configured correctly.

How do I need to go about this?  IPv4 forwarding is enabled already in /etc/sysctl.conf, traffic on eth0 isn't blocked in Firehol, however LAN clients aren't able to ping the HG612.  I've tried both checking logs & disabling the firewall but I'm pretty sure traffic isn't even making it that far...

Traceroutes on LAN clients get as far as the router and then stop.

Output of route -n on the router:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
10.8.0.2        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.12.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
195.166.130.141 0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
```

I'm pretty sure I've missed a step along the way somewhere, but at the moment my brain is cooked and I can't work out what I've done wrong/forgotten.

Anyone got some bright ideas? Any more info helpful?

Thanks!

---

