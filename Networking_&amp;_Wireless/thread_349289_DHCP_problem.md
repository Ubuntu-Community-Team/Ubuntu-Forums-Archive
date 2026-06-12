---
title: "DHCP problem"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by KocetoNs on 2007-01-30
Hi, i`ve installed ubuntu 6.10.Now i have one majour problem....there is no internet :(
My ISP is useing a dhcp server.

```
masterx@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:EE:EA:A6  
         inet6 addr: fe80::20f:eaff:feee:eaa6/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:15729 errors:0 dropped:0 overruns:0 frame:0
         TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:950237 (927.9 KiB)  TX bytes:2520 (2.4 KiB)
         Interrupt:217 Base address:0x4000

lo        Link encap:Local Loopback  
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:2 errors:0 dropped:0 overruns:0 frame:0
         TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
         NOARP  MTU:1480  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

Sorry for bad english & 10x for the answers.

---

### Post by inCursorated on 2007-01-30
Hi. DHCP should work automatically... you can initiate it manually with the command
```
dhclient eth0
```

---

### Post by KocetoNs on 2007-01-30
```
masterx@ubuntu:~$ dhclient eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted

```

Permission?

---

### Post by inCursorated on 2007-01-30
do it as root or use sudo
```
sudo dhclient
```

---

### Post by KocetoNs on 2007-01-30
> **inCursorated said:**
> do it as root or use sudo
```
sudo dhclient
```

problem solved 10x everyone :)

---

