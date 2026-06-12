---
title: "USB HDD not working"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by klein de usa on 2009-05-22
hi
i have a usb to ide adapter that use to work, i know the adapter still works because i can connect it to a cd or dvd drive and mount it and read it, it seems to only be hdd's that are affected? why? is there a solution? my computer is sata not ide so all my data on ide at this point i can't get to. any ideas?

---

### Post by superprash2003 on 2009-05-23
in your terminal type** sudo fdisk -l** and post output

---

### Post by klein de usa on 2009-05-23
hi 
i ran some commands here is the out put it gave me,

sudo fdisk -l
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b8df1cc


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+  83  Linux
/dev/sda2            3825        7648    30716280   83  Linux
/dev/sda3            7649       11472    30716280   83  Linux
/dev/sda4           11473       30515   152962897+   5  Extended
/dev/sda5           11473       11727     2048256   82  Linux swap / Solaris
/dev/sda6           11728       30515   150914578+  83  Linux



lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


dmesg | tail
[   89.924945] usb-storage: waiting for device to settle before scanning
[   94.924346] usb-storage: device scan complete
[  100.536050] usb 5-2: USB disconnect, address 3
[  100.536518] scsi 3:0:0:0: Device offlined - not ready after error recovery
[  112.796293] ppdev0: registered pardevice
[  112.844224] ppdev0: unregistered pardevice
[  113.948948] ppdev0: registered pardevice
[  113.996290] ppdev0: unregistered pardevice
[  114.025582] ppdev0: registered pardevice
[  114.072032] ppdev0: unregistered pardevice

---

### Post by NHArticleTen on 2009-05-23
HDD transplants into external position via USB...

most common problem is that a change in jumper position is required at the HDD...

let us know...

---

### Post by klein de usa on 2009-05-23
ok 

i have done some research, i have three of these one works good the other two are the same chip, and are hit or miss when it comes to different hdd's 

the one listed below works: 
Bus 005 Device 003: ID 04cf:8818 Myson Century, Inc. USB2.0 to ATAPI Bridge Controller


this one is hit or miss:
Bus 005 Device 004: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter


Myson Century i find is hard to get to read but it will work you might have to move it from one usb slot to another and cycle the power and it takes it a while to come up.


Genesys Logic some hdd's it will read and no matter what you do some it wont. from putting the id in google i found that, this chip id has had problems from the start and still isn't worked out.   


i'd like to buy a back up usb to ide adapter how would one find one that just works?

---

