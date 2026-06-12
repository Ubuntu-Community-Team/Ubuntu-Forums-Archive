---
title: "NAT64 - IPV6 Migration"
date: 2015-09-03
forum: Networking &amp; Wireless
---

### Post by rpugsley on 2015-09-03
My ISP (dual stack) do not provide public ipv4 and ipv6 only.
I am full of doubts about what to do in my network to have remote access that was once by ipv4 + port.

I use no-ip for DNS and from what I saw it supports IPv6.

My gateway is a Linux ubuntu which possess squid3 and iptables ( vpn , ssh, webmin , many nats ).

I've been researching solutions to convert these external ipv6 packets for ipv4 and found Tayga, a NAT64 solution.
But there were several doubts ...

Someone who has done this migration could explain me ? What changes , what remains the same.

---

### Post by TheFu on 2015-09-03
I don't think NAT exists for IPv6.  You should be getting public IPv6 IPs from your ISP - probably either a /64 or /54 according to my research.  Try using any IPv6 compatible stack for your remote access.  However, most remote locations will still be blocking all IPv6 traffic - we do. We aren't ready and don't want people getting access to our internal network that way.

he.net has free IPv6 training. [https://ipv6.he.net/certification/](https://ipv6.he.net/certification/)

---

