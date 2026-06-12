---
title: "DELL OptiPlex XE2 (Ubuntu 14.04 LTS) no wired connection; wireless OK"
date: 2016-11-24
forum: Networking &amp; Wireless
---

### Post by chenyuwai on 2016-11-24
I am able to connect to wireless but not wired networks. First I tried just plug the ethernet cable in (which works for  windows computers so it is live), the wired network is disconnected and  offline.
 
I tried network-manager restart, ping localhost, responses seemed OK.
```

> sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 8073
> ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_req=1 ttl=64 time=0.018 ms
64 bytes from localhost (127.0.0.1): icmp_req=2 ttl=64 time=0.043 ms
64 bytes from localhost (127.0.0.1): icmp_req=3 ttl=64 time=0.020 ms

```

"sudo dhclient eth0" gave no output after a long while.

Network card is eth0.

```

ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 34:17:eb:c0:7c:bd  
          inet6 addr: fe80::3617:ebff:fec0:7cbd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18636218 errors:0 dropped:75402 overruns:0 frame:0
          TX packets:172933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1895697517 (1.8 GB)  TX bytes:41478047 (41.4 MB)
          Interrupt:20 Memory:f7f00000-f7f20000 
```

  Please help to diagnose the problem. Thanks a lot!

---

### Post by wildmanne39 on 2016-11-25
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

