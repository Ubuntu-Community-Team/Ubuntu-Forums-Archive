---
title: "cannot connect eth0 after rebooting."
date: 2014-08-22
forum: Networking &amp; Wireless
---

### Post by arief_wibowo2 on 2014-08-22
sorry if my english bad

i have problem with my eth0,
I use ubuntu version 14:04 

network smoothly at first, but when I reboot. 
suddenly there was a notice out "Disconnected / Offline". 

I checked all the cables and routers, all running smoothly 
but why still disconnect? 

and then I try to use windows xp to test the cable. 
result in windows all smooth, no problems whatsoever ..

following log results
```

bowoekren@kitkat$ sudo ifup eth0

Ignoring unknown interface eth0=eth0.

bowoekren@kitkat$



bowoekren@kitkat$ sudo ifconfig eth0 up

bowoekren@kitkat$ sudo ifconfig eth0 down

bowoekren@kitkat$ sudo ifconfig eth0 up



root@kitkat:/media/bowoekren/Data/Linux Bak# ip link show eth0

2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT group default qlen 1000

    link/ether 00:24:88:10:17:b4 brd ff:ff:ff:ff:ff:ff





root@kitkat:/media/bowoekren/Data/Linux Bak# ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:24:88:10:17:b4  

          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0

          BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:5 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:300 (300.0 B)  TX bytes:0 (0.0 B)



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:65536  Metric:1

          RX packets:497 errors:0 dropped:0 overruns:0 frame:0

          TX packets:497 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:39247 (39.2 KB)  TX bytes:39247 (39.2 KB)



root@kitkat:/media/bowoekren/Data/Linux Bak# 
root@kitkat:/media/bowoekren/Data/Linux Bak# /etc/init.d/network-interface start

start: Rejected send message, 1 matched rules; type="method_call", sender=":1.106" (uid=999 pid=5510 comm="start network-interface ")



```

how to resolve this problem? 
I can not surf the internet

Thanks before

---

### Post by varunendra on 2014-08-25
Please post back the outputs of -
```
nm-tool
sudo ethtool eth0
```

---

