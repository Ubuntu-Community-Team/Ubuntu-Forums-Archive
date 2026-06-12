---
title: "Two Harddrives, two OS's"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by SouthOfHell on 2009-09-30
Hey there, currently i have a 160Gb HD with windows xp pro loaded on.  I ordered a 500Gb harddrive(SATA) and its due to arrive soon, is it possible to load Ubuntu onto the 500Gb and have the grub loader recognize that windows is loaded on the 160Gb HD so that i'm presented with a choice of which OS to boot?

---

### Post by Sir Jasper on 2009-09-30
Hi,

Yes you can do that. Personally, I would set your new drive as the slave.

My regards

[http://www.giveawayoftheday.com/partition-manager-10-0-personal-english/](http://www.giveawayoftheday.com/partition-manager-10-0-personal-english/)

The above link may be of interest. The free offer will be open for the next 12 hours or so. The program is, it says, also a cloning tool and a fixer of common bootload problems as well as a partition manager. However at some 100 MB I have no personal interest - and I do not believe you are especially likely to need it.

---

### Post by bodhi.zazen on 2009-09-30
Yes, it should work just fine. Set the Ubuntu drive as slave, install Ubuntu, and just stay with the defaults.

Make sure you understand the Linux terminology so that you do not install to the wrong HD.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning")

---

### Post by jmundinger on 2009-09-30
I currently have two hard drives with three operating systems on this computer and things seem to be working fine.  As others have suggested, install the second hard drive as a slave to the one that currently is in your computer.

Depending on how you intend to use the new hard drive, you might consider using disk management in XP to partition it before you install Ubuntu.  E.g. if you intend to use some of the space to store files that will be accessed from Windows, the partition has to be formatted in Windows.  You can retrieve files stored in Windows from Ubuntu, but I don't think you can do the reverse.

If you partition the hard drive from Windows, leave the space that you want to commit to Ubuntu as unpartitioned.  When you do the installation, Ubuntu will see both drives and the partitions and free space on each.  You will get to a screen that asks you where to install Ubuntu - it will have a line in the middle that shows the first hard drive (0).  That line has a menu arrow that allows you to toggle to the second hard drive.  Switch to that and then select the option to install Ubuntu to the largest unpartitioned space, i.e. the blank space you left for it when you partitioned the hard drive.

After you install Ubuntu, it will be the default operating system.  You can, however, change the length of the delay and the default by editing the file /boot/grub/menu.lst.

---

### Post by SoftPops on 2009-10-01
I am hoping to be doing much the same at some point over the next couple of months. The Compaq Presario I bought just over a year ago has Vista installed which I want to leave "as is" for the kids and for compatibility with my work (supporting Windows systems of various ages and flavours).
 
I have obtained a new HDD to install which I then intend to load Ubuntu on. I will probably wait till 9.10 is out and loaded on my laptop (purely Ubuntu) before proceeding.
 
Thanks to all for answering a question I hadn't yet asked! :smile:

---

### Post by markbuntu on 2009-10-01
What I did was remove the windows drive, make the new drive the master and install ubuntu on it. Then put the old drive back in as the slave and add a chainloader for windows to the boot/grub/menu.lst like this. 

title        Windoze
root         (hd1)
makeactive
chainloader  +1

If you have SATA drives you can just switch the plugs around.

The windows drive remains untouched if you do it this way. After you make sure that this works remove the windows drive and put it on a shelf in your closet....

---

