---
title: "ssh and server already connected to vpn"
date: 2014-12-23
forum: Networking &amp; Wireless
---

### Post by nico13 on 2014-12-23
Hello everyone

I try to connect my server (ubuntu server 12.04.5) via ssh remotely but I can't because this server is already connected to a vpn service and all the traffic goes through it.

Do you know a way to connect to this server from outside ?

thx

Nico

---

### Post by TheFu on 2014-12-23
It might not be possible - depends on whether the VPN allows "split tunnels."  Many companies do not with the VPNs - it is considered poor security practice by many to allow it.  So - check the routing table when the VPN is up. If everything is forced through the tun device, then split tunnels are not allowed and it is unlikely you'll be able to ssh without getting the corporate VPN people to change settings and policies.

---

### Post by SeijiSensei on 2014-12-23
Can you set up port forwarding on a publicly-visible machine that connects over the tunnel to the server?

---

