---
title: "Ubuntu 9.04 Installatio Prblm"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by sarvankarthik6 on 2009-09-12
**Guide me**

  Installed inside windows. next day not able to access system both XP n Ubuntu.

probs:
Wen I open In Ubuntu
 Cant find Grldr in all devices.

 in consistent file structure
 invalid compressed format
 ACPI aborted beacuse junk is compressed archv..
Wen I open XP
 
 Juts showing blank window nothing is displayed, left it for few hours...no use.



I re formatted. :(


I guess I did Ubuntu instalation in C drive itself where XP resides..


there are many ways i saw to install ubuntu... plz tell me a simeple way that doent harm XP..


thanx in advance!

---

### Post by redbob on 2009-09-12
Hi, sarvankarthik6! Welcome!

One of good things Ubuntu has got is flexibility.
If you're using Live-CD install, make a Manual Partitioning. So you could resize your partition, create a new partition into unmounted space, and create a new installation into it.

---

### Post by sarvankarthik6 on 2009-09-12
Thanks for ur reply...


Friend, Im newbie to using it...Mounting,Partitining etc are new terms for me.. owned sys newly.. 

I ordered Ubuntu online n i got courier. had CD of UBUNTU..

can u elaborate ur reply plzz ...

U mean i shud install it on oter drive say D:>? my D drive had 40GB free space.

Im sry if i irritate...

---

### Post by MelDJ on 2009-09-12
there are many ways i saw to install ubuntu... plz tell me a simeple way that doent harm XP..


go to xp. put the ubuntu cd into tray. a menu will come. select install inside windows. pick where you want to install ubuntu and how much space you want to allocate for it. then make a cup of coffee and let the installation progress:D. then restart the computer and you will be able to choose between running ubuntu or xp.
this is the installing inside windows way. it wont harm you windows at all

---

### Post by sarvankarthik6 on 2009-09-12
Thank You friend. I will give another trail.

My tension is that:

 after ubuntu installed, i switched to XP. i did defragmentation using Tune Up utilities. it forced me to restart. from then im not able to use XP. that's Y.

kk I'll have a cup of coffee..cheers to you as well..

Also:

can i install the following in UBUNTU:

[LIST=1]
[*]SQL Server 2008
[*]Visual studio 2008
[/LIST]
as it requires IIS to be enabled to work with asp.net.:popcorn:

---

### Post by NoaHall on 2009-09-12
You can't run them directly, but I'm running mine through VirtualBox running Windows 7 RTM.

Or install something called Gambas2, it's quite the same, except the coding isn't the 2008 version.

---

### Post by 3rdalbum on 2009-09-12
No matter how Ubuntu is installed, it shouldn't harm Windows. However, if you use the "Install inside Windows" option, then any problems booting Windows will prevent Ubuntu from being able to boot either (it's a long story as to why this happens, but it definitely does happen, and it's why I don't recommend this sort of fake install).

Your best bet is to either install Ubuntu onto your other internal hard disk, the 40 gig one (Ubuntu doesn't use drive letters like D: so neither will I); or use the "Resize a partition" option to create space on your main hard disk. Both options require you to boot up your computer from the CD and choose the "Install Ubuntu" option at the menu. Follow the prompts and you'll be fine.

If you decide to resize your main hard disk's partition, note that there is a slider in the bottom bar graph of the partitioning screen. You must drag this little slider to the left in order to allocate Ubuntu some disk space. If you don't, then Ubuntu installs into the minimum possible amount of space, which is no fun for anyone.

EDIT: You're switching to Ubuntu and wanting to use Microsoft software on it?! Instead of SQL Server, try MySQL - 95% of the features, 0% of the cost. Instead of IIS, try Apache - it's what all the big boys do, and it's more secure and reliable than IIS. I hear things about Gambas, but I never used it because BASIC is not my type of language. Try learning Python and GTK, and that way you'll be of much use to us :-)

---

