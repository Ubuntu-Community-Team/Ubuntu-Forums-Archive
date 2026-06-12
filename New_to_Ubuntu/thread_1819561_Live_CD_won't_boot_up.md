---
title: "Live CD won't boot up"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-08-06
Ok, new problem.
Last night, I decided to upgrade the 10.04 in my laptop to 10.10. To make a long story short, after doing the upgrade, it all went to hell.
So I decided to install Lubuntu 11.04. After downloading the torrent without a problem, and extracting the ISO file, I burned the CD on K3B. But the CD won't boot.
Then, I did a search, and came up with instructions on how to make a bootable CD, here:

[http://www.stchman.com/boot_cd.html](http://www.stchman.com/boot_cd.html)

So I burned another one, and, when I tried to install Lubuntu with it, I got this:

> 
No FAT32 Volumes Found, exiting...
NTFS Filesystem Driver for DR-DOS. Version 1.200
Copyright (c) 2002-2004 Ahead Software and its licensors.

Usage: ntfsread.exe [-u]

Partition C:\ installed
Partition D:\ installed

Search for USB HDD devices...

USB support successfully initialized
NWCDEX.EXE Version 2.81 CD-ROM file handler.
Copyright (c) 1992, 1997 Caldera Inc. All rights reserved.
     Drive E: Driver 'MSCD001' unit 0
Completed codepage prepare function
Completed codepage select function
NLSFUNC R4.00 National Language Support
Cpoyright (c) 1988, 1998 Caldera, Inc. All rights reserved.


Caldera DR-DOS 7.03
Copyright (c) 1976, 1998 Caldera, Inc. All rights reserved.
[DR-DOS] A:\>
I know for a fact that the computer is working properly. Right now, it has Windows 7 Ultimate. A few days ago, I had installed 11.04 and it worked without a hitch. Just ended up installing 10.04, because I didn't like 11.04.

I don't want to install Ubuntu as Wubi. What should I do to burn a CD I can boot up with, and start a 100% new install?

Thanks in advance. :)

---

### Post by Gone fishing on 2011-08-06
I don't quite understand - you don't need to extract anything from the iso image, all you need to do is burn the image to a disc (not copy the image to a dsc). Sorry I don't know k3b but with Brasero or even Nero in Windows there is an option to burn an image this is what you need to do I'm sure k3b can do this.

Very simple just burn the image if the image is good it will work.

---

### Post by Praveen30 on 2011-08-06
well,  i think you should give a try to brasero. it comes with Ubuntu cd..

[http://www.lostintechnology.com/how-to/how-to-burn-a-cd-or-dvd-on-ubuntu/](http://www.lostintechnology.com/how-to/how-to-burn-a-cd-or-dvd-on-ubuntu/)

---

### Post by Inodoro Pereyra on 2011-08-06
I will try to burn the ISO directly, see what happens.

I had a lot of grief with Brasero in the past, and, in turn, I was advised to switch to K3B, which has never given me trouble, so far. We'll see. I'll try burning the ISO with K3B first.

Thank you both for the replies. :)

---

### Post by Inodoro Pereyra on 2011-08-06
FML it's working. Just had to burn the ISO directly.

I'm feeling extremely stupid right now.

Anyway, thanks again. :)

---

