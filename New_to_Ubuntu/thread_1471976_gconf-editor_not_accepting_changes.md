---
title: "gconf-editor not accepting changes"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by Limitlesschannels on 2010-05-04
Hey all,

I searched a couple threads and found what looked like solutions to the symptoms, not the problem, so I figured I would ask.

Occasionally when I change something in gconf-editor it won't work.  I successfully change a value and exit the editor, but the change doesn't occur, even after a restart.  The setting is changed in the editor, but not physically different.  This happens mainly for two cases:

*Modifying the button order on the top bar (apps/metacity/general/button_layout)* set to **menu:minimize,maximize,close**
*apps/nautilus/preferences/always-use-location-entry* set to **True**.

both of these I've been able to change through command line direct modification of the gconf settings (can't remember the exact command now) but is there a way to reset the desktop environment to accept the changes?  startx or something?

---

### Post by clhsharky on 2010-05-04
HI Limitlesschannels

Using gconf-editor in terminal with sudo should allow changes to persist. 

[HTML]sudo gconf-editor[/HTML]

Always be very careful with gconf-editor.

Sharky

---

### Post by mcduck on 2010-05-04
First, Gconf-Editor is a graphical application and you should _always_ use gksudo instead of sudo for GUI applications.

..and second, running gconf-editor with gksudo will make it run as user root, so you aren't changing your normal user's settings at all, but root's instead. Of course running it as root allows you to set a key value as mandatory for all users of the system, but you only should do that if you really want to take the options away from the normal user accounts. Besides, it still only changes the same gconf key in the user's settings, so if that works then doing the same change as normal user (instead of setting a mandatory value as root) should work just as well.

So, if you want to change your user's settings, just run "gconf-editor". Or if you really want to force a setting to all users, and make the users unable to change it themselves, use "gksudo gconf-editor" and the "Set as Mandatory"-option.

---

### Post by clhsharky on 2010-05-04
Thank you mcduck

Sharky

---

### Post by Limitlesschannels on 2010-05-05
great, thanks mcduck, that did it.  I was using gksudo so I wasn't changing my own settings.

Thanks again,

---

