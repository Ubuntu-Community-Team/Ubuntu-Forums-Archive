---
title: "Non PnP USB device."
date: 2010-05-16
forum: New to Ubuntu
---

### Post by TerjeS on 2010-05-16
Hi, i got a Classpad 330, I can connect with USB but nothing happens when i do. There is some software bundled for winXP. It installs under WineHQ but it dosen't find the calculator.
The FA-CP1 program link, is basically a kinda old fashion Lap-link tool to copy data between PC and Classpad 

The thing is, is there a way of searching for this device with Ubuntu, to mount it as a Flash drive.   :confused:. Bee cool if it does. Cos i got Win7 64bit and the Software does not work

Thx
TerjeS

---

### Post by Ozymandias_117 on 2010-05-16
I'm not entirely sure how that device is designed to work, but, if you post the output of ```
sudo lsusb
``` and ```
sudo fdisk -l
``` I may be able to help you.

---

### Post by TerjeS on 2010-05-18
From sudo lsusb
> Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 07cf:6101 Casio Computer Co., Ltd 
Bus 005 Device 002: ID 172f:0500 Waltop International Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c504 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 059b:0370 Iomega Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubFrom fdisk -l

> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       60802   488282112    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         122      979933+  83  Linux
/dev/sdc2             123       23666   189117180   83  Linux
/dev/sdc3           23667       31390    62043030   82  Linux swap / Solaris
/dev/sdc4   *       31391       60801   236243857+   7  HPFS/NTFS



Think it is the Bus 005 Device 003: ID 07cf:6101 Casio Computer Co., Ltd.

---

### Post by Ozymandias_117 on 2010-05-18
Sorry, from what I see I don't know of any ways to mount it as a flash drive.

---

### Post by slavik_malenkij on 2010-10-14
Sorry for necroposting.  I was googling for the device ID, and this post came up, so I registered just to post this, in case it's useful to original author or others.

TerjeS, 

07CF:6101 is a CASIO CESG502 device.  Seems like this is a generic USB ID that Casio uses for its line of portable electronic dictionaries, PDAs and calculators.  

You won't be able to mount this device in a mass storage mode, since  Casio devices with this USB ID use OBEX over USB for communication.  

Brian Johnson maintains libexword project on github, which is a library and a command line utility to interact with these devices. (libexword because he has a Casio Ex-Word Japanese <-> English electronic dictionary, however it seems that other Casio devices that use OBEX might also work).  The emphasis so far is on Casio dictionaries, because this is what he has, but since Classpad has the same USB ID as the dictionaries, it's highly likely that it uses the same OBEX over USB communication protocol.

Just today Brian pushed in a major update, that actually supports interactive mode to communicate with the device, and there is a small header offset patch that needs to be pushed in (I found the bug in interaction with an ex-word dataplus 4 dictionary - dataplus 3 devices worked fine) to work with newer Casio devices.

At this point the library and utility are not hugely useful, since we are basically capturing USB traces from Casio Library and Casio TextLoader utilities, and attempting to recreate functionality.  Any  function requiring authentication (On electronic dictionaries, uploaded dictionaries are encrypted) won't work (so you can't copy content from the device).  But you should be able to query version of the device, upload text files onto it, and delete files on the device (careful with the last one).  Those might work with your ClassPad.   

It's possible that formatting of the SD card inserted into device will be the next feature that will be added for devices that support SD cards.   

But any way... if you want any chance for your calculator to work with Linux,  pull down [http://github.com/brijohn/libexword.git](http://github.com/brijohn/libexword.git) from github, compile, give it a go against your Classpad.  It just might work.  And if it doesn't, maybe you'll be able to get some USB captures, and get it to work. 

In any event, once you tried libexword, send Brian an email with yay or nay - it would be useful.

---

