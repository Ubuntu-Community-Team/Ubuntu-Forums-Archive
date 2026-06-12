---
title: "Seeking advice to implement this backup strategy"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by mjjohanson on 2011-01-13
After 22 years as a usoft user I have stepped up to ubuntu linux, however, I wish to emulate a backup strategy developed for my old systems and am seeking advice on how to do it. 

On the old system I have two drives each with two primary partitions.  The first partition on the first drive has the boot- and usr-like files.  The second partition on the second drive has var- and home-like files.  Every night any file that is changed or added during the day gets copied  to the parallel partition on the other drive. The objective is to save  the latest copy of current files as well as one copy of old files that  have been replaced. On the old system when the boot drive failed  (happened twice) I simply changed a jumper and booted off of the other  drive until I installed a replacement drive and copied stuff over. I  could also go back to yesterday's version of a file if I really trashed  something up. Third, I would have one copy of old data files as a  near-line archive while keeping the current directory cleaned out (I  also saved the archive-like folders to a third drive every so often).  And, fourth, it provided a modest level of load balancing between  drives.

I just need a bit of help to make the shift from the drive-oriented nature of DOS to the file-system-oriented nature of Linux. 
-How do I create parallel file systems on two drives, one primary, one secondary with the ability to swap roles?
-How do I make it possible to boot from one file system normally and  then the other after a drive crash? (I would change the boot drive in  the BIOS rather than jumpers.)
-What is the best utility to duplicate the functions of xcopy in DOS?

All of this is not RAID, mirroring, archiving or synchronizing. I have  considered and applied all of these at one time or another and nothing  has worked as well as what I have. Thank you, in advance, for your help.

---

### Post by candtalan on 2011-01-13
Not a direct answer here. But it might give you some ideas. I actually use three drives, two large data drives, and one smaller (but still fairly large) system drive. As it happens I have a triple boot on the system drive, various Ubuntu versions. 

On the system drive, normal use version, I have installed simple backup (sbackup) which is in the repositories. On the very rare occasions I have a  boot problem, I would first try to run one of the other ubuntu versions and if say, grub menu was not even available I would simply use a live CD to maybe access data, or more likely to reinstall grub2 into my chosen normal partition and drive, then subsequently I would get grub2 to update itself to the latest OS's information (sudo update-grub I think).

'Simple backup' details: this can run daily, backing up from and to, of your choice, with useful defaults. I regard it as a useful 'system' backup. The backups are configured by me to be put onto data-a, so finally at night, the sbackup data of the system, also finds itself included in the full data copy.

I would consider that a file system crash was less likely with modern Linux FS's, than (presumably) ntfs?

The two large data drives are used in a very lazy way by me. I call one a and the other b. Data-a is not used as home (home is only used for non persisting data things), it is used to keep all of my daily use data. At the end of each day I use a simple rsync command to copy the whole data a drive over to data-b drive.

I have used sbackup in earnest once, when I apparently lost the bash terminal 'history' of recent commands. It worked ok.

However I should say that Ubuntu is so easy to install that I would be more likely to reinstall if a major problem occurred than I would be to try to repair using sbackup, but it is there anyway. 

Nearly forgot - the normal grub boot menu includes a rescue mode which also includes an option to try to repair broken packages.

I also make use of web based file storage for some files. Ubuntu one works ok now and I use it, also dropbox is good, though more proprietary, and I use it also.

Hope that gives you some useful ideas?

---

### Post by freak42 on 2011-01-13
I am not the most experienced hd/partion user, however I hope I can provide you with some input nonetheless. Please be advised that all the following suggestions haven't been tested by me.

> -How do I create parallel file systems on two drives, one primary, one secondary with the ability to swap roles?

If your drives are identical, I would setup the whole system with the two partitions on one drive, and use a tool like 'dd' to copy the whole drive over to the other bit by bit. That *should* take care of issues such as the boot sector and such stuff. If you are using UUID's in your fstab config make sure that the UUID's don't get cloned in the copy process (I don't know whether the get copied or not)

Another approach is to simply use gparted to setup the 2nd disc similar to the first one and then manually add the bootsector afterwards with a live disk.

> -How do I make it possible to boot from one file system normally and then the other after a drive crash? (I would change the boot drive in the BIOS rather than jumpers.)

I don't see how you can do this without having a live disk nearby with which you can edit the fstab settings on your healthy disk in such a case.

> -What is the best utility to duplicate the functions of xcopy in DOS?

I don't know xcopy, however rsync (as root with -ao options) probably is a decent option (it has fast configuration options such as only updating changed files..etc)


hth

---

