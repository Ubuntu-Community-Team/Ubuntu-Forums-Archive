---
title: "Trying to Install Ubuntu 9.04 next to a corrupt WinXP partition"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by texla on 2009-08-12
Hey all - (reposting this with a Ubuntu prefix:)
I'm trying to install Ubunto 9.04 on a donated HP Pavillion (200GB SATA, 512MB RAM, Intel4) that has a defective Win XP on it. The XP is already on a 8GB partition. Currently, the computer will only start if I set it to load from the CD drive and that's how I got in to start the Ubuntu Live CD. As good as Ubuntu looks, I think I may never try to fix the XP on this machine. But just in case, I want to try to keep the xp partition during my ubuntu install for now. However I would like to set the computer to run ubuntu from now on. 

It has been difficult finding partition info related to this but I believe this how to page looks helpful: [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
But it shows their installation as using one partition for the whole disk and then separating out the Ubuntu. Should I keep the WinXP partition for now and then install Ubuntu on a partition of the Free space? Any other things to consider related to the HP Pavillion or SATA drives or anything?

Any advise before I go ahead with this would be greatly appreciated!

thanks!

---

### Post by Jaunty Jackalope on 2009-08-12
> **texla said:**
> Hey all - (reposting this with a Ubuntu prefix:)
I'm trying to install Ubunto 9.04 on a donated HP Pavillion (200GB SATA, 512MB RAM, Intel4) that has a defective Win XP on it. The XP is already on a 8GB partition. Currently, the computer will only start if I set it to load from the CD drive and that's how I got in to start the Ubuntu Live CD. As good as Ubuntu looks, I think I may never try to fix the XP on this machine. But just in case, I want to try to keep the xp partition during my ubuntu install for now. However I would like to set the computer to run ubuntu from now on. 

It has been difficult finding partition info related to this but I believe this how to page looks helpful: [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
But it shows their installation as using one partition for the whole disk and then separating out the Ubuntu. Should I keep the WinXP partition for now and then install Ubuntu on a partition of the Free space? Any other things to consider related to the HP Pavillion or SATA drives or anything?

Any advise before I go ahead with this would be greatly appreciated!

thanks!
When you run the installation from the CD, it should give you repartitioning choices. Before the actual installation proceeds it gives you a chance to configure your settings (so it won't clear Windows unless you choose that option). Hope this helps...

---

### Post by texla on 2009-08-12
Yes it does.  I'm just wondering if need to follow all of the suggestions in the above link about making the root file and then a swap file and then also my question is will it work just fine if I keep the win partition separate and start ubuntu on a new partition?

---

### Post by Jaunty Jackalope on 2009-08-12
> **texla said:**
> Yes it does.  I'm just wondering if need to follow all of the suggestions in the above link about making the root file and then a swap file and then also my question is will it work just fine if I keep the win partition separate and start ubuntu on a new partition?
Is there a reason for keeping the Windows XP (if it does not work)? And for your second question, do you mean dual-booting so that it gives you the option of using either OS?

---

### Post by texla on 2009-08-12
> **Jaunty Jackalope said:**
> Is there a reason for keeping the Windows XP (if it does not work)? And for your second question, do you mean dual-booting so that it gives you the option of using either OS?
Yes, dual-booting seems to be what I'm trying to do.  I'm just trying to keep the WinXP for now  in case I can fix it at a later date.  I would like the computer to boot straight to Ubuntu however so if it needs to use XP at all for a dual boot, I don't think this will work.

---

### Post by Jaunty Jackalope on 2009-08-12
> **texla said:**
> Yes, dual-booting seems to be what I'm trying to do.  I'm just trying to keep the WinXP for now  in case I can fix it at a later date.  I would like the computer to boot straight to Ubuntu however so if it needs to use XP at all for a dual boot, I don't think this will work.
If XP is not running, then I think you might need to use a recovery disk or install the OS anew. If you are dual-booting, I think it will always give you the option and will not boot straight into either. So if booting straight into Ubuntu is what you want then I think you would have to use the whole disk, right?

---

### Post by texla on 2009-08-12
> **Jaunty Jackalope said:**
> If XP is not running, then I think you might need to use a recovery disk or install the OS anew. If you are dual-booting, I think it will always give you the option and will not boot straight into either. So if booting straight into Ubuntu is what you want then I think you would have to use the whole disk, right?
Yes it seems that way - But I think there may be no harm in trying the double boot option by leaving the old XP on here first and if it doesn't fly right, I can go back and choose the entire disk option.  Just would like to see if it works and if I can avoid erasing the XP that would be a plus.  Thanks for your help!

---

### Post by Jaunty Jackalope on 2009-08-12
> **texla said:**
> Yes it seems that way - But I think there may be no harm in trying the double boot option by leaving the old XP on here first and if it doesn't fly right, I can go back and choose the entire disk option.  Just would like to see if it works and if I can avoid erasing the XP that would be a plus.  Thanks for your help!
No problem, glad I could help somehow.

---

### Post by mike555 on 2009-08-12
I think you might want to make the XP partition bigger , 8GB is not enough and might be the problem with it? 
   When you are ready to install Ubuntu pick "manual" install and make sure you don't write over XP (if you want to keep it)you really don't need to worry about separate partitions for Ubuntu , just let it install where you want it ......... when you restart you will see the Grub bootloader ,where you can pick XP or Ubuntu , or just wait and it will load Ubuntu .........

---

### Post by texla on 2009-08-12
OK - one more thing for you or whoever - This is a project computer so if I can manage to keep all the files intact, I will be very happy about it.  Right now there's a ton of data and programs on the second partition (about 40Gb of the 192 GB).  When I go through the manual partition option, the instructions I have say to delete this partition and then add the root partition, then make the rest a home partition.  If I do this will all of those files be saved automatically in the home partition or do they get deleted?  Is it better to edit this partition to add Ubuntu?

---

### Post by emeraldgirl08 on 2009-08-12
If you need files off the Xp. Use the liveCD to pull files off the Xp partition. 

You could also install Ubuntu and then still be able to access the Xp part to get the files you need.

Also:

If you would like to try and save that Xp side. By all means resize that partition! It seems a little too small for Windows. I run Xp Pro with an older lappy and it uses almost 10gb.

---

### Post by salb4 on 2009-08-12
Try this for partitioninghttp://www.giveawayoftheday.com/paragon-partition-manager-9-5-professional-english-version/

---

### Post by salb4 on 2009-08-12
for partitioning, try this: [http://www.giveawayoftheday.com/paragon-partition-manager-9-5-professional-english-version/](http://www.giveawayoftheday.com/paragon-partition-manager-9-5-professional-english-version/)

> **texla said:**
> OK - one more thing for you or whoever - This is a project computer so if I can manage to keep all the files intact, I will be very happy about it.  Right now there's a ton of data and programs on the second partition (about 40Gb of the 192 GB).  When I go through the manual partition option, the instructions I have say to delete this partition and then add the root partition, then make the rest a home partition.  If I do this will all of those files be saved automatically in the home partition or do they get deleted?  Is it better to edit this partition to add Ubuntu?

---

### Post by texla on 2009-08-12
> **mike555 said:**
> I think you might want to make the XP partition bigger , 8GB is not enough and might be the problem with it? 
   When you are ready to install Ubuntu pick "manual" install and make sure you don't write over XP (if you want to keep it)you really don't need to worry about separate partitions for Ubuntu , just let it install where you want it ......... when you restart you will see the Grub bootloader ,where you can pick XP or Ubuntu , or just wait and it will load Ubuntu .........
OK so the nuts and bolts question: I'm in the the manual option,  what I see is a  dev/sda1 FAT32 that is 8GB (with winXP on it) and I see a dev/sda2 ntfs with 192GB (with a ton of data and stuff).   Where should I put the Ubuntu so I hopefully don't lose either winxp or the data.  

also, I do like the idea about changing the partition size of the winxp later to see if it gets it working.

---

### Post by emeraldgirl08 on 2009-08-12
I'm not a total M$ guru but I think it needs adequate breathing room in order to work right.

Like room for Pagefiling etc.

If there isn't room for M$ version of swap then I'm not sure what effects that would have.

If you need to resize and partition use Gparted. It's on the LiveCD by the way.

Go to Preferences>>Administration>>Partition Manager.

You can modify to your hearts content.

Also Xp first. Ubuntu Second. Swap Third. Fat 32 last.

At least that's how I have my M$ and Linux coop going :)

---

### Post by texla on 2009-08-12
> **emeraldgirl08 said:**
> I'm not a total M$ guru but I think it needs adequate breathing room in order to work right.

Like room for Pagefiling etc.

If there isn't room for M$ version of swap then I'm not sure what effects that would have.

If you need to resize and partition use Gparted. It's on the LiveCD by the way.

Go to Preferences>>Administration>>Partition Manager.

You can modify to your hearts content.

Also Xp first. Ubuntu Second. Swap Third. Fat 32 last.

At least that's how I have my M$ and Linux coop going :)

Ah, that's what I'm talking about - thanks for the rundown on the order and the gparted tip. I'll do the repartitioning first and then see where the install leads me... hopefully to a happy place :P

---

### Post by texla on 2009-08-12
OK - big change in my evaluation.  I was wrong in thinking that the first 8gb was windows.  It's an HP recovery disk.  The second partition must have everything on it, the data and the bad winxp OS.  Plus, Gparted says that the second partition alsoo has a bunch of missing clusters so maybe I need to do something else altogetehr like more diagnostics or something first here.  Whoops

---

### Post by emeraldgirl08 on 2009-08-12
Are you able to press F8 upon booting to get a menu for M$???

If you are then try to use the option for command lines.

Try either C: CHKDSK or just CHKDSK by itself.

That scandisks your Xp partition and attempts repairs.

I believe that command will sort out all the sectors in that partition.

---

### Post by lkraemer on 2009-08-12
UPDATED: 
Since that machine is an HP, does it have a RECOVERY Partition?
Most Compaq and HP machines don't ship with a set of recovery
CD's, but instead have a Recovery Partition and you have the
option of making ONE set of CD's to restore the OS in case of trouble.

REMEMBER: there is a MAXIMUM LIMIT of FOUR PRIMARY PARTITIONS on any
one PHYSICAL HARD Drive.  If you already have an 8 Gig Recovery Partition,
and a 192 Gig XP partition, then you only have two partitions
remaining.  Unless, you use an Extended Partition you can't make a
/, and a /home, and /swap because you are over the limit of four.

Dual Boot Info:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Here is what I would suggest:
Boot the Ubuntu LiveCD and run Gparted:

Shrink the XP Partition to about 60 Gig. (A Fresh install takes about
6 Gig, so that will leave you some working room.)  Then I'd move the
8 Gig immediatley after the 60 Gig. Then I'd start with a SWAP Partition
that was 2 Times your RAM.  The remainder would be for Ubuntu.  (Four
primary used)

Later I'd purge XP and the Recovery, and make a Ubuntu Only Install,
because after you run Ubuntu for a year, you won't boot XP.
(15 Gig Ubuntu = /, 2 Times RAM = SWAP, remainder = /home)

Then I'd download the following and play:
1.  SystemRescue CD
2.  UBCD (Ultimate Boot CD and also a copy for Windows)
3.  Clonezilla
4.  Gparted
5.  Knoppix
6.  Testdisk & Photorec

Maybe you can repair the XP OS, but it is unlikely.


UPDATE:
You just posted that the 8 Gig is a recovery partition.
Typically the OS is first (C:) and the Second Partition is
the Recovery Partition (D:).  And they are in that order.
The Recovery Partition is always immediately after the
OS.  You can verify this by booting the XP OS and using
Manage Disks to make sure.  If it isn't that way, I'd
be fooled.

Good Luck.

LK

---

### Post by emeraldgirl08 on 2009-08-12
> 
Later I'd purge XP and the Data, and make a Ubuntu Only Install, because
after you run Ubuntu for a year, you won't boot XP.

:lolflag:

Ha ha ha. Don't forget though Ikraemer some of us here are still somewhat or total NOOBS at comp stuff. We need the familiarity of Gatesville sometimes and/or need it for incompatible programs in Wine.

---

### Post by texla on 2009-08-12
No, F8 does nothing - just loops back to the black screen asking for safe mode - I was able to get the system to boot from the Cd and that's where I got into Ubuntu.  So the repartitioning doesn't look like it will work from Gparted and I might have to see if there's any disk fixes out there on sourceforge that I can load as an iso unless there's one on the Live Cd.

---

### Post by emeraldgirl08 on 2009-08-12
If you can get into the menu for safe mode there should be a choice of safe mode w/ command prompt. 

Choose that selection.

Go into your admin account.

And enter CHKDSK.

Let's see if that sorts out some problems with your XP.

---

### Post by louieb on 2009-08-12
> **texla said:**
> Gparted says that the second partition also has a bunch of missing clusters so maybe I need to do something else altogetehr like more diagnostics or something first here.  Whoops

Don't believe I would touch that that drive -  little alone try to install or repair an OS on it until any and all critical data has been copied off to  another device.  Unless your very good and  very lucky.

There is a direct correlation between # of bad clusters and how much longer a drive will continue to work.  Modern hard drives have self diagnostic tools built in. and  if you get a [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic")  (nice open source rescue CD) it has **GSmartMon**   that will allow you to examine the health of the drive.

BTW** GSmartMon** will be available in the next release of Ubuntu. It gets it data from **smartmontools** a command line utility thats available in the Ubuntu repositories now. 
> The smartmontools package contains two utility programs (smartctl and smartd)
to control and monitor storage systems using the Self-Monitoring, Analysis and
Reporting Technology System (S.M.A.R.T.) built into most modern ATA and SCSI
hard disks. It is derived from the smartsuite package, and includes support
for ATA/ATAPI-5 disks. It should run on any modern Linux system.

---

### Post by texla on 2009-08-12
> **emeraldgirl08 said:**
> If you can get into the menu for safe mode there should be a choice of safe mode w/ command prompt. 

Choose that selection.

Go into your admin account.

And enter CHKDSK.

Let's see if that sorts out some problems with your XP.
Nope - it loops on that choice, too - I'm worried less and less about keeping the XP but I'm  going to use the Ubuntu Live CD for now and try to download some fixes - It's amazing how easy this OS is to use by the way!  Starting up on the internet from the Live CD just required plugging in the DSL cable - that's it!  Crazy - and all this is being done on a dead computer supposedly - I don't think enough people know how easy it could be to get their computers up and running again after a windows crash  -  And this has  a much better feel to it than XP -  very cool ! Now, I'll see what I can salvage....

---

### Post by emeraldgirl08 on 2009-08-12
True about copying the files first!

Thanks Louie.

Forgot about that :)

---

### Post by texla on 2009-08-12
> **louieb said:**
>  if you get a [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic")  (nice open source rescue CD) it has GSmartMon   that will allow you to examine the health of the drive.

Thanks!  Going to get it right now...

---

### Post by lkraemer on 2009-08-12
texla,
Since you have the Recovery Partition, you should be able to boot
into a Recovery mode that will restore your XP partition to Factory
state, but it will wipe out any software that was installed.  Since
the software wasn't installed by you, you won't likely miss it.
And since the Data isn't yours, you won't miss it either!

REMEMBER, you can always open the case and find the Manufacture of the
Drive, and go to their site and download their Diagnostics to test
the Drive.  You can also always purchase Spinrite from Gibson Research
to test the drive.  Spinrite will work on IDE and SATA drives now.
Older versions just worked on IDE type drives.  It is good software.

lkraemer

---

### Post by texla on 2009-08-13
> **lkraemer said:**
> texla,
Since you have the Recovery Partition, you should be able to boot
into a Recovery mode that will restore your XP partition to Factory
state, but it will wipe out any software that was installed.  Since
the software wasn't installed by you, you won't likely miss it.
And since the Data isn't yours, you won't miss it either!

REMEMBER, you can always open the case and find the Manufacture of the
Drive, and go to their site and download their Diagnostics to test
the Drive.  
lkraemer

Thanks, lkraemer - Ran the partition magic test and it cleared.  Ran two disk tests from Seagate - short and long - all passed with no errors.  And I checked out  the recovery partition.  It just boots to a wallpaper with the moon and the sea - very nice but not the recovery I was looking for - Guess I'll go ahead and see how the install does as a double boot for now - I know it's a bad idea and the XP on this thing is near dead -but I really want to see it and see what gets lost if anything.

---

### Post by Yuguar on 2009-08-13
Hi to you all,



Sorry to barge in but I have on my hands a laptop that has had some xp virus and mbr or whatever went south and Ubuntu Hardy is installed rather quick so one can use the machine...

This is fdisk list

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        1926    15414367+   7  HPFS/NTFS
/dev/sda3            1927        4864    23599485    f  W95 Ext'd (LBA)
/dev/sda5            1927        3401    11847906    7  HPFS/NTFS
/dev/sda6            3402        4796    11205306   83  Linux
/dev/sda7            4797        4864      546178+  82  Linux swap / Solaris


Can I repair XP boot and how to make it dual boot(xp repair console writing new mbr ? )...I can see the old c: and d: and files but some installed programs have info within that I cant acces and thats what I need. 

Thanks for the info ..Im still The noob for this boot sh....

---

### Post by texla on 2009-08-13
OK now I have XP restored - after installing ubuntu, during the double boot stage, it must have thought that the recovery partition was xp so when I chose xp just to see what it did, it actually loaded the recovery partition and this time for some reason it worked and restored xp.  Now I have a partition mess and no ubuntu.
 I'm moving this to a new thread since it's now a working xp double boot issue:

[http://ubuntuforums.org/showthread.php?p=7779791#post7779791](http://ubuntuforums.org/showthread.php?p=7779791#post7779791)

---

