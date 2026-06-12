---
title: "AR242x can see wireless networks but won't connect"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by opivy522 on 2008-08-08
I am having problems connecting to any wireless network.  I can find the networks but cannot connect to any of them. This is my lshw -C network. *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:7c:27:6d
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.108 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:e1:85:70:fc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.51+,06/21/2007,5.3.0.56 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

Any help would be greatly appreciated.

---

### Post by opivy522 on 2008-08-08
I got my wireless working fine now I used this forum.
[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

---

### Post by chili555 on 2008-08-08
Excellent! Please note that when a new kernel is included in an update, you will need to do a slightly modified version of the install again:```
cd ~/madwifi-hal-0.10.5.6
**make clean**
make
sudo make install
sudo depmod -ae

```

---

