---
title: "ifup permission denied"
date: 2015-09-30
forum: Networking &amp; Wireless
---

### Post by spandan_pradhan on 2015-09-30
I tried using ifup command to enable ethernet which showed permission denied error, later i found out that cable was unplugged. Even after plugging back the cable and internet working, i am not being able to do ifup or ifdown command. Following is the error :

[B] ifdown eth0
ifdown: failed to open lockfile /run/network/.ifstate.lock: Permission denied

sudo ifdown eth0
[sudo] password for spandanpradhan: 
ifdown: interface eth0 not configured

[/B]

---

### Post by kerry_s on 2015-09-30
sudo ifup eth0
sudo dhclient eth0

(not sure if you need to do dhclient anymore, might be automatic from just bringing it up)

---

### Post by spandan_pradhan on 2015-09-30
@kerry_s: I can't use both ifdown or ifup command. If i do sudo ifup eth0 it says 

sudo ifup eth0
Ignoring unknown interface eth0=eth0.

and ifdown shows
[B]ifdown eth0
ifdown: failed to open lockfile /run/network/.ifstate.lock: Permission denied

[/B]Ubuntu 12 had no such problem

---

### Post by kerry_s on 2015-09-30
in terminal:
ifconfig -a

so we can see what you got.

---

### Post by spandan_pradhan on 2015-10-02
~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr e4:11:5b:4c:11:68  
          inet addr:202.79.36.199  Bcast:202.79.36.255  Mask:255.255.255.0
          inet6 addr: fe80::e611:5bff:fe4c:1168/64 Scope:Link
          inet6 addr: fec0::c:2df0:6c7d:2c5f:5d8a/64 Scope:Site
          inet6 addr: fec0::c:e611:5bff:fe4c:1168/64 Scope:Site
          inet6 addr: 2002:ca4f:249e:c:e611:5bff:fe4c:1168/64 Scope:Global
          inet6 addr: 2002:ca4f:249e:c:2df0:6c7d:2c5f:5d8a/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1483602 errors:0 dropped:0 overruns:0 frame:0
          TX packets:906945 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1840159348 (1.8 GB)  TX bytes:96664750 (96.6 MB)
          Interrupt:20 Memory:d4800000-d4820000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:127307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:127307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12029250 (12.0 MB)  TX bytes:12029250 (12.0 MB)

wlan0     Link encap:Ethernet  HWaddr 24:77:03:5c:7a:50  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by chili555 on 2015-10-02
ifup and ifdown are used to control interfaces declared in the file /etc/network/interfaces. In systems running Network Manager, this doesn't include eth0.

As you can see, the interface is already up:> eth0 Link encap:Ethernet HWaddr e4:11:5b:4c:11:68 
inet addr:202.79.36.199 Bcast:202.79.36.255 Mask:255.255.255.0
inet6 addr: fe80::e611:5bff:fe4c:1168/64 Scope:Link
inet6 addr: fec0::c:2df0:6c7d:2c5f:5d8a/64 Scope:Site
inet6 addr: fec0::c:e611:5bff:fe4c:1168/64 Scope:Site
inet6 addr: 2002:ca4f:249e:c:e611:5bff:fe4c:1168/64 Scope:Global
inet6 addr: 2002:ca4f:249e:c:2df0:6c7d:2c5f:5d8a/64 Scope:Global
[COLOR="#FF0000"]UP[/COLOR] BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
<snip>What are you trying to do?

---

