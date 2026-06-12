---
title: "Dual-booting Questions with Windows already installed"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by JJuel on 2010-09-04
Okay I really want to dual boot Ubuntu on my machine that I already have Vista installed on. I have a lot of files already on my machine which is the only reason I haven't done this already. I was wondering how dangerous it would be to try and do this without backing my files up? Would you not recommend doing this? I really don't necessarily want to take the time to back my files up. Would it make a difference if I had a separate clean hard drive that I could install Ubuntu to be all it's own or would it still be best to back everything up that way? 

If it is going to be pretty dangerous to not back stuff up I will, but I have probably almost a TB worth of files on my computer already that I do not want to lose obviously. I know this is very noob-ish and the answer is probably obvious, but I really want some Ubuntu experts opinions on this matter. 

Thank you in advance for any help.

---

### Post by TimEnid on 2010-09-04
when i first dual booted, i didnt bother to back anything up. everything went well. but i think most would suggest that you do a backup.

---

### Post by davidmohammed on 2010-09-04
just ask yourself this question... what is it worth to you if you lost your data because your hard-drive fails?

If the answer is - "dont care" - then go ahead, install without backing up.

If the answer is - "I need it" - then invest some cash and buy a 1TB external hard-drive.  Trust me, its a worth while investment.

---

### Post by JJuel on 2010-09-04
Well that's what I was thinking. I was actually getting close to getting an external hard drive. I just didn't know if I installed a new internal hard drive with nothing on it and just used that for Linux itself would that make a difference? If I did go about it that way would I need to back up the files on the two other hard drives I already have in my computer?

Either way I am going to look into getting the external and backing all my stuff up anyways just in case something happens even if it isn't the attempted dual boot that screws it up.

Thanks again.

---

### Post by poosietgp on 2010-09-04
Im not an expert but, a TB worth of files means a lot of time and effort invested, and in a dual boot install lots of crazy things could happen (crazy things do happen and I've had my share in the past). Backing-up a TB worth of files could be time consuming too but it wouldn't hurt to back-up. 

If you decide to not back-up your precious files then I would suggest to reserve/create a primary partition for your ubuntu install, If you dont have a ready space for your ubuntu install I suggest you make room for one or get another hdd. :p

---

### Post by Mark Phelps on 2010-09-04
An alternate approach, if you have a desktop that can handle two physical drives, is to go out and buy a smaller driver for Ubuntu.  320GB drives are available dirt cheap these days and will provide LOTS of room.

Then, when you install, disconnect the Vista drive and install only to the Ubuntu drive -- including GRUB.

After that, reconnect the Vista drive, but continue to boot from the Ubuntu drive.  Open a terminal and enter "sudo update-grub".  This will rewrite the GRUB that is ONLY on the Ubuntu drive. It will do absolutely nothing to the Vista drive.

I've done this myself since the early days of Vista beta testing, and have not had a single problem with it.

PLUS, this allows you to boot each drive on its own. So, if you later choose to remove the Vista drive, you can still boot Ubuntu without problems.

---

### Post by JJuel on 2010-09-04
> **Mark Phelps said:**
> An alternate approach, if you have a desktop that can handle two physical drives, is to go out and buy a smaller driver for Ubuntu.  320GB drives are available dirt cheap these days and will provide LOTS of room.

Then, when you install, disconnect the Vista drive and install only to the Ubuntu drive -- including GRUB.

After that, reconnect the Vista drive, but continue to boot from the Ubuntu drive.  Open a terminal and enter "sudo update-grub".  This will rewrite the GRUB that is ONLY on the Ubuntu drive. It will do absolutely nothing to the Vista drive.

I've done this myself since the early days of Vista beta testing, and have not had a single problem with it.

PLUS, this allows you to boot each drive on its own. So, if you later choose to remove the Vista drive, you can still boot Ubuntu without problems.


This is what I was really hoping to be able to do. I just have a few questions about this. I already have two hard drives in my computer (I think I have room for 4 total). A lot of my stuff is on the second drive I installed after getting my computer, and Vista is obviously installed on the drive that came with the computer. If I didn't want Ubuntu to affect either one of those should I unplug them both or just the one that has Vista on it? Obviously nothing boots from my second drive right now I just have music, movies and school files on that one. 

If I am booting from the Ubuntu drive will I be able to choose which operating system from there or will I have to set my boot priorities different each time I want to switch?

Thanks

---

### Post by Sef on 2010-09-04
> If I am booting from the Ubuntu drive will I be able to choose which operating system from there or will I have to set my boot priorities different each time I want to switch?


Ubuntu will be the default, but you could choose to boot to Vista.  If you want to set Vista as the default, you can do that too.

---

### Post by audiomick on 2010-09-04
> **JJuel said:**
> This is what I was really hoping to be able to do. I just have a few questions about this. I already have two hard drives in my computer (I think I have room for 4 total). A lot of my stuff is on the second drive I installed after getting my computer, and Vista is obviously installed on the drive that came with the computer. If I didn't want Ubuntu to affect either one of those should I unplug them both or just the one that has Vista on it? Obviously nothing boots from my second drive right now I just have music, movies and school files on that one. 

If I am booting from the Ubuntu drive will I be able to choose which operating system from there or will I have to set my boot priorities different each time I want to switch?

Thanks
If you get it sorted the way Mark Phelps suggested, you will be able to choose at boot which system you boot into.


Just a few remarks:
Changing anything about the setup on your computer is never absolutely 100% garanteed safe.

Backing up is always a good idea.

If you want to change Vista partitions, use the Vista tool to do it. The various Linux tools should also work, but why not use the one made by the company who invented the file system?

---

### Post by poosietgp on 2010-09-04
> **JJuel said:**
> If I didn't want Ubuntu to affect either one of those should I unplug them both or just the one that has Vista on it? Obviously nothing boots from my second drive right now I just have music, movies and school files on that one. 

If I am booting from the Ubuntu drive will I be able to choose which operating system from there or will I have to set my boot priorities different each time I want to switch?

You can just unplug the one with vista on it or both. But again anything could go wrong so unplugging both is safer. Accidents can happen like accidentally erasing the whole drive, etc.

Yes, you can choose your operating system via grub (grub is the bootloader for ubuntu.). Grub runs after the BIOS finishes, and it displays a menu of all the OSes installed on your machine. 
If ever you cant find your windows os in the bootloader just continue booting in Ubuntu and go to a terminal then issue the command below.

```
sudo update-grub
```

Issuing this command will probe all your detected drives for any OS installation and adds them to the Grub boot menu at boot time.

---

### Post by JJuel on 2010-09-04
Thank you everyone! 

I think I have decided I am going to back up all of my current files AND I am going to get a new HD to put Ubuntu on. HD storage is so cheap these days it is really better to be safe than sorry. Again thanks for all of your advice, and I am sure I will need some more while trying to install, and after I get Ubuntu up and running :)

Thanks again!

---

### Post by bobhamilton on 2010-09-04
I've gone through installing and uninstalling both XP and Ubuntu Lucid Lynx (LL) on my computer multiple times. In this process I partitioned 20 GB and was able to install XP on this 20 GB partition. I want to install LL on the remaining 480 GB of my hard drive. When I use GParted, it recognizes this partition. I do not have LL installed on my computer at this time, however I do have XP installed on my 20 GB partition. As I write this I am using a live boot disk. When I tell LL to install itself however, it does not see any operating systems on my computer and asks if I want to delete everything and use all 500 GB. I have no idea what to do. Help

---

### Post by audiomick on 2010-09-04
Try choosing the "manual partitioning" option, maybe.

Then you should be able to point the installer at the partition you want to use.

---

### Post by bobhamilton on 2010-09-04
When I try to specify it manually it only specifies the 500 GB hard drive.

---

### Post by bobhamilton on 2010-09-04
So I decided to just go ahead and install Lucid Lynx. After I load XP from the GRUB menu however, XP does an autocheck and quits when it can't find some file.

---

### Post by JJuel on 2010-09-05
I am currently in the process of getting my files backed up onto a 1TB external HDD. Hopefully it doesn't take that long so I can jump into the installation of LL.

---

### Post by bobhamilton on 2010-09-05
Ok, so I actually got it to work. It was actually really easy. Here's how I did it:

1) Used live CD to install Ubuntu version 10. I used the entire capacity on my hard drive.
2) Rebooted and put XP install disc in. Deleted the Ubuntu partition. Then I allocated about 20 GB to a separate partition. I installed Windows on this 20 GB partition. 
3) Shut off the computer. Then I turned it back on and installed Ubuntu on the remainder of my computer's hard drive. 

The forum documentation is right on. It is MUCH easier to install Windows first. Admittedly this is not the most optimal way to do this, but it worked for me, required virtually no high tech knowledge (aside from knowing what a partition is), and might help somebody else stuck in my situation.

---

### Post by oldfred on 2010-09-06
You do not have to disconnect drives (I not not). But many have had issues and I am sure that is why Mark Phelps and others suggest removing other drives. If you leave drives plugged in what is critical is the advanced button that you tell grub which drive to install to. Grub likes to install to sda as it assumes that is your boot drive. Use BIOS to then set which drive to boot that has grub.

Advanced button
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by JJuel on 2010-09-06
> **oldfred said:**
> You do not have to disconnect drives (I not not). But many have had issues and I am sure that is why Mark Phelps and others suggest removing other drives. If you leave drives plugged in what is critical is the advanced button that you tell grub which drive to install to. Grub likes to install to sda as it assumes that is your boot drive. Use BIOS to then set which drive to boot that has grub.

Advanced button
[http://members.iinet.net.au/~herman546/p24/022f.png]("http://members.iinet.net.au/%7Eherman546/p24/022f.png")
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

I am currently backing my files up anyways, but you are saying I wouldn't have to unplug the HDD I just need to make sure I selected the right drive?

I am reading your second link right now, and yeah it does make sense. The only thing unplugging would do for me is just to make sure I couldn't make a mistake like you say huh?

Thanks everyone for all the help. My backup should be done in the morning, and I plan to undertake this task tomorrow.

---

### Post by JJuel on 2010-09-06
Do I need to format the drive in windows before I go to install Ubuntu on the new hard drive? 

Also what is better I have a 64-bit capable system should I use the 64-bit or 32-bit ubuntu? I have heard things saying 32 is better, but would like to know what you guys think. 

Thanks

---

### Post by oldfred on 2010-09-06
There are a bunch of threads on 32 vs 64. I use 64 bit Ubuntu and do not have any issues. Only if you do not have much memory should you consider 32bit. If you do any video or audio conversions the 64bit will be better.

Windows cannot format any partitions for Ubuntu install. If you are also creating a shared NTFS you can do that in windows or not. Gparted can do it in advance or you can do it as part of the install. The auto choices will only give you / (root) & swap. If you want any additional you should use gparted to set them up first, then use manual install to choose which partition is / , which is /home & it seems to find swap automatically.

[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by JJuel on 2010-09-06
So if I am just going to put Ubuntu on this whole drive I will not need to format it in windows at all? I can just start to install Ubuntu and it will format it for me right?

Thanks so much.

---

### Post by egalvan on 2010-09-06
You do not need to format the new drive before installing Ubuntu.

just pick the "use entire drive for Ubuntu" option.
the installer will format as needed.

note that if you unplug all other drives, you will not be able to mistakenly use the wrong drive.
Better safe than sorry...


And as others have stated, once the install has finished, 
shut down your machine, reconnect the drives,
re-boot, and a quick 

```
sudo update-grub
```

will make the other OS show up in your GRUB boot menu.

---

