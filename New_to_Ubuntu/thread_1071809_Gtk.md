---
title: "Gtk"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by icyest on 2009-02-16
I'm having a problem understanding the "themes" terminology in ubuntu and at gnome-look. What's GTK and GTK2? Are they related to metacity?
Do they come pre-installed with my ubuntu810? or do I have to get them?


BTW, what is the Ubuntu equivalent to windows' "Explorer"?

---

### Post by RomeReactor on 2009-02-16
Hi. [GTK]("http://en.wikipedia.org/wiki/Gtk") is the Gimp Tool Kit, used to create the user interfaces in Gnome (KDE uses QT). [Metacity]("http://en.wikipedia.org/wiki/Metacity") is the window manager (KDE uses KWIN). And the equivalent of windows explorer is called nautilus in Ubuntu (KDE uses Dolphin or Konqueror).

---

### Post by supersonicdarky on 2009-02-16
gtk - the look and feel of windows (ie, all the controls, buttons, textboxes, etc) <-- for gnome apps
metacity - default gnome window manager (ie, the window border)

One of the many equivalents to explorer is nautilus. Others include dolphin, pcmanfm, thunar and konqueror.

---

### Post by snova on 2009-02-16
> **icyest said:**
> What's GTK and GTK2?

The software responsible for drawing widgets. Every button you click, window you interact with, is drawn by GTK.

> Are they related to metacity?

I'm a bit sketchy on the details, but I think I can safely say No. Metacity is the window manager, it puts those lovely title bars all over the place so you can drag windows around. :)

> Do they come pre-installed with my ubuntu810? or do I have to get them?

Certainly. There wouldn't be much to look at without GTK. :)

> BTW, what is the Ubuntu equivalent to windows' "Explorer"?

Nautilus.

---

### Post by djbushido on 2009-02-16
Like the sig. Not the best idea, but hey, something new.
Before I begin, as to the big question, everything in that post SHOULD be pre-installed if you use Ubuntu. Xubuntu or Kubuntu is different. And it's Ubuntu 8.10, not 810. The year it was released ( 2008 ) and the 10 is the month (October). The next release is 9.04, march 2009.

GTK is a lot of things all at once.

First, the easy one - the file browser that is the equivalent of explorer.exe (windows explorer) is called "nautilus." This browser also handles the desktop, just like explorer.

Metacity is the window manager. This is the engine that draws the window borders and makes all that look nice and pretty. Like the close button, maximize, etc.

Themes are .tar.gz archives with images etc. packed inside that are read by the theme manager (forget what it is, will edit later) and "installed," meaning replacing the defaults.

Gnome-look is an UNOFFICIAL site for themes.

GTK is literally a display engine, that sets the foundation for all the previous things, and on top of which the GNOME desktop environment is based. Without going into the programming side, this is what shows all the nice things like textboxes, etc.

Gtk 1 & 2 are different versions of the program. GTK 1 is old, and unless you know what you're doing (which you apparently don't, sorry) ignore GTK 1. Stay away from it. Unless of course there is a specific reason to use it. Then you could run into more fun compatibility stuff, but best to avoid that.

So I think that's it, post back more questions you have. Have fun with Linux!

EDIT: awww... three people responded in the time it took for me to write this extremely long and detailed post... :-(

---

