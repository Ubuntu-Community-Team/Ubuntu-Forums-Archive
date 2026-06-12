---
title: "space required for 11.04"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by drow on 2011-06-09
when I installed 11.04, I thought I was installing it on a 160 G HD. After installation and installing VLC and other files from Medibuntu, I had 99 G left. This doesn't sound right. 
Does the base 11.04 take up around 70 G?
And where do I find this information on the computer?
 
Thanks

---

### Post by TeoBigusGeekus on 2011-06-09
Open a terminal and give
```
df -h
```
It will list all your partitions, their sizes as well as their mount points.
Post us the output if you want to, to give it a look.

---

### Post by aeronutt on 2011-06-09
> **drow said:**
> when I installed 11.04, I thought I was installing it on a 160 G HD. After installation and installing VLC and other files from Medibuntu, I had 99 G left. This doesn't sound right. 
Does the base 11.04 take up around 70 G?
And where do I find this information on the computer?
 
Thanks

No, it takes nowhere near 70G. Not quite sure exactly how much, but IIRC around 4-5G.

Depends on how you installed it, the disk partitioner may have simply set the partition size to 70G based on overall size of the HD, and the other things you have on there (eg a Windows partition.)

---

### Post by silex89 on 2011-06-09
That's odd... The clean installation should take 2 to 3 GB....did you used the regular CD/DVD installation or an alternate version?

---

### Post by BKbroila on 2011-06-09
I think the root and swaptakes up about 10~15  GB. But you may have partitioned to have /home to take up 60 or however much that would add up to 70 GB.

---

### Post by drow on 2011-06-09
I remember during installtion that there were 2 partitions. I din't I needed either so I tried to delete them both. If I remember correctly, one would not delete. I probably have a partition I don't need then it sounds like.

---

### Post by drow on 2011-06-09
silex89, I used the CD I created after downloading 11.04 from Ubuntu's homepage.

and TeoBigusGeekus, here's results from the terminal:
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             109G  3.3G  100G   4% /
none                  995M  648K  995M   1% /dev
none                 1002M  196K 1002M   1% /dev/shm
none                 1002M   92K 1002M   1% /var/run
none                 1002M     0 1002M   0% /var/lock


I don't understand what it means, but the 109G size and 100G available makes no sense to me.

---

### Post by TeoBigusGeekus on 2011-06-09
Can you also post the output of
```
sudo fdisk -l
```
(-L) ?

---

### Post by drow on 2011-06-09
sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000022c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14334   115132416   83  Linux
/dev/sda2           14334       14594     2085889    5  Extended
/dev/sda5           14334       14594     2085888   82  Linux swap / Solaris

3 devices? What do those last 3 lines refer to?

---

### Post by TeoBigusGeekus on 2011-06-09
Right...
Your hd is 120gb.
Your first partition (sda1), is 115132416 bytes, or ~109Gb.
You have an extended partition wherein lies your swap partition: 2085888 bytes or ~2Gb.

The numbers won't sum up (109+2 != 120) because of the 1024 and 1000 bytes thing.

You have 3.3gb for root (/) and about 1gb for /dev, /dev/shm, /var/run and /var/lock. They all add up to ~7.3gb. If you take also under consideration some temp files your system uses, the 99gb you have left are not illogical.

---

### Post by drow on 2011-06-09
OK, thanks a lot for your help. I obviously didn't have a hard drive that was as big as I thought.

---

### Post by TeoBigusGeekus on 2011-06-09
You're welcome.

---

