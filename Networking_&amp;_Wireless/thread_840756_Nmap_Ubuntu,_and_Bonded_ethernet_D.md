---
title: "Nmap Ubuntu, and Bonded ethernet :D"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by earthmeLon on 2008-06-25
Hey, recently Bonded my two ethernet cards and now nmap spits out this error:

```

Starting Nmap 4.53 ( http://insecure.org ) at 2008-06-25 17:12 CDT
Failed to find device eth1 which was referenced in /proc/net/route
Failed to find device eth1 which was referenced in /proc/net/route

vi /proc/net/route

Iface   Destination     Gateway         Flags   RefCnt  Use     Metric  Mask            MTU     Window  IRTT                                                    
bond0   0001010A        00000000        0001    0       0       0       00FFFFFF        0       0       0                                                       
eth1    0000FEA9        00000000        0001    0       0       0       0000FFFF        0       0       0                                                       
bond0   0000FEA9        00000000        0001    0       0       1000    0000FFFF        0       0       0                                                       
bond0   00000000        0101010A        0003    0       0       100     00000000        0       0       0                                                       
eth1    00000000        00000000        0001    0       0       1000    00000000        0       0       0                                                       



```

Any suggestions?

---

### Post by earthmeLon on 2008-06-27
bump :D

---

