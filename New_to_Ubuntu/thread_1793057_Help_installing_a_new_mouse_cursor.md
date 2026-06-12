---
title: "Help installing a new mouse cursor"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by slayner117 on 2011-06-28
[http://gnome-look.org/content/show.php/Pulse+Glass?content=124442](http://gnome-look.org/content/show.php/Pulse+Glass?content=124442)

^ Is the theme I am trying to install, However I am having some trouble doing so, in appearance if I try to install new theme it says not a valid theme and when you select mouse cursors from system setting it just seems to lock up and not really do anything. I have read a little about extracting in the icons folder but again -- I am having some trouble doing so. 

If anyone could please walk me through how to install this theme for my new cursor, I would greatly appreciate it.

---

### Post by jtarin on 2011-06-28
1. Untar the file into ~/.icons.(which is a hidden folder in your /home/username directory)
2.Then go to System> Settings> Appearances, select 'Themes' tab. select 'name of your cursor theme'.
3. re-login or reboot.

And on some versions of Ubuntu, you need some more steps.
1. sudo gedit /etc/alternatives/x-cursor-theme.
2. in the doc, find "Inherits=xxx", replace "xxx" by "yourthemename".
3. save, close, re-login.

---

