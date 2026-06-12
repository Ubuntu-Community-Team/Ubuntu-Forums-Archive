---
title: "I seem to be missing about half a terabyte..."
date: 2009-05-17
forum: New to Ubuntu
---

### Post by chemburn on 2009-05-17
so i built a file server a few weeks ago, today, it told me that it coldn't back up my laptop using scp because it had run out of room. i hve spent the entire morning trying to figure ut where the 460Gs of data it swears is on there since there are only to directories being used...and the grand total of all the data in there is about 60Gs. Passes fsck, and the mdadm shows the raid working fine, and all the sizes are reading correctly. This is a Raid1 partition btw. Now my first problem is ls. As far as I am aware "ls -ash" should show me the size of the files in the directory. Why is it saying everything is 4k or 16k? like, everything, even a directory that houses 20 gigs of music?  And is there any way to get du to list contents of a partition in decending order based off size?  

The build on the server is running 8.10 server 64bit, drives are as follows: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e2fb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496   fd  Linux raid autodetect
/dev/sda2            3648        4133     3903795   fd  Linux raid autodetect
/dev/sda3           60814      121601   488279610   fd  Linux raid autodetect
/dev/sda4            4134       60813   455282100   fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000eb6ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3647    29294496   fd  Linux raid autodetect
/dev/sdb2            3648        4133     3903795   fd  Linux raid autodetect
/dev/sdb3           60814      121601   488279610   fd  Linux raid autodetect
/dev/sdb4            4134       60813   455282100   fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008431d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect

/sd*4 on all three disks is a Raid5 set up, the other half of the two 1Tb drives is pretty much: boot, swap, and a big home directory (the 466 gigs I am fighting with) that is all Raid 1. Having started all this, I am aware this is not how I should have built it, its a bit sloppy and this was a learning experience mostly. Still, it was working fine until it magically ran out of space during my back up of 135 gigs. (My /home on my laptop). 

I am aware this is a lot of crap to dump in here, if there is a more preferred policy for that, by all means I will fix it, just wanted to maybe get someone with a little more knowledges opinion on this. i have already checked /var/log/ btw, nothing bigger then a Meg. Would be alot easier if I could figure out a way to check the data on te partitions size, but just du -h is a mess, and noone of it seems to add up to the total I am showing?

---

### Post by Aaardwark on 2009-05-17
Use:
```
df -h
```

Means disc space in human readable. If you would like it displayed with nice simple graphics, I recommend using gparted.

---

### Post by chemburn on 2009-05-17
yes, but it will simply give the percentage used, that is where my problem is. it says I am using up over 400 gigs of space. But there isn't enough data that I have placed on there to account for it being full.

joshua@frankenchrist:/home$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0               28G  1.1G   26G   4% /
tmpfs                 500M     0  500M   0% /lib/init/rw
varrun                500M  264K  500M   1% /var/run
varlock               500M     0  500M   0% /var/lock
udev                  500M  2.7M  498M   1% /dev
tmpfs                 500M     0  500M   0% /dev/shm
/dev/md3              932G  397G  535G  43% /Store1
/dev/md2              428G  403G  3.6G 100% /home


this is what it currently reads, I have been moving files off to the larger drive the last few minutes in kind of a trial and error manner to find where the majority of the space is being lost. Hence it only reads 3.6

---

### Post by Aaardwark on 2009-05-17
So the question is where the 400 GB on your /home disappeared to?
> /dev/md2 428G 403G 3.6G 100% /home
...or more specifically how to find out file size of folders or big files in text mode on said partition?

---

### Post by bumanie on 2009-05-17
I have found 9.04 to give accurate storage measurements, but 8.10 was way off on my computer. If using 8.10, that may be the problem. If you are using 9.04, I'm not sure what the problem could be.

---

### Post by Cheesemill on 2009-05-17
Change directory to / then do a
```
sudo du -h --max-depth=1
```
This will give you usage by directory, you can then cd into that directory and repeat until you've narrowed it down.

Cheesemill

---

### Post by chemburn on 2009-05-17
Aaardwark: yes, the trying to find it. sorry. was worried that didn't come out right. i am trying to find what is actually taking up that much space. Unfortunately this isn't much of a problem on a GUI, but the server is command line, ls doesn't seem to be helping, since it says everything is 4.0K if i am reading it right, and was looking for a way to reference the size of each file to figure out the offender, since i can't really account for that much space being used.

Cheesemill: ty, giving it a shot now

---

### Post by chemburn on 2009-05-17
thank you guys, found the culprit, though i am not sure how it happened, the back up I ran seemed to be a lot bigger then the actual file originally was and it couldn't give me number on part of it, i am guess a corrupted file?

---

