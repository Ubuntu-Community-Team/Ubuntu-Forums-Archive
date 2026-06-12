---
title: "Problem with belkin Belkins wireless network card"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by tsillbill on 2008-06-30
Hi, I just installed the new ubuntu on my toshiba laptop. When i was in LiveCD it showed me that i have the belkin network card connected to my laptop, when i installed ubuntu on the laptop it didint show it enymore. Can enyone tell me how to get it working?

network card is belkin and the model no. is F5D7010

---

### Post by ibutho on 2008-06-30
Hi.

You need to let us know which chipset your wireless card uses. Run Applications -> Accessories -> Terminal and enter
```
sudo lshw -C network
```
and
```
sudo lspci | grep -i net
```
Post back the results.

---

### Post by tsillbill on 2008-06-30
*-network               
       description: 802.11g CardBus
       vendor: Broadcom
       physical id: 0
       version: 4.5
       slot: Socket 0
       resources: irq:10
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:73:ab:53
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.66 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:50:34:81:8b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=213.35.133.87 multicast=yes wireless=IEEE 802.11g
silver@silver-laptop:~$ 
silver@silver-laptop:~$ sudo lspci | grep -i net
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
silver@silver-laptop:~$ 


i hope this helps, didnt realy know what i was doing :S

EDIT: in LiveCD it work well.

---

### Post by ibutho on 2008-07-01
I've never used broadcom wireless cards, so can't be of much help. Take a look at this [article]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") and also search on google for "ubuntu+broadcom+4306".

---

