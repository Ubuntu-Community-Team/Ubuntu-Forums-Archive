---
title: "Places tab not working"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by Amockineuropa on 2010-11-24
This sounds a bit strange but I recently loaded Ubuntu 10.04 to my little Acer ONE. Everything SEEMS to work just fine EXCEPT for this one issue:

At the top bar I have listed Applications Places and System. Under Places I have listed 
Home
Desktop
Music
Video
Downloads
Computer
Network

When I click on anyone of these I get the following:

No images found in file://home/randall/documents at the top of this message it says:

Eye of GNOME Image Viewer

I get such a message for ANY of the files I attempt to open under PLACES tab. To access my files I have to go to Computer then Home then Randall then whatever file I want.

---

### Post by endotherm on 2010-11-24
right click on ANY folder (outside the places menu)
and select "Open with other Application". select "File Browser" or "Open folder". make sure the box labeld "Remember this setting..." is checked.

that should do you.

---

### Post by Amockineuropa on 2010-11-24
When I right click on any tab w/in PLACES I automatically get the above. 

Eye of GNOME Image viewer

then it has a big red bar that says No images found on 'file:///home/randall/desktop

---

### Post by Verbeck on 2010-11-24
> **Amockineuropa said:**
> When I right click on any tab w/in PLACES I automatically get the above. 

Eye of GNOME Image viewer

then it has a big red bar that says No images found on 'file:///home/randall/desktop

create a folder on the desktop then right click it and do what's posted above

---

### Post by Amockineuropa on 2010-11-24
No sorry that indeed worked. I initially misread your instructions. All is well thanks

---

### Post by endotherm on 2010-11-24
the manual fix for this if you prefer, is to open this file:
```
~/.local/share/applications/mimeapps.list
```
and edit it to remove all references to EOG.

---

### Post by Homer0988 on 2011-05-07
worked for me...

---

