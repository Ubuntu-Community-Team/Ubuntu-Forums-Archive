---
title: "File  System shortcut"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Gtone on 2008-12-28
How could i add a File System shortcut on my desktop?
i am running ubuntu 8.04.1

---

### Post by jerome1232 on 2008-12-28
Well you can put a computer icon on your desktop like this

alt+f2; gconf-editor; run; Apps->Nautilus->Desktop->Check Computer Icon Visible, close.

Alternativly you could create a symbolic link

```
ln -s / ~/Desktop/filesystem
```

---

### Post by Kellemora on 2008-12-28
Hi Gtone

The easiest way is to go to the folder you want on your desktop, right click on it, then select "Make Link".
This will create a folder within the parent folder of where you are at.  Just copy this linked folder to your desktop, then go back and delete the one inside the parent folder that was just made.  Or if you can MOVE the linked folder to your desktop you won't have to go back and delete the second copy.

TTUL
Gary

---

