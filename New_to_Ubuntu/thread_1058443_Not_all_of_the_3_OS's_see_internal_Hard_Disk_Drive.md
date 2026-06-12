---
title: "Not all of the 3 O/S's see internal Hard Disk Drive! Why not???"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by suomalainen on 2009-02-02
Ubunteros, 

I have a tri-boot system and use the following operating systems:

Ubuntu 8.04LTS
Windows XP
Windows 2000

Each operating system has been installed in it's own dedicated hard drive. Each hard drive is mounted in its own dedicated mobile rack. Thus, I have three individual racks installed within my tower. To use a particular operating system the  PC must first be OFF. Then with a turn of the key, I turn &#8220;ON&#8221; the rack containing the operating system I want to use. It's that easy!

IMPORTANT: Mounted inside the PC is a 500GB hard drive. This hard drive is used to swap data between WINDOWS XP and UBUNTU 8.04LTS



THE PROBLEM

When I boot Ubuntu 8.04LTS, I can see the internal hard drive I have mounted inside the PC. When I boot Windows XP I can see the following hard drives:

Local Disk (H) This HD contains all the XP files and folders etc...
Local Disk (P) This HD is mounted inside the PC and is used to swap data between XP and Ubuntu 8.04LTS.

For over a year, I have used the internal hard drive to swap data back and forth between XP and Ubuntu. This has worked for me and I'm not willing to try anything else! It's not broken so there isn't anything to fix!

NOW, with Windows 2000 the story is different. In Win2k I have the following HD's:

Local Disk (C)  this has all windows 2000 files

Local Disk (I) This is the drive that has all my data. In XP it is seen as drive &#8220;P&#8221; and in Ubuntu by the name I gave to it. BUT in win2k it is known as the &#8220;I&#8221; drive.

HERE IS THE PROBLEM

Every time I click on the &#8220;I&#8221; drive I get the following message:

&#8220;Disk is not Formatted&#8221;

Do you want to format it now?

Yes OR No

WHY DOESN'T WINDOWS 2000 SEE THIS HARD DRIVE THE SAME WAY AS DOES UBUNTU 8.04LTS ANS WINDOWS XP?????

WHAT CAN I DO SO THAT I CAN SEE THE DATA THAT IS ON THIS DRIVE?????

F.Y.I. The goal here is that I want the internal hard drive to be able to be seen by all 3 operating systems. Currently, only Ubuntu and XP can see the data on this drive. As just stated above Win2000 does not. Why???


Thank you.

---

### Post by rudeboyskunk on 2009-02-02
The case is most likely that Win2K will not recognize the formatting of the hard drive you want (usually they only recognize FAT16, FAT32 and NTFS).  I know my Windows 7 partition (NTFS) does not recognize my Ubuntu partition, which is ext3.

If I'm wrong about this, somebody please correct me before he hurts his computer.

---

### Post by 2hot6ft2 on 2009-02-02
I suspect the same thing as rudeboyskunk in that the drive is formatted to a file system that win 2k can't read. You gave no info as to how it's formated in your info.

---

### Post by suomalainen on 2009-02-02
In Ubuntu I did A right click on this drive. I then clicked the "Volume" tab and it says 

FILE SYSTEM: ntfs(3.1)

Does this help????

Thanks

---

### Post by handydan918 on 2009-02-02
Apparently, [there are different versions of ntfs]("http://www.pcguide.com/ref/hdd/file/ntfs/verNTFS11-c.html"). Maybe you need to update win2k in order to use that version.

---

### Post by suomalainen on 2009-02-02
YOu mean I need to re-format the sata hard disk drive that windows 2000 is on?

Before I do that how to you tell what file system is in place in win2k?

---

