---
title: "Automatically Mount Partitions Help"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-11-29
I have a quick question. I have a partitioned HDD, One of the partitions has all of my data on it and ubuntu is on another partition.  I would like to know how to have ubuntu automatically mount that partition when ubuntu boots up. What i would like to do is automatically start boxee when the computer boots up and have it read the files on my data partition without me having to manually mount it.  Thanks

---

### Post by Verbeck on 2010-11-29
from a terminal (applications>accessories>terminal), do the following;

first make the mount point
```
sudo mkdir /media/data
```then find the uuid and file system of the drive
```
sudo blkid -c /dev/null
```then add a new line to your fstab
```
gksu gedit /etc/fstab
```the new line should be like
UUID=**somenumbers** /media/data **filesystem** defaults 0 0

where the numbers=the uuid of your drive and filesyatem=the file system of the drive (ntfs/ext3/ext4/vfat etc..)

example:
UUID=0C2A39615EAFB871 /media/Extras ntfs  0 0

---

### Post by hunter99507 on 2010-11-29
So now i need help. I created a folder and now i cant delete it. It says i have to have root access. How do i delete a folder? Can you list how in for terminal, and it there a way to use the GUI to make me have root access all the time? Thanks

---

### Post by hunter99507 on 2010-11-29
The Folder I need to delete is in file systems, media folder, but i dont know how to delete the folder or even get to that media folder in terminal

---

### Post by Elfy on 2010-11-29
```
gksudo nautilus 
```

will open a root terminal

```
gksudo nautilus /media 
```

will open it in /media

No-one is going to show you how to gain root access with a gui all the time.

You can remove folders with rm -r - but you need to get the syntax exactly right or it could all go horribly wrong.

It'll be similar to sudo rm -r /media/nameoffolder

Read the man page for rm

---

### Post by romankarlfranz on 2011-08-04
Hi!

I have Ubuntu 11.04 and have my HD in 2 partitions. On one of them I run Ubuntu and on the other I have my files. Both are ext4.
When I start Ubuntu the partition /media/Store (where I have my files) doesn't show up as mounted. When I click it in Nautilus it immediately mounts. But that's too late for me because on startup applications would need access to this partition already.

I did what you said in Terminal, added the line to this file but then I got error message at boot "can't mount partition" Something with Ctrl-D... I immediately deleted this line again and now I am back where I started from.

Did I do something wrong?

Thanks!

---

### Post by romankarlfranz on 2011-08-04
got it! this helped me out: [http://ubuntuforums.org/showthread.php?t=1299667](http://ubuntuforums.org/showthread.php?t=1299667)

---

