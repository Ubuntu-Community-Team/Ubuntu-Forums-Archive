---
title: "Failed to load module libcanberra-gtk-module.so"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by Omegaham on 2009-09-22
Hello again guys,

I installed PuTTY with the apt-get install function, but whenever I try to use it, it tells me,

```
mike@mike-desktop:~$ putty

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

```It then continues like normal.

This isn't a serious problem, but it's annoying to get nagged with an error message every time I want to play Nethack. Any help would be appreciated. Thanks.

---

### Post by ~sHyLoCk~ on 2009-09-22
Search in synaptic for that and install it.

---

### Post by Omegaham on 2009-09-23
It says it's already installed; I reinstalled it, and still have the same problem. :(

---

### Post by lebe0024 on 2009-10-23
For me I deleted all my gtk rc files/folders and the problem still existed.  Then I found out that GTK apps load any modules in your GTK_MODULES environment variable.  so I did an "unset GTK_MODULES" and that did the trick.

---

### Post by OrangeVixen on 2009-10-25
That is awesome, you deserve a commendation for finding that!! Do you know how many threads are out there with this problem??!?!??! :D

Now the next thing is, where do we set it up so that GTK_MODULES is not set in the first place? I'm assuming its in some bashrc config somewhere, does anyone know where it is?

---

### Post by wd5gnr on 2009-11-27
> **OrangeVixen said:**
> That is awesome, you deserve a commendation for finding that!! Do you know how many threads are out there with this problem??!?!??! :D

Now the next thing is, where do we set it up so that GTK_MODULES is not set in the first place? I'm assuming its in some bashrc config somewhere, does anyone know where it is?


Have a look in /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules

You can make the file nonreadable (sudo chmod 000 52libcan* ) or edit it to suit.

---

### Post by allCuExpMa on 2009-12-04
Thanks a lot "lebe0024" works like a charm.....was looking for a solution for ages....
T[m]

---

