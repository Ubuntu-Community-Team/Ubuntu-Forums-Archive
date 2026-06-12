---
title: "Finding second hard drive on eee netbook"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by bahsarie on 2008-12-16
Hi, I just got a eee 1000 netbook installed  xubuntu on it and can only find the smaller 8gb ssd and would like to get accesses to the second 32 gb hd. If anyone knows how to find and mount it I would be greatly appreciative. I have checked the file system but have not been able to find it  in there.

---

### Post by jbrown96 on 2008-12-16
I didn't know the eee's came with two hard drives, but I can help you find it if it is there.
First, open a terminal, Applications-->Accessories-->Terminal.

```
sudo fdisk -l
```
You will definately find an entry called /dev/sda. If there is a second drive, it will be listed as /dev/sdb. If you could post the output of this command, I can help you further, but here's basically what you need to do.

1) figure out which partition you want to mount /dev/sda1, /dev/sdb1, /dev/sda2, etc. 
2) figure out where you want to mount it. I generally recommend you home folder, and on an eee it would be good to mount directly on your desktop. However, this is all up to you. 
3) mount it. the form is generally ```
sudo mount -t auto /dev/sdXX /MOUNT/LOCATION
``` You would replace the last two pieces with your device and where you want to mount it.

---

### Post by bahsarie on 2008-12-16
thanks, can you help me understand what I might write for the mount section and I would like to mount to the desktop. 
The eee pc comes with two seperate hd one is truely a ssd and the is a sdhc

---

### Post by jbrown96 on 2008-12-16
Could you post the output of ```
sudo fdisk -l
```

---

### Post by Paqman on 2008-12-16
Your SDHC should mount automatically to the desktop when you put it in the slot.

If it doesn't, try this command and post any error messages:
```

sudo mount -a

```

---

### Post by bahsarie on 2008-12-16
> **jbrown96 said:**
> Could you post the output of ```
sudo fdisk -l
```

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x294a294a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris

Disk /dev/sdb: 32.2 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90599059

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3924    31519498+  83  Linux

---

### Post by bahsarie on 2008-12-16
> **Paqman said:**
> Your SDHC should mount automatically to the desktop when you put it in the slot.

If it doesn't, try this command and post any error messages:
```

sudo mount -a

```

there was no error message after i put that in. I know it should mount that is why I am asking about it. thank you.

---

### Post by jbrown96 on 2008-12-16
I didn't realize that the drive was removable. Does a 32GB entry appear in your "Places" menu? If so, you should just be able to click that and have it mounted. 

Otherwise, you can do the following procedure, but it is necessary each time you plug the drive in.
1) create a mount directory. This only needs to be done once. 
Just right click on the desktop and create a folder. Name it whatever you want, but I'm going to call it expansion, so if you name it something else just replace expansion with your name.

2) In a terminal, ```
sudo mount -t auto /dev/sdb1 ./Desktop/expansion
```
If you need to mount this way each time you mount (I doubt it), you can just press the up arrow in the terminal to scroll through your history, so it isn't necessary to memorize it. 
3) to remove the drive. If you want to remove the drive without shutting the computer down.
```
sudo umount ./Desktop/expansion
```

---

### Post by bahsarie on 2008-12-16
I tried that but this is the out put. I also did a dir command strraight from the terminal not sure if this is helpful. 

avi@avi-EEE:~$ sudo mount -t auto /dev/sdb1 ./Desktop/expansion
mount: mount point ./Desktop/expansion does not exist
avi@avi-EEE:~$ dir
array-apt-key.asc  Documents  Music	Public	Templates
Desktop		   LimeWire   Pictures	r.odt	Videos

---

### Post by bahsarie on 2008-12-16
got it! thanks

---

### Post by jbrown96 on 2008-12-16
to make a directory in Linux, its mkdir

Were you able to find it in "places" because all* parititions should be shown in there (obviously not the default-mounted paritions like /, /home, etc.?

---

