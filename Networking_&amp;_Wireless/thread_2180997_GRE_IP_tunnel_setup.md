---
title: "GRE IP tunnel setup"
date: 2013-10-15
forum: Networking &amp; Wireless
---

### Post by Alex_A on 2013-10-15
Hi, i don't have a huge amount of experience with networking, but basically what i want to do if tunnel all data from a DDoS protected IP, to an unprotected server. 
The DDoS protected server has 32IPs routed to it, which i plan to use to protect the other servers.

How exactly would i achieve this?

---

### Post by houstonbofh on 2013-10-16
I would install m0n0wall on that server, and place m0n0wall on the gateway to your real servers.  Set up an IPsec tunnel between them.  Now set up server based NAT rules forwarding to the internal IP addresses over the tunnel.  (M0n0wall is not the only answer, but it is one I know well.  Pick the VPN capable router you like)

---

