---
title: "Partitions not mounting?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by Rusty023 on 2008-12-05
I have a 3-partition setup, a 10GB partition, and then two 70GB partitions. Xubuntu 8.10 is installed on the first 70GB partitions. I had two NTFS partitions, and they wouldn't mount, so in GParted I deleted them and created new partitions (FAT32, ext2, ext3) and none of them would mount.

I don't care what file system they are, I just want them to mount so I can use them. Can someone tell me what to do, I'm pretty lost.

---

### Post by taurus on 2008-12-05
You just need to an entries for those three partitions if you want them to mount automatically each time you boot ubuntu.  Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by Rusty023 on 2008-12-05
sudo fdisk -l output:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe9e4f133

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            1275       10383    73168042+   5  Extended
/dev/sda5            1275       10006    70139758+  83  Linux
/dev/sda6           10007       10383     3028221   82  Linux swap / Solaris
rusty@rusty-desktop:~$ 
```

sudo blkid output:
```

/dev/sda1: UUID="BEF69F1CF69ED44D" LABEL="Music" TYPE="ntfs" 
/dev/sda3: UUID="94285DB8285D9A56" LABEL="Games" TYPE="ntfs" 
/dev/sda5: UUID="e7abb71c-ba9d-4d4f-82e7-8a3d7acd0b50" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="5ca5797c-4244-4435-9128-9977f645218c"
```

cat /etc/fstab output:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=e7abb71c-ba9d-4d4f-82e7-8a3d7acd0b50 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=5ca5797c-4244-4435-9128-9977f645218c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
df -h output:
```
Filesystem            Size Used Avail Use% Mounted on
/dev/sda5              66G  2.0G   61G   4% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  108K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.9M  502M   1% /dev
tmpfs                 505M     0  505M   0% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-7-generic/volatile
```

It appears that my partitions are still NTFS, but corrupted. I would muchly like to keep these NTFS partition's data if at all possible, thanks.

---

### Post by taurus on 2008-12-05
Both /dev/sda1 & /dev/sda3 don't even show up!  I am getting a mixed signal here.  You said that you used gparted to format them to vfat, ext2, and ext3 but now you want to keep those partitions because you have data on them?  

What happens if you try to mount them from a terminal?

```
sudo mkdir /media/sda1 /media/sda3
sudo mount -t ntfs-3g /dev/sda1 /media/sda1 -o force
sudo mount -t ntfs-3g /dev/sda3 /media/sda3 -o force
```

---

### Post by Rusty023 on 2008-12-05
They now appear to be mounted however I can't write anything and it still seems messed up.

---

### Post by taurus on 2008-12-05
Can you access those two mount points, /media/sda1 & /media/sda3?  I would strongly recommend you back up your music and games from those two partitions.  Then, reformat those two partitions to ext3 (Linux native filesystem) since it doesn't look like you have windows on that machine anymore.  Unless you have windows on that machine, why even bother using ntfs filesystem?

---

