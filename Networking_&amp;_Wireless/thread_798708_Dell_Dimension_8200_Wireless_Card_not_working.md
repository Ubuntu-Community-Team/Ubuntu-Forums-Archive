---
title: "Dell Dimension 8200 Wireless Card not working"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by Redian on 2008-05-18
I just installed (dual boot) Ubuntu 8.04 for my mom on her desktop. She doesn't use the computer much except for the internet. I figured the few times she does use anything else, Ubuntu 8.04 would be a lot fast then Windows XP Home edition. So I installed it, and oddly enough last night I had an internet connection, however this morning there is no connection.
I checked to make sure the cables are all plugged in, and I can be sure the card still works, because going back into Windows I can get on the internet on that machine.
I really don't know what to do, it seems to be using the loopback connection, and judging by the specs of the machine I found, the device drivers it is using are wrong, but I don't know how to verify any of this or change anything (I'm sorta new to the whole Linux thing, but a big Ubuntu fan)
Could someone give me some ideas on how to get an internet connection back? I can run any tests and report back the information here, but I'm not sure where to start. I did notice that the light on the Ethernet port is off if it means anything.

If it helps, here's the ifconfig -a output:
```
laura@laura-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:c0:a8:8a:fb:25  
          inet6 addr: fe80::2c0:a8ff:fe8a:fb25/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xec00 

eth0:avahi Link encap:Ethernet  HWaddr 00:c0:a8:8a:fb:25  
          inet addr:169.254.8.84  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2710 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2710 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 

```

---

