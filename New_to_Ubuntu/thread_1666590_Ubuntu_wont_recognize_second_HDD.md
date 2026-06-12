---
title: "Ubuntu wont recognize second HDD"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by kevinwmiller on 2011-01-13
I installed Ubuntu 9.10 on an older computer.  I can't access the second HDD.  I was wondering if there was some way for me to access it?  Ubuntu is the only operating system on the computer.  The Second HDD has several files of music and pictures on it.  

Thanks

---

### Post by garvinrick4 on 2011-01-13
You can find which sdx number it is by in terminal:
```
sudo fdisk -l
``` (lower case L)

If it is most likely sdb then:
```
sudo mkdir /media/data
``````
sudo mount /dev/sdb1 /media/data
```To Unmount use code below:
```
sudo umount /media/data
``` (not a typo)

# If you will open configuration editor and go to Apps to Nautilus
to Preferences and make sure the auto_mount and or auto_open
are checked as in screenshot: So as to auto mount media. Just incase they
are not in use. Is for USB and such.

---

### Post by click4851 on 2011-01-13
you don't say whether the 2nd harddrive is formatted or not....I was thinking gparted might list it, its in the repos....

---

### Post by kevinwmiller on 2011-01-13
When I entered the code from the first responder, I got this:

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13721371

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4703    37776816   83  Linux
/dev/sdb2            4704        4865     1301265    5  Extended
/dev/sdb5            4704        4865     1301233+  82  Linux swap / Solaris

My second HDD has 80GB, this only one shown has 40.0GB.  So it looks like it is only showing the one HDD.

---

### Post by kevinwmiller on 2011-01-13
> **click4851 said:**
> you don't say whether the 2nd harddrive is formatted or not....I was thinking gparted might list it, its in the repos....


The Second HDD was used when this machine was a Windows XP machine.  I know it has music and pictures on it.  I haven't touched it since I switched the system over to Ubuntu 9.10 ( XP went wonky on the computer for whatever reason and wouldn't boot)

---

### Post by kevinwmiller on 2011-01-13
The HDD shows up in Disk Utility as /dev/sda  

It shows it at 80GB, shows it as unrecognized.

It also says that the disk has a few bad sectors.

It also says it is not partitioned.  I wanted to know what kind of news that means for the data that was on it?  Is all of that data gone?  Will it be gone when I try to partition it?

---

### Post by garvinrick4 on 2011-01-14
#So /dev/sda is the original drive that had XP loaded on it and you want to get your
personal data off of it. 
#The drive is in an unbootable condition but had an operating system.
#You will need your XP recovery disk to attempt to repair or use some other recovery tool
that recovers Windows files. 
#Linux reads NTFS partitions so if it could it would read yours, assume now you have tried to fix and or repair it before this Post. 
#If XP was on it is partitioned just not in readable state.
#If you format it your data will be gone.

---

### Post by kevinwmiller on 2011-01-14
I didn't have an operating system on that particular drive, it was a secondary when I had XP.  The computer didn't come with an XP disk, that is why I went with Linux.  Hmm.  I don't really know where to go from here.  A lot of good stuff on that drive.

---

### Post by garvinrick4 on 2011-01-14
So it is basically a backup drive. Had to be formatted to hold your music and other data.
You did try:
```
sudo mkdir /media/data
``````
sudo mount /dev/sda1 /media/data
```Just to make sure it will not mount. Most likely not but never know until tried.
## Other than that this will bump it up to see if another user has a way to get data
off of that drive. 
## I do know that like over 20 years ago I use to give drives to companies that were in
business to retrieve data off of dead drives. Must be a lot of ways to do it by now. 
#Someone in the know might chime in here and help you out.

---

### Post by click4851 on 2011-01-14
probably redundant.... but make sure you have all the ntfs tools so linux can read those( if they are indeed readable)partitions/data. I think there are some ntfs tools/libraries in the repos that should be loaded. That might make the partition / data readable.

---

