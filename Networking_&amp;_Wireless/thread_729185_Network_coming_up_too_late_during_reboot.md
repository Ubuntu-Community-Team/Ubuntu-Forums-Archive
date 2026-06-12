---
title: "Network coming up too late during reboot?"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by trojanfoe on 2008-03-19
Hi there, I have noticed that my media server (Twonky Vision) and file server (Samba) are not accessible from the clients straight after a reboot, but work OK if I manually restart them (/etc/init.d/xxx restart).  I'm guessing that there might be an ordering problem during startup; i.e. they are starting before the network is up?  Does this ring any bells with anyone?

My details:

Ubuntu 7.10 with updates.
Vanilla 2.6.24.3 kernel.

Any help would be appreciated,
Cheers,
Andy

---

