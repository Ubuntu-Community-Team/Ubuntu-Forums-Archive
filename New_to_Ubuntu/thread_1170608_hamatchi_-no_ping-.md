---
title: "hamatchi -no ping-"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by trigsenior on 2009-05-26
I can't for the life of me work out why on my hamatchi network people can't ping on another. I have ubuntu 8.04 server + lamp.



This is my ifconfig





ham0 Link encap:Ethernet HWaddr 1a:c0:c4:ca:7a:4b

inet addr:5.103.229.110 Bcast:5.255.255.255 Mask:255.0.0.0

UP BROADCAST RUNNING MULTICAST MTU:1200 Metric:1

RX packets:0 errors:0 dropped:0 overruns:0 frame:0

TX packets:30 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:500

RX bytes:0 (0.0 B) TX bytes:1260 (1.2 KB)



ham1 Link encap:Ethernet HWaddr 8e:7c:42:a0:b4:31

inet addr:5.105.139.21 Bcast:5.255.255.255 Mask:255.0.0.0

UP BROADCAST RUNNING MULTICAST MTU:1200 Metric:1

RX packets:0 errors:0 dropped:0 overruns:0 frame:0

TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:500

RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)



routing table





5.0.0.0 0.0.0.0 255.0.0.0 U 0 0 0 ham0

5.0.0.0 0.0.0.0 255.0.0.0 U 0 0 0 ham1



and i added this to my /etc/network/interfaces



iface ham0 inet static

address 5.103.229.110

netmask 255.0.0.0



iface ham1 inet static

address 5.105.139.21

netmask 255.0.0.0



auto ham0

auto ham1





what am i doing wrong  ?



thanks to the wonderful Ubuntu community :D

---

