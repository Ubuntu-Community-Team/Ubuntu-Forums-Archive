---
title: "Accidentaly Deleted nm-applet"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by ben55 on 2007-08-10
Hi. I was messing around with Root File Browser.
And i accidentally deleted the nm-applet folder.
Its located at /usr/share/nm-applet.
Now, when i start up i get an error telling me that the nm-applet could not be started because the "glade" file could not be found. 
I have looked in trash to try and restore it but its not in there. 
I would appreciate it if someone could tell me a way to get that folder back or could attach a copy of theirs i could use.

Thanks :)

---

### Post by garas on 2007-08-10
try reinstall network-manager-applet package
*sudo aptitude reinstall network-manager-applet*

---

### Post by ben55 on 2007-08-10
I got this:
> Couldn't find any package whose name or description matched "network-manager-applet"

Any more ideas how to get hold of this. Thanks.

---

### Post by garas on 2007-08-10
try search applet in synaptic.
or check what are dependencies of network-manager

---

### Post by dominiquec on 2007-09-12
Ran into this problem as well.  Actually, all you need to do to fix it is to add the "Notification Area" from ("Add to Panel") again.

---

### Post by noob12 on 2007-09-12
If you want to try reinstalling the package, the name of the package is **network-manager-gnome**

---

