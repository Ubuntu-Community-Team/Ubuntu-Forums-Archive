---
title: "Source Routing"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by sooqing on 2006-12-28
Hi!

I am currently in south east asia, where the entire region's internet connection is down with the quake in taiwan. I am able to surf the web only if I connect to a proxy in australia, via the browser. I would like all my traffic to be routed through this proxy, a la source routing using traceroute, not just my http traffic. How do I do that, say through the use of a routing table?

Thanks!

---

### Post by beow on 2006-12-28
Don't think you can do that.  You can probably control how your outgoing traffic is routed, but the return traffic will follow its own routes. You would need to have a proxy for all your traffic in order to control the exit/entry point. 

On the other side, Internet should be resilient to these interruptions and route traffic to you on another existing route. How bad is it? Does it improve with time?

---

### Post by sooqing on 2006-12-28
> **beow said:**
> but the return traffic will follow its own routes.

you are right.. never thought of that.. hehe.. so is there any way for me to specify this proxy server in ubuntu, to direct all traffic through it.. want to find a more general way rather than relying on the browser? I can do so in Windows, albeit through the firewall ZoneAlarm Pro.

my country had stated it would take weeks to repair the submarine cables.. so looking for an alternative way to surf..

---

