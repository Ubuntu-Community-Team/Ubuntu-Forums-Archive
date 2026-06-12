---
title: "nmblookup + multiple interfaces on windows returns wrong IP"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by ^rooker on 2007-07-02
Hi everyone, 

I just ran into a nice problem:
I'm trying to connect to a windows computer that has VMWare installed, and thus it has 3 interface (1 physical, 2 virtual). Each of them in a different subnet.

Running "nmblookup" on the linux machine, returns all 3 IPs properly - but when mounting a share by name (e.g. "//mywinpc1/whatever"), it takes the wrong IP.


Is there any way of telling nmblookup to use only IPs within a certain range (e.g. ones that match a local route)?


Thanks for any tips.

---

