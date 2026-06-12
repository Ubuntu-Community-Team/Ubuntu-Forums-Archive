---
title: "Wifi driver and network setting"
date: 2013-09-29
forum: Networking &amp; Wireless
---

### Post by Nitin_Navneet on 2013-09-29
I am new user of Ubuntu and Linux
I have just installed ubuntu on Compaq 6710b laptop. I can't access Wifi. 
Need to check whether wifi driver installed and working
How I can set up wifi. It was earlier working with Windows

---

### Post by Bucky Ball on 2013-09-29
*Thread moved to **Networking & Wireless**.*

Welcome. Please open a terminal and copy/paste these commands, one at a time hitting return in between. Post the results back here between ```
 tags.
[code]
iwconfig
sudo lshw -C network
```

---

### Post by Nitin_Navneet on 2013-09-29
iwconfig response 

lo  no wireless extension
eth0 no wireless extensions

---

### Post by Nitin_Navneet on 2013-09-29
lshw - C network

*-network UNCLAIMED    
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:e4100000-e4103fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:18:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:4b:88:e6:bd
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 firmware=sb v2.09 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:e4000000-e400ffff

---

### Post by Bucky Ball on 2013-09-29
Do an update with a cable plugged in (through update manager) then check 'Additional Drivers' for anything that says 'B43' in it.

The other option is to install (through Software Centre or Synaptics):

b43-fwcutter
b43-firmware-installer

Restart. Working? That card ( BCM4311 802.11a/b/g) *should* work out of the box.

---

### Post by Hadaka on 2013-09-29
Hi, from a wired connection to the internet please do..
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree 
sudo modprobe b43
```
dissconnect your wired connection, your
wrieless should be working.
thanks.

---

### Post by Nitin_Navneet on 2013-09-29
I am not having plugged network. 

I installed b43-fwcutter

using dpkg -i b43-fwcutter. 

But how can I check if same got installed correctly. 

When trying to install firmware-b43-installer, it is giving error
(Reading database ... 143118 files and directories currently installed.)
Preparing to replace firmware-b43-installer 1:015-9 (using firmware-b43-installer_015-9_all.deb) ...
Unpacking replacement firmware-b43-installer ...
Setting up firmware-b43-installer (1:015-9) ...
No chroot environment found. Starting normal installation
This card work with newer 5.10.56.27.3 firmware. Trying to install it.
--2013-09-30 02:08:21--  [http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2)
Resolving mirror2.openwrt.org (mirror2.openwrt.org)... failed: Name or service not known.
wget: unable to resolve host address `mirror2.openwrt.org'
dpkg: error processing firmware-b43-installer (--install):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 firmware-b43-installer

---

### Post by Nitin_Navneet on 2013-09-29
b43-fwcutter -v 

result 

b43-fwcutter version 015

Does it mean fwcutter is properly installed?

If I am trying to install 

sudo apt-get -i b43-fwcutter 

I am getting similar error no Chroot environment found 

Do I need to reinstall b43-fwcutter

---

### Post by Hadaka on 2013-09-29
Hi, follow this link post #10
[http://ubuntuforums.org/showthread.php?t=2176558](http://ubuntuforums.org/showthread.php?t=2176558)

---

