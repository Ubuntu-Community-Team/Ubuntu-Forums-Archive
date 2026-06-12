---
title: "Can't route between subnets on same 16.04 system"
date: 2016-07-17
forum: Networking &amp; Wireless
---

### Post by tt8811 on 2016-07-17
I think I've tried pretty much all the tricks, to no avail. Here's the setup:

16.04 with packet forwarding enabled.

ip addresses on that box are 192.168.1.50 and 192.168.200.50

default gateway on the box is 192.168.1.1

second box (192.168.200.2) is trying to use the first system to reach a gateway modem via the first box to reach a specific external host (e.g. 192.136.9.9). It can't have it's own 192.168.1.X interface.

second box has a route:

192.136.9.0/24 gw 192.168.200.50

traceroute of 192.136.9.9 shows the next hop correctly to be 192.168.200.50.

But that's as far as I can get, despite various attempts at routes on the first machine.

The first machine can ping the second, the second can ping the first, and the first can ping the
gateway modem.

But I cannot get packets from the second machine, aimed at example address 192.136.9.9, to reach the 192.168.1.1 gateway.

What am I missing? Thanks!

---

