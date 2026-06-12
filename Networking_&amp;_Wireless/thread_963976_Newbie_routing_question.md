---
title: "Newbie routing question"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by fartingmonster on 2008-10-30
Hi, sorry for this newbie question, I checked the linux howtos but I wasn't able to make sense of ipv4 routing.

I would like to set up access to a VPN to route only traffic to/from google through a VPN interface rather than through eth0.

I have the VPN configured in network-manager and connecting works fine. When I connect to the VPN I can no longer access anything other than 10.x.x.x addresses. Here is the routing table before connecting to the VPN:
> 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.44.119.0     *               255.255.255.0   U     1      0        0 eth0
default         10.44.119.1     0.0.0.0         UG    0      0        0 eth0

Upon connecting
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
164.67.62.102   10.44.119.1     255.255.255.255 UGH   0      0        0 eth0
128.97.245.0    *               255.255.255.0   U     0      0        0 tun0
10.44.119.0     *               255.255.255.0   U     1      0        0 eth0
default         *               0.0.0.0         U     0      0        0 tun0

Thanks in advance

---

