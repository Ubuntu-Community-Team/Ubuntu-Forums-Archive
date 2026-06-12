---
title: "How to assign specific ethernet interface to specific user?"
date: 2017-10-20
forum: Networking &amp; Wireless
---

### Post by danielng on 2017-10-20
[COLOR=#242729][FONT=Arial]I have an Ubuntu 16.04 server running with multiple ethernet cards all connected to the internet with distinct IP addresses. I want to configure specific user to use specific card so that they will have different IP publicly. How can I set that up? The closest thing I can find is to do SourceBasedRouting but I am not sure if I am on the right track.[/FONT][/COLOR]

---

### Post by TheFu on 2017-10-22
The only way I've seen this is using iptables and the --uid-owner option.  It is quite a hack, since network resources aren't designed to be userid-specific. They are system resources.

[https://www.netfilter.org/documentation/HOWTO/packet-filtering-HOWTO-7.html](https://www.netfilter.org/documentation/HOWTO/packet-filtering-HOWTO-7.html) has more.
[https://www.linuxjournal.com/article/6091](https://www.linuxjournal.com/article/6091) is an old article that might be easier to follow.

Linux is very flexible.

---

