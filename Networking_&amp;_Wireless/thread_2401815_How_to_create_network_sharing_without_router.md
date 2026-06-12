---
title: "How to create network sharing without router"
date: 2018-09-22
forum: Networking &amp; Wireless
---

### Post by satimis on 2018-09-22
Hi all,

[COLOR="#FF0000"]
**How to create network sharing without a router**r[/COLOR]

OS:	Ubuntu 18.04.1/16.04.5 desktop

Oracle VirtualBox

**Connection:**
FTTH
-> ONT (Optical Network Terminal)
-> 4 ports for connecting computers

**[COLOR="#FF0000"]Computer 1[/COLOR]**
&#10219; ifconfig```

eth0      Link encap:Ethernet  HWaddr f0:79:59:65:2f:bb  
          inet addr:42.2.2.2  Bcast:42.2.2.255  Mask:255.255.255.0
          inet6 addr: fe80::b7ec:1609:53c6:bda8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:123 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8382 (8.3 KB)  TX bytes:14122 (14.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:16024 (16.0 KB)  TX bytes:16024 (16.0 KB)

```

**[COLOR="#FF0000"]Computer 2[/COLOR]**
&#10219; ifconfig```

enp2s0    Link encap:Ethernet  HWaddr 50:46:5d:54:bf:ac  
          inet addr:42.2.2.54  Bcast:42.2.2.255  Mask:255.255.255.0
          inet6 addr: fe80::920b:f080:170e:b4c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2449 (2.4 KB)  TX bytes:7496 (7.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15159 (15.1 KB)  TX bytes:15159 (15.1 KB)

```


On a brief searching I found following document;
Internet/ConnectionSharing
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Would it be relevant?  Or is there a better solution?


Please advise.  Thanks

Regards
satimis


Edit:
Remark:  Computer 1 and computer 2 are host of VirtualBox.  I'm looking for a solution to set up bridge networking

---

