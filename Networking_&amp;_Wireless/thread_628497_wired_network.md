---
title: "wired network"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by mrallen1971 on 2007-12-01
I am trying to connect a wired network in my home. I have cable internet and I wired it to a speedstream 5871 router. This led to my inability to connect to the internet. The cables are good and work if i connect the modem directly to the computer but not through the router. any suggestions

---

### Post by mellowd on 2007-12-01
Has the router been set up correctly? Is the router itseld able to connect to the internet? Once your pc is connected to the router, how far can you trace before it gets dropped?

---

### Post by victorbrca on 2007-12-01
It depends on many things. If your modem is not on transparent mode, it could be doing NAT, which can be on the same subnet as your router's LAN.

Connect to your modem and run this code on the terminal:

```
ifconfig | grep Bcast | expand | tr -s '[:blank:]' | cut -d' ' -f3
```

Write down the number. Them connect to your router (without connecting to the modem), wait for a little bit and run the same command. If the first 3 series of groups are the same you know you have a problem.

Also, make sure the router is enabled to get DHCP IPs on the WAN side.


Vic.

---

