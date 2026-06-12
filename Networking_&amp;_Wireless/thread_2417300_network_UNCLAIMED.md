---
title: "network UNCLAIMED"
date: 2019-04-22
forum: Networking &amp; Wireless
---

### Post by geanwinchester on 2019-04-22
[COLOR=#212121][FONT=arial]
Hello!

I'm having trouble with my wired network card.I already installed 3 different distro and in all the wired network does not work, however the wireless network works normally."In Windows the wired internet works without any problem" Only in linux that is giving this problem.until last month it was working![/FONT][/COLOR]


lshw -C network
  *-network UNCLAIMED       
       description: Ethernet controller
       product: Ethernet Connection I217-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:f7c00000-f7c1ffff memory:f7c3d000-f7c3dfff ioport:f080(size=32)
  *-network
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 18:cf:5e:cf:55:45
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=4.19.0-parrot1-20t-amd64 firmware=N/A ip=10.0.0.208 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:18 ioport:e000(size=256) memory:f7b00000-f7b03fff

---

### Post by TheFu on 2019-04-22
```
$ lshw -C network
*-network UNCLAIMED
description: Ethernet controller
product: Ethernet Connection I217-V
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
version: 05
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list
configuration: latency=0
resources: memory:f7c00000-f7c1ffff memory:f7c3d000-f7c3dfff ioport:f080(size=32)
```
Shows that no driver is being loaded.
Here's what my Intel NIC looks like:```

$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: **I211 Gigabit** Network Connection
       vendor: **Intel** Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 03
       serial: 0c:9d:cc:dd:dd:xx
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=igb driverversion=5.4.0-k **duplex=full firmware=0. 6-1 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:29 memory:f6600000-f661ffff ioport:d000(size=32) memory:f6620000-f6623fff
```

You need to determine the correct driver and have it loaded.  [https://ubuntuforums.org/showthread.php?t=2280968](https://ubuntuforums.org/showthread.php?t=2280968) shows the steps that someone else with that NIC took to solve the issue. Chilli is good.  Notice that the driver is very different from mine, so be certain to use the correct driver.  It is fairly well supported, IME on other systems.

---

### Post by chili555 on 2019-04-22
What is the exact response to the terminal command:```
sudo modprobe e1000e
```Thanks.

---

