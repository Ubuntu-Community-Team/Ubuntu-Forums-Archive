---
title: "Onboard nic card not deteted correctly"
date: 2015-10-26
forum: Networking &amp; Wireless
---

### Post by wei_chea on 2015-10-26
eth1      Link encap:Ethernet  HWaddr 60:e3:27:02:88:d2
          inet addr:xxxxxxx  Bcast:xxxxxxx  Mask:255.255.252.0
          inet6 addr: xxxx::xxxx:xxxx:xxxx:88d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9071 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3840 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3784172 (3.7 MB)  TX bytes:545638 (545.6 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:748 (748.0 B)  TX bytes:748 (748.0 B)


p133p1    Link encap:Ethernet  HWaddr 40:61:86:8c:5f:89
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Somehow the onboard nic card is being detected as p133p1 instead of eth0. Any idea why? Thanks.

---

### Post by praseodym on 2015-10-26
If it is 15.10, then its new:

[https://lists.ubuntu.com/archives/ubuntu-devel/2015-June/038786.html](https://lists.ubuntu.com/archives/ubuntu-devel/2015-June/038786.html)

---

### Post by wei_chea on 2015-10-26
> **praseodym said:**
> If it is 15.10, then its new:

[https://lists.ubuntu.com/archives/ubuntu-devel/2015-June/038786.html](https://lists.ubuntu.com/archives/ubuntu-devel/2015-June/038786.html)


Im running on lts 14... With the latest update though.

---

