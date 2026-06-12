---
title: "installed game wont run"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by SaiWarrior on 2010-09-18
I'am new to this Ubuntu (10.04) scene, but I've been getting to know how to use Ubuntu. I've recently installed Wine and a windows game that I haven't play with since Windows 98( I know old right XD) anyway I've installed it... it flashes on the taskbar( or whatever you call it for Ubuntu) like 3 or 4 times, I don't know what happened. I cd to the install dir and run "# wine ProgramName" and all it gives me is this "wine: cannot find L"C:/Windows/system32/NameOfProgram.exe"" Anyone know why? I've cofiged it so it runs the program with Win98 but still the same result. 

Thanks in Advanced
Ubuntu n00b

---

### Post by shuamu on 2010-09-18
I can think of a few things getting in your way here.

First off, I doubt you installed the game into the system32 folder. If so, that was silly. You should have installed it in program files.

Second, you should be able to run access it fairly simply from Applications > Wine > Programs.

If it's not in there, then you need to try the install again.

Third of all, which game is it? Is there any chance you might need directX for it? If so, you're going to have to add dxd# to your library (where # is the version of dX you would need).

---

### Post by 29732 on 2010-09-18
try installing playonlinux
then look at the list and see if your game shows on there
and if it doesnt, i doubt the game will run correctly

---

### Post by 29732 on 2010-09-18
> **SaiWarrior said:**
>  I cd to the install dir and run "# wine ProgramName" and all it gives me is this "wine: cannot find L"C:/Windows/system32/NameOfProgram.exe"" Anyone know why? I've cofiged it so it runs the program with Win98 but still the same result. 
 
Ubuntu n00b
keep in mind that ubuntu doesnt read partitions as "C:/" and etc.
you need to get into your old partition (with nautulius) and just grab the installer out of windows onto ubuntu (so it will be easier for me to understand and hopefully easier for you) and install it like that
and why do you have the game in system32?

---

### Post by shuamu on 2010-09-18
Also keep in mind that wine may not be able to detect your disc drive, if you're attempting to run a game that requires the disc to play. You'll need to rip the iso to your hard drive and mount it, in that case.


With regards to the earlier comment about "playonlinux": I say bollocks. There are plenty of games that work great with a little effort, which are not listed on playonlinux.

---

### Post by soldier1st on 2010-09-19
for the name of the game in question check this site [http://www.winehq.org/](http://www.winehq.org/) and see if it compatible with Wine, also for wine don't use non stable Wine versions as they could contain bugs and other problems so use the latest 1.2 Stable, also be aware that gaming on Linux is not that good though that is constantly changing and evolving.

---

### Post by SaiWarrior on 2010-09-19
> **shuamu said:**
> 

First off, I doubt you installed the game into the system32 folder. If so, that was silly. You should have installed it in program files.



1:I installed it into programs folder when i ran the installer the 
first time.
2nd: the game is called Zombie Shooter for windows 98.
ATM im going to install Zombie Shooter 2 and here are the sys reqs
Operating System : Microsoft Windows XP / Windows Vista / Windows 7
Processor : Intel Pentium IV at 2.5 GHz / AMD Athlon XP 2600+
Video Card : 128 MB VRAM – NVIDIA GeForce FX 5700 / ATI Radeon 9600
Memory : 1 GB RAM
Hard Disk : 1.5 GB of free Hard Drive space
Sound : DirectX 9.0 compatible sound card
Direct X : 9.0c
Controls : Keyboard & Mouse
Installation : DVD-ROM Drive 
Released : July 2010 (Wow 12 years later! I think the are copying SC2, SC2 released 12 years after the first one.)
I have higher then needed to run this game. Also will this run on Wine?

---

### Post by Paddy Landau on 2010-09-19
I really do recommend [PlayOnLinux]("apt:playonlinux") (it's in the repository). It handles a lot of the installation for you -- it's a sort of front-end for Wine. In fact, I don't know how to use Wine; I just use PlayOnLinux.

Having said that, be aware that Wine is an imperfect attempt at a Windows API. It's not Windows. Some things work well, many work with minor problems, and most don't work.

If you install through PlayOnLinux and it still doesn't work, the chances are that you'll need a Windows installation.

*EDIT* See the [Wine apps]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18821").

---

