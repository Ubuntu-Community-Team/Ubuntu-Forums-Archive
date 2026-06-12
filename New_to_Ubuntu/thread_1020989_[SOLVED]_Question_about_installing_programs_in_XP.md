---
title: "[SOLVED] Question about installing programs in XP"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by biggiemokey on 2008-12-24
Hi I am setting up an Ubuntu/XP dual boot and I was wondering how big I should make my partitions.  What I'm wondering is, do files like C:/My documents and C:/Program Files get placed into the Windows partition automatically?  I want to know where I should install programs like Microsoft Office, CD burning software, iTunes, Firefox etc. because I don't want these programs to take up all of the space inside a Windows partition.  I had planned to make an 11GB partition for Windows, SP2, and updates and install everything else in a shared data partition but I don't really know what I am doing so any advice, no matter how simple it might seem, would really be appreciated.

---

### Post by oilchangeguy on 2008-12-24
> **biggiemokey said:**
> Hi I am setting up an Ubuntu/XP dual boot and I was wondering how big I should make my partitions.  What I'm wondering is, do files like C:/My documents and C:/Program Files get placed into the Windows partition automatically?  I want to know where I should install programs like Microsoft Office, CD burning software, iTunes, Firefox etc. because I don't want these programs to take up all of the space inside a Windows partition.  I had planned to make an 11GB partition for Windows, SP2, and updates and install everything else in a shared data partition but I don't really know what I am doing so any advice, no matter how simple it might seem, would really be appreciated.


you don't say how big your hard drive is. but, why not just split it in half? and my documents, and program files are part of windows, and thus will be installed in your windows partition. and just where were you planning to install the other programs, such as office, itunes, etc.? they won't work in the linux environment, and putting them in a shared partition is a waste of space. so they'll have to go in the windows partition also.

---

### Post by biggiemokey on 2008-12-24
I have 160GB hard drive, but am keeping most of my files (music, videos) on a 500GB external drive so I have space to spare.  The thing is, I want full compatibility between the two OSes.  I want to be able to edit a word document through either Windows or Ubuntu just by double clicking on the file, and I thought it would be best to have a setup where I have:
1) Windows
2) Ubuntu
3) /home
4) Shared Data
Where the Shared Data would hold all of my programs whether they are XP or Ubuntu based.  But I am not experienced with computers and if that does not work please tell me what I should do instead.

---

### Post by oilchangeguy on 2008-12-24
> **biggiemokey said:**
> I have 160GB hard drive, but am keeping most of my files (music, videos) on a 500GB external drive so I have space to spare.  The thing is, I want full compatibility between the two OSes.  I want to be able to edit a word document through either Windows or Ubuntu just by double clicking on the file, and I thought it would be best to have a setup where I have:
1) Windows
2) Ubuntu
3) /home
4) Shared Data
Where the Shared Data would hold all of my programs whether they are XP or Ubuntu based.  But I am not experienced with computers and if that does not work please tell me what I should do instead.

you have to understand that most of the software you listed will not run in linux. there are linux alternatives to some, if not all you listed. so i still think that installing things like office in a shared partition is a waste. with a dual boot setup you will not be able to run both at the same time. dual booting amounts to having two computers share one box. from what i understand you can have some things in a shared partition. and access them when running either os. i've never done it myself.

---

### Post by albinootje on 2008-12-24
> **biggiemokey said:**
> Hi I am setting up an Ubuntu/XP dual boot and I was wondering how big I should make my partitions.  What I'm wondering is, do files like C:/My documents and C:/Program Files get placed into the Windows partition automatically?  I want to know where I should install programs like Microsoft Office, CD burning software, iTunes, Firefox etc. because I don't want these programs to take up all of the space inside a Windows partition.  I had planned to make an 11GB partition for Windows, SP2, and updates and install everything else in a shared data partition but I don't really know what I am doing so any advice, no matter how simple it might seem, would really be appreciated.
I don't know much about MS-Windows usage at all, but I do know that after your XP installation you can install all additional Windows-software in another partition, say E:

Is that because you want to run your Windows-software from that partition within Linux with software like VMware, qemu, Wine or VirtualBox ?
That's first of all not easy and tricky.. not recommended.
And second of all, I think it would in that scenario make more sense to have your Windows software in one partition so that the emulation software can find all the software + registry right away.

Having a shared partition on a dual-boot linux/windows made sense years ago when Linux didn't have full and stable read/write support for NTFS-partitions, but I think you can easily do without a shared data partition nowadays in a dual-boot linux/windows setup.
There are now also more tools to read Linux partitions from Windows too.

---

### Post by Boelcke on 2008-12-24
Don't confuse where you put your programs with where you put your files.

XP goes in one partition
/ (root) is the Ubuntu OS, which goes in another.
/home is often made as a separate partition.  I like the practice.  On my linux-only installations, this is where I store all MY files.
/shared a FAT-32 partition, where you'll put all the FILES you want to share between the two Operating Systems.  Word documents, Open Office documents, pictures, music, etc.

In both cases (XP and Ubuntu), the actual installation of the program is on the same partition as the OS.  XP is in your, ah, C: drive, and ubuntu has it on your root.

I guess you could actually install your Windows applications on a different partition, but it doesn't seem worth it.  It's so tied to that OS, what with common Windows files, registry stuff, etc., that it's only usable when running XP.

---

### Post by Kareeser on 2008-12-24
biggiemokie, please be advised that while it is possible to relocate "Program Files" to wherever you want (like a different drive), it is inadvisable, as these programs will fail to work if and when you decide to format the Windows system. They depend on registry values which are linked to the Windows system and won't function without the host... like an insidious virus.. heh heh.

Relocating "Program Files" also involves registry diving. You've been warned! =P

---

### Post by biggiemokey on 2008-12-24
Thanks for all the responses everyone.  So, would it make sense to do:

1) Windows XP + Windows Programs - NTFS
2) Ubuntu + Ubuntu Programs - ext3
3) /home - ext3
4) Shared FILES (.doc, etc) - NTFS since Ubuntu can read and write NTFS
5) Swap

The other option looks like it would be:

1) Windows XP + Programs + Files - NTFS
2) /root + Ubuntu Programs - ext3
3) /home - ext3
4) Swap

I like the second option because I can then make the 1st partition take up all available space rather than guess how much space I need for Windows XP Programs and Shared Files, like in the 1st option.  If the 2nd setup is viable, could anyone suggest sizing partitions.  I have 160GB HDD and 2GB RAM.

My only problem with the 2nd setup is that I wanted to try out other environments like KDE and XFCE.  It seemed easier to do in the 1st setup I put but I can't really justify why it would be easier because I don't know too much about this stuff.

---

### Post by Boelcke on 2008-12-24
The other window managers (KDE, XFCE) will install right in the root ubuntu partition.  I always make mine 10 gb for ubuntu root, but it never expands to more than 5gb.  Closer to just over 3gb.

You can have all three installed (Gnome, XFCE, KDE), plus a few others that are out there.  Then, you can choose which one at boot-time.

Fun stuff, indeed.

---

### Post by theozzlives on 2008-12-24
I don't use Windows for much so I have a 30 GB partition, Root 10 GB, Swap the amt of RAM you have, /home all the rest. That's if you're gonna be a primary Linux user like me. BTW: I have 160 GB.

---

### Post by biggiemokey on 2008-12-25
One last question - if I have files in the Windows partition, such as in C:\My Documents, can I open them from Ubuntu?  I think it's a yes but I just want to make sure.

---

### Post by -kg- on 2008-12-25
OK, I'll make a stab at this.

> Hi I am setting up an Ubuntu/XP dual boot and I was wondering how big I should make my partitions. What I'm wondering is, do files like C:/My documents and C:/Program Files get placed into the Windows partition automatically? I want to know where I should install programs like Microsoft Office, CD burning software, iTunes, Firefox etc. because I don't want these programs to take up all of the space inside a Windows partition.

...I am not experienced with computers...

Hey, we were all there at one point.  To the basics:

Usually, when you get a new Windows computer, the hard drive is formatted with one large Primary partition on which Windows is installed.  By necessity, this will be a Primary partition, since Windows must be installed in a primary partition, with it's boot files installed near the beginning of the drive.

When you want to install Linux (like Ubuntu) on the drive with Windows in a dual-boot configuration, you will need to shrink this partition and create other partitions on the drive in which to install Linux.  The problem is that the partition in which you want to install Windows must be not only a Primary partition, but it's boot files must be in the first part of the drive.

How many and what types of installations you want to have will determine what partitions you need to create and how you need to create them.  Windows requires a Primary partition, and Linux will install into any partition anywhere on the drive.

When creating partitions on a drive, you may only create 4 Primary partitions.  Any attempt to create additional partitions will fail.  (I wish I had my Wiki page finished on this subject)  This 4 partition limit is applicable to any type of partition...FAT, NTFS, ext2/3, swap, as well as an Extended Partition.  This is where an Extended partition comes into play.

An Extended partition is a special type of Primary partition in which you can create any number of special partitions, called Logical partitions.  Linux will install in and run from a Logical partition, so if you feel you might need more than the allowed 4 Primary partitions, you will want to shrink your Primary partition containing Windows and create an Extended partition encompassing the remaining free space (If you already have 4 primary partitions, you will need to delete one, as an Extended partition takes one of the 4 allowed spaces).

Once you create the Extended partition, you can create your remaining Logical partitions in the free space inside of it.  You can then install Ubuntu on them, as well as create any additional Windows partitions you might want.  Windows will access them...it just won't run out of them.

> I have 160GB hard drive, but am keeping most of my files (music, videos) on a 500GB external drive so I have space to spare. The thing is, I want full compatibility between the two OSes. I want to be able to edit a word document through either Windows or Ubuntu just by double clicking on the file, and I thought it would be best to have a setup where I have:
1) Windows
2) Ubuntu
3) /home
4) Shared Data
Where the Shared Data would hold all of my programs whether they are XP or Ubuntu based.

As has been said before, Windows is not Linux and Linux is not Windows.  Software written to run in one will not run in the other.  But as far as the data files which each manipulates, you can access them with the proper software from each OS, since the data files will be in the same format.

For instance, a file generated by any submodule of OpenOffice can be used by the same submodule in either OS.  The data will be the same.  Since you want to access these files from either OS, you will want to save your data files on a FAT or NTFS partition.  Windows isn't able to access files on an ext2/3 partition without special drivers, but both are able to access a Windows partition.

> I guess you could actually install your Windows applications on a different partition, but it doesn't seem worth it. It's so tied to that OS, what with common Windows files, registry stuff, etc., that it's only usable when running XP.

Not necessarily accurate.  I have done this for years with no problems, and if you have your data files in this extra partition as well, you will be able to access and manipulate those files from Linux as well as from XP.

These days, I would suppose that it isn't really much of an issue, since there is so much room on modern hard drives and with the newer file systems, there isn't the restriction of hard drive and partition sizes that there once was.  The only real reason for additional partitions would be for organizational and back-up purposes.

> But I am not experienced with computers and if that does not work please tell me what I should do instead.

It all depends on what you want to do with your computer.  If you are just going to browse the web and do simple word processing, etc., then you could use any of the scenarios you've presented, and that others have presented.  Any of them would work, as long as you create an Extended partition in which to make more than 4 partitions, in case you need to.  If you create 4 Primary partitions then decide you need more, it will be a major PITA to re-format your drive so you will be able to (See above, where I said you'd have to delete one of them).

If you do a lot of gaming, or (as in my case) do video editing work, or want to experiment with other Linux distros, you will need to be able to make more partitions, and minimize room in partitions in which you don't need the space.  You will likely (as I did) need to install additional hard drives to give you even more space, or transfer your partitions to another larger hard drive.

Not knowing your situation or desires, my suggestion would be as follows:

First, do your install of Windows XP, if you haven't already done so.  The installation process will create one large Primary partition covering your hard drive and place the boot files on the proper part of the partition, as well as placing the XP boot loader in the MBR on the very first part of the drive.

Then I would boot to the Ubuntu Live CD and, from the desktop, select "System/Administration/Partition Editor."  This will launch GPartEd, with which you will be able to shrink the XP partition (from the right side, of course...if you shrink it from the left (beginning) part of the drive, you'll be moving the Windows partition out of it's bootable space) and create an Extended partition to encompass the remaining free space.

Once you have done this, start the Ubuntu installation process.  Since you indicated you want to create separate "/root" and "/home" partitions, at the appropriate place, select "manual partitioning," since either of the "Guided" selections will only make a "/home" partition which contains the /root information in one large partition.

You will then need to manually create your /root, /home, and swap partitions to the size you desire.  When using this method, don't forget to set the tags.  You must tag each partition you've created as /root, /home, and swap respectively, so the installation program knows where to install what.

As for sizes...

This is the hardest of all to say, since I have no idea what you want to do with the computer, or what you might want to do in the future.  The computer I'm using right now (my laptop) is a Vista/Ubuntu dual boot with 240 GB of space in two physical hard drives.  I basically use it for internet and light word processing, and some light programming.

The primary hard drive has two Primary ntfs partitions, the Vista OS being installed into around 70 GB.  Being that you are talking XP, you don't really need *nearly* this amount of space...you probably don't need more than 30 or 40 GB, and that will be plenty of room.

If you start getting crowded, you can always create another ntfs partition (which I believe you were planning to do anyway, and install some of your software in it as well...go ahead, it will hurt nothing, and it's what I've done for years) or you can either shrink some of the partitions on the drive with some room in them, or backup your hard drive to image files and transfer the partitions to another larger hard drive in the future.

My slave drive is entirely enclosed by an Extended partition, and has my Ubuntu partitions as well as a couple of other ntfs partitions as logical drives.  My /root partition is around 10GB (my desktop, on which I do video editing and other things is around 30 GB). My /home partition is around 30GB (on my desktop, 60GB, with additional ext3 partitions in various other places).  This should work in most circumstances for most installations that aren't used for massive projects or storage.

As for swap, mostly I have heard that you should create it as twice the amount of RAM that you have installed.  If you have 1 GB of RAM, it should be 2 GB, and so on.  I know that others use less, but if you have the room (and you do) I would go with the larger value.

One other consideration:

> I have 160GB hard drive, but am keeping most of my files (music, videos) on a 500GB external drive so I have space to spare.

You do know that you can also install Ubuntu to your external hard drive, right?  As long as GRUB resides in the MBR (Master Boot Record...the very first part of the master hard drive) it can point to other partitions on other hard drives.  It won't even matter if you remove that external drive, you will still be able to run Windows and, once you hook up the external you should be able to boot back into the Linux distro which is installed on the external hard drive.

This can also make Ubuntu very portable.  You can install GRUB to a floppy disk or cd/r, boot to it, then select Ubuntu from the GRUB menu.  This should allow you to boot into your installation of Ubuntu on most any computer that is able to boot to a floppy or CD/ROM drive.

> The other window managers (KDE, XFCE) will install right in the root ubuntu partition. I always make mine 10 gb for ubuntu root, but it never expands to more than 5gb. Closer to just over 3gb.

As it is with my laptop, but *not* on my desktop.  From [this web page:]("http://www.control-escape.com/linux/lx-partition.html")

> The size of your root partition will vary depending on what you install or plan to install. Check your distribution's documentation, and reserve enough space for a maximum installation, plus at least 100MB more for temporary space and installation of new software. If you plan to download and try out lots of software, leave more space. If you have a small hard drive, you can trim back on your installed packages to save space. 

While I have a bit installed on my laptop, it doesn't *compare* to what I have on my desktop.  Like I said, if you have the room, more is better.  If you find you don't need quite that much room, or if you have a bunch of room but want to install another distro of Linux for experimentation, you will need to leave yourself room to do so.

Though with a 500GB external hard drive (and depending on how many video and audio files you have on it) you should have enough room for quite a bit.

My desktop has a 400 GB master IDE hard drive, a 160 GB slave IDE drive, an internal SATA 1 TB drive, and an external 1 TB drive, but as I said, I do video editing (among other things) and need quite a bit of room.  I also have my partitions backed up multipley-redundantly...if one drive goes out I can replace it and completely reconstruct it from image files on my other drive(s).

Anyway, enough information for now.  Any further questions, just ask!  That's what we're all here for, to answer any questions (as well as to get our own answered!).

:lolflag:

---

### Post by -kg- on 2008-12-25
:lolflag:

> One last question - if I have files in the Windows partition, such as in C:\My Documents, can I open them from Ubuntu? I think it's a yes but I just want to make sure.

Yes, absolutely.  As long as you have the software (and the software's plugins) installed in Ubuntu that will recognize the type of file it is, there is no problem.  It will read the files there as well as on a separate FAT or NTFS partition.

---

### Post by albinootje on 2008-12-25
> **biggiemokey said:**
> One last question - if I have files in the Windows partition, such as in C:\My Documents, can I open them from Ubuntu?  I think it's a yes but I just want to make sure.

Yes, definitely.
The last few Ubuntu releases come with software pre-installed which will try to mount the NTFS partitions by default.

However if you didn't shut down Windows properly then those NTFS-partitions can be marked as "in use".
In that case you can :
1) Boot into Windows again, and shut down properly.
2) Use the "force" mount option of the ntfs-3g software in Linux
3) Install ntfsprogs to use the tool ntfsfix

GL!

---

### Post by biggiemokey on 2008-12-26
Wow thanks everyone but thanks -kg- especially that was very thorough and helped a lot.  I thought about installing it on the 500GB drive but actually it's a network drive and I think it would be kind of a pain.  So I was thinking:

1) Windows, Windows programs, Shared files - 106 GB NTFS
2) /root - 30 GB ext3
3) /home - 20 GB ext3
4) Swap - 4 GB SwapFS?

Does that seem good?  Also, can I choose whether to make a partition primary or extended through GPartEd?

Thanks again for all the help everyone, I'm glad the community here is so good because I would have a lot of trouble with Ubuntu otherwise.

---

### Post by albinootje on 2008-12-26
> **biggiemokey said:**
> 
1) Windows, Windows programs, Shared files - 106 GB NTFS
2) /root - 30 GB ext3
3) /home - 20 GB ext3
4) Swap - 4 GB SwapFS?

Does that seem good?  

Looks fine to me.
> 
Also, can I choose whether to make a partition primary or extended through GPartEd?


Yes, you can.
Remember, (just in case), that using primary partitions is easier, and gives a clearer overview, but is limited to 4 primary partitions total.
So if you would go for 4 primary partitions total, it's not that easy to add more partitions later on.

---

### Post by -kg- on 2008-12-26
> Wow thanks everyone but thanks -kg- especially that was very thorough and helped a lot.

You're welcome.  I try to help wherever I can.  I'm a relative Linux newbie myself, but I have knowledge in other areas of computers which apply.

> 1) Windows, Windows programs, Shared files - 106 GB NTFS
2) /root - 30 GB ext3
3) /home - 20 GB ext3
4) Swap - 4 GB SwapFS?

Does that seem good? 


Sounds fine to me.  Your /root is maybe a bit big, but if you plan to install a lot of software and stuff, then you might need that size.  The /home seems fine.  I have a 30 GB /home partition on this laptop, and 668 MB used, so really I could shrink that partition without problem.  And if you have 2 GB of RAM on your system, 4 GB is fine.

> Also, can I choose whether to make a partition primary or extended through GPartEd?

Yes, but I suppose that depends on what you intend to do.  An already existing partition?  No.  You have to create an Extended partition...there's no other way.

Remember above that I stated:

> (I wish I had my Wiki page finished on this subject)

Well, it's finished and posted:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

You can read all about creating, manipulating, and deleting partitions on the above page and it's subpages.

Any more questions...just ask!

:guitar:

(edit)
BTW, I would definitely read the Wiki before installing Ubuntu.  albinootje is correct about the 4 Primary partition limit, and if you would need to create more later down the line, it would be impossible to create any more until you created an Extended partition.

If you already have 4 Primary partitions, you would have to delete one of them, because an Extended partition takes one of the 4 Primary partition spaces.  Read especially some of the Partitioning Conventions, like you can't move or extend a Primary partition into Extended space or vice versa.  You create Logical partitions within the Extended partitions.

It's all explained on the Wiki page.

---

### Post by biggiemokey on 2008-12-28
Thank you everyone for all the help.  I'm excited to get this done and I'll post how it works out soon.

---

### Post by biggiemokey on 2009-01-04
One more question - is there any disadvantage to an Extended Partition?  If not, it seems like I should make Windows and Swap Primary Partitions, and then /root and /home Extended Partitions.

---

### Post by albinootje on 2009-01-04
> **biggiemokey said:**
> One more question - is there any disadvantage to an Extended Partition?  If not, it seems like I should make Windows and Swap Primary Partitions, and then /root and /home Extended Partitions.

Personally I find extended+logical partitions sometimes a little confusing at first to look at, when looking at some output of "sudo fdisk -l", but apart from that it should be all fine.

The extended+logical partitioning scheme only started because of the maximum of four primary partitions restrictions afaik.

---

### Post by Elfy on 2009-01-04
You can't have /root and /home as extended partitions. An extended partition is to all intents and purpose a primary partition and is a 'box' to put logicals in.

Personally I would put all my linux partitions in an extended partition which then leaves space for more primaries if needed.

Eg - this would allow for 2 more primaries.

windows - primary

Extended 
Logicals for swap, / and /home

You can have a maximum of 4 primary partitions, including 1 extended partitions.

---

### Post by biggiemokey on 2009-01-04
Makes sense, thanks.  Unfortunately, because my WINDOWS Home Server isn't working properly, I can't reformat just yet.  I am looking forward to Linux more and more as each day goes by.

---

### Post by biggiemokey on 2009-01-11
Well, I set up the dual boot and it seems to working perfectly.  Audio worked natively!  It didn't in 8.04 at least not through Wubi.  Now I'm just trying to figure out a few things, like making my Microsoft keyboard buttons work, setting up wireless with Dell Truemobile card, and installing Kubuntu (I think I installed it in place of Ubuntu, trying to figure it out still.)  But I'm very happy!  Thanks for all the help everyone.

---

