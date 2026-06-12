---
title: "second harddrive"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by Madagaine on 2009-09-06
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14030   112695943+  83  Linux
/dev/sda2           14031       14593     4522297+   5  Extended
/dev/sda5           14031       14593     4522266   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05f49d64

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4be82cf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS
Hello...I have a new install of ubuntu 9.04 and only ubuntu...'no windows'...and I can't find my second hardrive...I know, I'm new and don't know much about this. I've installed GParted and it shows up there and when I run the terminal it shows up there as well...
But it does not show up in places...Can anyone tell me what to do?

---

### Post by Bodsda on 2009-09-06
> **Madagaine said:**
> Hello...I have a new install of ubuntu 9.04 and only ubuntu...'no windows'...and I can't find my second hardrive...I know, I'm new and don't know much about this. I've installed GParted and it shows up there and when I run the terminal it shows up there as well...
But it does not show up in places...Can anyone tell me what to do?

Can you please post the contents of '/etc/fstab' and the ouput from the terminal command ```
sudo fdisk -l
```
This will help us build a picture of what your drives are named and how the system handles them.

Kind regards,
Bodsda

[I][B]fstab: fstab is a file that tells your system how and where to mount you partitions. This file decides whether or not a partition is automatically mounted

fdisk -l: This program, 'fdisk', is a terminal partition manipulator program. It can do basically what gparted can do. The -l option tells it to output a list of all partitions it knows about[/B][/I]

---

### Post by Madagaine on 2009-09-06
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14030   112695943+  83  Linux
/dev/sda2           14031       14593     4522297+   5  Extended
/dev/sda5           14031       14593     4522266   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05f49d64

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4be82cf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

---

### Post by Bodsda on 2009-09-06
> **Madagaine said:**
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14030   112695943+  83  Linux
/dev/sda2           14031       14593     4522297+   5  Extended
/dev/sda5           14031       14593     4522266   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05f49d64

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4be82cf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

Thanks, could you also provide the contents of the fstab file. To access it, run the following command
```

gedit /etc/fstab
```

Thanks,
Bodsda

---

### Post by Madagaine on 2009-09-06
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=5dbd2ae8-f70b-49bd-b801-2e91629f9f03 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e8963c74-09ad-41a9-be62-507f26afe24c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Bodsda on 2009-09-06
> **Madagaine said:**
> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=5dbd2ae8-f70b-49bd-b801-2e91629f9f03 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e8963c74-09ad-41a9-be62-507f26afe24c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Ok, so this tells us that your second hard drive is not being automatically mounted... So, I am assuming that it is your NTFS drive that you want, so trying running the following commands
```

sudo mkdir /media/win
sudo mount /dev/sdc1 /media/win

```
The first command creates a directory or folder which is needed for the mount point. The second command mounts /dev/sdc1 which, according to your fdisk -l, is your ntfs drive, at the mount point that the first command created.

Hope this helps,
Bodsda

---

### Post by Madagaine on 2009-09-06
Do I want an NTFS drive? Do I need an NTFS drive? I have only ubuntu installed...is it necessary to have an NTFS drive...?

---

### Post by NoaHall on 2009-09-06
No, not if you only have Linux. Use something like ext3 or ext4 instead.

---

### Post by Madagaine on 2009-09-06
thanks

---

### Post by Bodsda on 2009-09-06
> **Madagaine said:**
> Do I want an NTFS drive? Do I need an NTFS drive? I have only ubuntu installed...is it necessary to have an NTFS drive...?
Ok, I am a bit confused. I see more then one other partition so I don't kow which one you want. From what I can see, you have 2 120GB drives and one 500GB drive.

Which one do you require?

Kind regards,
Bodsda

---

### Post by Madagaine on 2009-09-06
Ok...I'm sorry, I wasn't clear...sda is my primary drive...sdb is my slave...the 500 is just storage
I'm trying to mount the sdb or slave and can't seem to get it visible

---

### Post by Madagaine on 2009-09-06
I'm sorry I wasn't more clear...sda is my primary and sdb is my slave...I'm trying to get sdb to show up...the 500 is just storage

---

### Post by Bodsda on 2009-09-06
> **Madagaine said:**
> Ok...I'm sorry, I wasn't clear...sda is my primary drive...sdb is my slave...the 500 is just storage
I'm trying to mount the sdb or slave and can't seem to get it visible

Ok, no worries, in that case lets run the following command to mount sdb1
```

sudo mkdir /media/slave
sudo mount /dev/sdb1 /media/slave

```

Then see if that shows up.

Kind regards,
Bodsda

---

### Post by Madagaine on 2009-09-06
I require sdb the second internal drive...the slave...sda is primary....the 500 is just storage...sorry I wasn't more clear

---

### Post by Bodsda on 2009-09-06
> **Madagaine said:**
> I require sdb the second internal drive...the slave...sda is primary....the 500 is just storage...sorry I wasn't more clear

No worries, just follow the instructions that I have posted just above. :)

---

### Post by Madagaine on 2009-09-06
Ok...Ok I think I understand now...
The sda, or primary is the filesystem drive...Right?
and the sdb or slave shows up as 120GB media...Right?

---

### Post by Bodsda on 2009-09-06
> **Madagaine said:**
> Ok...Ok I think I understand now...
The sda, or primary is the filesystem drive...Right?
and the sdb or slave shows up as 120GB media...Right?

Yes I would think so.
sda1 is already mounted, it is the one you have your system files and your home directory on. sdb1 is not used at all at the moment.

Hope this helps,
Bodsda

---

### Post by Madagaine on 2009-09-06
Thank you very much  Bodsda  Whoever you are...how do I mark this solved?

---

### Post by Bodsda on 2009-09-06
> **Madagaine said:**
> Thank you very much  Bodsda  Whoever you are...how do I mark this solved?

If your happy with the resolution then you can mark the thread by scrolling up, and at the top of the page, above the post on the right hand side there is a drop down list called 'thread tools'. One of the options in that list is mark thread as solved.

Thanks,
Have a nice day,
Bodsda

---

### Post by pedro3005 on 2009-09-06
Click Thread Tools then Mark as Solved.

EDIT: Bodsda beat me to it :(

---

