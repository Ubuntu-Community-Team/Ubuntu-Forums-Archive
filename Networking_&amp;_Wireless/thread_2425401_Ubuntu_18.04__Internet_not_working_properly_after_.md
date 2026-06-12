---
title: "Ubuntu 18.04 : Internet not working properly after forced shutdown"
date: 2019-08-25
forum: Networking &amp; Wireless
---

### Post by mskar.lat on 2019-08-25
Hi!
After a forced shutdown of my laptop with Ubuntu 18.04, I cannot open any websites from 
the browser. The wireless network is connected. Here is the output from ip link :

```

ip link

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: wlp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DORMANT group default qlen 1000
    link/ether 50:5b:c2:c6:56:8d brd ff:ff:ff:ff:ff:ff
```

By the way, update and upgrade works. I could also successfully install a software using
Synaptic Package Manager.

Any help would be greatly appreciated!

Thanks.

---

### Post by Skaperen on 2019-08-25
it looks like your wireless is up.  try doing "ping -c 8 8.8.8.8" and see if you get any response.  if you do, tell us what you tried to do that did not work.  are you posting here using that laptop?  what do you get on the screen when you try to open [https://ubuntuforums.org/](https://ubuntuforums.org/) ?

---

