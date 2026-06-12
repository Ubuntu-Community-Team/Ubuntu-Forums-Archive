---
title: "Double speed through 2 interfaces?"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by daller on 2006-12-22
Hi there,

I have 3 interfaces. ppp0, eth0 and eth1 (eth0 and eth1 point to the same host, so lets look at them as 1 interface)

What I'd like to do, is to enhance my speed on the internet.

I have a 512/128 line, and an almost as fast datacard from 3g. (which I primarily use OnTheGo)

Is it possible to "merge" these 2 lines to double my connection speed? (or use one interface for one application, and the other for another application?)

Please help! 512/128 is dead slow! :D

---

### Post by tturrisi on 2006-12-22
No, your bandwidth is controlled by the isp, and yes, you can merge 2 adapters into a bridged set.

---

### Post by daller on 2006-12-23
I know it's controlled by my ISP, but eth0 and eth1 connects to one ISP (Cybercity), and the other OnTheGo datacard connects to the ISP "3G"

How do I bridge them?

---

### Post by djRobbieF on 2006-12-23
I think the only way you could make your internet "seem" faster is to pipe SOME traffic through one, and SOME through the other... but it'll be IP-specific for each eth card; so it's not actually going to work very well (for what it's worth in the time you'll spend setting it up).

The only thing I could think of doing would be to have, for example, two browsers installed; each using a different traffic route.  Or use one broadband connection for upstream and the other for down... but it seems so very pointless... you're not going to get that big of a boost.

---

