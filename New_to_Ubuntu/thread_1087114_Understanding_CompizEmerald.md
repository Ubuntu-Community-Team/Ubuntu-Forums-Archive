---
title: "Understanding Compiz/Emerald"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-04
Okay, so let's see if I get this right.

Compiz fusion gives Ubuntu (Gnome) those cool effects.

Then there are different Window Decorators, such as Emerald which is another theme addon system (In emerald format) for Compiz?

But, nor compiz or emerald alters the control bar graphic. This is done in appearance?

Clear me up if this is not all right, interested to know how my ubuntu learning is going lol

---

### Post by linuxisevolution on 2009-03-04
> **Gp. said:**
> Okay, so let's see if I get this right.

Compiz fusion gives Ubuntu (Gnome) those cool effects.

Then there are different Window Decorators, such as Emerald which is another theme addon system (In emerald format) for Compiz?

But, nor compiz or emerald alters the control bar graphic. This is done in appearance?

Clear me up if this is not all right, interested to know how my ubuntu learning is going lol

Thats correct. Gnome uses metacity if your not using compiz. Metacity is a window manager like openbox, blackbox, fluxbox, dwm, etc. You can even replace Gnome with a window manager if you like things minimalist :D

---

### Post by Gp. on 2009-03-05
and how do I do that? lol

---

### Post by cwsnyder on 2009-03-05
You can go to System >> Administration >> Synaptic in the menu system, then search for Window Manager

---

### Post by Blåbär on 2009-03-05
I don't want to hijack the thread here, but...

Compiz is a window manager aswell, right? So, what's the line of actions to get it to "load"/"use" emerald themes?

I'm somewhat confused about this setup aswell.. Shouldn't I be able to use  emerald under metacity?

---

### Post by SunnyRabbiera on 2009-03-05
Compiz is the desktop effects and emerald is the window decorator for Compiz.
By default though compiz uses metacity another decorator and emerald is a neat add on for it.

---

### Post by Gp. on 2009-03-05
and what exactly is GTK?
I'm a bit confused on GTK.

---

### Post by cwsnyder on 2009-03-06
GTK, as I understand it is the Gnome application programming interface (also known as an API) which defines how programmers access the Gnome libraries and how to use windows in a way in which the 'themes' selected by Gnome (or Compiz on Gnome) propegate across all applications.  This includes color selection, fonts used in menus and headers, icon placement, maximize/minimize/close tools, etc.

KDE uses the QT3 (for KDE 3.x) or QT4 (for KDE 4.x) toolkit to do the same thing in KDE, and XFCE uses the GTK (metacity) interface as well.  That is why KDE apps sometimes look strange if not all of the KDE libraries are loaded, and why, when you go to XFCE, many of the same applications from Gnome are selections on the menus.

---

