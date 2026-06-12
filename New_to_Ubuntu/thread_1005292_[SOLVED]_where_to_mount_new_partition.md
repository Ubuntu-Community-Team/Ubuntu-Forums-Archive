---
title: "[SOLVED] where to mount new partition"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by corkscrew on 2008-12-08
I have created a new ext3 partition where I wish to store my data. My partitions are (triple boot xp - nvista and ubuntu)

extended
root
home
swap
new ext3 partition

The new ext3 partition has mounted itself at /media/disk

I would like to mount it on root at directory called ext3data is this possible and is it advisable?

---

### Post by Kobalt on 2008-12-08
Yes it's possible, and advisable. See this for more info : [https://help.ubuntu.com/community/MoveMountpointHowto](https://help.ubuntu.com/community/MoveMountpointHowto)

---

### Post by mapes12 on 2008-12-08
I have a second HDD on my machine where I keep backups of stuff. 

Terminal -
```
sudo mkdir /HDD2
```
# creates a folder in the filesystem called HDD2

```
sudo mount /dev/sdb1 /HDD2
```
# mounts the 2nd HDD Linux partition to the file system via the above directory

Your partition may be something different to sdb1 as in my case. To see what yours is in Terminal ```
fdisk -l
``` will give you its label.

The above does not permanently mount HDD2 as I don't want it mounted every time I boot but the new directory HDD2 sits there for whenever I need to mount to it and I just run the mount command to access the partition when I need it.

---

### Post by taurus on 2008-12-08
If you want to mount that partition automatically each time you boot, then you need to add an entry in /etc/fstab.

```
/dev/XXXX   /ext3data   ext3   defaults   0   2
```
Replace the /dev/XXXX with the actual device or you can use the UUID if you wish.

```
sudo blkid
```
And of course, you need to create that new mount point.

```
sudo mkdir /ext3data
```

---

### Post by corkscrew on 2008-12-08
> **Kobalt said:**
> Yes it's possible, and advisable. See this for more info : [https://help.ubuntu.com/community/MoveMountpointHowto](https://help.ubuntu.com/community/MoveMountpointHowto)

Hey thanks, followed the link and made a dir under root and edited fstab accordingly.

---

