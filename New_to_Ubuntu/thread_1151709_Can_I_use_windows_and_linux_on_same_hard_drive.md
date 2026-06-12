---
title: "Can I use windows and linux on same hard drive?"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by Entrenched on 2009-05-07
I'm having some real problems using some necessary software with linux, and am wondering, can I install both windows and linux on my computer? You know, partition the hard drive in 2 and have one partition linux, the other windows? I do not know if this can be done since the both use totaly different file systems. Also, I know that creating a partition will slow down my computer a bit. HOwever, I need to use certain things, for example my printer, and there is no linux drivers that allow it's use. This is not the only problem though. Anyhow, back to my question, can this be done? Thanks all.

---

### Post by b@sh_n3rd on 2009-05-07
Well, it depends on how much of total and free space you've got on your drive. I'm not sure of resizing the partition though but to tell you the truth, I installed Ubuntu once on my dad's computer on a seperate partition on the same HDD. It worked good enough but trouble comes when you wanna get rid of Ubuntu. But it IS possible.

---

### Post by fatality_uk on 2009-05-07
> **Entrenched said:**
> I'm having some real problems using some necessary software with linux, and am wondering, can I install both windows and linux on my computer? You know, partition the hard drive in 2 and have one partition linux, the other windows? I do not know if this can be done since the both use totaly different file systems. Also, I know that creating a partition will slow down my computer a bit. HOwever, I need to use certain things, for example my printer, and there is no linux drivers that allow it's use. This is not the only problem though. Anyhow, back to my question, can this be done? Thanks all.

Yes uou can, easily.

If you're happy to, Ubuntu will create a new partition for you when you install it.

Even better, you can use WUBI to install Ubuntu "inside" a copy of Windows without the need to create a new partition.

Just run the install disc from Windows and fllow instructions.

I apologise for my poor spelling above. I have taken myself outside and given myself a HUGE slap!!!

---

### Post by b@sh_n3rd on 2009-05-07
yup, wubi's cool too. Only thing is it's performance is not the same as installing it on it's own partition. But then again, wubi is pretty much safe if you are not thinking of using ubuntu full time.

PS: [fatality_uk]("http://ubuntuforums.org/member.php?u=442924"), what elephants were running on linux? :lolflag:

---

### Post by aktiwers on 2009-05-07
You could try out VirtualBox if you don't need apps on Windows that requires 3d rendering (like games).

---

### Post by mosaic2s on 2009-05-07
If the applications are not resource hungry, you can set up virtual machine within Ubuntu / Linux. Virtualbox is good.

Once virtual machine is set, you will need to allocate hard disk space to it, RAM and video RAM to it. Then load the other OS within it. It is wonderful.

Whats your printer ? Make and model?

---

### Post by Entrenched on 2009-05-07
Epson ME 30 is the model, and I have searched and searched, seems linux does not make a compatible driver. Also, even if they did, there are many advanced features that just would not be available, like making business cards and such.

Anyhow, I have 160 GB hard drive, more than large enough for another partition. I know that you can use ubuntu directly from the CD for installation, while at the same time keeping your Windows OP, however I have done this before, and it is super slow. I know of no other way to use linux inside a windows OP.

My only fear is a super slow computer, I mean really, how much of a slow down are we talking about if I partition my hard drive? Also, I assume I'll have to completely wipe it to do this? I hate having to do that.

---

### Post by alphacrucis2 on 2009-05-07
> **Entrenched said:**
> Epson ME 30 is the model, and I have searched and searched, seems linux does not make a compatible driver. Also, even if they did, there are many advanced features that just would not be available, like making business cards and such.

Anyhow, I have 160 GB hard drive, more than large enough for another partition. I know that you can use ubuntu directly from the CD for installation, while at the same time keeping your Windows OP, however I have done this before, and it is super slow. I know of no other way to use linux inside a windows OP.

My only fear is a super slow computer, I mean really, how much of a slow down are we talking about if I partition my hard drive? Also, I assume I'll have to completely wipe it to do this? I hate having to do that.

I have a laptop running dual boot with Vista and Ubuntu Jaunty. It is a very common configuration. The laptop has a 160GB hd divided between Vista (NTFS) and Ubuntu Jaunty (two EXT 4 partitions and one swap). The problem is that when you start you will probably find that the NTFS partition takes up most of the drive. It is advisable that you defrag the NTFS partition within Windows before shrinking it down to make space for Ubuntu. The Ubuntu installer overwrites the master boot record so that your machine will fire up the grub boot loader which displays a menu asking you to select a Linux kernel to boot or at the bottom of the list you will see Windows/Longhorn.

---

### Post by arapa on 2009-05-07
With a 160 GB hard drive you won't see a degradation in disk performance by partitioning. 

The hardware doesn't care what kind of file system you're using. Windows will ignore your linux partition. Currently I have my Ubuntu root partition as ext4, my home partition as ext3 and my windows as ntfs.  

You can format each partition independently without the other partitions being effected.

If the entire disk is currently one giant 160 GB partition formatted as NTFS you can easily shrink the partition and create a one in the newly freed area on your disk. Run disk defrag from windows before resizing (right click on your C drive >Properties>Tools tab>Defragment now button>defragment button)

Of course back up important stuff before messing with the disk structure.

Then reboot from the live CD and open gparted.

[http://gparted.sourceforge.net/larry/resize/resizing.htm]("http://gparted.sourceforge.net/larry/resize/resizing.htm")

---

### Post by Entrenched on 2009-05-07
Well right now I only have Ubuntu, no windows. What your saying is I need to install windows, meaning delete ubuntu, then defrag, then go to disk manager and create a new partition? Don't you create partitions when you first install Windows, and not after? Also, why would I need to defragment a newly installed OP which has yet to be used and has just been reformatted to NTFS? Also, I have no clue what this EXT 3 and ext 4 things are your talking about, I only wish to have 2 patitions, maybe 80 gb and 80 gb, or should I make the Linux one smaller?

---

### Post by Linux&amp;Gsus on 2009-05-07
When do a fresh install of Windows you don't need to defrag it.
I would recommend to partition the disk first (e.g. with gparted) then install Windows first, then Linux. How much space you give each OS depends on your needs. However, it's very likely that Windows will need more space for the OS to install then Linux. Not counting in the applications needed/wanted.

Also, it's advisable to have a separate "/home" partition on Linux. /home is where all your data is stored (in a sub directory with your username) plus all your settings. To have it on an extra partition makes it a lot easier to backup and re-install.

Cheers,
L&G

---

### Post by Entrenched on 2009-05-07
Thanks, have no idea how to set up a smaller "home" partition inside a larger linux one, no idea whatsoever. As for 2 partitions, that one is easy. The truth is I don't plan on using windows that often. I'll only use it for whatever software and games won't work on linux. I'd say most of the time, including use of the net, will be linux. That being said, I still don't know how much I hsould use for windows. 80 GB, or less? As for the double partition inside linux, I don't have the foggiest, nor would I know how toback up settings, since truth be told I can't hardly use linux well enoughy yet to even worry about settings.

---

### Post by card_ace on 2009-05-07
i only have 20 gigs to my Windows XP.  it doesn't take that much.  i guess the biggest deciding factor for you will be how many things your going to install.  obviously, the more things your going to install the more space its going to need.

---

### Post by Bartender on 2009-05-07
Entrenched -
I'm a bit confused here.  Post #7 you say you hate wiping the drive.
But in Post #10 you say that you're only running Linux.

You're going to have to wipe the drive to install Windows and reinstalling Linux is easy.

In my opinion, the simplest thing to do would be to download GParted LiveCD and burn to a CD.  When you're done you have a powerful partitioning tool that works better than the partitioner inside the Ubuntu installer.  The guts are actually the same, but the dedicated GParted LiveCD (GPLCD) works better and gives you better control over your options.

You can use any Windows PC to download and burn the GPLCD CD as long as you know how to burn an image.  Same process as you used to make the Ubuntu install CD.

One odd thing about GPLCD - I've found that sometimes older versions work better than the newer ones.  So if you download the latest stable version, and it doesn't work, try going back a year or two.  The most reliable version I have of GPLCD is about 2 years old!

Boot the PC to GPLCD.  If you have one HDD it will be recognized as sda. Delete all partitions.  Apply each step as you go, otherwise GPLCD will let the tasks stack up.  Create a primary partition at the "front" (left-hand side) of the disc.  This partition will be for Windows.  40 to 80 GB oughta be plenty, less if you really don't think you'll be using it much.  Apply the change.  Make sure to format this partition as primary, and file system as NTFS.  When you're done GPLCD should show a partition with a bright green border.  Click on the rest of the drive and create an extended partition.  You don't have to format it or anything.  Just click on it, create a partition, create it as "extended", Apply.
Now install Windows.  I'm not absolutely sure if the Windows install CD will ignore the extended partition, or see it.  Either way, just make sure to install Windows to the primary partition.  You'll be able to recognize it by the description and the size.  Windows wants to install to C: anyway, so it should be pointing to the correct partition when you go into the process.  If you have a recovery disc or discs instead of a genuine Windows CD, it should recognize the NTFS partition and ignore the extended.
Get Windows working.  Install drivers, anti-malware, etc.  
Once you're happy with that, pop the Ubuntu CD in and install to the extended partition.  You should be able to use the Guided option.  Ubuntu will see the extended partition.
I would also suggest separate /home folder but it's not critical.  We just want to get you going this time.  Maybe next time you install.  Just let Ubuntu install automatically to that extended partition and you'll be fine.

---

