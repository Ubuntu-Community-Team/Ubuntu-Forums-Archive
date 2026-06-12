---
title: "iptables routing to self?"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by tyce on 2008-07-24
Trying to consolidate some servers and was wondering if there was a way to route traffic from the router to itself?

ie:

iptables -t nat -A PREROUTING -p tcp --dport 22 -i eth0 -j DNAT --to-destination eth1

(where eth1 is on the internal network)

I know it's not the most secure way to do things, but I'm just curious if it's possible.

Thanks in advance,

---

