---
title: "run GNOME environment after login"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by Nervouswreck on 2009-06-26
Hopefully someone can explain this to me, because I thought I was a fairly competent UNIX user until I did this.

I installed Ubuntu 9.04 on a secondary desktop. I then decided that I wanted a straight command line bash interface so I unchecked GNOME from the startup services dialog in system/administration/services.

(Yes, I am an idiot. I could have just logged into a terminal session from the graphical login screen, but this is what I did.)

Unfortunately none of the other people who use this computer (my mother and sister, dad is a UNIX guru) can use the command line. Is there a way to start up the Gnome environment and it's various components after I log in? Alternatively, how do I edit the startup programs from the command line to include the various components of the gnome interface?

Thanks in advance.

---

### Post by Ru$$i@N on 2009-06-26
you can type in the console
```
startx
```
and GNOME should start. and from there you can toggle it back on in the startup sessions.

---

### Post by Nervouswreck on 2009-06-28
First of all, thanks a lot. I must have left my brain elsewhere that day.

Update: startx starts the Xwindows system which is good enough for most purposes. However, to change startup services or other things affecting login (including toggling GNOME back as a startup service) requires the Gnome display manager so you have to type
```
sudo gdm
``` at the prompt instead of startx.

---

