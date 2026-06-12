---
title: "i think i overwrote windows on install...help!"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by boblettoj99 on 2008-12-21
Hi i just tried to install kubuntu on my computer (already had win xp on it), it worked fine but i think in the process of resizing partitions i overwrote windows. 
Once kubuntu was installed i mounted the windows partition fine but the only folder in it is called "lost + found", when i try to enter that it says "could not enter folder"

have i completely messed it up?
is there any way of getting windows back?
please help!!!

---

### Post by az on 2008-12-21
> **boblettoj99 said:**
> Hi i just tried to install kubuntu on my computer (already had win xp on it), it worked fine but i think in the process of resizing partitions i overwrote windows. 
Once kubuntu was installed i mounted the windows partition fine but the only folder in it is called "lost + found", when i try to enter that it says "could not enter folder"

have i completely messed it up?
is there any way of getting windows back?
please help!!!

If the windows partition is still there, you formatted it.  You may still be able to recover some files using data-carving, but there is no way you will recover a fully-functioning Os from that partition.

See [http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

Use photorec or foremost to data-carve file types you want to recover.  Use one of those to recover family photos or mp3s and the like.

---

### Post by hexanol on 2008-12-21
"lost + found" is typical of a non-windows partition. Please post the result of ```
sudo fdisk -l
```
and we might be able to tell if you did erase your windows partition.

---

### Post by Monotoko on 2008-12-21
Do you not have any Windows disks kicking around anywhere? If so i would get them out, because you may need to reinstall windows

---

### Post by boblettoj99 on 2008-12-21
i assume the line you're interested in is:
/dev/sda1        1         54462       437465983+      7      HPFS/NTFS

the linux machine isn't hooked up to the internet yet so im using windows laptop atm which is why i couldnt copy it straight here.

---

### Post by boblettoj99 on 2008-12-21
i'd like to avoid that at all costs...unless i can do a windows repair, some veeeery important files on there. and yes i know....backup :(

---

### Post by OutOfReach on 2008-12-21
> **boblettoj99 said:**
> i assume the line you're interested in is:
/dev/sda1        1         54462       437465983+      7      HPFS/NTFS

the linux machine isn't hooked up to the internet yet so im using windows laptop atm which is why i couldnt copy it straight here.

Hmm it seems that your Windows partition is still there, I am not sure if the actual OS is still there though.
How exactly did you access the Windows drive?

---

### Post by hexanol on 2008-12-21
Indeed, that may be good sign, depending on how many windows partition you had before.

Well, just try to mount this partition and see if your files are still intact. I guess they should be.

---

### Post by boblettoj99 on 2008-12-21
i went to system settings>advanced>disks + filesystems, the sda1 partition was there so i enabled it and it came up in storage media..

---

### Post by boblettoj99 on 2008-12-21
i don't know if i mounted it properly..
what are the correct settings, at the moment the mount point is /sda1 is that right? i kind of guessed...

---

### Post by boblettoj99 on 2008-12-21
perhaps my fstab will help?
its looking pretty messy...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=c6c6db2c-d1cf-4f4a-b6f5-d28dee6adf4d / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda5
UUID=3e5ed18f-e85f-4b4e-88f6-6e0d0c4ed96b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
<device> /dev/disk auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/sda1 / auto nouser,atime,auto,rw,nodev,noexec,nosuid 0 0

---

### Post by boblettoj99 on 2008-12-21
perhaps my fstab will help?
its looking pretty messy...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=c6c6db2c-d1cf-4f4a-b6f5-d28dee6adf4d / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda5
UUID=3e5ed18f-e85f-4b4e-88f6-6e0d0c4ed96b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
<device> /dev/disk auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/sda1 / auto nouser,atime,auto,rw,nodev,noexec,nosuid 0 0

---

### Post by boblettoj99 on 2008-12-21
oops

---

