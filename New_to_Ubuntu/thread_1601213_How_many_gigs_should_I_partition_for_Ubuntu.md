---
title: "How many gigs should I partition for Ubuntu?"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by naveed.akter on 2010-10-19
Going to install 10.10

I have a Tera-byte.

Is 150 Gig enough? 

Currently for Windows 7 I've only used about 131 Gigs.

Thanks again.

---

### Post by Cuddles McKitten on 2010-10-19
150 GB should be plenty.  After install it should probably be about 8 GB, giving you about 140 GB for data.

Edit: Also, you can increase/decrease your partition's size later if needed.  gparted will let you do that relatively easily (but be sure to back up your data before doing that, since it can be dangerous).

---

### Post by AoSteve on 2010-10-19
I've personally never went beyond 40GB with a ubuntu install.  I do have a 1TB drive just for storage though...

---

### Post by sandman6471 on 2010-10-19
I agree with cuddles. I have a 160gb drive, it shows 128gb free. I have all the softeware I use loaded plus themes and other things. So you should have no problems with 150gb allocated for Unbuntu.

Linux is Great.....
Take Care Everyone.....

---

### Post by bigsmitty64 on 2010-10-19
150 gig should be more than sufficient!

---

### Post by oldfred on 2010-10-19
If you have lots of room I like to make several / (root) partitions and have a current install and another for testing the next install.

I also like to have a shared NTFS partition for any data that you may want whether booted in windows or Ubuntu. I have firefox & thunderbird profiles in my NTFS shared partition so bookmarks & email are the same.

If data is not in root you do not need much space. Standard install is just over 3GB, I have installed lots of programs and have used about 6GB. Since all my data is elsewhere my /home is only 1GB, but if you keep data in /home you should make it as large as you can.

1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical (or size of RAM memory if want to hibernate)

No separate /boot unless old computer, server, encrypted or btrfs system partition.
If lots of room add another root partition for testing/running next version. (I use 3 in rotation)

If you create partitions in advance with gparted then you use the manual or advanced install in Ubuntu and choose which partition is which & what format to use.

[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by naveed.akter on 2010-10-20
I have no idea what you just said. Computer-Illiterate Speak please :D

EDIT: And thanks guys! I'm really liking the active community. Really feels good haha!

> **oldfred said:**
> If you have lots of room I like to make several / (root) partitions and have a current install and another for testing the next install.

I also like to have a shared NTFS partition for any data that you may want whether booted in windows or Ubuntu. I have firefox & thunderbird profiles in my NTFS shared partition so bookmarks & email are the same.

If data is not in root you do not need much space. Standard install is just over 3GB, I have installed lots of programs and have used about 6GB. Since all my data is elsewhere my /home is only 1GB, but if you keep data in /home you should make it as large as you can.

1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical (or size of RAM memory if want to hibernate)

No separate /boot unless old computer, server, encrypted or btrfs system partition.
If lots of room add another root partition for testing/running next version. (I use 3 in rotation)

If you create partitions in advance with gparted then you use the manual or advanced install in Ubuntu and choose which partition is which & what format to use.

[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by beew on 2010-10-20
> **Cuddles McKitten said:**
> 150 GB should be plenty.  After install it should probably be about 8 GB, giving you about 140 GB for data.

Edit: Also, you can increase/decrease your partition's size later if needed.  gparted will let you do that relatively easily (but be sure to back up your data before doing that, since it can be dangerous).

8GB after install? I have a installation of 10.10 along with a whole bunch of craps that I don't even use as a demo. It has all kind of multimedia and graphic stuffs and even some KDE apps (along with the dependencies) it is 2.8G. I install this in a 4G external drive and it is more complete than the desktop of many people I know. (Ok, I cheated by cleaning it up with bleachbit, but 2.8G!)

My working system has an installation of about 6G,not counting data. That includes a lot of redundancies(like two browsers and several media players) because I want to try out and compare different softwares with similar functionalities.

My problem is that I don't know what to do with my disk space. For a single installation 60G is more than enough,--I don't keep pictures or videos,--I delete them after I watch them. I have my music and ebooks on an external drive. I would be lost if I have a 250G hd (how many distro do I want to multi boot in order to use up the space??) 1 Tb is insane.

---

### Post by lilbmorgan on 2010-12-28
When I used Wubi it only needed 17gb to install.

---

