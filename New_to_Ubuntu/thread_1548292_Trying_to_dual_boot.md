---
title: "Trying to dual boot"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by Planetes on 2010-08-08
I've been at this way too long now after exhausting all of my own ideas so i come to you now.

My current HDD status is in two perspectives:

Windows perspective - 3 standard windows partitions + 1 ext4 part + 1 swap part(that i made with gparted)

Linux perspective - 3 standard windows parts + 1 unallocated part

I believe this is because for whatever reason ubuntu doesn't enjoy having more than four primary partitions. Because of this i did the actual creation of the latter two partitions in windows and then formatted them with the ubuntu disk utility off of the live disc.

When i try to install however it just lumps those two partitions into one "unallocated space" even though the disc utilities(gparted and the like) recognize the ext4 and swap while in live disc operations.

**Thanks for any posts and if i don't respond for a while, keep going i've probobly just fallen asleep :) ...finally

---

### Post by jtarin on 2010-08-08
Impossible for Windows to see Linux partitions. Windows sees as unallocated space.Linux can see Windows partitions.You might have 3 primary partitions but I'll bet your Linux and swap are in an extended partition.You can only have 4 primary partitions on your disk it doesn't matter what the operating system is.
Boot your Ubuntu Live CD/DVD and when at the desktop open a terminal and issue the command ```
fdisk -l
```post the results. In addition, where did you install Grub? MBR or /boot of your Linux install?

[Some info]("http://www.faqs.org/docs/Linux-mini/Partition.html")

---

### Post by mapes12 on 2010-08-08
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by Planetes on 2010-08-08
I don't think i installed grub, i'm just running off the live disc. And i don't seem to be getting any output from that command, just fdisk (util-linux-ng 2.17.2)

---

### Post by cascade9 on 2010-08-08
> **jtarin said:**
> Impossible for Windows to see Linux partitions. Windows sees as unallocated space.[]("http://www.faqs.org/docs/Linux-mini/Partition.html")

Stock, windows wont see linux partitions. But you can make at some version of windows see EXt2/EXT3. I've got XP to see EXT3 filesystems before, and I'm pretty sure this was the tool is used- 

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Planetes on 2010-08-08
:( I thought i had it that time. 

So. story time, I decided to do this after having a full-buntu install  for a few months because i am going to be going to school here soon in  the fall and i thought hmm maybe i  should have it(windows) available  just in case. Though i would still  predominantly use ubuntu. I know  that ubuntu and windows don't play well together or at least their boot  loaders don't so i decided to do a full install of windows 7 via my  restore disc. After doing that each of the four times i have done that  tonight/this morning my HDD looks like this:

100mb (system) partition / 15GB (system recovery) partition / 100GB (C drive  partition) / 350GB (D drive)

the system recovery and D: are unused after a fresh install...hope some  of this helps you help me :)

---

### Post by john newbuntu on 2010-08-08
I am taking a wild guess that those 4 are primary partitions.  Anyway, I'd suggest following the procedure in this post (Method 1) to delete the D: drive/volume.  
[http://www.sevenforums.com/tutorials/2668-partition-volume-delete.html](http://www.sevenforums.com/tutorials/2668-partition-volume-delete.html)

Then boot from an Ubuntu liveCD and during the partitioning step, choose "install them side by side..." which will give it the entire 350GB of free space (the one that you just deleted).  Complete the installation making sure that the bootloader (GRUB2) is installed on to the MBR of your only drive /dev/sda.  Click on the "Advanced.." option when you get to this screen.  Check only sda NOT sda1 or any of the other partitions.
[http://www.psychocats.net/ubuntu/images/installinglucid10.png](http://www.psychocats.net/ubuntu/images/installinglucid10.png)
Complete the install.


Here are a few points to ponder before the install:
Do you need to create more partitions for Ubuntu(like say one for /home or perhaps an extra NTFS partition for data etc).  I would suggest to do so since you will retain the data in /home during upgrades and will have more data that can be shared with another OS.

Should you decide to go this route, prior to installation, run gparted from the liveCD and create an "Extended partition" in that 350GB free space.  Within this extended partition, create your swap(2GB), /(30GB), /home (20GB) logical partitions.  The sizes I have given are only examples, you can adjust them according to your needs.  The idea is to optimize space and use the remaining 300GB for future needs (of any OS). For example, you could create an NTFS partition to hold your data and share it with Windows.
For help with gparted:[ http://gparted.sourceforge.net/larry/generalities/gparted.htm]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

After you create these partitions, install Ubuntu and choose the option to "specify partitions manually".  Assign partitions appropriately to swap, /, /home.  Continue with the install.  Post back if you need more help.

---

### Post by jtarin on 2010-08-08
> **cascade9 said:**
> Stock, windows wont see linux partitions. But you can make at some version of windows see EXt2/EXT3. I've got XP to see EXT3 filesystems before, and I'm pretty sure this was the tool is used- 

[http://www.fs-driver.org/](http://www.fs-driver.org/)
Filesystems yes....partitions schemes...no.

---

### Post by Planetes on 2010-08-08
John could you or somebody else talk a little more about putting my home folder in a seperate partition. What would the purpose of this be and what are the benefits of it. I'll of course do some research on my end as well.

Thanks.

---

### Post by jtarin on 2010-08-08
The purpose is to preserve all your personal configuration files in the event you have to reinstall or some other event that would cause you tolose all your configs if they were on the same partition as your system files. I recently was running Ubuntu...decided to try Kubuntu....then came back to Ubuntu. All the time my configs were the same....with the exception of additional ones by KDE in my home folder, which I cleaned up after reinstalling. This way if you have a software problem with an application you installed or just want to refresh your install your ready to go. You can also keep in mind this scheme for other directories....such as /var where your downloaded packages are kept. People on a slow connection don't like to have to download all those extra packages they did after initial install.Think of the concept.It's an elegant solution and can develop good habits when we forget to backup and disaster stikes. It will take some experience to know what space requirements you need as an individual.

---

### Post by Planetes on 2010-08-08
Okay that sounds like an interesting idea. 

Thank you for all your help.

---

