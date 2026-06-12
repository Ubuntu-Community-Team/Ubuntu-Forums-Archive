---
title: "Controlled internet access"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by gabbo_21 on 2008-08-18
Hi, I was wondering if anyone can help. I currently have a setup at work in our accommodation blocks to allows users to access internet via wireless. I have users connecting to wifi routers, which currently ends up going through a transparent squid proxy. User's currently pay me for access to service where I will add there MAC access to access points, but this is alot of work. Is there a way I can control access to internet using my ubuntu squid proxy? E.g. user issued a password/key and once entered user has net access, so no key no internet. Any help would be could, and as a newbie to linux the clear it is, the better.

---

### Post by maecro on 2008-09-04
As far as I know there is no real easy way that is going to save you a lot of time and effort. 

This is not to say that you cannot authenticate through squid. There is a pretty good how-to for squid ncsa authentication on [http://www.cyberciti.biz/tips/linux-unix-squid-proxy-server-authentication.html]("http://www.cyberciti.biz/tips/linux-unix-squid-proxy-server-authentication.html")

The problem is that authentication in squid cannot be done while squid is running transparently (see chapter 7 on [http://wiki.squid-cache.org/SquidFaq/InterceptionProxy]("http://wiki.squid-cache.org/SquidFaq/InterceptionProxy")). So there is not really much saved in terms of work, as all connecting computers would need to be configured to use the proxy.

---

