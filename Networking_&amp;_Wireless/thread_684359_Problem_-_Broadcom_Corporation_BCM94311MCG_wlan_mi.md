---
title: "Problem - Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by zirtik on 2008-02-01
Hi,

Before starting I have to say that I read almost everything related to my chipset and tried all the solutions but none worked for me. Finally I found the page on:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

and installed ndiswrapper but still my wireless card's light is red (not blue).
However, I didn't get any error messages at all and the installation seemed to be successful.

I am using an HP Pavillion dv2615nr and have the chipset:

Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02).

The weird thing is that when I type lshw -C network I get the following output:

```
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:16:d3:f2:78:16
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.64 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
```

I think my problem is with the last line because in my opinion the driver should be nidswrapper not b43-pci-bridge. If I'm right, how can I fix this?

Finally, here is the output for vim /etc/modules

```
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
sbp2
ndiswrapper
```

and I added the line

```
blacklist bcm43xx
```

to my  /etc/modprobe.d/blacklist file.

I am currently running Hardy and wireless is my only problem. Looking desperately for help,

Thank you for reading and thanks in advance for any solution ideas.

---

### Post by zirtik on 2008-02-02
Today I have tried to install ndiswrapper from source. I even tried latest stable release ofn diswrapper, namely version 1.51. Everything seems perfect but I still can't make it. Again, the 'weird' thing is that when I type

lshw -C network

I get

```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:16:d3:f2:78:16
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.64 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
```

Note that the last line still says that I,m currently using the b43-pci-bridge driver and I think it is not supposed to be used. How can I change it to ndiswrapper?

---

### Post by zirtik on 2008-02-02
Based on this post:

[http://ubuntuforums.org/showthread.php?p=4216379&highlight=driver%3Db43-pci-bridge#post4216379](http://ubuntuforums.org/showthread.php?p=4216379&highlight=driver%3Db43-pci-bridge#post4216379)

This was an issue related to Hardy and the new kernels. What I did was adding the following lines
to to my /etc/rc.local file.

```
rmmod ohci_hcd
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ohci_hcd
```

and adding ssb to the blacklist (/etc/modprobe.d/blacklist). 

Now everything is fine!

---

### Post by Tech Provider on 2008-04-25
1.Run in terminal for testing :

rmmod b43
rmmod b44
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe b44

2.If it works use a script to run the commands and install wifi-radar to detect wireless networks  !

---

