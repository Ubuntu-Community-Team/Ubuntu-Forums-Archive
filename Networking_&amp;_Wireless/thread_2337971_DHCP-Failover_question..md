---
title: "DHCP-Failover question."
date: 2016-09-23
forum: Networking &amp; Wireless
---

### Post by john328 on 2016-09-23
Hi everyone,

I configured 2 Ubuntu (14.04) Dhcp servers in fail-over mode for our wireless system, which work very well. I am using port number 647 for the primary and the secondary (peer server)

My question is, I am going to build another 2 servers for wired network (in different network that the wireless system) , could I use the same port for the new system (647)? or should I use e.g 519 for primary and 520 for secondary? or 847 for moth?

Please advise.

Many thanks

---

### Post by SeijiSensei on 2016-09-23
A separate physical network?  DHCP clients use broadcasts when trying to get an address, so if the other network is physically disconnected from your current one, there shouldn't be any conflicts.

---

### Post by john328 on 2016-09-24
Many thanks SeijiSensei

---

