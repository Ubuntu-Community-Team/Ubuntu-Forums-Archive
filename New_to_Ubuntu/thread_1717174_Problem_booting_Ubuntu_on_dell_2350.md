---
title: "Problem booting Ubuntu on dell 2350"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by nhwd on 2011-03-29
I have a couple of problems with Ubuntu and my computer.
First, I'm using a live disk that I burned myself. One of the problems is that when I reboot, my system doesn't read the disk and starts Windows normally. After restarting Windows, I press F8 or F12 (not sure which) and get a boot menu and I select the option that runs it from the Disk Drive. So, it runs Ubuntu's loading page but it freezes after a while and doesn't load. So then, I try installing it onto Windows but I get an error that says something about list "index out of range"... I have around 1 gb plus of free space so I think that's why I get that error. Then I try to install the program that the live CD offers to help add a boot menu but I have trouble installing that as well and I get a "permission denied" error.

I run Windows XP on a Dell Dimension 2350 with around 614mb of ram and I have 27gb in total of space but only around 1.4 gb of free space.

---

### Post by fabricator4 on 2011-03-31
You've got a couple of problems here.  Firstly, there's absolutely no way you can install Ubuntu on that machine with only 1Gb of free space.  Maybe (quite possibly) you could get a Wubi install jammed on there since it is compressed, but neither operating system would have any room at all to do anything.  Quite likely it would all fall in a large heap.

You certainly don't have enough room for a full install of Ubuntu: that would require another partition with at least 3.5 GB of space just for the filesystem, plus another few spare GB to keep everything happy for a short time.

Secondly, if you can't run the "Try Ubuntu" selection on the live CD where it runs entirely off the CD, then there's a good chance that the CD is corrupted or is otherwise not a good burn.  It may also be that your computer is not able to run the Ubuntu LiveCD such as if you don't have at least 512Mb of memory, the installer will not run.  

In this case I would suggest the alternate install CD, but that doesn't let you try it first.

There's some very light versions of Linux that you might want to look at, especially Lubuntu, DreamLinux, and DSL (Damn Small Linux)

In any case, your priority right now needs to be backing up your data and cleaning out that drive, or adding a drive to the system to give you more space.  You're going to have to do this no matter what operating system you want to run on it, and right away.

Chris.

---

### Post by Rubi1200 on 2011-03-31
There is a 3GB minimum for Wubi installs. I don't believe it is possible to go under this without causing serious problems.

---

### Post by rudy1094 on 2011-03-31
I too am trying to install Ubuntu on my Dell Dimension 2350, although I'm using the entire hard drive. I initially had problems trying to run the live CD. I got a "Busybox V1.15.3... unable to find medium containing live system" error.

It turned out to be some type of video card issue. Once I changed the BIOS to use the on board graphics card rather than the "auto" option, it allowed me to Try Ubuntu. I still haven't installed Ubuntu yet, that's tonight's entertainment.

---

### Post by wildmanne39 on 2012-07-28
Old thread closed.

---

