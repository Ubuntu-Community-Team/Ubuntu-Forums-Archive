---
title: "cant find installed application"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by UncleAlan on 2010-10-11
I am using Ubuntu 10.04.1. I have installed qcad using the software Centre and it says it was installed. However I cant find where as it isnt showing up in any of the application sections. I had a similar thing a long time ago with 9.10 and had to type in a command but I cant remember what.

Alan

---

### Post by Hippytaff on 2010-10-11
Found this on another thread
> **camporter1 said:**
> Just right-click on your menu at the top, then select edit menu.

GO to the graphics section, then add a new item, and type in the command  for the program and it's name. The icon for it is probably floating  somewhere inside /usr

worth a punt

---

### Post by emoguitarist06 on 2010-10-11
Have you tried ALT+F2 and typing qcad or looking at list of known aps?
Or the terminal?
Once you find where it's at you can right click applications and add it wherever you like

---

### Post by UncleAlan on 2010-10-11
This nearly worked. Tried that but I dont know what the command is !!

---

### Post by UncleAlan on 2010-10-11
This sort of worked. Tried a couple of things. in Terminal I just typed qcad and it opened. another time I tried locate qcad and I got a list of stuff
alan@alan-desktop:~$ locate qcad
/usr/bin/qcad
/usr/lib/mime/packages/qcad
/usr/share/doc/qcad
/usr/share/doc/qcad/README
/usr/share/doc/qcad/changelog.Debian.gz
/usr/share/doc/qcad/copyright
/usr/share/man/man1/qcad.1.gz
/usr/share/menu/qcad
/usr/share/pixmaps/qcad.xpm
/var/cache/apt/archives/qcad_2.0.5.0-1+090318-2_i386.deb
/var/lib/dpkg/info/qcad.list
/var/lib/dpkg/info/qcad.md5sums
/var/lib/dpkg/info/qcad.postinst
/var/lib/dpkg/info/qcad.postrm
alan@alan-desktop:~$ 

This doesnt mean much to me at the moment but we are getting closer. Does this message help you?

---

### Post by Hippytaff on 2010-10-11
look into grep - search command in the terminal

[https://help.ubuntu.com/community/grep](https://help.ubuntu.com/community/grep)

---

### Post by UncleAlan on 2010-10-11
HOLD IT !!!!!

BY jingle I have it working, well it seems to. I tried The reply from Hippytaff again and was inspired to try again. Under name AND command I entered qcad and now I have it under applications - graphiscs and I can open it and use it. 
THANKS Both, I learnt something there.
ALAN

---

### Post by Hippytaff on 2010-10-11
happy days - remember to mark the thread as solved in the thread tools at the top of the page :-)

---

