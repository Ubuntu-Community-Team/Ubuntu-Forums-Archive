---
title: "wifi doesn´t work"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by radeque on 2008-07-12
hello, 
i have a problem with my laptop..it says the wifi card is not recognized, i don´t know which driver i have to download..
my laptop is: Acer Extensa 5220-101G12Mi (LX.E870C.034)
the wifi type is: Acer InviLink, 802.11b/g
Thanks for advice

---

### Post by superprash2003 on 2008-07-12
in your terminal type lshw -class network and post output here

---

### Post by radeque on 2008-07-12
vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:16:be:dd
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.23 ip=85.132.249.197 latency=0 module=tg3 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

---

### Post by superprash2003 on 2008-07-12
follow this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by bobdobbs on 2008-08-01
I also have an extensa 5220.

It turned out that I had an inbuilt broadcom card, with an atheros chipset.

I had no luck at all with the ndiswrapper way of doing things.

Apparently, these units require the madwifi drivers.

I managed to make some progess by going through this document:
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

Unfortunatly, you have to kinda outside the ubuntu way of doing things. Rather than using apt or synaptic you have to compile and install the drivers yourself.

Fortunatly, the madwifi package maintainers provide simple and good instructions which walk you through the scripts.

I am now at the point where after I load the ath_pci module, I can see a couple of new wireless interfaces when I use ifconfig.

Trouble is, I haven't worked out how to configure the interface yet.
Unfortunately, ubuntu doesn't really seem to have wireless network configuration utilities. Nothing intuitive to me, anyway.

Now that I can see the interface with ifconfig, I'd like to be able to scan for networks and connect to them. But I haven't figured that out yet.

As much as I like linux and especially ubuntu, wireless networking in ubuntu is a pain.

---

