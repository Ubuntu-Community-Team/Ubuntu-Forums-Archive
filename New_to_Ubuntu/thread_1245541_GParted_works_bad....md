---
title: "GParted works bad..."
date: 2009-08-20
forum: New to Ubuntu
---

### Post by Tender Prey on 2009-08-20
HI,

i'm trying to create the necessary partition to install Ubuntu with Gparted Live (cd ISO) but it read my HD as almost all busy (7GB free on 60). The problem is that i have about 36GB free but Gparted doesn't read the free space?
some one ca help me?
thanks

---

### Post by blur xc on 2009-08-20
Just a shot in the dark, but did you do a defrag before running the live cd?

BM

---

### Post by Tender Prey on 2009-08-20
yes, i did with several differnt softwares !

---

### Post by hibliss on 2009-08-20
You should resize the Windows partition from within Windows after all those defrags. 

Even with 36gb free, if the drive is fragmented, there is nothing Gparted can do.

You are always better off using the Windows disk management utility to shrink the Windows partition and then use Gparted to format the free space as EXT for Linux.

---

### Post by LowSky on 2009-08-20
defrag the hard drive in windows first, it will condense the used space and make gparted work correctly. Windows is horrible at data management.

Also make sure you shut down correctly as NTFS partitions are notorious for not being accessible if you power down incorrectly.

---

### Post by blur xc on 2009-08-20
I've been curious about this-

Say you have a platter with files A, B, C, D, and E on it, and they are laid out like - AxxBxxxCxxxxDxxxxE (x being free space), and each file isn't fragmented, just scattered about the disk, would a defrag squish all the data to the beginning of the disk or leave it where it is, since each file is already contiguous?

BM

---

### Post by Tender Prey on 2009-08-20
are you telling me that i have to create the partition within Win and the i should format the partition with GParted to format the partitions in the way i need (i.e. ext 3, swap..)? Just to be sure i undestood well..

---

### Post by hibliss on 2009-08-20
No, I am telling you you need to Shrink the current NTFS partition from within Windows first. This will create the free space needed for Gparted to do what it needs to.

Are you on Vista? [http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/")

---

### Post by Tender Prey on 2009-08-20
ok, i have just to create free space within win om my hd and the i can use gparte to create the partition i need!
thanks!
which program can you suggest me to shrink win? i have Acronis Disk Director Suite...

---

### Post by hibliss on 2009-08-20
Vista or XP?

---

### Post by nhasian on 2009-08-20
xp does not have this feature, but if your using vista you may be able to shrink the ntfs volume by right clicking on my computer, then going to manage, then disk manager.  right click on the volume and select shrink volume.

I know everyone in this thread recommended you use the tool in vista to shrink your volume (if you are even using vista) but personally i've never gotten it to allocate enough drive space.  I always use and highly recommend gparted regardless of what OS your using.

---

### Post by Tender Prey on 2009-08-21
Xp

---

### Post by Tender Prey on 2009-08-21
> **nhasian said:**
> xp does not have this feature, but if your using vista you may be able to shrink the ntfs volume by right clicking on my computer, then going to manage, then disk manager.  right click on the volume and select shrink volume.

I know everyone in this thread recommended you use the tool in vista to shrink your volume (if you are even using vista) but personally i've never gotten it to allocate enough drive space.  I always use and highly recommend gparted regardless of what OS your using.

You are right but my problem is that GParted doesn't recognize the right free space!!!!

---

### Post by Tallman on 2009-08-21
> **Tender Prey said:**
> You are right but my problem is that GParted doesn't recognize the right free space!!!!

Please post a screenshot of GParted from the LiveCD.

---

### Post by Tender Prey on 2009-08-21
here it is

---

### Post by Bartender on 2009-08-21
What does the HDD look like in XP after you've defragged?  I'm guessing that XP will show a sliver or two of "unmovable" data way out there to the right of the drive.  I don't know why the data is recognized as "unmovable" but it seems like that happens regularly.

I dunno, it looks to me like it's time to buy a bigger HDD and use the HDd manufacturer's utility to copy XP over to it.

---

### Post by Tallman on 2009-08-21
I think the 'free space' you are talking about is free space in your window environment. This space is not available for Ubuntu.

In GParted, shrink your windows partition and install Ubuntu in the resulting unallocated space.

---

### Post by todd1049 on 2009-08-21
If you have Windows Vista, I would encourage you to try the Vista partition program.  I have used it to install linux dual-boot on two machines now, with no problems so far.  As much as people badmouth Vista, maybe deservedly, its partition tool is pretty good.  I have never used XP's partition tool.

---

### Post by hibliss on 2009-08-21
> **Bartender said:**
> What does the HDD look like in XP after you've defragged?  I'm guessing that XP will show a sliver or two of "unmovable" data way out there to the right of the drive.  I don't know why the data is recognized as "unmovable" but it seems like that happens regularly.

I dunno, it looks to me like it's time to buy a bigger HDD and use the HDd manufacturer's utility to copy XP over to it.

The unmovable files are often the pagefile. This can be fixed by disabling the pagefile, then defragging again.

---

### Post by Tallman on 2009-08-21
> **hibliss said:**
> The unmovable files are often the pagefile. This can be fixed by disabling the pagefile, then defragging again.

Or by resizing the partition in GParted.

I mean, the OP is in the LiveCD, GParted is right there...

---

### Post by karth83 on 2009-08-21
From Windows XP you can use Partition Magic or any software of that sort to create an empty partition on the free space.

But I would recommend 10GB Free space atleast for Installing Ubuntu.

Try freeing up some space if possible or copy into a friend's external hard disk/pen drive. Then in the free space you can try any partioning tool for windows like partition magic and create an empty drive. This you can use for installing Ubuntu. 

If space is available copy the data back from the external disk.

---

### Post by Bartender on 2009-08-21
hibliss -
Thanks for the page file tip.  I'll have to write that down and try it next time the problem comes up!

---

### Post by hibliss on 2009-08-21
> **Tallman said:**
> Or by resizing the partition in GParted.

I mean, the OP is in the LiveCD, GParted is right there...

This can damage a Windows install. If the partition is fragmented and you use gparted to format space that is not actually free, problems will occur.

Read - [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

---

### Post by Penguin Guy on 2009-08-21
> **blur xc said:**
> I've been curious about this-

Say you have a platter with files A, B, C, D, and E on it, and they are laid out like - AxxBxxxCxxxxDxxxxE (x being free space), and each file isn't fragmented, just scattered about the disk, would a defrag squish all the data to the beginning of the disk or leave it where it is, since each file is already contiguous?

BM
I believe it depends what defragmenter you use. The default Windows XP one will leave them where they are most of the time.

---

### Post by LewRockwell on 2009-08-21
> **Tender Prey said:**
> HI,

i'm trying to create the necessary partition to install Ubuntu with Gparted Live (cd ISO) but it read my HD as almost all busy (7GB free on 60). The problem is that i have about 36GB free but Gparted doesn't read the free space?
some one ca help me?
thanks

Gparted shows the partition(s) and the usage within those partitions

You need to figure out where this difference is, between what you think you have and what Gparted reports

My guess is that files you THINK you've deleted...either are not really deleted or something else is happening

Here, try these:

[http://download.cnet.com/ccleaner/](http://download.cnet.com/ccleaner/)

[http://download.cnet.com/Smart-Defrag/3000-2094_4-10759533.html](http://download.cnet.com/Smart-Defrag/3000-2094_4-10759533.html)

[http://download.cnet.com/Eusing-Free-Registry-Cleaner/3000-2094_4-10521691.html](http://download.cnet.com/Eusing-Free-Registry-Cleaner/3000-2094_4-10521691.html)

.

---

### Post by LewRockwell on 2009-08-21
and there's always this thread to follow up on

[http://ubuntuforums.org/showthread.php?t=1246316](http://ubuntuforums.org/showthread.php?t=1246316)

.

---

### Post by Tender Prey on 2009-08-22
Hi,

i'm trying to put all your informations and suggestions togheter.
I'd like to thanks all of you for you replies and patience...I think this is what make the Ubuntu community very special and different!
anyway...I hope to solve my problem!

---

### Post by Herman on 2009-08-22
I would give up on defragging and try running CHKDSK instead.
GParted has always been able to resize Windows partitions regardless of their state of fragmentation. CHKDSK may fix some corruption in your file system that's causing it to report the wrong amount of used space. I would run CHKDSK /R, (it implies /F).

Also, Vista and Windows 7 users should make sure they remove the check mark from the 'Round to cylinders' check box in GParted, (not shown in the how-to geek's illustrations), as failure to do so will result in having the start point of your partition moved, then you will need to use the how-to geek's advise to fix it and make it bootable again.
If you just remove the check mark, you'll save yourself some time and trouble.
Somebody gave a link to the how-to geek in an earlier post. I've written to the how-to-geek to see if he'll fix his website.
If you're using XP it doesn't matter, you can leave the checkmark as it is.

Regards, Herman :)

---

### Post by Tender Prey on 2009-08-22
I think you are right...I tryed to defrag the HD with any software available! Nothing, nothing and again nothing!!!! Gparted continues to read only 7Gb as free space! My problem is that i'm not so smart with dos, wind and administration tools in general. sometime i feel scared in doing something sice i think i can damnage the HD in a definitive way!
I don't want to give up to install Ubuntu but, at moment, i don't see other solutions... sorry for that!

---

### Post by philinux on 2009-08-22
Can you post a screenshot of what windows sees?

---

### Post by Tender Prey on 2009-08-22
sure

---

### Post by Zill on 2009-08-22
> **Tender Prey said:**
> ... My problem is that i'm not so smart with dos, wind and administration tools in general. sometime i feel scared in doing something sice i think i can damnage the HD in a definitive way!...
You are quite right in that partitioning (or other events!) *can* damage your hdd.

One word of advice: BACKUP.  It is always advisable to have backups of *all* your important data so that in the unlikely event that your hdd is trashed you can always restore your data.

---

### Post by Herman on 2009-08-22
> I think you are right...I tryed to defrag the HD with any software available! Nothing, nothing and again nothing!!!! Gparted continues to read only 7Gb as free space! My problem is that i'm not so smart with dos, wind and administration tools in general. sometime i feel scared in doing something sice i think i can damnage the HD in a definitive way!
I don't want to give up to install Ubuntu but, at moment, i don't see other solutions... sorry for that!  That's okay, but I'd really like to help you. Maybe the information below here will help.

Quoted from: '[NTFS and FAT32 File System Repair and Maintenance]("http://members.iinet.net.au/%7Eherman546/p10.html#NTFS_File_Fystem_Repair_and_Maintenance") ' - File Systems and Mounting Page, Illustrated Dual Boot Site,
> The NTFS file system is the preferred file system from Microsoft for most Windows XP and Vista users since it's supposed to add more security for the Windows Operating System.
The NTFS file system needs a file system check every once in a while the same as any other file system and it's a good idea to do so.  
It is also recommended to run CHKDSK after the file system had been resized.
Often that will clear up problems or at least keep things running well. 
In Windows XP, the program to use for running a file system check on a FAT32 or NTFS file system is CHKDSK.

**CHKDSK on bootup**
To schedule CHKDSK to run next time you reboot Windows XP, you can go 'My Computer',-->'Local Disk (C, and right-click on 'Properties'.
Open the 'Tools' tab, and in the 'Error Checking' box, click the 'Check Now' button.
A 'Check Disk' window will open.

[LIST=1]
[*]Place a check mark in the square for 'automatically fix file system errors', and also a check mark in the square for 'Scan for and attempt recovery of bad sectors'.
[*]Click the 'Start' button
[*]A window will open advising you it can't do it right now but you can schedule a disk check for next time you boot up. Click Yes.
[*]Reboot your computer and choose Windows XP from your GRUB menu. Don't be alarmed when it blue-screens in the middle of starting Windows XP and runs your disk check.
[/LIST]
Just to make sure you understand, or in case I missed anything, here's a Symantec link about how to do that, [How to Run Microsoft CHKDSK from the command line]("http://service1.symantec.com/SUPPORT/powerquest.nsf/docid/2004066687571562").
[B]
CHKDSK from Windows Recovery Console[/B]
If an NTFS file system needs repair or maintenance, and Windows won't even boot, you may need to use a [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"), available from your Windows XP Installation disk (CD-ROM). 
If your  computers came with a 'Recovery' CD or worse, a 'Recovery Partition' instead of a real Windows 'Installation' disc, you will need to go borrow a Windows XP 'Installation' CD from a friend, just to use the Recovery Console. 

The CKDSK has 'switches' (Windows language for 'options'), for specifying what you want the command to do.
Here are a few links to explain what 'switches' you can use and what they do,
[Chkdsk]("http://www.microsoft.com/technet/prodtechnol/windows2000serv/reskit/prork/pref_tts_ffgh.mspx?mfr=true") - Microsoft, and [An explanation of CHKDSK and the new /C and /I switches]("http://support.microsoft.com/kb/314835") - Microsoft, and [Sample Chapter from Microsoft® Windows® 2000 Professional Resource Kit]("http://www.microsoft.com/mspress/books/sampchap/1393b.aspx").
[CHKDSK]("http://www.ss64.com/nt/chkdsk.html") - ss64.com

---

### Post by Herman on 2009-08-22
Partitioning damages the hard disk? :confused:

Well, that's an abbreviated way of saying something that would take a lot of words to explain properly, in some way you could be right. 
The problem is, when new users read brief statements like that without and further clarification they get frightened.

What the partition editor does for you is write some numbers in your partition table, which is a small part of your hard disk's Master Boot Record. 
There are four spaces in the partition table reserved for four 'primary' partitions, and there's space for sixteen bytes of information about each partition. This information is very breif and basic, and just includes the bare minimum details, such as what sector the partition is to begin at, and what sector it ends at, and what type of partition it is.
The Master Boot Record is located in sector 0 of every formatted hard disk. It also has a space reserved for the boot loader's 'Initial Program Loader or 'IPL' code, which is basically just a pointer to direct the BIOS to a partition boot sector and/or to the actual boot loader, which is most often in the operating system's partition.
There are also some other small items in the MBR (Master Boot Record), like a 'Disk Identifier', which is important to Vista and Windows 7's boot loader.
It's okay to write new information to the partition table and overwrite the old information as long as it's done properly. The MBR is made of the same material as the rest of the hard disk and it can be written to and erased a lot of times without wearing out.
Most of the time it's pretty simple from the user's point of view to run programs for changing out partitions and it's quite rare for things to go wrong. Sometimes problems do occur and that's why it is recommended to always back up your data before using disk partitioning software, for your convenience and protection. 
A 'corrupted partition table' can mean that we won't be able to access our data in the normal way. The directions (in the partition table) that the computer uses to remember where the partitions start is messed up. If the computer doesn't 'know' where the partition starts thn it can't find the file system blocks at the start of the partition which contain the directions to access the files and the operating system itself. Most often, a 'corrupted partition table' is caused by a difference in opinion between two different disc partitioners, information written in the partition table by a previous partitioning program can look like garbage to another brand of disk partitioner. Most of the time they agree, but not always. GParted does a sanity check first and it normally will refuse to do anything if it detects garbage in your partition table written by some previous partitioner, so most of the time when you're using GParted you will be protected against having a corrupted Partition Table. 
In the unlikely event that one does have a serious partition table problem, we Linux users have a program called 'TestDisk' available to help. TestDisk can scan the hard disk for data that resembles the start sectors of partitions (probably boot sector and file system blocks I imagine), and it will report the location of those back to the user who can then select which ones to include when TestDisk writes a new partition table, based in the user's selections.

The other role that most partition table editors do is, they also run commands to build your boot sector and file system at the start of a new partition, or overwrite the file system in an old partition, (when you reformat a partition).
The boot sector and file system blocks can be located almost anywhere on the hard disk but by convention, Linux and most Windows partitions start and finish on a 'cylinder boundary', (there are 63 sectors in a cylinder). Windows 7 and Vista are different, that's why we remove the 'align partition on cylinder boundary' checkmark in GParted when working on Windows 7 or Vista partitions.
In simple terms, your file system contains directions for how and where the operating system can find your stored data.
If something bad happened to the file system blocks, even that doesn't always mean you have lost all of your data, TestDisk contains another program called 'PhotoRec', which can rescue your data right off the hard disk without the need of directions from the file system. There are other kinds of file recovery software too. [Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/") is a specially made Ubuntu which contains software like that.
The partition boot sector and the file system blocks at the start of the partition are also made of the same material as the rest of the hard disk and it doesn't matter how many times they are written to and erased, it doesn't do any damage to the actual material that the hard disk is made of.

I have test computers that have had operating systems installed in them and deleted, re-installed, moved around, deleted and rescued again, overwritten, and so on. I've also practiced with TestDisk and PhotoRec so if somebody needs partitions restored or files rescued I have a pretty good idea how to help,  Every time a new Ubuntu comes out I install it and delete it about tenor twenty times or more probably, to find out how the partitioner works and what's the best way to use it, (in my opinion). I've been doing these operations for years now,  so I think I would be the first to know if partitioning can actually damage your hard drive. Well, it might wear it out eventually, but it will take a very long time.

So, there's no need to be scared of partitioning our hard disks, we have safeguards and we have ways to fix things if thing do go haywire, but it's still best to make a backup first. As long as you do that then there's really nothing to be scared of.  :)

---

### Post by Tender Prey on 2009-08-22
Hi Herman,

fisrt of all many thanks for your accurate explantion.
I launched the **CHKDSK on bootup **as you told me, i waited a long time and then i tryed to run GParted Live to see what happens. NOTHING! Gparted conitnues to read only 7GB as free space instead of 26 or something like that. I'm disappointed. I know maybe i should change my HDD and buy another one but what i really don't like it's the idea that i have to change the HDD to make Ubuntu works!! How is it possible that i have to change the HDD?!?! The question is: any time something goes wrong i have to change HDD? I hope no, i don't want to think so but...WHERE IS THE SOLUTION? Maybe Win is not efficient but i have to recognize that most of the time is easier than Linux. Or maybe it's just my fault...
regards

---

### Post by JC Cheloven on 2009-08-22
> **Tender Prey said:**
> Hi Herman,

fisrt of all many thanks for your accurate explantion.
I launched the **CHKDSK on bootup **as you told me, i waited a long time and then i tryed to run GParted Live to see what happens. NOTHING! Gparted conitnues to read only 7GB as free space instead of 26 or something like that. I'm disappointed. I know maybe i should change my HDD and buy another one but what i really don't like it's the idea that i have to change the HDD to make Ubuntu works!! How is it possible that i have to change the HDD?!?! The question is: any time something goes wrong i have to change HDD? I hope no, i don't want to think so but...WHERE IS THE SOLUTION? Maybe Win is not efficient but i have to recognize that most of the time is easier than Linux. Or maybe it's just my fault...
regards

1) Bad title. Gparted is working flawlessly for you. Windows is working bad here: it is unable to properly handle its own native filesystem!! Don't blame anyone else. 

2) Please, don't even think in buying anything extra. It seems that keeping your current M$ install is giving you a lot of headhaches. If you are not frightened by the possibility of reinstalling windoze, consider points 3 and 4 below.

3) I had a similar problem with vista (a friend's pc), and took the risk: after defrag (which you already did), started ubuntu live cd, ran gparted, and shrinked the vista partition to my wish. Then I installed ubuntu, etc. Know what? Everything was ok with vista afterwards. But it was risky, though.

4) If point 3 fails for you, or if you simply want to, consider backup your data, delete and partition your entire disk as you like, reinstall windows, and then install ubuntu. 

I think it's a good advice at this time, as you surely are tired of running circles around your _*windows problem.*_

EDIT. Suggested setup for you: 16Gb ntfs for XP (well, depending on how much stuff you need to install). 12Gb ext4 for ubuntu. 0.5~1.0Gb swap (interchange area used by linux). The rest, about 31Gb ntfs partition for your data. The idea is that you can access your files from both operating systems (and use this instead of either "MyDocumments" or "/home").

Don't despair, the whole thing it's worth! :-)

---

### Post by Herman on 2009-08-22
Your hard disk is probably okay, but it seems as if there's some problem in what's written on it that we haven't been able to identify yet or to have fixed easity
There are two grades of CHKDSK, one is just F, which is quick in case you're in a hurry and there's not much wrong, and then there's /R, which is very slow and thorough, and fixes a lot more problems.
I think if you are working with the GUI version of CHKDSK, (schedule CHKDSK at next reboot), you should click in both of the squares to place  check marks in front of 'automatically fix file system errors' and 'scan for and attempt repair of bad sectors', I think that would be the same as running CHKDSK /R from the command line.
If you have already run a thorough disk check, then I don't know, I'm inclined to agree with JC Cheloven there, (in the post above).

Sometimes just repeating the same disc check works to fix  Windows file system problems. It's more likely that a repeated file system check will fix it than repeated defragging. I don't think defragging Windows will do any harm, and it may do Windows a little good. However, I don't believe that it's at all necessary to defragment Windows before resizing with GParted. GParted can resize Windows just as well regardless of the state of fragmenation, at least it always has done so for me. Defragmenting is probably just a waste of time. 
According to the Parted Users Manual, you don't need to defrag, refer, [2.4.13 resize]("http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html#SEC25") - Parted Manual
The ntfsresize documentation says defragging doesn't matter, [How to resize NTFS without data loss?]("http://darkstar.ucd.ie/timosh/links/ntfsresize.html#example").
According to the Linux manual page for ntfsresize it's not necessary, 
Quote:
> The  ntfsresize program safely resizes Windows XP, Windows Server 2003, Windows 2000, Windows NT4 and Longhorn NTFS filesystems without data loss. 
All NTFS versions are supported, used by 32-bit and 64-bit Windows.  
Defragmentation is NOT required prior to resizing because the program can relocate any data if needed, without risking data integrity.

---

### Post by Tender Prey on 2009-08-23
Well..wath to say..Thanks. Your suggestions are very precious to me. I think i'm pretty sure about what to do.

---

