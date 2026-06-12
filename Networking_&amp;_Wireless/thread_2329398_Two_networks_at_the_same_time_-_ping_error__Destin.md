---
title: "Two networks at the same time - ping error:  Destination Host Unreachable"
date: 2016-07-01
forum: Networking &amp; Wireless
---

### Post by ravaelman on 2016-07-01
[COLOR=#242729][FONT=Arial]I installed linux on my computer/home server. I want to connect the computer to two networks: the raspberry (LAN) and the Internet (ethernet USB - modem Huawei E303).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My problem:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Once everything is correctly, while other times I have an error when I go on any website:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][B]ERR_ADDRESS_UNREACHABLE
[B]
and ping e.g google werbsite:[/B][/B][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]**  Destination Host Unreachable**[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]It helps to reset network:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]sudo service networking restart[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What may be the problem? I can not reset the entire connection "networks" because I lose my connection with the raspberry, and this is a very important connection for the server / computer.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have a configuration in / etc / network / interfaces:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]eth0 - Raspberry[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]eth1 - Internet
[/FONT][/COLOR]
```
auto lo
iface lo inet loopback

auto eth1
allow-hotplug eth1
iface eth1 inet dhcp

auto eth0
iface eth0 inet static
address 10.42.0.5
netmask 255.255.255.0
gateway 0.0.0.0

```

[FONT=Arial]ifconfig:

[/FONT]```

eth0      Link encap:Ethernet  HWaddr 00:26:22:1c:c2:73  
          inet addr:10.42.0.5  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:22ff:fe1c:c273/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2163 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:11340 (11.0 KiB)  TX bytes:142861 (139.5 KiB)

eth1      Link encap:Ethernet  HWaddr 00:1e:10:1f:00:00  
          inet addr:192.168.8.100  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:10ff:fe1f:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10789933 (10.2 MiB)  TX bytes:5075482 (4.8 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:20350 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7067502 (6.7 MiB)  TX bytes:7067502 (6.7 MiB)
```

---

