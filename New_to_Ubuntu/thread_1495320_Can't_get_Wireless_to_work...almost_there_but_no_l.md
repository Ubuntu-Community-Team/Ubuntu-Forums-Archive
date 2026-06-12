---
title: "Can't get Wireless to work...almost there but no luck..."
date: 2010-05-27
forum: New to Ubuntu
---

### Post by vpr80 on 2010-05-27
I am so close, but I just can't seem to get it to work. I got the BCMWL drivers installed on my Dell D620, but it still won't connect. Here is the output from LSHW, can someone help. Why does it say network DISABLED at the bottom for Wireless interface? Thanks

lenny@lenny-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:ab:2c:b9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=5752-v3.19 ip=192.168.1.157 latency=0 multicast=yes
       resources: irq:27 memory:efcf0000-efcfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7d:38:04:af
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by SlidingHorn on 2010-05-27
> **vpr80 said:**
> *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7d:38:04:af
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

according to your lshw, the wireless isn't using any driver.  Did you install it with ndiswrapper?

---

### Post by vpr80 on 2010-05-28
nevermind...seems to have started working by itself....i don't get it, but it work.

---

