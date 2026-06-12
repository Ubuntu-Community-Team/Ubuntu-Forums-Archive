---
title: "triple booting and partitioning question"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by ave2 on 2009-11-01
I want to set up a triple boot with Windows xp, Ubuntu 9.10 and then have a third that I can use to try some other o/s- such as linux mint, kabuntu or ultimate edition. 
now refering to the following guide:

[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

it states:

> A hard disk can only have 4 primary partitions.

However you can create a logical partition instead. This allows another 2 extended partitions to be created within it.

now I also read that ubuntu needs 3 partitions


> 
   1.Root partition - where Ubuntu is installed. This should be at least 4GB.
   2.Home partition - where your files are kept.
   3.Swap partition - this need only be twice the size of your memory.

so if I want to install windows, ubuntu and ultimate edition will I need:

3 partitions for ubuntu
1 for windows
3 for ultimate edition
=7 (too many)

how is the best way to set the partitions up

---

### Post by adalal on 2009-11-01
> I want to set up a triple boot with Windows xp, Ubuntu 9.10 and then have a third that I can use to try some other o/s- such as linux mint, kabuntu or ultimate edition.
now refering to the following guide:

[https://help.ubuntu.com/8.04/switchi...titioning.html](https://help.ubuntu.com/8.04/switchi...titioning.html)

All you really have to do is make sure you have enough continuous free space on the drive, and use some sort of partition manager.

As far as primary and logical partitioning goes, Windows requires to be on a primary partition, but linux distributions do not have that limitation, so you can actually go ahead and create a logical partition for them.

> now I also read that ubuntu needs 3 partitions


[QUOTE]Quote:
1.Root partition - where Ubuntu is installed. This should be at least 4GB.
2.Home partition - where your files are kept.
3.Swap partition - this need only be twice the size of your memory.
so if I want to install windows, ubuntu and ultimate edition will I need:

3 partitions for ubuntu
1 for windows
3 for ultimate edition
=7 (too many)
[/QUOTE]

The root and the home partitions can be the same, but it disables you from easily erasing and reinstalling your distribution without the need to worry about backups. As for the swap partition, you're only going to be using one distro at a time, therefore, the swap partition can function for your Ubuntu 9.10 and the other linux distribution you'd want to use.

You can also use the same home partition for the two linux distribution as well, since it'd be redundant to have so many copies of the same files. Also, if you hardly use windows, you can easily access the windows drive as a home folder as well... which is not really recommended, but I do anyways... 

So, here's the breakdown:

1 for Windows
1 for Ubuntu 9.10 root
1 for your other linux distro
1 for your swap (1-2 times the size of your RAM is recommended)
1 for your home

So, there you go! If you used your windows partition to store the your home, you can benefit from having just one copy of files that you could use throughout your computer (eg. Music, pictures, documents, videos, etc.), and that'd also reduce the number of partitions to 4 instead of 5...

---

### Post by indytim on 2009-11-01
The above is not obtainable.

Keeping it simple with a partition editor:

1.  Create partition #1 NTFS (Windows has a strong preference for being first out of the gate.
2.  Create a small swap partition (2x RAM or max 2G).
3.  Create an ext3 partition for Ubuntu "/".
**4.  Create an extended partition for the remainder of the drive.**
4.  Within the extended partition, create a ext3 for your "/home".
5.  Leave the reset of the space within the extended partition as un-allocated (for future distro's etc.)

IndyTim

---

### Post by QLee on 2009-11-01
[QUOTE=ave2]
it states:
Quote:
 A hard disk can only have 4 primary partitions.
 
 However you can create a logical partition instead. This allows another 2 extended partitions to be created within it. [/QUOTE]

I think this was a source of misconception for you. You can create 2 logical partitions in the extended partition as per the howto. However, you are not limited to only 2 logical partitions in the extended physical partition. You would be able to create the third one you mentioned.

I kind of like indytim's solution but you may want swap equal to RAM or just a small amount more if you want to hibernate. I would probably put swap as the third instead of second, just a difference of style, not likely to make much difference.

Be careful if you try to have the same /home for two different distros, sometimes if they are too divergent the configuration files for software has problems because of different versions. Also if this is to be a "test" partition, consider if you want your tests to muck with your real home for the Ubuntu partition?

---

### Post by ave2 on 2009-11-01
thanks everyone, that makes sense... I have 4 GB Ram, so I dont need a huge swap drive, ill keep it 2GB as suggested, the first time I installed 8.10, I was completely lost- i was used to windows with only one partition, but I think I get it now

---

### Post by desperado665 on 2009-11-01
I currently quad boot windows 7 (requires 2 primary partitons), Ubuntu 9.10, Mint 7 kde, Mint 7 Gnome and I also have a data partition that I save all my data to.

Starting with a clean 500GB hard drive, I first installed Win7 (windows 7 requires the first 2 primary partitons on your hard drive) and allotted 60GB for it. 

Next I installed Mint KDE. Manually set up a 2gb swap (primary) partition, then allocated the remainder of my drive as an extended partition. Within the extended partition, set up how ever many 20gb logical drives as you want distros, these will be mounted as your / for each distro you install (in my case 3). Then I set up a logical drive of 100GB for a combined /home partition. In this case you **MUST** have different logon names for each distro. Also you **MUST NOT** format your /home partition after the first install.

Then I installed Mint gnome by setting the second (sda7) extended 20gb drive as / and set /home (sda9) without formatting.

I installed Karmic last to take benefit of grub2 by setting / to (sda8 ) and home to (sda9) without formatting. 

So far, I have not had any problems at all booting into any OS at my choosing. Hope this helps.

---

### Post by ave2 on 2009-11-01
I read somewhere where someone suggested that in addition to the small partitions for each o/s, you create large NTFS partition for both windows and ubuntu files- is this good advice, or is it better to keep the two o/s completely seporate

---

### Post by LewRockwell on 2009-11-01
Multi-booting...Partitioning Screenshots Provided

Acer Aspire One Multi-Boot Machine(daily use=ten hours plus)

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)


Toshiba Satellite Multi-Boot Machine(daily use=four to six hours plus)

[http://ubuntuforums.org/showthread.php?t=1252042](http://ubuntuforums.org/showthread.php?t=1252042)


Other:

[http://www.justlinux.com/forum/showthread.php?t=147959](http://www.justlinux.com/forum/showthread.php?t=147959)

.

---

### Post by Penguin Guy on 2009-11-01
> **ave2 said:**
> I read somewhere where someone suggested that in addition to the small partitions for each o/s, you create large NTFS partition for both windows and ubuntu files- is this good advice, or is it better to keep the two o/s completely seporate
Your choice, I would use FAT instead of NTFS though. When your setting up your partitions you should use GParted, and you'll probably need to do it from the live CD. Ubuntu does not need 3 partitions, it only needs one, although the geeks say it is better to have more.

I triple boot too, take a look at my partitions:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=134093&stc=1&d=1257085203[/IMG]

The light blue box is an extended partition, and the four dark blue boxes inside that are logical ext3 partitions. From left to right they are: /boot, /, /home, Utility.
The Utility partition is just another install of Ubuntu (as you can see it *is* possible to install Ubuntu on one partition). So you should be trying to make something like that (but of course it's your choice if you want to have multiple partitions or not).

---

### Post by desperado665 on 2009-11-01
> **ave2 said:**
> I read somewhere where someone suggested that in addition to the small partitions for each o/s, you create large NTFS partition for both windows and ubuntu files- is this good advice, or is it better to keep the two o/s completely seporate


Personally I use windows ONLY for gaming. I never download anything using windows. So my data partition is formatted ext4. I can still easily copy anything from ext4 to my NTFS partition if necessary.

---

### Post by ave2 on 2009-11-01
thanks once again everyone, this gives me a lot of options...

---

### Post by QLee on 2009-11-01
> **ave2 said:**
> I read somewhere where someone suggested that in addition to the small partitions for each o/s, you create large NTFS partition for both windows and ubuntu files- is this good advice, or is it better to keep the two o/s completely seporate

This depends somewhat on the way you use you system and your skill level. It definitely *could* be good advice to create a partition NTFS for sharing files between the two OS whichever OS is running but that is not the only way. One size does not fit all. I think sometimes leave MP3s, pictures, etc. on a native Windows filesystem to make it easier to see and open them from Windows.

---

### Post by kansasnoob on 2009-11-01
I don't know what the limit is regarding the number of logical partitions contained in one extended partition, I haven't reached it yet:

[ATTACH]134104[/ATTACH]

In that case partitions are as follows:
sda1 = Windows
sda3 = Karmic /
sda2 = extended
sda5 = Jaunty /
sda6 = Jaunty /home
sda7 = Mint Gloria /
sda8 = Mint Gloria /home
sda9 = swap
sda10 = Karmic /home
and sda 11 & 12 are just waiting for my next project

---

