---
title: "WiFi disabled after everytime I boot Ubuntu 16.04"
date: 2017-06-25
forum: Networking &amp; Wireless
---

### Post by arindam1997007 on 2017-06-25
I did already post this question yesterday, but since I got only one reply, which didn't work for me,  I'm asking it again. Really hoping, you guys would be able to help me.
I'm a new Ubuntu user and have been using it just for the past 2  days. I saw that my wifi strength is much superior in windows than in  Ubuntu. So, I thought of updating the wireless driver in Ubuntu. I am having a problem that my network is disabled after boot. I'm  currently running dual boot with Windows 8.1. Here's the output of ```
sudo lshw -C network
``` :

  > *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: enp8s0
       version: 07
       serial: 38:63:bb:72:97:97
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:4000(size=256) memory:b5600000-b5600fff memory:b5400000-b5403fff
  *-network DISABLED
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eno1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN latency=0 multicast=yes wireless=Ralink STA
       resources: irq:16 memory:b5510000-b551ffff
  After I boot, I need to run these 2 commands:
  ```
sudo ifconfig eno1 up 
sudo service network-manager restart

```  It's really frustrating, that I need to run these 2 commands,  everytime I boot my laptop. It started happening after I installed the  rt3290 drivers as mentioned here [https://askubuntu.com/a/593018/692756](https://askubuntu.com/a/593018/692756)
  After the commands, here's the output of ```
sudo lshw -C network
``` :

  > *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: enp8s0
       version: 07
       serial: 38:63:bb:72:97:97
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:4000(size=256) memory:b5600000-b5600fff memory:b5400000-b5403fff
  *-network
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eno1
       version: 00
       serial: c0:38:96:6e:ae:d7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN ip=192.168.225.110 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:16 memory:b5510000-b551ffff

I did as stated here : [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
And here's my pastebin link with all of my networking data: [http://paste.ubuntu.com/24949971/](http://paste.ubuntu.com/24949971/)

---

### Post by howefield on 2017-06-25
Duplicate thread closed.

---

