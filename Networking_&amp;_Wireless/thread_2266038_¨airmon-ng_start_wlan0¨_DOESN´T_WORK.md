---
title: "¨airmon-ng start wlan0¨ DOESN´T WORK"
date: 2015-02-19
forum: Networking &amp; Wireless
---

### Post by unkn0wn4u on 2015-02-19
Helle, so here is my problem when i type
```
root@unkn0wn4u-brain:~/rtl8812au# airmon-ng start wlan0


Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
697    avahi-daemon
704    avahi-daemon
899    NetworkManager
29518    dhclient


Interface    Chipset        Driver



```
There is no interface

I work with a wifi adapter (WLA-2104)
iwconfig
```
root@unkn0wn4u-brain:~/rtl8812au# iwconfig
eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.


```
ifconfig
```

root@unkn0wn4u-brain:~/rtl8812au# ifconfig
eth0      Link encap:Ethernet  HWaddr 64:d1:a3:23:b3:a2  
          inet addr:192.168.43.215  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::66d1:a3ff:fe23:b3a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10875 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7450293 (7.4 MB)  TX bytes:1473932 (1.4 MB)

eth1      Link encap:Ethernet  HWaddr 08:00:27:35:67:df  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:126854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104280206 (104.2 MB)  TX bytes:4241792 (4.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:380203 (380.2 KB)  TX bytes:380203 (380.2 KB)

```

---

### Post by Bucky Ball on 2015-02-19
*Thread closed.*

Discussions regarding airmon-ng (aircrack) are not supported on these forums. You could try the aircrack or Kali forums. From the forum Code of Conduct:
> 
Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

Good luck.

---

