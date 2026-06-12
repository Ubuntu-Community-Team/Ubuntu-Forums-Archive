---
title: "Sony VPC190X Ubuntu 14.04  trying to set a script to run in /etc/network/if-up.d brok"
date: 2014-11-24
forum: Networking &amp; Wireless
---

### Post by matt158 on 2014-11-24
Hello World,

I am trying to get a simple script to run when I establish an Internet connection.  Found a few walkthroughs recommending to put it in if-up.d and mke various changes to NetworkManager.conf and interfaces.  Never got the script to run, but over the course of testing I noticed I cannot connect over ethernet.  I am not sure I I ever have been, I may have just noticed for the first time today.  

NetworkManager.conf
```
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=F0:BF:97:E4:E3:4C,

[ifupdown]
managed=true

```

Interfaces
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
    up fund_price_update
```

Script
```
#!/bin/sh

OUTFILE=~/Documents/Banking/quotes.csv

wget -O $OUTFILE "http://www.finance.yahoo.com/d/quotes.csv?s=EDJI+GOOG&f=snd1l1c1&e=.csv"

```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr f0:bf:97:e4:e3:4c  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::f2bf:97ff:fee4:e34c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20967 (20.9 KB)  TX bytes:16112 (16.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1449 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:126709 (126.7 KB)  TX bytes:126709 (126.7 KB)


```

---

