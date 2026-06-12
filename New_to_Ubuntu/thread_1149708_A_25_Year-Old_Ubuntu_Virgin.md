---
title: "A 25 Year-Old Ubuntu Virgin"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by thdn on 2009-05-05
Hello Guys, first post here, i heard a lot of good comments about the new Ubuntu and im ready to take the chance and jump to the Ubuntu World, but before that , i have a lot of questions and hope you can help me out !

First, i have a Core 2 DUO  2.8 , 4 GB Ram with a new 500 GB hd ( So i dont need re-partition )  and i want to partition the hd this way :

20 GB  NTFS ( Unit C: for windows installation)
450 GB NTFS ( Unit D: for music, games, movies )
25 GB ext3 ( For ubuntu Installation )
5   GB  ( For Swap )

- The sizes of partitions are ok ? or am i missing something?
- Whats best, install ubuntu x86 or x64
- There's a tool for partition or just the wizards from windows or ubuntu
- Whats best, install ubuntu or windows first ?
- If I start using Ubuntu regularly for download stuff ( moviex, music, torrents , etc ) I can save this directly to Unit D ( NTFS partition ) ? or just cant?

---

### Post by taurus on 2009-05-05
That is a heck of a swap partition there.  You probably don't need more than 2GB.  4GB of swap should be plenty.  10GB is just over kill.

p.s.  Swap partition is not ext3 filesystem.

---

### Post by thdn on 2009-05-05
> **taurus said:**
> That is a heck of a swap partition there.  You probably don't need more than 2GB.  4GB of swap should be plenty.  10GB is just over kill.

p.s.  Swap partition is not ext3 filesystem.

Thanks mate, i've corrected the values ;)

---

### Post by Bucky Ball on 2009-05-05
> **thdn said:**
> 

20 GB  NTFS ( Unit C: for windows installation)
450 GB NTFS ( Unit D: for music, games, movies )
20 GB ext3 ( For ubuntu Installation )
10 GB ext3 ( For Swap )

Make that ...

20 GB  NTFS ( Unit C: for windows installation)
20 GB ext3 ( For ubuntu Installation )
450 GB NTFS ( Unit D: for music, games, movies )
10 GB ext3 ( For Swap )

Faster part of the drive. 


- The sizes of partitions are ok ? or am i missing something?

You probably don't need the OS partitions that big. 10, 12, 15 - if you are intending to store just small files.

- Whats best, install ubuntu x86 or x64

If you have 64bit processor, AMD64 (doesn't matter if you are running intel, that is the one)

- There's a tool for partition or just the wizards from windows or ubuntu

You will get the option to manually setup your Ubuntu partitions during install.

- Whats best, install ubuntu or windows first ?

Windows first always. Can be done other way but this is much easier.

- If I start using Ubuntu regularly for download stuff ( moviex, music, torrents , etc ) I can save this directly to Unit D ( NTFS partition ) ? or just cant?

NTFS fine. You will need to install ntfs3, but that is easy and comes way down the track from where you are now.

:)

This page will get you far, my friend:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

... and like taurus said. In my opinion, 2Gb swap is fine. You will probably never touch it with 4Gb of RAM, trust me.

---

### Post by AnLGP on 2009-05-05
you have to install windows first if i recall correctly.  there may be workarounds but as far as i know i've always had to.

NTFS support is easy.  Just do what Bucky said.

---

### Post by Therion on 2009-05-05
Even 5GB for swap is insanely huge; the more RAM you have installed the LESS likely you are to need a swap file AT ALL.  

2GB of swap is overkill in my opinion on a system with 4GB of RAM.

Also, you don't say what version of Windows you want to dual-boot with, but install it first and then Ubuntu.  It's just easier to let Windows do it's own thing (it won't like "sharing" the drive if you try to install it after Ubuntu) and then let Ubuntu install/use GRUB to handle the heavy lifting.

Dual-boot tutorial:  [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by whoop on 2009-05-05
**- The sizes of partitions are ok ? or am i missing something?**
Swap is not of type ext3 but of type swap. I also think you have a little to much swap on there. You have 4 gigs of ram so you are not going to be using swap that often, and not that much if you are using it. The ubuntu installer will suggest a swap size for you so you should not worry about that. I would use a little more than 20 gigs for your ubuntu root partition (especially if your home is on there as well) , although 20 is technically enough.
**- Whats best, install ubuntu x86 or x64**
I would suggest x64 but it is a personal preference. Look here to make up your own mind: [http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)
**- There's a tool for partition or just the wizards from windows or ubuntu**
The ubuntu installer has a wizard and you can also use the partitioning tool from the live-cd called gparted. System-->Administration-->Partition editor
**- Whats best, install ubuntu or windows first ?**
I always install windows first (and defragment it if I used windows before installing ubuntu), launch the ubuntu livecd after that, run the partition editor to create unpartitioned disk space for the root and swap partition. Reboot (just to be safe) and install ubuntu using the installer
**- If I start using Ubuntu regularly for download stuff ( moviex, music, torrents , etc ) I can save this directly to Unit D ( NTFS partition ) ? or just cant? **
Ubuntu has drivers to read/write to ntfs partitions

---

### Post by Penguin Guy on 2009-05-05
> **thdn said:**
> 
1 The sizes of partitions are ok ? or am i missing something?
2  Whats best, install ubuntu x86 or x64
3 There's a tool for partition or just the wizards from windows or ubuntu
4 Whats best, install ubuntu or windows first ?
5 If I start using Ubuntu regularly for download stuff ( moviex, music, torrents , etc ) I can save this directly to Unit D ( NTFS partition ) ? or just cant?
1 - Yes.
2 - You don't have a choice (depends on your hardware).
3 - You don't need a partition tool (although it is nice to have one anyway).
4 - Windows first (unless you are good with computers).
5 - You can.

---

### Post by CLomax on 2009-05-05
> - Whats best, install ubuntu x86 or x64
- There's a tool for partition or just the wizards from windows or ubuntu
- Whats best, install ubuntu or windows first ?
- If I start using Ubuntu regularly for download stuff ( moviex, music, torrents , etc ) I can save this directly to Unit D ( NTFS partition ) ? or just cant?

1) I'd go for x86 as it messes up less for me.
2) You are given the options for partitioning just before installation.
3) I normally do Ubuntu, then Windows, then recover GRUB (The menu to choose the OS) with the Ubuntu LiveCD (I've never had much luck the other way round). This is rather easy to do, I can give instructions if you wish.
4) Yes, as far as my understanding goes, Ubuntu supports NTFS out-of-the-box so you shouldn't have a problem there.

---

### Post by Sjeti on 2009-05-05
For future reference, when you install use:

```

sudo apt-get install ntfs-config
sudo ntfs-config

```

Run that and check all the boxes, then you'll automount everything at startup and have read/write privileges.

Install Windows first because when you install Ubuntu, grub will autodetect you windows drive and you won't have to worry about using SuperGrubDisk or manually editing your menu.lst.

---

### Post by MrWES on 2009-05-05
> **Therion said:**
> Even 5GB for swap is insanely huge; the more RAM you have installed the LESS likely you are to need a swap file AT ALL.  

2GB of swap is overkill in my opinion on a system with 4GB of RAM.

Also, you don't say what version of Windows you want to dual-boot with, but install it first and then Ubuntu.  It's just easier to let Windows do it's own thing (it won't like "sharing" the drive if you try to install it after Ubuntu) and then let Ubuntu install/use GRUB to handle the heavy lifting.

Dual-boot tutorial:  [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

I agree on the swap -- I wouldn't put more than 512mb -- period. Also, I'd consider a separate /home partition. I have 2gb of ram on my laptop running Jaunty and the swap hardly ever gets hit.

Bill

---

### Post by Mark Phelps on 2009-05-05
> **thdn said:**
> 
- The sizes of partitions are ok ? or am i missing something?

As already mentioned, swap is bigger than you need.

Also, recommend you change the partitioning to replace the last two with an Extended partition, and inside that, put a partition for root, a separate partition for home, and a separate swap partition.

> 
- Whats best, install ubuntu x86 or x64

Your choice. x64 will see all 4GB of RAM; x32 will only see a little over 3GB of it.
> 
- There's a tool for partition or just the wizards from windows or ubuntu

Have personally found the embedded LiveCD graphical tool to be buggy.  Would recommend the text-mode Alternate CD and manual partitioning.
> 
- Whats best, install ubuntu or windows first ?

Windows first.  Ubuntu will see Windows when you install it and add a stanza to menu.lst to handle it.
> 
- If I start using Ubuntu regularly for download stuff ( moviex, music, torrents , etc ) I can save this directly to Unit D ( NTFS partition ) ? or just cant?
Yes -- but it won't be "D".  That's an MS Windows artifact.  Be sure to install the ntfs-3g package if you're going to do NTFS partition stuff.  I believe that this is installed by default in 9.04.

---

### Post by joey-elijah on 2009-05-05
I have 4Gb RAM and a 2GB Swap and the swap has **never** been touched - even during peaks of loads of windows open, encoding etc.

EDIT: Also i would strongly recommend you go witha  64bit install - there is no reason not to - especially with your specs. It's flawless and everything works fine. I've been using x64 bit for 3 years and Jaunty is by far the most snappy, stable and strongest release so far.

---

### Post by Therion on 2009-05-05
> **Penguin Guy said:**
> 2 - You don't have a choice (depends on your hardware).
Seeing as how a 64-bit architecture can run a 32-bit OS, he very well may.

---

### Post by Vorian Grey on 2009-05-05
> **thdn said:**
> 

20 GB  NTFS ( Unit C: for windows installation)


You didn't say what version of Windows you plan on using but Vista won't install on partitions of less than 40 GB. Even using XP you could fill that space easily if you add a lot of games.

---

### Post by tom56 on 2009-05-05
> **MrWES said:**
> I agree on the swap -- I wouldn't put more than 512mb -- period. Also, I'd consider a separate /home partition. I have 2gb of ram on my laptop running Jaunty and the swap hardly ever gets hit.

Bill

You need at least as much swap as you have RAM in order to hibernate. In this case 5gb makes sense (4gb to match RAM for hibernation, 1gb for actual use as swap).

---

### Post by wiznillyp on 2009-05-05
If you want to use all 4GB of your Ram and have a 64 bit processor, use 64-bit.

If you are using Vista, you will probably need more than 20GB of space, especially if you plan to play games.

Install Windows first as everyone stated above.

---

### Post by Junkieman on 2009-05-05
I have 3GB memory and a 3GB swap partition, and the swap only kicks in when I do a LOT at once. Your 5GB is perfect.

Thought about making your storage partition FAT32, so you can use the space in both OS's with peace of mind. Although I use NTFS USB Disks without any problems ;)

Use the partitioner built into Ubuntu installer, which comes up during the Ubuntu install prep. You can check it out by booting the live CD, it's on the menu System -> Administration -> Partition Editor, 

Read [this article]("https://help.ubuntu.com/community/HowtoPartition") on partitioning your drive, and more importantly, [how to dual boot]("https://help.ubuntu.com/community/WindowsDualBoot") Ubuntu and Windows.

And welcome to the community! :guitar:

---

### Post by MrWES on 2009-05-05
> **tom56 said:**
> You need at least as much swap as you have RAM in order to hibernate. In this case 5gb makes sense (4gb to match RAM for hibernation, 1gb for actual use as swap).

IMHO, Jaunty reboots faster than a resume from suspension and/or hibernation.

Bill

---

### Post by thdn on 2009-05-05
> **wiznillyp said:**
> 
If you are using Vista, you will probably need more than 20GB of space, especially if you plan to play games.

Install Windows first as everyone stated above.

No way i hate Vista , in fact thats the reason why im jumping to Ubuntu.

---

### Post by thdn on 2009-05-05
> **Vorian Grey said:**
> You didn't say what version of Windows you plan on using but Vista won't install on partitions of less than 40 GB. Even using XP you could fill that space easily if you add a lot of games.

Windows XP Sp3, tunned by me :D

---

### Post by thdn on 2009-05-05
> **Mark Phelps said:**
>  Also, recommend you change the partitioning to replace the last two with an Extended partition, and inside that, put a partition for root, a separate partition for home, and a separate swap partition.. 

I dont understand  ??  i come from a win32 world ,  so i dont really get this new concepts 
:(

---

### Post by wpshooter on 2009-05-05
I did not read ALL of the previous postings, but if noone mentioned it, make sure that you setup a SEPARATE **_/home_** partition !!!

---

### Post by wiznillyp on 2009-05-05
thdn,

All the talk of setting up a separate partition for the home directory is really good and sound advise, but do not get overwhelmed with those details.  When I first used Linux, I had no idea what a home directory even was, so do not feel bad if you do not.

Just go the easy route and create a small swap partition, and Use EXt3/4 for your OS partition and learn away!

---

### Post by emeraldgirl08 on 2009-05-05
Wow. I should be receiving an extra HD soon. 

Just reading all this info is helping me out- BIG TIME!

I'm a noob here too so it does feel inundating with all the new information and command-entering. It's pretty cool learning tho :)

---

### Post by Bucky Ball on 2009-05-06
> **Sjeti said:**
> For future reference, when you install use:

```

sudo apt-get install ntfs-config
sudo ntfs-config

```

For a new user why would you give terminal instructions when ntfs is readily available in Synaptics? Please check the beans and always try and keep it 'in the GUI' for new users (unless impossible). 5 beans? Probably never even heard of sudo so you would need to give a rather more complete explanation (like type in a terminal and where to find the terminal).

---

### Post by golusweet on 2009-05-06
> **thdn said:**
> Hello Guys, first post here, i heard a lot of good comments about the new Ubuntu and im ready to take the chance and jump to the Ubuntu World, but before that , i have a lot of questions and hope you can help me out !

First, i have a Core 2 DUO  2.8 , 4 GB Ram with a new 500 GB hd ( So i dont need re-partition )  and i want to partition the hd this way :

20 GB  NTFS ( Unit C: for windows installation)
450 GB NTFS ( Unit D: for music, games, movies )
25 GB ext3 ( For ubuntu Installation )
5   GB  ( For Swap )

- The sizes of partitions are ok ? or am i missing something?
- Whats best, install ubuntu x86 or x64
- There's a tool for partition or just the wizards from windows or ubuntu
- Whats best, install ubuntu or windows first ?
- If I start using Ubuntu regularly for download stuff ( moviex, music, torrents , etc ) I can save this directly to Unit D ( NTFS partition ) ? or just cant?


Install 25 GB Partition as / [root] and I recommend choosing ext4

Make swap 2 gb.

Install x86, and Install windows first.

You will able to access all partitions from ubuntu.

---

### Post by Bucky Ball on 2009-05-06
> > **mark phelps]Also, recommend you change the partitioning to replace the last two with an Extended partition, and inside that, put a partition for root, a separate partition for home, and a separate swap partition..

[quote=thdn said:**
> I dont understand  ??  i come from a win32 world ,  so i dont really get this new concepts 
:([/quote]Extended partitions have nothing to do with OS and exist commonly in Windoze World (most notably on a data drive with no OS and over four partitions).

A hard drive will take 4 partitions max. But with an extended partition if, for example, you were to format a drive with a 10Gb *primary* partition for the Windoze OS and the rest of the drive as an extended partition, ***you can then create as many logical drives (read partitions) inside the extended partition as you like*** (actually, I think there is a limit, someone correct me but vaguely remember 99). So, in theory, a drive could have one partition for XP OS and an extended partition with 5 logical drives in that = 6 partitions. Your one physical drive will then appear as C, D, E, F, G drives. (Swap not shown) (One of a few possible permutations).

Windows *must* be on a primary partition. Ubuntu will take either; primary or logical. Therefore, you could indeed make a 10Gb primary partition for Windoze, rest of the drive an extended partition with your Ubuntu install partition and whatever other partitions you choose to create as logical drives ***inside*** the extended partition.

Hope that makes some sense. :)

---

### Post by El Zoido on 2009-05-06
With 4 Gig of Ram I think going 64bit will be better.

Additionally, I'd increase the size of the Ubuntu partition a bit.
If you don't have a separate home partition (neither do I), 25 GB can fill pretty fast if you store some stuff there and install a couple of programs.
If you don't mind using a bit more space for Ubuntu I would go for 40-50 GB here, although you can of course just use the 450 GB partition you intend to create for storage of bigger files.

---

### Post by rlogan on 2009-05-06
Hiya

As wpshooter saif I would setup a /home folder to store your personal settings in a separate partition. So if ever decide to do a fresh install in the future you don't lose your personal data.

Cheers

Richard

---

