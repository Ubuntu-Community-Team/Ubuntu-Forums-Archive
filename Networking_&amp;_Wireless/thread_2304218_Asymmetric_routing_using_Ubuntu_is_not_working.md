---
title: "Asymmetric routing using Ubuntu is not working"
date: 2015-11-25
forum: Networking &amp; Wireless
---

### Post by joko-yuliantoro on 2015-11-25
Hi,

I have an Ubuntu 14.04.2 and I am trying to setup it as a simple router for my test network.
It has Y topology, 2 subnets (192.168.20.0/24 and 192.168.30.0/24) to the client and 1 subnet (192.168.100.0/24) to the server.
The Ubuntu router has a route 192.168.40.0/24 via 192.168.30.245 (the client router at the other end).
The forward traffic from 192.168.40.1 to the server is planned to go via 192.168.20.0/24 --> 192.168.100.0/24 path.
With the above route, the return traffic is set to go via 192.168.100.0/24 --> 192.168.30.0/24 path.
However, when the client tried to send the first packet to the server, the packet stopped at 192.168.20.0/24 segment and it did not appear in 192.168.100.0/24 network.
It is confirmed by tcpdump trace plus the traffic runs fine if I change the route to via 192.168.20.245 (same router but different interface).

My networking skill is rusty, so rust that even I could not recall the correct term for this logic.

Appreciate any advice to enable the packet that comes in from different assigned route interface.

Thanks!
-joko

---

