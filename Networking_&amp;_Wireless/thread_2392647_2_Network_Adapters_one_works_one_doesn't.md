---
title: "2 Network Adapters one works one doesn't"
date: 2018-05-23
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2018-05-23
I have a computer with two network adapters, one works and one doesn't.

eth0 is a Realtek RTL8169 PCI Gigabit Ethernet Controller
enp1s0 is an onboard Qualcom  QCA8171 Gigabit Ethernet

The Qualcom is not working

Both are recognized and the drivers seem to be loaded alx in the case of the Qualcom, r8169 in the case of the Realtek

Both are configured as static ip address using /etc/network/interfaces.

I have confirmed the hardware works. If I boot into a Live DVD the interface comes up and works just fine.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# New Onbaord Ethernet Chip
auto enp1s0
iface enp1s0 inet static
 metric 90
 address 192.168.1.26
 netmask 255.255.255.0
#       gateway 192.168.1.1
dns-nameservers 8.8.8.8 8.8.4.4 75.75.75.75 75.75.76.76
#PCI network card
auto eth1
iface eth1 inet static
 metric 100
 address 192.168.1.24
 netmask 255.255.255.0
 gateway 192.168.1.1
dns-nameservers 8.8.8.8 8.8.4.4 75.75.75.75 76.76.76.76
```

ifconfig indicates the interface is up but not running.

```
enp1s0    Link encap:Ethernet  HWaddr 70:85:c2:52:a7:90
          inet addr:192.168.1.26  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18

eth1      Link encap:Ethernet  HWaddr 00:e0:4c:23:2f:4f
          inet addr:192.168.1.24  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe23:2f4f/64 Scope:Link
          inet6 addr: 2603:3001:600:4a00:2e0:4cff:fe23:2f4f/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1916666 errors:0 dropped:4 overruns:0 frame:0
          TX packets:2598754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:564880257 (564.8 MB)  TX bytes:2368940494 (2.3 GB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:845 errors:0 dropped:0 overruns:0 frame:0
          TX packets:845 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:45591 (45.5 KB)  TX bytes:45591 (45.5 KB)
```

You can see that enp1s0 is up but not running.
ifup and ifdown run without error.
```

# ifdown enp1s0
# ifdown enp1s0

```
I've tried a lot of things but can't figure out why this isn't working.
I have confirmed the hardware works. If I boot into a Live DVD the interface comes up and works just fine.

---

### Post by rsteinmetz70112 on 2018-05-24
I discovered on adapter was being manage by network manager and that was causing a conflict with /etc/network/interfaces. removed the configuration form /etc/network/interfaces and everything ifs fine. doing the configuration of that interface through network manager.

---

