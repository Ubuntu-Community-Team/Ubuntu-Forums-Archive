---
title: "Network is unreachable"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by Particle on 2008-03-21
Howdy folks.

Any idea why I can't reach out on any networks with my box?  I can't ping or access anything.

I suspect a routing problem, because I get the following error if I try to manually add my gateway:
SIOCADDRT:  Network is unreachable



The IP I am using is 66.36.244.229, the netmask is 255.255.254.0, and the gateway is 66.36.242.1.


I know these things worth together since I used them on a different VM yesterday and earlier today successfully.  However, I trashed those VMs due to other problems.

---

### Post by Particle on 2008-03-21
I don't know how these settings were working on the older VMs.  The subnet was too tight.  Yet, it was and isn't now.  That was the problem, however.

---

