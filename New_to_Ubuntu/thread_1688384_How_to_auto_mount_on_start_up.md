---
title: "How to auto mount on start up?"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by dado prso on 2011-02-15
Hello,

I have all of my music on a separate  partition than Ubuntu. When I start rythmbox, it can't find my music. How do I set Ubuntu to automatically mount this other partition whenever I sign on?

Thanks,
Dado

---

### Post by TeoBigusGeekus on 2011-02-15
Mount your drive and post us the output of 
```
mount
```
```
sudo fdisk -l
```
```
blkid
```
Don't forget to tell us which is the partition you want mounted on startup.

---

### Post by dado prso on 2011-02-15
> **TeoBigusGeekus said:**
> Mount your drive and post us the output of 
```
mount
```
```
sudo fdisk -l
```
```
blkid
```
Don't forget to tell us which is the partition you want mounted on startup.

Hey Thanks! Here it is:

```
eric@ubuntuPC:~$ sudo mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/eric/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=eric)
/dev/sda3 on /media/Storage type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```

```
eric@ubuntuPC:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9f1b3866

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       40543   325553152    7  HPFS/NTFS
/dev/sda3           40543       81072   325553152    7  HPFS/NTFS
/dev/sda4           81072      121602   325551105    5  Extended
/dev/sda5           81072      120122   313665536   83  Linux
/dev/sda6          120122      121602    11884544   82  Linux swap / Solaris

```

blkid did not do anything. The partition I want to mount is sda4.

---

### Post by TeoBigusGeekus on 2011-02-15
Do you mean sda3?

As for blkid, try
```
sudo blkid
```

---

### Post by dado prso on 2011-02-15
> **TeoBigusGeekus said:**
> Do you mean sda3?

As for blkid, try
```
sudo blkid
```

```
eric@ubuntuPC:~$ sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="FCE8D5A8E8D56186" TYPE="ntfs" 
/dev/sda2: UUID="EC82DF6382DF30B6" TYPE="ntfs" 
/dev/sda3: LABEL="Storage" UUID="CEC65614C655FD61" TYPE="ntfs" 
/dev/sda5: UUID="ac32987a-cde9-4599-9127-2c0c5d3a80f5" TYPE="ext4" 
/dev/sda6: UUID="53df999d-7845-4248-aa64-cdafa4c073a9" TYPE="swap" 
```

You are right! sda3!

---

### Post by TeoBigusGeekus on 2011-02-15
Brilliant. You need to edit your fstab file
```
gksu gedit /etc/fstab
```
and add this line 
```
UUID=CEC65614C655FD61 /media/Storage ntfs defaults 0 0
```
at the end of the file.
Save, reboot and you're done.

---

### Post by dado prso on 2011-02-15
> **TeoBigusGeekus said:**
> Brilliant. You need to edit your fstab file
```
gksu gedit /etc/fstab
```
and add this line 
```
UUID=CEC65614C655FD61 /media/Storage ntfs defaults 0 0
```
at the end of the file.
Save, reboot and you're done.

Thank you so much! Can you explain to me what we just did?

---

### Post by TeoBigusGeekus on 2011-02-15
The fstab file controls the partitions that are mounted on startup.

Using the fdisk command, we have a general look at your partitions.

Using the mount command, we found on which folder your partition should be mounted(/media/Storage).

Using the blkid command, we found the UUID - Universally unique identifier - of your partition(CEC65614C655FD61).

With all this info, we added the line

```
UUID=CEC65614C655FD61 /media/Storage ntfs defaults 0 0
```

to the fstab file.

UUID=CEC65614C655FD61 : which partition to mount
/media/Storage : where to mount it
ntfs : format of the partition?
defaults : mount options - defaults should be ok for everyone
0 : should the system perform backups of the partition after a number of mounts? - No.
0 : should the system check the partition for errors after a number of mounts? - No, linux has no tool to check ntfs partitions.

---

### Post by dado prso on 2011-02-15
Awesome. Thank you!

---

### Post by Red Kelly on 2011-02-17
Extremely helpful. Thanks.

---

### Post by Rakeshvijayan on 2011-02-17
Great Help

---

