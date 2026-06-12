---
title: "What is my version of GTK2?"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by resander on 2009-06-26
I need to know the version of GTK2, i.e. the graphics system underlying GNOME, because I want to install a recent version of Glade that may depend on the version number. It may want a more recent version of GTK than I have.

How can I find out about the GTK version on my PC?

---

### Post by WRDN on 2009-06-26
You can find the version information for all gtk items installed using the command:

```
dpkg -l | grep gtk
```

Note, it is a lowercase L, not a number 1.

---

### Post by dnairb on 2009-06-26
System --> About Gnome

The version is displayed bottom left.

---

