---
title: "Disk Utility (explanation?)"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by cabo82 on 2010-12-08
Hi recently installed Ubuntu Desktop on my laptop (Inspiron Mini 1012) I installed it using the Windows installer, which created a partition (presumingly - why?) after reboot it showed me Windows 7 and Ubuntu options, after selecting Ubuntu it installed it.

I want to install some applications in Ubuntu but i don't know how much space i have available in the Ubuntu partition(?) since at no point it asked me to define a partition.

Can anyone please explain me how to read the information in the Disk Utility? - Screen shots attached. 

Thanks.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=177857&stc=1&d=1291851918[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=177858&stc=1&d=1291851918[/IMG]

---

### Post by ExileSith on 2010-12-08
You can see how much space you have available simply by opening any folder (Places-> Home Folder, for example) and looking at the bottom of it, you'll see something like "Free Space: xxgb" or similar. At least thats the way I do it xD
As for the disk utility, im no expert, but I dont think theres anything there that needs explaining...

---

### Post by cabo82 on 2010-12-08
I know but the thing is that the laptop came with a 160GB drive and as you see in the picture there is the 160GB drive and also a 18GB file.

Is there a way to make this file/partition bigger?

---

### Post by ExileSith on 2010-12-08
There is a way to resize partition, by booting with a live cd and using partitionsomething (cant recall the name right now), but thats for someone with more experience to explain, mostly because I dont know about that root.disk, as it is not present in mine... and im quite new in this just as you xD

---

### Post by cabo82 on 2010-12-08
Thanks, its the first time i have installed Linux or i should say started installing Ubuntu within windows not from a CD (since my netbook has no CD drive,) so seen this Hard drives/ devices threw me off. If it was a pure Linux system i wouldn't be worried cus i would know how/have an idea of much space i have.

---

### Post by libssd on 2010-12-08
If you have just installed Ubuntu, and have not invested any effort in customization, etc., just re-install, choose the manual partitioning option, then delete the partition Ubuntu is currently installed in. Then shrink the Windows partition by the amount you want to grow the Ubuntu partition (16gb is actually plenty of room until you start adding pictures and music, but 32gb is a nice size). Unlike Windows, Ubuntu isn't a disk hog.

**Good reference**: [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by oldsoundguy on 2010-12-08
the program to use is GParted.  It is under system> administration.
The first thing that will have to be done is to SHRINK the Windows partition .. that will guarantee that nothing in that partition gets borked.

Why I hate DUAL booting!  Disk management that is not needed under normal circumstances .. much prefer to have TWO CPU's and share the display, keyboard and mouse and audio via a switch!!

---

### Post by mick222 on 2010-12-08
You have installed Ubuntu inside Windows (wubi) Thats why Ubuntu shows as a file. I'm not sure if you can resize it but think you should have had that option on install. 
  If your mainly using ubuntu it would be better to install in it's own partition, you could do this by installing unetbootin and creating a bootable flash drive or memory card and installing from that.
  DO NOT attempt to use gparted on a wubi install Ubuntu is only a file inside windows.

---

### Post by cabo82 on 2010-12-08
> **libssd said:**
> If you have just installed Ubuntu, and have not invested any effort in customization, etc., just re-install, choose the manual partitioning option, then delete the partition Ubuntu is currently installed in. Then shrink the Windows partition by the amount you want to grow the Ubuntu partition (16gb is actually plenty of room until you start adding pictures and music, but 32gb is a nice size). Unlike Windows, Ubuntu isn't a disk hog.

**Good reference**: [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

cool thanks for the link, i currently downloaded the Ubuntu Netbook edition onto my flash drive since thats the only way i can set up this netbook.

[QUOTE=oldsoundguy]the program to use is GParted. It is under system> administration.
The first thing that will have to be done is to SHRINK the Windows partition .. that will guarantee that nothing in that partition gets borked.

Why I hate DUAL booting! Disk management that is not needed under normal circumstances .. much prefer to have TWO CPU's and share the display, keyboard and mouse and audio via a switch!![/QUOTE]

I'm not a big fan of dual boot either but i want to test Ubuntu and play around before i decide to delete windows 7 from it. I'll look it up and play around with GParted if not ill do it the long way :p

I need more space cus i want to install or play with some free music applications and others that i saw were free and seem comparable to payed Windows applications.

---

### Post by cabo82 on 2010-12-08
> **mick222 said:**
> You have installed Ubuntu inside Windows (wubi) Thats why Ubuntu shows as a file. I'm not sure if you can resize it but think you should have had that option on install. 
  If your mainly using ubuntu it would be better to install in it's own partition, you could do this by installing unetbootin and creating a bootable flash drive or memory card and installing from that.
  DO NOT attempt to use gparted on a wubi install Ubuntu is only a file inside windows.

Wow thanks, lol i was about to boot up my netbook hehehe. yea odd it didnt prompt me for some reason. I already have the drive for the netbook version of Ubuntu, i read that its the same just with a different view and that i can log off of it and see it normally?

---

### Post by mick222 on 2010-12-08
Your wubi install will be fine you should be able to access any files on you windows partition and import them to  any application you want to use.

---

### Post by cabo82 on 2010-12-08
> **mick222 said:**
> Your wubi install will be fine you should be able to access any files on you windows partition and import them to  any application you want to use.

so I could save what ever i do in wubi in a folder inside windows? that would be nice since apparently i have what 14/16GB free in wubi?

---

### Post by libssd on 2010-12-08
The WUBI catch was a good one -- in my opinion, running Ubuntu under Windows is asking for trouble. Trash WUBI, and do a real install. Depending on the version of Ubuntu you are installing, gparted may not be automatically installed, which is why I suggested the re-install Ubuntu approach, which depends on the fewest assumptions about pre-existing knowledge of Linux.

---

### Post by mick222 on 2010-12-08
wubi works well for a while it is a useful tool for trying Linux and maybe gaining a bit of knowledge before doing a full install. I would say use it until you are comfortable with Ubuntu then do an install with a separate /home partition.

---

### Post by cabo82 on 2010-12-09
Thanks guys, yea i wanted to try and see some programs before officially installing it and see how fast it would run on the netbook, thanks again :)

---

### Post by oldsoundguy on 2010-12-09
> **cabo82 said:**
> Thanks guys, yea i wanted to try and see some programs before officially installing it and see how fast it would run on the netbook, thanks again :)

Whether you run in WUBI or in a VM or from the CD   .. judging just how fast a program will run when run in a stand alone Linux is next to impossible.  You are dealing with an additional layer between the program and the operating system.

---

### Post by bcbc on 2010-12-09
> **oldsoundguy said:**
> Whether you run in WUBI or in a VM or from the CD   .. judging just how fast a program will run when run in a stand alone Linux is next to impossible.  You are dealing with an additional layer between the program and the operating system.

I think you mean an additional layer between the OS and the hardware. However, wubi is not a vm. It uses a loop device (virtual disk) instead of a block device (partition). It is slower than a direct install, but not noticeably (in my experience... but depends on the type of usage - as it automatically syncs writes to 'disk') and much faster than a vm.

Wubi has had some major issues with grub lately. If you continue to use wubi, do not update packages grub-pc and grub-common (they are listed under "Recommended" updates in Update Manager.) Otherwise you'll need this wubi megathread to fix the fallout: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by mick222 on 2010-12-09
> **oldsoundguy said:**
> Whether you run in WUBI or in a VM or from the CD   .. judging just how fast a program will run when run in a stand alone Linux is next to impossible.  You are dealing with an additional layer between the program and the operating system.

True i was only trying to let the op get the hang of Ubuntu before installing. I love linux in all it's guises from mint to arch sorry not brave enough for gentoo . But think it is good to learn about partitioning if you are gig to dual boot . I sometimes  have up to 4 OS on one hard drive

---

