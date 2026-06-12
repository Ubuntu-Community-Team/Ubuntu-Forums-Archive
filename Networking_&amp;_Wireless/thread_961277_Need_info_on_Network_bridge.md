---
title: "Need info on Network bridge"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by bengaltiger on 2008-10-28
Hi,

In my system , windows is host and ubuntu is guest. VMware networkis set to bridge.

In my pc, network bridge and ICS is desabled by windows group policy as its a company PC .

When I run ubuntu I found that ubuntu gets a IP address from my company DHCP server.

And I can browse using proxy server.

My Q is, how ubuntu is getting a IP address is from DHCP server?

if I use NAT, I cant browse from ubuntu.

any idea?

Thanks

BT

---

### Post by nixscripter on 2008-10-28
Bridging means that the packets from Ubuntu will be forwarded down the "real" interface on the host. That also includes DHCP requests.

NAT, on the other hand, means that the traffic will be filtered to within the box. That means that the box (probably VMware) filters packets and only those that look like TCP connections other places are then translated to look like they came from the host. However, a lot of other stuff is just dropped.

Is there a specific problem you are trying to solve?

---

