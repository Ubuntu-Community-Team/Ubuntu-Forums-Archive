---
title: "Backup question following failed web and HOWO search"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by Anton32828 on 2009-11-04
I have been running Ubuntu for the past few weeks as a learning experience. I used Unix a loooong time ago and am very impressed with how far GNU/Linux has come towards a desktop OS.  But I still find myself with puzzling newbie questions which I hope you can help me answer.

In my short time with the system, I have done two clean installs: one for a dual-boot of 9.04 NBR with my Windows XP netbook, and one to wipe out 9.04 entirely and allow 9.10 to format my Ubuntu partition as ext4 and install 9.10. I can see with the bug reports posted thus far and Ubuntu's frequency of updates that my clean-install procedure will be a regular occurrence. My question: is there a commonly accepted way of backing up all files, mail, browser bookmarks, and installed-package information so that customizing a fresh install is fairly automated? Is there a HowTo or graphical tool that I should know about?

Here is specifically what I would like to do:

1) Backup all the data, mail, preferences, desktop environment tweaks, and other user-level settings. Is this as simple as copying my home directory to a USB stick or external drive? I am coming from a Windows mindset that sees hidden application data repositories scattered all over different directories.... Perhaps I am over-complicating this step?

2) Run a tool that identifies my installed software so I can automatically fetch it from the servers for re-installation following a clean install. Is there such a thing? Currently I am manually re-installing such things as GnuCash, Opera, Adobe Reader, etc. I've got to believe someone has written a utility that automates this stuff.

I have found the following HowTo but it is very command-line oriented and seems more oriented towards a complete disk-copy and restore, rather than the upgrade model I've described:

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

Thanks in advance for your help.

---

### Post by yeats on 2009-11-04
> 1) Backup all the data, mail, preferences, desktop environment tweaks, and other user-level settings. Is this as simple as copying my home directory to a USB stick or external drive? I am coming from a Windows mindset that sees hidden application data repositories scattered all over different directories.... Perhaps I am over-complicating this step?

If you back up your /home directory and /etc, (and /opt if you use that directory to install non-standard versions of things), you should be covered.  All of your settings are in hidden directories within /home/[*your username*].  Next time you upgrade, consider keeping a separate /home partition and this is made even easier.

> 2) Run a tool that identifies my installed software so I can automatically fetch it from the servers for re-installation following a clean install. Is there such a thing? Currently I am manually re-installing such things as GnuCash, Opera, Adobe Reader, etc. I've got to believe someone has written a utility that automates this stuff.

What I do is create a bash command to capture the names of my installed programs (discoverable with the command ```
dpkg -l | grep ii
```) and save that list for fresh installs.  I don't know of a GUI tool that does the same thing, but I imagine there is one somewhere :-)

---

### Post by KIAaze on 2009-11-04
> **Anton32828 said:**
> is there a commonly accepted way of backing up all files, mail, browser bookmarks, and installed-package information so that customizing a fresh install is fairly automated?

I believe the commonly accepted way is to create a separate home partition.

> 
Is there a HowTo or graphical tool that I should know about?

-"Synaptic" for saving the list of installed packages: [http://www.ubuntugeek.com/howto-reinstall-all-of-currently-installed-packages-in-fresh-ubuntu-install.html](http://www.ubuntugeek.com/howto-reinstall-all-of-currently-installed-packages-in-fresh-ubuntu-install.html)
-"GParted" for partitioning.
-How to create a separate home partition: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

There may be others I don't know about.

> 
1) Backup all the data, mail, preferences, desktop environment tweaks, and other user-level settings. Is this as simple as copying my home directory to a USB stick or external drive? I am coming from a Windows mindset that sees hidden application data repositories scattered all over different directories.... Perhaps I am over-complicating this step?

Yes, just backup all your home directory. :)
cf the following links for info on how to change the home partition:
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
(Never done it myself, so I don't know which solution is the best.)
Just replacing the new home directory with the old one should also work of course provided you've kept the same username. (or just rename /home/olduser to /home/newuser)

> 
2) Run a tool that identifies my installed software so I can automatically fetch it from the servers for re-installation following a clean install. Is there such a thing? Currently I am manually re-installing such things as GnuCash, Opera, Adobe Reader, etc. I've got to believe someone has written a utility that automates this stuff.

[https://help.ubuntu.com/community/InstallingSoftware#Backup/Restore%20installed%20packages](https://help.ubuntu.com/community/InstallingSoftware#Backup/Restore%20installed%20packages)

_Warning:_ This will not back up system-wide configuration files (the ones in /etc mostly) or any program not installed via the package management system!

> 
I have found the following HowTo but it is very command-line oriented and seems more oriented towards a complete disk-copy and restore, rather than the upgrade model I've described:

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)


Yes, it's equivalent to a complete disk copy, except that instead of creating a disk image, it creates archives containing all files (system+user).
Backing up /etc that way can be useful if you've modified some files in /etc.
Backing up the GRUB files isn't necessary IMO, unless you've customized it a lot. (Most GNU/Linux distro installations recognize already installed operating systems and add them to the GRUB menu.)

---

### Post by Anton32828 on 2009-11-04
Thanks for the direction. This looks like it will do it for me. I already got familiar with gparted (and the Super Grub Disk live CD) when I formatted my system for the second fresh install. It looks like I will go migrate to a new "home" directory tonight.

---

### Post by LewRockwell on 2009-11-04
we use clonezilla

being able to revert to a reasonably fresh clone is quite simple and does not even require internet connectivity since your clone will be "up to date" already

.

---

