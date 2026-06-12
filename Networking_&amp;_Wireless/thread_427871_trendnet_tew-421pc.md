---
title: "trendnet tew-421pc"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by mrstamil on 2007-04-29
No matter what I try I cannot get my trendnet tew-421 wireless card working.  The drivers are installed, the card is recognized, the act button is lighting.... the link button is NOT lit up.  I find no connection.  I have a Panasonic cf-71, 300mhz.  I'm running ubuntu dapper.  I am new to Linux and trying SO HARD not to go back to windows!  Does anyone have any suggestions that aren't already mentioned?

---

### Post by atlfalcons866 on 2007-04-30
hi welcome to ubuntu. Try this page
[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by Count Doofus on 2007-10-25
It ain't pretty by any means but it got me there. I got my trendnet 421pc card running using a broadcom 43xx python script. Here's is what i did to get it going on my machine.

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

