---
title: "help with mount points"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by DarinB on 2009-01-31
About two months ago i got help at this site for mounting my 2nd hard drive at boot up for my music.
now my /dev/sda1 does not show up in system monitor in partition editor i get a warning unable to find mount point. i am trying to *** a screen shot as an attachment.
I really don't know why this thing still boots up if the main drive can't be found but how do i fix this???????

---

### Post by taurus on 2009-01-31
Post the outputs of these commands from a terminal.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by DarinB on 2009-01-31
darin@darin-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ae79d16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19175   154023156   83  Linux
/dev/sda2           19176       19457     2265165    5  Extended
/dev/sda5           19176       19457     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcaf8909d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux
darin@darin-desktop:~$ sudo blkid
/dev/sdb1: UUID="3a4f7394-8461-4d90-abf8-7489fecd4825" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdc1: UUID="3a4f7394-8461-4d90-abf8-7489fecd4825" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda1: UUID="49c0f552-e94d-4748-b938-3f5c17e4f39e" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="6e020492-7bb1-4b19-be11-f6ef3c3ff128" 
darin@darin-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
 /dev/sdb1   /music   ext3   defaults   0   1
# /dev/sdb5
UUID=6e020492-7bb1-4b19-be11-f6ef3c3ff128 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
darin@darin-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 378M     0  378M   0% /lib/init/rw
varrun                378M  204K  378M   1% /var/run
varlock               378M     0  378M   0% /var/lock
udev                  378M  2.9M  375M   1% /dev
tmpfs                 378M   60K  378M   1% /dev/shm
rootfs                145G   33G  105G  24% /
lrm                   378M  2.0M  376M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb1              74G   52G   19G  75% /music
darin@darin-desktop:~$

---

### Post by taurus on 2009-01-31
Somehow, your root filesystem, /dev/sda1, is not mounted through /etc/fstab.

Therefore, edit it

```
gksudo gedit /etc/fstab
```
and add this line after the proc entry.

```
UUID=49c0f552-e94d-4748-b938-3f5c17e4f39e   /   ext3   relatime,errors=remount-ro   0   1
```
Save it and reboot.

---

### Post by DarinB on 2009-01-31
Thank you Thank you thank you
i am not sure what i did to get the muxic to mount, but i must have altered
the fstab.
I works great now.
gotta love the philosophy of Ubuntu community!!!!!

---

