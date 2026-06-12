---
title: "How do I install gnome themes without GUI?"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by Buce on 2009-07-13
I working on getting a fluxbox-based desktop working on an install done off the Minimal CD, and gnome themes aren't working correctly for me. I installed both the [Darkilouche]("http://art.gnome.org/themes/gtk2/1285") and [Clearlooks-DarkLime]("http://art.gnome.org/themes/gtk2/1364") by extracting the contents to ~/.themes, but when I include them in my .gtkrc file, it only seems to partially apply the theme. The buttons on firefox, for instance, still have square corners, instead of the rounded ones depicted at the download pages. What else do I have to do to get the themes working?

---

### Post by RedSquirrel on 2009-07-13
Do you have the clearlooks engine installed? I usually install the **gtk2-engines** package or even **gnome-themes** and **gnome-themes-extras**, which will pull in gtk2-engines.

---

### Post by Buce on 2009-07-13
Perfect, that's exactly what I needed. Thanks a bunch!

---

### Post by RedSquirrel on 2009-07-13
> **Buce said:**
> Perfect, that's exactly what I needed. Thanks a bunch!
You are most welcome. Thanks for the tip about those two themes. I've been looking for something new. :D

---

