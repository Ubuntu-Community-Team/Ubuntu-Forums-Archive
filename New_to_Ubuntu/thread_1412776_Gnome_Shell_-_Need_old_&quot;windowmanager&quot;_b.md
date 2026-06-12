---
title: "Gnome Shell - Need old &quot;windowmanager&quot; back"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by aristoddler on 2010-02-21
I replaced "windowmanager" with "gnome-shell" in gconf-editor. Now **[COLOR=#ff0000]Gnome[/COLOR]** **[COLOR=#ff0000]shell[/COLOR]** is moving impossibly slow and I have no idea how to return to the normal panel.. help!!

---

### Post by Greenwidth on 2010-02-21
```
compiz --replace
```
(or metacity) - replaces for current session

gconf-editor > desktop > gnome > session > required_components >> windowmanager
for perm change

---

### Post by k3lt01 on 2010-02-21
If you make changes like that you can use System > Preferences > Startup Applications. That way you have a nice GUI that you can see the changes you have made and revert back to your old configuration easily.

---

