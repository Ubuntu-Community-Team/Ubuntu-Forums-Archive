---
title: "Is it as bad as i think?Ext3 over my ntfs?"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by mickey57 on 2009-06-03
[SIZE="3"]
Oh hell,I think I lost xp...........

....I did a check file system (shutdown -Fr now) last night.Came back to my computer this morning and tried go into my xp ntfs from ubutu.Clicked on the drive and it threw me into 'Lost and found"!!!!!!.Rebooted and got the,"error 13 invalid or unsupported executable format"When trying to boot into my xp!
.....Grub looks fine
## ## End Default Options ##

title Ubuntu karmic (development branch), kernel 2.6.30-6-generic
uuid e0858650-7da3-44ec-8b49-645550257878
kernel /boot/vmlinuz-2.6.30-6-generic root=UUID=e0858650-7da3-44ec-8b49-645550257878 ro quiet splash
initrd /boot/initrd.img-2.6.30-6-generic
quiet

title Ubuntu karmic (development branch), kernel 2.6.30-6-generic (recovery mode)
uuid e0858650-7da3-44ec-8b49-645550257878
kernel /boot/vmlinuz-2.6.30-6-generic root=UUID=e0858650-7da3-44ec-8b49-645550257878 ro single
initrd /boot/initrd.img-2.6.30-6-generic

title Ubuntu karmic (development branch), kernel 2.6.30-5-generic
uuid e0858650-7da3-44ec-8b49-645550257878
kernel /boot/vmlinuz-2.6.30-5-generic root=UUID=e0858650-7da3-44ec-8b49-645550257878 ro quiet splash
initrd /boot/initrd.img-2.6.30-5-generic
quiet

title Ubuntu karmic (development branch), kernel 2.6.30-5-generic (recovery mode)
uuid e0858650-7da3-44ec-8b49-645550257878
kernel /boot/vmlinuz-2.6.30-5-generic root=UUID=e0858650-7da3-44ec-8b49-645550257878 ro single
initrd /boot/initrd.img-2.6.30-5-generic

title Ubuntu karmic (development branch), memtest86+
uuid e0858650-7da3-44ec-8b49-645550257878
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Windows NT/2000/XP
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
**********************************
 fdisk -lu  <  Mickey-57 >  06/03 09:23:02

*********************************
..The NTFS appears to still be there:
mickey@mickey-desktop:~$ sudo fdisk -lu
[sudo] password for mickey:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0c8acc5d

Device Boot Start End Blocks Id System
/dev/sda1 * 63 149838254 74919096 83 Linux
/dev/sda2 149838255 156296384 3229065 5 Extended
/dev/sda5 149838318 156296384 3229033+ 82 Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf18df18d

[COLOR="Red"]Device Boot Start End Blocks Id System
/dev/sdb1 * 63 156232124 78116031 7 HPFS/NTFS
/dev/sdb2 156232125 156248189 8032+ 8e Linux LVM[/COLOR]
mickey@mickey-desktop:~$ 



Hard drive with Ubuntu....

*-disk:0
description: ATA Disk
product: WDC WD800JB-00JJ
vendor: Western Digital
physical id: 0
bus info: scsi@2:0.0.0
logical name: /dev/sda
version: 05.0
serial: WD-WCAM9S263707
size: 74GiB (80GB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 signature=0c8acc5d
*-volume:0
description: EXT3 volume
vendor: Linux
physical id: 1
bus info: scsi@2:0.0.0,1
logical name: /dev/sda1
logical name: /
version: 1.0
serial: e0858650-7da3-44ec-8b49-645550257878
size: 71GiB
capacity: 71GiB
capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
configuration: created=2009-05-15 09:43:04 filesystem=ext3 modified=2009-06-03 11:04:34 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=writeback mounted=2009-06-03 10:16:27 state=mounted
*-volume:1
description: Extended partition
physical id: 2
bus info: scsi@2:0.0.0,2
logical name: /dev/sda2
size: 3153MiB
capacity: 3153MiB
capabilities: primary extended partitioned partitioned:extended
*-logicalvolume
description: Linux swap / Solaris partition
physical id: 5
logical name: /dev/sda5
capacity: 3153MiB
capabilities: nofs 

Hard that "HAD" XP.......Oh Hell!!!!!!!! 

*-disk:1
description: ATA Disk
product: Maxtor 6L080P0
vendor: Maxtor
physical id: 1
bus info: scsi@2:0.1.0
logical name: /dev/sdb
version: BAH4
serial: L2262S3G L2262S3G
size: 74GiB (80GB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 signature=f18df18d
*-volume:0
description: EXT3 volume
vendor: Linux
physical id: 1
bus info: scsi@2:0.1.0,1
logical name: /dev/sdb1
[COLOR="Red"]logical name: /media/a90b9405-8fbb-4cfa-a740-565042beb532[/COLOR]
version: 1.0
serial: a90b9405-8fbb-4cfa-a740-565042beb532
size: 74GiB
capacity: 74GiB
capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
[COLOR="Red"]configuration: created=2009-06-02 21:37:54 filesystem=ext3 modified=2009-06-03 11:24:32 [/COLOR]mount.fstype=ext3 mount.options=rw,nosuid,nodev,relatime,errors=continue,data=writeback mounted=2009-06-03 11:24:32 state=mounted
*-volume:1
description: Linux LVM Physical Volume partition
physical id: 2
bus info: scsi@2:0.1.0,2
logical name: /dev/sdb2
serial: 35qSbB-fxE7-0lCP-w59a-SsLk-UU94-FwbeiT
size: 8032KiB
capacity: 8032KiB
capabilities: primary multi lvm2 
********************************************************
...It appears that more went on than I intended :([/SIZE]

---

### Post by billgoldberg on 2009-06-03
Post outcome of

```
sudo fdisk -l
```

---

### Post by mickey57 on 2009-06-03
> **billgoldberg said:**
> Post outcome of

```
sudo fdisk -l
```
**************************
mickey@mickey-desktop:~$ sudo fdisk -l
[sudo] password for mickey: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c8acc5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf18df18d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9725    78116031    7  HPFS/NTFS
/dev/sdb2            9726        9726        8032+  8e  Linux LVM
mickey@mickey-desktop:~$
************************
mickey@mickey-desktop:~$ sudo ntfsmount /dev/sdb1
Access is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
You can use force option to avoid this check, but this is not recommended
and may lead to data corruption.
*******************************
Unmounted it then:
mickey@mickey-desktop:~$ sudo ntfsmount /dev/sdb1
Failed to startup volume: Invalid argument.
Failed to mount '/dev/sdb1': Invalid argument.
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
Mount failed.

---

