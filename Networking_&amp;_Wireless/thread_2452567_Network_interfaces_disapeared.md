---
title: "Network interfaces disapeared"
date: 2020-10-24
forum: Networking &amp; Wireless
---

### Post by Will_Moonen on 2020-10-24
Team,

This morning I discovered a strange problem.
One of the Ubuntu servers "lost" 4 network interfaces.

The command "lspci | grep -i eth" is still showing the card of these interfaces:
```
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
0a:00.0 Ethernet controller: Intel Corporation 82576 Gigabit Network Connection (rev 01)
0a:00.1 Ethernet controller: Intel Corporation 82576 Gigabit Network Connection (rev 01)
0c:00.0 Ethernet controller: Intel Corporation 82576 Gigabit Network Connection (rev 01)
0c:00.1 Ethernet controller: Intel Corporation 82576 Gigabit Network Connection (rev 01)
```

However, the command "ip link show" shows only the first interface (among the local and a few KVM/bridge interfaces):
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp7s0: <BROADCAST,MULTICAST,PROMISC,UP,LOWER_UP> mtu 1500 qdisc fq_codel master LAN state UP mode DEFAULT group default qlen 1000
    link/ether 04:92:26:4a:f2:06 brd ff:ff:ff:ff:ff:ff
7: DMZ: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DEFAULT group default qlen 1000
    link/ether fe:54:00:45:9f:50 brd ff:ff:ff:ff:ff:ff
8: LAN: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DEFAULT group default qlen 1000
    link/ether 04:92:26:4a:f2:06 brd ff:ff:ff:ff:ff:ff
9: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default qlen 1000
    link/ether 52:54:00:38:f2:14 brd ff:ff:ff:ff:ff:ff
10: virbr0-nic: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel master virbr0 state DOWN mode DEFAULT group default qlen 1000
    link/ether 52:54:00:38:f2:14 brd ff:ff:ff:ff:ff:ff
11: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master LAN state UNKNOWN mode DEFAULT group default qlen 1000
    link/ether fe:54:00:18:7e:29 brd ff:ff:ff:ff:ff:ff
12: vnet1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master DMZ state UNKNOWN mode DEFAULT group default qlen 1000
    link/ether fe:54:00:45:9f:50 brd ff:ff:ff:ff:ff:ff
```

The file /etc/network/interface is still showing these interfaces (all in promisc mode - as by design):
```
auto enp10s0f0
iface enp10s0f0 inet manual
up /sbin/ifconfig enp10s0f0 promisc on

auto enp10s0f1
iface enp10s0f1 inet manual
up /sbin/ifconfig enp10s0f1 promisc on

auto enp11s0f0
iface enp11s0f0 inet manual
up /sbin/ifconfig enp11s0f0 promisc on

auto enp11s0f1
iface enp11s0f1 inet manual
up /sbin/ifconfig enp11s0f1 promisc on
```

What is happening? Any suggestions?


Thank you - Will

---

### Post by TheFu on 2020-10-25
Which release?  17.10 and later use netplan, not the interfaces file unless you go out of your way to retain that. At least that's my understanding. 
[https://wiki.ubuntu.com/MigratingToNetplan](https://wiki.ubuntu.com/MigratingToNetplan)
[https://www.linuxjournal.com/content/have-plan-netplan](https://www.linuxjournal.com/content/have-plan-netplan)

Do you have auto-package installs enabled?

---

### Post by Will_Moonen on 2020-10-25
I have 18.04-LTS installed - updated (and rebooted) last Saturday.
This is coming from 16.04 and has no netplan installed.
And yes - auto-package installs is enabled.

---

