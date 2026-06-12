---
title: "Unable to access USB Flash Drive"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by hnarwan on 2009-08-30
Hi All,

I'm on Ubuntu 9.04, just recently installed.

When i plug my 64GB Corsair USB Flash drive it shows up but when i double click it to get at the files inside i see the following error:
[SIZE="4"][B]
Unable to mount location[/B][/SIZE]

Can't mount file

I'm completely clueless as to how i'm supposed to mount this drive. 

I have created a folder under /media called disk and tried to issue the following command but i dont know what the error means or whether the /dev/sdb bit is even right.

root@hardeep-laptop:/home/hardeep# sudo mount /dev/sdb /media/disk
mount: you must specify the filesystem type

Please help, i'm starting from scratch here, all i've figured out so far is to use this flash drive i need to mount it to a mount point but i dont know how to go about doing that.

thanks for the help.

---

### Post by DFlame on 2009-08-30
Lets take a look. Plug in the flash drive and open a Terminal window (Applications, Accessories, Terminal). Enter this code and type your password when prompted:

```
sudo fdisk -l
```

Please post the output and we can take a closer look :)

---

### Post by HereInOz on 2009-08-30
If this is a NTFS formatted USB drive, and the last time it was used it was removed from a Windows machine without going through the proper disconnection, it will not mount in Ubuntu.

If this is the case, plug it back into a Windows machine, let Windows find it, then properly disconnect the drive, unplug it, and plug it into the Ubuntu machine.  

All things being equal (they rarely are), it should then mount successfully.

Good luck.

---

### Post by hnarwan on 2009-08-30
Thanks guys, output is below, i'll do a clean disconnect from my windows machine and report back to confirm if that helps me:

root@hardeep-laptop:/home/hardeep# sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000dc16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29321   235520901   83  Linux
/dev/sda2           29322       30401     8675100    5  Extended
/dev/sda5           29322       30401     8675068+  82  Linux swap / Solaris

Disk /dev/sdb: 64.6 GB, 64692944896 bytes
64 heads, 32 sectors/track, 61696 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x2c6b7369

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      945327     1849555   925929529+  68  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      649505      912677   269488144   79  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      263179      945973   699181456   53  OnTrack DM6 Aux3
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      680971      680981       10668+  49  Unknown
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by hnarwan on 2009-08-30
Guys i've tried another usb (much smaller at 2.1 GB) which works great.

Not sure what the problem is with the 64GB usb drive?

---

### Post by LewRockwell on 2009-08-30
> **hnarwan said:**
> Guys i've tried another usb (much smaller at 2.1 GB) which works great.

Not sure what the problem is with the 64GB usb drive?

so the reconnect and then performing a clean disconnect(safely remove) didn't work?

it should be noted that some windoze machines are more difficult than others to cleanly dismount

.

---

