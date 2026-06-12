---
title: "Lost panel task bar"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by kawlinkoko on 2009-08-21
I am new user of ubuntu. now i have a little problem. I lost panal task bar on my desktop :confused: . How can i do? please help me.

---

### Post by super kim on 2009-08-21
if there is a panel you can right click on it and then click on new panel. if there are no panels then i'm not sure, try enetering this into a terminal ```

[INDENT]sudo debconf gnome-panel
```
[/INDENT]

---

### Post by hetx on 2009-08-21
You right click on your panel, choose "Add to panel". You get a new window, scroll down to "Window List" and select it. There you are!

---

### Post by super kim on 2009-08-21
> **super kim said:**
> if there is a panel you can right click on it and then click on new panel. if there are no panels then i'm not sure, try enetering this into a terminal ```
[INDENT]sudo debconf gnome-panel[/INDENT]
```
actually you'd better just read [this]("http://www.saifur-rahman.com/2008/12/restoring-default-ubuntu-panel/") that command might not work anymore.

---

### Post by ciprian.topala on 2009-08-21
Which panel did u lose?
The top or the bottom one?
If it's the top one you can enable it by typing gconf-editor into a terminal and then go to desktop -> gnome -> session -> required_components.
Make sure that panel key has the value gnome-panel.

---

### Post by hetx on 2009-08-21
Personally I had alot of trouble just getting rid of the damned panel! I think he still has atleast one panel, he's just missing the Window List.

---

