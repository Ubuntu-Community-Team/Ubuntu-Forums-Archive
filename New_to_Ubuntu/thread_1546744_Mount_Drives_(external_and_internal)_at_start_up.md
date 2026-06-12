---
title: "Mount Drives (external and internal) at start up"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by TimEnid on 2010-08-05
Can someone tell me how to do this? I want all my drives to mount as soon i log into ubuntu. thanks.

---

### Post by darolu on 2010-08-05
It's quite simple, you just have to edit your fstab file with your drives info.

The first step is to create [mount points]("http://en.wikipedia.org/wiki/Mount_%28computing%29") for your drives. This is the easiest part, and it's used so when you mount your drives they don't mount to weird locations like "WD512GB982-3wTF" or whatever; all you have to do is create directories for each of your drives, for example, lets say I have a Media hard drive with all my music and videos, open a terminal and run:
```
sudo mkdir /media/MyMedia
```
And your mount point is ready, I recommend creating them within "/media" so they are listed in your Nautilus list (and under your Places menu).

After you created all your mount points, you will have to add your [file systems]("http://en.wikipedia.org/wiki/File_system") to your fstab file, but first you will need to find out where your file systems (your drives) are located at, in your terminal run:
```
sudo fdisk -l
```
That's a lowercase L btw; write down where your drives are, the part you need is one that looks like "/dev/sdb1" etc. In my example:
```
**/dev/sdb1**               1       24321   195358401    7  HPFS/NTFS
```
Once you have your mount points ready and you know your file systems location in your terminal (or with Alt+F2) run:
```
gksu gedit /etc/fstab
```
Then at the end of the file add a line for each of your drives using its corresponding data, for my <MyMedia> example:
```
#MyMedia on /dev/sdb1:
/dev/sdb1	/media/MyMedia	ntfs	defaults,user,exec,rw	0	0

#MyMedia2 on /dev/sdc1
UUID=49B723546D64AA24	/media/MyMedia2	ntfs	defaults,user,exec,rw	0	0
```
After that, you just have to save the file and that's it.

You can learn about how fstab works and all of its options at the links below this; in my example I added 2 NTFS hard drives with enough permissions to write, read, edit and execute files from them, the <options> entries are the same options you find in mount (the command) manuals.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

As you can see, my second entry does not use "/dev/sdc1" for the <file system> option; it uses a unique ID code, a [UUID]("http://en.wikipedia.org/wiki/Universally_unique_identifier") to be more precise; it is widely recommended that you use a UUID instead the "raw" route to your drive/partition, to find out what's the UUID code for your drives run this on your terminal:
```
sudo blkid
```

Good luck.

---

### Post by TimEnid on 2010-08-06
thanks, im gonna need it.

---

### Post by fterh on 2010-08-07
Regarding fstab: If for options I state noauto, which means I'd have to mount the partition manually right? Then in that case I wouldn't even need to enter an entry in my fstab file if I want noauto? Am I right to say this?

---

