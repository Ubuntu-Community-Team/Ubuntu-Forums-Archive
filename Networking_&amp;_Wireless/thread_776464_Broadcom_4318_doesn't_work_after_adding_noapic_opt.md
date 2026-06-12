---
title: "Broadcom 4318 doesn't work after adding noapic option to /boot/grub/menu.lst"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by DerArzt on 2008-04-30
Ever since installing Feisty 7 months ago, when booting, right after grub I've gotten the message MP-BIOS BUG: 8254 timer not connected to IO-APIC. After installing Hardy, it still happened, so I finally got over my 7 month laziness and decided to fix it. Upon researching I found out it was quite an easy fix. Just add the option 'noapic' to defoptions in /boot/grub/menu.lst. Well after doing that and rebooting, my wireless no longer worked. I have a bcm-4318 wireless card. Any one have any suggested fixes? Thanks.
DerArzt

---

### Post by DerArzt on 2008-04-30
anyone?

---

### Post by DerArzt on 2008-04-30
double bump madness

---

### Post by Jamie Jackson on 2008-04-30
Update: Missed it before, but now see you're on Hardy, so you might pass on the following, until the howto solidifies.

For now, though, what's "lshw -C network" show?

----------------------

[This guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") is solid for Edgy, Feisty, and Gutsy, but is currently hit-or-miss with Hardy.

Even if I don't make it back to this thread to help you, this information will help someone else help you, so please list:

Machine Brand and Model
Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
Wireless Chipset: lspci -n | grep '14e4:43'
Ubuntu Version: lsb_release -d
Kernel/architecture (including 32 vs. 64 bit) : uname -mr
Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)

---

### Post by DerArzt on 2008-05-01
Ok, so to install the wireless driver, I just went to hardware drivers, and let it download and install the driver. That worked (for the first time ever). After I did that, i added the noapic option to menu.lst, and upon reboot the wireless card no longer worked. I guess it might also be useful to add that I did a clean install of hardy,  not an update. Once I saw that the noapic option kills my wireless, I removed it again, so I am currently using wireless. 


These are the results of lshw without the noapic option included (so the wireless is obviously working). I can reboot with noapic added and see if there is a difference. I will post the results of lshw with noapic added in a few minutes.

sudo lshw -C network
IDE                       
  *-network        
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:03:25:28:b1:8b
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:08:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:58:04:76
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.5 multicast=yes wireless=IEEE 802.11g

---

### Post by DerArzt on 2008-05-01
So this time, upon re-setting noapic, when i restarted, my wireless network showed up but it wouldn't connect. Here is the lshw for it. I haven't even compared them myself yet, so they may be identical.

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:03:25:28:b1:8b
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:08:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:58:04:76
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by DerArzt on 2008-05-01
As to the other info:

lspci | grep Broadcom
08:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

lspci -n | grep '14e4:43'
08:07.0 0280: 14e4:4318 (rev 02)

lsb_release -d
Description:	Ubuntu 8.04

uname -mr
2.6.24-16-generic i686

I am running the 32bit version

I have a gateway mx-7118 laptop

---

### Post by DerArzt on 2008-05-02
And one last bump

---

### Post by DerArzt on 2008-07-07
Still havent solved it.. PleASE HELP

---

### Post by Ayuthia on 2008-07-07
> **DerArzt said:**
> So this time, upon re-setting noapic, when i restarted, my wireless network showed up but it wouldn't connect. Here is the lshw for it. I haven't even compared them myself yet, so they may be identical.

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:03:25:28:b1:8b
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:08:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:58:04:76
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

The results show that b43 is being used.  If you are using NDISwrapper based on Jamie Jackson's suggestion, you can try the following:
```
modprobe -r b43 b44 ssb bcm43xx ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
```
If that works, you can add the info in Version 0.3 of this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Version%200.3](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Version%200.3)

---

