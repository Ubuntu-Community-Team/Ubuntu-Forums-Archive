---
title: "Trouble installing Ubuntu 10.10 32-bit"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by ntonline on 2010-12-02
Hey all,

I am running a machine that came with Windows XP preinstalled.  I've been having trouble with Windows performing very, very slowly; plus the audio on my machine sounds garbled.  Since I have been having so many problems, I decided to partition my hard drive to install Ubuntu to give it a try.  

I split my C: drive into two separate partitions.  There were three originally partitions, so now there are a total of 4 partitions.  My hard drive is an 80GB drive and allocated 35GB to my C: drive (for XP) and 35GB to my E: drive (for Ubuntu).  

I downloaded Ubuntu 10.10 from Ubuntu.com and burned the image onto disk.  I inserted the disk into my computer and restarted the machine.  The installation did not occur as expected when the machine started up.  I ended up having to install some software so the computer would recognize the disk on startup.  After installing this software, I restarted my machine again, and this time the installation of Ubuntu began.  During the install, at around 60 percent, the installation failed.  A message appeared stating something to the effect that the installation directories were not found.  At this point I attempted to install Ubuntu a second time, but the second install attempt failed at the same point and with the same message.  

Frustrated, I rebooted my computer and was greeted by the following error:

```
error: unknown filesystem.
grub rescue>
```Now my computer would not even boot Windows XP.  I am new to linux and  spent many hours trying to research this error and have not found anything that resolved this particular issue.

Whenever I enter a command at the grub rescue prompt I am told the command is an Unknown command.  The only command that is recognized is the "ls" command, which yeilds the following:

```
error: unknown file system.
grub rescue> ls
(hd0) (hd0, msdos6) (hd0, msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (fd0)
grub rescue>
```How do I fix this problem?  I'm trying to set up a dual boot option on my machine so I can access XP or Ubuntu.

Hardware:
Dell Dimension 3000
80GB hard drive
Windows XP
Intel Celeron processor

I can't get the exact specs because I don't know how to look them up from the command prompt and I can't get the machine to boot XP right now.

---

### Post by Rubi1200 on 2010-12-02
Hi and welcome to the forums :)

Boot the computer with a LiveCD and choose to try not install Ubuntu.

Click on the link at the bottom of my post and follow the instructions there to run the boot info script.

Post the results back here please.

Thanks.

---

