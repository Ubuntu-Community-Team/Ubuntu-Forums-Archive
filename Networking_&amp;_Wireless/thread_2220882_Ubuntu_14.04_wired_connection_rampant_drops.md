---
title: "Ubuntu 14.04 wired connection rampant drops"
date: 2014-04-29
forum: Networking &amp; Wireless
---

### Post by bhlee on 2014-04-29
I am using Ubuntu 14.04 LTS and a wired connection. While it works, it frequently drops. My /etc/network/interfaces says only the following:

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

My /etc/NetworkManager/NetworkManager.conf says the following:

```
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=00:14:D1:16:2E:6C,

[ifupdown]
managed=false
```

This is what my "sudo lshw -C network" says:

```
bhlee@bhleeubuntu:~$ sudo lshw -C network
[sudo] password for bhlee: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:21:9b:13:72:9c
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:ce00(size=256) memory:fdeff000-fdefffff memory:fddf0000-fddfffff memory:fdd00000-fdd1ffff
  *-network
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: eth1
       version: 10
       serial: 00:14:d1:16:2e:6c
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:be00(size=256) memory:fdbff000-fdbff0ff
```

Is there a solution to my issue with this newly installed OS? I am using Windows 7 as well, and I have never experienced any drops once the wired connection is established there. Thank you.

---

### Post by cumminsd on 2014-05-02
I am experiencing the same thing on an HP ZBook. Both the wireless and wired networks drop frequently and reconnect. Simple browsing makes this obnoxious, but connecting to an external database or using RDP to get to another machine is extremely painful because the connection has to be re-established over and over again.

Any ideas on what may be causing it?

---

### Post by bhlee on 2014-05-05
I am running Ubuntu 14.04 LTS and Windows 7 on a Dell Vostro 410. I do not have wireless capability on this computer, I believe, due to the lack of a wireless network card.

---

### Post by bhlee on 2014-06-14
It seems that my issue has been resolved. I believe that the reason for the repeated wired connection drops is that a router in my office LAN network had DHCP enabled. Now that it has DHCP disabled, coincidentally or uncoincidentally, I do not get dropped anymore.

---

