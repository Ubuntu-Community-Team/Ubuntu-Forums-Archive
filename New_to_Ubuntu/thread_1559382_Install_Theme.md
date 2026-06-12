---
title: "Install Theme"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by romertz on 2010-08-23
Hello... I am new and I hope be writing this in the right place...

...I have installed ubuntu two days ago and I installed also a theme for the windows, icons, cursor, etc...from gnome-look...I can see them in the normal windows (like my personal folders), but I don't see how can I see them when I see the system windows like synaptics or when I go to sudo nautilus...the theme that that windows have doesn't like me.... please, someone could tell me how can I install the themes (windows, icons, cursor, etc...) to these system windows?

thank all you...


romertz.

---

### Post by inameiname on 2010-08-23
Sounds like you merely installed them in your home directory, not your system directory as well. Usually the default method for an installation of a theme and/or icon set is to install in your home directory, to '~/.themes' and '~/.icons'. This works, but it is best to install those files directly into '/usr/share/themes' and '/usr/share/icons', as then you will get systemwide change of icons and theme. So just cut and paste those things inside those folders, and you should be all set. That's what I do for themes and icon sets I've gotten off of gnome-look.

FYI, you must 'sudo nautilus' to get into the root nautilus first, and then just cut and paste (no need to keep them in your home folder, ie '~/.themes' and '~/.icons') from nautilus, to those folders in sudo nautilus. Just remember to refresh nautilus, either by 'killall nautilus & exit' or restarting your computer.

---

### Post by romertz on 2010-08-23
ok....

....I copied the folders to the places you told me and now it's like I wanted....the themes are changed well...I just reloaded the theme from Preferences/Aparience (Preferencias/Apariencia) after make the copy...

...thank you so much...

---

### Post by inameiname on 2010-08-23
Sure. Glad you got it working for ya.

Oh, and don't forget to mark this thread as solved so others may find it helpful later on. Just click the Thread Tools link and there you will see Mark as Solved.

---

