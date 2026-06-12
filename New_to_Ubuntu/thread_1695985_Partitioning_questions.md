---
title: "Partitioning questions"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by llmunro on 2011-02-26
Hi,

I dual boot Ubuntu 10.10 with Windows 7.  When I started with Ubuntu, I was planning to only give it a little bit of room because I was only going to mess around with it sometimes.  Little did I know that I would come to use it nearly exclusively!

Because the partition for Ubuntu is pretty small, I've started getting low disk space warnings.  I used the live CD and fired up GParted to adjust the partitions.  I shrank the Windows partition down to make more room for Ubuntu and it is here that I'm having problems.  I can't make the Ubuntu partition larger than it already is.  There are also two large gray bars in GParted that say "unallocated space."  I would like to be able to use that space for Ubuntu instead, but I'm not sure how to do this, as looking at the unallocated space in GParted gives me no other option than to make a new partition.  (I don't think I want to do this.  I just want to use the unallocated space for an existing partition.)

Can this be done?  Advice?

Thanks.
Lisa

---

### Post by Mark Phelps on 2011-02-26
You'll be lucky if you can now get back into Win7.  Shrinking the parition with Gparted is asking for trouble.

As for your partitioning question, there is not nearly enough information to answer that.

At the least, open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list out the partitions on your drive.

---

### Post by seawolf167 on 2011-02-26
You'll want to resize the Ubuntu partition into the unallocated space - note that the unallocated space needs to be "next to" the partition you wish to resize.

As noted by Mark Phelps, it is suggested that you use the built in Windows partition editors or another Windows-specific program to resize Windows partitions to ensure that everything goes smoothly.

[Here]("http://www.howtoforge.com/partitioning_with_gparted") is a GParted how-to

[Here]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions") is a resize windows partitions how to

---

### Post by llmunro on 2011-02-26
Hi,

Thanks for the help and advice.  I confess that I didn't realize the inherent dangers in resizing Windows partitions with Gparted, but luck seems to be with me, as the Windows partition is fine.

I'll try to provide more information about the partitions:


lisa@lisa-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2           81920    21053439    10485760    7  HPFS/NTFS
/dev/sda3   *    21053440   164560895    71753728    7  HPFS/NTFS
/dev/sda4       205037719   312496379    53729330+   5  Extended
/dev/sda5       205037721   239689799    17326039+  83  Linux
/dev/sda6       239689863   241296299      803218+  82  Linux swap / Solaris
/dev/sda7       309476223   312496379     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00097991

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976773119   488385536    b  W95 FAT32


As far as I can tell, the unallocated space is indeed next to the Ubuntu partition.

I'll do some more reading about using Gparted.  In the meantime, any further advice would be greatly appreciated.

Thanks much.

Best,
Lisa

---

### Post by el_koraco on 2011-02-26
[http://www.dedoimedo.com/computers/gparted.html]("http://www.dedoimedo.com/computers/gparted.html")

---

### Post by Hedgehog1 on 2011-02-26
> **llmunro said:**
> ... There are also two large gray bars in GParted that say "unallocated space."  I would like to be able to use that space for Ubuntu instead, but I'm not sure how to do this, as looking at the unallocated space in GParted gives me no other option than to make a new partition...

Lisa,

Having JUST done this myself two days ago, the reason you cannot enlarge your Ubuntu partition is because it is sitting inside an 'extended' partition that must be enlarged first.

The extended partition is /dev/sda4 and then the partitions that follow it are 'indented'.  That means they live inside the extended partition.

If you look at your drive with the disk utility (go look right now, I will wait...) you will see that there is a long extended partition shown above the Ubuntu partition.

Enlarge that one first, and the rest will work like you were expecting!

:KS

*p.s. I went from 150gig to 700gig for Ubuntu this week!*

---

### Post by Hedgehog1 on 2011-02-26
```

Device Boot Start End Blocks Id System
/dev/sda1 63 80324 40131 de Dell Utility
/dev/sda2 81920 21053439 10485760 7 HPFS/NTFS
/dev/sda3 * 21053440 164560895 71753728 7 HPFS/NTFS
/dev/sda4 205037719 312496379 53729330+ 5 Extended
[B][COLOR="Red"]/dev/sda5 205037721 239689799 17326039+ 83 Linux
/dev/sda6 239689863 241296299 803218+ 82 Linux swap / Solaris
/dev/sda7 309476223 312496379 1510078+ 82 Linux swap / Solaris[/COLOR][/B]

```

As a note - primary/base partitions are always 1-4.

Any partition number [COLOR="red"]**5**[/COLOR] or higher lives in an extended partition.

Lisa - you have 2 swap partitions.  (sda6 & sda7).  You only need one.  

:KS

---

### Post by samacaster on 2011-02-26
Win7 is fine after a resize with Gparted. It'll run its chkdsk funtion on startup to realign -if you will- everything. The drawback is that on an NTFS sytem this creates fragmentation. When next in Win7 I would recommend a Defrag. 

As Hedgehog said, you do not need two swap partitions.

---

### Post by llmunro on 2011-02-26
Hello to all and thanks much for the help!

I have zero idea how I ended up with two swap partitions.  Is this something I need to fix?

I did look at the partitions with the disk utility, as suggested. (Screenshot attached, just in case!) I can see that the Ubuntu stuff is under the 55 GB extended partition. (And yes, its a very small hard drive that's many years old at this point.  I have a second hard drive of 500 GB, as well, but Ubuntu is on the small hard drive.)  So, do I understand correctly that I need to extend /dev/sda4?

Many thanks!

Best,
Lisa

---

### Post by Hedgehog1 on 2011-02-26
> **llmunro said:**
>   So, do I understand correctly that I need to extend /dev/sda4?


Yes - that is your first step.

Once it is expanded, you can them move/expand /dev/sda5

:KS

***By the way - you can still reach this web site using the browser on the liveCD as you wait for things to be moved around by gparted (so we are still available).***

---

### Post by Hedgehog1 on 2011-02-26
> **samacaster said:**
> Win7 is fine after a resize with Gparted. It'll run its chkdsk funtion on startup to realign -if you will- everything. The drawback is that on an NTFS sytem this creates fragmentation. When next in Win7 I would recommend a Defrag. 


This has been my experience as well - defrag before you shrink an NTFS partition with gparted and you should be fine.

Backups are always a good idea - you might lose power during the move or kick the plug or - well - these things happen (ask me how I know - no - don't ask. Really.).

Thanks samacaster!

---

### Post by llmunro on 2011-02-26
Ha.  This (kicking the power plug, etc.) sounds like me on a good day! :P

Nevertheless, the Windows stuff is backed up, so if I completely mess it up, at least I will not be sobbing.

Anyways, I'm writing from my laptop and looking at my desktop, the latter of which is the one I'm trying to arrange the partitions on.  I've run into the first problem: when I select dev/sda4, I can't resize it, as GParted says that its is Busy (at least one logical partition mounted).  As I'm running GParted from the live CD, I don't really see how its possible that there's a partition mounted.

Thoughts?

Thanks.
Lisa

---

### Post by Hedgehog1 on 2011-02-26
> **llmunro said:**
> Ha.  This (kicking the power plug, etc.) sounds like me on a good day! :P

Nevertheless, the Windows stuff is backed up, so if I completely mess it up, at least I will not be sobbing.

Anyways, I'm writing from my laptop and looking at my desktop, the latter of which is the one I'm trying to arrange the partitions on.  I've run into the first problem: when I select dev/sda4, I can't resize it, as GParted says that its is Busy (at least one logical partition mounted).  As I'm running GParted from the live CD, I don't really see how its possible that there's a partition mounted.

Thoughts?

Thanks.
Lisa

It likely got mounted when you were looking it things on the disk.

Right click on the partition in gparted and select 'unmount'.

---

### Post by llmunro on 2011-02-26
Ay, no joy.  The option to unmount dev/sda 4 is grayed out and un-selectable.

Also, it looks like one of the two swap partitions is sitting between my dev/sda5 and the unallocated space that I want to extend the sda4 into.  Keep or delete?

Thanks for the persistent help.

Best,
Lisa

---

### Post by Hedgehog1 on 2011-02-26
> **llmunro said:**
> Ay, no joy.  The option to unmount dev/sda 4 is grayed out and un-selectable.

Also, it looks like one of the two swap partitions is sitting between my dev/sda5 and the unallocated space that I want to extend the sda4 into.  Keep or delete?

Thanks for the persistent help.

Best,
Lisa

This is where things can get difficult - I can't see over you shoulder.

If you have booted from the LiveCD - you can unmount drive partitions.

If you cannot unmount hard drive partitions, then that tells me you are running off the hard drive and not the CD.

So I have to ask - are you SURE you really booted off the CD? :confused:

---

### Post by Hedgehog1 on 2011-02-26
Wait a moment:

You may have to unmount sda5, sda6 and sda7 first before you can unmount the parent partition of sda4.

:KS

---

### Post by Hedgehog1 on 2011-02-26
> **llmunro said:**
> 
Also, it looks like one of the two swap partitions is sitting between my dev/sda5 and the unallocated space that I want to extend the sda4 into.  Keep or delete?


Keep one - delete the other.  Don't know which on should be deleted, we can fix that in the fstab file later if you delete the wrong one.

---

### Post by llmunro on 2011-02-26
Hi,

I checked all seven of the partitions and not one with an option to dismount.

Not sure what to do now.

Thanks.
Lisa

---

### Post by Hedgehog1 on 2011-02-26
*Old saying: Take two reboots and call me in the morning...*

Do this - Reboot on the liveCD go directly to Gparted - don't look at the hard drive any other way first.

Then none should be mounted, and you can follow the original plan.  I hope. [-o<

---

### Post by nm_geo on 2011-02-26
Hi Hedge!
I am following this one looks like fun  :D

---

### Post by llmunro on 2011-02-27
I generally find that rebooting is the most logical thing to do when you're about out of options, but still no dice in this case.

Here's my thought: what if I reinstall Ubuntu? Do you think I would be able to change the partitions on the installer?

Any thoughts or ideas appreciated.

Many thanks.
Best,
Lisa

---

### Post by Hedgehog1 on 2011-02-27
Yup - waiting for data to get moved is like watching paint dry...

I had to move 640 gigs to a new 1 tb drive a few mights ago, using ddrescue as I had some bad sectors on the source drive.

Luckily, I had no finished watching the Daytona 500 - so that gave me something fun to do...

Here is my gparted picture after:

---

### Post by Hedgehog1 on 2011-02-27
Lisa,

Before you uninstall a dual-boot system, you first have to boot on the windows rescue CD and do the  FIXMBR.

Otherwise you cannot boot into windows again after deleting the Ubuntu partitions from Windows disk manager.

Do you know how to do that?  If so, and uninstall is a perfectly reasonable thing.

This time you can manually control your partitions, too.

---

### Post by Hedgehog1 on 2011-02-27
Here is the crash course:

[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/5151606.png?619[/IMG]

[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/2756040.png?559[/IMG]

[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/1433690.png?753[/IMG]


Now when you reboot, you come up directly in Windows 7, no grub menu.

**THEN** you can delete all the Ubuntu partitions.

---

### Post by nm_geo on 2011-02-27
You know in Gparted you can turn off swap partitions.  Since the swap partition is in the extended partition you might need to do that.

---

### Post by Hedgehog1 on 2011-02-27
> **nm_geo said:**
> You know in Gparted you can turn off swap partitions.  Since the swap partition is in the extended partition you might need to do that.

***[SIZE="2"]And where were you when I needed you????[/SIZE]***

I did not know that.  Is this what is catching Lisa out?

---

### Post by nm_geo on 2011-02-27
> **Hedgehog1 said:**
> ***[SIZE=2]And where were you when I needed you????[/SIZE]***

I did not know that.  Is this what is catching Lisa out?

  Could be I just resized my swap file as a test, but first turn swap off with two I would delete the one between Ubuntu partition and the free space.

normally swap is like 2X ram.

---

### Post by Hedgehog1 on 2011-02-27
> **nm_geo said:**
> Could be I just resized my swap file as a test, but first turn swap off with two I would delete the one between Ubuntu partition and the free space.

normally swap is like 2X ram.

This is weird (well, for a hedgehog, anyway) because i do this all the time, and once I am booted from the CD or USB stick, I can change any partition any way I like on the hard drive.

There is something we are assuming, that Lisa doesn't know we are assuming.

But what....

---

### Post by nm_geo on 2011-02-27
LIsa is booting from CD but I think the swap files are still enabled to swap if ram gets low.  It really would not hurt to turn swap off delete both swap files and create one after the Ubuntu partition is expanded.

---

### Post by Miljet on 2011-02-27
When you boot a live CD, if it finds a swap partition, it will automatically use it. Since the swap, or in this case both swaps, are a part of the extended partition that you are trying to resize, swap has to be turned off.

---

### Post by Hedgehog1 on 2011-02-27
Cool - so can you tell Lisa*** (and me)*** how we turn off swap?

I run 12 gigs of ram - so I never really hit the swap space...

---

### Post by nm_geo on 2011-02-27
Lisa are you sure you are using Gparted the screenshot was taken from disk utility?  You have 2 areas of free space.

---

### Post by nm_geo on 2011-02-27
> **Hedgehog1 said:**
> Cool - so can you tell Lisa*** (and me)*** how we turn off swap?

I run 12 gigs of ram - so I never really hit the swap space...

Sure go to Gparted and check on the swap file Under partition swap off option.

---

### Post by Hedgehog1 on 2011-02-27
> **nm_geo said:**
> Sure go to Gparted and check on the swap file Under partition swap off option.

See - that was MUCH too easy.

No wonder I never noticed it.

Thanks!

:KS

---

### Post by nm_geo on 2011-02-27
> **Hedgehog1 said:**
> See - that was MUCH too easy.

No wonder I never noticed it.

Thanks!

:KS

By the way this village is better off with you around.. I like your style.. Hope Lisa responds back soon. I really think perhaps Lisa was using the disk utility (maybe not) but the screenshot was disk utility.

Hedge do you have Gparted installed in your working Ubuntu?

---

### Post by Hedgehog1 on 2011-02-27
I do have it installed, yes.

I am (at this instant) working from a new 'Ubuntu-on-a-stick' bootable USB stick.

I am working through the 274 updates...

Did you want me to try something? :confused:

:KS

*So this car battery goes into a Bar. The bartender says to it: 'You can stay, but don't you start nothing!'*

---

### Post by nm_geo on 2011-02-27
> **Hedgehog1 said:**
> I do have it installed, yes.

I am (at this instant) working from a new 'Ubuntu-on-a-stick' bootable USB stick.

I am working through the 274 updates...

Did you want me to try something? :confused:

:KS

*So this car battery goes into a Bar. The bartender says to it: 'You can stay, but don't you start nothing!'*

No not really after the regular install most user don't go get Gparted but I thought you might. Just curious.. Guess Lisa called it a night I am about to do the same..

I still think she was using disk utility instead of Gparted. OUT

---

### Post by Hedgehog1 on 2011-02-27
I'm going to shut down now too.

Great working with you (and Lisa too!)

:popcorn:

---

### Post by llmunro on 2011-02-27
Good morning to all! Thanks for all of the help and responses!

The screenshot I attached was indeed taken with Disk Utility from the Ubuntu installation on my hard drive.  I've been using GParted from the Live CD to try (unsuccessfully so far) to change the partitions.

It seems from the discussion here that the swap between the two partitions may be the culprit. It sounds like I need to use GParted from the live CD and turn it off and then try to extend the paritions?

I'm backing up all my data in case something goes bad wrong.  

Many thanks.
Lisa

---

### Post by llmunro on 2011-02-27
SUCCESS!!!!!  

Here's what I had to do:
I turned both swaps off, which then allowed me the option of resizing dev/sda4.  I attempted to extend it into the 19.30 GB unallocated space that you can see on the GParted screenshot I've attached here.  I kept getting an error message that this wasn't possible, so I decided to get brave and just delete one of the swaps, the one sitting between the dev/sda5 and the other unallocated space.  This allowed me to extend dev/sda5 from 18 GB or so to 35.  I suppose I'll probably have to revisit this problem and figure out the error message about dev/sda4 when I run out of disk space again, but in the meantime, I at least have some new disk space!  Hooray!

I love Ubuntu.  I learn at least ten things about it every day.

Many thanks to all who brainstormed to help me figure this out.  I salute you all! 

Best,
Lisa

---

### Post by Hedgehog1 on 2011-02-27
I also learned something, too: Once you have a couple of swap spaces, things can get unpredictable.

When you feel brave again, you can extend your partitions to use all the extra space.

No hurry, though.  We will be here when you need us.

:KS

---

### Post by nm_geo on 2011-02-27
I had a feeling Lisa would get it solved with the information we provided. C U both around the [I]Village.


[/I]

---

