---
title: "Mounting partitions at start up - Ubuntu 11.04"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by ai4kn on 2011-08-03
[SIZE=3]I currently have a computer with a 320 hard-drive. I have a 50 gb partition for the operating system and associated files plus another 250 gb partition that I use for movies, music, audio books, etc. In addition to the OS partition, I would like to have to the 250 to mount automatically. I can do this manually, and it's no big deal, but I am curious about how to do it automatically.
[/SIZE]

---

### Post by TeoBigusGeekus on 2011-08-03
You need to edit your fstab file.
Mount the drive and post us the output of
```
sudo fdisk -l
```
(-L)
```
mount
```
```
sudo blkid
```
as well as the contents of your fstab file
```
gedit /etc/fstab
```
Don't forget to tell us which is the partition you want mounted.

---

### Post by ai4kn on 2011-08-03
[SIZE=3]/dev/sda2[/SIZE]

---

### Post by TeoBigusGeekus on 2011-08-03
> **ai4kn said:**
> [SIZE=3]/dev/sda2[/SIZE]

Nice. Now open a terminal and post us the output of the commands I gave you.

---

### Post by ai4kn on 2011-08-03
john@john-GT5657E:~$ sudo fdisk -l
[sudo] password for john: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbfaa9354

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10120    81285120   83  Linux
/dev/sda2           10120       38912   231273473    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5           10512       38912   228130528+  83  Linux
/dev/sda6           10120       10512     3142656   82  Linux swap / Solaris

Partition table entries are not in disk order

john@john-GT5657E:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)
/dev/sda5 on /media/Trice002 type ext4 (rw,nosuid,nodev,uhelper=udisks)


john@john-GT5657E:~$ sudo blkid
/dev/sda1: UUID="d173691a-105b-479c-95eb-7709b7381107" TYPE="ext4" 
/dev/sda5: LABEL="Trice002" UUID="2bc18a33-0d12-4583-b481-39692081a7b6" TYPE="ext4" 
/dev/sda6: UUID="bce26dcf-6edf-4185-a11d-2a8a7fa0a3f6" TYPE="swap" 
john@john-GT5657E:~$

---

### Post by TeoBigusGeekus on 2011-08-03
You need to have the drive (sda2) mounted.
Please mount it and post again the output of the commands.

---

### Post by ai4kn on 2011-08-03
I'm sorry, it should have been /sda5

---

### Post by TeoBigusGeekus on 2011-08-03
Alright then. Open your fstab file with write permissions
gksu gedit /etc/fstab
and add this line at the end of it
```
UUID=2bc18a33-0d12-4583-b481-39692081a7b6 /media/Trice002 ext4 relatime 0 2
```
Save, reboot, post back.

---

### Post by ai4kn on 2011-08-03
could that last word relatime have been realtime?

---

### Post by TeoBigusGeekus on 2011-08-03
> **ai4kn said:**
> could that last word relatime have been realtime?

Nope. It's relatime.

---

### Post by ai4kn on 2011-08-03
It worked.  It took me a while to correct the spelling errors, but I finally got it.

---

### Post by TeoBigusGeekus on 2011-08-03
Brilliant!!!
Don't forget to mark the thread as solved.
For a brief explanation of what we did, read post #8 in [here]("http://ubuntuforums.org/showthread.php?t=1688384").

---

### Post by ai4kn on 2011-08-03
It worked.  It took me a while to correct the spelling errors, but I finally got it.

---

