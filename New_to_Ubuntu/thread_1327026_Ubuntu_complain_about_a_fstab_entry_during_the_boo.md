---
title: "Ubuntu complain about a fstab entry during the boot process...."
date: 2009-11-15
forum: New to Ubuntu
---

### Post by legolas_w on 2009-11-15
Hi


When I turn on my laptop I get an error message complaining about the fact that Linux can not mount one of the entries in the /etc/fstab (but system boot and work properly)
Following snippet shows my fstab content and as far as I can say all of them are valid because I can use /home, /opt, / and the swap space. other entries are commented as you can see in the code.




```


# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=23caec3b-2cf8-4824-ac78-f36480daf57b /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=40b97400-9a1b-48e8-aba5-23fa82a2d569 /home           ext3    relatime        0       2
# /opt was on /dev/sda2 during installation
UUID=a06750df-2464-41c4-b689-aa819074ad0f /opt            ext3    relatime        0       2
# swap was on /dev/sda6 during installation
UUID=f7cbe24a-0f99-41a8-8cd7-31ca009d9dad none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#UUID=0E842FDA3AD44253 /media/Archive           ntfs-3g defaults,locale=en_US.utf8 0 0
#/dev/sdb1 /media/Personal  ext3    relatime        0       2


#Musics, uncomment when away from external disk

#UUID=64b6db3e-3abc-4bff-805e-f73adefa0aa8 /media/Personal  ext3    relatime        0       2



```


Do you see any abnormality in the code?



Thanks.

---

### Post by longtom on 2009-11-15
No, I don't.  But I checked my fstab because of your post and guess what:

It looks similar!  The partition were my system is running on also says "errors=remount-ro" but works like a charm.

Beats me...

---

### Post by grandtoubab on 2009-11-15
check your disk
```
sudo fdisk -l
```



```
ls -l /dev/disk/by-uuid
``` 
and compare with your fstab

---

### Post by grandtoubab on 2009-11-16
**errors=continue** / **errors=remount-ro** / **errors=panic** Define the behaviour when an error is encountered. (Either  ignore errors and just mark the file system erroneous and continue, or  remount the file system read-only, or panic and halt the system.) The default is set in the  filesystem superblock, and can be changed using [I]**[tune2fs]("http://linux.die.net/man/8/tune2fs")**

[/I] [http://linux.die.net/man/8/mount ]("http://linux.die.net/man/8/mount")
):P
[ ]("http://linux.die.net/man/8/mount")

---

