---
title: "Installing ubuntu"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by jste on 2011-01-06
Hi,

I would like to install ubuntu 10.04 LTS on my netbook which has already windows xp and I would like to keep this aswell. What size of partition do have have to take for ubuntu? I have a harddisk of 160 GB.
And can I cancel this partition if i decide later on to remove Ubuntu agai

thanks
cal

---

### Post by oldfred on 2011-01-06
Welcome to the forums.

Yes you can reformat partitions if you want to uninstall Ubuntu. If you have tried the liveCD to make sure it works with your hardware, and you still are not sure you can just install wubi. Wubi is a version that just runs as a file inside the windows NTFS partition and uses the windows boot loader. It is not a 'good' as a full install as it is using NTFS and is not a true dual boot but makes for a better test of Ubuntu than liveCD without issues of partitioning.

I prefer a full install. And in your case you should create another NTFS partition as shared for data you may want in both systems. I have my Firefox & Thunderbird profiles in the shared so I have the same email & bookmarks in both systems. While Ubuntu will read & write directly into your windows install, it shows all the hidden files that windows protects you from and then it is easier to accidentally delete or move something you should not. I suggest making the windows install read only from Ubuntu.

Separately use gparted to shrink XP and then reboot XP, & run chkdsk. Besure to leave 20-30% free space in the NTFS partition as windows likes lots of room or it slows down dramatically. 

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by hansolo4949 on 2011-01-06
I recommend a partition of at least 30-40 GB if you are going to be downloading a TON of stuff to use on Ubuntu. Ubuntu only takes up about 2-5 GB of space after you install it, so you have plenty of breathing room. If you are only going to use it for browsing, and maybe download a few files, you can get away with 15-20 GB just fine. If you want to remove Ubuntu, you can, but you will have to have a recovery cd, and know how to get to windows's partition manager. Installing Ubuntu is VERY simple, you just answer a few questions, adjust a slider to tell Ubuntu how much space it can take, and presto! you're in business.

Hope that helps!

hansolo4949

---

