---
title: "2nd hard drive on Dual boot hard drive"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by buffaloeb23 on 2011-02-13
I am new to Linux. I am running ver 10.10 on a dual boot system that has 2 hard drives. The 2nd hard drive was originally formatted in Windows XP. This machine is connected to a network with other Linux machines. There are folders on that 2nd hard drive that I want to share with the other machines. I have used samba to set those folders to be shared. However when I try to access them from the other machines I get an error message that says "Windows Share can not be mounted"
I am debating between 2 courses of action. Do I reformat the second hard drive under Linux and just make it a Linux drive? or is there a simpler way to get those folders available to the other Linux machines. Thanks.

---

### Post by Mark Phelps on 2011-02-14
Unless there is some reason for retaining MS Windows filesystem compatibility, since your network is Linux PCs, I would just reformat the drive with a Linux filesystem.  Less problems in the long run that way.

---

### Post by oldfred on 2011-02-14
I used to have XP on my portable & dual boot desktop and when traveling wanted to copy much of my desktop to the portable. Samba seemed to always give issues, mostly caused by windows, firewall and virus check software updates. 

I realized I was in Ubuntu most of the time and converted the laptop to Ubuntu also and now use NFS to copy files. It requires some initial set up but I saved commands to a couple of bash files and just have to rerun them, after  I have done a new install and it still works.

HOWTO: NFS Server/Client if no windows 
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

