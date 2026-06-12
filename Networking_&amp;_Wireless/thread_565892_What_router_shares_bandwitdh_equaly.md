---
title: "What router shares bandwitdh equaly?"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by shvanze on 2007-10-02
If anyone can help me....
I've tested several ADSL Modem/router devices (Netgear, Belkin, Linksys) but all of them seem to stuck when 4-7 users are connected.
For an example, if one user is downloading large file through FTP or HTTP then others can't even access WWW
Is there any piece of equipment that divides bandwidth equally?
Many thanks

---

### Post by shad0w_walker on 2007-10-02
Most routers that are capable of traffic shaping (Controlling bandwidth to each computer) are very expensive, there are probably some cheaper ones but mostly expensive devices such as Cisco brand routers. Your best bet is to try and find a router that has quality of service (QoS) which should atleast help to reduce the problem to a degree by making WWW traffic higher priority than FTP/Bittorrents/whatever

---

### Post by vambo on 2007-10-02
I reckon you need a router capable of load balancing. For that we might be looking at a small Cisco box, unless of course those other manufactures you mentioned offer this.

---

### Post by RoyalPro on 2007-10-02
ClarkConnect is a flavor of Linux that is setup to do routing and much more.  It has Bandwidth control with priorities built in.  It runs on low sys req and with 4-7 computers already trying to get on the net getting any old P3 with a couple network cards together shouldn't be to hard.

---

