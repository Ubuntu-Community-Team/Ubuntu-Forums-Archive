---
title: "Grub help!"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Myx0.x3 on 2009-01-19
Hi! i installed Ubuntu 8.10 on my USB memory (Sandisk cruzer 4GB) but when i rebooted my system i got all "f"ed up, i got Error 21... and i cant use my Windows XP CD becuse it says that i have no harddisk inserted :S anyway... i got Freedos and i removed the Linux partitions...

but now when i reboot my computer i get into grub :S it says something whit: 

"[ Minimal BASH-like ling edeting is supported.     for the first word, tab lists possible command completions. anywhere else tab lists the possible completions of a device/filename ]

grub>"


please help me to remove this sh*t i realy need my computer today, and forward... its my school computer btw also so i cant format the computer...

---

### Post by Myx0.x3 on 2009-01-19
Hi! i installed Ubuntu 8.10 on my USB memory (Sandisk cruzer 4GB) but when i rebooted my system i got all "f"ed up, i got Error 21... and i cant use my Windows XP CD becuse it says that i have no harddisk inserted :S anyway... i got Freedos and i removed the Linux partitions...

but now when i reboot my computer i get into grub :S it says something whit:

"[ Minimal BASH-like ling edeting is supported. for the first word, tab lists possible command completions. anywhere else tab lists the possible completions of a device/filename ]

grub>"


please help me to remove this sh*t i realy need my computer today, and forward... its my school computer btw also so i cant format the computer...

---

### Post by jimmy the saint on 2009-01-19
Please don't double post.  Please don't swear in your posts.  Pleae DO read the forum do's and dont's
[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

It seems odd to me that the windows cd would show no disk.  Try booting with the Ubuntu Live CD.  From there, open up the partiton manager and make sure that you did mistakenly do something to the HD while you were doing the installation. 
 
You say you installed it to the thumbdrive, but then you say you got freedos and deleted the linux partitoins.  You mean you deleted them from the thumbdrive?  Make sure you didn't delete one from the computers drive.

---

### Post by Myx0.x3 on 2009-01-19
> **jimmy the saint said:**
> Please don't double post.  Please don't swear in your posts.  Pleae DO read the forum do's and dont's
[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

It seems odd to me that the windows cd would show no disk.  Try booting with the Ubuntu Live CD.  From there, open up the partiton manager and make sure that you did mistakenly do something to the HD while you were doing the installation. 
 
You say you installed it to the thumbdrive, but then you say you got freedos and deleted the linux partitoins.  You mean you deleted them from the thumbdrive?  Make sure you didn't delete one from the computers drive.


sorry for the dubble post, but i did not know where to post it, heh... anyway...


is there any IRC channel for this forum? i need help now.. and im am very confused atm..

---

### Post by jimmy the saint on 2009-01-19
nobody is going to be able to help you if you are not more specific about the situation.  The reason that I asked for that information is because the solution will depend on the answer.

---

### Post by Noblacktie on 2009-01-19
Don't panic.

Don't start deleting things willy-nilly.

To get XP back, boot-up with your XP installation/recovery CD.

Get to a command prompt and type 

```
C:\ fdisk /mbr
```

Make time to experiment before upgrading/changing software.

Never do it when you have a "need my computer today" situation.

---

### Post by Myx0.x3 on 2009-01-19
> **Noblacktie said:**
> Don't panic.

Don't start deleting things willy-nilly.

To get XP back, boot-up with your XP installation/recovery CD.

Get to a command prompt and type 

```
C:\ fdisk /mbr
```

Make time to experiment before upgrading/changing software.

Never do it when you have a "need my computer today" situation.


it says i have no hdd when i use the "r" in the windows menu...

---

### Post by Noblacktie on 2009-01-19
What 'r'?

What windows menu? 

Can you boot into Windows XP?

I was working on the assumption that all you have is a Grub4DOS prompt.

To boot using your XP CD, press the Function key listed for BOOT OPTIONS during BIOS POST and select your CD/DVD drive.

---

### Post by bapoumba on 2009-01-19
Threads merged.

---

