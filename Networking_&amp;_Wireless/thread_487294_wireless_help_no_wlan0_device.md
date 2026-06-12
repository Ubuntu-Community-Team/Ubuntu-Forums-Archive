---
title: "wireless help: no wlan0 device?"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by TXBDan on 2007-06-28
Hey all,

I'm working w/ a Linksys WMP11v4 here. i installed the lates ndiswrapper and the windows drivers.

'ndiswrapper -l' looks good. driver and device present

modprobe -l |grep wrapper looks good:

/lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko

My /etc/network/interface shows:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dcp

auto eth1
iface eth1 inet dhcp

auto eth2 
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



However if i do a ifconfig, or iwconfig, or iwlist, etc, no wlan0 shows up...?

any ideas?

Thanks

---

### Post by kevdog on 2007-06-28
Can you post the output of 

lshw -C network

That would help me a lot.  Im trusting you that the things you told me about things "looking good" are true!

---

### Post by TXBDan on 2007-06-29
haha im reading the forums on my laptop... this is a lot to type by hand..

here it goes

*-network
description: ethernet interface
product: nvidia corporation
physical id: 4
bus info: pci@00:04.0
logical name :eth0
version: al
serial: 00:0e:a6:e1:5e:78
width: 32bits
clock: 66mhz
capabilites: bus_master caplist ethernet physical
configuration: broadcast=yes driver-forcedeth driverversion=0.59 latency=0 maxlatency=20 mingnt=1 multicast=yes
resources: iomemory:e3000000-e3000fff ioport:e000-e007 irq:16

*-network UNCLAIMED
description: ethernet controller
product: wmp11v4 802.11b PCI card
vendor: linksys, ldfkjd
physical id: 9
bus info: pc@01:09.0
version: 00
width: 32bits
clock: 33mhz
capabilites: bus_master cap_list
configuration: latency=32 maxlatency+32 mingnt=32
resources: iomemory:e2000000-e20007ff irq:10


Thanks a lot in advance for any help!

---

### Post by TXBDan on 2007-06-29
more info:

ndiswrapper -v:
utils version: 1.7
driver version: 1.38

ndiswrapper -l:
installed ndis drivers:
lsipnds driver present, hardware present

---

### Post by TXBDan on 2007-06-29
just d/led the lates greatest source and am running that now.

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586 



still no wlan0, etc

modprobe -l | grep wrapper shows the module is loaded..

---

### Post by TXBDan on 2007-06-29
woohoooooo

i rebooted and i'm in business. 

woot woot

:D

---

