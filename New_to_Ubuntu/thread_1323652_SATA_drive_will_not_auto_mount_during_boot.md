---
title: "SATA drive will not auto mount during boot"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by VTT Alps on 2009-11-11
I just upgraded from 8.04 to 9.10.  My 500 GB SATA drive was hooked to the computer when I installed 9.10.  I was hoping ubuntu would just auto mount it like it did in 8.04.

Nautilus sees the drive,  but when I click on it, I have to type the root password.  Then an icon appears on the desktop and all is fine.  But it does not return after a re-boot.  

I tried adding a line in the fstab file

/dev/sda1   /media/sda1   ext2   defaults   0   2

then I created a directory  sudo mkdir /media/sda1

then I typed sudo mount -a   and the drive mounts.  However, it still does not auto mount during boot.

Here is what I get when I type  Sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003bffe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001   83  Linux

If anyone knows how to make this drive auto mount during boot,  please let me know. 

Thank you.

---

### Post by Tman5293 on 2009-11-11
I don't know how to fix this but I'm pretty sure that the reason why you have this problem is because you upgraded between to many releases. Its a big jump in between 8.04 and 9.10.

Just sayin. Sorry I Can't Help You. Hope You Find The Answer.

---

### Post by VTT Alps on 2009-11-11
It was a fresh install of 9.10.  All of 8.04 was erased and 9.10 was installed.

---

### Post by VTT Alps on 2009-11-13
Looks like Ubuntu has a bug with the fstab file.  

when I replaced the line in the fstab file (that worked great in 8.04)

/dev/sda1 /media/sda1 defaults 0 2

with 

UUID (disk identifier) /media /sda1 ext2 defaults 0 2

The drive auto mounts every time.  Plus, I can read and write to it.

What happened in 9.10   Why didn't it just see the disk during the installation and take care it automatically.  Why didn't it use my first line of code above.  It worked in 8.04.   


Cheers.

---

