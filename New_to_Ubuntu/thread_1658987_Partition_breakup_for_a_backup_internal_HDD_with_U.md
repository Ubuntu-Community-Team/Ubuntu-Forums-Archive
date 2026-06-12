---
title: "Partition breakup for a backup internal HDD with Ubuntu"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by beopen on 2011-01-03
Hi all ,
Can anyone guide me on the disk allocation for ubuntu and  data on a backup internal HDD?

My system Config 

Intel 2.53 Core 2 Duo,2 GB RAM 160 GB existing HDD , New 500 GB backup Internal HDD,
Windows XP ( in exisiting drive).

My requirement

I plan to use 500 GB ( 465 GB free space only technically available) drive for a pure backup option  with a monthly/bi-monthly backup operation of my files.

My queries
1. Which version of Ubuntu should i use for stability purposes? 
2.What is the disk allocation i should make for installing any version of Ubuntu OS in new drive?
3. How much allocation for a swap partition?
4.What is the file system i should use in the remaining space in order to access data by both Windows and Ubuntu in this new drive?

Regards
beopen

---

### Post by Verbeck on 2011-01-03
1. both 10.04 and 10.10 are pretty stable. the main differents is one has 'long term support' (3 years) while the other does not (18  months)

2. about 6-10 gb /

3. same as RAM - 2gb

4. ntfs

---

### Post by scott_tiger on 2011-01-03
Give some 15-20 GB of space for any ubuntu versions to install. Strictly ubuntu even can be installed in 2 GB (not recomeded).
 
If u occasionally use/do not have idea to setup ubuntu , as u have xp in your drive install insde Windows XP as an application(thoung i don't suggest that).
 
U can install ubuntu in the same drive as xp,by inserting ubuntu cd and installing the ubuntu side by side in same xp drive.Here your xp and ubuntu boot from same partition of the drive.Ubuntu automatically takes some 12-13 GB of the space in side by side installation in the same drive , you need not explicity give the size and space of installion(both xp and ubuntu will be installed separately but in same drive genereally C: drive).
 
Chose LTS(long term service) versions of ubuntu eg 10.04(I don't have idea abt 10.10) as Canonical provide 3 yr services for LTS release.
 
give ext4 file syatem if u r instaling 10.04 or above or ext3/ext4 if installing 9.10 or below versions.
 
swap space will be automatically taken by ubuntu or several options will be prompted to choose from regarding swap space.select the  one suitable to u.
 
Visit following url:
 
[http://www.techhamlet.com/2010/05/how-to-install-ubuntu-10-04/](http://www.techhamlet.com/2010/05/how-to-install-ubuntu-10-04/)
 [http://www.liberiangeek.net/2010/03/how-to-install-ubuntu-from-a-bootable-usb-drive/](http://www.liberiangeek.net/2010/03/how-to-install-ubuntu-from-a-bootable-usb-drive/)

---

### Post by germanix on 2011-01-03
I will go with the advice from "Verbeck" above. Cant do better than that. Have fun.

---

### Post by seawolf167 on 2011-01-03
> **Verbeck said:**
> 1. both 10.04 and 10.10 are pretty stable. the main differents is one is has 'long term support' (3 years) while the other does not (18  months)

2. about 6-10 gb /

3. same as RAM - 2gb

4. ntfs

+1 for this, note that currently a fresh Ubuntu install uses ~4GB of space, so 10GB should be more than enough for the root partition, though you may want to make a home partition larger/smaller depending what (if anything) you will store on it

---

### Post by oldfred on 2011-01-03
If you want to keep the windows boot loader on your old drive (recommended), be sure to use manual install and then choose to install grub to the new drive. Then in BIOS set that drive as the boot drive. If you ever have issues you can select to boot sda and still get into your windows install. I like to keep each drive with a separate operating system and its boot loader so it can be used without any other drive.

My suggestions, not really that much different from Verbeck's, but perhaps more options, if interested.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

---

