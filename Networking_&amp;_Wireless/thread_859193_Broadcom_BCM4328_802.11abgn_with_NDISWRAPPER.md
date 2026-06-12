---
title: "Broadcom BCM4328 802.11a/b/g/n with NDISWRAPPER"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by casibbald on 2008-07-14
Hi Guys,

After trying to get my Broadcom BCM4328 802.11a/b/g/n to work with NDISwrapper and failing a number of times I decided to document this for others.

I am running a Acer Ferrari 1100, on Hardy 8.04 64bit and this may have a slightly different adapter from what you have but hope this helps.

This procedure is based on a new install, do not install any restricted drivers or anything else till you have got this working as some restricted drivers seem to mess things up. I discovered this after 8 attempts...and even verified this by doing this all again with restricted drivers installed first. You will be able to install your restricted stuff after this is complete.

I used the following cab driver pack (32 & 64Bit)
[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-53245-1&lc=en&cc=us&dlc=en&product=3650146&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-53245-1&lc=en&cc=us&dlc=en&product=3650146&os=228&lang=en)

Do not use the driver on the acer site or possibly even your own manufacturers site, use the one above from HP.

Download and copy the file to:
/usr/src/wireless

get cabextract files:
# sudo apt-get install cabextract

extract your files when in /usr/src/wireless
# sudo cabextract sp36684.exe

# sudo ndiswrapper -i bcmwl5.inf
# ndiswrapper -l
# sudo depmod -a
# sudo modprobe ndiswrapper
# sudo cp /etc/network/interfaces /etc/network/interfaces.orig
# echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
# sudo ndiswrapper -m
# echo 'ndiswrapper' | sudo tee -a /etc/modules
# echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

If all has gone well you should be able to run:
# lshw -C network

#####################
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:14:a6:64
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.23 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:1e:4c:a3:ef:68
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,07/11/2007, 4.150. ip=192.168.105.244 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
##############

reboot and start your machine...

My machine has a hardware switch and for some reason it needs to be off, for the wireless to work...go figure...so not sure how it switches it on...so the hardware wireless light must be off.

good luck.

---

### Post by JZhou on 2008-07-15
It works very well and I don't even have to reboot. I am using Xubuntu AMD64 hardy on Macbook3,1.

This is a great post, saving a lot of my time. Many thanks!

---

### Post by ibnuariff on 2008-07-22
There's a slightly easier way of doing this. First of all, the step is the same until extracting the driver. 

After that, go to package manager and search for ndiswrapper. Download ndiswrapper as well as the NDISGTK. 

After installing go to System > Administration > Windows Wireless Drivers

Click on Install New Driver and tell the utility where is the .inf file. 

Note:
1. I disabled restricted driver as the original guide
2. Tested on Acer Ferrari 1000 with Ubuntu 8.04 64bit

Anyway, thanks a lot to cassibald who worked this out in the first place!

---

