---
title: "Repartition help!"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Zombie_Gaz on 2009-01-28
When I installed Ubuntu I separated my three hard drives into three partitions for the system... hd1 for boot, hd2 for / and swap, and hd3 for /home.

However, the hard drive I put on boot is about 15 gigs. Question #1 is do I really need 15 gigs for /boot? With that in mind, my /home is also 15 gigs and I am already a decent amount into it.

Is there a way I can take some space from the boot partition (like as much as possible) and put it on /home/me. Then I would have part of hd1 for boot, part of hd1 for /home/me, hd2 for / and swap, and hd3 for /home (excluding /home/me).

Thanks!

---

### Post by echo8413 on 2009-01-28
The only reason you need to partition is for multi boot. Like I'm running both Windows Vista and Ubuntu 8.04. Windows is my primary partition and that is 85 gigs. Then I did a partition for Ubuntu that is only 15 gigs. You don't need multi partitions for different directories of Linux.

---

### Post by caljohnsmith on 2009-01-28
15 GB is definitely too much for the boot partition, you can make it just 200 MB and that should be plenty. If you want specific help with how to repartition your drive, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And please post the output. We can work from there if you want.

---

### Post by egalvan on 2009-01-28
> **echo8413 said:**
> The **only reason you need **to partition is for multi boot. ...** You don't need **multi partitions for different directories of Linux.

Sorry, but I disagree with this.

Each person has to identify his own needs or wants when it comes to partitioning the install media.

There are security, space, and performance issues, among others.

There are advantages and dis-advantages to this situation.

What works for you may not work for anyone else.

For a beginner's first install, using a single partition may be easier.


That said, I have never installed Linux in a single partition...
except for "fun" installs of Puppy, and a few tests of Ubuntu.

But then, I never installed Microsoft products on a single partition, either. :) 
(except where the customer requested single partition install).

Separate partitions, indeed separate drives, can provide safety to one's data.

ErnestG

---

### Post by Zombie_Gaz on 2009-01-28
Disk /dev/sda: 18.3 GB, 18373349376 bytes
255 heads, 63 sectors/track, 2233 cylinders, total 35885448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfa3d67e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    35873144    17936541   83  Linux

Disk /dev/sdb: 18.3 GB, 18373349376 bytes
255 heads, 63 sectors/track, 2233 cylinders, total 35885448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05d51fbc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    35873144    17936541   83  Linux

Disk /dev/sdc: 36.4 GB, 36420075008 bytes
255 heads, 63 sectors/track, 4427 cylinders, total 71132959 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00022bb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    58589054    29294496   83  Linux
/dev/sdc2        58589055    71119754     6265350    5  Extended
/dev/sdc5        58589118    71119754     6265318+  82  Linux swap / Solaris
gaz@dante:~$

---

### Post by Zombie_Gaz on 2009-01-28
And in regards to the last post about not needing multipartitions... I don't agree at all. I do it in Windows too.

I always give a little separate something to at least /home.

Anyway... I guess I was a little misleading. I have multiple hard drives... not really the same as partitions, I guess.

---

### Post by caljohnsmith on 2009-01-28
I think there are many options open to you in your situation; one idea would be to simply create a data directory on your boot partition, and then use that for your personal files. You could make a symbolic link from that directory to your home directory so you could easily access it. The advantage of that is you wouldn't need to do any repartitioning. But if you want to go ahead and repartition, another option would be to shrink your boot partition down to ~200 MB and then create a data partition with the freed space for you to use on that drive. You could mount that partition in a directory in your home folder or some other place where it would be convenient to access it. Those are just two ideas, and I'm sure other people will share their opinions too. Do either of those ideas sound like what you might want, or are you looking for something else?

---

### Post by Zombie_Gaz on 2009-01-28
I guess the advantage to just making symbolic link to some space is that I don't need to go through with the risky buisness of repartitioning?

I'd rather just repartition that boot drive down to like 500 megs (you said 200 but just to be sure) and give the other 17.5 or whatever to /home/me.

Again, though... is there going to be some sort of risk of lost data if I do that (and that's why you're suggesting a symbolic link to a folder?

---

### Post by caljohnsmith on 2009-01-28
Well there's always a risk of losing something when you repartition, but in your case, since you are just going to shrink the boot partition, I wouldn't worry about it and would just go ahead and shrink the boot partition. Even if you were to lose everything in your boot partition, it's possible to reinstall all the boot files again. So if a creating new data partition is what you prefer, I say go for it.

---

### Post by Zombie_Gaz on 2009-01-28
So could I just use a LiveCD to do this (otherwise I wouldn't be able to unmount /boot, right?)?

That's my question... how do I "go for it"?

---

### Post by egalvan on 2009-01-28
> **Zombie_Gaz said:**
> A
Anyway... I guess I was a little misleading. I have multiple hard drives... not really the same as partitions, I guess.

To the computer, there is (almost) no difference between partitions (primary, extended and logical) and hard drives...
for all intents and purposes, they are interchangeable.

Back in the days of 5 & 10 MEGABYTE hard drives, partitions usually spanned an entire hard drive, especially with SCSI allowing so many to be connected.  (anybody else getting misty-eyed remembering this stuff?)

ErnestG

---

