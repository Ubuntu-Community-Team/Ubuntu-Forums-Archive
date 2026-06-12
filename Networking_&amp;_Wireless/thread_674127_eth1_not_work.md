---
title: "eth1 not work"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by srknc on 2008-01-21
Hi,
(ubuntu server 7.10)
I have 2 ethernet cards called eth0 and eth1. I'm using eth0 normally for using internet.
I want to use this machine as an firewall so add a new ethernet card and connect it an other open computer. But ethernet link led doesn't work.
What is the problem?

ifconfig->
[I]eth0      Link encap:Ethernet  HWaddr 00:0C:76:16:3F:9D  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fe16:3f9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5148 (5.0 KB)  TX bytes:4736 (4.6 KB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:08:54:3D:01:B7  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
[/I]

interfaces->
[I]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
                address 192.168.2.2
                netmask 255.255.255.0
                gateway 192.168.2.1



auto eth1
iface eth1 inet static
                address 192.168.0.1
                netmask 255.255.255.0
[/I]

---

### Post by burbankmarc on 2008-01-22
You might need to use a cross-over cable.

---

### Post by srknc on 2008-01-22
Are you sure, why?

---

### Post by burbankmarc on 2008-01-22
Because ethernet to ethernet card you need a cross-over cable, unless the card is auto-sensing, which most of the newer ones are. But you said the leds aren't even lighting up when you plug it in, so it leads me to believe it's some kind of physical problem.

---

