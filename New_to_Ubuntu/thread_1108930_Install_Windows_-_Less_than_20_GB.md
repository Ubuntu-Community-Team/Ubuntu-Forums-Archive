---
title: "Install Windows - Less than 20 GB?"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by UnknownFear on 2009-03-28
I use Ubuntu for pretty much everything, but I want to install Windows mainly for the purpose of gaming. Now, I know how to boot into the LiveCD and resize the partition in GParted, so that is not a problem. The question I want to know is: is it possible to install Windows with a set amount of space? For instance, could I install Ubuntu with 20 GB, more than enough for a few games, nothing else?

---

### Post by mikewhatever on 2009-03-28
> **UnknownFear said:**
> I use Ubuntu for pretty much everything, but I want to install Windows mainly for the purpose of gaming. Now, I know how to boot into the LiveCD and resize the partition in GParted, so that is not a problem. The question I want to know is: is it possible to install Windows with a set amount of space? For instance, could I install Ubuntu with 20 GB, more than enough for a few games, nothing else?

Yes, you can install Windows to a partition of 20 GB, as well as Ubuntu.

---

### Post by GrimmReaperVI on 2009-03-28
Depends on the size of the Hard drive

---

### Post by presence1960 on 2009-03-28
> **UnknownFear said:**
> I use Ubuntu for pretty much everything, but I want to install Windows mainly for the purpose of gaming. Now, I know how to boot into the LiveCD and resize the partition in GParted, so that is not a problem. The question I want to know is: is it possible to install Windows with a set amount of space? For instance, could I install Ubuntu with 20 GB, more than enough for a few games, nothing else?

I have XP Pro installed on a 20GB partition. Works great. I only have Adobe Acrobat Professional and Office Enterprise 2007 installed on there because I need them for work. This is the only time I boot into Windows.

---

### Post by linuxisevolution on 2009-03-28
My sisters computer has a 20gb hard drive and she has 2 winxp installs and one Ubuntu install. Ubuntu has 10gb of the hard drive and each xp install has 4.5gb... Both xp installs died long ago though(one has missing sys32 and the other bsod on boot).

I have windows 2000 on this laptop in a 990mb partition lol:guitar:

Ubuntu is on the other partition (30gb).

Windows Xp needs 4gb
Windows 2000 needs 700mb
Ubuntu needs about 5gb


Good luck.

---

### Post by DutchShrek on 2009-03-28
I know nothing about Linux, but Windows is a different story.
You wish to use it for games, I suppose the size of your windows partition will have to be enough to carry those games.
I don't know what games you are  talking about.
An extreme example would be GTAIV, this is a 10GB install by itself, give or take.

As for Windows itself, there are steps you can take in order to make the install smaller.
You could look for tutorials on using Nlite. Of course  this requires you to work from Windows so it may not be helpful. I don't know if Wine would help with this?
But Nlite will allow you to rebuild a windows ISO, in order to take out most of it's bloatware.
You can bring down a 4GB install to under 1GB.
Actually, this will also improve the speed greatly. So for gaming, it comes in handy!

I don't know if helped you at all, but I figured I'd throw this in here

---

### Post by UnknownFear on 2009-03-28
So would I use the LiveCD, open GParted and resize the partition to... say, 20 GBs. Than, use the Winodws XP cd and install it on that partition?

---

### Post by tylerspaska on 2009-03-28
I have XP on less than 5GB, granted I don't have any games installed.

---

### Post by BDNiner on 2009-03-28
20GB is not enough for a windows install. You will run out of space quickly. There are windows installer files that are used whenever a windows update or other software is installed. They are normally placed in C:\windows\installer. That directory can take up more than 10GB. I would recommend 40GB if you didn't want to do maintennance every year or so.

---

### Post by DutchShrek on 2009-03-28
I agree with BDNiner, 20GB is probably not enough.
Even if you don't update your Windows, you will still run out of space quickly when installing programs and especially games.

Like I said, it depends on the software/games you are trying to run.
Some are real diskspace hogs.
If you have enough, I'd go with 40GB. 

but to answer your question...yes, open gparted, create and format your partition to NTFS and install windows to that partiton.
Or at least shrink your current partitoon to make free space.
During install of windows you'll have the opportunity to create the ntfs partition in the free space available

---

### Post by lykwydchykyn on 2009-03-28
Don't know about Vista, but you want to leave XP a few GB of wiggle room so the page file doesn't get fragmented.  

How big are you games?

---

### Post by argie on 2009-03-28
> **UnknownFear said:**
> So would I use the LiveCD, open GParted and resize the partition to... say, 20 GBs. Than, use the Winodws XP cd and install it on that partition?

You can get away with that, but if you have many modern games you might run out of space. Still, that sounds like enough space for 4 or 5 games.

One word of warning, it is likely that installing windows will overwrite the master boot record. It's a good idea to find out how to reinstall GRUB first.

---

### Post by SunnyRabbiera on 2009-03-28
Yeh it depnds on the drivespace, if the OP only has 40GB of space it actually might be better to just use XP on that drive until they get another HD.
Knowing how much space XP needs after all its updates and knowing how much space major commercial games need 20GB will run out real fast.

---

