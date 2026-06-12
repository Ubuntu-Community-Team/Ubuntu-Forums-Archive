---
title: "External harddrive formatting for OS X"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by Azrael3000 on 2010-03-13
Hi!

I have an external harddrive that is formatted in ntfs. If my friends mounts it on her Mac she only has read access, which is sort of stupid.

So she gave me the drive to format it to some mac file system. What I read is that hfs+ is the current standard, so I installed hfsprogs to use it with gparted for partitioning. I resized the existing partition and added an hfs+ one.

```

$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0058d47a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       70285   564564231    7  HPFS/NTFS
/dev/sdb2   *       70286      121601   412195770   83  Linux

```

In gparted the later partition is shown to be hfs+. The correct Id in fdisk should be af though.
Now when I gave the drive back to my friend, she couldn't mount the new file system. It just didn't appear. Since I have no clue about macs I don't know about any error messages that might have appeared in any log file.

Any suggestions on what to do?

Thanks in advance,
Arno

[color=red][solution]
Start fdisk on the drive and change the partition label with the 't' command to 'af'. Write changes with 'w' and everything should work.
[/solution][/color]

---

### Post by coffeecat on 2010-03-13
> **Azrael3000 said:**
> I have an external harddrive that is formatted in ntfs. If my friends mounts it on her Mac she only has read access, which is sort of stupid.

No, it isn't sort-of stupid. It isn't stupid at all. NTFS is the proprietary filesystem developed by Microsoft. 99% of Mac users have no need of using NTFS so read-only is more than good enough. Apple have bigger priorities than developing NTFS write capability. However, there is absolutely no difficulty in getting NTFS write capability in MacOS - you install the ntfs-3g driver, more of which in a moment.

The reason the hfs+ formatted drive, formatted in Gparted is unusable in MacOS is that you've got an MS-DOS partition table. An Apple filesystem on a Microsoft partition table: that's the misbegotten offspring of two versions of Satan! :-s :wink: Apple uses the (far superior) GUID partition table. If you want a hfs+ filesystem read-write on both MacOS and Ubuntu, use the Mac Disk Utility and specify the non-journalled version of hfs+. Ubuntu/Linux can read-write to the non-journalled version of hfs+, but can only read the journalled version.

You could probably format it in Gparted if you create a new partition table of the correct sort first, but it's better to use a Mac. Use an Apple OS to create an Apple filesystem.

Or, back to NTFS. Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1426589](http://ubuntuforums.org/showthread.php?t=1426589)

I posted a link for ntfs-3g in MacOS in post #6., and there's more discussion of the pros and cons of choosing a filesystem for read-write in both MacOS and Linux.

---

### Post by Azrael3000 on 2010-03-13
well she used to have Windows so that's why it is formated in this way.

Anyhow thanks for all the information. One more question: Deleting the partition table will delete all data right? That's kind of something I wanted to avoid, but if it doesn't work otherwise it is a possibility.

---

### Post by coffeecat on 2010-03-13
> **Azrael3000 said:**
> One more question: Deleting the partition table will delete all data right? That's kind of something I wanted to avoid, but if it doesn't work otherwise it is a possibility.

Yes it will. You'll get a completely unallocated disc - no partitions.

Did you read through that thread I linked? I go into more details of one disadvantage with hfs+ - that of potential permissions problems when swapping files between Ubuntu and MacOS. You avoid that if you use NTFS. Installing the ntfs-3g driver is really easy in MacOS. Two packages to download, two packages to double-click on. Install MacFUSE core first. The only difficult bit is a question you get asked when installing ntfs-3g. Disable caching = slow; enable caching = not quite so slow. :wink: You can change this in the Mac System Preferences later if you need.

One more point - if you reformat the drive in the Mac Disk Utility for hfs+, make sure it gets the partition table right. If I remember correctly (in Ubuntu atm) there's an 'advanced' button in the partitioning section where you can choose from one of 3 or four partition table types. If you choose hfs+ it *ought* to set this correctly for you but as the disc already has an ms-dos partition table, Disk Utility might get this wrong.

Good luck!

---

### Post by Azrael3000 on 2010-03-13
Thanks man. I think I'll go with the ntfs-3g option.

[edit]
another solution found. see last post.
[/edit]

---

### Post by srs5694 on 2010-03-13
> **coffeecat said:**
> Apple have bigger priorities than developing NTFS write capability. However, there is absolutely no difficulty in getting NTFS write capability in MacOS - you install the ntfs-3g driver, more of which in a moment.

As a point of information, OS X 10.6 does include NTFS read/write capability; however, the write feature is disabled by default, and users who have enabled it have reported that it's buggy. Perhaps it'll be fixed with 10.7....

> The reason the hfs+ formatted drive, formatted in Gparted is unusable in MacOS is that you've got an MS-DOS partition table.

That's incorrect. OS X is perfectly capable of handling MBR (aka "MS-DOS") disks, and can use HFS+ on MBR disks. Azrael3000 correctly identified the problem with his configuration in his first post: The HFS+ partition is marked as type 0x83, when it should be 0xAF. The solution is easy: Use Linux fdisk to change the partition type. (Use the 't' option in fdisk to do this, then save the change with 'w'.)

> If you want a hfs+ filesystem read-write on both MacOS and Ubuntu, use the Mac Disk Utility and specify the non-journalled version of hfs+. Ubuntu/Linux can read-write to the non-journalled version of hfs+, but can only read the journalled version.

This is largely correct, although I believe it's possible to disable the journal with a mount option or utility of some sort. (I don't recall the details, though.)

[quote=Azrael3000]One more question: Deleting the partition table will delete all data right? That's kind of something I wanted to avoid, but if it doesn't work otherwise it is a possibility.[/quote]

There are a handful of utilities that will convert from MBR to GPT without loss of data. My own [GPT fdisk](http://www.rodsbooks.com/gdisk/) is one; another is [gptgen.](https://sourceforge.net/projects/gptgen/) I believe the FreeBSD gpt program will do it, too.

---

### Post by coffeecat on 2010-03-13
> **srs5694 said:**
> That's incorrect. OS X is perfectly capable of handling MBR (aka "MS-DOS") disks, and can use HFS+ on MBR disks.

I stand corrected. I know that Macs can handle MBR discs because they can read FAT32 discs. I was simply going from personal experience with HFS+ on MBR. When I (mistakenly) created an ms-dos partition table and then a hfs+ partition using Gparted, my Mac wouldn't have anything to do with it. But you've given me something to try out again. Thanks for that.

---

### Post by srs5694 on 2010-03-13
I just tested myself, and got the same results as Azrael3000: GParted incorrectly creates HFS (my GParted wouldn't do HFS+) as MBR type 0x83, but the correct MBR type code for HFS or HFS+ is 0xAF. OS X definitely does support HFS or HFS+ on a type 0xAF partition.

---

### Post by coffeecat on 2010-03-13
> **srs5694 said:**
> my GParted wouldn't do HFS+

I just had a look in Gparted in Lucid. I hadn't installed any of the hfs* packages in the repos yet. View > File System Support said that I needed hfsutils for hfs and hfsprogs (which is in Universe) for hfs+. So I installed each of the packages in turn, closing and re-opening Gparted each time:

Installed hfsplus - no difference

Installed hfsutils - the green tick in the Create column appeared for hfs.

Installed hfsprogs - the green tick in the Create column appeared for hfs+

I've haven't tested it in anger, so to speak, by formatting a drive, but it looks as though Gparted thinks it can create an hfs+ partition if you install hfsprogs. I haven't time to do any further fiddling now to see whether that is really true, but I will do sometime. Based on what you've just found it was probably the case that when I thought I had created hfs(+) on a MBR disc in Gparted a year or so ago, it had really created an ext filesystem and that was why MacOS couldn't read it - just like with the OP. Bit of a gotcha, that. Thanks for the clarification.

Whatever - it seems to be safer to use a Mac to format hfs+. :)

---

### Post by srs5694 on 2010-03-13
> **coffeecat said:**
> Based on what you've just found it was probably the case that when I thought I had created hfs(+) on a MBR disc in Gparted a year or so ago, it had really created an ext filesystem and that was why MacOS couldn't read it - just like with the OP.

Actually, my suggestion is that GParted is creating the correct filesystem but setting the wrong partition type code in the partition table. That's definitely what happened to me. It's got a type code of 0x83 (Linux), but when I mount it, /etc/mtab shows it to be mounted as type "hfs". Changing the type code using fdisk should therefore correct the problem.

On a related but peripheral note, I'd have to advise caution when using OS X's Disk Utility. It's pretty inflexible, and I've encountered situations where it will delete partition A when you tell it to create a filesystem on partition B. This happened to me on an MBR disk with a slightly unusual layout: two primary partitions (/dev/sda1 and /dev/sda2 in Linux parlance), an extended partition (/dev/sda3) filled with several logical partitions (/dev/sda5 through /dev/sda{something}), trailed by a primary partition at the end (/dev/sda4). When I asked Disk Utility to create a fresh filesystem on the final logical partition, it also deleted /dev/sda4. IIRC, it also expanded the extended partition to fill the space formerly occupied by /dev/sda4. Fortunately I had a backup of my partition table so I was able to recover pretty easily. Somebody without such a backup would have been much worse off.

---

### Post by coffeecat on 2010-03-14
> **srs5694 said:**
> Actually, my suggestion is that GParted is creating the correct filesystem but setting the wrong partition type code in the partition table.

Thanks for the clarification. That sounds like a bug. Since your knowledge is deeper than mine, do you want to fle a bug report? :wink:

> **srs5694 said:**
> On a related but peripheral note, I'd have to advise caution when using OS X's Disk Utility. It's pretty inflexible, and I've encountered situations where it will delete partition A when you tell it to create a filesystem on partition B.

Agreed. In fact I've never been able to get it to do anything but wipe the whole disc and start over if I wanted to reformat just one partition. I take a pragmatic approach. If I want HFS+ to swap between MacOS and Linux I format an old drive with just one partition using Disk Utility. If I want to do partitioning/reformatting which doesn't include HFS+, I use Gparted.

But now I've installed ntfs-3g on my Mac the point is moot for me because I can use NTFS. The one big advantage with NTFS, in my view, is that it neatly sidesteps permissions issues. My UID on Ubuntu is 1000 whereas my UID on my Mac is 99 (iirc) and I did get permissions hiccups when using HFS+ between MacOS and Ubuntu. I've occasionally pointed out this unintended advantage of NTFS and been roundly castigated by the MS-haters here. But I'm a pragmatic man - it works and I've got Windows available to repair the NTFS filesystem if need be.

---

### Post by Azrael3000 on 2010-03-14
Well I most certainly agree with SRS on this matter. I changed the partition table with fdisk and voila it worked. Must be a bug so.

[edit]
Bugreport filed:
[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/538682](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/538682)
[/edit]

---

### Post by srs5694 on 2010-03-14
> **coffeecat said:**
> Thanks for the clarification. That sounds like a bug. Since your knowledge is deeper than mine, do you want to fle a bug report?

I've tried filing bug reports on the [official GNU Parted bug tracker](http://parted.alioth.debian.org/cgi-bin/trac.cgi/newticket) in the past, but it's always thought I was spamming it. :rolleyes: I've heard they take bug reports on their mailing list, but I don't want to subscribe to a mailing list just to file a bug report!

---

### Post by Azrael3000 on 2010-03-14
might be a good idea to do an upstream bugreport

---

### Post by coffeecat on 2010-03-15
@Azrael3000 and @srs5694, a little bit to add:

Creating an ms-dos partition table and an hfs+ partition in Gparted on an old drive gave me the same issue: mtab mounts it as hfs but sudo fdisk -l lists it as type 83. Changed that to type af with fdisk and the disk mounts read-write quite happily in Snow Leopard.

OK, that's nothing new, but:

In the course of this I discovered something interesting about Ubuntu automounts to /media. I'm sure it wasn't like this a year or more ago. After setting the partition type to type af with fdisk, it automounted quite happily in Karmic but, predictably, I couldn't do a drag and drop into it at first because the mountpoint was owned by root. A quick:

```
sudo chown myusername: /media/untitled
```...fixed that, but when I unmounted and remounted (the mountpoint was deleted and recreated as usual) the newly-recreated mountpoint /media/untitled was still owned by myself and I could drag and drop into the HFS+ partition without issue. This even survived a reboot. So the OS must be "remembering" the chown for that mountpoint. I guess also the UUID, because in the course of my experiments I reformatted the drive with a unlabelled partition and the new /media/untitled was now owned by root again.

I also tried this with an ext3 partition. When first mounted /media/partitionlabel was owned by root but after I had chowned to to my username, the permissions survived a remount and a reboot. That's extremely useful and I have not come across this before.

On a side note, I still think that having to sudo chown the first time is still unnecessary in a single user home environment - and also newbie-unfriendly. You see plenty of threads from inexperienced users who have formatted their external drives ext2/3/4 and can't understand why they're running into permissions problems. Apple gets this right in MacOS. You have the option to set restrictive permissions on your files if you wish, but you don't get any of this access denied because the drive is mounted by root nonsense. I think this counts as a papercut. What do you think?

Anyway, to continue... I think I've discovered another bug in Gparted. If you create a "mac" type partition table (I think that's the older Apple Partition Map, not GUID) you get the odd little partition 1 which is actually the partition map. If you then try to create a partition in the unallocated space, it fails with an error. The "details" file reports "*Cannot have overlapping partitions." *If you move the start point for the new partition so that there is unallocated space between it and the 31.5KiB so-called sdx1, the new partition is created just OK. And Snow Leopard was quite happy with it - reading and writing to it OK.

Is it worth reporting? I shouldn't think many people are going to use Gparted to create an APM with a HFS+ (non-journalled) partition, but I could add this observation to the Launchpad thread. What do you think?

---

### Post by Azrael3000 on 2010-03-16
> **coffeecat said:**
> 

On a side note, I still think that having to sudo chown the first time is still unnecessary in a single user home environment - and also newbie-unfriendly. You see plenty of threads from inexperienced users who have formatted their external drives ext2/3/4 and can't understand why they're running into permissions problems. Apple gets this right in MacOS. You have the option to set restrictive permissions on your files if you wish, but you don't get any of this access denied because the drive is mounted by root nonsense. I think this counts as a papercut. What do you think?


Yeah I was also quite annoyed by this. Maybe you could have a dialog appearing after first mount saying something like: 
```
A new device has been attached to the computer. 
Do you want to mount it for user or root access?
[button1]Open for user access (standard)[/button1] 
[button2]Open for root access only[/button2]

```
If you click 'user access' you have to provide the root password and a chown is done. Otherwise everything stays as per usual.
Maybe we can also have a little checkbox saying 'Save this setting for future use of this device' (standard: enabled)

> **coffeecat said:**
> 
Anyway, to continue... I think I've discovered another bug in Gparted. If you create a "mac" type partition table (I think that's the older Apple Partition Map, not GUID) you get the odd little partition 1 which is actually the partition map. If you then try to create a partition in the unallocated space, it fails with an error. The "details" file reports "*Cannot have overlapping partitions." *If you move the start point for the new partition so that there is unallocated space between it and the 31.5KiB so-called sdx1, the new partition is created just OK. And Snow Leopard was quite happy with it - reading and writing to it OK.

Is it worth reporting? I shouldn't think many people are going to use Gparted to create an APM with a HFS+ (non-journalled) partition, but I could add this observation to the Launchpad thread. What do you think?

Well why not add it. Sure there are not many people doing it but only a removed bug is a good bug. And it doesn't sound as if it would be that much work to fix it.

---

### Post by Azrael3000 on 2010-03-19
coffeecat can you please have a look at the bug in launchpad. Your profile says you are using the development version. So can you confirm what the people say about the fix?

---

### Post by coffeecat on 2010-03-19
> **Azrael3000 said:**
> So can you confirm what the people say about the fix?

Running Lucid fully updated this morning (effectively Beta 1), creating a new ms-dos partition table + hfs+ partition, I get the same as in Karmic. That is, mtab shows the partition mounted as "hfsplus", but fdisk gives partition id as 83. I haven't bothered to plug it into my Mac.

However. From that Launchpad thread....

> This patch is included in the parted-2.0 release.The version of parted in Lucid is currently 2.1, but 2.2 is available but cannot be installed just yet. This is because a needed dependency hasn't yet been uploaded to the repositories. This is common at the alpha and beta stage. It'll get sorted out by the time of final. Also...

> Lucid currently has libparted 2.2, so it should be fixed there... (not  tested myself)

Well no, or not yet. My libparted is currently 2.1, with no 2.2 showing as available yet. I guess it's libparted 2.2 that parted 2.2 is waiting for, so I should imagine this will be resolved soon. As soon as it is I'll retest and repost.

---

### Post by Azrael3000 on 2010-03-19
Well yes he corrected himself. It's solved in 2.2 not in 2.0. So I guess this bug can be closed.

Maybe you can open another bug for the Mac partition table issue.

---

### Post by coffeecat on 2010-03-19
> **Azrael3000 said:**
> Maybe you can open another bug for the Mac partition table issue.

Maybe. I think the number of people who have need to create a partition table type with Gparted that is really only of use with the older PowerPC Macs could be counted on very few fingers. I think I'll pass on that one! :p

---

### Post by srs5694 on 2010-03-19
> **coffeecat said:**
> Maybe. I think the number of people who have need to create a partition table type with Gparted that is really only of use with the older PowerPC Macs could be counted on very few fingers. I think I'll pass on that one! 

Why do you think that only older PowerPC Macs might use MBR? Intel-based Macs can handle it fine, too, and I can think of several scenarios in which users might want to do this:


[list]
[*]A user might want to create such a partition table on a USB flash drive or other removable medium for exchanging files between Linux and OS X. The original post by Azrael3000 sounds like it falls into this category.
[*]This might make sense in certain dual-boot configurations on Macs -- say, if an existing Linux installation on an MBR disk were physically moved to a Mac and the user wanted to add or change a partition for use in data exchange. (Intel-based Macs can reportedly boot from MBR disks, although I personally have never done this and so can't verify it myself.)
[*]Many people in the Hacktosh community (those who run OS X on non-Apple hardware) install OS X on MBR disks.
[/list]

---

### Post by coffeecat on 2010-03-19
> **srs5694 said:**
> Why do you think that only older PowerPC Macs might use MBR?

I wasn't. I was referring to APM.

---

### Post by srs5694 on 2010-03-19
Oh, OK. I forgot about the mention of an APM bug earlier in the thread.

---

