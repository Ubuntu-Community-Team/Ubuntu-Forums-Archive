---
title: "Equivilent of startup application on lubuntu"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-04-10
How do i run a script on startup on lubuntu, i can find a list of services that load up under preferences > desktop sessions manager, but its not editable, there must be a lubuntu equivilent to startup applications??

---

### Post by TeoBigusGeekus on 2011-04-10
Look in ~/.config/openbox
Isn't the autostart.sh file there?
That's where I put my startup scripts on my system, but I use openbox stand-alone, not lxde...

---

### Post by CaptainMark on 2011-04-10
no its not in there,

---

### Post by ~Plue on 2011-04-10
then you can edit the system-wide default script in /etc/xdg/openbox/autostart.sh 
or, copy the file  to ~/.config/openbox/ and then edit it

---

### Post by kosy on 2011-04-13
Trying also to start application automatically in lubuntu. This is too complicated...
Is there a way to install the startup application software like used in ubuntu so the startup applications can be edited easily?

---

### Post by kosy on 2011-04-13
Found out how to.
edited autostart file in /etc/xdg/lxsession/lubuntu/

Added:
@firefox
to the end of the file and it worked!
I am using v.10.10

---

### Post by melrokz on 2012-07-01
Is it really necessary to add @ before the startup command?
@firefox or firefox?

lxsession-edit does not seem to have an option to add startup applications. It will be great if that's implemented.

---

### Post by ubudog on 2012-07-01
Old thread closed.

---

