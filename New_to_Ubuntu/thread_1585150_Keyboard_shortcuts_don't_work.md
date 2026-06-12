---
title: "Keyboard shortcuts don't work"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by bokgeneraal on 2010-09-30
Hi everyone
My shortcut key to open the terminal is not working anymore 
I did check System>Preferences>Keyboard Shortcuts to make sure it's set to the shortcut I'm using.
I even changed it to mod+t . But is still doesn't work
:confused:

---

### Post by Hippytaff on 2010-09-30
Do you mean alt+F2 to select programs > and selecting Teminal from list?

---

### Post by dcsoldschool53 on 2010-09-30
> **bokgeneraal said:**
> Hi everyone
My shortcut key to open the terminal is not working anymore 
I did check System>Preferences>Keyboard Shortcuts to make sure it's set to the shortcut I'm using.
I even changed it to mod+t . But is still doesn't work
:confused:
Instead of using two keys, try just using one key like a function. I use F8. see if that works. Also you can use the Gconf-editor /apps/metacity/global-keybindings or /apps/metacity/keybinding-commands to try and fix your problem if you don't like my first suggestion.

---

### Post by JC Cheloven on 2010-09-30
Perhaps the shorcut you intend to use conflicts with compiz (ie, compiz uses that shortcut for something else). You can try disabling desktop effects in system-> preferences -> appearence, or installing  ```
sudo aptitude install compizconfig-settins-manager
``` and use it to browse keyboard shortcuts used by compiz.

Anyway, if memory helps, ctrl-alt-T is the default for opening a terminal. I always set alt-F5 for that (a matter of habit). Does any of the above work for you?

---

### Post by bokgeneraal on 2010-10-06
[SIZE=3][FONT=Lucida Console]I reset Visual Effects to none and then the [/FONT][/SIZE][FONT=Lucida Console][SIZE=4]shortcuts worked. I then set the visual effects back to custom then found they still work. I guess the problem arose from using compiz-config instead of simple-compiz config.
Thanks for help:)
[/SIZE][/FONT]

---

