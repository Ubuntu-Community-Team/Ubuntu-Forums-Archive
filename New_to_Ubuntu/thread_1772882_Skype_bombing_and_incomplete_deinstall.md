---
title: "Skype bombing and incomplete deinstall"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by JamButty on 2011-06-01
Last few days, Skype has been bombing within 1 second of attempting to start. There is no error message, it just falls out. I can see it appear and disappear on the processes list. A related bit is that, even after complete removal, there are straggler files I can't  (normally) remove  -


[LIST]
[*] /usr/share/app-install/desktop/skype
[*]/var/cacheap/archives/skype_2.2.0.25-1lucid_i386.deb
[*]         /usr/share/app-install/icons/skype.png
[/LIST]

My guess is the DEB and PNG files are harmless but not the desktop file. Even after removal/reinstall, the program has my Skype username and password pre-loaded, which can't be right unless the deinstall is partial. Anyone familiar with Skype bombing this way or with tips on getting rid of the straggler files or tips on other places my Skype ID info would be lurking? thanx

---

### Post by satanselbow on 2011-06-01
Deleting those files from a root terminal will do no harm ;)

There is also a hidden ".skype" folder under home - open nautilus and press CTRL+H to show hidden files - delete only the .skype folder as the other config other apps and system settings ;)

---

### Post by JamButty on 2011-06-01
Trashing the .skype dir did it. Skype is happy again. 

Thanks to your elbow, Satan

---

