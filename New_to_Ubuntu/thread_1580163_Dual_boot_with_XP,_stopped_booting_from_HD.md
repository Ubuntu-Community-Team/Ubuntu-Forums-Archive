---
title: "Dual boot with XP, stopped booting from HD"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by cmmichael on 2010-09-22
I've seen this problem in recent posts, but with no solutions, so I'll try to spell everything out. I tried a dual boot install of 10.04 on a HP mini 311, with the Nvidia Ion LE chip. It ran OK from the thumbdrive, there's plenty of room on the HD, and the install seemed fine - ran a few times yesterday. Today it will boot from the thumbdrive, but trying to boot from the HD stops with a blinking cursor and a black screen. 

I have a couple of years experience with Hardy Heron on a desktop, so I know how to run command lines. Also, I'd like to change the interface back to one that is more familiar, the HP screen isn't that small.

---

### Post by mikewhatever on 2010-09-23
Looks like the classic case for [Boot Info Script]("http://sourceforge.net/projects/bootinfoscript/"). Run it (sudo ./boot_info_script055.sh) and post the output.

---

### Post by Rubi1200 on 2010-09-23
As above, but we also need to know what graphics card you have installed please.

---

### Post by cmmichael on 2010-09-23
Now it's not booting from the thumbdrive. Here is a transcript of the relevant messages - I'm working thru XP to communicate here. 

No filesystem could mount root, tried: ext3, ext2, ext4, fuseblk

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block (8,1)


The Nvidia chip is the graphics card, right?

---

### Post by cmmichael on 2010-09-23
I should add that I tried to reinstall from the thumbdrive when it was working. I didn't see any way to overwrite the existing partition.

---

### Post by Rubi1200 on 2010-09-23
Is Windows working?

Yes, then please post the results of the bootscript linked to by mikewhatever; it will give us a better idea of what is going on and make offering solutions easier.

Thanks.

---

### Post by cmmichael on 2010-09-23
OK - thumbdrive is working ...


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

error: /dev/loop0: Permission denied
error: /dev/sda1: Permission denied
error: /dev/sda5: Permission denied
error: /dev/sda6: Permission denied
error: /dev/sda: Permission denied
error: /dev/sdc1: Permission denied
error: /dev/sdc: Permission denied

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/d433916a-7ee9-413c-801d-01af75fa7dba ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

=======Devices which don't seem to have a corresponding hard drive==============

sda sdc 
=============================== StdErr Messages: ===============================

dmraid: error while loading shared libraries: /lib/libdmraid.so.1.0.0.rc16: cannot read file data: Input/output error
dmraid: error while loading shared libraries: /lib/libdmraid.so.1.0.0.rc16: cannot read file data: Input/output error
dmraid: error while loading shared libraries: /lib/libdmraid.so.1.0.0.rc16: cannot read file data: Input/output error

---

### Post by cmmichael on 2010-09-24
bumpity

---

### Post by mikewhatever on 2010-09-24
Are you sure you've run the script with sudo? Usually, the output is much longer then you posted.

---

### Post by Rubi1200 on 2010-09-24
Also there are a number of errors here that I would be concerned about:
```
no valid partition table found
```
```
Permission denied
```

> I should add that I tried to reinstall from the thumbdrive when it was  working. I didn't see any way to overwrite the existing partition. 	
You didn't by chance wipe out the whole installation by mistake?

---

### Post by cmmichael on 2010-09-25
No. I use gparted (I think) on the thumbdrive to reformat the main ext4 partition. 

After two more reinstall tries from the thumbdrive, I'm getting the same result. Between the install and the restart, I get the following error message:

Error mounting '64 GB Filesystem': Daemon is inhibited.

I think I've gotten the same message each time. Any ideas on where to go from here?

---

### Post by beew on 2010-09-25
Exactly how did you install in the thumb drive in the first place? Did you choose "manually install" in step 4 or something automatic?

Ok, consider the following scenario, if you create a dual boot by installing Ubuntu in a partition in the hard disk side by side with Windows and later delete the Ubuntu partition, Windows would not boot anymore. The remedy would be to boot from a Windows CD and go into repair then type fixmbr.

I think something like that is happening here. When you installed into the thumb drive, depending on your mode of installation the thumb drive might appear to be a part of the hdd so removing it would be like deleting the Ubuntu partition in the dual boot. 

So the solution may be the same. Boot from a Windows CD and do fixmbr.

I am only guessing but since so far all other advices don't seem to work, my guess is probably just as good or bad as the others'. :)

---

### Post by wilee-nilee on 2010-09-25
If you look at XP from gparted is there a triangle flag, and in the right click information does it tell you you may need a chkdsk.

---

