---
title: "D-link card freezing system"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by decker405 on 2007-05-22
[SIZE="2"]Alright, I've searched around for 2 days now, and I can't find anything related to
 this problem.  My D-Link WNA-1330 worked right out of the box, even with WPA.  
But then, the internet disconnected, I tried to reconnect, it failed, and the system
froze.  
Now, whenever I get disconnected from wireless or insert the
wireless card (pcmcia) the system completely freezes, mouse and everything
and I have to reboot.  But strangely it only freezes right when I insert it, the system 
still boots with it in and connects to wireless with it.

I am using a Toshiba Satellite A45-S121, Feisty Fawn Ubuntu, Kernel 2.6.20-15-generic

I've only been on linux for a week or so now, I've tried to do most of the things 
myself but here I have no idea haha...hope I gave you enough information 
but not too much...[/SIZE]

lspci shows this:

       ```
 02:00.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC 
        (rev 01)
        Subsystem: D-Link System Inc Unknown device 3a1c
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at 40000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
```
ifconfig shows this:

```
ath0      Link encap:Ethernet  HWaddr 00:15:E9:73:AD:D2  
          inet addr:192.168.0.185  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:e9ff:fe73:add2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2950 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2718 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2472235 (2.3 MiB)  TX bytes:389443 (380.3 KiB)

eth0      Link encap:Ethernet  HWaddr 00:08:0D:85:94:D0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0:avah Link encap:Ethernet  HWaddr 00:08:0D:85:94:D0  
          inet addr:169.254.8.18  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:610 (610.0 b)  TX bytes:610 (610.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-15-E9-73-AD-D2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18175 errors:0 dropped:0 overruns:0 frame:651
          TX packets:3330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:5862575 (5.5 MiB)  TX bytes:484313 (472.9 KiB)
          Interrupt:16
```

---

