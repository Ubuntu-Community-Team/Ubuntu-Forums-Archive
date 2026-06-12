---
title: "Wireless doesn't works"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by Brunno Silva on 2008-05-07
I have no clue about what's the problem. My wireless connection doesn't works... I have a HP Pavilion dv6745BR Notebook PC and Ubuntu 8.04. I already tried many solutions that appears in Google, but none resolved my problem. Do you have any ideas? I don't know which information is necessary, but you just need to request them that I post here.

---

### Post by chili555 on 2008-05-07
Let's have a look at, from a terminal:```
sudo lshw -C network
```You may omit the parts that describe your ethernet card. Thanks.

---

### Post by Brunno Silva on 2008-05-30
brunno@laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth3
       version: a2
       serial: 00:1e:0b:9b:2b:1f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=half ip=192.168.254.3 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=10MB/s
  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network **DISABLED**
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:1a:73:6e:73:9f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by Positive on 2008-05-30
Does your HP Pavilion dv6745BR have a physical switch to enable/disable wireless card? I'm ona toshiba.... 
Happened to me the first few times. Doh, 

Good luck.

---

### Post by Unix_Slayer on 2008-05-30
> **Brunno Silva said:**
> brunno@laptop:~$ sudo lshw -C network

  *-network **DISABLED**
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:1a:73:6e:73:9f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Logical name should be wlan0. It's coming up a physical wired card.

---

### Post by Unix_Slayer on 2008-05-30
Mine reads as follows:

*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:e5:da:93:86
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2870 driverversion=1.52+Linksys, A Division of Cisc ip=192.168.1.107 link=yes multicast=yes wireless=IEEE 802.11g

---

### Post by chili555 on 2008-05-30
To see if the switch or key combination is set correctly, do:```
sudo cat /var/log/messages | grep switch
```If you see no reference to the wireless switch or rfkill, you are fine.

Do you have the needed firmware installed for your Broadcom? Please do:```
sudo apt-get install b43-fwcutter
```Finally, Network Manager will not manage and connect your wireless as long as you have an IP address wired, which you do:> ip=192.168.254.3 latency=0 link=yesAfter the firmware is installed, detach the wire, reboot and see if your wireless has appeared.

---

### Post by Brunno Silva on 2008-05-31
*-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:1a:73:6e:73:9f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


Thanks a lot!

---

### Post by adden93 on 2008-05-31
[QUOTE=Brunno Silva;5084528]*-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:1a:73:6e:73:9f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Hi im having the exact same problem as the above, and getting the exact same output, but still no internet. Ive followed your steps so far and im getting the same results.

Any help appreciated adden

---

### Post by Unix_Slayer on 2008-05-31
Realtek drivers ==>[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false")

Ralink drivers ==>[http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")

---

### Post by chili555 on 2008-05-31
> **Unix_Slayer said:**
> Realtek drivers ==>[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false")

Ralink drivers ==>[http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")What part of this:> *-network
description: Network controller
product: BCM94311MCG wlan mini-PCI
vendor: Broadcom Corporationis Ralink or Realtek?

---

### Post by Unix_Slayer on 2008-05-31
> **chili555 said:**
> What part of this:is Ralink or Realtek?

The tg3 driver does not support the Broadcom proprietary load balancing software module known as BASP. The Linux bonding driver and 802.1q driver provide similar functionalities and can be used with tg3. BASP will also be discontinued. The tg3 driver also does not support module parameters to configure the device (line speed, flow control, ring sizes, etc) but relies on standard Linux utilities such as ethtool. Other than these differences, the two drivers are very similar in terms of hardware support, robustness, and performance.

This is why the logical name is incorrect. The logical name should be wlan0, but in this situation.... it's coming up eth1. Because the adapter is pci, and wireless, Linux sees it as a wired device. You need to trick it to see it as wlan0. <== Hint Hint


Have you ever seen this. ==> eth0 no wireless extensions  <== Why would eth0 have wireless extensions, if it's not wireless. Think...... it will come to you.

---

### Post by arachal on 2008-05-31
I am new to this system and my wireless lan does not work.  I have a Compaq Presario V4000.  Can anyone help please?:guitar:

---

### Post by Unix_Slayer on 2008-05-31
> **arachal said:**
> I am new to this system and my wireless lan does not work.  I have a Compaq Presario V4000.  Can anyone help please?:guitar:


Chili555... would you like to take this one. You seem to know more about the chips running in these proprietary systems. I build my own, so I know what's going in them.

---

### Post by GoTerpsGo on 2008-05-31
> **chili555 said:**
> To see if the switch or key combination is set correctly, do:```
sudo cat /var/log/messages | grep switch
```If you see no reference to the wireless switch or rfkill, you are fine.

Do you have the needed firmware installed for your Broadcom? Please do:```
sudo apt-get install b43-fwcutter
```Finally, Network Manager will not manage and connect your wireless as long as you have an IP address wired, which you do:After the firmware is installed, detach the wire, reboot and see if your wireless has appeared.

That is so dumb...  You need to have the wired adapter disconnected before the wireless interface gets an address?!?!?!  Well that was the problem for me!  Thx for this little nugget!!!

FYI for anyone else who has my config and would find this useful:

Hardy Heron
Toshiba Satellite A215-S5837 (AMD Turion 64 x2)
Atheros AR5007 chipset
ndiswrapper w/WinXP 64-bit driver (net5211)

And my lshw output is as follows:

  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:cb:65:28
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,06/21/2007,5.3.0.56 ip=10.1.0.203 latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g


The driver is available from the link below:
[http://ubuntuforums.org/showthread.php?t=800686&referrerid=591060](http://ubuntuforums.org/showthread.php?t=800686&referrerid=591060)

Happy camper signing off...  :-D

---

### Post by Unix_Slayer on 2008-05-31
> **GoTerpsGo said:**
> That is so dumb...  You need to have the wired adapter disconnected before the wireless interface gets an address?!?!?!  Well that was the problem for me!  Thx for this little nugget!!!

FYI for anyone else who has my config and would find this useful:

Hardy Heron
Toshiba Satellite A215-S5837 (AMD Turion 64 x2)
Atheros AR5007 chipset
ndiswrapper w/WinXP 64-bit driver (net5211)

And my lshw output is as follows:

  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:cb:65:28
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,06/21/2007,5.3.0.56 ip=10.1.0.203 latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g


The driver is available from the link below:
[http://ubuntuforums.org/showthread.php?t=800686&referrerid=591060](http://ubuntuforums.org/showthread.php?t=800686&referrerid=591060)

Happy camper signing off...  :-D


I knew you could do it big guy. Can't have wired, and wireless running at the same time. Unless you know how to code it properly to run in unison. ;)

---

### Post by Unix_Slayer on 2008-05-31
Just for reference.... my network setting....

```
*-network
                description: Ethernet interface
                product: 82573L Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0a:00.0
                logical name: eth0
                version: 00
                serial: 00:1c:c0:30:b3:dd
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e1000 driverversion=7.3.2 ip=192.168.1.207
*-network
       description: Wireless interface
       physical id: 4
       logical name: wlan0
       serial: 00:1e:e5:da:93:86
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2870 driverversion=1.52+Linksys, A Division of Cisc ip=192.168.1.107 multicast=yes wireless=IEEE802.11g
```



Both running at the same time.

---

### Post by arachal on 2008-06-01
this does not work for me.  It says couldn't find package b-43-fwcutter

---

### Post by unutbu on 2008-06-01
Run this command:

```
pigeon@park:~% apt-cache search fwcutter
bcm43xx-fwcutter - Utility for extracting Broadcom 43xx firmware

```

You are probably looking for bcm43xx-fwcutter.

---

### Post by chili555 on 2008-06-01
> **arachal said:**
> this does not work for me.  It says couldn't find package b-43-fwcutter

Did you look for **b43-fwcutter**, or for b-43-fwcutter?

---

### Post by arachal on 2008-06-01
> **unutbu said:**
> Run this command:

```
pigeon@park:~% apt-cache search fwcutter
bcm43xx-fwcutter - Utility for extracting Broadcom 43xx firmware

```

You are probably looking for bcm43xx-fwcutter.

says pigeon@park: command not found

---

### Post by unutbu on 2008-06-01
Type
```
apt-cache search fwcutter
```
(Sorry, the pigeon@park was part of my command prompt, not the command.)

---

### Post by Unix_Slayer on 2008-06-02
This man hit it right on the head. You might check out this link. ==>[http://ubuntuforums.org/showthread.php?t=815756]("http://ubuntuforums.org/showthread.php?t=815756")

---

