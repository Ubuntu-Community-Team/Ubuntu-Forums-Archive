---
title: "Boot time-'waiting for resume device'"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by ExileAmongYou on 2009-01-31
Ever since I got rid of an old install of ubuntu, deleted the partition it was on and resized my main partition to fill the space, ubuntu takes significantly longer to boot up (by about 30 seconds or so). It appears to get stuck for a long time on "waiting for resume device".

Does anyone have any ideas about how to fix this?

---

### Post by Ptero-4 on 2009-01-31
Check if the UUID and device number (sda1, sda2, etc) of your swap partition matches what both the /etc/fstab and the "resume" part of the kopt line in /boot/grub/menu.lst (that´s an "L" in the filename extention). To do that you type
```
 sudo cfdisk
```
in the console (cfdisk won´t open unless you put the "sudo" in front of it). This will show you exactly which number your swap partition have. From there you use the blkid command to get the partition´s UUID and then you check both number and/or UUID against what the fstab and menu.lst says and fix it in both files if it doesn´t match the cfdisk and blkid output.

---

### Post by ExileAmongYou on 2009-01-31
Okay, so cfdisk lists my main partition as sda5 and my swap as sda6. 
blkid gives this:
```
/dev/sda1: UUID="22f4c492-052b-42c4-8881-0269d1b79e20" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="35d86082-af4d-4bc4-be9a-15dac41e92f2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="c6878f5d-bf0b-46bd-a9bf-dc0856f037a9" 
/dev/sda7: UUID="a1ea9975-77ab-4eeb-b245-04837c231f58" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="4970-5B73" TYPE="vfat" 
/dev/mmcblk0p1: SEC_TYPE="msdos" LABEL="G400-SD" UUID="4B06-956B" TYPE="vfat" 
```

and fstab has 
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=35d86082-af4d-4bc4-be9a-15dac41e92f2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=a1ea9975-77ab-4eeb-b245-04837c231f58 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

They obviously don't all match up, but what exactly am I supposed to be editing?

---

### Post by Ptero-4 on 2009-01-31
The one in fstab. And also check in menu.lst and edit as well.

---

