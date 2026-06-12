---
title: "partitioning will or won't wipe out Win fiiles?"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by jrnsr on 2011-05-09
Ubuntu 11.04 new installation on new HP AMD64 computer.  I tried installing without Wubi but got NO FILE SYSTEM...error.  The correction procedure was explained that the drive will require added partitioning.  
I thought I read that the repartitioning would move files in the process, but when exploring the partitioning, the warning says files will be deleted.
New 350 Gig hard drive has just under 70 Gb in Windows files.

Do I dare redo partitions or should I live with Wubi installation?

---

### Post by rosencrantz on 2011-05-09
I assume your default setup is one big partition?
In that case, the partitioner has no free space to create your Ubuntu partition in; you'll have to resize the Windows partition first. This usually doesn't lead to data loss, however, I'd backup important files first. Also, do a defragmentation on Windows to have all your data in a big chunk on the partition before resizing.
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

---

### Post by coffeecat on 2011-05-09
You have a Hewlett Packard computer. Almost certainly it comes with four primary partitions set up already. The mbr partition table scheme which the machine uses allows a maximum of four primary partitions. This is probably the cause of your problem. The only way round this - I've had to do this myself on a HP machine - is to delete one of the primary partitions so that you can create an extended partition in which you can create a number of logical partitions for Ubuntu. The question is: which partition do you delete?

Boot up the live Ubuntu 11.04 CD and choose "try Ubuntu". If that takes you to the Unity desktop (dock-like launcher on the left), click on the Ubuntu button top left and type "Gparted" and open the Gparted application. If you get the classic desktop (panels top and bottom) choose Gparted from the System > Applications menu.

Take a screenshot of the open Gparted window (alt+Printscreen) and post that so that we can see what your partition layout is like.

---

### Post by jrnsr on 2011-05-11
Screenshot attached (hopefully).  I appreciate the advice.

After 3 hours trying to backup Windows 7 and wasting 4 DVDs, I'm awaiting arrival of a 500 GB USB drive to backup hard drive.
  
By the way, this new computer did not come with a Win 7 disc.

---

### Post by Hedgehog1 on 2011-05-12
Once you have your data backed up, may I suggest a dual-boot install of Ubuntu (not WUBI)?

Here is my quick tutorial on installing on an HP system with all four primary partitions already taken.  The partition you may choose to delete may or may not be /dev/sda3, so you may alter the partition being deleted.

[SIZE="3"]When all four primary partitions are taken (the HP install)[/SIZE]

[SIZE="4"][COLOR="DarkOrange"]First how it looks in Windows:[/COLOR][/SIZE]
[IMG]http://img859.imageshack.us/img859/9104/hp4partitions01.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]What it looks like in gparted off the LiveCD:[/COLOR][/SIZE]
[IMG]http://img859.imageshack.us/img859/8806/hp4partitions02.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Right click on sda3 and select 'Delete':[/COLOR][/SIZE]
[IMG]http://img856.imageshack.us/img856/2164/hp4partitions03.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the 'check' mark button to really make the change:[/COLOR][/SIZE]
[IMG]http://img190.imageshack.us/img190/1732/hp4partitions04.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Right Click, on empty area, select new and create extended sda3 (Press that check mark button again...):[/COLOR][/SIZE]
[IMG]http://img69.imageshack.us/img69/5967/hp4partitions05.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create your sda5 Ubuntu partition, leave a little room for swap later (Format this ext4 - and press that check mark button again.):[/COLOR][/SIZE]
[IMG]http://img863.imageshack.us/img863/4839/hp4partitions06.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create sda6 and make it swap space:[/COLOR][/SIZE]
[IMG]http://img855.imageshack.us/img855/3999/hp4partitions07.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the check mark button again[/COLOR][/SIZE]

---

### Post by Hedgehog1 on 2011-05-12
[SIZE="4"][COLOR="DarkOrange"]You are ready to install Ubuntu:[/COLOR][/SIZE]
[IMG]http://img864.imageshack.us/img864/2449/hp4partitions08d.png[/IMG]

[SIZE="4"][COLOR="DarkOrange"]
Once your partitions are laid out, you will start the install and eventually get to the **Disk Space Allocation** screen.  

If you are installing Natty/11.04, select the '**Something Else**' option.

If you are installing 10.04 or 10.10, select the '**Specify Partitions Manually (Advanced)**' option.[/COLOR][/SIZE]

[SIZE="4"][COLOR="DarkOrange"]And you will get to here:[/COLOR][/SIZE]
[IMG]http://img849.imageshack.us/img849/9937/hp4partitions10.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]We will add some extra data to sda5 and sda6.  With sda5 highlighted, press the [CHANGE] button:[/COLOR][/SIZE]
[IMG]http://img861.imageshack.us/img861/5274/hp4partitions11.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]These settings prepare the partition to be exdt4, '/'.[/COLOR][/SIZE]
[SIZE="4"][COLOR="DarkOrange"]Repeat the steps for the swap area (This usually set itself up OK) :[/COLOR][/SIZE]
[IMG]http://img26.imageshack.us/img26/4934/hp4partitions12.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]You are ready to install.  Press [Install Now].[/COLOR][/SIZE]
[IMG]http://img857.imageshack.us/img857/6342/hp4partitions13.png[/IMG] 
[SIZE="4"][COLOR="DarkOrange"]This is what the drive looks like in the 'Disk Utility' in Ubuntu after the load is complete:[/COLOR][/SIZE]
[IMG]http://img852.imageshack.us/img852/3987/hp4partitions14.png[/IMG]  

***The Hedge***

:KS

---

### Post by Allavona on 2011-05-12
Did I just see someone advise the OP to delete their recovery partition?

---

### Post by wildmanne39 on 2011-05-12
> **jrnsr said:**
> Ubuntu 11.04 new installation on new HP AMD64 computer.  I tried installing without Wubi but got NO FILE SYSTEM...error.  The correction procedure was explained that the drive will require added partitioning.  
I thought I read that the repartitioning would move files in the process, but when exploring the partitioning, the warning says files will be deleted.
New 350 Gig hard drive has just under 70 Gb in Windows files.

Do I dare redo partitions or should I live with Wubi installation?

Hi, I have an HP computer also,make sure you leave your recovery partition as well as your windows partition. Both should be ntfs.:)

---

### Post by arpanaut on 2011-05-12
Once you have your data backed up to external media, and created the recovery disks with the HP tools, there should be no issue with deleting the Recovery Partition.

HP documentation even says that you can do this, just be sure the recovery disks have been correctly created.

---

### Post by coffeecat on 2011-05-12
> **arpanaut said:**
> Once you have your data backed up to external media, and created the recovery disks with the HP tools, there should be no issue with deleting the Recovery Partition.

HP documentation even says that you can do this, just be sure the recovery disks have been correctly created.

Since both the Windows partitions (sda1 and sda2) need to be kept, the choice is between deleting the recovery partition and deleting the HP tools partition. You could delete either once you have made your recovery disks. After I had made a set of recovery disks with a HP machine, I decided to delete the HP tools partition. But as added double-insurance I made ISOs of the four recovery disks, and made images of both the recovery HP tools partitions with Macrium Reflect. And images of the Windows boot and C: partitions with Macrium Reflect too! I believe in being thorough. :)

---

### Post by mastablasta on 2011-05-12
^^uf tripple or quadruple backup....
 
anyway two defragmenattions and then running check disk before partitioning will:
1. move data that is now scatered in clusters all over disk into one place (on beginning of disk).
2. it will verify and fix any disk errors created by these files. 
 
then you can split the disk with practicly no worries to your data. still, i would back it up just in case.
 
back in the 90's i remember that red hat wanted to be installed in beginning of disk drive. the result was that i had to punch a hole between data to squeeze the ne partition in there. no data was lost. luckilly this is not necessary anymore. things are a lot simpler and safer nowadays.

---

### Post by jrnsr on 2011-05-12
I really appreciate the easy-to-follow "bread crumb trails" to partitioning.

As I mentioned, the new drive is 350GB and I've just ordered a 500Gb USB drive for backup (needed to upgrade my remote drive anyway).

While trying to backup with DVDs, I see Win 7 offers a variety of backup schemes, with no really explanation of functions.  Which one, or ones, would be recommended?
Right now, this computer has really only the Win 7 operating system and the CAD programs.  My focus is mainly to reinstall just these programs on catastrophic failure.

Another question... if I purchase another notebook drive and install it, can the backup drive spoon feed the programs onto a fresh drive, ie cloned a hard drive?

---

### Post by rosencrantz on 2011-05-13
> **jrnsr said:**
> 
Another question... if I purchase another notebook drive and install it, can the backup drive spoon feed the programs onto a fresh drive, ie cloned a hard drive?

Official Microsoft howto:
[http://support.microsoft.com/kb/249694](http://support.microsoft.com/kb/249694)
Edit: I thought this was more recent, but it's Vista and below. For Win7, have a look at Windows Restore or similar products. Caveat: Never tried any of them, I always axe my Windows when I change hard drives...

---

### Post by raydeen on 2011-05-13
Here's another suggestion: Download VirtualBox ([http://www.virtualbox.org/](http://www.virtualbox.org/)) and create an Ubuntu virtual PC and install to that.. It looks like you have plenty of hard drive space and this will negate the need to do any partitioning. You'll be able to have both systems running at the same time albeit at the cost of a slight performance hit in speed and possibly graphics (although if you've got a decent graphics card in your machine you may get all the fancy graphics bells and whistles - my Dell does).

---

### Post by Dutch70 on 2011-05-13
I'm not sure if anyone has mentioned this already, but to add to the info you've already gotten. You can create another logical partition & put your recovery partition and/or HP Tools back on your computer.

---

### Post by jrnsr on 2011-05-14
Thanks all.

Success... used gparted live cd

---

### Post by Dutch70 on 2011-05-14
> **jrnsr said:**
> Thanks all.

Success... used gparted live cd

Great! 

Don't forget to mark this thread "Solved" with "Thread Tools" at the top of the page when your satisfied that it is solved.

---

