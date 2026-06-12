---
title: "What to Expect When Dual Booting?"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by Wataru8675 on 2009-09-06
Hey folks. I just got a new laptop and want to dual boot Linux with Windows 7 when it comes out later. What should I expect when dual booting? I (think I kind of) know how to go about doing so, but what will happen to my existing single partition that holds (what is now) Vista? Will it just be shrunk, so everything I have on it will be saved? For example if I download the couple things I want on Windows (Myst, Firefox, just a couple programs)...will they remain after I dual boot, or will I have to reinstall them?
 
Also, I'm a bit confused as to where my media will be accessed from. If I, say, rip a CD using Linux, can it only be accessed when I'm running the Linux boot? And vice versa with Windows? Or can I make a third partition where all my media will go, that both Windows and Linux can access?
 
Third, about how big should I make my partition? I'm using Vista primarily for gaming and maybe for a thing or two more (like my webcam), so I won't be using it a whole lot... I was thinking maybe 75GB of my 500GB HDD?
 
Anything else I should know about dual booting?

---

### Post by k33bz on 2009-09-06
everything on your windows side would stay the same, just shrink the partition on which it sits. You would not need to re-install anything at all.

Warning however, unless things have changed since the last time I checked on it, Vista itself is very temperamental about shrinking the partition it self stays on.

---

### Post by Wataru8675 on 2009-09-06
Oh crud.  What does that mean, "temperamental"?

---

### Post by HermanAB on 2009-09-06
Howdy,

Note that the Ubuntu installer is notoriously bad when it comes to making machines dual boot.  Most other Linux distributions handle a dual boot install automatically and error free, but Ubuntu has a lot to learn in this regard still and this is the favourite way for newcomers to lose all their Windows data...

Some pointers:
Install Windows first.  If already installed, defragment it.
Boot with Linux CD and run Gparted to split the disk into two partitions.
Now install Ubuntu and tell it to do so on the secondary partition.

If all the computer gods are smiling kindly upon you, you should end up with a machine that will have multiple entries in the Grub boot menu.

Linux can access Windows file systems without much of a problem using VFAT or NTFS-3g.  Windows can access Linux Ext3 file systems if you install special software.

---

### Post by k33bz on 2009-09-06
> **HermanAB said:**
> Howdy,

Note that the Ubuntu installer is notoriously bad when it comes to making machines dual boot.  Most other Linux distributions handle a dual boot install automatically and error free, but Ubuntu has a lot to learn in this regard still and this is the favourite way for newcomers to lose all their Windows data...

Some pointers:
Install Windows first.  If already installed, defragment it.
Boot with Linux CD and run Gparted to split the disk into two partitions.
Now install Ubuntu and tell it to do so on the secondary partition.

If all the computer gods are smiling kindly upon you, you should end up with a machine that will have multiple entries in the Grub boot menu.

Linux can access Windows file systems without much of a problem using VFAT or NTFS-3g.  Windows can access Linux Ext3 file systems if you install special software.


IDK about that, I had a dual boot just fine with XP and Ubuntu.

---

### Post by Wataru8675 on 2009-09-06
> **HermanAB said:**
> Howdy,
 
Note that the Ubuntu installer is notoriously bad when it comes to making machines dual boot. Most other Linux distributions handle a dual boot install automatically and error free, but Ubuntu has a lot to learn in this regard still and this is the favourite way for newcomers to lose all their Windows data...
 
Some pointers:
Install Windows first. If already installed, defragment it.
Boot with Linux CD and run Gparted to split the disk into two partitions.
Now install Ubuntu and tell it to do so on the secondary partition.
 
If all the computer gods are smiling kindly upon you, you should end up with a machine that will have multiple entries in the Grub boot menu.
 
Linux can access Windows file systems without much of a problem using VFAT or NTFS-3g. Windows can access Linux Ext3 file systems if you install special software.
 
...and if the gods AREN'T smiling upon me?

---

### Post by k33bz on 2009-09-06
What he means by that is Vista does not like it's partition size being downgraded, there are several success stories, but I personally have no experience with dual booting linux and Vista, just XP. And yes grub itslef, with ubuntu can act up, didn't with me though, but there are always ways to work around all of this.

---

### Post by Mark Phelps on 2009-09-06
> **Wataru8675 said:**
> Hey folks. I just got a new laptop and want to dual boot Linux with Windows 7 when it comes out later. What should I expect when dual booting? I (think I kind of) know how to go about doing so, but what will happen to my existing single partition that holds (what is now) Vista? Will it just be shrunk, so everything I have on it will be saved? 
There should be no problems as long as you use the Vista Disk Management utility to shrink Vista.
> For example if I download the couple things I want on Windows (Myst, Firefox, just a couple programs)...will they remain after I dual boot, or will I have to reinstall them?
They will not be touched.
 
> Also, I'm a bit confused as to where my media will be accessed from. If I, say, rip a CD using Linux, can it only be accessed when I'm running the Linux boot? And vice versa with Windows? Or can I make a third partition where all my media will go, that both Windows and Linux can access?
The default in both OSs is to put the files local to the OS.  But if you create a shared NTFS partition and direct the files there, you will be able to access the files from either OS.
 
> Third, about how big should I make my partition? I'm using Vista primarily for gaming and maybe for a thing or two more (like my webcam), so I won't be using it a whole lot... I was thinking maybe 75GB of my 500GB HDD?
I have a LOT of stuff in Vista and 35GB gives me room to share.
 
> Anything else I should know about dual booting?
Yes, IMHO, it's the best solution for using two different OSs.

---

### Post by Wataru8675 on 2009-09-06
> **Mark Phelps said:**
> There should be no problems as long as you use the Vista Disk Management utility to shrink Vista.

 
I just rifled through the contents of the box my lappertop came in and see no discs.  What is this?

---

### Post by Hobgoblin on 2009-09-06
> **Wataru8675 said:**
> I just rifled through the contents of the box my lappertop came in and see no discs.  What is this?

It is an application within Vista.

IIRC you find it within computer management.

---

### Post by pi.boy.travis on 2009-09-06
I dual-booted successfully for about a year before I went 100% open source.  You can keep all your data as long as you act carefully and methodically. Here is what I did:

-Defrag your Vista partition manually, then again, then once more.  You may want to run the disk cleanup utility, and do anything else you can to minimize the amount of data on that partition.

-Boot into the Ubuntu LiveCD environment.  Go to System>Administration>Partition Editor, and shrink your Vista partition to the desired size.  If you get an error, boot back into Vista and defrag some more.  Leave the free space alone for now.

-Reboot the Ubuntu LiveCD, and start the installer. When you get to the partitioner, tell Ubuntu to use the largest continuous free space, then continue as usual.

-Laugh Heartily! 

Good luck!

---

### Post by Megaptera on 2009-09-07
> **Hobgoblin said:**
> It is an application within Vista.

IIRC you find it within computer management.

Here's a guide with screenshots - worked for me:

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by Wataru8675 on 2009-09-07
> **Hobgoblin said:**
> It is an application within Vista.
 
IIRC you find it within computer management.
 
Fantastic, I found it...now I just want to be 100% sure I'm going to do this right so I have no problems:
 
I right click on the biggest partition...click "Shrink Volume...", and then set it to how many MB I want it BEFFORE I install Ubuntu, right? And then it'll make another partition with all the extra space on the HDD which I will then install Ubuntu to?

---

### Post by Wataru8675 on 2009-09-07
> **pi.boy.travis said:**
> I dual-booted successfully for about a year before I went 100% open source. You can keep all your data as long as you act carefully and methodically. Here is what I did:
 
-Defrag your Vista partition manually, then again, then once more. You may want to run the disk cleanup utility, and do anything else you can to minimize the amount of data on that partition.
 
-Boot into the Ubuntu LiveCD environment. Go to System>Administration>Partition Editor, and shrink your Vista partition to the desired size. If you get an error, boot back into Vista and defrag some more. Leave the free space alone for now.
 
-Reboot the Ubuntu LiveCD, and start the installer. When you get to the partitioner, tell Ubuntu to use the largest continuous free space, then continue as usual.
 
-Laugh Heartily! 
 
Good luck!
 
This answers my question to above.  Shoulda refreshed before I posted.  Thanks!

---

### Post by crownedzero on 2009-09-07
Just my two cents; screw messing around with shrinking the volume and dual booting off of one hard disk. Pick up an external OR grab virtualbox and install that way. It takes a little setting up but in the end you get the same result with less headache. I also enjoy the fact that you don't have to reboot to go back and forth.

---

### Post by piperdown10 on 2009-09-07
I agree with **crownedzero**. I have Win98 and Vista on VirtualBox and they work great.

---

### Post by Wataru8675 on 2009-09-07
What is Virtualbox, and how does it work?

---

### Post by longtom on 2009-09-07
> **Wataru8675 said:**
> What is Virtualbox, and how does it work?

In this particular case plodding in VirtualBox will confuse the matter of the OP.

If anything, he could install Ubuntu in a VirtualBox in his Vista install.  I, however, am convinced, that this will not have satisfiable results in checking out, how Ubuntu works and what it can do.  It certainly defeats the purpose as far as security is concerned.

Having Windows in a VirtualBox in Ubuntu does work (I do it with XP), however one must keep in mind that a VB installation can not take advantage of your video setup and 3D applications might not run as good as in a normal install or not at all.

To the OP:

VirtualBox is an application which gives you the opportunity to run an OS in a virtual setup, provided your PC has enough resources (mostly ram) to do so.  I use this all the time to test different OS' as well as different flavours of Linux (also known as distros or distributions).  However, as said above, it does not take advantage of all of your hardware, since some of it gets created by the program virtually.

I would suggest to back up your data and go for the dual boot as described above.  Once that is done, you can install VirtualBox in Ubuntu and test the waters and see, if it is enough to run Vista the way you want to have it run.
Once that is done and you are satisfied, you can use it that way and do away with your dual boot.  Just make very sure.

All in all - it is not as complicated as it sounds.  Once you are in it, things explain itself most of the time.  It looks like a mountain now - it isn't really.

And should you get into trouble - shout.  This here is the best and most helpful online community you will find for Ubuntu related problems.

Good luck!!

---

### Post by Wataru8675 on 2009-09-07
A couple more questions about partitions now have come up... First, when I tried to resize the partition using Disk Manager, Vista won't let me make it less than 205GB. How can I change this? I'd like to make it around 50...
 
Also, when I checked on how much disk space was being use, I found that Windows is already occupying 40GB of my HDD...and I literally just bought this yesterday. Is this a "stupid Windows" moment, or a necessary evil?

---

### Post by longtom on 2009-09-07
> **Wataru8675 said:**
> A couple more questions about partitions now have come up... First, when I tried to resize the partition using Disk Manager, Vista won't let me make it less than 205GB. How can I change this? I'd like to make it around 50...
 
Also, when I checked on how much disk space was being use, I found that Windows is already occupying 40GB of my HDD...and I literally just bought this yesterday. Is this a "stupid Windows" moment, or a necessary evil?

I am not familiar with Disk Manager.  I popped in the Ubuntu live disk and used gparted.

After I defraged my Windows installation (XP) I could shrink it the way I wanted.

As far as the 40GB are concerned, I have heard Vista grabs a lot - but this seems ridiculous. 

Good luck!!

---

### Post by Wataru8675 on 2009-09-07
> **longtom said:**
> I am not familiar with Disk Manager. I popped in the Ubuntu live disk and used gparted.
 
After I defraged my Windows installation (XP) I could shrink it the way I wanted.
 
As far as the 40GB are concerned, I have heard Vista grabs a lot - but this seems ridiculous. 
 
Good luck!!
 
Ah. On XP.  I think Disk Manager is only on Vista, if I'm understanding these previous posts correctly.  It was made to sound earlier that Vista might not act desireably if I just use gparted.

---

### Post by longtom on 2009-09-07
> **Wataru8675 said:**
> Ah. On XP.  I think Disk Manager is only on Vista, if I'm understanding these previous posts correctly.  It was made to sound earlier that Vista might not act desireably if I just use gparted.

I never used Vista, so I am afraid somebody else needs to talk up.

---

### Post by pi.boy.travis on 2009-09-07
> **Wataru8675 said:**
> A couple more questions about partitions now have come up... First, when I tried to resize the partition using Disk Manager, Vista won't let me make it less than 205GB. How can I change this? I'd like to make it around 50...
 
Also, when I checked on how much disk space was being use, I found that Windows is already occupying 40GB of my HDD...and I literally just bought this yesterday. Is this a "stupid Windows" moment, or a necessary evil?


This is indeed a stupid Windows moment.  My Vista partition refused to shrink smaller that 60 GB.  It has something to do with the way Vista handles shadow copies, or some pointless, frivolous thing like that. . .

---

### Post by pi.boy.travis on 2009-09-07
> **Wataru8675 said:**
> Ah. On XP.  I think Disk Manager is only on Vista, if I'm understanding these previous posts correctly.  It was made to sound earlier that Vista might not act desireably if I just use gparted.

Vista will get upset if you shrink it's partition using an external tool, but it should work out ok as long as you give it the space it needs.

---

### Post by Wataru8675 on 2009-09-07
So would I just be safer to shrink it via Disk Manager? I'd really rather not have a 200GB partition for Windows, but if I'm stuck...

---

### Post by pi.boy.travis on 2009-09-07
> **Wataru8675 said:**
> So would I just be safer to shrink it via Disk Manager? I'd really rather not have a 200GB partition for Windows, but if I'm stuck...


If you defragment it, you should be able to shrink it with gParted, just make sure you back up your important stuff first.  gParted is good, but not perfect.  

Another option is to back up your data, then reinstall Vista in a smaller partition, leaving as much room as you want for Ubuntu.

---

### Post by Wataru8675 on 2009-09-07
I got Vista out-of-box.  Is there a way I can burn an .iso of it or something, or is there another way...?
 
Actually, now that I think of it, I should be getting a Windows 7 upgrade come October/November.  Would that do the trick?

---

### Post by Hobgoblin on 2009-09-07
> **Wataru8675 said:**
> 
I right click on the biggest partition...click "Shrink Volume...", and then set it to how many MB I want it BEFFORE I install Ubuntu, right?
Yes.

> And then it'll make another partition with all the extra space on the HDD which I will then install Ubuntu to?
No, just leave the rest unpartitioned, boot from the Ubuntu CD and install Ubuntu with the default settings which should be to use largest free space.

---

### Post by Windows Nerd on 2009-09-07
> **pi.boy.travis said:**
> Vista will get upset if you shrink it's partition using an external tool, but it should work out ok as long as you give it the space it needs.

It worked fine with me, I resized and set every single partition the way it is from my default setup using GParted. I know some people have had some pretty bad experiences with GParted, but you should be fine if you:

1) BACK UP YOUR DATA! This is very important when working with partitions at all, as if you accidentally nuke your partition, you have no need to worry.

2) Do your research. There is no reason to be confused when working with partitions.

Hope this helps,

Scott

---

### Post by Bartender on 2009-09-07
Wataru -
Have you made your recovery discs yet?
This might sound a little radical, but it should work.  If you burned your recovery discs, and you're pretty sure they're viable, boot up with a GParted LiveCD (link under my sig) and wipe the drive clean.  Then create a primary NTFS partition for Vista.  40GB, 60GB, whatever.  When you drop the recovery disc in, it should only recognize the NTFS partition and ignore the rest.

---

### Post by scared0o0rabbit on 2009-09-07
is there a way to edit what OS is selected by default in grub on bootup?  I'd like to install linux along side xp on another computer that's going to be using xp like 90% of the time.  Having ubuntu first works great on my main pc, but if I can't have xp be the default bootup on this other computer I'm just going to have to do with xp only on it.

---

### Post by k33bz on 2009-09-08
yes there is a way. Forgive me how ever if I dont remember how to set it up that way.

---

### Post by markusf21 on 2009-09-08
Install startupmanager via add/remove or synaptic or in a terminal put
```
sudo apt-get install startupmanager
```
It will be under system admin you can use it to set a lot of stuff up, like default boot, number of menu entries even the timer. IMHO much easier than editing menu.lst

---

### Post by Wataru8675 on 2009-09-08
Windows Nerd:  I'm not confused...I'm just trying to make 100% sure that I'm doing this correctly so I don't eff up my new computer...  I have a bad habit of ruining technology fast, and it's not a habit I necessarily enjoy.
 
Bartender:  Thanks a lot, I think I'll do that if GParted doesn't work.  Not much to back up right now; anything I want is automatically backed up with Steam, so not terribly concerned with backing up.

---

### Post by nick24 on 2009-09-08
> **k33bz said:**
> IDK about that, I had a dual boot just fine with XP and Ubuntu.

Same here. I never had a problem dual booting XP with Ubuntu.  I had to update Grub in order for it to detect XP only because I am using unofficially released Ubuntu version (Karmic) other than that it runs like charm.

---

### Post by lukeiamyourfather on 2009-09-08
> **Wataru8675 said:**
> Hey folks. I just got a new laptop and want to dual boot Linux with Windows 7 when it comes out later. What should I expect when dual booting? I (think I kind of) know how to go about doing so, but what will happen to my existing single partition that holds (what is now) Vista? Will it just be shrunk, so everything I have on it will be saved? For example if I download the couple things I want on Windows (Myst, Firefox, just a couple programs)...will they remain after I dual boot, or will I have to reinstall them?
 
Also, I'm a bit confused as to where my media will be accessed from. If I, say, rip a CD using Linux, can it only be accessed when I'm running the Linux boot? And vice versa with Windows? Or can I make a third partition where all my media will go, that both Windows and Linux can access?
 
Third, about how big should I make my partition? I'm using Vista primarily for gaming and maybe for a thing or two more (like my webcam), so I won't be using it a whole lot... I was thinking maybe 75GB of my 500GB HDD?
 
Anything else I should know about dual booting?

If it were my laptop I'd install Windows 7 first using about 40GB on a single partition. Then install Linux on another 40GB partition at which point Ubuntu should automatically setup the boot loader and recognize Windows on the other partition. Then take whatever space is left and make a large partition for user data, probably in FAT32 so it can be read from both Windows and Linux, note that you'd have to create that partition in Linux since Windows has a (artificial) limitation on the size of FAT32 that it can create. Other option would be to make the media partition ext3 and use an installable file system to read it from Windows, but that's a little more tricky and risky. Cheers!

---

### Post by Wrathe on 2009-10-04
I allocated 117GB out of 300GB or so by using Disk Management in Vista.  Then put in the Ubuntu CD and went through the installation.  When I got up to the partitioning part of it I selected the 'use largest contigous space.' The preview diagram then went all 'weird.' It said my Vista1 (recovery partition) had 11GB, my Vista2 had 280GB and Ubuntu only had 2.5GB.  Is this a bug?

Should I just install it using the manual option?

Thanks

---

### Post by rs_man on 2009-10-04
My system was initially setup for XP, formatted 80GiB. Then created a second logical drive about 20GiB to point *My Documents* to. When it came time for installing Ubuntu I used the manual partitioner, from the LiveCD, to create a partition and swap. Fairly simple, though the partitioner sets up the partitions based on KBs so you may have to do some math to get the exact MiB/GiB space allocation. Not sure how anyone else recommends swap setups but I was advised that its wise to make it at least twice the volume of your RAM.
my $0.02...

To the OP:
When loading Windows7 the installation wizard should identify other partitioned space on the drive. It should be fairly simple to work through. Have you tried creating a "test" partition through the setup wizard(windows) yet?


Ryan

---

