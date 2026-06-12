---
title: "Disk Partitions and file systems"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by BennyBoy1983 on 2009-07-18
Hi There

I'm totally new to Ubuntu, I haven't fully installed it yet but had a play around with the Live CD and I love what I'm seeing. Unfortunately I do still need Windows, so I intend to dual boot.

Here's the deal, I have a 500GB HD, windows XP installed, formatted as NTFS. I need at least 100GB of this for Windows and it's programs, Let's say 250GB though for room to expand into. I do want to get another 500GB HD as well for additional storage space.

Is the best option to install Ubuntu onto the first HD, leaving 250GB as NTFS for Windows and creating a partition during the Ubuntu install of 250GB and having it as ext3? Then when I get a new 500 GB HD, formatting it as either FAT32 or half/half FAT32 and ext3?

Or

Do I wait until I have a new hard drive and have one as a windows NTFS and one as Ubuntu ext3 and keep it all nice and separate? 

I hope all this makes sense, thanks in advance for any help!:P

---

### Post by Najand on 2009-07-18
If you know how to mount hard disks and you prefer to share data between Windows and Linux (because Windows cannot mount ext3/4 partitions), the first option. Else, wait for your second Hard Disk and install it later.

Anyway, it is always advised to install Windows first and install Linux afterwards. (Windows is unable to recognize any other OS installed on your computer and will mess up with your bootloader.)

---

### Post by Paqman on 2009-07-18
> **BennyBoy1983 said:**
> 
Is the best option to install Ubuntu onto the first HD, leaving 250GB as NTFS for Windows and creating a partition during the Ubuntu install of 250GB and having it as ext3?


Yep, that's a pretty sensbible way to do it. If you let the Ubuntu installer handle this for you it'll actually create two new partitions. One for the system, and a tiny one called swap that works like a Windows swap file. 

> 
Then when I get a new 500 GB HD, formatting it as either FAT32 or half/half FAT32 and ext3?


I wouldn't use FAT32, it's pretty old and clunky. I'm not sure if it even supports disks that big, certainly it has a 4GB max file size. It also fragments badly. If you want a partition that both Ubuntu and Windows can read I would use NTFS. You can use the package ntfs-config on Ubuntu to set up permanent access to it.

---

### Post by donaldt on 2009-07-18
I have what I believe to be a related question.  My linux OS is set up and operating on an external 250GB hard disk drive.  My laptop Sony computer is configured to go to the USB drive first and see if it is inserted.  If it is, the linux 9.04 system boots up.  If it is not plugged in, Windows Vista (the Sony factory installed version) boots up.

I have some old files that I would like to access from both/either  operating system.  I have used gparted to establish around 50 GB of free space on an extended partition on the external hard drive.  (the external hard drive also provides space to back up my Windows files)  Am I correct in my understanding that an NTSF formatted section would be visible and accessible from either my windows Vista OS or Linux 9.04?

Thanks as usual for the free advice!

donaldt

---

### Post by jeppewinther on 2009-07-18
You are quite right.
Ubuntu will happily access NTFS, and Windows will as well, obviously.
As stated above, Ubuntus NTFS access can be set up using ntfs-config.

---

### Post by raymondh on 2009-07-18
@ BennyBoy:

If it were me, I would put both OS' in one HD and use the 2nd HD as a NTFS storage.

@ Najand:

*Windows first before Linux* is really an Old-Wives-Tale. Sorry, I do not agree.

It does not matter which OS is installed first or last.  Even in a linux + windows install and Windows overwrites into the MBR, recovering GRUB is a simple and quick effort on the Operators' part.  

The only convenience in Windows + Linux is that GRUB will be the bootloader when operator reboots after installation.  But, what if GRUB is messed up after that first reboot?

Really, recovering GRUB is so common nowadays that it no longer matters which comes first.  There are so many tutorials (in and out of the forum) on how to recover GRUB.

Back to the OP....

-Back up your files
-Defrag windows
-Check the liveCD for defects and md5 
-Read/research on installation guides to minimize errors/frustrations when the time comes

Some guides:

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.ht](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.ht)

Good luck.

---

### Post by donaldt on 2009-07-20
Thank you for the confirmation.

Now, I have loaded ntfs-config into Ubuntu, but it does not recognize the disk I want to set up.  When I go to Gparted it will not allow me to format unallocated space or an extended partition.  If I go to Vista I can access the external hard drive where all of this resides, but again there is no way to format the partition I want to use.

What am I missing on this?  How do I get ntfs config to work and end up with a partition that will be accessible to Vista and Ubuntu?  It is not apparent to me in the trials I have made so far.  

Thanks if you can help...

donaldt

---

### Post by CaptainMark on 2009-07-20
Just play around with the live cd long enough until you realise that you infact *don't *need windows anymore, worked for me, 3 months so far never looked back.

---

### Post by oldfred on 2009-07-20
Gparted will not work on mounted partitions. Are you using it from the linux install on your first disk or from the CD?

---

