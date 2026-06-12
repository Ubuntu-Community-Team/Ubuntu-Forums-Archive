---
title: "How do I figure out where the missing HD space went?"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by NotSoheavyD on 2011-02-20
So I'm a newbie and I was playing around with Ubuntu 9.04 and only bothered to upgrade with 9.10 this weekend. I noticed something odd with the file system though. When I boot into 10.10 with a live disk to check my file system it tells me that it has a capacity of 76.5GB. It also tells me that 52.1gb are used and 24.4 are free. What odd about that is that the dialog also tells me that there's a total of 20.5 GB in 176,844 items. I'm curious why if it says there's 20.5 GB in items that the final tally of disk usage is 52.1GB? Any ideas? I have no idea if this was true before the upgrade or not. (Not a big deal if it's an issue of upgrading. I can always wipe the file system and put on a fresh one from 10.10)

---

### Post by cariboo on 2011-02-20
What command are you using to check disk space? IF you are using the disk usage applet from the accessories menu, you may get a reading that is inaccurate due to a bug that was fixed in later versions. TO get a true reading of disk usage, open an Accessories->Application->Terminal and type:

```
df -h
```

the results will look something like this:

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  4.6G  4.2G  53% /
none                  997M  700K  996M   1% /dev
none                 1005M  1.4M 1003M   1% /dev/shm
none                 1005M  104K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
/dev/sda2             221G  118G   92G  57% /home
```

---

### Post by trooperchix on 2011-02-20
I am still missing 20 gig...

---

### Post by Hedgehog1 on 2011-02-20
> **NotSoheavyD said:**
> When I boot into 10.10 with a live disk to check my file system it tells me that it has a capacity of 76.5GB. It also tells me that 52.1gb are used and 24.4 are free. What odd about that is that the dialog also tells me that there's a total of 20.5 GB in 176,844 items. I'm curious why if it says there's 20.5 GB in items that the final tally of disk usage is 52.1GB? Any ideas? I have no idea if this was true before the upgrade or not. 

NotSoheavyD,

Perhaps a graphical display will work better for you to track down this curiosity. 

The next time you boot the 10.10 LiveCD, run gparted after selecting the 'Try' option (Menu System >> Administration >> GParted Partition Editor).

This tool will show you where an unallocated space (or more likely a lost partition of 20 gigs in your case) is.  Please remember that any changes you make in GParted are real.

If you find something really odd, then please follow instruction on the previous post: ```
 df -h 
``` and add the text that is output to your next post.

:KS

---

### Post by NotSoheavyD on 2011-02-20
Thanks for the info. I'll give it a check in a little bit. (It is cool that you can put the live disk on a thumb drive and boot off of it isn't it?)

---

### Post by Hedgehog1 on 2011-02-20
It is VERY cool.  Feels like cheating, actually.  I demoed Ubuntu at work off a thumb drive and that was as impressive to the group as Ubuntu itself.

You never know what is going to 'WOW' the crowd. :KS

---

### Post by NotSoheavyD on 2011-02-21
Lets see, when I do df -h I get

ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  1.6G   25M  1.6G   2% /
none                  1.6G  356K  1.6G   1% /dev
/dev/sdc              7.6G  710M  6.9G  10% /cdrom
/dev/loop0            661M  661M     0 100% /rofs
none                  1.6G  116K  1.6G   1% /dev/shm
tmpfs                 1.6G   16K  1.6G   1% /tmp
none                  1.6G   88K  1.6G   1% /var/run
none                  1.6G     0  1.6G   0% /var/lock
/dev/sdb5              77G   49G   25G  67% /media/eb9c310c-064f-49fb-b1a4-b564f642bbb9
/dev/sdb2             851G  415G  437G  49% /media/60BCF87BBCF84D52


Hmm, the partition is /dev/sdb5 for what it's worth. When I look at it in gparted I can see it as a single partition that's half used. (Hmm, I'm tempted to just wipe it and start with 10.10.)

---

### Post by Hedgehog1 on 2011-02-21
> **NotSoheavyD said:**
> 
/dev/sdb5              77G   49G   25G  67% /media/eb9c310c-064f-49fb-b1a4-b564f642bbb9
/dev/sdb2             851G  415G  437G  49% /media/60BCF87BBCF84D52
Hmm, the partition is /dev/sdb5 for what it's worth. When I look at it in gparted I can see it as a single partition that's half used. (Hmm, I'm tempted to just wipe it and start with 10.10.)

Well - at least the mystery of where the space went is solved. 

What to do about it - that one is up to you... :)

---

### Post by NotSoheavyD on 2011-02-21
> **Hedgehog1 said:**
> Well - at least the mystery of where the space went is solved. 
 
What to do about it - that one is up to you... :)
 
It is? Wait I'm confused. I have a partition that is about 77GB. That df -h told me that about 50GB is being and 25GB is free. But right clicking on the file system told me that but also told me that 20GB are being used in a bunch of items. Umm, so what is the other 30GB being used on? Does ubuntu do automatic backup or something like that. Again as I've said I'm pretty much a newbie when it comes to Linux/Ubuntu.

---

