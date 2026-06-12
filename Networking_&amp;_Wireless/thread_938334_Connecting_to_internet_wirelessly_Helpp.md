---
title: "Connecting to internet wirelessly? Helpp"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by Hornzog on 2008-10-04
Ok so before my computer completely died i had wireless internet set up perfectly using a "Wireless-N PCI adaptder, Model no. WMP300n" But after not getting windows to work again and deciding to try Ubuntu i cannot get connected to the internet at all. 
When i insert the CD to install the adapter onto the computer the window comes up showing the contents of the CD, however nothing i do can get the CD to install, clicking on the setup.exe literally does nothing, and the autorun.inf comes up with an option to run, cancel or run in terminal, in which clicking on does absoloutely nothing either.
Is there anyway to install this onto my computer and subsequently get conected to the internet, ive only had ubuntu on the computer for a few days so am completely clueless, a walkthrough guide would be helpfull :D
Thanks in advance.

---

### Post by Crafty Kisses on 2008-10-04
What are the results of this command?
```
lshw -C network
```

---

### Post by Hornzog on 2008-10-04
something like..

Warning: you shold run this program as super user.
network :B unclaimed
description: network controller
product: AR5416 802. 11abgn wireless PCI adapter
vendor: Atheros communications inc.
physical id: 0
bus info: pci@0000:04:00.0
version: 01
width: 32 bits
clock 66Mhz
capabilities: bus_master cap_list
configuration: latency=64

*network:1
description: Ethernet interface
prioduct: BCM4401 100Base-T
Vendor: Broadcom Corporation
physical id: 3
bus info: pci@000:04:03.0
logical name: eth0
version:01
serial: 00:11:43:24:c8:d7
width: 32 bits
clock 33Mhz
Capabilities: bus_master cap_list ethernet
configuration: broadcast=yes driver=44
==ssb multicast=yes

---

### Post by melojo on 2008-10-04
here is link
[http://ph.ubuntuforums.com/showthread.php?t=814187](http://ph.ubuntuforums.com/showthread.php?t=814187)

---

### Post by melojo on 2008-10-04
try this link
[http://ubuntuforums.org/showthread.php?t=668272](http://ubuntuforums.org/showthread.php?t=668272)

---

### Post by Hornzog on 2008-10-04
modprobe: invalid option -- 1
usage: modprobe [-v] [-v] [-c config-file] [-n][-i] [-Q] [-b] [-o <modname
>] [ --dump-modversions ] ,modname. [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]

---

### Post by melojo on 2008-10-04
> **Hornzog said:**
> modprobe: invalid option -- 1
usage: modprobe [-v] [-v] [-c config-file] [-n][-i] [-Q] [-b] [-o <modname
>] [ --dump-modversions ] ,modname. [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]

need to run modprobe as a super user
sudo modprobe -l

its a small L not a one

---

### Post by Hornzog on 2008-10-04
> **melojo said:**
> need to run modprobe as a super user
sudo modprobe -l

how do i do that?

---

### Post by melojo on 2008-10-04
> **Hornzog said:**
> how do i do that?

open a terminal and type this below

sudo modprobe -l
it seems that madwifi seems to work with this card 
follow the second link
[http://ubuntuforums.org/showthread.php?t=668272](http://ubuntuforums.org/showthread.php?t=668272)

---

### Post by Hornzog on 2008-10-04
> **melojo said:**
> open a terminal and type this below

sudo modprobe -l
it seems that madwifi seems to work with this card 
follow the second link
[http://ubuntuforums.org/showthread.php?t=668272](http://ubuntuforums.org/showthread.php?t=668272)

I will do tomorow, its late here. Thanks for your help.

---

