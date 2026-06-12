---
title: "GnoMeni"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by Dobbie03 on 2009-09-28
How do I install this?

---

### Post by bruno9779 on 2009-09-28
There is no trace on the net of a program or package with that name

---

### Post by renkinjutsu on 2009-09-28
do you mean [this]("http://www.gtk-apps.org/content/show.php/GnoMenu+-+consolidated+menu+for+gnome?content=93056")?

There seems to be a readme in the downloaded file (according to the description) and it details the installation process

---

### Post by Dobbie03 on 2009-09-29
lol silly me, I meant GnoMenu.  Stupid fat fingers and not proof reading.

---

### Post by ankspo71 on 2009-09-29
Hi,
Did you get GnoMenu installed yet? The installation was quick and painless when I tried it. In case you didn't get it installed...

Extract the gnomenu archive on the desktop. Then open the terminal and type the following ```
sudo apt-get install python python-xdg python-cairo python-gconf python-xlib deskbar-applet
``` to make sure you have all of the dependencies installed. Then type in the terminal
```
cd Desktop/gnomenu
``` so that you will be working inside the directory you need to be in (required). Notice the capital "D" because it is case sensitive. Then type in the terminal ```
sudo make install
``` to install it. You will find it in your applets menu of the panel.

Normally installing packages requires doing the following:
**sudo apt-get install** <dependencies> 
**cd** <location of working directory>
**./configure**
**make **(or sudo make)
**sudo make install**
So GnomeMenu had easier instructions.

---

### Post by Dobbie03 on 2009-10-01
I cant get it to work.  But thanks for your help.

---

