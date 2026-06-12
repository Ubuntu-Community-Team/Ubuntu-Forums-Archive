---
title: "How to install Wifi driver In Ubuntu for hp 14s-cf0xxx"
date: 2018-09-21
forum: Networking &amp; Wireless
---

### Post by zi-o on 2018-09-21
Hi this is my first time installing ubuntu version 16.04 . I have installed correctly but i can't connect to internet. 
My ethernet plug  worked but i can't connect with wireless because i haven't installed the drivers. 
How can i install manually the wifi drive ?

---

### Post by jeremy31 on 2018-09-21
Moved to Networking & wireless

---

### Post by NM5TF on 2018-09-21
We need more information to be able to answer your question...:-k

please post the result of 

```
inxi -N
```

and 

```
ip link
```

they should look something like this

```
[tommy@tommy ~]$ inxi -N
Network:   Card: Edimax EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
           driver: rtl8192cu
[tommy@tommy ~]$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: wlp0s2f1u10: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether 80:1f:02:b6:d2:ce brd ff:ff:ff:ff:ff:ff
```

---

