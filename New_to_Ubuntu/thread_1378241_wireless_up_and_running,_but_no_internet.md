---
title: "wireless up and running, but no internet"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by michelvb on 2010-01-11
Hi,
Could anyone help to get my internetconnection working?
I just installed ubuntu 9.10 on a Acer Aspire 9500. It connects to the wireless router (a Speedtouch 580) without problems. i can see the router, and the other PCs. However, I can't get passed the router onto the nternet. Tried to ping the dns server of the provider but it says Network is unreachable.
All works fine for the windows PCs (sorry to say ;))

I ran various of the diagnostic commands (meaning little to me), see below the result

Euh, help?
Michel



michel@laptop1:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:95:8d:64
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:21 ioport:8000(size=256) memory:bc020000-bc0200ff memory:90000000-9001ffff(prefetchable)
  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wmaster0
       version: 01
       serial: 00:14:a4:54:39:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.67 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:bc010000-bc01ffff

michel@laptop1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:95:8d:64  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a4:54:39:02  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a4ff:fe54:3902/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1139 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1006 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:166611 (166.6 KB)  TX bytes:115792 (115.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A4-54-39-02-35-34-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

michel@laptop1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:95:8d:64  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a4:54:39:02  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a4ff:fe54:3902/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1139 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1006 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:166611 (166.6 KB)  TX bytes:115792 (115.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A4-54-39-02-35-34-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by lolekbolek4 on 2010-01-11
Try to unplug router and modem from electricity for 30sec. It helped me when i could connect to wireless router but had no internet access. Your router settings could be wrong also.

---

### Post by michelvb on 2010-01-11
amazing, that indeed solved it. :o
tried al sorts of restarts, but not the router (as it worked fine for the xp machine)

Thanks!
Michel

---

