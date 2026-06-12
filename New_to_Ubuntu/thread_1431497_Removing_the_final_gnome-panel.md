---
title: "Removing the final gnome-panel"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by blazemore on 2010-03-16
I'm using AWN for my panel-related tomfoolery. How can I remove the top panel, as the option is greyed out and killing the panel just spawns another.

---

### Post by xtremesupremacy3 on 2010-03-16
I'm pretty sure thats not possible due to the fact that it holds the menus, the taskbar, the clock etc

---

### Post by blazemore on 2010-03-16
Of course it's possible. I could take away execution permissions on gnome-panel binary.
Here's a screenshot proving I don't need gnome-panel.

---

### Post by mechro on 2010-03-16
There's a setting in gconf-editor that may work...

desktop > gnome > session > required_components: panel... delete or unset the key.

---

### Post by tom.swartz07 on 2010-03-16
> **blazemore said:**
> Of course it's possible. I could take away execution permissions on gnome-panel binary.
Here's a screenshot proving I don't need gnome-panel.

The only easy way that I remember is two steps
1) kill the panel process, and remove it from your current session
2) in power options, advanced tab theres an option to remember running programs, check that and it wont re-start the panel.

I remember seeing another method but it involved screwing around with some settings in gconf-editor and i dont remember offhand.

---

