---
title: "Dual boot on two different hard disks"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by greatzin on 2011-03-27
Ubuntu newbie,

Is it possible to install win 7 on first hdd and then install Ubuntu 10 on the second hdd and have them install without a problem.

Seems all instructions I have seen is to dual boot on same hdd.

If this is possible is there instruction to follow for a successful dual boot?

Reason for this is that in case of one hdd crashing I still would have access with other hdd.

Thanks for all help.:grin:

greatzin

---

### Post by R.Bucky on 2011-03-27
I suspect that it would be possible to do this if you configured a RAID1 Master Boot Record? Otherwise, if the disk with the boot loader on it were to fail, you would be dead in the water. The better method of having two operating systems would be to install one operating system on one disk and then installing VirtualBox or VMWare and then using the other disk to store your virtual files. I think that you are looking for problems using two disks in the manner in which you express.

---

### Post by ubudog on 2011-03-27
Welcome.

You may want to check here, it has some nice tools.  (for reference)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Something more to the point may be this:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Sorry I couldn't be of any more help.  Hope that gets you started.

---

### Post by oldfred on 2011-03-28
Here is a newer link to one of Herman's pages. He is very detailed so it looks complex but he is just explaining everything.

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

The main issue is you have to use manual partitioning to get the combo box that lets you choose which drive's MBR to install grub's boot loader into. Grub likes to default to sda as that is most common.

Even with all the room of another drive I like to keep system partitions smaller and use /home or /data for all the data. Then I can reinstall the system without worrying about data. Of course /home and some settings in / (root) should be regularly backed up.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

Shared NTFS partition 
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Razorback on 2011-03-28
I am triple booting with three separate drives (XP, Ubuntu and Deban).  I installed each OS on one drive without the others attached.  Then chose one of the Linux drives in my bios (because Grub was installed) as primary boot.  After booting the drive with all attached I ran sudo update-grub and let grub find the other drives.  Then, on the next boot, the other OSs showed up in the Grub menu allowing me to select which one.

---

