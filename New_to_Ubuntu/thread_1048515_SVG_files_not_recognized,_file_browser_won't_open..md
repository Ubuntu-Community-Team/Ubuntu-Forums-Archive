---
title: "SVG files not recognized, file browser won't open."
date: 2009-01-23
forum: New to Ubuntu
---

### Post by rgb96 on 2009-01-23
So when I turned my machine on today I got an error message saying something like 

'Human' theme file format can not be recognized "/usr/share/gdm/themes/Human/bottom_bar.svg"

When I logged in, my background is gone, my file browser won't open, and if i try to move any of my icons, the screen blacks out and then comes back.

I found on another thread someone suggesting to download and install from source the librsvg-2.22.3.tar.gz library, but I get errors when I try to make it. Any ideas?

---

### Post by ajgreeny on 2009-01-23
Sounds rather like a corrupt entry somewhere in your ~/.gconf folder where all the gnome settings are stored.  Try renaming that and then logging out and in again.  OK, all your personal settings will be gone, but at least you may be able to get a working desktop again, and then just reset all your preferences.  Of course, if you have a recent good backup of your ~/.gconf folder, you may be able to restore that and get back your good desktop.

---

