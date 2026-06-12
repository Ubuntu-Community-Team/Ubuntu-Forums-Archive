---
title: "drivers for Broadcom 802.11g Network Adapter"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by coasterfanryan on 2007-08-05
I can't find a driver for  Broadcom 802.11g Network Adapter for Ubuntu 7.04 Feisty Fawn I use with Wubi. I have searched google and haven't found anything. has anyone else found a driver for this network adapter. If anyone has could you let me know please. thank you

---

### Post by noob12 on 2007-08-05
We need to see more about the specific device.  Can you post the output of these commands
```

lspci -nn
lshw -C network

```

---

### Post by coasterfanryan on 2007-08-06
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: eth1
       version: 01
       serial: 00:14:a5:f8:b6:58
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=0 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:50000000-50003fff irq:17
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:4a:47:5b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.103 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:2000-20ff iomemory:d0100000-d01000ff irq:20
ryan@ubuntu:~$

---

### Post by noob12 on 2007-08-06
OK.  There are basically two camps on that.

One camp uses the Feisty-shipped linux driver with firmware installed separately.  See this post for a HOWTO which lots of people have reported following with success: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

The other camp uses ndiswrapper + Windows drivers.

I would recommend you first try the post above, and if that doesn't work for you we can lead you through the ndiswrapper method.

---

### Post by coasterfanryan on 2007-08-12
thank you very much

---

### Post by misfitpierce on 2007-08-12
Usually you can just enter this in terminal as well...

sudo apt-get install bcm43xx-fwcutter...

works like a charm for me

---

### Post by euler_fan on 2007-08-12
Assuming you have a Broadcom 4318 wireless chipset, the following is a great link . . . 

[which is right here]("http://ubuntuforums.org/showthread.php?t=197102")

---

### Post by coasterfanryan on 2007-08-12
I just used it and I an now on wifi thank you again  =)

---

