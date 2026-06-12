---
title: "How to bind to a specific adapter?"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by MalcolmCarmen on 2007-07-16
I have two wireless adapters on my system; eth1 and rausb0. Each one is connected to a seperate wireless router and is assigned addressing via DHCP. Each is working perfectly.

I'm not sure how to control which adapter is used in various situations. I believe I could nearly handle this with iptables, but that would still not allow doing something such as running two browsers, each one only using one of the adapters. 

I suppose I'm hoping a proxychains-esque application exists, in that I could execute a binary restricted to only a given adapter (whereas proxychains forces all TCP traffic through a proxy, but the same concept exists).

As a side note, I can certainly bring down one of the adapters to force the other to be put into use, but that isn't desirable for using them concurrently!

Thanks for any help!

---

