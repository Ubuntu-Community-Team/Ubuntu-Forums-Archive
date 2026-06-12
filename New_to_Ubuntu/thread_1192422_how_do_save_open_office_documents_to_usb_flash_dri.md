---
title: "how do save open office documents to usb flash drive?"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by jonobe on 2009-06-20
When I go to save an Open Office document to usb, I can't seem to find where to save it - the USB drive is not obviously available. Is it hidden away somewhere not in my Home directory, or what?

 I am currently having to save to Home, and then use a file manager to copy and paste to the USB, but this is a long winded process.

I would appreciate it if anyone can tell me a quick way to save straight from Open office, if it's possible in Linux.

:???:

---

### Post by thegreenblob on 2009-06-20
Flash drives are usually mounted in somewhere in /media/ and not in your home directory. If you browse to /media in open office you should be able to find it.

Hope this helps. :)

---

### Post by oeyrvin on 2009-06-21
By me, using Dolphin, the name of my flashdrive even comes up last in the left menue...  :D

---

### Post by LewRockwell on 2009-06-21
maybe it has U3 on it?

[http://ubuntuforums.org/showthread.php?t=487746](http://ubuntuforums.org/showthread.php?t=487746)

[http://ubuntuforums.org/showthread.php?t=803809](http://ubuntuforums.org/showthread.php?t=803809)

[http://www.pendrivelinux.com/u3-uninstaller-for-usb-flash-drive/](http://www.pendrivelinux.com/u3-uninstaller-for-usb-flash-drive/)


the interwebs are full of distaste for U3 and those manufacturers who include it on their drives

you think they'd get the hint?

---

### Post by jonobe on 2009-06-30
I don't have U3 on it.  But when I go to Media, the USB directory is not there, I only see CDROM and CDROM0.

I can see the USB in Dolphin - it shows up as its own thing down the side fine.  But I don't want to have to go to Dolphin to save files, I want to save them directly from the program I'm using (obviously).

It is when I try to open or save a file from within a program such as Open Office, that I can't locate the USB file.

This really is annoying - if anyone has a workaround or something, i'd much appreciate it.

---

### Post by RiceMonster on 2009-06-30
> **jonobe said:**
> I don't have U3 on it.  But when I go to Media, the USB directory is not there, I only see CDROM and CDROM0.

I can see the USB in Dolphin - it shows up as its own thing down the side fine.  But I don't want to have to go to Dolphin to save files, I want to save them directly from the program I'm using (obviously).

It is when I try to open or save a file from within a program such as Open Office, that I can't locate the USB file.

This really is annoying - if anyone has a workaround or something, i'd much appreciate it.

Open up the usb drive with dolphin and see what it says the directory path is. Browse to there from Open Office.

---

### Post by jonobe on 2009-06-30
ok i've looked around.

I have found it as /media/disc now. 
It is now below cdrom and cdrom0, where before it wasn't.  Strange.   Why not ever before I don't know...? 

Thanks

---

