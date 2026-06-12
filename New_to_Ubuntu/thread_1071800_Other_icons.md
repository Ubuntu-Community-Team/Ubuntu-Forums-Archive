---
title: "Other icons"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by bob brazie on 2009-02-16
V8.10

Is there a folder somewhere on the installation that contains other icons then the ones default icons were set at?

Maybe somewhere to down load new ones?

I would like to change some to have a better mix.

Thanks in advance.

---

### Post by Iandefor on 2009-02-16
I'm amazed this hasn't been answered yet.

Ubuntu (and Linux GUI's in general- GNOME, XFCE, KDE, LXDE, and the *box's) supports custom themes for icons, UI widgets, and window borders. You can get new themes at like gnome-look.org or art.gnome.org, or if you look around on Deviantart there are GNOME icon themes hosted there, too.

Icon themes are stored in two places: in a folder called .icons in your home directory (it's hidden thanks to that leading period, there's a checkbox to show hidden files somewhere in the file manager's preferences window) and in /usr/share/icons, which is for system-wide icon themes (ie, themes you want everyone to use). If you go to the Appearance configuration window and hit "customize" under the theme tab, you can mix and match window manager themes, GTK themes, icon themes, and mouse cursors.

You can also use the "install" button to install an archived theme (a theme in a .tar.gz or .bz2 or some other kind of compressed/archived format) automatically- but if it doesn't work, you can un-archive the theme manually and install it to .icons or /usr/share/icons (.icons is probably easier).

---

### Post by bob brazie on 2009-02-17
Thanks a bunch, I was hoping there was more.

Bob.

---

