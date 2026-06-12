---
title: "External Hard Drive Won't Mount After Burning CD"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by stargrrl17 on 2010-01-28
I burned a cd and now I can't mount my external hard drive. When I try to mount it in the file manager I get this:
> Error org.freedesktop.Hal.Device.Volume.UnknownFailureI have Googled this error and all I can find is information for Windows/Linux partitions which I don't have or NTFS format, mine is Ext2 formatted. I did that the day I got it. Up to this point it has mounted just fine. 

When I run fdisk -l I get this:
>  Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x008bd57c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  LinuxWhich I think is ok?

When I try to manually mount it I get this:
> didi@didi-laptop:~$ sudo mount -t ext2 /dev/sdb1 /mnt/externalhd/
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or soWhen I try dmesg | tail I get this
> [ 4686.602786] EXT2-fs: unsupported inode size: 0
[ 4753.421661] EXT2-fs: unsupported inode size: 0
[ 4753.485663] EXT2-fs: unsupported inode size: 0
[ 4762.074655] EXT2-fs: unsupported inode size: 0
[ 4762.142049] EXT2-fs: unsupported inode size: 0
[ 5154.201783] EXT2-fs: unsupported inode size: 0
[ 5154.281658] EXT2-fs: unsupported inode size: 0
[ 9014.620539] EXT2-fs: unsupported inode size: 0
[ 9131.358416] EXT2-fs: unsupported inode size: 0
[ 9131.421787] EXT2-fs: unsupported inode size: 0

I don't actually know if that is useful or not, but I thought it'd be better to include it.

When I run fsck /dev/sdb1 I get this:
> fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Superblock invalid, trying backup blocks...
ExternalHD was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizesI never unmounted my hard drive so I don't know why it says that.
It also gave me this option:
> Inode 5431299, i_blocks is 1424848, should be 1434496.  Fix<y>?I haven't chosen yes because I don't want to mess anything up further. 

I hope the info I've provided is useful, I have been trying to figure this out for about 3 hours and have gotten nowhere. I would greatly appreciate any help.
BTW I am a newbie, so if there is anything wrong with this post, please let me know so I can fix it!!!:)

---

### Post by phillw on 2010-01-28
> **stargrrl17 said:**
> I burned a cd and now I can't mount my external hard drive. When I try to mount it in the file manager I get this:
I have Googled this error and all I can find is information for Windows/Linux partitions which I don't have or NTFS format, mine is Ext2 formatted. I did that the day I got it. Up to this point it has mounted just fine. 

When I run fdisk -l I get this:
Which I think is ok?

When I try to manually mount it I get this:
When I try dmesg | tail I get this
I don't actually know if that is useful or not, but I thought it'd be better to include it.

When I run fsck /dev/sdb1 I get this:
I never unmounted my hard drive so I don't know why it says that.
It also gave me this option:
I haven't chosen yes because I don't want to mess anything up further. 

I hope the info I've provided is useful, I have been trying to figure this out for about 3 hours and have gotten nowhere. I would greatly appreciate any help.
BTW I am a newbie, so if there is anything wrong with this post, please let me know so I can fix it!!!:)

Hi & welcome to the forums,

It is quite safe to say <y>es  fix it, provided the drive is not mounted. To double check that it is not mounted type the following ```
df -H
``` the drive (sdb) should **not** be listed.

Regards,

Phill.

---

### Post by stargrrl17 on 2010-01-28
> **phillw said:**
> Hi & welcome to the forums,

It is quite safe to say <y>es  fix it, provided the drive is not mounted. To double check that it is not mounted type the following ```
df -H
``` the drive (sdb) should **not** be listed.

Regards,

Phill.

Thanks so much for your quick reply. I entered yes, restarted, and the drive started just fine. The best part was that all the files were there. I was worried about that because I had a lot of pics that were irreplaceable. So thank you again.

---

### Post by warfacegod on 2010-01-28
You may want to consider checking your hard drive with Palimpset and/or gsmartcontrol. Making a backup might be wise, if you have the room on another hard drive.

---

### Post by phillw on 2010-01-28
> **stargrrl17 said:**
> Thanks so much for your quick reply. I entered yes, restarted, and the drive started just fine. The best part was that all the files were there. I was worried about that because I had a lot of pics that were irreplaceable. So thank you again.

Glad it's fine. Linux files are hardy animals and it is a real bad day if fsck cannot ride to the rescue !!

As a foot-note, ext2 is a pretty old filesystem - you might want to consider changing to ext3, or even the newer one ext4.  It's real quick, but you do need to take a backup, just in case (I've not known it bork a drive - but a power cut half-way through could be real bad news)

Regards,

Phill.

---

