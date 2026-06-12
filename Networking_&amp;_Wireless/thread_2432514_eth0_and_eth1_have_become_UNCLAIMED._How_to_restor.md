---
title: "eth0 and eth1 have become UNCLAIMED. How to restore?"
date: 2019-12-03
forum: Networking &amp; Wireless
---

### Post by crazybear on 2019-12-03
somehow I made eth0 and eth1 disappear while struggling to make the wifi work!....they are now listed as UNCLAIMED.  Please, how do I fix this? I need them!! the MAC addresses they had can  be found in the lower part of the window.

```

$ sudo lshw -c network
  *-network               
       description: Wireless interface
       product: RTL8812AE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 01
       serial: 04:d4:c4:13:c1:51
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8821ae driverversion=4.15.0-70-generic firmware=N/A ip=192.168.1.24 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:36 ioport:ee00(size=256) memory:fbefc000-fbefffff
  *-network _**UNCLAIMED**_
       description: Ethernet controller
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:be00(size=256) memory:fbaff000-fbafffff memory:fbaf8000-fbafbfff memory:fbb00000-fbb1ffff
  *-network_** UNCLAIMED**_
       description: Ethernet controller
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:ae00(size=256) memory:fb8ff000-fb8fffff memory:fb8f8000-fb8fbfff memory:fb900000-fb91ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: virbr0-nic
       serial: 52:54:00:2b:2f:a7
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s
[SIZE=5][U][B]
how they were...[/B][/U][/SIZE]

  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 03
       serial: 00:24:1d:ce:b6:64
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw  latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:be00(size=256) memory:fbaff000-fbafffff memory:fbaf8000-fbafbfff memory:fbb00000-fbb1ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:1d:ce:b6:66
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw  latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:17 ioport:ae00(size=256) memory:fb8ff000-fb8fffff memory:fb8f8000-fb8fbfff memory:fb900000-fb91ffff

```

---

### Post by chili555 on 2019-12-03
Revise the blacklist as exlained in your other thread.

---

### Post by jeremy31 on 2019-12-03
I wonder why the dkms didn't work, something to look at later

---

### Post by crazybear on 2019-12-04
> **chili555 said:**
> Revise the blacklist as exlained in your other thread.

Can you be more specific. I saw something about downloading a driver and then running some terminal commands. But I want to make sure I'm using the correct driver - the note on the driver I think you are referring to talks about using for ones that don't work with the drivers built in to the kernels and my LAN ports were always working before without any new driver...so I'm worried it might not be the correct one. How can I find out for sure before doing this. The instructions for removing the driver were complex indeed! Thanks and sorry for the caution. I'm no pro.

---

### Post by chili555 on 2019-12-04
> **crazybear said:**
> Can you be more specific. I saw something about downloading a driver and then running some terminal commands. But I want to make sure I'm using the correct driver - the note on the driver I think you are referring to talks about using for ones that don't work with the drivers built in to the kernels and my LAN ports were always working before without any new driver...so I'm worried it might not be the correct one. How can I find out for sure before doing this. The instructions for removing the driver were complex indeed! Thanks and sorry for the caution. I'm no pro.Please see post #87 here: [https://ubuntuforums.org/showthread.php?t=2431415&page=2&p=13913598#post13913598](https://ubuntuforums.org/showthread.php?t=2431415&page=2&p=13913598#post13913598)

You may safely copy and paste the command into the terminal; press Enter; reboot. You should be all set.

---

