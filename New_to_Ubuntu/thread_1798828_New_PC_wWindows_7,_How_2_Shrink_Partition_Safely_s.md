---
title: "New PC w/Windows 7, How 2 Shrink Partition Safely so Can Install Kubuntu 11.4?"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by GregA on 2011-07-06
Just setup a new Intel based Lenovo desktop running Win 7 on a 500 gb drive - - a fairly generic budget system.

I'd like to install Kubuntu 11.4 alongside Win 7 (dual boot).  

 ? What are the basic steps to accomplish this, retaining Win 7?

I've read it's best to shrink Windows 7 using the provided partioning tool within Windows.

 ? What is the smallest size I can safely shrink windows to? (no new software, files beyond OEM cruft)

 ? Will the Kubuntu installer see the new unallocated hd space and allow me to setup a ext3 or 4 linux partition, and then proceed to install?

 ? Lastly, I'd prefer for Grub to choose Kubuntu as the default OS to load upon startup, but allow the user to select Windows if needed.

I've been searching the forums (can't find the wiki) for this basic setup situation (the forums have plenty of threads on more complex install scenarios (multiple drives, etc.)

Thanks much.

---

### Post by Derek Karpinski on 2011-07-06
-First, defrag your hard drive multiple times.  That will help gain more space when shrinking.  
 
-Sometimes windows puts 'non-movable' files and you can't shrink even after defragging.  Then you'll have to run Perfect Disk that will defrag on boot before windows loads so it can move those files.  You may have to do this a few times as well. [http://www.raxco.com/products/home-perfectdisk12-home-premium/learn-more](http://www.raxco.com/products/home-perfectdisk12-home-premium/learn-more)
 
-Then shrink using the windows disk management tool.  I have vista installed in a comfortable 50GB.  I left room for some big CAD/CAM applications, and enough for windows updates.  I'm using about 25-30 at this point.
 
-IMPORTANT........restart and boot into windows a few times after shrinking.......I don't know exactly why.  Just have read people having problems if they didn't do this.  Can't hurt right?
 
-So, at this point, you'll have an unallocated space on your HD, run the (K)ubuntu install disk, and choose 'Do something else' instead of install along side Windows, or use whole disk.
 
-You can follow this guide for general info on paritioning space for linux. [http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
Make sure that you don't overwrite your windows partition when manually defining partitions.  Only work with the 'free space'.  You should be able to see where windows is by the NTFS file system flag.
 
If you can't shrink as much as you want using Perfect disk, I'd do a fresh install of windows, and reshrink.

---

### Post by oldfred on 2011-07-06
Just to add to the good advice from Derek Karpinski.

Windows likes to have 30% free for NTFS to work well, so do not shrink too much. If dual booting it is often best to create another NTFS D: drive for data and that is a shared drive that both windows and Ubuntu can use for data. Only mount your windows partition read-only if you mount it at all, to avoid windows issues. 

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Different versions have slightly different install screens but the process is the same.
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by GregA on 2011-07-08
Thanks Derek and OldFred - - your posts helped me to sort out how to successfully install Kubuntu. 

Basically,  I did the following:
1.   Changed BIOS settings so the PC will boot from CD/DVD or Flash drives before booting from the hard drive.
2.   Tested  the Live KDE version of Ubuntu 11.4
3.   Used the Windows 7 application in their control panel, to shrink the   windows partition.  Did not create any new partitions using the windows tool - - only shrunk the C drive leaving 80 gb for windows.  Tested windows still boots.
4.   Used the Kubuntu Live/Install disk to partition my ex ntfs drive into 4 partitions (for Kubuntu, Home, Swap and TBD)
5.   Installed Kubuntu.  Only 1 glitch, it took 3 or 4 attempts to successfully create users.  Kept getting error "you are required to change password immediately - root enforced."  Then, when I tried to comply, the system  would not recognize my input (new user pw), and would freeze up.   Finally got around that by deleting the users, re-adding,and on 4th attempt, I could finally input the required new password.  Since that hurdle was overcome, the remainder of the install went perfect.

Now, Kubuntu is running smoothly on my Lenovo H410 - - a very Linux friendly system.

Now to try and remember the in & outs of KDE (I've been a Gnome user for past 3-4 years), , ,  but it is slowly coming back to me.

Thanks again.

---

