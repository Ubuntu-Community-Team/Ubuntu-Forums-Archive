---
title: "New To Ubuntu, Need a Little Advice on Installing"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by thehonorableflamingo on 2009-01-21
Hello everyone,

I am new to Linux, and I need a little help.  I have a laptop (IBM Thinkpad T60) that has been running Windows XP.  Without going into too much detail, I seem to be having some major registry corruption problems, although no one has been able to find any viruses.  I assume my best bet was to format my hard drive and do a clean install.  However, I don't have the Windows CD, and I can't really afford (nor do I want to) shell out the cash to buy a new copy.  Which brings me to why I am here.  I already have a computer that runs Windows, so I thought I might try out Linux, and Ubuntu seems to be one of the more user-friendly versions I have looked at.

So, now that I have made you read all that background, here is my question.  How should I proceed?  Can I wipe out Windows XP and then install Ubuntu?  Or must I?  Or will the installation of Ubuntu do that for me?  Any help would be greatly appreciated.

I apologize if these questions are a bit green-ish.  I have never uninstalled or installed an operating system before, and I don't really want to mess anything up.

Thanks!

---

### Post by x33a on 2009-01-21
you can retain your windows partition.

ubuntu's installer will let you install ubuntu on a different partition, and you will get windows in your bootloader menu after the install.

---

### Post by adult swim on 2009-01-21
hello honorable flamingo
if you download an ubuntu live cd (what is used to install ubuntu) when you get to step 4 of the install process, you can choose "guided-use entire disk" to wipe your drive and give it all to ubuntu.  once you have made the cd, you will need to boot your computer from it.  whenever you turn your computer on, when the bios screen appears, you will need to hit a key (it is different on different computers) to change the boot order.  once you find the key, hit it and choose to boot from the cd drive and you will be on your way.

---

### Post by thehonorableflamingo on 2009-01-21
Thanks for the replies.

The Windows XP registry on my laptop seems to be in such bad shape, I think I will just wipe the disk and start fresh with Ubuntu.

I will definitely stop back here if I have any other questions.  You have been very helpful.

Thanks again!

---

### Post by jrusso2 on 2009-01-21
You do realize if you delete the IBM backup partition you will have to buy XP to go back?

I would make backups at least of that Windows Recovery.  There is usually an IBM program that does this.

---

### Post by mrbiggbrain on 2009-01-21
a little off topic, you can always take it to your local computer store and they will have disks to install with.

back on topic, its really up to you, you could use gparted to make the windows drive smaller and then use free space to install ubuntu, then have a chance to mount it, and chainload it later. or just wipe the drive and move on.

---

### Post by laffinet on 2009-01-22
It might not be a bad idea to boot into the live CD, enter this in a terminal:

```
sudo fdisk -l
```

(lists your partitions)

and post the output here. That way people can tell if you have a recovery partition with XP on it, which you might want to back up before wiping the hard drive.

---

### Post by Vaedrah on 2009-01-22
Perhaps you could download a registry fix program e.g.

[http://www.3bsoftware.com/](http://www.3bsoftware.com/)

or from tucows

[http://www.tucows.com/](http://www.tucows.com/)

Some of these are "free and fix" downloads but many just point out "problems" and then ask for $$$ to fix them! From memory the 3B

   registryrepair_rrse08.exe

is free for home use.

If you want to try Ubuntu as a "dual boot" companion to windows then there are two preparation methods for this

**XP:**
1. Defrag the hard drive (so that the right hand view becomes clear space.
2. Run the Ubuntu CD with its *.iso file (windows may not burn this to CD without using another s/w package e.g. ir045_unicode.exe - free to download)
3. Install Ubuntu manually (you can leave XP on a small partition and add Ubuntu + swap file to the larger remaining partition.

**Vista**
Vista has a "shrink drive" feature that removes the defrag step. It may appear on your notebook but not work though (I found this on my Acer Aspire 5920 - now it runs Ubuntu 8.04 and has several "Virtual Machines" running on top using VirtualBox)

You can also use the XP method for Vista - providing the Vista OS will let you!

I suggest keeping a small windows "legacy" in case you come across a solution later on. Then again, unless you have favorite S/W that only runs on windows, then Ubuntu is certainly a good choice!

If you want to remove windows later on then you can then move the Ubuntu partition over (I think without loosing any Ubuntu files) or use the unused partition for file storage. (This notebook has 10 GB of FAT32 storage + 150 GB Ext3/Ubuntu - this FAT32 partition just stores s/w that I can load on to any new VM I may want to try - easier than using multiple CD's)

---

### Post by thehonorableflamingo on 2009-01-22
I decided to keep my Windows partition, at least for now, and would like a little advice, since I am pretty new to this.

I have a 120 Gig. hard drive which, as of now, has only one partition, devoted entirely to Windows.  I click "New Partition Table," which makes the only partition that I have read "free space."  Now I can create new partitions, including one for Windows I think.  How large should I make this partition (I assume I would make the first partition the Windows one)?  When I boot up Windows, the C:\ drive says it has about 75 Gigs. of free space.  That doesn't mean that the Windows partition needs to be 45 Gigabytes, right?

After that, I figure I can probably handle it.  I'll need to create a partition for Ubuntu of 10 Gig., and a swap partition of about 4 G., since I have 2 G. of RAM.  Does this seem correct?  Again, any advice is greatly appreciated.

---

### Post by angliski on 2009-01-22
Hi.

You won't need 4gig for swap, 250Mb will be ample. Also Ubuntu wont use anything like the amount you are proposing 4Gig will be more than enough.

Don't forget to change the boot order after burning the ubuntu .iso image so that it will boot from the CD for your install.

You will need a 700Mb writable CD ro burn the image to.

The bootable CD will set up live ubuntu on your system and put a folder called install on the desktop. Click on it and you will be guided through the process.

It might be an idea to print off things like your video card type, internet connection type, ie dial up or broadband, connection instructions etc, wireless card type if that is what you use.

Ubuntu installs most of the programmes you will ever need and theyre all free.

Linux will also write a prog called grub to your MBR so you can dual boot if you eveer want to sort something out from windows.

Hope this helps.

Steve

PS I'm new to this and I managed!!

---

### Post by thehonorableflamingo on 2009-01-22
Thanks for the help, it is greatly appreciated!

Do you have any advice on how large to make the Windows partition?  I'm assuming 10 Gig. or so would be enough, but I'd like to be sure before I go on.

Thanks!

---

### Post by laffinet on 2009-01-22
How much space does your windows installation use at the moment ? That plus a bit extra for future stuff should be the size of your windows partition.

Whatever you do, back up any important data before you start installing Ubuntu. If you know what you're doing it's pretty safe (although things can still go wrong), but from your comments I gather you're not too familiar with Ubuntu. You don't want to end up wiping everything by accident without a back up.

---

### Post by laffinet on 2009-01-22
Have you established if you have a recovery partition that you might want to keep ?

---

### Post by thehonorableflamingo on 2009-01-22
I am definitely quite new to Ubuntu, and I appreciate the help.  My Windows registry has had problems on the machine I am installing Ubuntu on for quite a while, so I don't have any important data left on it, I have transferred it all over.  In fact, there is really not a lot of harm done if the entire disk were to be formatted in the installation, which I considered doing.

However, I settled on trying to keep Windows in a separate partition.  I will try to type what I have here and maybe get a little feedback to make sure I have interpreted the install directions from this site correctly.

This is what I have in the "Prepare partitions" screen.

/dev/sda1 - do not use the partition - 15000MB
/dev/sda5 - swap - 501MB
/dev/sda6 - ext3 - 100002MB
/dev/sda7 - ext3 (mount /home) - 4523MB

Does this seem like an acceptable setup?  And all the boxes under the "Used" heading read "unknown," I'm not sure if that is significant.

I swear I'm going to get the hang of this thing sometime!  Thanks for the help.

---

### Post by laffinet on 2009-01-22
/dev/sda1 - do not use the partition - 15000MB
I'm assuming this is your windows partition. If so, all good. What file system is it ? If fat, fat32 or ntfs it's the windows partition.
/dev/sda5 - swap - 501MB
OK
/dev/sda6 - ext3 - 100002MB
/dev/sda7 - ext3 (mount /home) - 4523MB
You might want to swap these to around, /home is where all your data is kept and programs are installed, so it should be the biggest one. The root partition is fine with approx. 4 gig.
If you later need to change something you can always resize.

Don't know about the "unknown" bit, sorry. Wouldn't worry about it too much though.

---

### Post by thehonorableflamingo on 2009-01-22
I don't seem to have a recovery partition.

I typed the command you suggested into the terminal.  Here is what came up.

Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x53985398

   Device Boot      Start         End       Blocks    ID  System
 /dev/sda1  *           1       15505    117217768+    7  HPFS/NTFS

To me it looks like I only have 1 partition, and no recovery one.

Oh, and the /dev/sda1 was type ntfs, so it was the Windows partition.  There was no way I could see to resize it, since it was the only partition, so I just had to delete the partition so I could make new ones.

Thanks for the help!

---

### Post by laffinet on 2009-01-22
> **thehonorableflamingo said:**
> I don't seem to have a recovery partition.

Agree, looks like you don't have a recovery partition.

> **thehonorableflamingo said:**
> Oh, and the /dev/sda1 was type ntfs, so it was the Windows partition. There was no way I could see to resize it, since it was the only partition, so I just had to delete the partition so I could make new ones.

You are aware that this deletes your windows installation ?

---

### Post by thehonorableflamingo on 2009-01-22
I had a suspicion that it might not work the way I had hoped, but I didn't know that it would delete the Windows installation.

I'm having trouble finding how to resize the Windows partition instead of deleting it.  The documentation that I have been reading is apparently using a different partitioning software, since I can't find anything that allows me to resize.  I have no free space to partition until I delete the original one.

---

### Post by laffinet on 2009-01-22
> **thehonorableflamingo said:**
> 
I'm having trouble finding how to resize the Windows partition instead of deleting it.  

There should be an option to "manual partition", which is not hard to do. Do you see that ? What options do you have ?

---

### Post by thehonorableflamingo on 2009-01-22
When I get to the partitioning step, I have 2 options there is "Guided - use entire disk" and "Manual".

I clicked on manual, and then forward.

When I get to the next screen it shows my hard drive /dev/sda, and under that is the only partition, which is /dev/sda1, type ntfs, and it is using the entire drive.

If I highlight that, I have the option to 'edit partition' or 'delete partition', I click on edit, but it just allows me to change how the partition is used and where it is mounted.  I can't seem to find an option to resize anywhere.

As always, I appreciate your continued help.

---

### Post by laffinet on 2009-01-22
You could also boot the LiveCD, start gparted from there and do your partitioning. 
Or download a standalone [gparted liveCD]("http://linux.softpedia.com/progDownload/GParted-LiveCD-Download-8864.html") and do the same.

---

### Post by laffinet on 2009-01-22
> **thehonorableflamingo said:**
> When I get to the partitioning step, I have 2 options there is "Guided - use entire disk" and "Manual".

I clicked on manual, and then forward.

When I get to the next screen it shows my hard drive /dev/sda, and under that is the only partition, which is /dev/sda1, type ntfs, and it is using the entire drive.

If I highlight that, I have the option to 'edit partition' or 'delete partition', I click on edit, but it just allows me to change how the partition is used and where it is mounted.  I can't seem to find an option to resize anywhere.

As always, I appreciate your continued help.

That seems to be the right section. When right clicking on the partition, what options do you have ?

Also, I'm assuming you booted from a Ubuntu CD and chose the option to install. Correct ? Just checking...

---

### Post by thehonorableflamingo on 2009-01-22
I am booting from an Ubuntu CD, and I am installing from there.

When I right-click the partition that has Windows on it, I have the option to edit or delete the partition, or to undo changes to partitions.  The last one is of no consequence at the moment, since I have already undone my changes.

---

### Post by laffinet on 2009-01-22
> **thehonorableflamingo said:**
> I am booting from an Ubuntu CD, and I am installing from there.

When I right-click the partition that has Windows on it, I have the option to edit or delete the partition, or to undo changes to partitions.  The last one is of no consequence at the moment, since I have already undone my changes.

I'm confused ;)

When selecting edit, what do you get ? You should be getting to something like this: [IMG]http://gparted.sourceforge.net/screens/gparted_5_big.jpg[/IMG]

Do you have something like this (one line only for you,obviously): [IMG]http://gparted.sourceforge.net/screens/gparted_1_big.jpg[/IMG]

---

### Post by laffinet on 2009-01-22
Stab in the dark (doesn't make sense, but try nonetheless): highlight the partition, select "partition" from top menu, select unmount.

Then right click the partition again and see if you've got a resize option.

---

### Post by laffinet on 2009-01-23
One other thing: is there room on the windows partition ? What does gparted report ? What does windows report ?

You might want to boot windows and run defrag a couple of times. Then try again.

Sorry, I'm flooding you with suggestions, but I'll be away from my computer for a while soon. Trying to give you lots of things to try...

---

### Post by thehonorableflamingo on 2009-01-23
The problem, I am guessing, is that the partitioner that is on my LiveCD of Ubuntu is not gparted, but something else entirely.  I'm not sure why this is, as today was the first time I have downloaded and made an Ubuntu CD, so I should have an up-to-date release.

I got it from this page [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download).

Perhaps the difference is because I downloaded the 32-bit version?

---

### Post by thehonorableflamingo on 2009-01-23
I appreciate the suggestions very much.

I am considering just letting Ubuntu use the whole drive, and erasing Windows.  For whatever reason, I can't really run anything in Windows due to its problems, and as I mentioned, I really don't have any files on the computer that I need.

I have another computer that uses Windows, which I use for most of my day to day work.  I figure even if I don't like Ubuntu, I still have a computer with Windows, and I am really no worse for the wear.

---

### Post by laffinet on 2009-01-23
That could indeed be the problem :D

I thought gparted was still part of the install CD. 32 bit should have nothing to do with it.

I haven't installed 8.10 from scratch, only updated from Gutsy Gibbon, which used gparted.

Can you download a gparted liveCD ?

---

### Post by laffinet on 2009-01-23
> **thehonorableflamingo said:**
> I appreciate the suggestions very much.

I am considering just letting Ubuntu use the whole drive, and erasing Windows.  For whatever reason, I can't really run anything in Windows due to its problems, and as I mentioned, I really don't have any files on the computer that I need.

I have another computer that uses Windows, which I use for most of my day to day work.  I figure even if I don't like Ubuntu, I still have a computer with Windows, and I am really no worse for the wear.

That is obviously the easy option. Up to you, try a bit longer and hopefully keep your windows OR take the plunge and delete the whole thing.

---

### Post by thehonorableflamingo on 2009-01-23
I could do that.  Do I use the LiveCD for gparted first, and then replace it with the Ubuntu CD?

---

### Post by laffinet on 2009-01-23
Sorry, got to go. Might be back later.

---

### Post by laffinet on 2009-01-23
> **thehonorableflamingo said:**
> I could do that.  Do I use the LiveCD for gparted first, and then replace it with the Ubuntu CD?

What you do is boot the gparted liveCD, do your partitioning. Then put the Ubuntu CD in and reboot, choose install, off you go.

Once you get to the partitioning bit you should see all your partitions.

As mentioned, got to go, sorry.

---

### Post by thehonorableflamingo on 2009-01-23
Thanks a lot!  I will try that.  You have been a great help, and I really appreciate it.

---

### Post by laffinet on 2009-01-23
No worries.

Will be back from time to time, let us know how you go.

---

