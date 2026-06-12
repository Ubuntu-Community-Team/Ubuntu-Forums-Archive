---
title: "How to access Linux partition files"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by g_ramesh on 2010-09-03
Hi

I have a pc with Win xp (Prof), win 7 and Ubuntu 10.04 installed on three seperate partitions.  

I  am able to access windows files from Ubuntu but not the other way!


I was going through an article where it says Ubuntu can be installed within win7 using VMware player (of course there is WUBI option as well)

I think this is a good option instead of installing Ubuntu on a seperate partition as I am not able to see the Ubuntu partition either in xp or win 7 and save some data on it.
Now that much of hard disk space is exclusively reserved for Linux.
 
I would like to reclaim that space by uninstalling Ubuntu and installing it again thru VMware player within win 7 (or xp which is better?) 

or

 installing thru WUBI is ok?

Please suggest.

---

### Post by julio_cortez on 2010-09-03
> **g_ramesh said:**
> Please suggest.
I'd suggest you not to mount the Linux partition in Windows, as it can be easily screwed up, and even because some filenames (*like .conkyrc*) that are perfectly ok in Linux "scare" Windows Explorer to the extent it refuses to open/move/modify/delete them.

My suggestion will then be to have a "shared" NTFS data aprtition that both Linux and Windows can access, but to keep the Windows partition unmounted in Linux, and not to try mounting the Linux partition in Windows.

If you're still willing to do so, though, maybe you can read something about it. I found [this]("http://www.linuxjournal.com/article/9449") after a quick search in Google, maybe it can be of help.

---

### Post by anaconda on 2010-09-03
it depends on which filesystem type you selected for ubuntu.

in 10.04 the default filesystem is ext4, which can't be accessed from windows. If you would have choosen ext3 then you would have been able to install ext3 support for windows and you could access ubuntu from windows.

vmware is good for trying an os out. it will run slower through vmware... the other thing of vmware is that it also reserves space for ubuntu, which wont be accessible for windows. (the virtual hard disk)

I have newer tried wubi, but it would seem the best solution for you

---

### Post by scorp123 on 2010-09-03
> **g_ramesh said:**
>  I  am able to access windows files from Ubuntu but not the other way!  Of course not. Microsoft doesn't play nice with others, didn't you know that? :D

I recommend you use a FAT32 partition somewhere and exchange files that way. Both Windows and Linux can read and write to FAT32 without problems. Or you use an on-line sync service such as Dropbox? It works for Mac, Linux and Windows. You could then sync files to Dropbox, and each time you boot into your other OS your Dropbox would automatically download the new files.

> **g_ramesh said:**
>  I was going through an article where it says Ubuntu can be installed within win7 using VMware player (of course there is WUBI option as well) And Windows can be installed inside VirtualBox. 

> **g_ramesh said:**
>  I think this is a good option instead of installing Ubuntu on a seperate partition as I am not able to see the Ubuntu partition either in xp or win 7 and save some data on it. I personally think it's a very bad idea to have Windows on a partition anywhere and that it's best if you banish it into a virtual machine and let Linux control all your hardware. But as I said: that's just my personal opinion.

As for Windows not being able to read other OS's partitions: please take your complaint to Microsoft. :D

---

### Post by julio_cortez on 2010-09-03
> **scorp123 said:**
> please take your complaint to Microsoft. :D
I'd rather thank them for it.
This way, you can't screw other OSs partitions by mistake (and I really think it's true also the other way round: I'm a little scared of Linux being capable of reading/writing NTFS file systems for the very same reason).

---

### Post by scorp123 on 2010-09-03
> **julio_cortez said:**
>  I'm a little scared of Linux being capable of reading/writing NTFS file systems for the very same reason). And rightly so. Because Microsoft never really opened those NTFS specifications. So the few things Linux can do with NTFS were achieved by people reverse-engineering NTFS disk accesses. In other words: they watched what Windows is doing and then they guessed how to reproduce that behaviour. Sometimes this reverse-engineering works, but sometimes it doesn't. And in the case of NTFS I know it doesn't always work 100% because I already lost a disk ... I actually tried to fix it, but instead I lost it completely. Oh well ... There is always a new lesson to be learned :D

The good thing about Linux is that normally it will leave the disks of other OS alone. So unless you specifically tell it to access a NTFS disk (which I don't recommend ...) nothing ever should happen.

---

### Post by prshah on 2010-09-03
> **g_ramesh said:**
> I  am able to access windows files from Ubuntu but not the other way!

Use [ext2read]("http://sourceforge.net/projects/ext2read/")

---

### Post by scorp123 on 2010-09-03
> **prshah said:**
> Use [ext2read]("http://sourceforge.net/projects/ext2read/") 

EDIT: ... never mind ... It indeed seems to work with Ext4 now.

---

### Post by Zintha on 2010-09-03
> **scorp123 said:**
> 
 I personally think it's a very bad idea to have Windows on a partition anywhere and that it's best if you banish it into a virtual machine and let Linux control all your hardware. But as I said: that's just my personal opinion.

As for Windows not being able to read other OS's partitions: please take your complaint to Microsoft. :D


I've never told anyone to go all Linux/Non-windows OS ever before.
The people who would be able to handle not having windows are already using Linux or another OS (excusing Mac, horrible OS, no offence Mac users) and the people who use exclusive windows OS on their computers are people who are not computer savvy enough to go without it or do too much non-linux-easily-supported software or games.

As for your second part I heard, not confirmed for myself yet, that Microsoft deliberately discourage you from using Linux alongside windows in several ways.

---

### Post by Zintha on 2010-09-03
> **scorp123 said:**
> 

The good thing about Linux is that normally it will leave the disks of other OS alone. So unless you specifically tell it to access a NTFS disk (which I don't recommend ...) nothing ever should happen.

I play World of Warcraft using Wine off my Windows installation and it works better than any linux installation i've tried yet.

Yet to mess it up to! Which I am very happy for so far.

Also, to not jabber on and to try and add something productive to the conversation, the ideas of having a shared area which you dump linux and windows stuff into when you need to access them from both sides is what i've done and would do in future. Just seems to work the best. Either that or use a flash disk or some removable drive of sorts.

---

### Post by biswarupg on 2010-09-03
Well, in my machine, I once used Virtual Box inside WinXP and Win7 to run Ubuntu. WinXP seems to me a better choice for it runs Ubuntu faster in VirtualBox. 
But, XP runs even faster inside Virtual Box in Ubuntu and Mandriva. If you have a powerful machine with 2gb of RAM atleast, you can get a secure Windows XP running within Linux.

---

### Post by oldfred on 2010-09-03
I prefer the shared NTFS data partition. Even windows users often recommend a separate data partition so when you have to reinstall windows you do not lose all your data.

I do not like to use another system to write into a system, reading is ok but writing can lead to issues no matter how good the implementation of the driver is. Except for repairs of windows from linux.

With the shared data partition you can have all the data you may want in both systems easily accessed. I use it for my firefox & thunderbird profiles so I have the same bootmarks and email in both systems.

---

### Post by g_ramesh on 2010-09-05
> **prshah said:**
> Use [ext2read]("http://sourceforge.net/projects/ext2read/")

thnaks for the reply, but it is only listing the files and not allowing to save files to this partition.

---

### Post by g_ramesh on 2010-09-05
> **Zintha said:**
> Also, to not jabber on and to try and add something productive to the conversation, the ideas of having a shared area which you dump linux and windows stuff into when you need to access them from both sides is what i've done and would do in future. Just seems to work the best. Either that or use a flash disk or some removable drive of sorts.

Hi Zintha and oldfred

thanks for your replies please tell me how can I create this shared area out of Linux partition (about 100 GB) ?

---

### Post by snip3r8 on 2010-09-05
use ext2explore

---

### Post by oldfred on 2010-09-05
I have both NTFS shared and ext3 data partitions for all my data and have several 20-25GB root partitions as I keep several versions of Ubuntu installed - 9.10 previous, 10.04 current, & 10.10 testing. 

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Link XP my docs
[http://www.techsupportalert.com/how_to_move_my_documents.htm](http://www.techsupportalert.com/how_to_move_my_documents.htm)

You can use the same linking with NTFS, it just does not support linux ownership & permissions.
Painless Linux Multi-boot Setup - see also comments by Morgan Hall
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions (post #5) of data linking from above blog, based on more from comments 
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by g_ramesh on 2010-09-06
> **snip3r8 said:**
> use ext2explore

As earlier it is showing only files, not allowing to save files to Linux partition.

---

### Post by Insomnia64 on 2010-09-06
> **g_ramesh said:**
> thanks for your replies please tell me how can I create this shared area out of Linux partition (about 100 GB) ?

I would download the gparted .iso from [[COLOR="Blue"]here[/COLOR]]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/") and boot with that. You should be able to select your hard disks from the drop down box on the right (if you have more than one). From here you can resize the partitions as required (by dragging the boxes), remember to unmount any partitions before trying to modify them. You can resize them to leave you 100GB free (if that's the size you want) then format it FAT32 or NTFS. Be aware that you cannot store files larger than 4GB on a FAT32 partition, so if that is a requirement then use NTFS. Once you have arranged the partitions as you like you can click apply and it will set them up for you.

---

### Post by Mark Phelps on 2010-09-06
> **snip3r8 said:**
> use ext2explore

Sigh ... according to their site, this only works with Ext2/Ext3 partitions, and as has been said SEVERAL times in this thread, 10.04 installs by default in Ext4 partitions.

So, unless their site info is incorrect, this will not work with 10.04 filesystems.

---

### Post by g_ramesh on 2010-09-08
> **Insomnia64 said:**
> I would download the gparted .iso from [[COLOR=Blue]here[/COLOR]]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/") and boot with that. You should be able to select your hard disks from the drop down box on the right (if you have more than one). From here you can resize the partitions as required (by dragging the boxes), remember to unmount any partitions before trying to modify them. You can resize them to leave you 100GB free (if that's the size you want) then format it FAT32 or NTFS. Be aware that you cannot store files larger than 4GB on a FAT32 partition, so if that is a requirement then use NTFS. Once you have arranged the partitions as you like you can click apply and it will set them up for you.

thanks Insomnia64 for your reply. 
I d/l the GParted (0.6.2-8) live iso and burned onto a cd and run it and resized the partition which is having Linux installed on it. It went well and when I try to format that unallocated space it is showing can not create already 4 primary partitions are there?

Then I rebooted the pc into win 7 and thru Disk management tried to format the unallocated space it is showing 

" you cannot create a new volume in this unallocated space because the disk is already containing the maximum number of partitions. "

The screeshot I u/l and the link is

"  [http://www.4shared.com/photo/MAnS40Gi/partition_image.html](http://www.4shared.com/photo/MAnS40Gi/partition_image.html) "

please tell me how can I format that about 68GB of drive as NTFS and use as shared disk between win and Linux.

---

### Post by Arla on 2010-09-08
Unfortunately you would need to get an extended parition to put other logical partitions in (system limitation of at most, 4 primary & extended partitions (I think I got that right)) so you'd need to delete another partition and then create an extended partition with two logical partitions in it.

---

### Post by oldfred on 2010-09-08
According to your screen shot you already have a logical which must be inside an extended. You can expand the extended if it is next to the unallocated and add additional logicals inside it. If not next to it you have to move other partitions around as you can have only one extended partition (with many logicals inside) and then three primary partitions.

To see the order on your drive from liveCD. From liveCD you may not need sudo.

```
sudo fdisk -l
```

---

### Post by g_ramesh on 2010-09-08
> **oldfred said:**
> According to your screen shot you already have a logical which must be inside an extended. You can expand the extended if it is next to the unallocated and add additional logicals inside it. If not next to it you have to move other partitions around as you can have only one extended partition (with many logicals inside) and then three primary partitions.

To see the order on your drive from liveCD. From liveCD you may not need sudo.

```
sudo fdisk -l
```

thanks oldfred for your reply. I remember it is at the last and  after Linux partition. can you please tell me how to move other partitions around and bring this unallocated space inside the extended partition?

I thinks the three primary are win xp.,  swap and Linux partitions is it right? Is swap and linux partitions are required to be primary?

---

### Post by oldfred on 2010-09-08
Windows requires a primary partition to boot from. Linux can be totally installed in logical partitions and NTFS data partitions can also be logical partitions. You can even install a second version of windows in a logical but always will have to boot thru the first install in the primary.

Some links:
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by g_ramesh on 2010-09-09
> **oldfred said:**
> Windows requires a primary partition to boot from. Linux can be totally installed in logical partitions and NTFS data partitions can also be logical partitions. You can even install a second version of windows in a logical but always will have to boot thru the first install in the primary.

thanks. Please tell me how to move other partitions around and bring unallocated space next to exteneded partition so that I can expand it and merge the unallocated space?

---

### Post by oldfred on 2010-09-09
I think the first link I gave you discusses a lot of gparted tasks. I do not like to move a lot of data around on a disk as it is slightly higher risk as all data has to be moved and verified. Make sure you have good backups.

It depends a lot on where your partitions are and where the space you have is. Partitioning is something best planned in advance. 

You can post this or a screenshot of gparted to show partition layout
```
sudo fdisk -lu
```

---

### Post by Insomnia64 on 2010-09-09
You can only have 4 primary partitions on any one hard drive and any partition with an operating system on it must be primary. I'm not sure how many operating systems you are running on it. To make more partitions you must first make an extended partition. This in itself is a primary partition so it will be necessary to remove one first. Once this is made other logical partitions can be created within it.

---

### Post by g_ramesh on 2010-09-10
> **oldfred said:**
> I think the first link I gave you discusses a lot of gparted tasks. I do not like to move a lot of data around on a disk as it is slightly higher risk as all data has to be moved and verified. Make sure you have good backups.

It depends a lot on where your partitions are and where the space you have is. Partitioning is something best planned in advance. 

You can post this or a screenshot of gparted to show partition layout
```
sudo fdisk -lu
```

Before reading your above reply I did the following (as I tried it y'day night)

OOPS! It seems I messed up XP :oops:

y'day night after going thru " [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) " I tried and moved the SWAP and Linux partition around and brought the unallocated space next to a primary partition where xp is loaded. Then I merged both and then moved the xp partition to right. 

Then when I tried to boot into XP it was showing fault /ntldr. Then I merged back the XP partition and unallocated sapce and tried boot again. Now also is shows the following message when I try to boot in to XP

" Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:
1. Insert your windows installation disc and restart your computer.
2. choose your language settings and then click "NEXT"
3.Click "Repair" your computer.

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

File: \ntldr
Status: OX0000225

Info: The selected entry could not be loaded because tha pplication is missing or corrupt.  "


I u/l the screenshots from GParted before and after I merged the unallocated space to xp partition and the link is 

" [http://www.4shared.com/file/kwy9JguJ/gparted1.html](http://www.4shared.com/file/kwy9JguJ/gparted1.html) "

and the output of fdisk -lu is given below

sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa3c6a3c6

   Device            Boot              Start                         End            Blocks                  Id                System
/dev/sda1                                  16126           236026979    118005427           f         W95 Ext'd (LBA)
/dev/sda2       *        236027904    561364991     162668544     7        HPFS/NTFS
/dev/sda3              561364992     565270527       1952768     82      Linux swap / Solaris
/dev/sda4               565270528     625141759      29935616   83          Linux
/dev/sda5                                 16128         236026979     118005426              7      HPFS/NTFS



Booting in to win 7 and Ubuntu is normal.

Unfortunately I do not have the installation disc of XP. Please tell me how to fix ntldr problem.

However I am able to access programs installed in XP thru win 7 and run them.

Note: I tried several times ti edit the fdisk -lu output but after saving it is becoming as above, sorry.

---

### Post by oldfred on 2010-09-10
Did the partition number that XP is in change, then you need to edit boot.ini. If it is missing ntldr you can copy it from backups on your drive.

[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 


You may also need to recover the boot sector, testdisk usually will do that.

This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

BOOTCFG  /rebuild
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

---

### Post by Dragynn on 2010-09-10
> **Mark Phelps said:**
> Sigh ... according to their site, this only works with Ext2/Ext3 partitions, and as has been said SEVERAL times in this thread, 10.04 installs by default in Ext4 partitions.

So, unless their site info is incorrect, this will not work with 10.04 filesystems.

[sourceforge.net/projects/ext2read/]("sourceforge.net/projects/ext2read/")

"Ext2Read is an explorer like utility to explore ext2/ext3/**ext4** files."

It reads the linux partition from windows okay, but won't let you open the actual file, just shows icons, on mine it will let me copy the file to my windows partition, but then immediately gives an error message and shuts down. 

typical windows nonsense, can't do anything natively, always needs an add-on program to do things i can do in Ubuntu with just a right-click, and programmers have to do endless bug-fixing and trial-and-error to accomplish a program that does the simplest of tasks.

---

### Post by g_ramesh on 2010-09-10
> **oldfred said:**
> Did the partition number that XP is in change, then you need to edit boot.ini. If it is missing ntldr you can copy it from backups on your drive.

[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

I think the partition number is not changed?  I had saved boot.ini earlier and seen the partition no. as 1 same as now. Otherwise how to check it?

I am able to boot into Ubuntu and checked up, under root of C:/ I have boot.ini with the following content:

"
; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" 
/NOEXECUTE=OPTIN /FASTDETECT  "

it is same as a copy which I earlier saved. Also ntldr, NTDETECT.COM and bootmgr are available under root of C: drive which is my XP partition. 

Please tell me what to do now?  
(As suggested in your reply other options let us try later please.)

---

### Post by oldfred on 2010-09-10
It looks like all the normal files are in the right places. The partition boot sector then is critical.

I have not used testdisk but many do. This will check if the backup boot sector is different and let you install it. Or testdisk does have a way to totally rebuild the boot sector.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

download or it is in Ubuntu's repositories - TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by g_ramesh on 2010-09-11
Sorry, now I think in the Disk management screen of Win 7 that the Drive letters C: and D: are interchanged ?

The screen shot taken is u/l and the link is  " [http://www.4shared.com/photo/-yt1Yvbx/Disk_Management_Screeshot.html](http://www.4shared.com/photo/-yt1Yvbx/Disk_Management_Screeshot.html) "

The E(C:/) is Win7 and C(D:/) is xp and I think these got interchanged  when I was merging the partitions in GParted. Can this happen?

After posting this I actually booted the pc with xp disk and selected repair option.

After a while it gave two options:

1: D:\Windows
2: C:\WINDOWS

when I selected option 1, it did not allow me to enter inside, when selected option 2 it went into windows dir of xp.

I think my doubt stated above is correct, is it not? ( i.e change of drive letters C and D).

Is fixboot C: will harm the pc in recovery console?

Later I stumbled upon bootscript from sourceforge.net which was mentioned in one of the posts here and Results.txt is u/l and link is 

[http://www.4shared.com/document/Ya7SScVL/RESULTS.html](http://www.4shared.com/document/Ya7SScVL/RESULTS.html)

please see.

---

### Post by oldfred on 2010-09-11
Normally whatever windows you boot is the c: drive and any other NTFS partitions become added letters.

You have installed win7 in a logical partition. Windows will not directly boot from a logical partition and only boots thru the primary partition that has windows and the boot flag (active partition).

Now your XP partition is part XP and part win7. I am not sure if you repair with XP  or with the win7 tools, I would think win7.

---

### Post by g_ramesh on 2010-09-16
thanks oldfred for your replies. I used EasyBCD from Neosmart.net and it has solved my problem.

---

