---
title: "unable to conect to router"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by kennster on 2008-06-15
After coming home from a power outtage my computer was disconnected off line but i dont think i had to log back on so dont think the computer restarted but my mom and sis sed the power just went out for a sec. well now i cant get online with my desktop. olny the mac (this computer) sisters lap top and moms desktop. are all online fine any idea what might have happen? or know a way to get it back on line?

```
laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:73:ca:zc  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0B)  TX bytes:0 (0B)
          Interrupt:22 address:0x2000

eth1        Link encap:Ethernet  HWaddr 00:18:f3:73:d7:eb
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0B)  TX bytes:0 (0B)
          Interrupt:21 address:0x2000

eth0:avah link encap:ethernet HWaddr 00:18:f3:73:ca:2c
                   inet addr:169.254.7.92 Bcast:169.254.255.255 mask:255.255.0.0
                   UP BROADCAST MULTICAST MTU:1500 Metric:1
                   Interrupt:22 base address:0x2000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2743 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15556(15.1 KB)  TX bytes:1556 (15.1 KB)
```

---

### Post by wormser on 2008-06-16
It looks like you are not getting an IP address.  Check your cables.  Try getting one manually with dhclient.

```
sudo dhclient
```

---

