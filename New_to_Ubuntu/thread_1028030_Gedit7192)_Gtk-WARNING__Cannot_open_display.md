---
title: "Gedit:7192): Gtk-WARNING **: Cannot open display"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by Cambiar on 2009-01-02
Hi,

 When I booted I would just go into the command prompt instead of gnome, I would say that there was no resume image and I found the solution on the forums. However the instructions were to add the Busid of each of my graphics cards by running lspci and then editing xorg.conf and adding in the Busid.

I used lspci and got

02:00:0
03:00:0

but when i tried to use gedit to edit xorg.conf it replied with this:

(Gedit:7192): Gtk-WARNING **: Cannot open display

I tried to open it with nano but it was blank.

---

### Post by Tim Sharitt on 2009-01-02
Are you opening xorg.conf from the /etc directory or, if not, using the full path to open it?
```
sudo nano /etc/xorg.conf
```

---

### Post by adult swim on 2009-01-02
tim forgot part of the path, it is /etc/X11/xorg.conf

---

### Post by Cambiar on 2009-01-02
Yes I used
Sudo gedit /etc/x11/xorg.conf
And
Sudo nano /etc/x11/xorg.conf

---

### Post by scorp123 on 2009-01-02
> **Cambiar said:**
> Yes I used
Sudo gedit /etc/x11/xorg.conf First of all ... **[COLOR="Red"]Case matters![/COLOR]** "_x_11" and "**_[COLOR="Red"]X[/COLOR]_**11" are **_[COLOR="Red"]not[/COLOR]_** the same thing.

Secondly ... if you are on the terminal then there is no X11, hence the error "Gedit:7192): Gtk-WARNING **: Cannot open display" is correct, you can't use a GNOME program if there is no working GUI.

You will have to use text mode editors .... **nano, pico,** ... and if you know how to use it: **vim**.

---

### Post by Cambiar on 2009-01-02
Ok case sensative got it, that's probably also why nano just opened a blank page. Thanks for the help Ill be at my computer on the 3rd so I'll let you guys know!

---

