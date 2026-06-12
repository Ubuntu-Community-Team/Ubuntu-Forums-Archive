---
title: "Total Linux newb, partition size"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by mlthmp on 2009-08-07
Hey guys. I have a question.

I installed Ubuntu yesterday from a LiveCD I burned the night before. I kinda messed up and only made my partition 2.5gb. Is there any (fairly easy) way to increase it any? Currently I only have 21.0MB free =( I am duel booting with XP and am using a single 40GB HD.

I've been able to stumble my way around and get almost everything else working (Belkin Wireless USB adapter, video / sound cards, etc) but I am stumped on this one =(

Any help would be greatly appreciated. Also, I will provide any information requested (terminal info, etc)

---

### Post by drs305 on 2009-08-08
mlthmp, welcome to Ubuntu.

You aren't the first to end up with a 2.5GB partition. In fact, enough have preceeded you that I wrote a couple of guides on how to recover from it.

Your options are to expand the system partition by taking some space from Windows or another partition, or to reinstall. The guide discusses how to do the latter and what caused the error and how to correct the former.

Here is the link:
[2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")

Fixing It:
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by 123456789123456789123456 on 2009-08-08
There is a partition tool that can work

it is very powerful, it may be in the Universal Ultimate boot tool disk, you can find that online.

Can't remember what the partition manager is called off hand.  It will allow you to literally shrink the size of the windows partition, take back any partitons that are not used, extra ones that have nothing installed on it, and along with any free space, and reconfigure the drive, to allow you to resize the 2.5gb partition to a greator size.

However this is not recomended unless you know everything you are doing.  It is simple to work around with the program, but the process of shrinking a drive, and manipulating the drive partitions in the way mentioned, can cause data loss in wither the Ubuntu partiton or the windows partition.

The best way around this however is to litterly start over.  First backup the data you have on both partions.

second, identify which OS you wish to have as the main OS, Windows or Ubuntu.

Third, if Windows is chosen, then start up with the Windows cd, remove all partitions using the cd.
Note the total disk space.
Remember that ubuntu will create a swap partiton.
you may won't to use half the disk for widnows and the other half for Ubuntu.
Easy to do so through the deletion of partitons.
Create a new partiton, though the windows cd.  XP and Vista allow you choose the size of the partiton.  Don't except the size it suggests, type in a new amount, which is half the disk.  You need to calculate this.
after you set windows up.
You can then go to the Ubuntu live cd, have it use the unpartitioned space to install on.
It will take the space not being used by windows, and create a Ubuntu partiton, and a swap file, the swap partiton will not or should not automatically be more than 10gb in size.
This is the best way I know of to set up the partitions.  IF you don't understand this, you can ask others, I am sure someone has done this method before.

---

### Post by mlthmp on 2009-08-08
Hey guys, thanks for the QUICK responses!

As I mentioned earlier I was duel booting with Windows XP, so I decided to log into Windows for awhile (while I was waiting on some responses here) Logged in, and got a couple Win errors (same things I had been getting for awhile now) Spent a little time trying to "fix" XP and just finally said to hell with it.

So, long story short I reinstalled Ubuntu, and used the entire disk this time. So now I have 30.9GB free. I just got tired of messing with XP and its errors (which is the original reason I wanted to try Ubuntu in the firts place.

Im sure I'll be looking for help along the way, but im just going to stick with Linux, and use my backup lappy (Vista) for anything else I need Windows for.

Thanks guys!

---

### Post by magmon on 2009-08-08
Welcome to the ubuntu family :).

---

### Post by mlthmp on 2009-08-08
> **magmon said:**
> Welcome to the ubuntu family :).

Thank you very much =)  I just hope I can figure enough of this out on my own to keep from bugging everyone here all the time, lol!

I do have one (unrelated) question. I dont want to start a new thread for something like this lol.

I can expect "decent" performance from my system with Ubuntu, right?

P4 3.0ghz with 3GB memory. Nothing too fancy, couple of years old.. but should be stout enough to run Linux "safely" over an extended period of time.. no?

---

### Post by TheSpartin on 2009-08-08
lol, i did the exact same thing as u as far as partition size and then i messed up the whole partition and got the grub 22 error for a couple of days, but yea, sound like u should be able to run it fine :)

---

### Post by JedV on 2009-08-08
> **mlthmp said:**
> Thank you very much =)  I just hope I can figure enough of this out on my own to keep from bugging everyone here all the time, lol!

I do have one (unrelated) question. I dont want to start a new thread for something like this lol.

I can expect "decent" performance from my system with Ubuntu, right?

P4 3.0ghz with 3GB memory. Nothing too fancy, couple of years old.. but should be stout enough to run Linux "safely" over an extended period of time.. no?

Absolutely.  I have been running Ubuntu since 6.06 on the same machine, upgrading each distribution.  My system is very similar to yours, and works great.

Have fun learning.  These forums are great.

---

