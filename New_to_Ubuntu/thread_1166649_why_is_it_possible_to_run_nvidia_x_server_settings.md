---
title: "why is it possible to run nvidia x server settings without root?"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by sp0tz on 2009-05-21
It never lets you save any of the changes you made if you don't have root access...

More importantly, how do I fix it? I'd like to add, like, a gksudo call to  
system>admin>nvidia X server settings 
. Can I do that? what does that icon point to, is it like a bash script or something?

---

### Post by Hospadar on 2009-05-22
You do need root permission to save the changes you make in nvidia-settings

You can either:
Alt-F2 and type "gksu nvidia-settings"

or edit the menu entry, right-click the menu bar, edit menus, find the entry and edit it (change the "command" from "nvidia-settings" to "gksu nvidia-settings"

---

### Post by sp0tz on 2009-05-22
thank you, sir. The menu is something I hadn't looked at much before.
I see I can add my own custom launchers. Awesome.

---

