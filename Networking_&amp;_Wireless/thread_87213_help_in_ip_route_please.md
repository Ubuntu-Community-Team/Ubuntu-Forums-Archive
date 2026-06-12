---
title: "help in ip route please"
date: 2005-11-07
forum: Networking &amp; Wireless
---

### Post by mailmaldi on 2005-11-07
i ve these multiple ppp connections through the same interface...eth0...

so i ve devices like ppp0 ,ppp1,ppp2.etc

to load balance them i delete my default route(s) by

ip route del default

then add a new default like

ip route add default proto static scope global equalize nexthop dev ppp0 nexthop dev ppp1 nexthop dev ppp2  nexthop dev ppp3

the problem is that whenever one of my ppp connection dies on its own, my default path is deleted & my connection to the net gets conked off..

however if i manually bring down a connection by
ifconfig ppp3 down
then in the default route that device is simply marked dead & my internet connection in still alive...

i there anything i can do so that i can access net even if one of my ppp connection dies on its own???

---

### Post by mips on 2005-11-08
Anybody got any ideas ?

---

