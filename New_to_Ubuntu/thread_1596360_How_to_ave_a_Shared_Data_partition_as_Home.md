---
title: "How to ave a Shared Data partition as /Home"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by Mistiq Dragon on 2010-10-14
Greetings all, I"m still relatively new to Linux/Ubuntu.  Earlier this year, I made the transition to using Lucid Lynx the majority of the time, after a lot of work and help from the community, I ended up with a Linux partition, Windows 7 partition and a huge (well big to me) NTFS partition for all my data.

It worked out okay but it's not what I really wanted.


My ideal setup would be SDA for Linux(/root, /swap) 20Gb
SDA 2 would be for my WIndows 7 partition 40 GB
SDA 3 would be where all my personal files as well as /Home would be


So now that I'm ready to reinstall WIndows 7 and Maverick onto my system I wanted to get advice from the people here on what needs to be done.  I've already seen that /home won't be mounted on a NTFS partition but I definitely want /home to be separate so that I don't have to worry about losing data while I'm playing around with all these wonderful distros.


1st and foremost, how do I go about getting home sepearate from root and pointing towards the Data partition that I already have set up and organized?

2nd of all, any advice on how I should set up my linux system when I'm installing?

The system I'm working with has 5 GB of ram, is a quad core system, Linux will be in a 20 GB EXT4 system, while Windows will be in a 40GB NTFS partition.



Thank you and let me know if I can clear anything up.

---

### Post by jtarin on 2010-10-14
First of all, Windows needs to be on the first partition /sda1.Then your data partition would come next /sda2. Then a partition each for /,/home and swap. During install you can designate mount points for each Linux partition.You can only have 4 primary partitions so installing Ubuntu you will more than likely install /,home and swap to an extended partition.Linux will detect your data and Win partitions when you boot into Linux. Little or no configuring needs to be done.

---

### Post by srs5694 on 2010-10-14
Windows does *not* need to be on /dev/sda1. I've seen this claim many times, but I've never had problems installing it elsewhere. That said, there's also no reason *not* to install it on /dev/sda1 if you're starting from scratch or if it's otherwise convenient. Windows *does* need to be on a primary partition, though, or at least use one for the initial part of its boot process.

Given the stated needs, I'd suggest using ext3fs, rather than ext4fs or something else, on the /home partition. There are Windows drivers for ext2fs and ext3fs, but not for ext4fs, so if /home is on ext3fs, you should be able to access /home from Windows by installing the relevant drivers. That said, I've only toyed briefly with these drivers myself, so I can't vouch for their speed, reliability, safety, etc. If you use these drivers, I recommend using something other than ext2fs or ext3fs, and maybe not even ext4fs, for the Linux root (/) filesystem. Perhaps ReiserFS or XFS would be a good choice. This will keep Windows from mucking with the Linux root filesystem.

As to the logistics of transitioning from the current setup to the new one, I'm not sure; that depends on how much data must be preserved, what sorts of backup tools are available, etc. The simplest and safest option is probably to back up all the personal data to another disk, DVD, tape, or whatever; wipe all partitions and create new ones in the desired locations and sizes; re-install Windows; re-install Linux; and then restore the data.  Another option would be to use GParted to resize partitions in such a way as to enable copying personal data from the current data partition to what will be the new /home partition, then delete everything else and re-install both OSes.

---

### Post by Mistiq Dragon on 2010-10-14
The reason I have my setup as I do was because I was led to understand that the closer to the beginning of the hard drive the data was, the easier it's accessed.  (I hope that made sense)

I think Originally, I had Windows as SDA, data as SDA2, and Linux as Sda3 but since my data was so big it pushed my Linux partition all the way to the back of the drive which didn't feel right to me.

So I switched Linux to the very front as I'm intending that to be my primary OS.

The setup I have hasn't caused me any problems so far, I just want an efficient way to have my Home folder and my Data partition be the same instead of me having to manually go in and edit things all the time.

I've heard about using ext3 on Windows but I've been led to believe that it wasn't quiet up to snuff

---

### Post by srs5694 on 2010-10-14
It's certainly not "easier" to access data at the start vs. the end of a disk, although there can be modest speed differences. These differences will be quite small, though. I just ran some tests on one of my disks. In three measurements from partitions near the start and end of one particular disk (which is a couple of years old), I got an average of 78.06 MB/s for an early partition and 77.52 MB/s for a late partition. I doubt if you'd notice that difference in any real-world application -- it's only about 0.7%.

Another matter: /dev/sda is the entire first disk. Partitions on that disk are numbered after that -- /dev/sda1, /dev/sda2, and so on. There can be gaps in partition numbers, although not normally in numbers above 5 on most disks. These device filenames, being Linux identifiers, are case-sensitive. Primary partitions are numbered 1-4, while 5 and up are logical partitions. For this reason, it's slightly less confusing to put primary partitions at the start of the disk and to use /dev/sda4 to define an extended partition that holds logical partitions. That way, device numbers can reflect order of the partitions on the disk. This isn't strictly necessary; you can have one or more primary partitions at the end of the disk, with logical partitions before them. Doing so can be slightly confusing, though. Since Windows must consume a primary partition, creating a neatly-ordered setup with more than four partitions therefore requires Windows to come at the beginning of the disk.

---

### Post by oldfred on 2010-10-14
I prefer to have system partitions both windows and Linux separate from data. You can use a separate /home and or separate /data partitions. But if sharing with windows you may want data easily accessed from both so then another /shared partition that is NTFS works well. 

From Ubuntu I may read data in my Windows System partition but only write into it to make repairs. I have Firefox & thunderbird profiles in a /shared NTFS partition so bookmarks & email are the same in both. 

If you want to move /home - 3 slightly different ways rsync, cp & cpio:

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)
cp without -a and copying as sudo root takes ownership (not good)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

