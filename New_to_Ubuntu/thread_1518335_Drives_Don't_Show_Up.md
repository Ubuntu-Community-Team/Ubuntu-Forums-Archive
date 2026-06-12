---
title: "Drives Don't Show Up"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by AnotherKevin on 2010-06-26
Hi all!

After a couple year hiatus, I'm back with Ubuntu...

Only problem at present is that I can't look at my CD/DVD.  It shows up on a file browser, but will not allow me to view the contents.  It's as if there is nothing there (there is).

Thanks!

Kevin

---

### Post by mapes12 on 2010-06-26
Have you put a CD/DVD in the drive? Ubu should normally detect the media and open a window asking how you want to open it.

---

### Post by xtremesupremacy3 on 2010-06-26
When you say that it shows up in file browser, do you mean when you click Places > Computer, or does it show up in any place on the left panel with an eject icon next to it?

---

### Post by AnotherKevin on 2010-06-26
When I open a file browser (Nautilus) it shows an icon (in the browser) for the drive, but it will not show me contents of the disk.  There is no desktop icon for any drive.  There are no desktop icons at all.

This is a new install of Ubuntu 10.4/64 bit.

Kevin

---

### Post by xtremesupremacy3 on 2010-06-26
Okay lets try something.

Open up your terminal (Applications > Accessories > Terminal) and type the following:

```
cd /media/cdrom0
```

After you hit enter and it doesn't give any errors type:

```
ls
```

Does that show anything?

---

### Post by AnotherKevin on 2010-06-26
Started showing all of a sudden.  It was like the CD was frozen or something.  It's a new machine...  Everything seems fine now.  

Appreciate the help!  :-)
:guitar:

---

