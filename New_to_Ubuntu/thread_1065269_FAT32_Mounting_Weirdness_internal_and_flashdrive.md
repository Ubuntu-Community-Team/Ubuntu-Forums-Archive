---
title: "FAT32 Mounting Weirdness: internal and flashdrive"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by literatedegenerate on 2009-02-09
My problem is specifically with mounting FAT32 media, both internal volumes and usb flashdrive. Up until a about a week ago, everything was working normal. My internal FAT32 partition would appear in the Places context menu and I had the option to mount it, eject it, etc. I could plug in my usb thumbdrive and my computer would recognize it and present a dialogue box with the option to mount (or so I think anyway, I didn't pay attention when it was working) and it also would appear in the Places menu. However, for some unknown reason (probably novice error on my part but I don't know what I could have done to cause this) none of these things happen. The Places menu does not show either my internal partitions which it previously did (both NTFS and FAT32), or my thumbdrive. To make this even more strange, when I do plug in the thumbdrive, an additional rescan USB drive button appears, making for a total of 2 scan scan USB drive buttons which do absolutely nothing when I click on them. Both of these volumes in question do appear in the output of the fdisk -l command, and I can also manually mount them from the command line. I have since configured my /etc/fstab file so that my FAT32 data partition automounts at startup, so problem is remedied--although I do not know the root of the problem--with a bandaid of sorts. By the way, I tried reformatting the thumbdrive to ext2 and it behaves just fine, so it would appear that the problem is specifically with NTFS and FAT32 volumes. Also, even after manually mounting the thumbdrive, I have tried to copy files to it and the file transfer operation begins, but never finishes, presenting me with an I/O error of some sort. I have searched the forums the best I can and still cannot find a solution to my problem or another similar case to reference. 
Any suggestions appreciated, as I've tried everything I can find to no avail.

---

### Post by unplugged23 on 2009-02-09
Try formatting to ext 3

---

### Post by literatedegenerate on 2009-02-09
Thanks for the suggestion, however that is not really an option as I have the FAT32 filesystems for a particular reason--compatibility with my Windows OS and also university computers in the case of the thumbdrive--so having data on a filesystem which other Windows computers will not recognize would not help (I realize that I can add ext3 functionality to Windows, but that won't help me on the university computer system). I'm really trying to get to the root of the problem, it worked last week but not this week--why?

---

### Post by unplugged23 on 2009-02-09
Have you run any major system updates?

---

### Post by literatedegenerate on 2009-02-09
System Updates, well if there were any major updates released in the last week or so then yes, I have installed all updates available. As I just did a fresh install about two weeks ago I have added many software packages and have no idea which of these are causing the problem
I guess that is a lesson to me: backup your system.

---

### Post by unplugged23 on 2009-02-09
yup lol,

I cant say for sure weather or not this was the culprit or not, but it sure sounds like it to me. However theres got to be another way around this, I just cant think of any...

---

