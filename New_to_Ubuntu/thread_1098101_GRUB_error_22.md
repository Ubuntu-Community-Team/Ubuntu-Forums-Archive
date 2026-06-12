---
title: "GRUB error 22"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by onthestairs on 2009-03-16
Hi everyone,

This is my first experience with Linux so excuse my limited knowledge. I burned the boot cd, booted up and installed ubuntu what i thought was successfully. However, when i was struggling to get my wireless connection set up, I decided to go back onto windows vista to do some googling.

So i restarted and got the option of a few different things, i chose windows vista/longhorn and it loaded for a bit before a big error message came up. I can't remember exactly what it was, but it mentioned recovery.dat and I couldn't do anything so i had to force a shut down.

I turned the computer back on and this is when I got the GRUB error 22. It occurs when doing something regarding stage1.5.

I am currently running off the ubuntu live cd. I tried working through [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick%20Start](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick%20Start) but was unsuccesful, I kept getting the file not found error.

After my research, I believe the following information may be of use. It is the result of fdisk -lu
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6c2421e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    16386047     8192000   1c  Hidden W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    16386048   207454653    95534303    7  HPFS/NTFS
/dev/sda3       207463410   436116554   114326572+   f  W95 Ext'd (LBA)
/dev/sda5       260585472   436104778    87759653+   7  HPFS/NTFS

Disk /dev/sdc: 1006 MB, 1006632960 bytes
65 heads, 32 sectors/track, 945 cylinders, total 1966080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32     1966079      983024    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(960, 64, 32) logical=(945, 14, 32)

```

I would be very grateful for any help concerning this matter, as I currently can't access either of my operating systems!

Thanks

---

### Post by Dynaflow on 2009-03-16
Try this:  [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

This is Grub Error 22 explained:  [http://www.jumpingbean.co.za/blogs/mark/grub_error_22](http://www.jumpingbean.co.za/blogs/mark/grub_error_22)

---

### Post by Dynaflow on 2009-03-16
Come to think of it, your partition table does look rather ... eccentric.  For contrast, my Vista/Ubuntu dual-boot machine's partitions look like this:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2a182a17

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    55376054    27687996    7  HPFS/NTFS
/dev/sda2        55376055    56163239      393592+  83  Linux
/dev/sda3        56163240   156296384    50066572+  83  Linux
```

How, exactly, did you go about installing Ubuntu?

---

