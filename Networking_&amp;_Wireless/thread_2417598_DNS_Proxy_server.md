---
title: "DNS Proxy server"
date: 2019-04-24
forum: Networking &amp; Wireless
---

### Post by uthall on 2019-04-24
Ok, this might might be better than iptables.

Does anyone have a good tutorial on howto setup a dns proxy server on ubuntu.

The purpose is to allow me to use the server for dns resolution of clients, but also specify some domains to be proxied out, and the rest just dns resolved.

Really hard to find a good working guide on this....any help appreciated.

Thanks
Jeff

---

### Post by TheFu on 2019-04-25
Do you really want a DNS proxy and not just a DNS-caching server?  They cache external DNS lookups for the TTL period and can be DNS for your LAN.
[https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)
[https://wiki.debian.org/HowTo/dnsmasq](https://wiki.debian.org/HowTo/dnsmasq) is the normal, small LAN/Business solution.

BTW, another option is to use a proxy server and only provide external DNS to that server, so LAN desktops never get DNS to the outside world. There are a few good reasons this is common in corporations and schools.


Or did I completely miss the reason for setting up a proxy?

---

