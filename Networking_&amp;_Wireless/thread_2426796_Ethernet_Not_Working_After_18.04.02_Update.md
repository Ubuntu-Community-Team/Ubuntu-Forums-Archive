---
title: "Ethernet Not Working After 18.04.02 Update"
date: 2019-09-13
forum: Networking &amp; Wireless
---

### Post by theasianmamba24 on 2019-09-13
When I reinstalled Ubuntu Budgie 18.04.2, the wired connection was working as I downloaded software updates during the installation. However, the wired connection did not connect. Here's my log when I executed the command  ```
lshw -C network
```

```

  *-network
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 63
       serial: 0c:8b:fd:0e:0e:07
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.0.0-27-generic firmware=17.948900127.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:49 memory:b0500000-b0501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:05:00.1
       logical name: enp5s0f1
       version: 14
       serial: 08:9e:01:c3:cf:b4
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:19 ioport:3000(size=256) memory:b0404000-b0404fff memory:b0400000-b0403fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:7
       logical name: wlx409bcd056453
       serial: 40:9b:cd:05:64:53
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8xxxu driverversion=5.0.0-27-generic firmware=N/A ip=172.18.144.61 link=yes multicast=yes wireless=IEEE 802.11

```

And here's what I got when I ran ```
discover
``` (Via apt install discover)

```

Intel Corporation Lynx Point-LP PCI Express Root Port 3 
Intel Corporation Lynx Point-LP USB xHCI HC 
Intel Corporation Haswell-ULT Integrated Graphics Controller 
Intel Corporation Lynx Point-LP USB EHCI #1 
unknown unknown 
Intel Corporation Haswell-ULT DRAM Controller 
Intel Corporation Lynx Point-LP SMBus Controller 
Intel Corporation Lynx Point-LP PCI Express Root Port 4 
Intel Corporation Lynx Point-LP HD Audio Controller 
Intel Corporation Lynx Point-LP HECI #0 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Intel Corporation Lynx Point-LP LPC Controller 
Intel Corporation Lynx Point-LP PCI Express Root Port 1 
Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] 
Linux Foundation 3.0 root hub 
unknown unknown 
unknown unknown 
Logitech, Inc. Wireless Mouse M305 
unknown unknown 
unknown unknown 
Linux Foundation 2.0 root hub 
unknown unknown 
Linux Foundation 2.0 root hub 

```

May I know how I can resolve this issue? Thank you in advance.

---

### Post by theasianmamba24 on 2019-09-13
It seems like I have fixed the issue by downloading Ukuu and upgrading my kernel to the latest version. Now it works like a charm.

[https://github.com/teejee2008/ukuu/releases](https://github.com/teejee2008/ukuu/releases)

---

