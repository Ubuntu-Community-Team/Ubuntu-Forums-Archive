---
title: "I know you are tired of this question!"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by m1schuld on 2010-01-23
I'm using Windows Vista but would like a dual boot screen with ubuntu. I know I need to back up everything which I have done. Why is there so much concern with losing all my files? If I download ubuntu and burn it to a cd and then attempt to install it, how do ensure that I can still access windows? Where is the screen that asks, "Would you like to keep Windows and have Ubuntu as well?" Forgive my ignorance. I'm not fluent on partitioning and want to install ubuntu but I do not want to risk losing all of my files and having to restore the entire system. How can I avoid this? I'm running windows 7 on a partition, can I not install ubuntu on the remaining harddrive space? In other words, must I create a new partition? Can I trust that when I do create a new partition, it will be created over an empty portion of my hard drive? 

I am extremely grateful to anyone who has made it this far into my ramble! Thank you for your help!

---

### Post by sandyd on 2010-01-23
> **m1schuld said:**
> I'm using Windows Vista but would like a dual boot screen with ubuntu. I know I need to back up everything which I have done. Why is there so much concern with losing all my files? If I download ubuntu and burn it to a cd and then attempt to install it, how do ensure that I can still access windows? Where is the screen that asks, "Would you like to keep Windows and have Ubuntu as well?" Forgive my ignorance. I'm not fluent on partitioning and want to install ubuntu but I do not want to risk losing all of my files and having to restore the entire system. How can I avoid this? I'm running windows 7 on a partition, can I not install ubuntu on the remaining harddrive space? In other words, must I create a new partition? Can I trust that when I do create a new partition, it will be created over an empty portion of my hard drive? 

I am extremely grateful to anyone who has made it this far into my ramble! Thank you for your help!
from vista onwards, all versions of windows will freak out if you resize its partiton using ubuntu.

However, windows itself has a partitoning tool.

Go to Control Panel -> Administrative Tools -> Computer Management -> Disk Management (or something similar to disk management)

resize ONE of the partitions (remember, you can only create free space to the right of the partition) and leave it as free space (un partitoned)

boot up ubuntu from cd and choose to install ubuntu.
when you get to the partitioning stage of the installer, choose "use largest block of free space" (or something close to this).
Continue the installation and youll be fine.

---

### Post by Bartender on 2010-01-23
Hey, until you've done it a few times, it's scary!  My best advice is practice on a spare PC.  

You'll get to partitioning at Step 5 on a LiveCD.  The Ubuntu partitioner will show you what it sees and give you a few choices.  One of those will be to install Ubuntu alongside Windows.  Unless it sees four primary partitions, which is not uncommon.  

The basic idea is simple enough, but the devil's in the details and it's fairly easy for someone who hasn't practiced a few times to screw it up.  Add all the variables (RAID, flaky hardware, power surge, a million different combinations of parts) and maybe you'll see why everyone says to back up.  Plus there's always Murphy's Law waiting to strike.  

If you've got broadband, watch a few videos of people installing Ubuntu.  That might help.

---

### Post by Zimmer on 2010-01-23
Have a good read first!
Try the live cd (you do not INSTALL it, it will run like the old games used to direct from the CD drive.)
If you really like what you see ... then read 
[http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu-2/](http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu-2/)

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

and if you are still keen to dual boot, then read more

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

The steps, simplified, that I took to dual boot Vista and Ubuntu 9.04 on my new laptop was as follows :
Defrag the hard drive. 
Make unallocated space on the hard drive using Vista ...

Use the Ubuntu Live CD to partition the unallocated space how I wanted it for an Ubuntu install.

Used the Ubuntu Live CD to install, making sure to install Ubuntu root (/) to the partition I had created and not on the Vista partition(s) 
When prompted to install GRUB I installed it to that same Ubuntu partition, NOT THE MBR..
When the computer was rebooted it went to Vista.
I downloaded and installed EasyBCD and added the relevant entry for the Ubuntu install.
On reboot that gives me a choice of Vista or Ubuntu.
The Ubuntu choice sends me to the GRUB menu and I select the top entry from there...

There are other ways... this method has been working for me since Sept 2008.
Bear in mind I had already been using Ubuntu exclusively since Oct 2005 before I bought a new laptop and decided to keep Vista and dual boot. (need Line6 software on Windows if anyone was curious as to why).

Examine your motives for using Ubuntu and select the best method for you..(Dual boot or Wubi or just Live CD)

Oh, and you did create your restore disks for Vista, yes? or you have a Vista Install CD?  as the post above says, be prepared....

---

### Post by PenguinInside on 2010-01-24
1. Always have a backup of your data files from Windows (\User directory)

2. Download VirtualBox from [http://www.virtualbox.org/](http://www.virtualbox.org/)

Install Ubuntu a couple of times inside VirtualBox a couple of times.

Once you know what you're dealing with, I think you'll be more at ease doing the real installation.

If you have a fast enough computer, you may be satisfied with just running Ubuntu inside VirtualBox.

---

### Post by OrangeCrate on 2010-01-24
> **m1schuld said:**
> I'm using Windows Vista but would like a dual boot screen with ubuntu. I know I need to back up everything which I have done. Why is there so much concern with losing all my files? If I download ubuntu and burn it to a cd and then attempt to install it, how do ensure that I can still access windows? Where is the screen that asks, "Would you like to keep Windows and have Ubuntu as well?" Forgive my ignorance. I'm not fluent on partitioning and want to install ubuntu but I do not want to risk losing all of my files and having to restore the entire system. How can I avoid this? I'm running windows 7 on a partition, can I not install ubuntu on the remaining harddrive space? In other words, must I create a new partition? Can I trust that when I do create a new partition, it will be created over an empty portion of my hard drive? 

I am extremely grateful to anyone who has made it this far into my ramble! Thank you for your help!

Here's a "hard copy" of the instructions Carlee posted earlier:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

(This is how I set up dual booting, both on my computers, and others.)

---

### Post by capitalfear on 2010-01-24
did he say virtualbox? virtual box...i think he said virtual box....all hail the king of ubuntu and windows on the same computer!!!!!!!!!!!!thats what i was gonna suggest

---

