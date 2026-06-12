---
title: "Did I lose my wireless controller"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by oldcity on 2006-08-11
Using a Dell Inspiron B130 laptop
60 gb HD,512 MB RAM,Celeron M 1.40 GHz
Dell 1370 minipci wireless, Broadcom NIC

After downloading the updates I lost my wireless connection.
(Timed out after about 1 hour).
Get this error upon doing:

sudo modprobe ndiswrapper
*
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-686/kernal/drivers/
net/ndiswrapper/ndiswrapper.ko): Invalid argument
*

sudo lshw -businfo

Bus info     Device  Class    Description   
pci@02:03.0          network  BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller

sudo iwconfig

lo     no wireless extensions.
eth0   no wireless extensions.
sit0   no wireless extensions.

sudo ifconfig
Password:

eth0 Link encap:Ethernet HWaddr 00:14:22:8E:AC:C9
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:217

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:42955 errors:0 dropped:0 overruns:0 frame:0
TX packets:42955 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:3486433 (3.3 MiB) TX bytes:3486433 (3.33.3 MiB)

lspci -n

0000:02:03.0 0280 14e4:4318 (rev 02)

sudo lshw

*-network:0
description: Ethernet interface
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id:0
bus info: pci@02:00.0
logical name: eth0
version: 02
serial 00:14:22:8e:ac::c9
width: 32bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration broadcast=yes driver=b44 multicase=yes
resources: iomemory:dfbfc000-dfbfdfff irq:217

*network:1
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 3
bus info: pci@02:03.0
version:02
width: 32bits
clock: 33MHz
capabilities: bus_master
resources: iomemory:dfbfe000-dfbfffff irq:10

sudo lsmod

Unable to identify in output the  BCM4318 controller to
determine if the controller is loaded and running.

 My question is:
How do I get the Wireless connection with wlan0 back?

Or 

Is it possible the network controller has failed?
If so how to tell?
Kubuntu occupies the entire hard drive (no XP)

Thanks in advance.
oldcity

---

### Post by Ptero-4 on 2006-08-11
Did you update from breezy to dapper? I ask b/c it seems that dapper somehow manages to delete several .ko and .o files during an install/upgrade/dist-update (It deleted to ppp.o and hwclock.ko files on my eMac the first time I installed it and also it did the same when I dist-updated from breezy).

---

### Post by oldcity on 2006-08-11
I don't remember exactly. I have a 5.4 cd and it was the 6.06
version I was upgrading. I have Ndiswrapper, Wifi-radar and
Madwifi that worked great before the update.
oldcity

---

