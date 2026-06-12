---
title: "RTL8188EE Wireless Adapter not working in Ubuntu 14.04.5 LTS"
date: 2017-10-18
forum: Networking &amp; Wireless
---

### Post by kkisha2s on 2017-10-18
Hi,

I've been running Ubuntu 14.04 for some time and now wifi adapter is not working. I couldn't see any available wi-fi to connect to. The output to the command 

```
sudo lshw -C network
```

is as follows:

  *-network               
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 07
       serial: 58:20:b1:7e:86:19
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-1_0.0.1 06/29/12 ip=192.168.2.109 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:4000(size=256) memory:c5000000-c5000fff memory:c5100000-c5103fff

  *-network UNCLAIMED
       description: Network controller
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0d:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:c3000000-c3003fff

Any help would be much appreciated! :)

---

### Post by jeremy31 on 2017-10-18
The first thing I would try is ```
sudo apt-get install --reinstall linux-image-extra-$(uname -r)
```
Reboot if there are no errors

---

### Post by kkisha2s on 2017-10-19
Thanks a lot! Worked like a charm! :)

---

### Post by vasa1 on 2017-10-19
[How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

