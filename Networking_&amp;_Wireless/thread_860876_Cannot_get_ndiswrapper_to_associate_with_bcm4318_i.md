---
title: "Cannot get ndiswrapper to associate with bcm4318 in hardy"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by rumman on 2008-07-16
I have a Broadcom BCM4318 card in my Dell Inspiron 710m. It was working fine with Feisty. I did an upgrade to Gutsy and it still worked without having to make any changes. I have been using Ndiswrapper to connect. Now I have upgraded to Hardy and have huge problems.

My ethernet adapter which is a Broadcom 4401 is working fine. But the wifi just refuses. b43-fwcutter did not work so I removed that. I have blacklisted bcm43xx, b43, b43legacy and ssb in /etc/modprobe.d/blacklist

When I do an lshw -C network I get this

 *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 02
       serial: 00:14:22:9a:c2:0d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=10.0.0.86 latency=32 module=ssb multicast=yes

As you can see the wireless is using ssb as its module, but it shows no logical name which should be eth1. If I rmmod b44 and ssb then nothing works. If I then only modprobe ndiswrapper nothing works. As soon as I modprobe b44 both the wireless and ethernet start using ssb.

I have downloaded ndiswrapper 1.50 sources and done a make install. My dmesg shows that 

[   30.139509] ndiswrapper version 1.50 loaded (smp=yes, preempt=no)

However, no matter what I try ndiswrapper fails to associate with eth1 which is my wireless card.

Please HELP.

---

### Post by rumman on 2008-07-16
Ok sorted out some of the mess. Thankfully, I booted into windows by mistake and found that the wireless card was not working there as well. Sorted that out by turning the wifi card on  !!!

Anyway, despite that Hardy still refuses to run the card. So I tried one of the older kernel versions [2.6.22-15-generic] that shows up in GRUB. The result is that the card is discovered at boot up, but then turns off. I have to open up a terminal and do an ifdown eth1 followed by an ifup eth1 to get it working.

So, is this a kernel issue?

---

