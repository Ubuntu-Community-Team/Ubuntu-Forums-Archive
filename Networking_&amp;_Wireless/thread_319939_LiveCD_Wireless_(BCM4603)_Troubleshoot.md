---
title: "LiveCD Wireless (BCM4603) Troubleshoot"
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by maclenin on 2006-12-16
I am a Linux maiden and soon-to-be mono-boot Edgy Eft user. However, before I take the plunge (and wipe clean all remnants of the windows world from my laptop) I'd like to jump-start my wireless card (Dell Truemobile 1350 / Broadcom 4306 on a Dell Inspiron 600m) within the LiveCD environment. 

Givens:

A. I am running Edgy Eft in a LiveCD environment on a Dell Inspiron 600m.

B. The output generated using: 

```
sudo lshw -C network
```

reads as follows:

*-network:1 DISABLED
description: Wireless interface
product: BCM4306 802.11 b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 3
bus info: pci@02:03.0
logical name: eth1
version: 03
serial: 00:0b:7d:1c:3f:c5
width: 32 bits
clock: 33 MHZ
capabilities: bus_master ethernet physical wireless
configuration: broadcast=yes driver=bcm43xx driverversion=2.6.17-10-generic
link=no multicast=yes wireless IEEE 802.11 b/g
resources: iomemory:faffc000-faffdff irq: 5

C. I have read through a handful of posts, with particular reference to: [http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm43xx](http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm43xx).

D. I have no connection to the internet (within Edgy Eft), which I think implies no access to repositories.

E. I have located what I believe to be the relevant wireless driver (bcmwl5.sys) in /windows/sytem32/drivers.

F. I have downloaded the latest firmware extraction tool (bcm43xx-fwcutter-006.tar.bz2 from [http://developer.berlios.de/project/showfiles.php?group_id=4547](http://developer.berlios.de/project/showfiles.php?group_id=4547)) into a windows parition (via Windows XP).

G. I have made a directory called /c using:

```
sudo mkdir /c
```

H. I have mounted my windows partition (/dev/hda2) to /c using:

```
sudo mount /dev/hda2 /c -t ntfs
```

I. I can "see" both the wireless driver ("driver") and extraction tool ("tool") in the windows partition, via Linux, using:

```
sudo ls /c/windows/the/respective/locations/of/each/file
```

Assumptions:

J. I need to copy my driver from the windows partition to a "Linux" partiton (i.e. to /home/drivers or some such) in order for the tool to be able to extract the firmware from the driver.

K. I need to copy/move the tool from the windows partition to a "Linux" partition (i.e. to /opt/utilities or some such) in order to unpack it and install it and use it to extract firmware from the driver.

L. Once the tool has been copied/moved I can unpack it using:

```
tar jxfv bcm43xx-fwcutter-006.tar.bz2
```

M. Once the firmware has been extracted from the driver, I should be able to use my wireless card after I've made certain it's enabled (and properly configured) via the Networking tool.

Questions:

N. How (via the terminal) and into which directory should I copy my driver in prep. for firmware extraction?

O. How and into which directory should I copy/move the tool?

P. Does the unpacking command...

```
tar jxfv bcm43xx-fwcutter-006.tar.bz2
```

...unpack the tool (or any packed file) into a specific directory (i.e. into the directory in which the packed file is currently located)? Or can I designate a destination/path?

Q. How do I "install" the tool? Using aptitude? Using apt-get? (Do I need an internet connection for aptitude or apt-get?) Just install? Do I install it into the same directory into which I have copied it from the windows partition?

R. With more specific reference to unpacking into a certain directory, might the command:

```
tar jxfv bcm43xx-fwcutter-006.tar.bz2 -C /opt/utilities
```

be in the proper format, assuming /opt/utilities is where the packed file resides? Does it matter where the packed file resides? With reference to: [http://ubuntuforums.org/showthread.php?t=314082&highlight=.tar.bz2](http://ubuntuforums.org/showthread.php?t=314082&highlight=.tar.bz2) it doesn't seem to matter.

S. Do I need to be in the directory within which the tool or driver reside in order to unpack or install or cut the firmware? That is...

```
cd /opt/utilities
```

...in order to unpack or install the tool or...

```
cd /home/drivers
```

...in order to cut the firmware from the driver?

T. Should I blacklist the other "bcm43xx" driver before "installing" the "new" one?

U. What is the terminal syntax for extracting the firmware from my driver?

V. Is there anything I am leaving out?

There's a lot of stuff here. I appreciate whatever guidance anyone might be able to pass along.

For slightly evolved thinking on this topic, see: [http://ubuntuforums.org/showthread.php?t=322652](http://ubuntuforums.org/showthread.php?t=322652)

---

### Post by maclenin on 2007-01-15
This is where I ended up...

[http://ubuntuforums.org/showthread.php?t=332253](http://ubuntuforums.org/showthread.php?t=332253)

...and am currently in wireless connectivity trouble-shoot mode:

[http://ubuntuforums.org/showthread.php?t=331997](http://ubuntuforums.org/showthread.php?t=331997)

I chose bcm43xx because it seemed cleaner than ndiswrapper - but am not opposed to wrapping (or another solution) should all else fail....

---

### Post by maclenin on 2007-01-17
The [latest]("http://ubuntuforums.org/showthread.php?p=2027150#post2027150")....

---

### Post by maclenin on 2007-01-31
The [**latest**]("http://ubuntuforums.org/showthread.php?t=340689")....

---

