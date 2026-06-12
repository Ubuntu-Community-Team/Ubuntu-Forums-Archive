---
title: "Fixed sound but now lost wireless"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by QPRWinst on 2008-11-27
Hi all

I have a problem with my new ubuntu notebook.  When it first booted up there was a message saying updates available, so i duly downloaded and updated.  This though caused me to lose all sound.  After a couple of days trying anything and everything I finally fixed the sound with

sudo apt-get install linux-ubuntu-modules-2.6.24-19-*    (got that from linux.dsplabs.com.au)

But i think this must of been like using a hammer to turn a screw because although sound works now i have lost my wireless connection.  I have also noticed that the hardware drivers section is now empty whereas there was a couple of entries there before.

$ iwconfig     gives me...
lo        no wireless extensions.

eth1      no wireless extensions.

$ cat /etc/*rel*      gives me....
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

~$ dpkg -l |grep linux-ubuntu         gives me...
ii  linux-ubuntu-modules-2.6.24-19-lpia       2.6.24-19.29netbook13                      Ubuntu supplied Linux modules for version 2.
ii  linux-ubuntu-modules-2.6.24-19-lpiacompat 2.6.24-19.28                               Ubuntu supplied Linux modules for version 2.


$ dpkg -l |grep linux-restricted   gives me....
ii  linux-restricted-modules-2.6.24-19-lpia   2.6.24.13-19.45netbook4                    Non-free Linux 2.6.24 modules on LPIA
ii  linux-restricted-modules-common           2.6.24.13-19.45netbook4                    Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-lpia             2.6.24.19.21                               Restricted Linux modules for LPIA

I am new to all this and really would appreciate any pointers/assistance.

Cheers

---

### Post by Ayuthia on 2008-11-27
Can you let us know what your wireless card is?  Please post the results of:
```
lspci -nn
lshw -C network
```
This will help us identify your wireless card along with which driver it is using.

---

### Post by QPRWinst on 2008-11-27
Hi

lspci -nn  gives me....

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)


lshw -C network
bash: lshw: command not found


thank you

---

### Post by QPRWinst on 2008-11-28
found lshw in synaptics package manager.  now i get....

WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 02
       serial: 00:1e:33:71:90:e0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.10 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

cheers

---

### Post by QPRWinst on 2008-11-28
UPDATE

downloaded a restricted module that said something about madwifi and after reboot I now have a couple of entries in Hardware Drivers but still no wireless shown in network settings.

---

### Post by QPRWinst on 2008-11-28
UPDATE

Uninstalled all the modules and then reinstalled but no change.
Tried to follow instructions in the Atheros thread but this did not work either.

Dont want to resort to restore disk as you dont learn how to fix doing that.  

help me obi-wan kenobi , youre my only hope.

---

### Post by QPRWinst on 2008-11-29
anyone any ideas?

---

