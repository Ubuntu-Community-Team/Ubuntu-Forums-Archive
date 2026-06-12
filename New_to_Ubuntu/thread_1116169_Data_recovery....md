---
title: "Data recovery..."
date: 2009-04-04
forum: New to Ubuntu
---

### Post by Icemanyurt on 2009-04-04
So my old laptop died awhile back, but I was able to salvage the hard drive by sticking it in an external enclosure.  While trying to copy all the files over, I got a message saying I can't copy the files because I don't have the permission...how do I get around this?

---

### Post by utnubuuser on 2009-04-04
Suppose you've tried going through gksu?

Alt+F2, then gksu, then nautilus.  This gets you into nautilus as root.

Or you might have to do a chmod to the effect of> sudo chmod 777 /dev/sda
or whatever the name of the drive is "sda", or "sdb", or "hdb".  
fdisk -l in terminal will get the right info.

---

