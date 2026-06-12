---
title: "idiots guide to installing /home on 2nd HD"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by myotis on 2011-01-23
I want to install Xubuntu on my Asus eeepc po1 which has a 4gb SSD /dev/sda and a 32gb HD /dev/sdb.


For obvious reasons I would like xubuntu on the 4gb SSD, but my home directory on the 32gb SSD, and using all 32gb.

I know this can be done at the install stage, but the instructions I have found in the past, seem to assume a level of understanding some what higher than I have. Iget confused at what I actually have to enter to set up the home directory, and just end up with everything in one partition.

Are there some step by step instructions somewhere that would help.

And as a secondary question, I currently have Ubuntu on the Asus, but entirely on the 32gb SSD as it is too big to install onto the 4gb SSD. 

I am assuming since Xubuntu only needs 2gb to install that my strategy for installing makes sense,and that then 4gb will be fine.

Many thanks,

Graham

---

### Post by [Snc] on 2011-01-23
> **myotis said:**
> I want to install Xubuntu on my Asus eeepc po1 which has a 4gb SSD /dev/sda and a 32gb HD /dev/sdb.


For obvious reasons I would like xubuntu on the 4gb SSD, but my home directory on the 32gb SSD, and using all 32gb.

I know this can be done at the install stage, but the instructions I have found in the past, seem to assume a level of understanding some what higher than I have. Iget confused at what I actually have to enter to set up the home directory, and just end up with everything in one partition.

Are there some step by step instructions somewhere that would help.

And as a secondary question, I currently have Ubuntu on the Asus, but entirely on the 32gb SSD as it is too big to install onto the 4gb SSD. 

I am assuming since Xubuntu only needs 2gb to install that my strategy for installing makes sense,and that then 4gb will be fine.

Many thanks,

Graham

There is a nice step by step instruction on just that here: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Enjoy!

---

### Post by myotis on 2011-01-23
> **'[Snc] said:**
> There is a nice step by step instruction on just that here: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Thanks, but this is about "moving" the home directory :-(

Graham

---

### Post by [Snc] on 2011-01-23
> **myotis said:**
> Thanks, but this is about "moving" the home directory :-(

Graham

Well, I don't know about any way to do it directly during the installation procedure. :}

Just after you install your OS, your Home folder is basicly an almost empty folder, that's the time to move it and remount it to another drive, after that it is always located on the other hard disk.

---

### Post by ubudog on 2011-01-23
This may help you...

[http://ubuntuforums.org/showthread.php?t=1383179](http://ubuntuforums.org/showthread.php?t=1383179)

Hope it does.

---

### Post by oldos2er on 2011-01-23
You need to choose manual installation. [http://sazeit.com/articles/manually-select-partitions-ubuntu](http://sazeit.com/articles/manually-select-partitions-ubuntu)

---

### Post by myotis on 2011-01-23
> **'[Snc] said:**
> Well, I don't know about any way to do it directly during the installation procedure. :}

Just after you install your OS, your Home folder is basicly an almost empty folder, that's the time to move it and remount it to another drive, after that it is always located on the other hard disk.

I see, I had just assumed that as you could put home into a separate partition during install, you could also put it into a separate HD.

Thanks,

Graham

---

### Post by ubudog on 2011-01-23
> **myotis said:**
> I see, I had just assumed that as you could put home into a separate partition during install, you could also put it into a separate HD.

Thanks,

Graham

I guess anything's possible right?  

You could theoretically do it by moving your home directory to a seperate HD, then changing the mount point of the home folder so that Ubuntu knows your home dir is actually on the seperate hd.  Then, you could create a script that mounts and opens it, put it on your desktop, and voila.  That may work.

---

### Post by myotis on 2011-01-23
Mmmmm, I was rather hoping this would be easier than its turning out to be.

Thanks everyone.

Graham

---

### Post by ubudog on 2011-01-23
> **myotis said:**
> Mmmmm, I was rather hoping this would be easier than its turning out to be.

Thanks everyone.

Graham

I don't think it would be that hard to accomplish...

I will try to put together a guide.

---

### Post by cariboo on 2011-01-23
Setting up the partitions is fairly easy, once you get to the partitioning section of the install process, choose the manual partition option. A window will open up showing you you the hardrives on your system. To set the root partition, right click the 4Gb device and select change., another window will popup asking what file system you want to use, select ext4, then the mount point, where you would select /, just leave the size as it is, and amke sure it is the primary partition, and it is at the start of the drive. 

Once you have made the changes, Select the 32Gb device, and select delete from the right-click menu, this will create 32Gb of unallocated space. Next right-click and select new, Inthe window that pops up set the size to 30Gb, as you probably want to sleep/hibernate your system, Select ext4 for the file system and /home for the mount point.

Finally right-click the last bit of unallocated space and click new, then from the file system type menu, select swap.

Click next, and you should be on your way.

---

### Post by myotis on 2011-01-23
> **ubudog said:**
> I don't think it would be that hard to accomplish...

I will try to put together a guide.

Thanks, that would be really useful, as it would be good to have the OS on the much faster 4gb SSD.

Graham

---

### Post by philinux on 2011-01-23
> **myotis said:**
> Thanks, that would be really useful, as it would be good to have the OS on the much faster 4gb SSD.

Graham

Post #11 has the info you need.

---

### Post by myotis on 2011-01-23
> **cariboo907 said:**
> Setting up the partitions is fairly easy, once you get to the partitioning section of the install process, choose the manual partition option. A window will open up showing you you the hardrives on your system. To set the root partition, right click the 4Gb device and select change., another window will popup asking what file system you want to use, select ext4, then the mount point, where you would select /, just leave the size as it is, and amke sure it is the primary partition, and it is at the start of the drive. 

Once you have made the changes, Select the 32Gb device, and select delete from the right-click menu, this will create 32Gb of unallocated space. Next right-click and select new, Inthe window that pops up set the size to 30Gb, as you probably want to sleep/hibernate your system, Select ext4 for the file system and /home for the mount point.

Finally right-click the last bit of unallocated space and click new, then from the file system type menu, select swap.

Click next, and you should be on your way.

Thanks, I will give this a go. Probably not till tomorrow now.

Graham

---

### Post by myotis on 2011-01-24
Thanks for everyones help, the instructions from cariboo907, helped me through, and xubuntu now clean installed and home directory on 2nd hard drive.

Firefox seems a lot snappier on the faster SSD, so so far it seems a worthwhile exercise, just need to get used to the new interface.

Graham

---

