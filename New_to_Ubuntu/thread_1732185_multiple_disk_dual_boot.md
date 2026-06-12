---
title: "multiple disk dual boot"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by 2spurs on 2011-04-17
Hi
Building a new computer & I want Ubuntu on it.  I’m reusing 2 sata drives from my old computer + a new drive.  
 Drive 1 - 74GB Raptor,  
drive 2  - 160 GB Sata disk.  
Drive 3 -  WD 1 TB Caviar black.  
New computer is AMD quad core,  8 GB memory.

I want to dual boot Win 7, and Ubuntu 11.04. Drive 1 & 2 drive will each be a separate OS.  Drive 3 will be a shared data storage.

 My thoughts go to using drive 1, the Win 7,  with 2GB boot partation,  50 GB for Win 7.
The 160 GB partationed as,  15GB as /,   4gb swap, 20gb extended.  70 gb for Windows backup area
Drive 3 as 2 - 500gb partations.  Formatted as NTFS

Question 1)	Is this sizing of the partations appropiate?  I feel comfortable with the Windows part,  but not with the Ubuntu.

Question 2) what do I make the 2gb partation on the first drive?  Do I leave it unallocated when I load Windows?  My understanding is to load Windows then Ubuntu – in that order.

Question 3) How do I point Ubuntu to drive 3 to hold user data?  Do I need to have a /user partation on drive 2 and just copy data to drive 3 once a week?
Thanks in advance for any help on this.

---

### Post by scott-ian on 2011-04-17
That is much more swap space than you need.  Also, what is in the extended partition?  You can either use a symbolic link or mount the drive as your home folder.

---

### Post by wolfen69 on 2011-04-18
If you are using separate drives for each OS, why not just let the OS's use the whole drive? And it doesn't matter what OS you install first with separate drives, but as a general rule it's good to install windows first. 4gb of swap is way too much when you have 8gb of ram to work with. I would bet you'll never use all 8gb and would maybe want no more than 1.5-2gb of swap. I have 1gb of swap and have never used *any* that I can recall.

And btw, you don't need to make a boot partition for windows, as that is done automatically during install.

---

### Post by spur on 2011-04-18
Make sure that the boot partition and Grub are on the drive your bios says is the boot device. I found the auto install installed it on the wrong drive and then had to go and do it all over again ensuring the partitions had enough space and in the right places. If you want to make a  partition on a different drive connect with your installed Ubuntu, when installing do a manual partition not the auto one, and create the partition were you want it and make the mount point what you want. You get a choice of ones that will work. The Ubuntu will do the rest for you. I always tick the little box to ensure all the partitions I have planned will be formatted as well, even if it doesn't appear they need it.
Good idea to check you hard drives for faults first if you can and do the disk check available for the install disk. Just reduces the chances of an 'unexplainable' event.

---

### Post by Mark Phelps on 2011-04-18
From personal experience, have found what tends to cause the least trouble with using multiple OSs with multiple drives, is to install Linux OSs to one drive, Windows OSs to the other drive -- and have only the install target drive connected during the install.

That prevents accidentally overwriting MBRs and boot folders.

It's a simple matter, once done, to boot from the Ubuntu drive and regenerate the GRUB2 menu to include the other OSs.

---

### Post by 2spurs on 2011-04-18
Points taken.  I need to make the drive 2 pure Ubuntu.  The MS 7 backup space should be on drive 3.

I am fooling around with Ubuntu 10.10 while I wait for 11.04 to be released.  On a 1 TB drive I selected auto install.  It partationed a 23 gb swap space, a 23 gb extended space,  and 900 gb boot partation!   In my limited Ubuntu experence this seems to be a Bad design.  

How big should a / partation be on a 160 GB drive?   If I can make the partations reasonably small,  the disk performance goes up and management (window experence) is better.  

Question;  the boot partation that will decide to go Windows or Ubuntu,  should be located where?  the first partation of the Win drive?  the first partation of the Ubuntu drive?  

Doing the install of each OS on a drive that is the Only drive on the system is a good idea.  But - when and how do I then tell the system to dual boot?

---

### Post by oldfred on 2011-04-19
If you do not disconnect drives as Mark Phelps suggests, then you have to be careful where everything is installed. It can be done but you have to partition in advance or use manual partitioning that is part of the Ubuntu install.

I prefer small system partitions for both windows & Ubuntu & having data on other partitions. But small is relative. Windows needs more than Ubuntu.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Herman has lots of detail, not as complex as it looks:
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

Other than possibly having /home separate, you do not need to have any other system partitions separate for a standard desktop. Servers, RAID, LVM or very old systems that cannot boot beyond 137GB may need /boot.
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

the boot partition does not determain which system boots, but the MBR. BIOS boots to the MBR of which ever drive you choose. Best to have windows boot loader in the MBR of the windows drive and grub2's boot loader in the MBR of the Ubuntu drive and choose that drive to boot as grub will let you boot windows, but windows will not let you boot Ubuntu.

---

