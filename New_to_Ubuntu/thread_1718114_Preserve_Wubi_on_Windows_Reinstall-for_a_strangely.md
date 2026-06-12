---
title: "Preserve Wubi on Windows Reinstall-for a strangely partitioned system"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by shubhbansal on 2011-03-30
Hi

A virus has caused my windows OS to crash. I currently have 3 OS's installed on my system: Windows, Ubuntu (1-the regular desktop variety, has its own partition) and Ubuntu (2-the wubi kind). (Side Note-Ubuntu(1) sort of stopped working because I had allocated too little space while installing it, and I didn't think it was worth meddling in boot loaders and partition managers to uninstall it.)

Given the recovery options available with my notebook, I can only restore the Windows partition to its original state, not repair my windows installation, and since Ubuntu(2) and windows share the same partition, I'd like some way to preserve Ubuntu(2).

I have read on forums that an easy way to do this is as follows:
1. Backup the Ubuntu iso present in the windows partition.
2. Reinstall windows, reinstall wubi.
3. Replace the new wubi's installed files by the backed up Ubuntu(2) files.

My questions are- 
1. Would this work given my system? I have 3 OSs, three levels of BOOT menus etc.
2. Now that I'm reinstalling windows, I'd also like to know if there's an easy "Risk-free" way to get rid of the Ubuntu(1) partition. Risk Free because I just don't have enough external hard disk space to backup all my data, and even though I have backed up critical stuff, I still wouldn't want to lose anything.

Total Noob, simple, detailed instructions much appreciated.

Thanks!

---

### Post by fabricator4 on 2011-03-31
> **shubhbansal said:**
> 
2. Now that I'm reinstalling windows, I'd also like to know if there's an easy "Risk-free" way to get rid of the Ubuntu(1) partition. Risk Free because I just don't have enough external hard disk space to backup all my data, and even though I have backed up critical stuff, I still wouldn't want to lose anything.


Note that installing Windows is going to overwrite the grub boot loader in the MBR, so you're going to lose the ability to boot off the Ubuntu partition in any case.  It's possible to boot off the LiveCD and replace just grub.

Maybe you should take the opportunity, since you're re-installing, to reorganise your hard drive so it works better for you.  In particular set up separate /home and / partitions to avoid the sort of problems you've had.  The / (root) partition should be at least 15 - 20 GB in my opinion, though it can easily be as small as 10 GB if you wish. The /home partition should be big enough to take all of your data, and both Linux partitions should be ext4. If you need to access /home from the Windows boot you can do so by installing the open source file system driver ext2 in Windows.  

Note that having a separate /home partition has two very big advantages: firstly it prevents a large influx or creation of data from filling the drive that file system lives on, and secondly it means that you can re-install Ubuntu at any time without even touching the partition that your data is on.  This makes recovery from even the worst disasters stress and trouble free.

I don't know if copying the ISO as you suggest is going to work.  You might as well try it, as if your current windows install is unbootable you have very little to lose.  At the very least, if you've got a copy of the ISO then maybe one of the recovery programs (photorec, testdisk etc) can access the data.  Maybe google recovering a Casper drive.

The Live Gparted CD is a useful tool as it contains Gparted and some disk recovery tools.  Its also a very light debian distro, only 128 MB to download, runs off a USB or CD very nicely, and yet has a graphical fluxbox environment.

It's also possible that Gparted can re-size the linux partition for you, so you can use it again as long as it hasn't been completely borked.  You'll have to reduce the size of the windows partition (risky, since it sounds like it's badly damaged - I would fear for your data) then increase the extended partition size, then increase the ext4 partition you've got Ubuntu on.

Chris.

---

### Post by Mark Phelps on 2011-03-31
To respond to your original question ... it's not a Wubi ISO, it's a file -- and I believe it is named root.disk (or something like that -- don't actually use Wubi).

And, I too have heard that what you intend to do should work -- in terms of restoring your present Wubi install.

---

