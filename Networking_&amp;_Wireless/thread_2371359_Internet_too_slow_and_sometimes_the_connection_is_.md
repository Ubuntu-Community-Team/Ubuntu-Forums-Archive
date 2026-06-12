---
title: "Internet too slow and sometimes the connection is dropped"
date: 2017-09-13
forum: Networking &amp; Wireless
---

### Post by einarromero-0 on 2017-09-13
I'm moving from Windows 10 with an ASUS A455LF, there i had to disable the Bluethoot all the time to get the WiFi working properly


Here in DeepIn i've tried the same, but it doesn't work, the navegation turn too slow most of the time and have weak signal even near to router, and sometimes connection is lost with "802.1X" error, after that, it doesn't recognize any WiFi conection and the only way to get it works again is rebooting the PC


By the way, with the LAN conection everything goes fine


My hardware info:
```
*-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 10
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=192.168.1.88 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:47 ioport:e000(size=256) memory:f7204000-f7204fff memory:f7200000-f7203fff
  *-network
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.1.60 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:19 memory:f7100000-f7107fff

```


Already tried:
1. Fix the bug in Debian Avahi-daemon
```
sudo gedit /etc/nsswitch.conf

```Replacing
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```with```

hosts:          files dns

```

2. Disabling the network maganer and installing WICD
```
sudo apt-get install wicd
sudo systemctl eneable NetworkManager.service

```

Please, help me

---

