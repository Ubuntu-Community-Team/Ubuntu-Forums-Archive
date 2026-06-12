---
title: "Compaq Presario v5000 Wireless"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by metalsonic84 on 2011-02-28
I searched and saw other topics about the same trouble getting the broadcom wireless card working in the Compaq Presario v5000. I downloaded the driver through the administration/additional drivers. I now see the networks but when i try to connect it will attempt for a while then fail to. What am i needing to do  differently?

---

### Post by TeoBigusGeekus on 2011-02-28
What's your wireless card?
```
lshw -C network
```

---

### Post by metalsonic84 on 2011-02-28
*-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:fb:77:4f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:7e:a0:ba
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg

---

### Post by TeoBigusGeekus on 2011-02-28
I'd recommend [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

---

### Post by Matt__ on 2011-02-28
Any of these of use to you?

[Broadcom BCM43XX Wireless Driver for Ubuntu 10.10](http://www.downloadatoz.com/driver/articles/broadcom-bcm43xx-wireless-driver-for-ubuntu-10-10.html)

or [B43 fwcutter](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

or
[Broadcom in 10.04](http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO:+Broadcom)

---

