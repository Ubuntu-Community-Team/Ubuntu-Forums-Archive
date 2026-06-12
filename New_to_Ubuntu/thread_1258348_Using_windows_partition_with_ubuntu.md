---
title: "Using windows partition with ubuntu"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by whizzard on 2009-09-04
Hello,  I installed ubuntu using Wubi.  I have looked in the file manager for any "external" drive to mount or any sign of the files that I access from the NTFS part of the drive that I used to store files and folders on when using windows.  I would like to be able to use that partition for storage and such because my install of ubuntu is not very large. 

I downloaded NTFS tools, but dont see anything to mount with it.  I also don't know how to access the root folder or root permissions. I really need access to those files and that portion of the disk.  I used Wubi because I don't own a USB drive and liked that I can dual boot and never need to hook a drive up to my mini pc.

The OS runs very nice on this HP-Mini netbook.  I would love to use it all the time but need access to my old disk (read and write)

---

### Post by Paqman on 2009-09-04
Your Windows filesystem should be at /host, and IIRC there should be a link  to it in your "Places" menu if you're using the default Gnome desktop.

---

### Post by cwsnyder on 2009-09-04
When you install under WUBI, you don't have a separate partition for Windows and Ubuntu.  Ubuntu is simply installed on a folder of the Windows partition, and as such the Windows partition is already mounted.  It has been a while since I mounted a WUBI install to test it, but I seemed to remember using Nautilus (Places), I could go fairly easily to the C:\ folder area (which is different from the / root folder).

---

### Post by Windows Nerd on 2009-09-04
> **cwsnyder said:**
> When you install under WUBI, you don't have a separate partition for Windows and Ubuntu.  Ubuntu is simply installed on a folder of the Windows partition, and as such the Windows partition is already mounted.  It has been a while since I mounted a WUBI install to test it, but I seemed to remember using Nautilus (Places), I could go fairly easily to the C:\ folder area (which is different from the / root folder).

You should be able to find it under the Places>xxGb Media menu as well. That and "My Computer" 

Scott

---

### Post by whizzard on 2009-09-04
Thanks so much!  I found it under /host.  I unfortunately have a whole new problem.  The intel HD audio device on my laptop will not playback sound.  I checked all volume control and it is all un-muted.  There is no sound from external speaker at all but the headphone jack makes a little static. I am currently looking into any fixes and may need to make a new thread.

---

### Post by sailthesea on 2009-09-04
Have a look here for a guide on getting multimedia support installed 

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
:)

---

