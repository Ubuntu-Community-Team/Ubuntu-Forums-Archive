---
title: "Malfunction after login, possibly panel related"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by gir9999 on 2010-01-12
I'm running Karmic Koala with the latest kernel.  I turn on my laptop, it boots fine, and I get to the login screen.  Type in my password, everything is great up to this point, but then my panels remain blank and my title bars for any window currently visible never load (the bit above File Edit...)  My desktop does load, and icons can be clicked.  

Everything worked just fine before this boot, and i have some idea what may be causing the problem.  I was working on a latin text file the other day, and wanted to use the character pallete panel feature for the long vowels.  I made a panel on the left, and set it to autohide, but the panel disappeared and would not return on mouseover.  Made another panel, autohid again, disappeared again.  Because there was nowhere to click on them, I did not know how to delete them.  My solution was to no longer autohide the panel, so now i have three panels on the left, two malfunctioning and hidden and one non-hidden and working fine.  This served me perfectly well until my last reboot, bringing me here.

Is there any way i could command-line delete those panels?  Also, what's wrong with my autohide?

Thanks for reading!
\\:D/

i made a desktop launcher to access gnome-terminal and it worked

---

### Post by gir9999 on 2010-01-12
update: i've found the offending panels in gconf-editor, removed autohide, deleted them, and now everything works!


there are a few topics on here that describe the same problem after autohiding panels.  here's what I did.

created launcher on desktop command: gnome-terminal
click launcher
type gconf-editor
apps->panel->toplevels

look around in there for a panel that has attribute auto_hide checked and uncheck it

close gconf-editor

in a terminal, type 
sudo pkill gnome-panel
to restart your panels

Delete spare panels if necessary 

DONE.

---

### Post by doru001 on 2010-01-16
See also: 
[http://ubuntuforums.org/showthread.php?p=8674264#post8674264](http://ubuntuforums.org/showthread.php?p=8674264#post8674264)

---

