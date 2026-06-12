---
title: "Wireless Card - Best Method"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by alligoodw on 2008-09-29
Problem:  Wireless card not detected.

I have a HP Pavilion dv6000.  My wireless card is a Atheros AR5007.  I'm dual-booting with Windows Vista and Linux Mint 5 on top of Ubuntu 8.04.  This is my second installation of Linux Mint.  Why?  After several attempts of trying to get my wireless working and in order, I messed up my system (Linux).  This is a second attempt to get this hardware up and running.  

For this type of laptop and wireless card, what is the best method of installation:  WICD, Ndiswrapper, Madwifi, or Network Manager? Having determined this, I need the following:

I need someone to help me get it up and running.  Do I need to disabled restricted drivers regarding the Atheros card? What commands do I need to issue to determine the state of my system?  I need step by step instructions.  Preferably, I need someone with a successful installation of the Atheros card.

Believe me, any help provided will be deeply appreciated.

---

### Post by superprash2003 on 2008-09-29
in your terminal type lshw -C network and post output

---

### Post by alligoodw on 2008-09-29
> **superprash2003 said:**
> in your terminal type lshw -C network and post output

Here you go - 

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:73:53:79
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.103 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

---

### Post by mykrob on 2008-09-29
I just did this same wifi card on my friends laptop. Here's the instructions i used:

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

works flawlessly with the native madwifi driver.

---

### Post by superprash2003 on 2008-09-30
[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

---

