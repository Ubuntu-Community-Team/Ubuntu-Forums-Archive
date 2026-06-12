---
title: "Restart to fsck error 8"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by Elep.Repu on 2009-08-11
I've done this a few times, but running fsck hasn't helped, I reformatted the drive too, so I'm not sure.
This just started happening after an installation, so I'm not sure.
I'll post my fstab and the error log for you.

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=b680172e-f2d5-4d09-ab2a-37d154ce90fc /               ext3    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=edc4a964-baf0-49fd-98fa-85c4177e08b2 /boot           ext3    relatime        0       2
# /home was on /dev/sda7 during installation
UUID=df00275c-2d08-4299-bdab-89881918866e /home           ext3    relatime        0       2
# swap was on /dev/sda1 during installation
UUID=0dfc924a-ddfd-414d-a74e-9408d6f54502 none            swap    sw              0       0
# swap was on /dev/sdb3 during installation
UUID=f1171db9-771c-461e-a602-0ee8e4922e80 none            swap    sw              0       0
# swap was on /dev/sdc2 during installation
UUID=0de4c836-a1b1-4c0e-9096-0a14f45a0a04 none            swap    sw              0       0
# swap was on /dev/sdd8 during installation
UUID=c024d8a1-63da-4da1-960f-a4eab772c8e3 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sdb3       none            swap        sw                    0       0

/dev/sdb1       /media/Lib      ext3        defaults              0       2
/dev/sdb2       /media/Sed      ext3        defaults              0       2

/dev/sdb4       /media/bk       ext3        defaults              0       2
/dev/sdc1       /media/vbox     ext3        defaults              0       2
/dev/sdd5       /media/Pr0n     ext3        defaults              0       2
/dev/sdd6       /media/pic      ext3        defaults              0       2
/dev/sdd7       /media/prog     ext3        defaults              0      2
/dev/sde1       /media/bak      ext3        defaults              0       2

```Fsck log

```
Log of fsck -C3 -R -A -a 
Tue Aug 11 16:29:08 2009

fsck 1.41.4 (27-Jan-2009)
fsck.ext3: No such file or directory while trying to open /dev/sde1 
/dev/sde1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

/dev/sda5: clean, 38/24096 files, 36408/96356 blocks
vbox: clean, 11/960992 files, 102495/3839527 blocks
Pr0n: clean, 10/2616320 files, 209263/10462315 blocks
Lib: clean, 14657/19202048 files, 71077782/76800732 blocks
/dev/sda7: clean, 18196/58884096 files, 15766501/235510884 blocks
pictures: clean, 2346/640848 files, 1150385/2560351 blocks
Sed: clean, 17412/14147584 files, 17893852/56576913 blocks
prog: clean, 17356/1602496 files, 4741904/6399886 blocks
bk: clean, 8999/27516928 files, 10795788/110045250 blocks
fsck died with exit status 8

Tue Aug 11 16:29:10 2009
----------------



```I'm not sure what I should be doing. I don't think the drive is bad. 
When I take:
```
/dev/sde1       /media/bak      ext3        defaults              0       2
```
out of fstab, I boot fine.

---

