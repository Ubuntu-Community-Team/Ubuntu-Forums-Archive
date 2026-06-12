---
title: "disk space issue/ orphan mount points, etc"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by mystmaiden on 2011-04-16
This disk has been reformated or partially reformated a few times, and now I'm noticing some space issues. I read through and did the steps in the tutorial here on reclaiming disk space and while I was doing it I discovered what I believe are mount points with nothing to mount. Also, there is a folder for sda3 which no longer exists but it contains an old backup file. I tried deleting the backup file via gksudo nautilus but sda3 can not be mounted. 

I'd love some instructions on how to clean this up, I think it will make a difference.

thanks

mystmaiden

---

### Post by K_45 on 2011-04-16
Post the output of

```
fdisk -l
```

and a screenshot of Gparted.

---

### Post by mystmaiden on 2011-04-16
Thanks for the reply! 

fdisk -l 

```
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bc836

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10836    87039146   83  Linux
/dev/sda2           10857       14691    30804637+  83  Linux
/dev/sda3           14692       14946     2048287+   5  Extended
/dev/sda5           14692       14946     2048256   82  Linux swap / Solaris
mystmaiden@hal:~$ 


```sda3 is now the extended partition, but before the re-partitioning the data partition was sda3. I think the backup is stuck in the old file. To add a further little complication here, when I try to change permissions so that I can use the new data partition (named it Stash to avoid confusion with all the 'data')  with these instructions someone kindly gave me awhile back [http://ubuntuforums.org/showthread.php?t=1677576](http://ubuntuforums.org/showthread.php?t=1677576) every way I tried, I get 'no such file or directory'

I'm not sure how pertinent this is, but running 

```
ls /media
data1  data2  floppy  floppy0  sda2  sda3

```That's what made me suspect the issues of drive space and orphan mount points

Attached is a screenshot of gparted.

---

### Post by K_45 on 2011-04-16
Something has gone wrong - fdisk reports around 123GB, Gparted around 115GB. Try this:

```
sudo chown -R username /media/sda2
``` where username is your username

then

```
sudo chmod -R 755 /media/sda2
```

which should fix the permissions for you, for a start.

---

### Post by mystmaiden on 2011-04-17
In every ubuntu I've had to date, the extended partition was sda2 - so I also tried repartitioning the extra space that way. No difference yet in the volume  but before the change, I couldn't run the commands to chown the data partition, afterward I could so I can use that at least. The volume difference has not changed and things are behaving just slightly strangely. Here's the new fdisk and attached is the new gparted

CORRECTION - I can mount sda3 but no permissions yet


```
fdisk -l
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bc836

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10836    87039146   83  Linux
/dev/sda2           14684       14938     2048287+   5  Extended
/dev/sda3           10837       14683    30901027+  83  Linux
/dev/sda5           14684       14938     2048256   82  Linux swap / Solaris


```On reboot now I get an error message that sda2 can't be mounted and it gives the uid number - I'm assuming that's the old one.

---

### Post by K_45 on 2011-04-17
Did you try to chmod the media? 

Can you also post the output of

```
gksu gedit /etc/fstab
```

---

### Post by sandyd on 2011-04-17
> **mystmaiden said:**
> In every ubuntu I've had to date, the extended partition was sda2 - so I also tried repartitioning the extra space that way. No difference yet in the volume  but before the change, I couldn't run the commands to chown the data partition, afterward I could so I can use that at least. The volume difference has not changed and things are behaving just slightly strangely. Here's the new fdisk and attached is the new gparted

CORRECTION - I can mount sda3 but no permissions yet


```
fdisk -l
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bc836

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10836    87039146   83  Linux
/dev/sda2           14684       14938     2048287+   5  Extended
/dev/sda3           10837       14683    30901027+  83  Linux
/dev/sda5           14684       14938     2048256   82  Linux swap / Solaris


```On reboot now I get an error message that sda2 can't be mounted and it gives the uid number - I'm assuming that's the old one.
/dev/sda2 is an extended partition - you don't mount extended partitions, you mount the partitions inside of the extended partition. Which in your case is /dev/sda3.

post the output of
```

sudo mount -l
cat /etc/fstab

```

---

### Post by K_45 on 2011-04-17
^^^

That makes sense. Wasn't clear which partition was which.

---

### Post by mystmaiden on 2011-04-17
Thank you K_45 and Sandyd for the replies. Here  is the code you each requested.

K_45 I just tried to chown Stash (sda3) and it is now working - I'm able to copy files to it, yay!

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=f752e784-ef82-4653-821c-2221bb33361b  /               ext4  defaults                  0  1  
# swap was on /dev/sda5 during installation
UUID=9f7fc64f-4c9b-4fc5-9f94-931c1bb1cde0  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  

/dev/sda3                                  /media/sda3     ext4  users,noauto              0  0  
/dev/sda2                                  /media/sda2     ext4  defaults                  0  0  
```> /dev/sda2 is an extended partition - you don't mount extended partitions, you mount the partitions inside of the extended partition. Which in your case is /dev/sda3.I may have confused the issue with the change I made, sorry. That, or I'm just confused (which is highly probable). Isn't it sda5 (swap) which is inside the extended partition now? 


```
sudo mount -l
/dev/sda1 on / type ext4 (rw)
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
gvfs-fuse-daemon on /home/mystmaiden/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mystmaiden)
/dev/sda3 on /media/sda3 type ext4 (rw,noexec,nosuid,nodev) [Stash]

```and 

```
cat /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=f752e784-ef82-4653-821c-2221bb33361b  /               ext4  defaults                  0  1  
# swap was on /dev/sda5 during installation
UUID=9f7fc64f-4c9b-4fc5-9f94-931c1bb1cde0  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  

/dev/sda3                                  /media/sda3     ext4  users,noauto              0  0  
/dev/sda2                                  /media/sda2     ext4  defaults                  0  0  

```Thanks again for having a look at this

---

### Post by K_45 on 2011-04-17
That looks good. Are you still having any problems?

---

### Post by sandyd on 2011-04-19
> **mystmaiden said:**
> Thank you K_45 and Sandyd for the replies. Here  is the code you each requested.

K_45 I just tried to chown Stash (sda3) and it is now working - I'm able to copy files to it, yay!

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=f752e784-ef82-4653-821c-2221bb33361b  /               ext4  defaults                  0  1  
# swap was on /dev/sda5 during installation
UUID=9f7fc64f-4c9b-4fc5-9f94-931c1bb1cde0  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  

/dev/sda3                                  /media/sda3     ext4  users,noauto              0  0  
/dev/sda2                                  /media/sda2     ext4  defaults                  0  0  
```I may have confused the issue with the change I made, sorry. That, or I'm just confused (which is highly probable). Isn't it sda5 (swap) which is inside the extended partition now? 


```
sudo mount -l
/dev/sda1 on / type ext4 (rw)
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
gvfs-fuse-daemon on /home/mystmaiden/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mystmaiden)
/dev/sda3 on /media/sda3 type ext4 (rw,noexec,nosuid,nodev) [Stash]

```and 

```
cat /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=f752e784-ef82-4653-821c-2221bb33361b  /               ext4  defaults                  0  1  
# swap was on /dev/sda5 during installation
UUID=9f7fc64f-4c9b-4fc5-9f94-931c1bb1cde0  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  

/dev/sda3                                  /media/sda3     ext4  users,noauto              0  0  
/dev/sda2                                  /media/sda2     ext4  defaults                  0  0  

```Thanks again for having a look at this
```

#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=f752e784-ef82-4653-821c-2221bb33361b  /               ext4  defaults                  0  1  
# swap was on /dev/sda5 during installation
UUID=9f7fc64f-4c9b-4fc5-9f94-931c1bb1cde0  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  

/dev/sda3                                  /media/sda3     ext4  users,noauto              0  0 
 
``````

sudo mv /etc/fstab /etc/fstab.bak
sudo nano fstab

```copy and paste the modified fstab (above) and press control +X

and also post results of
```

sudo bkid
```your supposed to mount with UUIDs, not mountpoints.

---

