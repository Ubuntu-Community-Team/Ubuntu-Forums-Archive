---
title: "Wifi adaptor behaving randomly on Ubuntu 14.04"
date: 2015-09-21
forum: Networking &amp; Wireless
---

### Post by Ardnag on 2015-09-21
Hi,

I've recently installed ubuntu 14.04 on my HP laptop(Not dual boot, just ubuntu) and i'm new to ubuntu

[B]Problems with Wifi:
[/B]**. **Sometimes the Ubuntu boots with wifi enabled and connected to the network but not able to browse the internet(No problem with router/provider because i can browse net on other laptop)
. Sometimes i can browse internet for a short period of time and it disconnects without reconnecting 
. Sometimes wifi adapter gets disabled when i suspend the system or put to sleep
. Sometimes it boots with adapter disabled and cant be enabled even by pressing the hardware switch


- After searching on this site i tried some random suggestions like changing config file in /etc/modprobe.d/iwlwifi.conf
- After this the wifi adapter stopped working(Always in disabled mode)

So I've reinstalled ubuntu but wifi adaptor is not getting enabled

I've tried below commands but nothing is shown, even the wireless script doesn't show anything

. rfkill list
. lspci -nn | grep -i network

With  **sudo lshw -C network **command i get

> *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 2c:27:d7:03:13:17
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:25 ioport:2000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff





Please help

Thanks :)





[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by jeremy31 on 2015-09-21
See if removing the wifi card and reinstalling it in the motherboard helps.  There may be an access panel on the bottom of the laptop to remove and there is normally one screw securing the wifi card

---

### Post by Ardnag on 2015-09-21
I've reinserted it. Wifi is on and connected. Will post again if the connection is not stable.

Thanks man :)

---

