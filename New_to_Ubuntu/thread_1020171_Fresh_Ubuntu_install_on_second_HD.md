---
title: "Fresh Ubuntu install on second HD"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by krisfrajer on 2008-12-23
Hi ubuntuers,
I am planning to update one of my computers and loaded with ubuntu. I am thinking in setting up the dual partition so to have the Windows and ubuntu at the same time. I have windows in a HD of 250 GB which is currently running, and I am about to add another HD where I want to install ubuntu. My question is what is the best way to integrate both HD and how should I proceed with the install? Should I disconnect my Windows HD and then install Ubuntu in the second HD or could I safetly do the install on the second HD whitouht worring about the windows HD? How should I proceed about the grub so to have both operating system available when the computer starts up? Would it be enough if I set up the linux HD to be the master and the windows to be the primary slave?

Thxs for any advise,

---

### Post by TBomBM3879 on 2008-12-23
You may want to disconnect your windows HD if you don't want a linux partition on it.

What do you mean by integrate your hard drives together? If you want linux to recognize both hard drives you'd have to create a partition for linux that incorporates both harddrives

Installing linux will install grub on your system so you won't be able to run windows unless you add windows to grub

To add windows to GRUB try following this topic on the forum; read the whole thing before you try it,though.

[http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub)

---

### Post by krisfrajer on 2008-12-23
> **TBomBM3879 said:**
> What do you mean by integrate your hard drives together? If you want linux to recognize both hard drives you'd have to create a partition for linux that incorporates both harddrives


[http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub)

What do you mean with creating a partition for linux that incorporates both hard drives?

Would it be enough if I define a windows entry in the grub menu on my Linux HD?

Thxs,

---

### Post by egalvan on 2008-12-23
> **TBomBM3879 said:**
> You may want to disconnect your windows HD if you don't want a linux partition on it.

If you don't want a Linux partition on your first drive, then don't create one on that drive.

The partition editor has a selection menu that makes it rather difficult to choose the wrong drive. Not impossible, but just pay attention.

if you disconnect your Windows drive, then GRUB will not find it,
and you will have to set up widnows manually.


> What do you mean by integrate your hard drives together? If you want Linux to recognize both hard drives you'd have to create a partition for Linux that incorporates both harddrives

Linux recognizes a wide range of partition types, including Windows FAT & NTFS.
 You need not do anything "special" to get Linux to play nice with the rest of the world.

> Installing linux will install grub on your system so you won't be able to run windows unless you add windows to grub

Again, GRUB will almost always find a Window install, and set it up in its menu. Let GRUB do its thing.
I've set up at least two, maybe three computers like this in the past six months... I've lost track, because I've done over 15 installs... All dual-boot in some way.
All worked, GRUB found and set up Windows.

> 
To add windows to GRUB try following this topic on the forum; read the whole thing before you try it,though.

[http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub)

caljohnsmith has a better 'howto' but I don't have it at hand.

---

### Post by krisfrajer on 2008-12-23
What would you suggest about the master drive? Should I set up my Linux HD to be the master HD? I am just thinking that should be the most convenient thing to do so to have the grub install in that same HD. Is that right?

Thxs for sharing your advises and for all the comments so far,

---

### Post by BGFG on 2008-12-23
What you are asking is how i had my machine setup. The installation will be easy don't worry. Firstly, you don't necessaraily need to disconnect you windows drive in the installation, ubuntu will see one empty drive and one with space used, so your selection of installation drive will be obvious :)

Secondly, the reason I'd leave the windows drive connected is because the ubuntu installer will see the windows bootloader and ask you if you'd like to add it to grub, to which your answer will be yes :) that way, grub will handle your dual boot and you will have a easy selection of OS'es when you boot.

As for integrating the two, in my experience, Ubuntu sees and is able to write to and copy from a windows partition easily. If you run into any problems, there are multiple useful threads on the topic or just post back here.
Windows however, sees ubuntu supported filesystems as a large unallocated space in disk management. So don't forget NOT to format your new (ext3 i'm guessing) system while you are in windows...

Enjoy your install.

One more thing, If you are up to it, I'd suggest you create separate partitions for / and /home. Makes future upgrades a lot simpler :)

---

### Post by eriqjaffe on 2008-12-23
Echoing BGFG, mostly.  I have Windows installed on my IDE "Master" and installed Ubuntu on my unformatted "Slave" drive with no problems whatsoever.

It is, however, possible to get EXT3 partitions readable in Windows - I have my home partition showing up as the Z: drive when I boot back into XP for some reason:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by bazboy on 2008-12-26
Hi
After reading up on all the things that could go wrong in a two hard drive dual boot Windows XP/ Ubuntu, i am reassured to find that for most people it works as it should with no problems booting from XP or Ubuntu. My Ubuntu laptop died so i put the reformatted old laptop drive in my desktop( i want to put ubuntu back on this).The drive layout is different than most so i wondered if it would cause any problems. On the first Ide socket on the motherboard i have the windows xp hard drive and a Dvd writer with built in card reader. I will have to connect the new hard drive to the second ide socket leaving it set as Master and install Ubuntu onto it. So i have in fact two master hard drives but on different ide sockets on the mother board. Will this cause any problems on installing of booting xp or Ubuntu.I also hope Ubuntu will find the blank drive and make the install even easier.

Your opinions will be gratefully received as i do not want to mess up my system but would use Ubuntu more than windows.
Bazboy

---

### Post by egalvan on 2008-12-27
> **bazboy said:**
> Hi
After reading up on all the things that could go wrong in a two hard drive dual boot Windows XP/ Ubuntu, i am reassured to find that for most people it works as it should with no problems booting from XP or Ubuntu. My Ubuntu laptop died so i put the reformatted old laptop drive in my desktop( i want to put ubuntu back on this).The drive layout is different than most so i wondered if it would cause any problems. On the first Ide socket on the motherboard i have the windows xp hard drive and a Dvd writer with built in card reader. I will have to connect the new hard drive to the second ide socket leaving it set as Master and install Ubuntu onto it. **So i have in fact two master hard drives but on different ide sockets on the mother board. Will this cause any problems on installing of booting xp or Ubuntu**.I also hope Ubuntu will find the blank drive and make the install even easier.

Your opinions will be gratefully received as i do not want to mess up my system but would use Ubuntu more than windows.
Bazboy

You will have two Masters, but one will be Primary, and the other Secondary. No problems.

And Ubuntu will find the blank drive, again  no problem.

When partitioning, you should find that:
The first drive should be labeled sda
the second drive should be labeld sdb

unless you are using an older version of the partitioner.
then they will be hda and hdb.

And remember, GRUB has a different order.

Nothing difficult, just keep in mind which is first, and which is second.

One being full of Windows, and the other blank will  be an advantage.

And yes, I have done this type of install.

I used PartedMagic LiveCD. Easier then Ubuntu LiveCD because it supported drive labels.

And remember, the partioner will not write the changes until you tell it to. This gives you a bit of "space" to work with.

ErnestG

---

