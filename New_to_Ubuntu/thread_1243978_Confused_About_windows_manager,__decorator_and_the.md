---
title: "Confused: About windows manager,  decorator and themes."
date: 2009-08-19
forum: New to Ubuntu
---

### Post by sumantri_84 on 2009-08-19
Hi, i am using ubuntu version 9 and I am interested in trying something new in ubuntu version 9. 

I am totally confused about the windows manager , windows decorator, and the themes.


Below are the list that i search that have similar function to each other: Which of these features is best to use in Ubuntu version 9?

1)Compiz Fusion and Beryl,

2)Compiz, Emerald, metacity ( If i am not mistaken, i know that Emerald is no longer providing the update, so i thinks emerald is not the best to use as theme in version 9)

3)Gnome, Gnome Do, Gnome  3,Gnome Shell

---

### Post by Merk42 on 2009-08-19
Lot of things listed there so I'll try to sum it up, otherwise you can search those individual items.
Compiz / Beryl (now Compiz Fusion) Basically the specially effects you often see, the wobbly windows, the cube, etc.

GNOME is the desktop environment for Ubuntu (Kubuntu used KDE, and Xubuntu used Xfce).  The current version of GNOME with Ubuntu is 2.26. The desktop environment is basically the top and bottom bar, and how menus are layed out.

Metacity is the default window manager for GNOME


GNOME Do, is simply an application.
GNOME 3, is the next major version of GNOME
GNOME Shell is one of GNOME 3's components. It is scheduled to replace both Metacity and Compiz Fusion.

---

### Post by mcduck on 2009-08-19
**Compiz** and **Metacity** are window managers. Basically window anager's purpose is to put your running programs into windows, draw frames around those windows and allow you to move them around, minimize them and so on. Compiz does a bit more than that, it also handles alpha compositing (for transparency) and loads of other cool effects.

When you enable the desktop effects in Ubuntu your window manager changes from Metacity to Compiz. There is no Beryl any more, it was a fork of Compiz project, but the two merged back together.

**Emerald** is a window decorator. Unlike other window managrs, Compiz doesn't draw the window borders itself, instead it's able to use different plugins to handle that task. The default setup in Ubuntu uses Gtk-window-decorator, which allows using the same themes that Gnomes own window manager, Metcity, uses. Emerald is just an alternative to that, allowing more transparency effects and including it's own graphical tool for managing and editing it's themes.

**Gnome-Do** is just an extra application that can be used to launch programs etc, much like Quicksilver on OSX, if you've ever used that.


Which ones to use? Use the ones you like most. :D

---

### Post by 3rdalbum on 2009-08-19
Compiz and Metacity are window managers. Forget Beryl, it doesn't exist anymore.

Emerald is a window decorator - it controls the theming of your window borders when running Compiz.

Gnome is a desktop environment. Gnome-Do is a utility program. Gnome-shell is a new (in development) interface for the Gnome desktop environment. They don't have anything to do with themes.

To what end do you want to know this stuff?

---

### Post by Viva on 2009-08-19
Quoting myself from another thread,

> Metacity themes change your window frame(title bar).
GTK themes change your window controls. To put it simply, they change everything except your title bar, icons and pointer.
Icon themes change your icons.
Emerald themes do the same as metacity themes, but they require compiz(desktop effects) and emerald running. You install them using emerald theme manager. They are often better looking and more flexible than metacity themes. They can add effects like title bar transparency.
x11 mouse themes change your pointer.

---

