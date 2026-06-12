---
title: "50%+ packet loss from notebook towards wifi router (android phone has no packet loss)"
date: 2015-08-08
forum: Networking &amp; Wireless
---

### Post by Peter Vojtek on 2015-08-08
Hello,


I have Dell E6410 with ubuntu 12.04 and experience big packet loss (more than 50%) towards my wifi router.


When I try to ping the wifi router from my android phone, I experience no packet loss.


I tried two different wifi network cards and both exhibit the same behaviour:
internal wifi card Intel Centrino Advanced-N 6200
external wifi via usb 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n


this is ping behaviour from dell notebook:


// for 10-15 seconds everything is fine
64 bytes from 12.0.0.1: icmp_req=175 ttl=64 time=3.10 ms
64 bytes from 12.0.0.1: icmp_req=176 ttl=64 time=2.53 ms
64 bytes from 12.0.0.1: icmp_req=177 ttl=64 time=3.01 ms
64 bytes from 12.0.0.1: icmp_req=178 ttl=64 time=5.82 ms
64 bytes from 12.0.0.1: icmp_req=179 ttl=64 time=27.8 ms
64 bytes from 12.0.0.1: icmp_req=183 ttl=64 time=4.02 ms


// then for 20-30 seconds all packets are lost


// and the again it works properly for another 20 seconds
64 bytes from 12.0.0.1: icmp_req=205 ttl=64 time=3.34 ms
64 bytes from 12.0.0.1: icmp_req=206 ttl=64 time=3.47 ms
64 bytes from 12.0.0.1: icmp_req=207 ttl=64 time=2.94 ms
64 bytes from 12.0.0.1: icmp_req=208 ttl=64 time=23.7 ms
64 bytes from 12.0.0.1: icmp_req=209 ttl=64 time=1.78 ms
64 bytes from 12.0.0.1: icmp_req=210 ttl=64 time=2.53 ms
64 bytes from 12.0.0.1: icmp_req=211 ttl=64 time=6.12 ms
64 bytes from 12.0.0.1: icmp_req=212 ttl=64 time=4.42 ms
64 bytes from 12.0.0.1: icmp_req=213 ttl=64 time=2.54 ms


the wifi router is D-Link DWR-116 connected to internet via 4G LTE usb modem (D-link DWM-221).
I restarted the routed several times.
On dell notebook I tried to downcrease MTU to 300bytes but has not helped.

I also tried to change wifi network channel to other one, has not helped.

network strengh should not be source of the problem, the distance between notebook and wifi router is less than 2 metres (in the same room).

when I connect the notebook to the router via LAN cable, connectivity is ok (no packet loss).

I took another notebook (samsung) with ubuntu 12.04 and this one experiences the same packets loss issues as the dell notebook. actually the both seem to drop the packets at the same time periods.

Any help is appreciated :)

---

### Post by Peter Vojtek on 2015-08-08
I also tried to check IP address colision via arping (arping -I wlan1 12.0.0.56), which returned no outcome which should mean that there is no IP address collision.

---

### Post by Peter Vojtek on 2015-08-08
I also updated the kernel to the latest available (3.2.0-88-generic-pae #126-Ubuntu SMP Mon Jul 6 21:47:47 UTC 2015 i686 i686 i386 GNU/Linux) and all the packages, but the problem remains.

---

### Post by Peter Vojtek on 2015-08-08
this modprobe hack has solved the problem:
[http://ubuntuforums.org/showthread.php?t=1978457&p=11928720#post11928720](http://ubuntuforums.org/showthread.php?t=1978457&p=11928720#post11928720)

---

