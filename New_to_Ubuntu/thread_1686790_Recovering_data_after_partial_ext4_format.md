---
title: "Recovering data after partial ext4 format"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by vafortier@bellsouth.net on 2011-02-12
I am a newbie user to ubuntu -- really like it so far.  However, I downloaded 10.04 x86-64 LiveCD and booted, ran fine.  I powered-up my external drive which has my install plan and lots of backup files representing 4+ years of work.  I even read the install documentation instructing me to unplug all external drives as they will be formatted by the install process -- can you see where this is going! :(

OK, I'm stupid!  I formatted my 250GB external drive with ext4 -- at least until I pulled the plug!!!  :confused:  I can't believe I am the first to do this, especially since there is a specific comment in the instructions to unplug external drives which I promptly ignored! ](*,)  I've searched the Internet looking for _recovering ext4 data_ and found hundreds of entries -- some blogs, some free software, and some software at cost.  After my stupid mistake, I'm hesitant to download and run the first thing that looks good as I'm afraid I may make a bad situation worse!!!

Initially, the external partition contained 63.9G of data.  When I run _Disk Utility_ it shows 61.5G used with no files or folders.  What does this mean?  Are some of my files still here?

Has anyone else done this and care to explain how to get out of it?  It certainly appears that recovering the data is not going to be easy.  Again, I'm afraid to do the wrong thing and make matters worse.  Can some of all of my data be recovered?

Thank you in advance.

---

### Post by Rubi1200 on 2011-02-12
Hi and welcome to the forums :-)

sorry to hear about your troubles.

Perhaps the best option for recovery is Testdisk and Photorec:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by jerrrys on 2011-02-12
i once wipe 80,000 pics from an external hdd and testdisk fixed it in minutes

---

### Post by vafortier@bellsouth.net on 2011-02-13
Thank you Rubi1200 and JerryS for your words of wisdom and encouragement.  I really feel like a dummy for doing this.  In my defense, it was late at night and anxious to get this done before going to bed.
 
I've read the documentation about TestDisk and it appears it will do the trick, although the documentation is clearly oriented more toward NTFS than ext2/ext3/ext4.  If/when I get through this, I'm going to format my external HDD as NTFS!
 
Again, thank you.

---

### Post by vafortier@bellsouth.net on 2011-02-13
Downloaded testdisk per instructions and read documentation.  I'm confused!  When I run right-click the desktop icons and select properties, it shows 6.1G used.  When I run testdisk, I get the following:

Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P EFI GPT                  0   0  2 30401  80 63  488397167

Bad relative sector.
No partition is bootable


Selecting QuickSearch reveals the following:

Disk /dev/sdb - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   0 35 15200 254 63  244204031 [Linux]
D HPFS - NTFS          15200 168  1 30401 254 63  244209546 [Windows]


The files I want to recover are in the [Linux] partition.  Selecting "P" to list the files shows:

     HPFS - NTFS              0   0 35 15200 254 63  244204031 [Linux]
Directory /

dr-xr-xr-x     0     0         0 29-Jan-2011 17:30 .
dr-xr-xr-x     0     0         0 29-Jan-2011 17:30 ..



Does this mean my files are gone for good?  Are there other options to consider?

Please advise.

---

### Post by jerrrys on 2011-02-13
select c to copy and see if will allow this

---

### Post by vafortier@bellsouth.net on 2011-02-15
I've followed the menu trees through testdisk and cannot seem to get past the root directory entries, i.e. the "." and ".." entries -- no files.  Testdisk does show the two partitions and high-level directories that were there.

I'm now trying photorec.  In just a few minutes, it seems to be finding files on the "lost" directory.  The search is scheduled to run for 3 hours, so it'll be a little bit before I can verify the results.

Am I missing something important on testdisk?  I just can't seem to get it to drill down past the . and .. entries!

---

### Post by Paqman on 2011-02-15
If Photorec is working for you, just go with that. Photorec is a part of Testdisk anyway.

Good luck!

---

