---
title: "OpenVPN client have IPv6 but DNS default only query A record"
date: 2017-08-29
forum: Networking &amp; Wireless
---

### Post by Bob_Puk on 2017-08-29
Hi,

My notebook had Ubuntu Gnome 17.04, the native connection on it is ipv4 only, and my openvpn server had ipv4 and ipv6, and both wiindows and android cleint can use ipv6 can browse ipv6 with no problem, but my Ubuntu Gnome although getting IPv6 address and i can do "ping6 ipv6.google.com", all application would default query DNS for A record, how can I force it to query AAAA as it should for IPv6 capable connection?
btw, if I had native ipv6 connection, then all applications do query AAAA record (tried test-ipv6.com, ipv6.google.com), only when native connnection is ipv4 only woulld application query A record by default.

---

