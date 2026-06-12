---
title: "There's a partition in this partition!!"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by DigiTan on 2009-03-09
I was reading the partitioning example on this [Novell Page](http://www.novell.com/coolsolutions/feature/19350.html) and couldn't help but notice the "extended" partition is eclipsing the "Linux" partition.  After all, they have the same start point.  I take it this was no accident, but **what's the benefit behind that?**  The example never really clarified.

```
linux-1reo:~ # fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        1402    11261533+   7  HPFS/NTFS 
/dev/sda2            1403        1415      104422+  83  Linux 
/dev/sda3            1416        1546     1052257+  82  Linux swap / Solaris 
/dev/sda4            1547        9729    65729947+   5  Extended 
/dev/sda5            1547        7920    51199123+  8e  Linux LVM 
```

---

### Post by bodhi.zazen on 2009-03-09
Several potential benefits

The main one is it allows more then 4 partitions on a HD

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

There is also LVM which is way cool ;)

---

### Post by DigiTan on 2009-03-09
Aw, crud!  You mean to tell me just when I think I've got this partition stuff figured out, I gotta jump through *more* hoops?  #-o

Well at least it answers one thing.  When I install Ubuntu, I can have my / partition, my /home paritition, and swap space all under one extended partition.  And if I add a second or third Linux I can do the same?

---

### Post by DigiTan on 2009-03-10
For Ubuntu, if I want my slash, /home, and swap space in one extended partition; does it matter which order I do it in?

---

### Post by avtolle on 2009-03-10
> **DigiTan said:**
> Aw, crud!  You mean to tell me just when I think I've got this partition stuff figured out, I gotta jump through *more* hoops?  #-o

Well at least it answers one thing.  When I install Ubuntu, I can have my / partition, my /home paritition, and swap space all under one extended partition.  And if I add a second or third Linux I can do the same?
Yes; and if you install other distros, these may be on logical paritions within the same extended partition (you may safely share the swap partition between/among the various distros, BTW).

---

### Post by DigiTan on 2009-03-10
Just to clarify: do I add the mini-partitions inside the extended partition as *primary* or *extended*?  Fdisk is making me choose.

---

### Post by bodhi.zazen on 2009-03-10
> **avtolle said:**
> Yes; and if you install other distros, these may be on logical paritions within the same extended partition (you may safely share the swap partition between/among the various distros, BTW).

You can share a swap partition , but the only problem I have seen is occasionally an installer will re-format the swap partition during the install, which means the UUID changes ...

The easiest fix, IMO, is to edit /etc/fstab and change to entry for your swap partition from

UUID=xxx-yyy-zz

to

/dev/sdxy

---

### Post by DigiTan on 2009-03-11
So does everything that goes into the extended partion count as extended?

---

### Post by theozzlives on 2009-03-11
> **DigiTan said:**
> So does everything that goes into the extended partion count as extended?

They are logical drives.

---

### Post by Paqman on 2009-03-11
> **DigiTan said:**
> For Ubuntu, if I want my slash, /home, and swap space in one extended partition; does it matter which order I do it in?

Nope.

One trick though: you might want to leave the swap outside the extended. Why? Because LiveCDs automount any swap partitions they see (to help performance). The problem is that one of the more useful things you can do with a LiveCD is use Gparted on your partitions. However, if a swap within an extended partition is mounted it locks the whole extended partition. Which means Gparted can't edit any of those partitions.

Of course, the solution is to simply disable the swap (in Gparted right click > swapoff). So it's not a massive problem, but it's one that has stumped more than a few newbies who couldn't figure out why the couldn't edit their partitions even though they were on the LiveCD.

---

### Post by The Cog on 2009-03-11
Good idea, Paqman. Useful note.

To summarise, there are 3 types of partition:

Primary partition: The hard disk partition table has space for 4 primary partition entries.

Extended partition: A primary partition that is marked as an extended partition. Its purpose is to act as a container for more partitions. I think you can only have one extended partition. The extended partition has its own partition table inside, which is less space limited than the main disk partition table.

Logical partition: One of the sub-partitions inside the extended partition. I think I read somewhere that there's a limit of 64 of them.

---

### Post by DigiTan on 2009-03-11
Does the logical one count as extended or primary in fdisk?

---

### Post by bodhi.zazen on 2009-03-11
> **DigiTan said:**
> Does the logical one count as extended or primary in fdisk?

No : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

---

### Post by DigiTan on 2009-03-11
That link has already been posted.  I'm asking --when fdisk asks me "extended or primary?"-- which to select.  Logical isn't a choice and GParted is crashing on me.

---

### Post by bodhi.zazen on 2009-03-11
I did not see your question, all I saw was :

> Does the logical one count as extended or primary in fdisk?     Which is answered in the link I (re)gave you.

To answer your current question , first you make an extended , then you will need to make a logical (or more then one) within the extended ;)

Oh, and IMO it is best to reboot after changing your partition table. Not strictly necessary, but it can prevent problems , such as gparted crashing and others.

---

### Post by DigiTan on 2009-03-11
I see where the confusion was here.  When you want a new partition, FDisk makes "logical" an option, but only if there's already an extended partition somewhere on the disk.  This wasn't the case for me, so I was seeing "primary" and "extended" as the only options, and trying to speculate why my future Linux partitions wouldn't be called "logical."

Here's outcome:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30820   247561618+   7  HPFS/NTFS
/dev/sda2           30821       34867    32507527+   5  Extended
/dev/sda5           30821       31992     9414058+  83  Linux
/dev/sda6           31993       34604    20980858+  83  Linux
/dev/sda7           34605       34867     2112516   82  Linux swap / Solaris

```

---

### Post by ibuclaw on 2009-03-11
OK, if you didn't do your homework as bodhi.zazen kindly linked you to, let me just clarify on a ground level.

There are 3 types of partitions:
Primary, Extended and Logical.

A Hard Drive can only have up to **4** Primary Partitions.

An Extended Partition is counted as **1** Primary partition, but acts as a container which can house **many** Logical Partitions. Many being almost as many as you want (the free hard drive space being the only limit).

A Logical Partition is the name of a Partition that exists in an Extended Partition.

In Linux, Primary partitions are identified with the numbers 1-4
ie:
```
/dev/sda1  /dev/sda2  /dev/sda3  /dev/sda4
```
And Logical Partitions are identified with numbers starting from 5.
ie:
```
/dev/sda5  /dev/sda6  /dev/sda7  /dev/sda8
```

To get a better picture of how your hard drive looks, use **gparted** or to get a general idea of how it flows, run the following command:
```
dmesg | grep "sd[a-z]:" | cut -d: -f2 | sort -u
```
In that, you will see all partitions on all connected hard drives.

ie:
```

 sda3 < sda5 sda6 sda7 sda8 sda9 >

```
In my example, I have 1 extended partition on my harddrive (sda3), which homes sda5-9.

> **DigiTan said:**
> I see where the confusion was here.  When you want a new partition, FDisk makes "logical" an option, but only if there's already an extended partition somewhere on the disk.  This wasn't the case for me, so I was seeing "primary" and "extended" as the only options, and trying to speculate why my future Linux partitions wouldn't be called "logical."

Here's outcome:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30820   247561618+   7  HPFS/NTFS
/dev/sda2           30821       34867    32507527+   5  Extended
/dev/sda5           30821       31992     9414058+  83  Linux
/dev/sda6           31993       34604    20980858+  83  Linux
/dev/sda7           34605       34867     2112516   82  Linux swap / Solaris

```
If you shrink the size of the Extended Partition - and all partitions that sit inside it - to allow room for another partition, depending on whether or not it goes inside or outside the Extended Partition container will determine whether or not it will be a Primary or Logical.

Regards
Iain

---

### Post by DigiTan on 2009-03-11
Yeah, I got the numbering figured out.  My hangup was I couldn't see logical partition options until after I said "the hell with it" and made my extended one anyway.  Then I could see it.



Now there's a new problem...or more like a booby trap.  

During the install, I chose manual partitioning.  It lists all partitions asking me to choose one, but I click "Forward" and it says "no root file system is defined."  I tried editing, renaming, and even formatting the partitions but the error sticks.  Word is I gotta go back and name my sda5 partition **"/"**, and I'm about to try it.  If that's the case, I'm wishing they would've simply said that in English.  The error message is about as straightforward as a spring.  :-&

---

### Post by DigiTan on 2009-03-12
Yeah it was "/".  I throw up a little when I think of the time lost figuring out that error message.

---

### Post by estyles on 2009-03-12
Well, ya gotta have *something* be /... otherwise, where would your files go?

---

### Post by Paqman on 2009-03-12
> **estyles said:**
> Well, ya gotta have *something* be /... otherwise, where would your files go?

I think his point is that a newbie isn't going to know that / is also known as root. That's just a little piece of Linux jargon DigiTan. Unfortunately things like this are so fundamental that people often forget to explain them.

That's a case of a bad error message, which is a common fault on all operating systems. The people that write the error messages are working at a level so far above newbie level that they sometimes forget how to relate things without falling back on the jargon.

---

### Post by orethrius on 2009-03-12
> **estyles said:**
> Well, ya gotta have *something* be /... otherwise, where would your files go?

I think we've stumbled upon a usability issue.  Newcomers to UNIX-like systems have no clue what a "no root file system found" error means, because they're used to C:\ being root and already being setup.

Perhaps a clarified message could read:
> No root file system found.  One partition must be named **/** and will contain your system files.
...though I won't pretend that I know what kind of overhead that'd take.

---

### Post by Paqman on 2009-03-12
> **orethrius said:**
> 
Perhaps a clarified message could read:

...though I won't pretend that I know what kind of overhead that'd take.

Raise it as a bug in Launchpad. Against, er, Ubiquity I guess?

---

### Post by orethrius on 2009-03-12
> **Paqman said:**
> Raise it as a bug in Launchpad. Against, er, Ubiquity I guess?

I'm lazy and/or possibly sleep-posting.  Can we file a bug for "sleep deprivation affecting contributors", as well? :-D

---

### Post by estyles on 2009-03-13
> **orethrius said:**
> I think we've stumbled upon a usability issue.  Newcomers to UNIX-like systems have no clue what a "no root file system found" error means, because they're used to C:\ being root and already being setup.

Perhaps a clarified message could read:
No root file system found. One partition must be named / and will contain your system files. 


I don't necessarily agree that it's a problem, or that a newbie who has done no research is likely to do manual partitioning (if you're going to choose the advanced option, then be prepared to a) be advanced, b) ask someone who is, or c) do a little research).

But I *do* agree that it's a bad error message, and I like your proposed message much better.  Nothing beats Windows for the most useless error messages, but that doesn't mean that Ubuntu can't use improved error messages as well.

---

### Post by orethrius on 2009-03-14
> **estyles said:**
> I don't necessarily agree that it's a problem, or that a newbie who has done no research is likely to do manual partitioning (if you're going to choose the advanced option, then be prepared to a) be advanced, b) ask someone who is, or c) do a little research).

Hence why I said "issue" instead of "blocker". ;)
Seriously, though, in dealing with the Windows mindset, we're going to have to field previous "power users" who don't have a clue when it comes to fdisk, but will run it anyway just because they heard it might fix their problems.  Those are precisely the users that we want to call the response "more informative" and "generally better" than the Windows equivalents.

[QUOTE=estyles]But I *do* agree that it's a bad error message, and I like your proposed message much better.  Nothing beats Windows for the most useless error messages, but that doesn't mean that Ubuntu can't use improved error messages as well.[/QUOTE]

Indeed, and if I didn't have a day job I'd file it myself.  Even a brief message explaining that / is partly the equivalent of C:\WINDOWS is better than the current response.

---

