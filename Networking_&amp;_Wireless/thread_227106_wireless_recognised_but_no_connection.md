---
title: "wireless recognised but no connection"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by spaciousmonti on 2006-08-01
Hey all, bit of a pickle here and dont know how to fix it, please help.

ubuntu on laptop, wirless card works, network is recognised, packets apparently sent and received, but cannot get online or on the network.

Have tried connecting to the internet through xp box via ics and proxy, no result.

iwconfig:
eth0
unassociated ESSID: "home"
Mode: Managed Channel=0 Access point: Not-associated
Bit rate=0 kb/s Tx-power=20 dBm Sensitivity=8/0
Retry limit=7 RTS thr:off Fragment thr:off
Power management: off
Link Quality:0 Signal level:0 Noise level=0
Rx invalid nwid=0 Rx invalid crypt:0 Rx invalid frag=0
Tx excessive retries:0 Invalid misc=0 Missed beacon=0

ifconfig:
Link encap:ethernet  HWaddr 00:12:F0:42:32:3E
inet addr:192.168.0.4 Bcast:192.167.0.255 Mask:255.255.255.0
inet6 addr:fe80:212:f0ff:fe42:323e/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets 24310 errors:0 dropped:0 overruns:0 frame:0
TX packets:9924 errors:0 dropped:0 overruns:0 carrier:1
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
interrupt:201 Memory:fe9fe000-fe9fefff

Please help, would love to send bill a stuff it letter but cant live without wireless!

spacious

---

### Post by bigken on 2006-08-01
dont know if this will help but try this to get onto the net 

[http://www.ubuntuforums.org/showthread.php?t=222047](http://www.ubuntuforums.org/showthread.php?t=222047)

and for networking between ubuntu and xp you have to enable samba
take a look at reply 2 

[http://www.ubuntuforums.org/showthread.php?t=224550](http://www.ubuntuforums.org/showthread.php?t=224550)

---

### Post by dbw on 2006-08-01
what happens when you: ```
ping www.google.com
```

---

### Post by tonab on 2006-08-10
hi ive noticed in your wireless connection printout
that this line unassociated ESSID: "home" try naming essid the same as  the network your trying to connect to.it may help

---

