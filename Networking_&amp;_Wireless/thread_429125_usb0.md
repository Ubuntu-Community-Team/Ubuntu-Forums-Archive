---
title: "usb0"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by U2X001 on 2007-04-30
After upgrading to Feisty NetworkManager Applet is confusing my system by assigning usb0 to my eth0 since my old mobo has a built in networking via usb. I can only connect to the internet by:

sudo dhclient eth0 - this disable usb0 I can now connect to the internet yehey

results of: sudo lshw -C network

 *-network               
       description: Ethernet interface
       product: MX987x5
       vendor: Macronix, Inc. [MXIC]
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth0
       version: 25
       serial: 00:4c:69:6e:75:79
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.14 ip=122.2.95.84 latency=32 maxlatency=56 mingnt=8 multicast=yes
       resources: ioport:c000-c0ff iomemory:ef000000-ef0000ff irq:11
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 66:3a:08:1e:04:29
       capabilities: ethernet physical
       configuration: broadcast=yes driver=usbnet driverversion=22-Aug-2005 firmware=Genesys GeneLink link=yes multicast=yes

How can I permanently disable usb0?

---

### Post by LexRoss on 2008-01-04
I've got the same problem with my 7.10, Gutsy Gibbon system. Any luck fixing this issue?

sudo  lshw -C network
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 78
       serial: 00:03:99:8a:0a:f5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.2.32 latency=32 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: e2:0e:23:ab:3b:df
       capabilities: ethernet physical
       configuration: broadcast=yes driver=gl620a driverversion=22-Aug-2005 firmware=Genesys GeneLink link=yes multicast=yes

---

### Post by oscarw on 2008-02-29
First Post! 
First thanks for all the post, not just here but all over the community. Everything is running for me at last. Think I might have the same prob on Gutsy.

sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: wifi0
       version: 01
       serial: 00:19:e0:68:40:1e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) ip=192.168.1.67 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: d2:c7:d1:88:22:d4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=gl620a driverversion=22-Aug-2005 firmware=Genesys GeneLink link=yes multicast=yes


Either way the fix seemed to work, or perhaps it was just something else. Not that I mind as long as it works.

---

