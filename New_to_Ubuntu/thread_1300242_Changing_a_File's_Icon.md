---
title: "Changing a File's Icon"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by Don Bowen on 2009-10-24
What determines the icon for any given file type?  How can I change it?

---

### Post by MrWES on 2009-10-24
> **Don Bowen said:**
> What determines the icon for any given file type?  How can I change it?

right mouse click on the file; then properties. From there click on the current icon located in the upper left hand corner. Most icons are located in /usr/share/icons -- select the one you want.

Bill

---

### Post by Don Bowen on 2009-10-25
> **MrWES said:**
> right mouse click on the file; then properties. From there click on the current icon located in the upper left hand corner. Most icons are located in /usr/share/icons -- select the one you want.

Bill
wow...overwhelming... I found all the icons, and they're scattered over a bunch of folders!
Is there anyway to change an Icon back to it's default... I changed an icon on one file, and I don't know how to get it back to what it was!  

Is it possible to change the default icon for all .mp3 files or do you have to do them one at a time?  (I hope not!)

---

### Post by abhiroopb on 2009-10-25
There is a button that says "Revert"

---

### Post by Don Bowen on 2009-10-25
> **abhiroopb said:**
> There is a button that says "Revert"
thank you.  that worked nicely.

---

### Post by CatKiller on 2009-10-25
> **Don Bowen said:**
> What determines the icon for any given file type?

The icon theme. It will be an appropriately named/sized image in either ~/.icons/<*themename*> (for per-user themes) or /usr/share/icons/<*themename*> (for system-wide themes). It will be under <*icon-size*>/mimetypes.

> How can I change it?

Change theme, change that icon in the theme, or for one particular file you can change the way that file is displayed through Nautilus' metadata, as has already been described.

---

