---
title: "cannot apt-get from new server on LAN..."
date: 2010-08-23
forum: New to Ubuntu
---

### Post by IsaacAsimov on 2010-08-23
hi, i installed ubuntu 10.04 server edition on my dell inspiron (x64) successfully and established a static IP via /etc/network/interfaces. however, when i try to "sudo apt-get update", i get an ERROR - cannot resolve any of the archive hosts. what can i do? below is my interfaces code. i don't see to have a network manager...and of course, this is console-only. thanks very much in advance from a linux noob! 

```

eth0      Link encap:Ethernet  HWaddr 00:21:70:09:7b:f6  
          inet addr:192.168.178.2  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fe09:7bf6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:108963 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:29169185 (29.1 MB)  TX bytes:16955980 (16.9 MB)
          Memory:fdfc0000-fdfe0000 

```

ps. i run opensimulator on this server and connecting to it from within my LAN works well, too. connection is via ethernet cable to a DSL router.

---

### Post by IsaacAsimov on 2010-08-23
resolved this with the help of launchpad users (actionparsnip and Gerardo Garrott)...

answer is to add the following lines to resolv.conf (if you are working with /etc/network/interfaces as i do):

```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

i remain very impressed with the ubuntu support by user community...

---

