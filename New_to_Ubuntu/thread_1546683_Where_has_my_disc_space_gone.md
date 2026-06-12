---
title: "Where has my disc space gone?"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by GaryTheCat on 2010-08-05
Hello

I must be doing something stupid or have misunderstood something....

I have 2 HDDs in my laptop which is dual boot vista / lucid, one is 120 GB (2 partitions 20 GB and 100 GB) which I have set aside to run both OS's in the 100 GB partition.  The other is 500 GB in 2 partitions 1 x 100 GB, 1 x 400 GB which i set aside for data (media files, music library etc.) and made these partitions in vista before installing lucid.

Now the 20 GB and the 100 GB partitions are the size they should be in lucid.  The 400 GB partition is now 238.8 GB and the 100 GB partition is 48.8 GB.

My questions are:

What's going on here?
Is it something to do with vista and lucid using the same disc space?
How do I fix it?

TIA 

Gary

---

### Post by pharcycle on 2010-08-05
How have you configured the drive for both os's? Did you click the option to install ubuntu side by side with windows on that drive when you first installed? if so who then knows what it did on your behalf! Run gparted from somewhere in the system menu or 'sudo gparted' from the console and explore the drive layout. It may have split some of your drives for you to make Linux partitions (ext2/3/4, swap etc).

P.S. Are the 400gb and 100gb partitions onthe 500gb hdd both ntfs?

---

### Post by GaryTheCat on 2010-08-05
I did do the side by side install.

> **pharcycle said:**
> 

P.S. Are the 400gb and 100gb partitions onthe 500gb hdd both ntfs?

they are.

they're nowhere near full but it's bugging me where the GBs have gone

---

### Post by pharcycle on 2010-08-05
Does ubuntu and windows report the same amount of free space?

---

### Post by GaryTheCat on 2010-08-05
I'm pretty sure they do - I'll check in the morning

---

### Post by pharcycle on 2010-08-05
I need to go to sleep now and I'm still a newbie myself even after 3 years with linux so hopefully someone more qualified can help soon! Gparted should give you a clear picture of your fliesystem layout and help you track down the problem Note the differences that windows reports compared with ubuntu- windows has a filesystem tool, used to right click my computer and select manage but that was under xp.

Good luck

---

### Post by GaryTheCat on 2010-08-05
Here's what ubuntu's disk utility says

---

### Post by GaryTheCat on 2010-08-06
Can anyone explain the screenshot to me? 

Ta

G

---

### Post by sikander3786 on 2010-08-06
Hi.

The screenshot is telling that you have a 500GB hard disk split into 256 + 191 +52 = 499GB. I couldn't really understand the problem.

---

### Post by Elfy on 2010-08-06
Try running this from a terminal and posting it here.

```
df -h
```

Have a look here as well [http://ubuntuforums.org/showpost.php?p=5649417&postcount=1](http://ubuntuforums.org/showpost.php?p=5649417&postcount=1)

---

### Post by GaryTheCat on 2010-08-06
Here it is...

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5             170G   40G  122G  25% /
none                 1002M  340K 1002M   1% /dev
none                 1006M  436K 1006M   1% /dev/shm
none                 1006M  280K 1006M   1% /var/run
none                 1006M     0 1006M   0% /var/lock
none                 1006M     0 1006M   0% /lib/init/rw
/dev/sdb1             239G   97G  143G  41% /media/Data
/dev/sdb2              49G   88M   49G   1% /media/Ubuntu
/dev/sda3             100G   38G   63G  38% /media/OS

(Sorry about the double posting)

---

### Post by Elfy on 2010-08-06
If you have not put things in there - then check through some of the things in the link I gave.

---

### Post by GaryTheCat on 2010-08-06
Have read through the stuff at the end of the link and am still stumped.

Going to take a break from it and try to get my head round it later

think it's a case of PICNIC

---

### Post by slooksterpsv on 2010-08-06
A 500 GB Drive = 465.66 actual GB, due to the fact that 1KB = 1024 Bytes, which they round down, so 1 KB = 1000.

/dev/sdb1 239G 97G 143G 41% /media/Data = 256GB
/dev/sdb2 49G 88M 49G 1% /media/Ubuntu = 52GB 
/dev/sda3 100G 38G 63G 38% /media/OS = 107GB 
Plus Swap 5.77GB = 6.2
==================================

SDB = 393.7GB = 422.73GB

So the issue is with the 185GB ext4 partition. Somewhere its not reading it as 185GB, but as 107GB. 185GB = 172GB so:
239+49+100+5.7+72= 465.7GB which = 500GB by rounding to 1000 for each byte.

Sounds like the 185GB theoretical ext4 partition is missing 72GB actual, may need to run an fsck -fy on it.

---

### Post by GaryTheCat on 2010-08-10
Could it be that this is something being used by vista?

I used wubi to install lucid on the 'OS' drive and intended the 'Data' partition to be used by Lucid and Vista - have I done something silly?

---

### Post by mapes12 on 2010-08-10
Your post indicates you have both OS's installed on sda but on sdb your screenshot shows a 52GB Ubu partition formatted as NTFS. Odd?

Your sdb partitions add up to 499GB so I can't see that you have lost any space.

---

### Post by GaryTheCat on 2010-08-10
I just named the partition ubuntu as I was planning on putting the OS in there but I had trouble doing that with wubi.

It's that bit of drive I can't get at from Lucid that's causing me to scratch my head 

G

---

