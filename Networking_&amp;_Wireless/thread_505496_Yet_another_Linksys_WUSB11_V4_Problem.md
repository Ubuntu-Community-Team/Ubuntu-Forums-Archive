---
title: "Yet another Linksys WUSB11 V4 Problem"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by markeee on 2007-07-20
I have been trying to setup and configure my Linksys WUSB11 V4 wireless adaper on Kubuntu 7.04 fiesty

lsusb shows: 
[email]mark@kubuntu-laptop:~/.kde[/email]$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 004: ID 13b1:000b Linksys WUSB11 v4.0 802.11b Adapter
Bus 002 Device 001: ID 0000:0000
[email]mark@kubuntu-laptop:~/.kde[/email]$        


i followed the guide at:[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_(ndiswrapper))


'mark@kubuntu-laptop:~/.kde$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)
wusb11v4 : driver installed
        device (13B1:000B) present
[email]mark@kubuntu-laptop:~/.kde[/email]$           '


but i have nothing listed in ifconfig/iwconfig or in knetworkmanager for the device

and lshw -C network does not show it

[email]mark@kubuntu-laptop:~/.kde[/email]$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:47:d2:c5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.46+Broadcom,10/12/2006, 4.100. ip=192.168.1.4 latency=0 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:c0200000-c0203fff irq:18
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:61:4b:d2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 latency=64 multicast=yes
       resources: iomemory:c0300000-c0301fff irq:21
[email]mark@kubuntu-laptop:~/.kde[/email]$     

any ideas greatly appreciated

thanks

mark

---

### Post by markeee on 2007-07-20
bump-anyone?

i removed he driver for my dell wireless card (broadcam) which was setup using ndiswrapper

as i thought maybe this was causing problems with the linksys usb driver with ndiswrapper
so i only had the linksys usb driver installed

but still no wireless interfaces present (when i removed the dell (broadcom) wireless card) iwconfig / ifconfig show no wireless interfaces


someone got a suggestion? as saidive tried everything


followed the instructions, downloaded driver, used ndiswrapper and installed the linksys windows driver, rebooted still nothings

check with ifconfig/iwconfig and lshw -C network - but the device is not even shown in lshw -C network

but if i type lsusb the device is shown as present

mark

---

