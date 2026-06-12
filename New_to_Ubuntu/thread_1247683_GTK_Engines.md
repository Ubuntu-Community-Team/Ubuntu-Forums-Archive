---
title: "GTK Engines"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by Sly-.- on 2009-08-23
Hello. The majority of the time I install a GTK 2.x theme it will say something like "X  engine is not installed", X being the various engines of course. I came across [this]("http://www.linuxfromscratch.org/blfs/view/svn/gnome/gtk-engines.html"), would this be the correct package to install various engines?

Also, can anyone give me a hand installing it? I've tried using the commands provided, get some required dependencies issues, so try to install them but get nothing but errors.

Thanks!

---

### Post by CatKiller on 2009-08-23
If you're using Ubuntu, you don't really need to do whatever Linux-from-scratch does. You also don't need to install stuff from some random website. Use Synaptic like a sane Ubuntu user :) There are a number of GTK and GTK2 theme engines in the repositories.

---

### Post by Sly-.- on 2009-08-23
Ok thanks, I'm still pretty new to all of this. :)

Take [this]("http://thevalrog.deviantart.com/art/Gnome-Air-suite-V2-120843793") theme for example. Inside is a GTK folder and an emerald file for the Window. How do I install this emerald file?

Thanks.

---

### Post by shae on 2009-08-23
Well emerald is for the emerald compiz engine.  Enable compiz and use fusion-icon to select emerald (You may have to install emerald).  Afterwards, you can use emerald's theme manager to install emerald themes.

---

### Post by CatKiller on 2009-08-23
As far as I can tell, the GTK theme part of that only uses the Mist and Pixmap theme engines, so that's pretty simple. I'd imagine both of those are installed by default (Mist is provided by the gtk2-engines package).

Emerald is a [window decorator]("http://en.wikipedia.org/wiki/Window_decorator"). It draws the titlebars, mostly. You'll only need to install the Emerald theme (the .emerald file) if you're using Emerald as your window decorator. You'll need to be using a compositing [window manager]("http://en.wikipedia.org/wiki/Window_manager") (like Compiz) to use Emerald. It's entirely optional to do so (some people like the pretty effects). 

If you wish to use Emerald, install the Emerald Theme Manager to easily apply themes; it's just a drag-and-drop of the .emerald file on to the Emerald Theme Manager window. Actually, I think the theme manager gets installed when you install Emerald, but I could be mistaken.

If you get your other themes from somewhere like gnome-look.org, those themes are just a drag-and-drop (of the .tar.gz file) onto the Appearances window. I'm not sure that random members of Deviant Art necessarily package their themes correctly for this to work for those files.

---

