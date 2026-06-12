---
title: "Partitioning Scheme Suggestions?"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by Sirkey on 2010-06-27
Hello wonderful ladies and gentlemen of the Ubuntu community.

Within the week, I will be receiving a 640GB Toshiba external hard disk. I want to partition this disk so as to duel boot Ubuntu 10.04 (the latest one - downloaded it today) and BackTrack 4 (also the latest one - _not_ downloaded today). I also want to use the disk for general storage.

I have absolutely **no** experience with partitioning. When it comes to Ubuntu, I have installed EEEbuntu Standard onto a 4GB SDHC card and use it in my EEE PC 701 netbook.

I have searched around the forums, and internet, and have a vague idea of what sort of structure I should use, but nothing talked about installing BackTrack and Ubuntu together (on separate partitions).

What I _do_ know about partitioning is limited to this:
[LIST]
[*]You can only have 4 partitions, but any one can be converted into an extension partition, with any number of logical partitions within it.
[*]Partitions are labelled using names such as `sda1`, where the _`a`_ represents the drive, and the number represents the partition.
[*]The number in partition names represents what type of partition it is - 1-4 = normal/extended 5+ = logical.
[/LIST]

In my mind, I want three partitions;
[LIST=1]
[*]Ubuntu 10.04
[*]BackTrack 4
[*]Storage space
[/LIST]
However, I am aware that both Ubuntu and BackTrack will require several (logical?) partitions within these main partitions.

So, my question to you is;
[LIST=1]
[*]**How many partitions (and of what type - e.g. normal, extended, logical) should I have, and of what size each should be (remember overall disk space is 640GB), so as to allow Ubuntu and BackTrack to run comfortably?**
[*]**What tool should I use to do the partitioning, from what operating system, and how?**
[/LIST]

Please bare in mind - I use Windows XP Media Centre Edition on a Dell Inspiron 1501 mainly. It is likely that I will partition from this computer (laptop) using either Windows, or Ubuntu (as you will specify), and install Ubuntu & BackTrack from this computer, although I may use my EEEPC to avoid loosing important data by selecting the wrong drive.

Please specify as much basic and complex detail as possible - I'm a perfectionist, and until I feel 200% confident with that I'm doing, and am certain I understand the process correctly, I'll do _nothing_!

Thank you very much, in advance.

Sirkey.

---

### Post by nhasian on 2010-06-27
actually your partitions dont need to be very complicated.  you dont even need to create an extended volume.  I would suggest you 4 primary partition:

Partition 1) EXT4 for Ubuntu
Partition 2) EXT4 for Backtrack
Partition 3) Swap
Partition 4) storage space.  if you plan on using this storage space in windows than you'll want NTFS.  if you will only use this storage space in linux then EXT4.

You can create all the partitions by booting to the Ubuntu LiveCD and going to System-> Administration-> Partition Editor (gparted)

as for the sizes thats up to you.  i dont know what your requirements are.  swap should be the same size as the amount of memory in your computer.  my ubuntu installation has never exceeded 4 gigabytes (excluding my private data of course) most people will recommend 15-20 gigs to give you room to grow.  you've got a lot of disk space to work with which is nice.  let me know if you have any further questions.

---

### Post by Sirkey on 2010-06-27
Excellent! Thanks for the quick answer too!

Two technical questions first;
[LIST=1]
[*]**What does `EXT4` mean?** I'm guessing it's a drive format, as I know what NTFS is. **What are the differences between EXT4 and NTFS?**
[*]**Is `swap` the same as (or similar to) RAM?**
[*]**Will each operating system create logical partitions within the primary partitions you listed?**
[/LIST]

Would the following sizes be sensible?
[LIST=1]
[*]Ubuntu - 20GB
[*]BackTrack - 20GB
[*]Swap - 5GB
[*]Storage space - 595GB
[/LIST]

...or am I giving too much to BackTrack - I'm not sure how much it would need, perhaps I should consult its website?

I will be planning to use the storage space with Windows & Linux, so I shall make it NTFS.

Oh, and here's another question;
**Will gparted format the disk when partitioning?**

Thanks again!

~ Sirkey.

---

### Post by nhasian on 2010-06-27
> **Sirkey said:**
> 
**What does `EXT4` mean?** I'm guessing it's a drive format, as I know what NTFS is. **What are the differences between EXT4 and NTFS?**
[*]**Is `swap` the same as (or similar to) RAM?**
[*]**Will each operating system create logical partitions within the primary partitions you listed?**


EXT4 is the modern filesystem for linux. [http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

at least until ubuntu switches to [Btrfs]("http://en.wikipedia.org/wiki/Btrfs") possibly as early as Ubuntu 10.10 <fingers crossed>

also here's info on the [SWAP partition]("https://help.ubuntu.com/community/SwapFaq")

dont stress too much about the partition sizes.  if later you decide backtrack doesn't need that much space you can resize it in gparted.  and yes it will be formatted when the partitions are made in gparted.

---

### Post by Paqman on 2010-06-27
> **Sirkey said:**
> 
[*]Swap - 5GB


Probably way too big. That's not a problem, it's just a waste of space.

The only time you'd need a really big swap partition is if you have tons of RAM and want to use hibernation. When you hibernate the contents of your RAM is copied into your swap partition, so it has to be at least as big as your RAM.

If you don't need to hibernate then your swap doesn't need to any bigger than about 1GB, especially if you have plenty of RAM.

One thing to be aware of: You can only have 4 primary partitions on a drive. If you need more than that, put some or all of your non-NTFS/Windows partitions inside an extended partition.

---

### Post by Sirkey on 2010-06-27
> **nhasian said:**
> dont stress too much about the partition sizes.  if later you decide backtrack doesn't need that much space you can resize it in gparted.  and yes it will be formatted when the partitions are made in gparted.

So, if I install BackTrack, Ubuntu, etc, etc, and get everything working nicely, and then decide to reduce my BackTrack partition size, I will need to reinstall BackTrack because gparted formatted that partition, _or_ I'll need to reinstall **everything** on the drive, because all 640GB will be reformatted? Is there a way to change the partition size without having to go through that rigmarole?

> **Paqman said:**
> Probably way too big. That's not a problem, it's just a waste of space.

The only time you'd need a really big swap partition is if you have tons of RAM and want to use hibernation. When you hibernate the contents of your RAM is copied into your swap partition, so it has to be at least as big as your RAM.

If you don't need to hibernate then your swap doesn't need to any bigger than about 1GB, especially if you have plenty of RAM.

I'm not sure how much RAM the machines I'm planning to use will have. Not very much, I expect, but I think 5GB is a safe amount, and it's not like I'm going to be running out of space in the next few millennia! =P But thanks for the advice! =D

Thanks for the quick and useful replies again, gentlemen!

~ Sirkey.

---

### Post by Paqman on 2010-06-27
> **Sirkey said:**
> Is there a way to change the partition size without having to go through that rigmarole?


You can resize any partition in Gparted without having to reinstall, it's only creating a new partition that formats it. You can't resize partitions while they're in use though. The easy way around that is to boot up into the Ubuntu LiveCD and run Gparted from there.

---

### Post by -kg- on 2010-06-27
I'm glad I ran across this thread!

First thing I will say is, read on the pages in the link in my signature block.  This will give you a basic understanding of partitions and partitioning operations, with screen shots.

[COLOR="Red"]------------------------------------------------------[/COLOR]
[COLOR="Red"]ATTENTION!:[/COLOR] In reading and commenting on the various comments, I noted something.  In a default installation, the installer will install the GRUB bootloader in the MBR of the ***_default boot drive_*** of the computer you're making the installation from.  In this case, it would be your internal hard drive where Windows resides.

In most cases this is perfectly acceptable.  GRUB will automatically detect all OSes installed (including Windows) and include them in the menu.  However, I noted your statement:

> I'm not sure how much RAM [COLOR="Red"]the machines I'm planning to use[/COLOR] will have.

This tells me that you might be planning to use the drive to boot from more than one machine.  If you are, you ***do not*** want GRUB to install on the local machine - you want it to install in the MBR of your External drive!  Then on every machine you boot to (and hopefully they're not so old that they can't boot from a USB device) you can select to boot from that drive, and GRUB will be there to boot with.

I don't want to make this post super-big, so if that is what you intend, post, and I or someone else will help you with the installation of GRUB in the MBR of the External drive.
[COLOR="Red"]------------------------------------------------------[/COLOR]

Now on to the comments:

> actually your partitions dont need to be very complicated. you dont even need to create an extended volume. I would suggest you 4 primary partition:

Actually, especially since you don't intend to install Windows on it, I would suggest making the whole volume an extended partition.  Linux will install into and run from a Logical partition, and if you desire your Windows installation to access the storage space, Windows will access Logical partitions (as long as they're in the correct format)...they just won't (generally) run from one.

There's a good reason for making the whole drive an Extended partition.  Presently, you only need 4 partitions in total.  But what if you decide you'd like to try another Linux distribution in the future?  What if you decide that you would like a separate "/home" partition, or other partitions for various reasons?  You'd have to jump through hoops trying to do so (though it *can* be done).

If you encompass the whole drive in an Extended partition, you won't have to worry about the "4 - Primary Partition" limit at all, and can create as many partitions as you want or need (there *is* a limit, but it's outrageous and you'll likely never run up against it!) without jumping through hoops.

> One thing to be aware of: You can only have 4 primary partitions on a drive. If you need more than that, put some or all of your non-NTFS/Windows partitions inside an extended partition. 

As I said above, Windows will access a logical partition.  You can create an NTFS partition inside an Extended partition (a Logical partition) and Windows will access it.

> Oh, and here's another question;
Will gparted format the disk when partitioning?

Yes.  See the tutorial in my signature block.

<Edit> Upon re-reading this post, I felt I may have misunderstood this question, so I will elaborate:

Yes, GParted is ***capable*** of formatting a partition when it is created, or re-formatting an existing one.  However as for formatting the "disk" (are you referring to the whole hard drive here?), no it will not.  A hard drive cannot be formatted...only a partition, either upon creation (to the file system type you specify) or upon a ***specific command*** to format an existing one.  You can even create a partition and leave it unformatted (called RAW).

GParted ***will not*** delete everything on the whole hard drive wholesale and reformat everything; not without a *_series_* of *_specific_ _commands_* to do so.  I just wanted to make that clear, if that was the intent of the question.

> So, if I install BackTrack, Ubuntu, etc, etc, and get everything working nicely, and then decide to reduce my BackTrack partition size, I will need to reinstall BackTrack because gparted formatted that partition, or  I'll need to reinstall everything on the drive, because all 640GB will be reformatted? Is there a way to change the partition size without having to go through that rigmarole?

No, GParted will shrink or expand a partition without formatting it.  You don't need to delete/re-create the partition in order to do so.  Again, read the tutorial link in my signature block.

> I'm not sure how much RAM the machines I'm planning to use will have. Not very much, I expect, but I think 5GB is a safe amount, and it's not like I'm going to be running out of space in the next few millennia!

Exactly! :p

5 GB doesn't sound outrageous to me, especially considering the amount of space you have.  If one of the computers you have have massive RAM, you'll be good to go, and if you find you don't need that much (and just ***must*** have a couple more GB of space! :p ) you can shrink the swap partition without problem.

> But thanks for the advice! =D

Actually, these *are* good things to learn and know!  You never know; in the future you may find need to install Ubuntu on a machine with limited resources, where every GB of space you can squeeze out of it is critical.  Then you'll know these things and be able to make those partitioning decisions without resorting to (possibly) hours of research.

So, you're welcome!

:lolflag:

---

### Post by Dustin2128 on 2010-06-27
I'd not give more than 3GB to a swap partition and you only need your two OS (and one storage) partitions and a 1-3GB swap. I'd recommend ext3 over ext4 because in my experience it's a bit more *stable.* Also the poster above me was correct, if you use the drive on multiple computers GRUB *must* be on the drive, I know from experience #-o.

---

### Post by oldfred on 2010-06-27
You also do not have to format the entire drive if you are not sure. Just make sure the extended partition is last, so you can expand it and add partitions. You then can easily expand the last partition or add additional partitions if desired. I like to have an extra 20GB partition ot two for another install of Ubuntu or testing the next verison or keeping the last version as an alternate to boot.

I would have at least one primary partition. There are a few BIOS that will not let you boot unless it sees a boot flag on a primary partition (assumes windows). Grub does not use a boot flag. 

No matter what scheme you use, you will find with your own use that you will have certain data needs and what something different after a while. For me it was three years and then a new drive that gave me additional space for new choices.

---

### Post by Sirkey on 2010-06-29
> **-kg- said:**
> I'm glad I ran across this thread!
 
First thing I will say is, read on the pages in the link in my signature block. This will give you a basic understanding of partitions and partitioning operations, with screen shots.
 
I have done now, and it was a very useful link. I'm feeling a lot clearer now. Thanks!
 
> **-kg- said:**
> ...This tells me that you might be planning to use the drive to boot from more than one machine. If you are, you ***do not*** want GRUB to install on the local machine - you want it to install in the MBR of your External drive! Then on every machine you boot to (and hopefully they're not so old that they can't boot from a USB device) you can select to boot from that drive, and GRUB will be there to boot with.
 
I don't want to make this post super-big, so if that is what you intend, post, and I or someone else will help you with the installation of GRUB in the MBR of the External drive.
 
That **is** what I intend. I **do** want GRUB to install on the _External_ drive.
But I've got some questions about GRUB; My current understanding (from the context in which people use the word/name, more than any research specificially into GRUB) is that GRUB is required to boot any OS, and is therefore in the MBR of all disks containing OS's. Therefore, if I _don't_ install GRUB on the MBR of my external disk, will the computers I'm booting onto be able to use the GRUB installed within their internal drives to boot Ubuntu from my external drive?
I've got a feeling GRUB may be a Linux only thing? Either way, I'd like to know more about GRUB! =D
 
> **-kg- said:**
> Actually, especially since you don't intend to install Windows on it, I would suggest making the whole volume an extended partition...
 
Since reading the article within your signature, I'm very much inclined to agree with you! I think that's what I'll do then - make all 640GB of the drive an extended partition, containing as many logical partitions as required (which I will come onto shortly).
 
> **-kg- said:**
> [SIZE=1]<Edit> Upon re-reading this post, I felt I may have misunderstood this question, so I will elaborate:[/SIZE]
 
[SIZE=1]Yes, GParted is ***capable*** of formatting a partition when it is created, or re-formatting an existing one. However as for formatting the "disk" (are you referring to the whole hard drive here?), no it will not. A hard drive cannot be formatted...only a partition, either upon creation (to the file system type you specify) or upon a ***specific command*** to format an existing one. You can even create a partition and leave it unformatted (called RAW).[/SIZE]
 
[SIZE=1]GParted ***will not*** delete everything on the whole hard drive wholesale and reformat everything; not without a *_series_* of *_specific_ _commands_* to do so. I just wanted to make that clear, if that was the intent of the question....[/SIZE]
 
[SIZE=1]...No, GParted will shrink or expand a partition without formatting it. You don't need to delete/re-create the partition in order to do so. Again, read the tutorial link in my signature block.[/SIZE]
 
Thanks! I definitely understand this after reading the tutorial in your signature block!
 
> **Dustin2128 said:**
> ...I'd recommend ext3 over ext4 because in my experience it's a bit more *stable...*
 
Please explain! =D
 
> **oldfred said:**
> ...I would have at least one primary partition. There are a few BIOS that will not let you boot unless it sees a boot flag on a primary partition (assumes windows). Grub does not use a boot flag...
 
I'm slightly confused now. Are you saying that if I wanted to boot *Windows* I'd need to have a primary partition on the drive, but as I'm _not planning to install or boot Windows_ from my new external drive, there's no need to have a primary partition?
 
 
Thank you all very much - you've all cleared up a lot of things in my mind, especially -kg-!
 
 
 
 

However, I still have a few questions;[LIST=1]
[*]Is it at all possible to cause degredation to my drive by fiddeling with the partitions a lot?
[*]**Could I have some basic information about GRUB? **(I already asked for that earlier in this post).
[*]**Could I have some basic information about _fragmentation_?**
[*]**Could someone clarify if the following partitioning scheme would be acceptable? **I just want to make sure I've understood everything.
[/LIST]Bare in mind; I plan to make the whole drive an extended partition, so all partitions listed below will be **logical**.[LIST=1]
[*]Ubuntu - 20GB - EXT4
[*]BackTrack - 20GB - EXT4
[*]Swap - 5GB - Linux Swap *[SIZE=1](is that a filesystem type?)[/SIZE]*
[*]Storage - 595GB - NTFS
[/LIST]I am aware that Windows will not be able to read the EXT4 & *Linux Swap* partitions partition (1, 2, & 3), however it _will_ be able to read the NTFS partition (4).
 
 
I think that's all the questions I've got so far! =D
 
Thanks again, gentlemen!
 
~ Sirkey.

---

### Post by oldfred on 2010-06-29
I am saying that the BIOS is smarter and assumes you are going to boot windows. So it will not even let booting start without seeing a boot flag on a primary partition. I have seen some with Intel motherboards with this issue.

Your partition scheme will work. Just be aware as you use it you may want to change later on. Some flexibilty for future change is often good unless you think you will buy another drive by that time.

General info:
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Herman has a huge site with lots of info on dual booting, grub, grub2, computers, and other info. For beginners it may be overkill but if you want to learn a lot:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Fragmentation is a windows/NTFS format issue. It does not apply in EXT type formats unless you are to the point of running out of space.
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

---

### Post by -kg- on 2010-07-02
> **oldfred said:**
> I am saying that the BIOS is smarter and assumes you are going to boot windows. So it will not even let booting start without seeing a boot flag on a primary partition. I have seen some with Intel motherboards with this issue.

Hmmm...I have an Intel motherboard on this laptop, and have installed ubuntu on other machines using Extended/Logical partitioning schemes, but have never had the problem.  This is interesting to note.  I assumed that it was older BIOS that you were talking about.  I wonder if Intel has BIOS firmware that would address that problem?

Some interesting links in your post, though.  I'll avail myself of some of that information.  It's good to have links to information and I think I'm going to have to rearrange my Bookmarks so that I have a separate folder for information to use with these (and other) forums.

> Since reading the article within your signature, I'm very much inclined to agree with you! I think that's what I'll do then - make all 640GB of the drive an extended partition, containing as many logical partitions as required (which I will come onto shortly).

It won't hurt anything, since you're fresh installing these installations.  Install one, using your partitioning scheme, then put the drive on every machine you intend to use it on.  If one or more won't boot to it, then you'll just have to re-partition it, make a primary partition, and make the rest Extended/Logical.  If it works on all your machines, you're in like flint.

For your convenience, though, make sure you install the OS that you want to have control of GRUB (in the MBR of the external drive) last.  That way, you can boot into each installation from the external drive, make sure it installed correctly, and make the next installation.  Of course, if you install the control OS first, you can just have the other one install it's GRUB into the ***_partition_*** that the OS will reside in, then boot into the other and run "sudo update-grub" in the terminal (of course, if you want BackTrack to control GRUB, you'll have to become (or already will be) superuser in order to do so.

> My current understanding (from the context in which people use the word/name, more than any research specificially into GRUB) is that GRUB is required to boot any OS, and is therefore in the MBR of all disks containing OS's.

No, not necessarily.  For instance, I have two hard drives in this laptop and 4 separate OSes installed on it (Ubuntu, Fedora, OpenSUSE, and oh yes...Vista too).  Vista and Fedora are installed on the primary hard drive, Ubuntu and OpenSUSE on the secondary.  I only have GRUB on the primary hard drive.  While there are two bootable OSes on the secondary, I don't have GRUB in its MBR...it's not necessary.  If I *did* install a GRUB to the secondary hard drive and wanted to boot using that, I would have to select that hard drive in the menu I pull up using F-12 during the booting process, before I ever get to the GRUB menu.

At the very beginning of booting this computer, I get the Toshiba Splash screen, and at the bottom of this screen is two selections.  One F-key combo will take me into BIOS, and F12 will take me to the alternate boot devices screen.  From that I am able to select either hard drive, the optical drive (which is what I have to do to boot to the CD drive) and external USB drives.

With some BIOSes (and most all older ones) you will need to go into BIOS to change the boot sequence.  This is the part of BIOS where you select what drive BIOS is to check first, second, third, etc. for a boot loader.  A lot of older BIOSes are set to check the floppy, the CD drive, and then the (or either) hard drives, as well as USB devices, for those that support it.  You can change this to search any device in any order and some use this to speed up the boot process by having BIOS check the hard drive first.  On these computers, you will need to change the boot order to check the external USB drive first when you wish to boot to the installation(s) installed on it, and is why you really want to put GRUB in the MBR of the external drive.

> Therefore, if I don't install GRUB on the MBR of my external disk, will the computers I'm booting onto be able to use the GRUB installed within their internal drives to boot Ubuntu from my external drive?

Depends on whether it is actually GRUB or another boot loader (like the Windows bootloader).  If you have GRUB in the MBR of your internal drive, you can cause it to detect your external drive by booting on to the OS on your internal drive and running update-grub in the terminal.  If it is the Windows bootloader, it's a bit more complex than that, and impossible in some cases.

In any case, you would have to update GRUB on your internal drive to detect the OS on the external drive.  This would have to be done on every computer you intend to use the external on.  Much easier to install GRUB in the MBR of the external drive and choose to boot it from BIOS or the boot menu.

>  [QUOTE]Originally Posted by Dustin2128  View Post
...I'd recommend ext3 over ext4 because in my experience it's a bit more stable...
Please explain! =D[/QUOTE]

Ext4 is a newer implementation of the ext(x) filing system.  As such, it is still somewhat experimental, though it's becoming more stable by leaps and bounds, with more software being re-written to use it correctly.  I use it and have had no problems with it; others have had problems.  Ext3 is fine.  Lucid (10.04) uses ext4 by default in the installation; Karmic uses ext3.  You can elect to use other than the default in both by choosing the "Create Partitions Manually" option and selecting the file system of your choice.

Think I've answered everything that wasn't answered by others.  Enjoy, and if you have any more questions, just ask!

---

### Post by Sirkey on 2010-07-04
Thank you both - I am now clearer about both Grub, and fragmentation.

I have also gone ahead and done the partitioning, now that I have the drive (and believe me, it's very shiney! :D)
Here's what it looks like in GPartEd:

[IMG]http://i6.photobucket.com/albums/y227/WNxpuffin125/Linux%20Things/Screenshot--dev-sdc-GParted.png[/IMG]

I couldn't format my *Storage* partition to NTFS, because it was grayed out, but not to worry, I'm sure Fat32 will suffice.
Also, although I typed 20000 into the box, it doesn't say that the partitions for Ubuntu and BackTrack are 20GB. _Where has my 0.47GB gone?_

Anyway, now for the burning questions;

**When installing BackTrack and Ubuntu (BackTrack first), how do I tell them to install Grub to the external drive, and how do I point them to my swap partition?**

I already have the latest Ubuntu and BackTrack ISO's, and I plan to install the Live CD of each (_not_ at the same time) onto a 2GB memory stick for installation (saves on CD's), using UNetbootin.

Thanks for everything, once again! ;)

~ Sirkey

---

### Post by -kg- on 2010-07-04
> **Sirkey said:**
> I couldn't format my *Storage* partition to NTFS, because it was grayed out, but not to worry, I'm sure Fat32 will suffice.

It will, unless you try to store greater than 4 GB files (like some movie files).  In that case, you might want ntfs.  I'm pretty sure that the [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php") will format a partition as ntfs, but to create a Windows partition formatted to ntfs, there's no better tool to use than....Windows! :P

Just boot into Windows, launch Partition Manager, select the Storage partition, and format it to ntfs.  You'll have an ntfs partion with no problems in the making!

> **Sirkey said:**
> Also, although I typed 20000 into the box, it doesn't say that the partitions for Ubuntu and BackTrack are 20GB. _Where has my 0.47GB gone?_

It has to do with the difference between GB (1 GB = 1000 MB) and Gib (1 GiB = 1024 MB).  The same goes for MB to KB and B to KB.  I think they should adopt one standard and stick with it, but that's just me.  In any case, that's where your .47 GB went.

> **Sirkey said:**
> Anyway, now for the burning questions;

**When installing BackTrack and Ubuntu (BackTrack first), how do I tell them to install Grub to the external drive, and how do I point them to my swap partition?**

Not too hard.  Since I've never dealt with BackTrack and don't know how its installer is set up or handles things, you'll have to figure that out when the time comes, but I can walk you through the procedures with Ubuntu.

Since you've already created the partitions you're going to use, you'll need to use the "Manual Partitioning" selection at the appropriate place in the installation process.  When you get to that point, You'll see a list of all the hard drives connected to the computer, your external along with it, and the partitions and free space existing on each.

You need to select the appropriate partition (in this case, sdc5...I don't know whether the label will show up in the installer) and then mark the mount point for that partition.  You can reformat it...it doesn't really matter, and won't take much additional time...but it is important to mark the mount point as "/", which is root.  You shouldn't need to mark the mount point of swap...that's automatic.

In addition (I don't know whether this will work...probably will), you might want to mark a mount point for your Storage partition, as well.  If I remember correctly, there is a "/storage" mount point among the selections, and if not, you can create whatever mount point you want.

NOTE:  You will want to remember the drive designation of your external drive.  In this case, it is "sdc", but you'll need whatever it is during the installation procedure.

After you have marked the mount points of your partitions, you click through and enter the appropriate information in the subsequent screens, until you come to the very last screen, which tells you what changes will be made to your hard drive.  At the bottom right of the screen is a button labeled "Advanced."  Clicking on that allows you to control where GRUB is installed.

Default is the MBR of your first (internal) drive, but you want to set it to install in the MBR of your external drive (sdc, in the above case).  Be ***_sure_*** that you're installing it in the MBR and not a partition!  It should be sdc, and not sdc1, or sdc2, etc.

Once the installation is complete, you will then need to boot into the installation to complete the installation process and update the system, install drivers and software, etc.  When you boot into the installation, you will have to select the boot drive to boot to, of course...either through "F(2-12, whichever your computer uses)" boot selection or through Boot Sequence in BIOS.

That's all there is to it.  As I said, not having any experience with BackTrack, I can't tell you how it's installer handles it.  I could download it and run through its installation procedures and find out, but now that you know what you're looking for, you can likely figure it out for yourself.

It seems kind of interesting, so I'm downloading it now.  If you can't figure it out, I'll soon know what procedures to use.  Just don't allow BackTrack to install unless you ***know*** that it's going to install GRUB on your external drive.  While it can be corrected, it's kind of a PITA, and you won't be able to boot that computer without the external drive connected until it's corrected.

---

### Post by -humanaut- on 2010-07-04
I have a 250Gb harddrive and my partitions are like this:

ext2 /boot 1Gb (excessive I know but there where recent problems with have 100mb)
ext4 /(root) 20Gb
(swap) 5Gb
ext4 /home 220* Gb

*=rest of the hdd.

also the XFS filesystem is really nice I used it for a long time when I was running the 64Bit edition as my primary O.S. (kubuntu)

---

### Post by -kg- on 2010-07-05
A quick note:

I've downloaded and burned the Backtrack .iso.  Then I found the following page:

[http://www.backtrack-linux.org/tutorials/backtrack-hard-drive-install/]("http://www.backtrack-linux.org/tutorials/backtrack-hard-drive-install/")

If you scroll down the page to the last screen pictured in the installation process, you'll note that there is an "Advanced" button on the last page.  I assume that this serves the same function I described for Ubuntu, but I'll run through the installation procedure to make sure.  I want to install it and try it out anyway.  It seems to be quite interesting.

---

### Post by -kg- on 2010-07-05
OK, I've installed it and can confirm that the "Advanced" button is indeed where you select where to install GRUB, or not install it.  I also found out that BackTrack is based on Ubuntu 8.10 Intrepid, which is the only distro which I couldn't get working right on this computer.  I can't get it working right in this case either...I can't get the Network Manager to come up at all to configure (or attempt to configure) the Wireless.  Oh well...

Others have had luck with it, so you might, as well.  You will want Ubuntu to own the GRUB in the MBR, though.  Being based on Intrepid, BackTrack doesn't support the ext4 filesystem, and as such its GRUB isn't likely to be able to boot an OS on an ext4 partition.  It won't even mount the partitions.

Such is the case with the GRUB of a number of distros , like Fedora, for example.  You can use ext4 for the root partition, but you have to make a special /boot partition formatted to ext3 in order for its GRUB to be able to boot it.  Why they didn't use the patched Legacy GRUB that Karmic did, I don't know, but even the latest (F13) is this way.  Oh well, as long as I have Ubuntu and GRUB2, I don't have to worry about such things.

---

### Post by Sirkey on 2010-07-06
> **-kg- said:**
> It will, unless you try to store greater than 4 GB files (like some movie files).  In that case, you might want ntfs.  I'm pretty sure that the [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php") will format a partition as ntfs, but to create a Windows partition formatted to ntfs, there's no better tool to use than....Windows! :P

I've come up with my own solution. As I found that NTFS cannot be read by Ubuntu and BackTrack, I decided to create a FAT32 and NTFS partition, allowing a space for both Windows and Linux to access, and a space where 4GB+ files can be stored. I had to do that by downloading a plugin for GPartEd, so that NTFS formatting was supported. You'll see what I've done later on in this post.

> **-kg- said:**
> It has to do with the difference between GB (1 GB = 1000 MB) and Gib (1 GiB = 1024 MB).  The same goes for MB to KB and B to KB.  I think they should adopt one standard and stick with it, but that's just me.  In any case, that's where your .47 GB went.

I have recalculated my numbers, and got my 0.47GB back when calculated in binary, as you'll see below.

Here's my new partitioning scheme;
You'll notice that BackTrack is now EXT_3_, because it wanted to reformat it to EXT3, because it doesn't know about EXT4 yet, as you've mentioned - but this is no problem.

[IMG]http://i6.photobucket.com/albums/y227/WNxpuffin125/Linux%20Things/Screenshot-GPartEd-2.png[/IMG]

If you look down the label column, you'll notice that my `Storage` partition is labelled entirely in uppercase, and my `Swap` partition has no label. This is quite an annoying problem. No matter what I label my `Storage` partition, it comes out entirely in uppercase, no matter what case I input my desired label. This casing problem does _not_ affect the label of the drive in the file browser, however.
As for the `Swap` partition, the label button was grayed out, although you'll notice I _was_ able to label it before...any suggestions?

> **-kg- said:**
> ...I can't get the Network Manager to come up at all to configure (or attempt to configure) the Wireless.  Oh well...

Others have had luck with it, so you might, as well...

From my mildly limited experiences with BackTrack before, I know that in order to mount a device, or connect to the internet, one must input a minimum of three separate commands into the terminal! None the less, I got the internet working on BackTrack, and in Ubuntu (although it took some tricky driver installations to get it working in Ubuntu).

> **-kg- said:**
> You will want Ubuntu to own the GRUB in the MBR, though...

In relation to GRUB, I've got a small problem - everything works...but I want it to look slightly different. Note the below picture;

Click [here]("http://i6.photobucket.com/albums/y227/WNxpuffin125/Linux%20Things/PICT0001.jpg") to see the image - it was a little large, so I thought I'd best not just dump it here.

As you can see, Ubuntu is listed at the top, and Ubuntu is again listed further on down (sdc6). I am aware of which is Ubuntu (the top one), and which is BackTrack (Ubuntu 8.10 - sdc6).
It is possible to rename Ubuntu 8.10 to BackTrack? That would save all confusion!

Here's a third little problem:

[IMG]http://i6.photobucket.com/albums/y227/WNxpuffin125/Linux%20Things/Screenshot-FileBrowser.png[/IMG]

My partitions are sometimes mounted twice, as shown. However, if I click on the wrong partition, nothing happens. In order to see my `Storage` partition, for example, I must click on the correct drive (from the two which call themselves `Storage`) in the above picture, otherwise I get nothing. Also, I cannot unmount the `dummy` drive that appears, as it were. Any ideas as to why this is happening? It doesn't happen _all_ the time, either...only after a while...

Other than that, I believe there to be no problems (or if there are, I've already forgotten about them...but that wouldn't be hard). I've spent a proportion of today installing things on Ubuntu, and I'm so happy with it, I'm using it now to write this post, take screenshots, and upload them to PhotoBucket! =D

~ Sirkey

---

### Post by rewyllys on 2010-07-06
> **Sirkey said:**
> . . . . As I found that NTFS cannot be read by Ubuntu and BackTrack, I decided. . . .
Sirkey,

I'm glad you started this thread, as I've found it both interesting and instructive to me; and I commend you on your desire to be "200 per cent" certain of what you were getting ready to do.

Just two comments: 

First, Ubuntu CAN read NTFS files -- just use the Synaptic Package Manager to install the ntfs-3g driver (and whatever additional files SPM wants to add with it).

Second, I *strongly* recommend that you add a separate partition on which to place your /home directory.  If you have such a partition, then you can re-install the Ubuntu OS if you want or need to. 

Having a separate /home partition saved me much stress and hard work when it happened to me that I messed up the upgrade from 9.10 to 10.04, and wound up having to re-install 10.04 from scratch.  But my personal files and data, being in my separate-partition /home directory, were completely unaffected by my having messed up 10.04 the first time.

---

### Post by oldfred on 2010-07-06
I believe everything mounted in /media or /home is shown again either as the file size or the label in caps. You can see it mounted the the symbol next to it and then cannot mount it again.

I avoid it by mounting elsewhere and linking it in.
# Entry for /dev/sda7 :
UUID=defec4d7-3e36-4938-b5de-b2016b2dee27  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2  

In /home I run these:
ln -s /usr/local/fred/data/Music
ln -s /usr/local/fred/data/Documents
ln -s /usr/local/fred/data/Pictures
etc

Someone else suggested this:

Type sudo su
Type echo "LABEL=Storage /mnt/Storage vfat utf8,umask=007,uid=1000,gid=46 0 0" >> /etc/fstab
Type sudo mount -a

What should happen is this:

The mount point in /mnt will not produce an icon on the desktop
umask=007 will give the owner and group read/write access to the mountpoint
uid=1000 will make you the owner
gid=46 will make group plugdev - and all users are part of plugdev so all users will have read/write access

---

