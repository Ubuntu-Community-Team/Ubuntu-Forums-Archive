---
title: "WD 120GB USB external disk - not recognized"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by pekboy on 2010-03-10
Hi
It's not the first time i look for this but it stills not working for me..

I've a 120GB external disk drive and is not recognized by ubuntu
It is formated as NTFS disk
Never had problems on Windows (98/XP/Vista


some codes that I already saw at some posts:


jon@jon-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

jon@jon-laptop:~$ sudo fdisk -l
[sudo] password for jon:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2530252f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        4864    18587205    f  W95 Ext'd (LBA)
/dev/sda5            2551        4080    12289693+   7  HPFS/NTFS
/dev/sda6            4081        4154      594373+  82  Linux swap / Solaris
/dev/sda7            4155        4864     5703043+  83  Linux


These NTFS system drives appeared are just other partitions that I use to have XP installed on.


Tried looking on "dmesg" and something appeared when plugged the usb external disk:

[ 9396.616060] usb 1-1: new high speed USB device using ehci_hcd and address 25       
[ 9412.188050] usb 1-1: device not accepting address 25, error -110
[ 9412.300036] usb 1-1: new high speed USB device using ehci_hcd and address 26
[ 9427.856042] usb 1-1: device not accepting address 26, error -110
[ 9427.968034] usb 1-1: new high speed USB device using ehci_hcd and address 27
[ 9438.404041] usb 1-1: device not accepting address 27, error -110
[ 9438.460206] hub 1-0:1.0: unable to enumerate USB device on port 1
[ 9458.368047] usb 1-1: new high speed USB device using ehci_hcd and address 29
[ 9473.924048] usb 1-1: device not accepting address 29, error -110
[ 9474.036038] usb 1-1: new high speed USB device using ehci_hcd and address 30
[ 9489.592023] usb 1-1: device not accepting address 30, error -110
[ 9489.704047] usb 1-1: new high speed USB device using ehci_hcd and address 31
[ 9500.136049] usb 1-1: device not accepting address 31, error -110
[ 9500.248036] usb 1-1: new high speed USB device using ehci_hcd and address 32
[ 9510.680051] usb 1-1: device not accepting address 32, error -110
[ 9510.680087] hub 1-0:1.0: unable to enumerate USB device on port 1




Already tried different USB ports as well..

_________-
 
I saw this old-post on this forum : [http://ubuntuforums.org/showthread.php?t=271600](http://ubuntuforums.org/showthread.php?t=271600)   that I thought it was the same problem, solved using a usb hub! Well, i don't have usb hub here.. is there any other solution that can help without saying to use Windows ?!

Thz for the support ;) 

Using Ubuntu 9.10 - the Karmic Koala

---

### Post by pekboy on 2010-03-13
any1 have ideas :S ?

---

### Post by Daveth on 2010-03-13
and other usb devices mount ok when you plug them in? Or, in other words, it is only this drive that misbehaves and is not a systemic usb failure....

---

### Post by pekboy on 2010-03-14
already tried other usb disks and had same problems.. same with a 512MB flash disk :S

---

