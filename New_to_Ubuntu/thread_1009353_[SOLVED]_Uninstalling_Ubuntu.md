---
title: "[SOLVED] Uninstalling Ubuntu?"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by JAJB92 on 2008-12-12
For several reasons, I need to go back to using Windows, and I'm running into some problems.

I have removed all of my Ubuntu partitions and used the Windows installation disc to format my hard drives for Windows, but I am unable to install Windows on to the hard drives because Windows apparently can't find a "suitable volume" or something.

I'm wondering if this is because I improperly removed Ubuntu or something?  I hope I can get some insight here.

---

### Post by Duck2006 on 2008-12-12
Some thing here may help.

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

You may have to restore your mbr to get win to read the drive.

---

### Post by zzHanks on 2008-12-12
Have you deleted the partitions, or did you make some file system?

---

### Post by theozzlives on 2008-12-12
boot on the Win CD go to recovery consol and type:

```
fdisk /mbr
```

then

```
fixboot
```

---

### Post by JAJB92 on 2008-12-12
> **Duck2006 said:**
> Some thing here may help.

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

You may have to restore your mbr to get win to read the drive.

I followed the tutorial particular to me, and when I tried to follow it, it said in terminal when I tried to install ms-sys: 
"E: Couldn't find package ms-sys"

---

### Post by Duck2006 on 2008-12-12
> **JAJB92 said:**
> I followed the tutorial particular to me, and when I tried to follow it, it said in terminal when I tried to install ms-sys: 
"E: Couldn't find package ms-sys"

Is this to fix the mbr?
If so this may help you can do it from the live cd of ubuntu.

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

---

### Post by JAJB92 on 2008-12-12
> **Duck2006 said:**
> Is this to fix the mbr?
If so this may help you can do it from the live cd of ubuntu.

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

This is what I had tried, but my terminal is unable to find "ms-sys".

---

### Post by Duck2006 on 2008-12-12
Did you download it to the Desktop? If so 

cd ~/Desktop 

To where the file is and try again.

---

### Post by Therion on 2008-12-12
Okay let's backup here for a minute.  You should be able to install from your Windows disk and, as part of that install process, repartition and reformat the drive.  

The fact that you can't get to that point tells me you may be trying to install Windows XP to a SATA drive from an install disk that is pre-Service Pack 1; which means there are no SATA drivers being loaded which is preventing Windows from seeing the available (SATA) hard drive.

Does any of that sound possible?  When you try to reinstall Windows from the install disc, what is the ACTUAL error message that you receive?  This doesn't sound like a GRUB/MBR problem, this sounds like a hardware recognition error in the Windows installer.

---

### Post by JAJB92 on 2008-12-12
> **Therion said:**
> Okay let's backup here for a minute.  You should be able to install from your Windows disk and, as part of that install process, repartition and reformat the drive.  

The fact that you can't get to that point tells me you may be trying to install Windows XP to a SATA drive from an install disk that is pre-Service Pack 1; which means there are no SATA drivers being loaded which is preventing Windows from seeing the available (SATA) hard drive.

Does any of that sound possible?  When you try to reinstall Windows from the install disc, what is the ACTUAL error message that you receive?

I can get the error message in a moment.

I know I'm trying to install Vista on a SATA drive.

---

### Post by Therion on 2008-12-12
> **JAJB92 said:**
> I can get the error message in a moment.

I know I'm trying to install Vista on a SATA drive.
It's possible I'm wrong about this being your specific problem *right now*; but if your drive is SATA, and your install CD does NOT have SP-1 on it, you WILL have problems with Windows not being able to detect the drive.

---

### Post by JAJB92 on 2008-12-12
When I went to get the error message for you, I managed to install Windows, interestingly.  Apparently it didn't like me creating partitions for it in their partition manager, so it worked when I didn't.

So I guess this is solved.  Thanks for the help, though. :)

---

### Post by Therion on 2008-12-12
Hey, whatever works!  

Glad things are working out for you.

---

