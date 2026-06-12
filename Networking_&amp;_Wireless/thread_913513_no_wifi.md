---
title: "no wifi"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by samuelj on 2008-09-07
i tried the steps listed through this link
[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

nothing. starting from the sudo apt-get install build-essential

Then open the terminal from Applications–>Accessories–>Terminal and copy the following command

wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

make i get this:

samuelj@samuelj-mobile:~$ sudo apt-get install build-essential wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
wget is already the newest version.
E: Couldn't find package http:
samuelj@samuelj-mobile:~$ tar xfz madwifi-ng-r2756+ar5007.tar.gz
samuelj@samuelj-mobile:~$ cd madwifi-ng-r2756+ar5007
samuelj@samuelj-mobile:~/madwifi-ng-r2756+ar5007$ make
make: *** No targets specified and no makefile found.  Stop.
samuelj@samuelj-mobile:~/madwifi-ng-r2756+ar5007$ 

when i do iwlist, i get:

samuelj@samuelj-mobile:~$ sudo iwlist scan
[sudo] password for samuelj: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

why is it that everyone else seems to have no problem with configuring their wireless through these steps, but i can't seem to get sh*t accomplished with mine? this is turning into a very frustrating venture




my connection is ADSL through a motorola modem/belkin N router.

hardware is acer aspire 5720z
windows vista was the original OS

ISP is att.net in the US

Ubuntu version is 8.04

if i use the hard wire, i'm great. if not, there is no wifi.

i am connected through the hardwire to get online access at the moment.

lspci output

samuelj@samuelj-mobile:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
07:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:00.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:00.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
samuelj@samuelj-mobile:~$


lsusb output

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

samuelj@samuelj-mobile:~$ lsusb
Bus 007 Device 002: ID 5986:0102 Bison
Bus 007 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 003: ID 413c:3016 Dell Computer Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
samuelj@samuelj-mobile:~$

lshw -class network output

samuelj@samuelj-mobile:~$ lshw -class network
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: NetLink BCM5787M Gigabit Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:05:00.0
logical name: eth0
version: 02
serial: 00:1b:38:55:67:20
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.22 ip=192.168.2.3 latency=0 module=tg3 multicast=yes
*-network UNCLAIMED
description: Ethernet controller
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:06:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0


i do not dual boot to windows.



another issue is my touchpad no longer works. i have had to start using a wired mouse. no clue as to why though. didn't have problems before. i have wiped the drive and reinstalled ubuntu with no luck on that part.

ndiswrapper has done nothing to help.
when i do the ndiswrapper update, the only results i get are
ndisgtk
ndiswrapper-common
ndiswrapper-utils 1.9

iwconfig output-

samuelj@samuelj-mobile:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

samuelj@samuelj-mobile:~$

the wireless driver is the ath5k and i have also tried madwifi under under dreamlinux with no luck.

---

