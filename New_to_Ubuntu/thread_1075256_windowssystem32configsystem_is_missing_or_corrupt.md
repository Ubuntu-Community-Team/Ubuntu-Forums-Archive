---
title: "windows\system32\config\system is missing or corrupt"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by acidburns on 2009-02-20
hi will ubuntu live cd will solve my problem regarding my notebook wont boot up a message appears which says" windows\system32\config\system is missing or corrupt" ..the recovery cd that came with the notebook wont work... help please or at least google the message that appears on screen..so ill know what to do 

thanks

---

### Post by ibizatunes on 2009-02-20
Boot to a xp cd, drop into the recover mode and type fix /mbr
and irgnore the warnings, that will allow xp to boot
then boot to ubuntu and you will need to recover your grub loader
If you dont have a xp cd, you could always go 100% ubuntu ;-)

---

### Post by mikewhatever on 2009-02-20
> **acidburns said:**
> hi will ubuntu live cd will solve my problem regarding my notebook wont boot up a message appears which says" windows\system32\config\system is missing or corrupt" ..the recovery cd that came with the notebook wont work... help please or at least google the message that appears on screen..so ill know what to do 

thanks

No it will not. Ubuntu is not a recovery tool for Windows, and frankly, you should ask at a Windows related forum. Best of luck.

---

### Post by egalvan on 2009-02-20
> **mikewhatever said:**
> No it will not. Ubuntu is not a recovery tool for Windows, and frankly, you should ask at a Windows related forum. Best of luck.

Shame on you, mikewhatever. 

How many times have LiveCD's been touted as Windows recovery tools? ;)

---

### Post by 3rdalbum on 2009-02-20
I'm no Windows expert, but my understanding of the error is that it means "It's time to reinstall Windows".

An Ubuntu live CD can be helpful for fixing some Windows problems, but this isn't one of them. And Ubuntu is designed as an operating system in its own right, not just as a Windows-fixer; but I understand that you already know that.

---

### Post by DaveLH on 2009-02-20
> **3rdalbum said:**
> I'm no Windows expert, but my understanding of the error is that it means "It's time to reinstall Windows".


If %SystemDrive%\windows\system32\config\system is the problem, a full reinstall is probably not necessary, just a "repair" install, which will retain personal user files and settings and installed programs.  But it usually only works using a full-fledged, bona fide Windows XP install CD, not OEM disks that come with proprietary systems (e.g. laptops).  So if you want to do the repair yourself and not take your system into the repair shop, you need to get a hold of a real Windows install disk first off.

Since there's a feeling (probably justified) that this issue is off-topic, I'll stop here.  If you Google "windows\system32\config\system" you will find pages that give steps for fixing the problem, once you have a true Windows XP Install Disk...

---

