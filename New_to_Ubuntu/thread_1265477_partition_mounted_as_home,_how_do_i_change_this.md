---
title: "partition mounted as /home, how do i change this?"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by robvvrob on 2009-09-13
I just went through a fresh install of ubuntu, and somehow a small partition i left for recovery tools has been mounted as /home.  I would like my home folder to be located on my primary drive.

How do i fix this?

/dev/sda2 is mounted as /
/dev/sda7 is mounted as /home

both are ext4

thanks for any help ahead of time.

---

### Post by jbrown96 on 2009-09-13
It can be a good idea to keep /home on a separate paritition; it can make it quicker to do a reinstall. However, if you want to make your system only use one partition, here's the procedure.

1) Boot from a LiveCD
2) Mount both partitions. 
```
mkdir Desktop/root && sudo mount /dev/sda2 Desktop/root
```
```
mkdir Desktop/home && sudo mount /dev/sda7 Desktop/home
```
3) Create a folder called home. ```
sudo mkdir Desktop/root/home
```
4) copy your user(s) folder(s) into there. ```
ls Desktop/home/
``` This will show you the folders then ```
sudo cp -R Desktop/root/home/USER
``` replace USER with what you found with ls. This shouldn't take too long. You may need to repeat this for multiple users.
5) Update your fstab. First make a backup just in case. ```
sudo cp Destkop/root/etc/fstab Desktop/root/etc/fstab.backup
``````
sudo gedit Destkop/root/etc/fstab
``` This will open a text editor and you will have something like this: > # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=b212a9ce-a0f6-48b2-bb48-d328ccc1ed99 /               ext4    noatime,relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I have my system all on one partition (it's the line with UUID at the beginning). You will have an additional line that will have /home/ as the mount point; just delete that entire line. Save and exit. 
6) Reboot
7) Verify that /dev/sda7 is not being mounted ```
mount -l
``` This will list out all mounted file systems; look through the list and make sure /dev/sda7 is not on the list.

---

