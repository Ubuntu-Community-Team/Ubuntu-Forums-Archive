---
title: "Broadcom 1030 not installing"
date: 2015-02-25
forum: Networking &amp; Wireless
---

### Post by barry13 on 2015-02-25
This is an adapter for a Dell Inspiration 1011 mini.  Is there a way to download the driver?

---

### Post by Bucky Ball on 2015-02-25
Welcome. Please open a terminal and provide us with the output of:

```
sudo lshw -C network
```

Thanks.

Also, get online with a cable, do an update and then check 'Additional Drivers'. Is there anything in there for wireless? B43 or STA?

---

### Post by barry13 on 2015-02-25
[COLOR=#000000][FONT=verdana]*-network UNCLAIMED     [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       description: Network controller[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       product: BCM4312 802.11b/g LP-PHY[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       vendor: Broadcom Corporation[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       physical id: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       bus info: pci@0000:03:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       version: 01[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       capabilities: pm msi pciexpress bus_master cap_list[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       configuration: latency=0[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       resources: memory:f0100000-f0103fff[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]  *-network[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       description: Ethernet interface[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       vendor: Realtek Semiconductor Co., Ltd.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       physical id: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       bus info: pci@0000:04:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       logical name: eth0[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       version: 02[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       serial: 00:24:e8:cf:3b:87[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       size: 10Mbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       capacity: 100Mbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       resources: irq:43 ioport:2000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:40600000-4061ffff[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]  *-network[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       description: Wireless interface[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       physical id: 2[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       bus info: usb@1:4[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       logical name: wlan0[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       serial: 00:d0:41:bf:3a:03[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       capabilities: ethernet physical wireless[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]       configuration: broadcast=yes driver=rt73usb driverversion=3.16.0-31-generic firmware=1.7 ip=192.168.1.77 link=yes multicast=yes wireless=IEEE 802.11bg[/FONT][/COLOR][COLOR=#000000][FONT=verdana]
There were no additional drivers when I went on line.[/FONT][/COLOR]

---

### Post by Bucky Ball on 2015-02-25
Try following the instructions for 12.04 and the STA driver from [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29").

---

### Post by Hadaka on 2015-02-26
Hi, please do and post..

```
lspci -n | grep 0280
```
My guess is your bcm4312 card is going to have a pci id of [14e4:4315]
*If so...please remove your current wireless USB dongle and from a working
wired connection,,,if you have one,,if not...leave the dongle in and do,,
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
thanks.

---

### Post by barry13 on 2015-03-01
Tried everything but still can't get wireless card to work.  Is it possible the installer is 64 bit and my netbook is 32 bit?  I'm not computer savvy.

---

### Post by Bucky Ball on 2015-03-01
Don't think 64bit would have installed on a 32bit. You can go the other way around, but not 64bit on 32bit device. You would have gotten an error message when you attempted to install.

Please read and follow Hadaka's instructions in post #5 and report back.

---

### Post by barry13 on 2015-03-01
This time it worked.  Thanks to all.

---

### Post by Bucky Ball on 2015-03-01
Excellent news! Enjoy and good luck. ;)

---

