---
title: "Trying to dual boot xp with Ubuntu 8.1"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by jalehtor on 2009-08-13
and I can't find useful info on how to do this. I want to use xp for games--WoW, Rome--and Ubuntu for everything else. I now have Ubuntu installed, and nothing else. My home folder is backed up. 

I haven't a clue how to do this, and haven't been able to find a tutorial for idiots, which is where I am right now.

I'd appreciate any articles, youtube tutorials etc. I'd also like to know how much space to allot each system.

---

### Post by Dr Belka on 2009-08-13
was windows pre-installed on the system?

are you planning on installing windows now?

---

### Post by sblunix on 2009-08-13
This article should be easy for you to understand: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by jalehtor on 2009-08-13
> **Dr Belka said:**
> was windows pre-installed on the system?

are you planning on installing windows now?

Windows may have once been installed on the system, but I got it used, and it came blank. It only has Ubuntu now. I need to install XP along with Ubuntu for games.

---

### Post by jalehtor on 2009-08-13
> **sblunix said:**
> This article should be easy for you to understand: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Thank you! I have 8.1, and the article deals with 8.04. Will that make a difference?

---

### Post by sblunix on 2009-08-13
> **jalehtor said:**
> Thank you! I have 8.1, and the article deals with 8.04. Will that make a difference?
Nope, there's nothing version-specific in that guide, it's just a bit old.

---

### Post by jalehtor on 2009-08-13
> **sblunix said:**
> Nope, there's nothing version-specific in that guide, it's just a bit old.

Thank you! As far as partitioning the hard drive: I'm going to be playing games on xp, and pretty much everything else on Ubuntu. What kind of a division would work for this?

---

### Post by ramoj02 on 2009-08-13
> **jalehtor said:**
> and I can't find useful info on how to do this. I want to use xp for games--WoW, Rome--and Ubuntu for everything else. I now have Ubuntu installed, and nothing else. My home folder is backed up. 

I haven't a clue how to do this, and haven't been able to find a tutorial for idiots, which is where I am right now.

I'd appreciate any articles, youtube tutorials etc. I'd also like to know how much space to allot each system.

If you have Windows, install Wubi at [http://www.wubi-installer.org](http://www.wubi-installer.org). Then, run the program and it downloads and install Ubuntu on your computer without partitioning your hard drive. It's the easiest way to dual boot Windows XP/Vista and Ubuntu.

NOTE: It also work with Kubuntu, Xubuntu, and Mythbuntu.

Hope this helped you.

---

### Post by jalehtor on 2009-08-13
> **ramoj02 said:**
> If you have Windows, install Wubi at [http://www.wubi-installer.org](http://www.wubi-installer.org). Then, run the program and it downloads and install Ubuntu on your computer without partitioning your hard drive. It's the easiest way to dual boot Windows XP/Vista and Ubuntu.

NOTE: It also work with Kubuntu, Xubuntu, and Mythbuntu.

Hope this helped you.

I'm trying to install Windows on a Ubuntu machine. If the above article doesn't work for me, I might have to start from scratch, install Windows, then reinstall Ubuntu, but I'd rather not have to do that!

---

### Post by sblunix on 2009-08-13
> **jalehtor said:**
> Thank you! As far as partitioning the hard drive: I'm going to be playing games on xp, and pretty much everything else on Ubuntu. What kind of a division would work for this?

It vary's depending on your hard drive size and how many games your playing, partition size is only physical memory, it doesn't affect speed, so, if you're only gonna download and play 4GB worth of games, go ahead and make a partition with enough space for and XP install and an extra 4 or 5GB, and just leave the rest for Ubuntu...

I have a 200GB HD, and I play a lot of Windows Games that take up a lot of space, so I have about 50GB for windows and 150GB for Ubuntu

EDIT: Did some quick googling, and found out that a regular XP install only takes up about 1.6GB, so if you want make some space for some necessary files, for games, and then you can definitely shrink it down to a lot less than 50GB...

---

### Post by raymondh on 2009-08-13
Remember to [recover/reinstall grub]("http://ubuntuforums.org/showthread.php?t=224351") after you install XP.

---

### Post by jalehtor on 2009-08-14
> **sblunix said:**
> It vary's depending on your hard drive size and how many games your playing, partition size is only physical memory, it doesn't affect speed, so, if you're only gonna download and play 4GB worth of games, go ahead and make a partition with enough space for and XP install and an extra 4 or 5GB, and just leave the rest for Ubuntu...

I have a 200GB HD, and I play a lot of Windows Games that take up a lot of space, so I have about 50GB for windows and 150GB for Ubuntu

EDIT: Did some quick googling, and found out that a regular XP install only takes up about 1.6GB, so if you want make some space for some necessary files, for games, and then you can definitely shrink it down to a lot less than 50GB...

Hmmm....I have a 40 gb hard drive. Should I be thinking of installing a new hard drive instead? 

This is getting more complicated by the second.

---

### Post by raymondh on 2009-08-14
> **jalehtor said:**
> 

This is getting more complicated by the second.

:)  I have found XP comfortable/breathing at around 20GB.  My XP install has office suite, 1 work app, picassa, windows media player, VLC, cdburnerxp, AVG, CCleaner, Spyware, Thunderbird, Firefox and some games as well as about 5GB worth of music.

---

### Post by LewRockwell on 2009-08-14
Partitioning 101:

[http://ubuntuforums.org/showpost.php?p=7770278&postcount=38](http://ubuntuforums.org/showpost.php?p=7770278&postcount=38)
[http://ubuntuforums.org/showthread.php?t=1236742&page=4](http://ubuntuforums.org/showthread.php?t=1236742&page=4)

reprint:

Well here we are...just you, me, and this 250GB hard drive...what should we do now?

First we will run a Secure Erase function and then use GSmartControl to check the disk's health via the Parted Magic LiveCD


[http://partedmagic.com/](http://partedmagic.com/)

[http://sourceforge.net/projects/partedmagic/](http://sourceforge.net/projects/partedmagic/)


Ok, assuming that your hard drive is now securely erased and healthy we will now proceed with partitioning

I create the following partitions:

One 30GB Primary Partition at the beginning of the drive

One 20GB Primary Partition right next to the first partition

One Swap Partition equal to your system's MAXIMUM RAM(regardless of whether you're maxed out right now or not...building in future ease of upgrading)

Then you will take all the remaining space left and create one Extended Partition(inside an extended partition you can create/modify/manipulate as many logical partitions as you might desire in the future)

For the time being, if you decide you want a separate Home partition then you can create a logical partition for one in your shiny new extended partition

You're probably wondering about those first two partitions and I'll explain those now to give you some deeper insight as to my partitioning system for my own personal machines as well as the machines I set-up and maintain for others.

The first partition is created on the premise that you(or someone who buys the computer from you) will plop Windows XP/Vista/Seven/etc on it...(while it's vacant you can use it as a playground/sandbox for other stuff/distros/data/whateveryouoryoursistersodesire)

The second partition will get warm and cozy with Ubuntu 9.04 Jaunty Jackalope just as soon as we can get that crazy critter settled in!

The swap partition is set to max ram and while that seems utterly ridiculous today...tomorrow it may seem commonplace...never under-estimate advances in technology and the ever-increasing demand for more space!

The extended partition is where you can play and partition and experiment and such...with a home partition, a photo partition, a data partition, different *nix distros to goof around with...you know...whateveryouandsisterwant...

After you've completed your partitioning then when you get to the installation portion of Ubuntu pertaining to partitions you will need to manually tell it where you want your "/" mount point and your "/Home" mount point if you want them separate

Wheeee, this computin' stuff is fun!

.

---

