---
title: "Sharing NTFS partition...again..."
date: 2010-10-14
forum: New to Ubuntu
---

### Post by Verbeck on 2010-10-14
I'v been trying to get a new hard drive (ntfs partition) to be shared with a windows pc but nautilus wont let me change the permissions for the folder. Even when i try to open the directory from 'network' on this machine, an error message pops up "unable to mount location - failed to mount windows share" any help ?

/etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=bad8b9e2-6178-41fe-b44d-283b4e3aa327 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=1713728c-b4e1-4ab4-9c27-481f8ba3a5ca /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=eaa0af0e-7ab8-464c-9497-0b1163910a62 none            swap    sw              0       0
UUID="0CC283DCC283C902" /dev/sdb2 ntfs defaults,nls=utf8,umask=0222,gid=46 0    1
```:(

---

### Post by Morbius1 on 2010-10-14
> UUID="0CC283DCC283C902" /dev/sdb2 ntfs defaults,nls=utf8,umask=0222,gid=46 0    1You wouldn't be able to access that partition locally with that line in fstab. You system is ignoring that line because the syntax isn't correct and is instead mounting it by default in Nautilus.

Use the following steps as a template:

(1) Create a permanent mount point:
```
sudo mkdir /media/Data
```(2) Modify your existing fstab line to look like this:
```
UUID=0CC283DCC283C902 /media/Data ntfs defaults,nls=utf8,umask=0222,gid=46 0 0
```Note: the UUID has no quotes around it and you can use UUID or /dev/sdb2 but not both.

(3) Run the following command to test fstab and mount the new partition:
```
sudo mount -a
```

---

### Post by Verbeck on 2010-10-14
thanx, the share is now accessible :D . but the folder is owned by root so i cant create any file/folder there!

---

### Post by Morbius1 on 2010-10-14
It's not because it's owned by root it's because you set umask=0222. A "2" turns off write.

Change umask=0222 to umask=0000

Then unmount the partition. Using the former template as a guide:
```
sudo umount /media/Data
```
Then run:
```
sudo mount -a
```

---

### Post by Verbeck on 2010-10-14
Thank you again for your help .Problem Solved :-D

---

