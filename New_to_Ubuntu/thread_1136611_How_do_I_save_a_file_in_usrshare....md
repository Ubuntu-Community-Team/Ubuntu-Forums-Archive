---
title: "How do I save a file in /usr/share/...?"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by zzzonked on 2009-04-25
I've discovered that my web space is at /usr/share/apache2/default-site/

Now I wanna save a .php file in there, but gedit won't let me. And I foresee this happening everytime I wanna save a file here, so what do I do now?

---

### Post by ninjapirate89 on 2009-04-25
You could save it on the desktop and use the terminal to move it into the folder you need.

---

### Post by fahadsadah on 2009-04-25
You could move your web space if you like, but otherwise, start gedit as root.

---

### Post by befana on 2009-04-25
zzzonked,
Go to Synaptic and install nautilus-gksu - that will let you to open Nautilus as root (right click on a folder, and Open as Administrator) and to save or delete files. But be very, very carefull when working with root privileges!!!

---

### Post by zzzonked on 2009-04-25
> **fahadsadah said:**
> You could move your web space if you like, but otherwise, start gedit as root.

This seems like a better long term solution. How do I stars gedit as root?

---

### Post by Didius Falco on 2009-04-25
> **zzzonked said:**
> This seems like a better long term solution. How do I stars gedit as root?

Open Terminal and type ```
gksudo gedit
```.

To eliminate the Terminal step, open your menu, find Gedit and right-click it and add it to the desktop or a panel, your choice.

then right-click the created launcher and  open the Properties. Add ```
gksudo
``` to the front of the "Command" line.

Personally, I recommend placing it on the Desktop, and changing the name to something like "Edit with Root" so you don't accidentally open it when you don't need root privileges.

I treat root like a gun - it's the people that get cocky and careless that wind up accidentally shooting someone.

---

