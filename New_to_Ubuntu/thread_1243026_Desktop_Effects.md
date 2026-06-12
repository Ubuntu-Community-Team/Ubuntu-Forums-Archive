---
title: "Desktop Effects"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by BigSears on 2009-08-17
my desktop effects have been turned off. i know where to go to turn them on, but when i do it just gives me a window that says "Desktop Effects could not be enabled." they were working fine and then i switched over to a different user for my little brother went back to mine and they haven't worked since.

---

### Post by zerhacke on 2009-08-17
I'd open "Users and Groups" in the System menu and see if their permissions are right to use 3D acceleration.

---

### Post by CatKiller on 2009-08-17
A quick thing to check is to open **gconf-editor** and look for the **/apps/metacity/general/compositing_manager** key. You don't want a tick in this box.

---

