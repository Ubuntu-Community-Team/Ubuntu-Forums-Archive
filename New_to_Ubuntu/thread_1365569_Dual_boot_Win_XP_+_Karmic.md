---
title: "Dual boot: Win XP + Karmic"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by WestCity on 2009-12-27
Hi, I need Windows XP (for some personal reasons) + Ubuntu Karmic dual boot.

I'll do those steps:

1. Install Win XP/format all hard drive space (FAT32).
2. Install Ubuntu Karmic with option "side by side" or something like that (don't remember exactly...).

So, how both OS will use the same HDD space? In example: if I install a game and few programs in Windows, and ten programs in Linux, how it will look? Everything will work fine?

Or maybe I should split HDD into two parts, after installed Win XP? And then, install Karmic on second part? What is better?

---

### Post by markjensen on 2009-12-27
If you install with wubi, then Ubuntu will be a little filespace on your Windows drive.

Or you can do a traditional partitioning, in which case, Linux will be on a separately-created partition (which, in Windows, would be like a separate drive letter).

I am partial to the traditional partitioning, but there is nothing inherently "wrong" with a wubi install from within Windows.

---

### Post by Nicolas.Perrault on 2009-12-27
No, windows being greedy doesn't let you (as far as I know) be installed side by side if Linux is already installed. What I'd do is the following: 

1) Format your hard drive (Don't forget to make backups!)
2) Place the Windows XP CD in the CD reader as you open your empty computer.
3) Install Windows XP
4) Reboot your computer twice. Once to fully install Windows XP, and once to install Ubuntu.
5) Install Ubuntu with a second partition. Choose how much you wish to put in each partition. Keep in mind that windows takes way more space and is way more demanding than Linux

 Your programs on different partitions shouldn't interrupt each other. You should be good. I'm really new to Linux, so if I said something that ain't completely right, feel free to tell me.

---

### Post by Merk42 on 2009-12-27
If you do traditional partitioning as it seems you will, do it at the step of installing XP.

[list=1][*]Create two partitions, one NTFS and leave the other unallocated. (the size depends on your HDD and if you're going to put files in your Ubuntu Partition and/or Windows one)
[*]Install Windows XP on the newly created NTFS partition.
[*]Install Karmic manually into the unallocated partition, formatting it as EXT4[/list]

---

### Post by Twitch04 on 2009-12-27
Like markjensen said, you can have the Linux partition IN the Windows partition, or you can simply create a new partition on your hard drive. The hard drive my computer came with was split into two, a C: [main] drive and D: [recovery] drive. When I installed Karmic a few days ago my friend simply shrank my C: partition about 10 gigs or so and used that free space to create a new partition for Karmic, which I boot from [yay for GRUB!]. So now I have my C: partition, my D: partition, and my Ubuntu partition. [which Windows can't see. XD]

I'd do what I did, since that way if your personal reasons go away and you want to get rid of Windows, you can justdo that. If you use Wubi, you'd have to reformat your whole hard drive since Linux was IN the Windows partition.

---

### Post by oldfred on 2009-12-27
I consider wubi as a better liveCD for testing and experimenting with Ubuntu when you are primarily a windows person who just wants to try it. Once you make a decision to use it at least some of the time on a regular basis it is best to go with a true dual boot where each operating system is in separate partitions. Wubi is still a program running inside windows so if windows has problems so does wubi.

When I first started converting from windows, I had photos and profiles for firefox and thunderbird that I wanted to share so regardless of which system I was in they were the same. I created a shared FAT partition (3 years ago) but have since converted that to NTFS as it is more reliable and can hold files larger than 4GB. I now am in Ubuntu 90% and have added ext3 data partitions for data I know I will not share.

If you are going to install both, I would create the windows partitions in advance. Windows will only see the NTFS partitions (I cannot recommend FAT anymore) and will install to it. You then will not have to resize the windows partiiton or make the Ubuntu installer resize it. If you leave the rest blank you can then choose to install Ubuntu to the empty space. Or you you want you can with gparted to create the Ubuntu partitions (ext4 adn swap)and use manual install.

---

### Post by markjensen on 2009-12-27
> **oldfred said:**
> ... Wubi is still a program running inside windows so if windows has problems so does wubi.
...
Wrong.

A wubi install does NOT use the Windows operating system in any way. It uses the Microsoft boot loader to select an OS, but once Ubuntu is selected, it is Linux all the way.  No Windows at all.

---

### Post by WestCity on 2009-12-27
Thank you for the answers!

I had 9.04. Some weeks ago upgraded to Karmic. Now I want a fresh install of Karmic. I've decided, that I need Win XP too (for one game and maybe for a few specific programs only...). I've already copied all important files to external HDD.

So, probably I'll do those steps:

1. Insert XP CD and format HDD (NTFS).
2. Split HDD into two partitions (second will be unallocated).
3. Insert Karmic CD and install it on the second partition, so it will make ext4 by default.

Am I right now? :)

---

### Post by kansasnoob on 2009-12-27
> **WestCity said:**
> Thank you for the answers!

I had 9.04. Some weeks ago upgraded to Karmic. Now I want a fresh install of Karmic. I've decided, that I need Win XP too (for one game and maybe for a few specific programs only...). I've already copied all important files to external HDD.

So, probably I'll do those steps:

1. Insert XP CD and format HDD (NTFS).
2. Split HDD into two partitions (second will be unallocated).
3. Insert Karmic CD and install it on the second partition, so it will make ext4 by default.

Am I right now? :)

Sounds OK to me, maybe this is helpful:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1)

---

### Post by Teber on 2009-12-27
when installing a previous version of ubuntu i did as follows:

1. install xp and use to partition tool of xp to create a 40 gb partition, which i formatted leaving the rest unallocated. 
2. installed ubuntu on the unallocated space and manually partitioned it. 

less work...

when upgrading to karmic i did a fresh install formatting the linux partitions as ext4.

---

### Post by WestCity on 2009-12-27
Finally did this way:
[http://apcmag.com/how_to_dual_boot_w...rst.htm?page=1]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1")

Both OS works fine.

Thank you guys, especially kansasnoob. :)

---

