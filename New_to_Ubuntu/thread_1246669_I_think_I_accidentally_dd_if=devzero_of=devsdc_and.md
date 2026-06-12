---
title: "I think I accidentally dd if=/dev/zero of=/dev/sdc and now my usb drive fails."
date: 2009-08-22
forum: New to Ubuntu
---

### Post by disappearedng on 2009-08-22
Hey everyone
Recently I had to reformat my ipod, so I decided to use dd if=/dev/zero of=/dev/sdc to empty my ipod. 

now when I plug in my usb thumb drive, nothing shows up.

```

[682576.071275] sr 30:0:0:1: Attached scsi generic sg4 type 5
[682597.451462] VFS: Can't find ext4 filesystem on dev sdc.
[682618.185074] FAT: bogus number of reserved sectors
[682618.185078] VFS: Can't find a valid FAT filesystem on dev sdc.
[682759.173168] usb 2-3: USB disconnect, address 30
[682774.784520] usb 2-3: new high speed USB device using ehci_hcd and address 31
[682774.917039] usb 2-3: configuration #1 chosen from 1 choice
[682774.917238] scsi31 : SCSI emulation for USB Mass Storage devices
[682774.917693] usb-storage: device found at 31
[682774.917696] usb-storage: waiting for device to settle before scanning


[disappearedng@disappearedng-desktop:~]$ sudo fdisk  -lu
[sudo] password for disappearedng: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    90188909    45094423+   5  Extended
/dev/sda2        90188910   909391454   409601272+  83  Linux
/dev/sda5             126    86397569    43198722   83  Linux
/dev/sda6        86397633    90188909     1895638+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e26b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   110318354    55159146   83  Linux
/dev/sdb2       110318355  1953520064   921600855   83  Linux

Disk /dev/sdc: 4026 MB, 4026531328 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7864319 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              38     7839719     3919841    b  W95 FAT32


[disappearedng@disappearedng-desktop:~]$ ls /dev/sdc*
/dev/sdc


[disappearedng@disappearedng-desktop:~]$ sudo mount -t vfat /dev/sdc /home/disappearedng/Desktop/
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

What should I do? I notice that the disk identifier for /dev/sdc is Disk identifier: 0x00000000

---

### Post by Whiffle on 2009-08-22
So if I'm reading this right, your ipod is fine, but now your flash drive doesn't work?  Was it plugged in when you were cleaning off the ipod?

---

### Post by kerry_s on 2009-08-22
the command zeros out the drive, use gparted to format it.

---

### Post by disappearedng on 2009-08-23
Ok now my dilemma is that when I plug in my usb key, which normally turns on the light inside the usb drive automatically, the light no longer turns on. (which is kind of weird). My ipod, doesn't work, my usb key doesn't work, but my wireless mouse works. (which is plugged through the usb key). 

Do you mean using gparted to format my usb key drive? Cause the issue is, when I plug in my usbkey drive to my laptop, everything works perfectly. This appears that my usb drive in my computer has stopped working after that command. (Note that when I plug in my ipod it still shows "Connected" )

---

