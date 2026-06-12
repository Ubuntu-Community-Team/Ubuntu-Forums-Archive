---
title: "Xen multi-homed networking ?"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by clockwork on 2007-05-03
So I have a test box that I am playing around with. Its hooked into two different networks a 10.10.x.x and a 172.16.1.x (its essentially a shared server.) and I have been trying to create a xen guest that has two network devices (eth0 & eth1) one on each network. The physical host has two bond's setup, one uses eth1 & 2 (bond0) the other eth3 & 4 (bond1). So I need xenbr0 to use bond0 and xenbr1 to use bond1, then pass off the devices as eth0 and eth1 to the "guest".

Does anyone know how to do this with xen ? I have been using a script like this:

```

#!/bin/sh
/etc/xen/scripts/network-bridge start vifnum=0 bridge=xenbr0 netdev=bond0 $*
/etc/xen/scripts/network-bridge start vifnum=1 bridge=xenbr1 netdev=bond1 $*

```

but that doesnt work at all. Matter of fact it craters networking on the box whenever I try it. What am I missing ?

---

