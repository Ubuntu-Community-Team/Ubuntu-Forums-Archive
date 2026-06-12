---
title: "ipw3945 with ndiswrapper"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by holihue on 2007-06-23
I installed ipw3945 with ndiswrapper(because the driver from restricted drivers manager had bad searching and only 1Mbit in download speed).



And:
```
hk@hk-laptop:~$ ndiswrapper -l
w29n51 : driver installed
hk@hk-laptop:~$ 

```

But:
```
hk@hk-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D3:22:50:34  
          inet addr:192.168.121.32  Bcast:192.168.121.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe22:5034/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:127568 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56741 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:186739050 (178.0 MiB)  TX bytes:4496741 (4.2 MiB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26284 (25.6 KiB)  TX bytes:26284 (25.6 KiB)

hk@hk-laptop:~$ 

```


I haven't eth1.

What is wrong?


I used the Ubuntu guide to install driver with ndiswrapper.






Thanks

---

