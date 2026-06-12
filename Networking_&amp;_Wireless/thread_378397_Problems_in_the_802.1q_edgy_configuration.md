---
title: "Problems in the 802.1q edgy configuration"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by luigi.comper on 2007-03-07
Hello, im new on this forum.
I didn't know where I could search more **informations about 802.1q tagged vlan protocol**.
*My hardware and software configuration is:*
- **switch repotec with 3 tagged vlan configured**
- **server with 3 network interfaces and ubuntu installed(this server works as router)**
- **protocol 802.1q installed and configured**

The **system works** fine if I use protocols **with small packet like ping or telnet**.
**If I use protocols like VNC, HTTP**(downloading large packets), ... the network **doesn't work**.
I've searched on the Internet a **solution** and I've found this: *setting mtu under 1500 bytes (1492 or 1496), *with this configuration the system works better but the problem is the same.
I haven't found more documentation about this problem.
**I tried to use redhat 9.0** to understand if there are a bug in edgy eft and **with this system the configuration works fine**, but** i must use ubuntu **and i don't see any solution with this distribution.

Any idea?
Thanks Luigi

---

