---
title: "one of the 2 DNS resolution methods fail"
date: 2014-05-18
forum: Networking &amp; Wireless
---

### Post by jamapii on 2014-05-18
Hi,

this is a problem that i have seen often before in different distributions (laptops where the network configuration must be flexible). This is currently for my site-local names like myhost.site1.my-net.local. Names like [www.google.com](www.google.com) work fine, names like myhost.local work mostly, too. It works fine on other laptops and a macbook, but not on a new ubuntu installation.

When I ping or nslookup a DNS name, it works.

When I use ssh or vncviewer, it doesn't. ("could not resolve hostname")

So there are at least 2 methods, one for testing that works, and one for production that fails. How is that possible? What are the 2 methods, and how are they different?

ps ax|grep nscd shows nothing. I see dnsmasq running and 127.0.1.1 in /etc/resolv.conf. It is Ubuntu 14.04

---

### Post by jamapii on 2014-05-18
So i found this in /etc/nsswitch.conf:

hosts:          files mdns4_minimal [NOTFOUND=return] dns

I think the NOTFOUND=return must be the reason for the failure. After finding nothing in .local with mdns4_minimal, it does not continue for my site-local names.

Changing it to 

hosts:          files dns mdns4_minimal

should help, but i use

hosts:          files dns mdns4_minimal mdns4 wins

So I can understand that nslookup bypasses all this, but how come ping works without this change? It works for plain .local names too, so it can't be bypassing the avahi method?

edit - closing, i guess nobody knows...

---

