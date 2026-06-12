---
title: "gnome, compiz, GTK+  etc..."
date: 2008-12-28
forum: New to Ubuntu
---

### Post by FM101 on 2008-12-28
So what exactly are these?
My dell mini 9 came with ubuntu with gnome.
What do I get with gnome?  What kind of desktop stuff does it give me?  That did not come with ubuntu?
There is a cool thing where you can shake the windows.  What do you add in to get that?

---

### Post by midnightfox2 on 2008-12-28
Gnome is the desktop environment of ubuntu.

To get the shaky windows and a lot of other eyecandy you have to install compiz fusion. Just type compiz in the add/remove software search box and choose the first two and the fourth.

After installing go to system->preferences and set compiz up
That might take a long time cause there are a lot of settings to set up.

---

### Post by Dedoimedo on 2008-12-28
Hello,

You have asked a lot of questions that do not have simple answers:

1. Unlike windows, in linux, the desktop environment (GUI) and the kernel are separate. This means that you can use any which desktop manager on any which kernel. These managers have different names.

Some of these are gdm, kdm, fvwm etc. gdm stands for gnome desktop manager and it is built using the gtk+ framework, which is written in c.

Another very popular desktop manager is KDE, which uses the qt framework, which is, if I recall correctly, written in python and c++.

The desktop manager is more than just the desktop itself, it's an entire collection of applications, fonts, looks etc. So you get a certain set of applications with gnome that you would not normally see with other desktop managers.

Some apps can be used with different desktop managers, provided the right libraries are used on the system. This allows the flexibility of running kde or gnome apps on top of gnome and kde desktops any which way, for instance.

2. Now, in addition to the desktop manager, you have the windows manager, which gives the windows on top of your desktop their behavior, looks etc. Gnome, by default uses Metacity.

3. Compiz is a windows manager that uses the graphic card to render 3d effects with windows, creating nice decorative effects. This is what you call the wobbly windows.

So, this is the basis of what you asked for. Compiz can be installed through the synaptic package manager, after you have installed and enabled the graphics drivers for your graphic card.

If you need detailed instructions how to do this, ask.

Dedoimedo

---

### Post by FM101 on 2008-12-28
thanks for the help
so does ubuntu have to have gnome to have a windows environment?

---

