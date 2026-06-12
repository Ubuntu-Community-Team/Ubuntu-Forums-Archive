---
title: "New Install, no wireless, HELP!"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by nylenny on 2008-07-26
I have a Compaq F700 with a built-in Atheros AR5007 wireless card. When I book Kubuntu, the card is not initialized or activated.  How can I get and install a driver for this interface?

Any help would be appreciated.:confused::confused:

---

### Post by superprash2003 on 2008-07-26
to get the exact name go to the terminal and type lshw -C network and post output

---

### Post by nylenny on 2008-07-27
> **superprash2003 said:**
> to get the exact name go to the terminal and type lshw -C network and post output

lenny@ubuntu:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:eb:cb:0d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.254.6 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0


THANKS FOR YOUR HELP

---

### Post by superprash2003 on 2008-07-28
read this
[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)
[http://lampcomputing.com/getting-ar242x-80211abg-wireless-pci-express-adapter-work-fedora-9](http://lampcomputing.com/getting-ar242x-80211abg-wireless-pci-express-adapter-work-fedora-9)

---

### Post by nylenny on 2008-07-28
:) :) :)
SUCCESS!!!  YOU ROCK!

THANKS!

:guitar: :guitar: :guitar:

---

