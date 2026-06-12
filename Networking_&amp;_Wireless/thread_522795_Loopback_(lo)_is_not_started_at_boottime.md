---
title: "Loopback (lo) is not started at boottime"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by oliver.d on 2007-08-11
Hello to everyone,
I´ll have a problem with the looback interface. It is not startet while booting. After boot ifconfig 
shows up all eth0:y interfaces. 

```
[CODE]eth0      Link encap:Ethernet  HWaddr qq:qq:qq:qq:qq:qq
          inet addr:xx.xxx.xx.6  Bcast:xx.xxx.xx.31  Mask:255.255.255.224
          inet6 addr: xxxx::xxxx:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16420 (16.0 KiB)  TX bytes:25303 (24.7 KiB)
          Interrupt:185 Base address:0xe000

eth0:1    Link encap:Ethernet  HWaddr qq:qq:qq:qq:qq:qq
          inet addr:xx.xxx.xx.114  Bcast:xx.xxx.xx.119  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:185 Base address:0xe000

eth0:2    Link encap:Ethernet  HWaddr qq:qq:qq:qq:qq:qq
          inet addr:xx.xxx.xx.115  Bcast:xx.xxx.xx.119  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:185 Base address:0xe000

eth0:3    Link encap:Ethernet  HWaddr qq:qq:qq:qq:qq:qq
          inet addr:xx.xxx.xx.116  Bcast:xx.xxx.xx.119  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:185 Base address:0xe000

eth0:4    Link encap:Ethernet  HWaddr qq:qq:qq:qq:qq:qq
          inet addr:xx.xxx.xx.117  Bcast:xx.xxx.xx.119  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:185 Base address:0xe000

eth0:5    Link encap:Ethernet  HWaddr qq:qq:qq:qq:qq:qq
          inet addr:xx.xxx.xx  Bcast:xx.xxx.xx.119  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:185 Base address:0xe000
```

Entering ifconfig lo up enables the loopback adaper and he is shown by ifconfig.
```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```[/CODE]

What I expect is that the lo interface is started at boottime. My /etc/network/interfaces look like this:
```
# Loopback device:
auto lo
iface lo inet loopback

# device: eth0
auto eth0
iface eth0 inet static
address xx.xxx.xx.6
broadcast xx.xxx.xx.31
netmask 255.255.255.224
gateway xx.xxx.xx.1

auto eth0:1
iface eth0:1 inet static
address  yy.yyy.yyy.114
gateway yy.yyy.yyy.113
netmask 255.255.255.248

auto eth0:2
iface eth0:2 inet static
address yy.yyy.yyy.115
netmask 255.255.255.248

auto eth0:3
iface eth0:3 inet static
address yy.yyy.yyy.116
netmask 255.255.255.248

auto eth0:4
iface eth0:4 inet static
address yy.yyy.yyy.117
netmask 255.255.255.248

auto eth0:5
iface eth0:5 inet static
address yy.yyy.yyy.118
netmask 255.255.255.248
```

---

