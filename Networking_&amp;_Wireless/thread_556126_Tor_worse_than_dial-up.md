---
title: "Tor worse than dial-up"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by Wake Rider on 2007-09-20
I'm a bit paranoid about security with all the threats on the internet, so I decided to install Tor to hide my IP address. The tor servers are going so slowly it makes my broadband connection function worse than dial-up. How can I increase the speed??:confused:

---

### Post by msubzwari on 2007-09-21
Tor is basically a proxy and that too without any data cache AFAIK.  Like any other non-caching proxy, it will never match the speed of direct access.  Typical anonymity proxies work that way.

Note that your ISP proxy is a different type.  It caches data and does not fetch from Internet if the content is already in cache. So it creates an illusion of the net running faster.

So the bottom line is that if you want to surf securely, you have to compromise and settle for slower speeds.  Having said that...it should not be slower than dialup.  I think there are some ports that you have open/forward in your router/firewall/iptables (if you are using such a thing).  Do check on that.

---

