---
title: "Western Digital My Passport doesn't work"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by sudip@houston on 2010-03-08
I recently changed my OS from Windows to Ubuntu 9.10. I used to backup all my files in the WD USB HDD. When I now connect the USB HDD ubuntu cannot mount it and gives an error. I have two questions:
1. What is the correct way to mount it. I searched the web and figured that there are some issues with WD support for Ubuntu

2. If the issue still persists which is the USB external portable HDD drive works flawlessly with ubuntu.

Thanks in advance
Sudip

---

### Post by halitech on 2010-03-08
what is the error you get when it fails to mount?

what is the output of
```
lsusb
```and
```
sudo fdisk -l
```

---

### Post by sudip@houston on 2010-03-09
I search high and low in this forum as well as in the google to get an answer. In one of the post (don't have the link) it said that I should format the WD passport USB HDD in windows and then bring it over to ubuntu. So I formatted the HDD in NTFS and when I plugged nothing happened absolutely Nada. I tried FAT32 formatting again nothing. I looked up in the disk utility and figured out that it is showing my WD as unmounted device. However nothing absolutely nothing could be done to mount it. Please help.

---

### Post by zeroseven0183 on 2010-03-09
I also have WD My Passport 320GB (External HDD) but had no problems mounting it. I didn't reformat it to FAT32 or EXT3/4. I just left it as NTFS and it works fine on Ubuntu and on Windows machine.

So like the question before, what was the error message?

---

### Post by halitech on 2010-03-09
> **sudip@houston said:**
> I search high and low in this forum as well as in the google to get an answer. In one of the post (don't have the link) it said that I should format the WD passport USB HDD in windows and then bring it over to ubuntu. So I formatted the HDD in NTFS and when I plugged nothing happened absolutely Nada. I tried FAT32 formatting again nothing. I looked up in the disk utility and figured out that it is showing my WD as unmounted device. However nothing absolutely nothing could be done to mount it. Please help.

if you could run the commands I posted and give us the results we can try to help you out.

---

### Post by sudip@houston on 2010-03-09
Finally I could get something out. Out of the box Ubuntu does support WD My Passport. I installed ubuntu in my other laptop and when I plug in It Works.. BUT I need internet tethering ( I just love it!!) so I installed this [http://www.ubuntugeek.com/iphone-tethering-on-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/iphone-tethering-on-ubuntu-9-10-karmic.html) and all hell broke loose again.   Seems this update is incompatible with my USB external HDD. Question is how do I make it work if not How do I get rid of iphone tethering?    ERROR MESSAGE DBus error org.freedesktop.DBus.Error.NoReply:Message did not receive a reply (timeout by message bus)  Now the Outputs  lsusb

 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module] Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 002 Device 005: ID 1058:0705 Western Digital Technologies, Inc.  Bus 002 Device 002: ID 04f2:b015 Chicony Electronics Co., Ltd VGA 24fps UVC Webcam Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 

 sudo fdisk -l  

Disk /dev/sda: 160.0 GB, 160041885696 bytes 255 heads, 63 sectors/track, 19457 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x403ec116     Device Boot      Start         End      Blocks   Id  System /dev/sda1   *           1       18706   150255913+  83  Linux /dev/sda2           18707       19457     6032407+   5  Extended /dev/sda5           18707       19457     6032376   82  Linux swap / Solaris  Disk /dev/sdb: 320.1 GB, 320072933376 bytes 255 heads, 63 sectors/track, 38913 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x5c74ae42     Device Boot      Start         End      Blocks   Id  System /dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

---

### Post by sudip@houston on 2010-03-10
bump .. please help!!

---

### Post by sudip@houston on 2010-03-10
Can any one please help me. I'm stuck. If not please tell how to uninstall the ppa for iphone tethering

---

### Post by halitech on 2010-03-10
I can't understand anything you posted for the outputs due to everything running together

far as removing the PPA, open Synaptic and go to Settings - Repositories and remove the one you added.

---

### Post by jurakhon on 2010-05-14
I am having exact same issue. I have WD My Passport 500GB. It doesn't work with Ubuntu 9.10. I did install all mount related things from Ubuntu Software Center and still not working. anyone plz help.

---

### Post by formaldehyde_spoon on 2010-05-14
If I had a disk like that the first thing I would do would be:

  - install gparted: sudo apt-get install gparted  
- then use gparted to delete the partitions and repartition the disk.  
- finally, if it still won't mount, force mount it: sudo mount /dev/sd?? /media/?someDir? -o force

---

