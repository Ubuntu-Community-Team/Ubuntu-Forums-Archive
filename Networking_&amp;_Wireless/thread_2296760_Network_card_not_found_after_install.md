---
title: "Network card not found after install"
date: 2015-09-28
forum: Networking &amp; Wireless
---

### Post by Alban_de_Boissiere on 2015-09-28
Hello,

I successfully installed ubuntu on my acer 5560 but I am unable to connect to wireless networks. No wireless networks are shown. I am currently on a wired connection, which works. 
I am new to this world. I made some research but without success. I would be much obliged if you could guide my through this.

Thanks' !

---

### Post by Bucky Ball on 2015-09-28
*Thread moved to **Networking & Wireless**.*

Welcome to the forums. Please open a terminal (you should find it by searching in Dash or in Accessories) and copy/paste this:

```
sudo lshw -C network
```

Please post the result back here, thanks, between code tags (control+shift+c to copy from the terminal). See the last link in my signature for how to create code tags.

---

### Post by Alban_de_Boissiere on 2015-09-29
This is what I have :

```

  *-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 20:6a:8a:71:2e:5e
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=sb ip=192.168.0.24 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:11 memory:f0000000-f000ffff memory:f0010000-f001ffff memory:b0000000-b00007ff
  *-network
       description: Network controller
       product: BCM43227 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:11 memory:f0100000-f0103fff



```

---

### Post by Hadaka on 2015-09-29
Hi,from a working wired connection please COPY and paste the following
one line at a time.
```
sudo apt-get update
sudo apt-get install linux-headers-generic
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
disconnect the wired connection
boot and test wireless

---

