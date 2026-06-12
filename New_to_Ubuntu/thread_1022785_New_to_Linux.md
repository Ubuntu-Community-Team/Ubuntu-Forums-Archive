---
title: "New to Linux"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by cholmes on 2008-12-27
Hi, as I said in the title I am new to Linux. If someone could help me understand how to find programs and download them. I can get as far as the repository page but can't seem to find anything specific. Namely wine or wicd. I have installed Ubuntu in a different partition with the 30 GB option. Not sure I understand that either. With the live CD it gave the option of installation size from 4-30 GB, what is the difference? I assumed software but now I am not so sure. Is there a web page where I can get step by step? So far the few days I have used it it appears to be a good OS, not seemingly a whole lot off from Windows, just faster.

---

### Post by gettinoriginal on 2008-12-27
> **cholmes said:**
> Hi, as I said in the title I am new to Linux. If someone could help me understand how to find programs and download them. I can get as far as the repository page but can't seem to find anything specific. Namely wine or wicd. I have installed Ubuntu in a different partition with the 30 GB option. Not sure I understand that either. With the live CD it gave the option of installation size from 4-30 GB, what is the difference? I assumed software but now I am not so sure. Is there a web page where I can get step by step? So far the few days I have used it it appears to be a good OS, not seemingly a whole lot off from Windows, just faster.

Welcome to Ubuntu :popcorn:
First, the reason for the 4-30GB is only the installation of the OS, minimum is 4GB to run ubuntu.  Second, go to System > Administration > Synaptic Package Manager (It will ask for your password)
Once Synaptic is open, go to the search on top and enter the program/application you are looking for, check it for installation.  It may bring up a window showing that more will be installed with it, these are just dependencies required to run that application.  Go to Apply and once it is installed, it will show up in your main menu.  And yes, wine is available.  Being new, the following link is very helpful, check it out and bookmark it:
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by Coder543 on 2008-12-27
He suggested using the Synaptic Package Manager. But, even though it is better, it is harder to use. I would recommend you go to Applications then click on Add/Remove Software...

At the top there is a box you should click on, then change it to say "All Available Applications"


Now to install stuff, just find it, then check the box, then click apply. You may have to enter a password. It should then install itself.

The "wine" gettinoriginal mentioned is a program that lets you run some windows applications in Ubuntu.

---

### Post by Bucky Ball on 2008-12-27
You might find this link interesting:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Before installing wine, I would ask you what it is exactly you are wanting to run from the windoze side and have you researched to see if there are appropriate open-source 'drop-in' replacements. The Ubuntu packages might take a slightly different approach but achieve the same thing as their windoze counterparts, and probably a tad faster they are running natively and not through wine. You soon get the hang of it.

This is a good place to start:

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

For some gamers (and others), of course, wine seems to be essential.

---

### Post by cholmes on 2008-12-27
OK I will give these suggestions a try, I am sure I will be fine when I learn the way to get places. Also I have Linux installed as a dual boot, I have partitioned my HDD but can't seem to find a way to look at the HDD and see the partitions. Is there a way to do that? Can I partition the partion that Linux is on with Linux? In other words create a Part. for data?

---

### Post by Bucky Ball on 2008-12-27
Try:

System->Administration->Synaptics Package Manager

... and do a search for 'gparted'. Install that and you should be able to do the partitioning you need with that. In Synaptics again, do a search for 'ntfs-3g'. Install that and it will allow you to see your NTFS drives, which are not native to Linux (they are a creation of Microsoft). I am presuming the windoze partitions are NTFS? Gparted should let you know.

Incidentally, gparted should appear under System->Administration->Partition Editor

---

