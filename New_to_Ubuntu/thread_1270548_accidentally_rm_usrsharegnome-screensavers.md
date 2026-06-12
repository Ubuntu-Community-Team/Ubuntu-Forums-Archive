---
title: "accidentally rm /usr/share/gnome-screensavers/"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2009-09-19
I had accidentally removed a directory.
How can I download it? SVN?

I have subversion installed, i just need to know what branch, and where the svn is kept.

---

### Post by sunchiqua on 2009-09-19
```
svn co http://svn.gnome.org/svn/gnome-screensaver/trunk gnome-screensaver
```Source: [http://live.gnome.org/GnomeScreensaver](http://live.gnome.org/GnomeScreensaver)

---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2009-09-20
Check your /usr/share/gnome-screensaver/ directory.

It shouldn't be the same as in that svn...Too many files in that checkout..
Anyway it seems the files came back after a restart.

---

