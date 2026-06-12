---
title: "Memory card reader not recognised"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by andycowie on 2010-01-10
I've just upgraded to ultimate edition 9.10 but now when I plug in my usb card reader its not seen by the system. Any ideas? Thanks a lot, Andy

---

### Post by Excedio on 2010-01-10
Please plug the card reader in and post the output of
```
lsusb
```
 
If you're not sure how to do that: Applications > Accessories > Terminal

---

### Post by andycowie on 2010-01-10
Hi, here it is. Thanks for helping.
Bus 001 Device 008: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 03f0:3c02 Hewlett-Packard PhotoSmart 7350
Bus 003 Device 002: ID 045e:009d Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by sgosnell on 2010-01-10
The card reader is working, but the card is probably not being mounted automatically.  You can open Nautilus, click on the card icon, and it will mount it for you.

---

### Post by andycowie on 2010-01-11
Thanks very much, I'll give this a go.

---

### Post by xieu90 on 2010-01-20
hi
I have 1 computer and 1 laptop
the laptop has its own card reader (this one work, so this card reader and card are ok)
but my computer doesnt have its own card reader, so I use an extern all in one cardreader. (this one worked under window)
I tried that code above lsusb
and got this one 

Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)

in nautilus I can see around 4 or 5 icon(for sd, ms,usb cf, sm ...)
they are somehow like dvd read icon, I dont see mount/unmount option there, only open,open with, safely remove driver ...

what should I do now to mount my card?

---

### Post by anaconda on 2010-01-20
type 
```
sudo fdisk -l
```
in termnal, and if your card is listed there you can mount it with eg:
```
sudo mount /dev/xxxx /mnt
```
where the xxxx is your card.. to find out what xxxx is in your case read the output of fdisk -l carefully, or post it here...

After that your card should be mounted to /mnt
but it wont appear on your desktop, so you will have to navigate to /mnt with file-browser (nautilus)

---

### Post by josvanr on 2010-01-20
i've been having the same trouble since the last update
(yesterday?)

fdisk -l:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a0cd351

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29275   235151406   83  Linux
/dev/sda2           29276       30401     9044595    5  Extended
/dev/sda5           29276       30401     9044563+  82  Linux swap / Solaris

Disk /dev/sdd: 4059 MB, 4059611136 bytes
128 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         983     3963424+   b  W95 FAT32



but: 

fdisk -l:

root@stumpernicus:/# mount /dev/sdd1 /flash
mount: special device /dev/sdd1 does not exist

---

### Post by josvanr on 2010-01-20
sdd does seem to exist 

root@stumpernicus:/# mount -t vfat /dev/sdd /flash
mount: wrong fs type, bad option, bad superblock on /dev/sdd,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

but what is it?

---

### Post by josvanr on 2010-01-20
another remark:

root@stumpernicus:/# dmesg|tail
[ 1954.023957]    : Add. Sense: No additional sense information
[ 1954.056804] sd 10:0:0:1: ioctl_internal_command return code = 8070000
[ 1954.056809]    : Sense Key : Hardware Error [current] 
[ 1954.056814]    : Add. Sense: No additional sense information
[ 1954.104674] sd 10:0:0:1: ioctl_internal_command return code = 8070000
[ 1954.104679]    : Sense Key : Hardware Error [current] 
[ 1954.104686]    : Add. Sense: No additional sense information
[ 1954.118053] sd 10:0:0:1: ioctl_internal_command return code = 8070000
[ 1954.118059]    : Sense Key : Hardware Error [current] 
[ 1954.118067]    : Add. Sense: No additional sense information

hardware error? The camera doesn't seem to have any trouble with 
reading/writing of the card..


when I start nautilus, the name of the usb card keeps appearing and disappearing
in the 'places' list. When I manage to click it (as long as it is there)
I see a message box saying that the card does not exist (something to that
extent anyway)

---

### Post by xieu90 on 2010-01-20
I used fdisk -l
but my card wasnt listed there
if I use my laptop's own card reader, then it is there.(also auto mounted)

---

### Post by josvanr on 2010-01-22
hello all, the problem turned out to be the card reader 
hardware. Bought a new one, now it works again....

jos

---

