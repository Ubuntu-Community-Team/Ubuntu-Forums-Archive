---
title: "Tips for building Ubuntu box to control net sharing"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by adamssl on 2008-08-15
I live in an apartment with a bunch of guys. We share a single DSL connection, shared out with a Linksys WRT300N. A big problem is that randomly different guys will suck up a huge chunk of the bandwidth, slowing everyone else to a crawl. I'm tired of dealing with the mess. I'm thinking to set up a Linux box between the AP and the LAN port. I'm fairly Windoze / computer savvy, but a Linux neophyte. Installing Ubuntu was no problem, but configuring it to control the shared net goes beyond the newb level.

Can anyone offer any useful tips / links / advice for where to find reference material to:
1) Basic network-server box setup and config
2) Throttle users BW to control peak usage (Prefer to allocate a PER USER caps for fairness, versus per pipe, ala QoS)
3) How to ensure privacy? (ease fears about snooping)

Bonus: Any comprehensive sites that offer an A-Z overview of network admin in Ubuntu?

I'm also thinking it's a good opportunity to set up a firewall, but ufw seems easy enough to setup...

Anyhow! All advice is warmly welcome!

---

### Post by ilrudie on 2008-08-15
I know this is Ubuntu Forums and as such some people expect every reply to say Ubuntu is the best at everything but this is a case where you might want to consider using a different OS.  Ubuntu is very cutting edge and receives updates very often.  This is not ideal for an appliance like you are trying to build.  Ideally you would build it and forget about it for at least a year or four.  I'd recommend looking into OpenBSD.  Its stable and very very secure.  I think pf (built into OpenBSD) can control bandwidth usage and prevent one user from having it all.  That said; unless you are looking to learn about networking and its more important to learn than to get a solution working soon you should look at this:[http://www.dd-wrt.com/wiki/index.php?title=Quality_of_Service](http://www.dd-wrt.com/wiki/index.php?title=Quality_of_Service).  If dd-wrt supports your router you should consider flashing your router to unlock its full potential.  You can also look at OpenWRT.

---

### Post by adamssl on 2008-08-17
ilrudie... very insightful, thank you! I was hoping there would be a simple "quick-fix" solution, but I suppose that was a bit over-ambitious for the task I was trying to accomplish.

In terms of simplicity, it seems that OpenWRT looks like a slick option. If that doesn't pan out, or I'm looking for a meatier task to get some Linux education I may tackle the OpenBSD beast.

Thanks for the advice!

---

