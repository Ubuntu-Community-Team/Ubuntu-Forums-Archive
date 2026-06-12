---
title: "Samba Setup"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by User X on 2008-12-31
I have a dual boot setup with Windows XP and Ubuntu 8.04 LTS.  I have two drives in my machine, a 40Gb Ubuntu drive and a 200Gb Windows NTFS drive.  I would like to share the 200Gb drive over my network with My Windows XP laptop, as well as share my HP Printer.  The Printer works with Ubuntu through CUPS.  Is there a writeup out there that tells how to configure and set up Samba to share over a windows network?  I searched but didn't find much...  Thanks.

---

### Post by billgoldberg on 2008-12-31
I have one, but it doesn't include the printer part.

[http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/](http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/)

---

### Post by User X on 2008-12-31
Hey, thanks billgoldberg, that seems pretty easy.  I have one question though, is Nautalis the GUI interface that comse up when I go to Places-> System???  And when I run that as root user will I be able to drag and drop things that I normally cannot because I do not have permission?  Thanks again!

Edit: I guess thats two questions...

---

### Post by albinootje on 2008-12-31
> **User X said:**
> I have one question though, is Nautalis the GUI interface that comse up when I go to Places-> System???  And when I run that as root user will I be able to drag and drop things that I normally cannot because I do not have permission? 

Nautilus is indeed the default filemanager in Ubuntu.
And this will let you access your external drive :
```

gsku nautilus

```

---

### Post by User X on 2008-12-31
Thanks albinootje!  I'll try this when I get home.

---

