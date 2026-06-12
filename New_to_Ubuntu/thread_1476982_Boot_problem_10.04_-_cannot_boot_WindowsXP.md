---
title: "Boot problem 10.04 - cannot boot WindowsXP"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by prenoob on 2010-05-08
I hope you will allow for my being new to Ubuntu and not technical.  I upgraded a few days ago from Karmic 9.10 to Lucid 10.04 and things are fine (well, some minor matters can wait) apart from my inability to boot Windows XP.  Ubuntu is on an external drive, Windows on the main hard drive.

I had no problem with Karmic and the boot menu looks OK with an entry for Windows XP on sda1.  However, clicking on it simply produces a blinking cursor in the top left of a blank screen.  I honestly have no idea what to do (access to Windows XP is essential for my work).  I have extracted the following basic information:

> trevor@trevor-desktop:~$ sudo fdisk -l
[sudo] password for trevor: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaf73af73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x484d8931

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38539   309564486   83  Linux
/dev/sdb2           38540       38913     3004155    5  Extended
/dev/sdb5           38540       38913     3004123+  82  Linux swap / Solaris
trevor@trevor-desktop:~$ 


---

### Post by SpongeBob SquarePants on 2010-05-08
Hmmm... this happened to me too. Everything in GRUB looked fine, but XP wouldn't boot. So I reinstalled Lucid.

The only thing I did differently first time round, to second time round, is when it was installing GRUB it gave me the option to add an operating system. First time round I ticked the hard drive itself, my Linux partition and my XP partition. The result was I couldn't boot into XP. So I tried installing it again and this time, when installing GRUB, I ticked just the hard drive, and didn't bother with ticking the partitions as well. Lo and behold, I could boot into XP.

Another thing I tried, which worked, but was incredibly time consuming, was reinstalling 9.10 again and then using the upgrade feature to get me to 10.04 (making sure when it prompted me to upgrade GRUB I refused the maintainers settings and kept my own).

No idea what the problem is, but that's how I got round it.

---

### Post by prenoob on 2010-05-08
Thanks SquareBob.  I wondered about the possibilities you mentioned but they do seem long winded.  I honestly can't remember which version of Grub I chose - one with all the options ticked, I think.

---

### Post by oldfred on 2010-05-08
If you did the upgrade and checked all the boxes (you should have only checked drives not partitions)

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You can also use windows cd/dvd to repair with fixboot command. Instructions are slightly different for XP and vista/7 but you want to get into the repair console and go to command line. If you also run fixmbr you will be able to directly boot windows, but will have to reinstall grub or grub2 to the MBR or drives Master Boot Record to boot Ubuntu.

XP:
FIXBOOT C:

Vista/7
BootRec.exe /FixBoot #updates PBR or partition boot sector

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

---

### Post by julio.010101 on 2010-05-08
testedisk solved for me

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by prenoob on 2010-05-08
> **oldfred said:**
> If you did the upgrade and checked all the boxes (you should have only checked drives not partitions)

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You can also use windows cd/dvd to repair with fixboot command. Instructions are slightly different for XP and vista/7 but you want to get into the repair console and go to command line. If you also run fixmbr you will be able to directly boot windows, but will have to reinstall grub or grub2 to the MBR or drives Master Boot Record to boot Ubuntu.

XP:
FIXBOOT C:

Vista/7
BootRec.exe /FixBoot #updates PBR or partition boot sector

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
Thanks for all that information.  Testdisk looks to be within my capabilities (with luck!!) and it looks worth a try before reinstalling and making the best choice of Grub.

---

### Post by prenoob on 2010-05-09
Testdisk seems to have done the job (fingers crossed hard and touching real wood).  Many thanks for all the help - sincerely.

---

