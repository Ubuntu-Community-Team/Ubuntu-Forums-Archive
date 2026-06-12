---
title: "Policy routing default more than one hop"
date: 2016-07-19
forum: Networking &amp; Wireless
---

### Post by tt8811 on 2016-07-19
In the configuration in question, packets are arriving successfully in a router via an integral openvpn tunnel, with a vtun endpoint of 10.99.99.2. NAT can be used to forward these to systems on a 192.168.1.0/24 network. However, return packets cannot be routed back successfully to the tunnel, since the necessary default gateway points elsewhere. In the past on other networks I have solved this with policy routing when the openvpn endpoint was on the same physical machine. However, in this case the openvpn endpoint is on a router, and though I can create a static route that can ping 10.99.99.2 from the 192 network, attempts to set a default table based policy route for 10.99.99.2 fail with "no such host." Any ideas? Thanks!

---

