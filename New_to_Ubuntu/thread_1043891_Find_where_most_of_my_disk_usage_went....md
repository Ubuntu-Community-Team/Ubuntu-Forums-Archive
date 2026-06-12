---
title: "Find where most of my disk usage went..."
date: 2009-01-18
forum: New to Ubuntu
---

### Post by cartisdm on 2009-01-18
I'm trying to get a mythbuntu setup working but in the process I was recording some TV and I used up all my disk usage (or so I thought).

My desktop crashed and would no longer load any GUI and kept saying "Out of Disk Space."  I am on a liveCD now so I can clear up some space on my two harddrives but that didn't really free up much space.  What command can I enter that tells me where most of disk usage is taken up (deleted all my recordings didn't do the trick but I'm assuming there are some other recordings elsewhere)

---

### Post by diablo75 on 2009-01-18
Check to see if you have Applications>Accessories>Disk Usage Analyzer available.

---

### Post by mjheagle8 on 2009-01-18
you could go under nautilus and sort by the largest size. look at how big folders are and you'll find where it all went.

---

### Post by theozzlives on 2009-01-18
Do you have any .ISOs, I back mine up to DVD when I get 4.2 GB.

---

### Post by cartisdm on 2009-01-19
I don't have Nautilus, there's Thunder File Manager.  I was able to remove enough stuff to be able to boot into Mythbuntu.  I have a 120gb harddrive that I just formated to Ext3 using Gparted (I had cleared everything off my 40gb and 120gb leaving it all unallocated then just let Mythbuntu create the partition needed on the 40gb - hence why I ran out of space).

I just booted back into Mythbuntu but I don't see my second (120gb) harddrive I just formatted.  Where is it?

---

### Post by mjheagle8 on 2009-01-19
did you look in /media ? what did you set as the mount point for the drive?

---

### Post by diablo75 on 2009-01-19
> **cartisdm said:**
> I just booted back into Mythbuntu but I don't see my second (120gb) harddrive I just formatted.  Where is it?

[http://www.ubuntux.org/edit-fstab-to-mount-partition-at-startup](http://www.ubuntux.org/edit-fstab-to-mount-partition-at-startup)

---

### Post by yknivag on 2009-01-19
```
df
``` will tell you the usage on each volume.  Then change directory (cd) to the mount point of that volume and run
```
du -k --max-depth=1
``` which will tell you which directory is taking up the most space (the numbers represent the number of blocks used).

You can then either increase --max-depth to show further sub-directories (but the output can get very large) or you can cd to the largest directory and repeat the command.  This should point you to where the space is being used.

---

### Post by kaibob on 2009-01-19
Enter the following in a terminal window--it will show any files over 10mb in size:

```
sudo find / -xdev -size +10M -type f -exec ls -gohX {} \;
```

---

### Post by cartisdm on 2009-01-19
I haven't gotten to mounting the second Harddrive yet (although I checked and it's not in /media).

How come when I installed Mythbuntu on my 40gb harddrive it created two partitions?

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             10175300   2298700   7359712  24% /
tmpfs                   776624         0    776624   0% /lib/init/rw
varrun                  776624       368    776256   1% /var/run
varlock                 776624         0    776624   0% /var/lock
udev                    776624      2852    773772   1% /dev
tmpfs                   776624         0    776624   0% /dev/shm
lrm                     776624      2000    774624   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda6             27843076  26875552    967524  97% /var/lib

```

I just checked back in GParted and my second harddrive is listed as "hdb" and it says it should be in /dev/.  I don't see it still when I boot but I don't have a lot of experience with mounting drives that don't show up

---

### Post by mjheagle8 on 2009-01-19
there are two partitions: one for /, one for /var/lib

---

### Post by niteshifter on 2009-01-19
Hi,

Never mind the somewhat odd partitioning for the moment. This:
> **/dev/sda6             27843076  26875552    967524  97% /var/lib**
just doesn't look right. That's 26.8GB in /var/lib! Methinks that might be where some of your recordings are stored.

---

### Post by cartisdm on 2009-01-19
Must have been the way it was setup, I did a normal liveCD install and had it use Guided: Use entire disk.

I still don't know how to access my second harddrive.  I'd like to use that one for recording all my media.


> just doesn't look right. That's 26.8GB in /var/lib! Methinks that might be where some of your recordings are stored.

That's one large file that I copied to the Videos folder (seasons 1-10 of Friends:))

---

