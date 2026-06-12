---
title: "Dual boot, partitioning, am I on the right track?"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by veroslav on 2011-02-04
Hi,

I am about to install Ubuntu 10.10 alongside Windows 7 on my new computer and I need to check that I have understood the process and get some help and tips from you guys.

Currently, the computer has two partitions, one for Windows 7 (1,13 TB) and the other for the HP recovery software (12 GB).

This is how I intend to do it:
1. After burning the recovery DVD:s, delete the recovery partition (What tool do I need in order to do this? Does it come installed with Windows?)
2. Defragment the Windows partition
3. Shrink the Windows partition to about 100 GB (I want to use the rest for Ubuntu, and again, what tool should I use to shrink the partition and is it installed with Windows?)
4. Run the installation from Ubuntu Live CD (using "Manual partitioning"-option) and "use" the remaining space that is left after shrinking the Windows partition (not sure how this is done, I will probably need more help when I get there)

Am I on the right track here? I just want to be 100% sure before I do anything :)
Is there anything I need to take a special care of?

Thanks.

Kind Regards,
V

---

### Post by Paqman on 2011-02-04
> **veroslav said:**
> 
This is how I intend to do it:
1. After burning the recovery DVD:s, delete the recovery partition (What tool do I need in order to do this? Does it come installed with Windows?)


I believe Win7 does come with a disk partitioning tool, yes.

> 2. Defragment the Windows partition
3. Shrink the Windows partition to about 100 GB (I want to use the rest for Ubuntu, and again, what tool should I use to shrink the partition and is it installed with Windows?)

You can use the same Windows partitioning tool as you used in the previous step. One thing to be aware of is that partitioning operations can take a long time to complete, so just let it work away.

> 4. Run the installation from Ubuntu Live CD (using "Manual partitioning"-option) and "use" the remaining space that is left after shrinking the Windows partition (not sure how this is done, I will probably need more help when I get there)

It's not compulsory to use manual partitioning for this unless you want to set up a more complicated partitioning scheme (such as installing your /home to a dedicated partition). 

If you leave a large unpartitioned space on the disk one of the options the installer will present to you is to automatically partition and install to that space. The installer will create an extended partition in that space containing a small swap partition and a large EXT4 root partition. If that sounds good to you then i'd just go ahead and let it do all the work for you.

Don't stress too much about getting your partitioning perfect first time, you can always change it later. Do take a backup of your data on your Windows partition first though, just in case something goes wrong.

---

### Post by veroslav on 2011-02-04
Thank you for your reply.

Your method of automatic partitioning of the remaining disk space does sound a bit easier so I will go with that.

I have not dealt with partitioning before, is it 100% safe that the Live CD installer will be able to find the free space that is left after shrinking the Windows partition? Newbie as I am, I am worried of loosing that free disk space for ever :confused: Where does it take place after shrinking the Windows partition? I guess it is still available, just not visible.

---

### Post by veroslav on 2011-02-04
Also, one more question:

when I want to remove the Recovery Partition, do I simply delete it in the Disk Partitioning application or do I have to "tell" Windows partition to reclaim the free space left after Recovery Partition has been removed?

Dumb questions I know, but I prefer to be 100% sure than to make a misstake as a result of only knowing 99% :)

/V

---

### Post by Paqman on 2011-02-04
> **veroslav said:**
> 
Your method of automatic partitioning of the remaining disk space does sound a bit easier so I will go with that.


Actually, I might have to backtrack on that one a bit. It's certainly *supposed* to work that way, but I vaguely recalled there being a problem bug in the installer that was causing problems, and found [this thread]("http://ubuntuforums.org/showthread.php?t=1622388") which seems relevant.

I've not got any experience of the new installer's behaviour (I always do manual partitioning) so someone else might want to clarify, but it looks like it might be better to do it manually for now?

> **veroslav said:**
> 
when I want to remove the Recovery Partition, do I simply delete it in the Disk Partitioning application or do I have to "tell" Windows partition to reclaim the free space left after Recovery Partition has been removed?


That will depend on where that partition was on the disk. If the recovery partition is located after the Windows partition then simply deleting it will do. If it's before the Windows partition, then you'll want to delete it then shift the Windows partition to the start of the drive, which will be slooooow.

---

### Post by veroslav on 2011-02-04
O boy, just when I was feeling more comfortable with the whole thing :(

Right, so I read through the bug report in the installer (I followed the link you posted) and it appears in deed that the only option I have is the manual partition, which I feel very uneasy with.

Like, how would I know how many and how big partitions to create when doing it this way?
I heard that it is common to have a partition for /home (might not be necessary as you said), a swap partition (that should be at least or twice the size of the RAM) and the rest is for Ubuntu itself. Does this sound OK?

But i guess that the steps I stated in my first post still apply (incl manual partitioning).

Can anybody else confirm that this is the case?

I appreciate the previous response I've got, didn't knew about the bug mentioned.

Thanks.

/V

---

### Post by veroslav on 2011-02-04
I am reading through the link posted above and it does contain some good info.
I will read it and try to digest what is written there first, then come back for more help.

Thanks again.

/V

---

### Post by Paqman on 2011-02-04
> **veroslav said:**
> 
Like, how would I know how many and how big partitions to create when doing it this way?
I heard that it is common to have a partition for /home (might not be necessary as you said), a swap partition (that should be at least or twice the size of the RAM) and the rest is for Ubuntu itself. Does this sound OK?


You will need to create a swap partition and a root partition. Your swap is small, 1GB is a good size, and if you want to be able to hibernate then it should be the same size as your RAM. The rest of the space can be an EXT4 partition with the mount point / (which is shorthand for root). That's all there is to it, it's actually pretty straightforward once you've done it a couple of times.

Creating a separate partition for /home is a great idea, but entirely optional. If you did decide to do so then your root partition only needs to be about 10GB or so, and give all the rest of the space to an EXT4 partition with the mount point /home.

One issue that you might want to consider: you can only have four primary partitions on a disk. The way to get around this is to put one or more partitions inside a container called an extended partition. You can have as many partitions as you like inside and extended partition, and Linux is quite happy booting and running from within one, so it increases your flexibility without having any downside. Again, this is entirely optional.

If you're nervous about partitioning then there is an option to skip it altogether. You can install Ubuntu to a virtual partition located on the Windows partition. It's called [Wubi]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer") and it'll get you up and running very quickly. It's not a virtual machine, it's a proper dual-boot, it just uses some on-disk trickery instead of actual partitions. Long-term a properly partitioned disk will be more stable and reliable, but Wubi is great in the meantime.

---

### Post by Quackers on 2011-02-04
There are a few more things to clear up, I would suggest.
Firstly, it is unusual for Windows 7 to only take one partition - especially if it came pre-installed. There are usually at least 2 partitions, and sometimes 3 or 4. Quite often, 2 of Windows boot files can be stored in the recovery partition.
This needs to be checked, as partitioning is not to be done lightly.
What is shown in the Windows disk management screen? (Start > right-click Computer > select Manage > in the left pane select disk management).
Post a screenshot if you're not sure.

Which version of Ubuntu are you planning on installing? 10.10 has the nasty bug in the installer, which can trash your Windows installation! Whereas the 10.04 (Lucid Lynx) installer, is the safest and easiest to use installer that I have ever used. It's worth thinking about.

If we can clear these questions up first, things may go much smoother :-)

---

### Post by veroslav on 2011-02-04
Thanks to both Paqman and Quackers for your useful replies.

I am currently at work and do not have access to my computer, but as soon as I am home, I will be glad to provide you with the screenshots you mentioned.

I am planing to install 10.10 as it is newer, but I guess I wouldn't have much against going with 10.04 either (already running it on my laptop) if it will make the installation safer and smoother.

I am not in a hurry and would like to do this properly so I'll let it take its time.

As I said, as soon as I am home I will post the disk details as requested.

Thank you again.

/V

---

### Post by mastablasta on 2011-02-04
Quackers made some good points. I would only like to add that if recovery partition is not in the way then there is no need to delete it. I mean you have a huge enough disk and still having that parittion could help you later... just make sure first how many partitions you really have.
 
don't worry too much about partitions. even if you do it automaticly, you can always make new ones later.

---

### Post by mastablasta on 2011-02-04
> **veroslav said:**
>  
I am planing to install 10.10 as it is newer, but I guess I wouldn't have much against going with 10.04 either (already running it on my laptop) if it will make the installation safer and smoother.
 
 
/V
 
you can always upgrade to 10.10 (if you actually need to) after the install. ;-)

---

### Post by sanderd17 on 2011-02-04
> **Paqman said:**
> 
If you're nervous about partitioning then there is an option to skip it altogether. You can install Ubuntu to a virtual partition located on the Windows partition. It's called [Wubi]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer") and it'll get you up and running very quickly. It's not a virtual machine, it's a proper dual-boot, it just uses some on-disk trickery instead of actual partitions. Long-term a properly partitioned disk will be more stable and reliable, but Wubi is great in the meantime.

Wubi is only good for trying Ubuntu. You can easely erase wubi, but it's not stable. I've used it in my first month of ubuntu, than it crashed (wubi relies on windows, so it is possible that windows crashed) and I lost my data. After that, I installed a proper ubuntu (with automatic partitioning) which went well. When a next version came out, I installed it with manual partitioning which also went well by that time.

When you launch ubuntu from the CD, choose the option to try it and open gParted from one of the menus. There you will see what partitions you have and you should remember the configuration. e.g. note it down.

Linux partition names are differnet from windows. Windows gives letters to it (C: ,D: ...) , linux uses the name SDA for the first disk, SDA1 for the first partition on the first disk, SDA2 for the second partition on the first disk ... SDB for the second disk ...

When you install ubuntu, the update manager will say what partitions will be erased or changed (if you use manual partition), you need to check those names so that you don't erase important things.

---

### Post by veroslav on 2011-02-04
Finally, I am back at home and ready to continue. I've burned the recovery disks so now my windows installation is safe. I also downloaded and burned Ubuntu 10.10 64-bit Live CD, (verified MD5 and so on) this is the one I would like to install eventually.

So I tried the Live CD and everything looks good, the Internet connection is ok, the graphics.. 

Question 1: When trying the Live CD, I saw that the propriatery drivers were available for my video card. Is it possible to install and test these when trying the Live CD or do I need to really install Ubuntu first?

As requested, I've also captured the partition info in both gParted (from Live CD) and from Windows Disk Manager, here is how it looks like at the moment:

gParted output:

```
Partition    File System    Label        Size        Used        Unused        Flags
======================================================================================================
/dev/sda1    ntfs        SYSTEM        100 MiB        33.59 MiB    66.41 MiB    boot
/dev/sda2    ntfs        OS        1.35 TiB    36.16 GiB    1.32 TiB    
/dev/sda3    ntfs        HP_RECOVERY    12.88 GiB    11.29 GiB    1.58 GiB
unallocated    unallocated            1.40 MiB    --        --
```Windows Disk Manager output (I did my best to translate from Swedish):

```
Volume        Layout        Type        File System    Status            Capacity    Unused
===============================================================================================================
HP_RECOVERY(D:)    Simple        Standard    NTFS        OK(Primary partition)    12.88 GB    1.58GB
OS (C:)        Simple        Standard    NTFS        OK(System start, Swap     1348.29 GB    1348.11 GB
                                file, Crash dump, 
                                primary partition)
SYSTEM        Simple        Standard    NTFS        OK(System, Active,    100 MB        70 MB
                                primary partition)
```Question 2: What would you recommend the best partition set-up would be for running the Ubuntu 10.10 64-bit on this machine? I would prefer the simplest approach and avoid creating unneeded partitions. I dont really care about the HP_RECOVERY partition, if it is easier to leave it alone, I will gladly do that.

Question 3: I've got kind a confused when it comes to shrinkage of the Windows partition. As I've been reading, it appears that it can be shrinked both within Windows itself (some windows tool for this) and from gParted, when installing Ubuntu and selecting partitions). What is the best way to do it? I've heard that it is possible that Windows could become corrupt if it is shrinked directly from within Windows, but I am skeptic on this one.

I guess those are the questions I have at the moment. Could you please provide me some more partitioning tips based on the info I provided above? What should I do now?

Thanks in advance.

/Veroslav

---

### Post by Quackers on 2011-02-04
As a general rule, it is safer to use Windows tools to change Windows partitions and to use Linux tools to change Linux partitions.
Firstly, from within Windows I would recommend that you defragment the C: partition. Twice would be better.
Then from the Windows Disk Management console, right-click on the C: partition and select "shrink" from the menu. Then enter the amount of shrinkage required and click OK.
This will not take long to run.
When it finishes you should see the display change to include a new entry marked "unallocated space".
I would then reboot Windows more than once, to make sure it is happy about the change (Windows can be finicky about shrinkage, sometimes).

After that is done I would recommend that you boot from the live cd and run the installer, selecting "specify manually" on the partitioning screen.
At this point you can create an extended partition, occupying the whole of the unallocated space.
Then inside that extended partition you can create as many LOGICAL partitons as you want. 
For Ubuntu you should create a root partition, with a mount point of " / ", and, if required a separate /home partition, with a mount point of "/home" and a file system type of ext4. The size of these partitions depends on whether you have a separate /home partition. With no separate /home partition, all the space you wish to allocate to Ubuntu should be in the root (/) partition. 

With a separate /home partition, your root (/) partition can be just10GB or so (mine are about 12GB), then the rest of the space can be taken by your /home partiton - which is used for your user details, settings and config files.

You should also consider making a swap partition (no mount point). If you intend on using hibernate it should be slightly larger than the amount of ram available. If hibernation is not required a very small swap partition can be used (if you have at least 2GB of ram), or even none at all.

---

### Post by veroslav on 2011-02-04
Quackers,

I can't thank you enough, your last post makes sense and is very informative and detailed.
I get the feeling that I understand almost everything, if not all of it.

I will have to leave the actual work until tomorrow, as I feel quite tired at the moment and thus might make a mistake. I will notify you of my progress and I wonder if it is ok to ask more questions if any arise? As I said, I feel much more comfortable now, when you clearly specified what menu options that I should select and so on.

I really appreciate your kind help, thanks again.

Kind Regards,
V

---

### Post by Quackers on 2011-02-04
A wise move indeed :wink:
I wish I had made the same decision, more than once (whilst trying to recover something I'd over-written in my tiredness :-) ).
You should definitely ask first if you have any problems. Partitioning is a serious business and mistakes can cause a lot of work! 
I will hopefully be around here tomorrow, but there are many here who are vastly experienced and could give you advice.
In fact, there may be alternative suggestions made before then :-)

If you haven't done it already, you should leave a backup program running overnight to get everything recoverable - just in case!

---

### Post by rewyllys on 2011-02-04
Veroslav,

I'd like to urge you to use a separate partition for your /home directory.  

Doing so will let you make changes (including clean installs or re-installs) to your Ubuntu operating system without affecting your personal data, including the configuration data for the applications programs that you use.  The ability to do so has been a lifesaver for me!

---

### Post by veroslav on 2011-02-05
Good morning to you all!

Now I am ready to make the step and install Ubuntu.
Thank you for the tip about using separate partition for /home, rewyllys, I will do that.

What I have done so far, as suggested earlier:

1. Defragmented Windows 7 twice
2. Shrunk the Windows partition (C) to a half of the original size
3. Booted Windows twice to insure that it went ok
4. Inserted and booted Live CD, and this is how it all looks in gParted (see attachment)

How does it look so far? It looks as though there are five(!) partitions there, but I was told that four was the maximum?

To summarize, this is how I decided to do it:

1. Manual partition from Live CD after choosing Install Ubuntu
2. Use all of the unallocated space (689.5 GB) for ubuntu (not sure yet how I am going to create the extended partition, but I will ask again when I get there)
3. Inside this extended partition, I will create these logical partitions:
/ (root partition) (size ca 12 GB (is this enough, how can I know?), mount point (/), what should the file system type be, ext4, or is it set automatically?)
/home (mount point /home, file system type ext4, size = whatever is left after creating / (root) and swap partitions)
swap partition (do I need this? I've got 8 GB of RAM and dont need hibernate to work, how much swap do I need, if any?)

And I guess thats it, if somebody could just have a look at the above and confirm that is looks "sane" I will have a go and ask more questions and post screenshots if needed/available as I move along.

Thanks in advance.

Kind Regards,
Veroslav

---

### Post by Paqman on 2011-02-05
> **veroslav said:**
> 
1. Manual partition from Live CD after choosing Install Ubuntu
2. Use all of the unallocated space (689.5 GB) for ubuntu (not sure yet how I am going to create the extended partition, but I will ask again when I get there)


You simply click on the free space and create a new partition that takes up the whole thing. Instead of creating it as a "primary partition" you simply select "extended partition".

> 3. Inside this extended partition, I will create these logical partitions:
/ (root partition) (size ca 12 GB (is this enough, how can I know?)

Should be plenty. Only about 3-4GB will be used to start off, and you'd have to install a lot of stuff to get anywhere near 10GB. Having some free space helps it work more efficiently though.

> mount point (/), what should the file system type be, ext4, or is it set automatically?)

The default file system is EXT4, which is a good choice.

> /home (mount point /home, file system type ext4, size = whatever is left after creating / (root) and swap partitions)

Sounds good.

> swap partition (do I need this? I've got 8 GB of RAM and dont need hibernate to work, how much swap do I need, if any?)

That's a lot of RAM. You're highly unlikely to ever need any swap. I never touch swap on my 4GB system, even when I'm running VMs. Even with the default swappiness settings you'd need to have chewed up 4.8GB (!) of memory before your machine started swapping it to the disk. However your disk is bignormous, so having a 1GB swap wouldn't hurt. Up to you really.

---

### Post by veroslav on 2011-02-05
Thank you, Paqman.

I feel comfortable now and I will have a go now.
I'll keep you posted about my progress, I am very excited!

Regards,
Veroslav

---

### Post by veroslav on 2011-02-05
I am performing the installation and right now, I've chosen the
"Specify Manually" option. The attached screenshot shows how it looks.

If I understand it correctly, I will be installing Ubuntu on the "free space" device, right? And I would probably do this by clicking on the Add.. button in order to create new partition and then select "extended partition" from there?

Also, is the Boot Loader device specified correctly (/dev/sda/ ATA ST31500341AS(1.5 TB)? What does this mean? There are other choices I can choose from in the drop down box, is this one fine?

Thanks.

Regards,
Veroslav

---

### Post by veroslav on 2011-02-05
Sorry for spamming you with questions, I am a little bit unsure at the moment. This is the window that opens after clicking on the Add... button for the "free space":

CREATE PARTITION

Type for new partition: [] Primary [x] Logical
Partition size (MB) : <whole "free space">
Location: [x] Beginning [] End
Use as: Ext4 Journaling file system
Mount Point: [<various choices>]

What should I do first? I am unable to locate "extended partition" as told above?

Also, do I need to format the "free space" first? I saw the format checkbox being available for "free space", see the attachment in my previous post.

/V

---

### Post by Paqman on 2011-02-05
> **veroslav said:**
> 
If I understand it correctly, I will be installing Ubuntu on the "free space" device, right? And I would probably do this by clicking on the Add.. button in order to create new partition and then select "extended partition" from there?

Yep

> 
Also, is the Boot Loader device specified correctly (/dev/sda/ ATA ST31500341AS(1.5 TB)? What does this mean? There are other choices I can choose from in the drop down box, is this one fine?


/dev/sda is what Linux calls that disk (device SATA disk A). If you installed a second disk that would be /dev/sdb. The long string of stuff after that is the drive model number, in this case it looks like you have a Seagate Barracuda. 1.5TB is the size.

It's possible to choose exactly where to install the boot loader, but you don't need to do so. Just accept the default.

---

### Post by veroslav on 2011-02-05
Thank you for that Paqman, I understand, will leave it at default.

Could you also shed some light on my next question(s) please?
Not sure about where I can find the "extended partition" mentioned above and what kind of partition to create next.

Thank you.

/V

---

### Post by veroslav on 2011-02-05
Reading through the posts from earlier, I come to the conclusion that "extended partition" is probably the same as "Primary" partition in the "Create partition" window, and that I probably need to create such partition first, that takes up all of the "free space". Then I can create logical partitions by using the same method, but of course using "Logical" instead of "Primary" as the type for the new partitions.

One more thought/question: Suppose that I'm right about the above, would I keep Location of the new primary partition at the "Beginning" and also, should I keep "Ext4" as the file system type for it? Also, I assume that I should leave "Mount point" as empty for this primary partition?

/Veroslav

---

### Post by Quackers on 2011-02-05
NO! Primary is not the same as extended (although an extended partition is a form of primary partition). And logical partitions are created within an extended partition. I suspect that if you select Logical as the partition type the installer will create an extended partition on its own, though I haven't done it this way.
If you are at all unsure you should quit the installer and open up gparted from the live cd desktop. Then you can create an extended partition in gparted and fill it with logical partitions. Then when back in the installer you can just select the mount points for your new partitions.

---

### Post by veroslav on 2011-02-06
Hi Quackers,

you was right. I followed this guide: [http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

and managed to do it correctly! So now I have a working dual-boot (Windows 7/Ubuntu 10.10)

The only problem I am experiencing at the moment is that the wireless is not working, but I will start a new thread for this.

I would like to thank all of you who have helped me along the way. Now I know how it is done if I need to do it again. :)

Thanks.

Kind Regards,
Veroslav

---

