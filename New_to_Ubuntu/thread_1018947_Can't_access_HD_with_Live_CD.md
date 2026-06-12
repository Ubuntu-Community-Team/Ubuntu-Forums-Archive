---
title: "Can't access HD with Live CD"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by jdpearson on 2008-12-22
I've got 20+ years of computer experience but I'm quite the n00b to Linux.  I installed Ubuntu 8.10 on my laptop so I could start learning.  I ended up screwing up a file needed to boot.  

I used my Live CD to boot the computer and could see my drive.  I thought I would just track down the file and change it back.  At the very least I wanted to backup a few files from my /home directory.

However, whenever I tried to access my files I got a permissions error.  What am I missing?

Sorry, (I know this is lame) but I don't have the exact error.  I just reinstalled Ubuntu since it only takes a few minutes.

Finally, is it possible to reinstall Ubuntu without reformating/partitioning the drive?  Something like a Windowz Repair installation?

---

### Post by SlidingHorn on 2008-12-22
Well, there's two different things I think you could mean, so here goes:

1.  Data recovery - [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

or

2.  Keep your personal data separate from your actual OS installation - 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Hope that helps :)

---

### Post by IamReck on 2008-12-22
Are you trying to access the file through Nautilus?

You probably need to access the file through terminal using sudo.

---

### Post by akelsall on 2008-12-22
You might try booting with your LiveCD, open a terminal window, the "su" to whichever user you were when your created the files you're trying to recover. For example, if you created the files while logged in as "noobie", you would enter "su noobie" and use noobie's password. 

Here's a link that may also help as well. It's info I posted when upgrading to 8.10, but there are things there that may help (especially in respect to your question about re-installing without having to repartition). The other links posted looked very useful as well.

Andy

---

### Post by emecas on 2008-12-22
...About access your HD... how are you trying to access?

maybe you can take a view of those posts ....

[http://ubuntuforums.org/showthread.php?t=900839](http://ubuntuforums.org/showthread.php?t=900839)
[http://ubuntuforums.org/archive/index.php/t-250165.html](http://ubuntuforums.org/archive/index.php/t-250165.html)

---

### Post by dannyboy79 on 2008-12-22
when you boot from the livecd, does it show your hard drive as being mounted? is there for example after entering this command
```
mount
```
somewhere in the list something called either hda1 or sda1? if not, you'll need to mount it yourself. You need to find out what disks you have in your system first, that would be done with this command
```
sudo fdisk -l
```
this will show something like this:
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86938693

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4741    38082051   83  Linux
/dev/sda2            4742        4865      996030   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ddbc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

so determine which disk you want to mount.
that would be done with this command
```
sudo mount /dev/hda1 /mnt/
```
now the entire hda partition 1 is mounted at the folder within nautilus /mnt. Within there you should be able to access and change anything you want with sudo through the terminal or launch nautilus using gksudo nautilus BUT be careful, while using gksudo with nautilus can be very dangerous because one wrong drag and drop and you've really done it. Good luck and let us know what file you think you buggered up.

---

### Post by IamReck on 2008-12-22
It should be listed under "Places" you should just have to click on it to mount it.

---

### Post by jdpearson on 2008-12-23
> **SlidingHorn said:**
> Well, there's two different things I think you could mean, so here goes:

1.  Data recovery - [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

or

2.  Keep your personal data separate from your actual OS installation - 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Hope that helps :)

Thanks.  No, no. 1 is not what I'm looking for but #2, which I've seen discussed before, would help for future issues.  Although I think I'd still have to go back and install all the appys  I was more interested in just replacing the startup files.

---

### Post by jdpearson on 2008-12-23
> **IamReck said:**
> It should be listed under "Places" you should just have to click on it to mount it.

Thanks to all the posts so far.  The problem was not that I couldn't see or mount the hard drive.  In fact I could!  However, my desire was to copy my /home director to a backup drive, or just to edit the file that I think I screwed up.  No matter what file I tried to copy or move I got a permissions error.

Now, in WinDoze I would have simply "taken ownership" of the files (assuming they weren't encrypted) and been able to move all those files.

---

### Post by mapes12 on 2008-12-23
If you're using Terminal try changing permissions for /home and all its contents like this ```
sudo chmod -R 777 /home
``` but you may need a wildcard for the files to inherit the permissions like this ```
sudo chmod -R 777 /home/*
```
Note that 777 gives permissions for anyone to do anything.

Or a GUI option would be to go in with root access like this ```
gksudo nautilus
```and try dragging what you want to where you want it.

---

### Post by kandil on 2009-11-10
hi iam having the same problem and if u did fix it and recover ur files can u tell me how u did it

---

