---
title: "Partitioning recommendations for dual boot"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by OllieGab on 2009-09-11
I want to install Ubuntu and another distro on the same hard drive and I want to have the same set-up on both, ie 3 partitions: swap, root and home.

Question 1: Can I use just one swap, that will work for both distros?
Question 2: Do I need 2 /home partitions, one for each distro?
Question 3: Am I better setting up the partitions before I actually install anything, eg with GParted via a live CD?

Cheers Ollie

---

### Post by zerhacke on 2009-09-11
1.  Swap is universal.  You can use the same swap with both distros.

2.  I certainly suggest separate /home partitions.  The two distros will not have the same software and same versions so it could cause a lot of conflicts to share /home.

3.  If it's a blank disc or one you plan to overwrite completely you don't need to use Gparted Live.  Be sure to manually specify your partitions in the setup of both OS's though.

---

### Post by LewRockwell on 2009-09-11
one swap is fine

we always think ahead when partitioning and therefore size our swap partitions with regards to the machine's maximum ram capability

for example, say your machine will accept 2GB max ram...then your swap partition will be 2GB(other opinions exist but we will think ahead so that we don't need to enlarge the swap at a latter, more inconvenient, time)

we always recommend separate partitions for each operating system as this makes it easiest on those less technically inclined

if you think you need to set up a stand-alone data/storage partition then by all means do so, but try not to make your hard drive partitioning scheme so complicated that even you get confused(after all, this is supposed to be FUN and ENJOYABLE!)

as always, your mileage may vary

we now return you to your regularily scheduled programming

.

---

### Post by OllieGab on 2009-09-11
I know you said I didn't really need to partition my hard drive with (for instance) GParted beforehand...but I tried anyway:-?

Now, I can only make 4 primary partitions, maximum, by the looks of things. So how do I go about it, creating 2 root, 2 home and one swap partition.

I haven't got that primary/extended partition knowledge fully under my belt yet and it doesn't really want to play when I try...

---

### Post by oldfred on 2009-09-11
In your extended partition you can have many partitions. Only windows requires primary partitions. You can create one or two primary and put the rest in extended partitions, it will make no difference to Ubuntu or any other Linux. 
I agree with Lew on keeping it simple when starting out, but have a separate data partition to share with all installs makes sense to me.

If you want to see the planning involved in installing 145 systems on two hard drives (it is older but still valid and discusses some of the issues with various distributions):
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

---

### Post by LewRockwell on 2009-09-11
> **oldfred said:**
> In your extended partition you can have many partitions. Only windows requires primary partitions. You can create one or two primary and put the rest in extended partitions, it will make no difference to Ubuntu or any other Linux. 
I agree with Lew on keeping it simple when starting out, but have a separate data partition to share with all installs makes sense to me.

If you want to see the planning involved in installing 145 systems on two hard drives (it is older but still valid and discusses some of the issues with various distributions):
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

+ 1 on the 145 operating systems on one machine(do that with windoze...lol)

.

---

