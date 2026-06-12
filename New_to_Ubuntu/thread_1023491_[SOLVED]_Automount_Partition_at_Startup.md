---
title: "[SOLVED] Automount Partition at Startup"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Raynman37 on 2008-12-28
I have a large storage partition formatted for FAT32 so both my Windows and Ubuntu partitions can access it and I was wondering what I would have to do to have the partition automount when I startup Ubuntu.

I read in an older thread to put a line like this somewhere in the fstab file:

```
/dev/sda1 /home/user/Data           ext3    defaults        0       2
```

I was wondering a.) if this is the best way to do this, and b.) where *exactly* would I put this in the fstab.

Also, I wasn't exactly sure what I was doing and what to do with the storage partition when I was installing Ubuntu this time around because I was doing it differently, so does it sound like I did it right if I have three partitions: NTFS (Windows), FAT32 (shared storage), ext3 (Ubuntu), and Swap.  And if I did it properly, is it normal to have to mount that shared partition when you boot Ubuntu?

---

### Post by taurus on 2008-12-28
If you want that share partition to mount automatically upon boot, then you should add an entry in /etc/fstab for it.

```
/dev/sda1   /media/share   vfat   iocharset=utf8,umask=000  0   0
```
Assuming /dev/sda1 is the partition and /media/share is the mount point.

---

### Post by -kg- on 2008-12-28
Please run the following in a terminal window and post the results:

```
cat /etc/fstab
```

Let's see what your current fstab file looks like.

Edit:  What I'm thinking is that you might already have an entry, but it has been commented out.

Edit2: Please do listen to Taurus, however.  I'm sure he knows *WAY* more about the subject than I do!:P

---

### Post by Raynman37 on 2008-12-28
So would I just have to add

```
/dev/sda4   /media/Shared   vfat   iocharset=utf8,umask=000  0   0
```

to the very end of the fstab file?  Also it looks like each of the different partitions in there have

```
# /dev/sdaX
```

right above it.  Is that there for any reason other than as a comment (# means it's commented out right?)?

---

### Post by taurus on 2008-12-28
If /dev/sda4 is the fat32/vfat partition.

```
sudo fdisk -l
```
And don't forget to create that new mount point.

```
sudo mkdir /media/Shared
sudo mount -a
df -h
```

---

### Post by Raynman37 on 2008-12-28
So if it says:

```
/dev/sda4            3188       35344   258301102+   b  W95 FAT32
```

when I do fdisk -l, should I use "vfat" or "fat32" in the edit to the fstab?  Is there a difference depending on what I put in the file?

---

### Post by taurus on 2008-12-28
You have to use vfat for fat32 filesystem in /etc/fstab.

---

### Post by Raynman37 on 2008-12-28
Awesome, thanks a ton Taurus.  Thread solved!

---

