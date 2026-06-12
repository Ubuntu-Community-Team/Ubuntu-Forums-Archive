---
title: "change dialog sizes"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by vie_ascenseur on 2010-01-24
Hey everyone,

I am currently using an old Celeron machine as a Hardy Server - At the moment, it's hooked up to my TV - (I'm planning on running it headless). But, I'm using it at the moment as a standard desktop.

My TV currently only accepts a resolution of 640x480, (lame, I know) - I have managed to get it set to the right resolution, but I still have one problem. All the windows are extremely out of proportion, and most of them cannot be resized.

I was just wondering if it is possible to change the actual dialog resolution sizes, (i.e. a system setting).

Regards,

Joe

---

### Post by Wataru8675 on 2010-01-24
Maybe you could search the Internets for a theme that has windows the right size, or learn to make a theme yourself and just adjust the window size in there?  I'm not sure there's a simple size choice that you can click.

---

### Post by NCLI on 2010-01-24
I'm afraid not. 
Although Ubuntu's minimum spec recommendation is 640x480, the recommended minimum resolution is 1024x768, so you should probably be looking to invest in an HD-tv, if you can, or install applications which don't use a lot of screen space.

---

### Post by ankspo71 on 2010-01-24
Hi,
I know something that might help a little bit. Install gnome-color-chooser.
When you launch it, at the bottom of the first tab "global colors", it has a profile option dropdown box that lets you choose between  "theme default" and "compact".

```
sudo apt-get install gnome-color-chooser
```

It also lets you choose font size, font padding, scrollbar size, scrollbar padding, etc, and also lets you choose between engines for themes. These won't make a huge difference but it could help.

You might also want to search [http://gnome-look.org/](http://gnome-look.org/) for some compact themes.

---

### Post by ankspo71 on 2010-01-24
Before you try installing it on a server, I created a screenshot for you so you can decide if it's worth installing. It's the before and after after using the compact profile in Gnome Color Chooser.

See screeshot.

---

