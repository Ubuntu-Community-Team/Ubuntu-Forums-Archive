---
title: "Catastrophic failure..."
date: 2010-12-06
forum: New to Ubuntu
---

### Post by ppk on 2010-12-06
Just tried to install Ubuntu 10.10 on my machine. I used the installer's partitionner to partition my free space and install into it, leaving my vista partition untouched. The installer hanged at the keyboard language selection screen for over an hour and so I was forced to kill it. Now though, the computer refuses to boot. It just says this :

GRUB loading.
error: unknown filesystem
grub rescue (command prompt to write into, but I have no idea what to do)

Even though I understand killing the installer messed up everything, the windows partition should be unscathed, so why is it not booting with it?

---

### Post by CharlesA on 2010-12-06
Boot off a Vista CD and run a boot repair, to fix the MBR.

---

### Post by ppk on 2010-12-06
It didn't ship with a vista CD. All I've got is a backup partition to reinstall from, which would be fine if I could boot something up.

---

### Post by bananas4370 on 2010-12-06
> **ppk said:**
> It didn't ship with a vista CD. All I've got is a backup partition to reinstall from, which would be fine if I could boot something up.

Download one of the ISO images at [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

This is not an installation disk.

After you have burned the image to a CD, you'll be able to boot off it to repair the Vista boot. [Read this step by step guide]("http://www.bleepingcomputer.com/tutorials/tutorial148.html").

Cheers
Patrick

---

### Post by CharlesA on 2010-12-06
If you could borrow a Vista or 7 CD, you could fix the MBR.

I don't know how to do it otherwise.

---

### Post by ppk on 2010-12-06
Okay I'm downloading the repair disk right now... I'll let you know if I run into any problems.

---

### Post by wilee-nilee on 2010-12-06
> **ppk said:**
> Okay I'm downloading the repair disk right now... I'll let you know if I run into any problems.

Here is the drill with the download disc to just reload the mbr.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr**  
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by ppk on 2010-12-06
> **wilee-nilee said:**
> Here is the drill with the download disc to just reload the mbr.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr**  

That worked. Cheers :D

---

### Post by CharlesA on 2010-12-06
Don't forget to mark the thread as solved from thread tools. :)

---

### Post by Kixtosh on 2010-12-06
> **CharlesA said:**
> Don't forget to mark the thread as solved from thread tools. :)Just in case you haven't noticed, the **[COLOR="Red"]Thread Tools[/COLOR]** are shown in red, on the right hand side of your screen, right above your very first post at the top of the thread.

---

