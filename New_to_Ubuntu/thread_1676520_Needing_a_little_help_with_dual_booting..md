---
title: "Needing a little help with dual booting."
date: 2011-01-27
forum: New to Ubuntu
---

### Post by L Campbell on 2011-01-27
I would like to dual boot Ubuntu with Win XP by using 2 hard drives, as opposed to having Ubuntu in a partition on my Windows hard drive.

My searchings for a 'how-to' for this brings up instructions for doing it with Wubi but not with 2 separate hard drives and I would appreciate if you can share information, or a link, that will help me with this.

TIA

---

### Post by TeoBigusGeekus on 2011-01-27
There's nothing difficult to it-it's exactly the same as installing ubuntu on a windows hard drive, only easier.
Just boot up with your ubuntu cd and follow the steps.
The only thing you have to be careful about is the partitioning.
Once the installer reaches the partitioning stage, choose Manual Partitioning, select your empty drive (ie. not the drive with windows on it), create the necessary partitions (/, /home, swap, etc.) and you are ready.
Just remember to install grub on your boot disk, ie. the disk from which your system boots from (look for it in your bios settings).
Good luck!

---

### Post by mharrison on 2011-01-27
I've done this myself before.

What I did was have Windows installed first on whatever drive I wanted it on.

After it was installed and booted to it once just to be sure I popped in my Ubuntu disk and ran the installer.

When it came time to partition I setup my Ubuntu partitions on the other drive.  I also made sure to install the bootloader on the drive containing Windows so that way I didn't have to mess with my hard drive boot order in my BIOS.

HTH



Edit:
TeoBigusGeekus is correct.  I forgot that not everyone uses my computer and knows which drive is the primary drive in the bios :P

---

### Post by oldfred on 2011-01-27
A link to lots of detail if you want:

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

Issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.


GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by L Campbell on 2011-01-30
> **oldfred said:**
> A link to lots of detail if you want:

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

Issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.


GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Thanks very much.  This looks like the 'Mother Lode'and, although I haven't made a move yet, I'm REALLY enjoying reading through everything.

Kind regards.

---

