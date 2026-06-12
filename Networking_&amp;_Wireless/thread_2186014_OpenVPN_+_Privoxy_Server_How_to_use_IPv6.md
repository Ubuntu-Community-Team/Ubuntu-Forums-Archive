---
title: "OpenVPN + Privoxy Server: How to use IPv6?"
date: 2013-11-05
forum: Networking &amp; Wireless
---

### Post by void.pointer on 2013-11-05
I have a VPS that I am renting and have OpenVPN + Privoxy setup on it so I can anonymously browse the web. Currently I've setup my iptables to route to my external IPv4 public address:

-A POSTROUTING -s 10.8.0.0/24 -o venet0 -j SNAT --to-source 1.2.3.4

(1.2.3.4 is my public IPv4 address in this example)

What I'd like to do, if it's simpler and possible, is to keep the internal 10.8.0.0 network IPv4 but simply make it map to one of my 4 public IPv4 addresses instead. This way, when I use my proxy, websites see my IP address as IPv6 and not IPv4. Is this possible? If so, could I get some help setting this up? Thanks in advance.

---

