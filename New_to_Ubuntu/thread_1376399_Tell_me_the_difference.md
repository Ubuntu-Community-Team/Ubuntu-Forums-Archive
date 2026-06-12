---
title: "Tell me the difference"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by wirate on 2010-01-09
X, Gnome, Metacity, Gtk, Compiz. Tell me the difference and what each one does.
Thanks

---

### Post by x33a on 2010-01-09
X is a windowing system. it provides the framework for running graphical applications.

Gnome is a desktop environment. metacity is the window manager for gnome. gtk is a toolkit for creating graphical interfaces, and compiz is a compositing manager, which produces all the cool effects such as cube, wobble etc.

you can find detailed information on all of these here:

[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

[http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)

[http://en.wikipedia.org/wiki/Metacity](http://en.wikipedia.org/wiki/Metacity)

[http://en.wikipedia.org/wiki/Compiz](http://en.wikipedia.org/wiki/Compiz)

[http://en.wikipedia.org/wiki/GTK%2B](http://en.wikipedia.org/wiki/GTK%2B)

---

### Post by SecretCode on 2010-01-09
Seen another way, X underpins all of these. Without X, you just have a command-line console. 

gtk is a programming toolkit for the bits and pieces ("widgets") that enable you to do useful things with X. An alternative to gtk is qt - you only need one of these but you can mix them.

Metacity is a window manager. Compiz is a compositing window manager. You can switch between them (e.g. using the ccsm 'compiz config settings manager' package). There are lots of other window managers out there.

Finally, GNOME is a desktop environment, built on gtk, using metacity (with the option of compiz) and including tons of utilities and applications. KDE is another desktop environment, as used in Kubuntu; it uses the qt toolkit. And there are others.

---

