---
title: "Avahi .local"
date: 2013-10-14
forum: Networking &amp; Wireless
---

### Post by Maher_Elaissi on 2013-10-14
[COLOR=#000000]Hi,
I'm new user of linux, and I installed Ubuntu v 12.4 and I have wireless network issue, everytime I switch on my laptop I get this message :
"current network has a .local domain, which is not recommended plus[/COLOR][COLOR=#000000] incompatible with Avahi network[/COLOR][COLOR=#000000]....."
Internet still works but after a while it stops.
any help with this
thank in advance[/COLOR]

---

### Post by Maher_Elaissi on 2013-10-15
Please can anyone guide me through this.
Thanks

---

### Post by steeldriver on 2013-10-15
Hello and welcome to the forum

I don't think your internet problems are likely to be related to the avahi error message - the avahi service is only needed to allow name-based lookup of LAN devices and services (like local printers).

I suggest you post more info about your wireless hardware, either using [varunendra's wireless script]("http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385") or by running the following commands in a terminal and posting the output here:

```

sudo lshw -sanitize -C network

lspci -vnn | grep '\[02[08]0\]'

```

If you still want to address the avahi issue, if you are using your ISP's suggested DNS servers the first thing I'd suggest is changing those to Google or OpenDNS servers. If that doesn't work then there are options to configure avahi to use an alternate suffix.

---

### Post by Maher_Elaissi on 2013-10-17
sudo lshw -sanitize -C network  *-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: [REMOVED]
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 firmware=sb latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:c0430000-c043ffff memory:c0440000-c044ffff memory:c0450000-c04507ff
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205 [Taylor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: [REMOVED]
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-31-generic firmware=18.168.6.1 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:42 memory:c0500000-c0501fff

lspci -vnn | grep '\[02[08]0\]'
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0082] (rev 34)


this is the output I get, sorry for this delay :)

---

