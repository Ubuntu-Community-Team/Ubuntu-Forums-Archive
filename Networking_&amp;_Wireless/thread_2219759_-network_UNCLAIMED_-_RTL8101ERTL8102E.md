---
title: "-network UNCLAIMED - RTL8101E/RTL8102E"
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by DXXPublic on 2014-04-25
Hi all, 

Last night the system was working perfectly, i shutted down after an update and then today i eth0 is not starting.  i was hoping if you could shed some light.  Im a beginner with the Linux world and im on the &#314;earning curve, so im pretty much with no clue here.   Can anyone teach me how to solve this problem?

Here is what i see on lswh -C network
```
*-network               
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 64:5a:04:80:7f:7c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.11.0-20-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f7c00000-f7c7ffff memory:f7c80000-f7c8ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Ethernet interface
       physical id: 2
       bus info: usb@4:1
       logical name: eth1
       serial: 8c:ae:4c:fd:21:8a
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ax88179_178a duplex=full ip=192.168.0.109 link=yes multicast=yes port=MII speed=1Gbit/s


```

Thanks in advance

J

---

### Post by varunendra on 2014-04-27
Please post the outputs of -
```
sudo lshw -numeric -C network
lsmod
cat /etc/udev/rules.d/70-persistent-net.rules
```

Does it work if you boot into an older kernel (choosing it from Grub menu, which you can bring up by pressing 'Shift' or 'Esc' key during startup if it doesn't automatically show up)?

---

