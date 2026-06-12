---
title: "Swapped network adapter settings, now things are wonky with eth1"
date: 2013-09-10
forum: Networking &amp; Wireless
---

### Post by miked187 on 2013-09-10
/etc/network/interfaces

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.56.59
netmask 255.255.255.0
gateway 192.168.56.1

# second interface
auto eth0
iface eth1 inet static
address 192.168.1.159
netmask 255.255.255.0
gateway 192.168.1.1
dns_nameservers 8.8.8.8


```

output of "lshw -C network"
```

  *-network:0
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 02
       serial: 08:00:27:97:75:6d
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full ip=192.168.56.59 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:10 memory:f0000000-f001ffff ioport:d010(size=8)
  *-network:1
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: eth1
       version: 02
       serial: 08:00:27:e6:b0:ca
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full ip=192.168.1.159 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:9 memory:f0820000-f083ffff ioport:d040(size=8)


```

 I can ping 192.168.56.1, which I'd expect, successfully -- but I can also ping 192.168.1.1 which is only routed via eth1

result of ifup-v eth1

```
 
root@ubuntu:~# ifup -v eth1
Configuring interface eth1=eth1 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
ip addr add 192.168.1.159/255.255.255.0 broadcast 192.168.1.255           dev eth1 label eth1
RTNETLINK answers: File exists
Failed to bring up eth1.

```

ifdown -v eth1
```

ifdown: interface eth1 not configured
root@ubuntu:~#

```

wth am I missing??

TIA

---

### Post by ian-weisser on 2013-09-11
Well, you are probably missing assigning MAC to NIC in /etc/udev/rules.d/70-persistent-net.rules

---

