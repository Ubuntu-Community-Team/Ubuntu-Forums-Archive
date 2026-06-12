---
title: "Need Help Installing TRENDnet TEW-421PC"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by John GT on 2007-08-31
Hi,
I am a beginning Ubuntu user. I am having trouble installing a TRENDnet TEW-421PC wireless card. I have tried sugestions on the forumns, as well as the articles in the wiki and support documentation.

Here is what makes my case different from those previously addressed:
[LIST=1]
[*]My card version is C1.0R, the page link is [http://www.trendnet.com/asp/download_manager/list_subcategory.asp?SUBTYPE_ID=106](http://www.trendnet.com/asp/download_manager/list_subcategory.asp?SUBTYPE_ID=106)
[*]The current version of ndiswrapper is 1.47, not 1.27
[/LIST]

Now, here is my System Configuration:
Dell Latitude C810
512 RAM
40 GB HDD
1.83 GHz Pentium 3
Ubuntu 7.04

Here is the result of an lspci command:
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
02:06.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
02:06.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)


I understand that the Ethernet controller should be different, but it is not. (this command was run with the card inserted)

I hope someone can help me. Thank You

John

---

### Post by CourtD on 2007-08-31
I have the same type of card and have looked it up and found that it was a ACX 111 based card, and got the module almost completely set up using [this ]("https://help.ubuntu.com/community/WifiDocs/Driver/acx111") tutorial. Sadly, it gets held up when I try to compile the module by putting in ```
make -C /lib/modules/`uname -r`/build M=`pwd`
``` it replies ```
make: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  LD      /root/ACX/built-in.o
  CC [M]  /root/ACX/wlan.o
  CC [M]  /root/ACX/conv.o
  CC [M]  /root/ACX/ioctl.o
  CC [M]  /root/ACX/common.o
/root/ACX/common.c:6944:14: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/root/ACX/common.c: In function ‘acx_init_task_scheduler’:
/root/ACX/common.c:6943: error: ‘INIT_WORK’ undeclared (first use in this function)
/root/ACX/common.c:6943: error: (Each undeclared identifier is reported only once
/root/ACX/common.c:6943: error: for each function it appears in.)
make[1]: *** [/root/ACX/common.o] Error 1
make: *** [_module_/root/ACX] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
root@court-laptop:~/ACX# sudo make -C /lib/modules/`uname -r`/build M=`pwd` modules_install
make: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  DEPMOD  2.6.20-16-generic
make: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
```

Try that tutorial, and if it works for you great, if it doesn't, lame. Either way, is there someone out there who can help us?

Court

---

### Post by John GT on 2007-09-01
Thanks, I may try that. After I posted, I was able to get the card set up and work (using the instructions on the NDISwrapper website, quote below). Somehow, though, I deleted the driver and when I re-booted, it did not work. The graphical version of NDISwrapper would not open, not matter how I tried it. I spent forever re-installing & un-installing it. I finally re-installed Ubuntu. Now, even though I have the card in, the computer will not recognize it AT ALL!!!!!!!!! Does anyone know how to make Ubuntu recognize that the card is inserted? If I can do that, I can make it work.

Also, does anyone know if the USB equivalent of this card by TRENDnet works any better? CompUSA has both on sale for $3 and I may just go get one of those.

Here are the instructions for this card from the NDISwrapper website:


Card: Trendnet TEW-421PC Wireless CardBus Card

    *
      Chipset: Texas Instruments ACX 111 54Mbps
    *
      pciid: 104c:9066
    *
      Driver: Driver for the Airlink+ 802.11g Model AWLH3025 ([http://www.airlinkplus.com/driver/11g/awlh3025_v6_0_5_30_xp.zip](http://www.airlinkplus.com/driver/11g/awlh3025_v6_0_5_30_xp.zip)) works very well including WEP.
    *
      Other: Tested on a Dell Latitude 400CS running Debian Linux/testing with kernel 2.6.10 with ndiswrapper-1.2rc1.

---

### Post by John GT on 2007-09-01
I have finally figurred it out!
Try the link below for help:
[http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html](http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html)

---

### Post by Count Doofus on 2007-10-25
Thumbs down  Re: Trendnet wireless pc card TEW - 421PC
Hey I got my trendnet 421pc card running using a broadcom 43xx python script. Here's is what i did to get it going on my machine.

Use Synaptics package manager to download the latest Kernel

Let's make sure the network manager is up o date

Bla@Bla-Bla:~$ sudo apt-get install network-manager-gnome

Reading package lists... Done
Building dependency tree
Reading state information... Done
network-manager-gnome is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

lets see if you device was--11ab:1faa (rev 03) Capabilities: <access denied> -- like mine was


Bla@Bla-Bla:~$ lspci -n

00:00.0 0600: 1039:0650 (rev 11)
00:01.0 0604: 1039:0001
00:02.0 0601: 1039:0962 (rev 04)
00:02.1 0c05: 1039:0016
00:02.3 0c00: 1039:7007
00:02.5 0101: 1039:5513
00:02.6 0703: 1039:7013 (rev a0)
00:02.7 0401: 1039:7012 (rev a0)
00:03.0 0c03: 1039:7001 (rev 0f)
00:03.1 0c03: 1039:7001 (rev 0f)
00:03.2 0c03: 1039:7001 (rev 0f)
00:03.3 0c03: 1039:7002
00:0f.0 0200: 14e4:4401 (rev 01)
00:10.0 0607: 1524:1411 (rev 01)
00:10.1 0501: 1524:0510
01:00.0 0300: 1039:6325
02:00.0 0200: 11ab:1faa (rev 03) Capabilities: <access denied>

Bla@Bla-Bla:~$ sudo lspci -s 02:0.0 -v

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
Subsystem: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless
Flags: 66MHz, medium devsel, IRQ 16
Memory at 24000000 (32-bit, non-prefetchable) [disabled] [size=64K]
Memory at 24010000 (32-bit, non-prefetchable) [disabled] [size=64K]
Capabilities: [40] Power Management version 2

Open up the modules files and add the 88w8335 to the end of the list

sudo gedit /etc/modules

Bla@-Bla-Bla:~$ sudo lshw -C network

*-network
description: Ethernet interface
product: BCM4401 100Base-T
vendor: Broadcom Corporation
physical id: f
bus info: pci@00:0f.0
logical name: eth0
version: 01
serial: 00:0c:6e:99:5f:d2
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.1.108 latency=32 link=yes multicast=yes port=twisted pair speed=100MB/s
resources: iomemory:dc000000-dc001fff irq:17
*-network UNCLAIMED
description: Ethernet controller
product: 88w8335 [Libertas] 802.11b/g Wireless
vendor: Marvell Technology Group Ltd.
physical id: 1
bus info: pci@02:00.0
version: 03
width: 32 bits
clock: 66MHz
capabilities: cap_list
configuration: latency=0
resources: iomemory:24000000-2400ffff iomemory:24010000-2401ffff irq:16

Download this package, extract and install it

Bla@Bla-Bla:~$ wget [http://blakecmartin.googlepages.com/...nternet.tar.gz](http://blakecmartin.googlepages.com/...nternet.tar.gz)

--21:20:50-- [http://blakecmartin.googlepages.com/...nternet.tar.gz](http://blakecmartin.googlepages.com/...nternet.tar.gz)
=> `bcm43xx-0.3.2-internet.tar.gz'
Resolving blakecmartin.googlepages.com... 72.14.203.118
Connecting to blakecmartin.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19,375 (19K) [application/octet-stream]

100%[=======================>] 19,375 --.--K/s

21:20:51 (131.90 KB/s) - `bcm43xx-0.3.2-internet.tar.gz' saved [19375/19375]


Bla@Bla-Bla:~$ tar xvf bcm43xx-*.tar.gz
bcm43xx-0.3.2-internet/
bcm43xx-0.3.2-internet/LICENSE
bcm43xx-0.3.2-internet/installer.py
bcm43xx-0.3.2-internet/S05firmware-init-script
bcm43xx-0.3.2-internet/wcm.sh
bcm43xx-0.3.2-internet/bcm43xx.sh
bcm43xx-0.3.2-internet/bcm43xx-ndiswrapper.sh
bcm43xx-0.3.2-internet/wicd-tray.desktop
bcm43xx-0.3.2-internet/stats-logger
bcm43xx-0.3.2-internet/LICENSE-BROADCOM
bcm43xx-0.3.2-internet/READMEs/
bcm43xx-0.3.2-internet/READMEs/README-wcm-wicd
bcm43xx-0.3.2-internet/READMEs/README-installer
bcm43xx-0.3.2-internet/READMEs/README-wcm-wifi-radar
bcm43xx-0.3.2-internet/READMEs/GPLv2
bcm43xx-0.3.2-internet/READMEs/README-bcm43xx-ndiswrapper
bcm43xx-0.3.2-internet/READMEs/README-bcm43xx
bcm43xx-0.3.2-internet/READMEs/CHANGELOG
bcm43xx-0.3.2-internet/README

Bla@Bla-Bla:~$ cd bcm43xx-*

Bla@Bla-Bla:~/bcm43xx-0.3.2-internet$ ./installer.py

./wcm.sh wifi-radar
gksudo './bcm43xx-ndiswrapper.sh'

Bla@Bla-Bla:~/bcm43xx-0.3.2-internet$


cd ~
wget [http://blakecmartin.googlepages.com/...nternet.tar.gz](http://blakecmartin.googlepages.com/...nternet.tar.gz)
wget [http://blakecmartin.googlepages.com/...offline.tar.gz](http://blakecmartin.googlepages.com/...offline.tar.gz)
tar xvf bcm43xx-*.tar.gz
cd bcm43xx-*
./installer.py


See if your wireless card is now listed in the system/administration/network Devices-Network Tools in the Device pulldown menu and go configure your wep password and network id



!!! TADA !!!

---

