---
title: "While in a drunken stupor, I deleted the Shut Down/Log Off tab"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by skine on 2009-08-18
While in a drunken stupor, I deleted the Shut Down/Log Off tab that normally appears in Ubuntu. 

All of the other discussions I've found don't include drunken stupidity, and while the "add to panel" option has something that works, it's not quite the same. 

Thanks in advance, 

-skine

---

### Post by lisati on 2009-08-18
> **skine said:**
> While in a drunken stupor, I deleted the Shut Down/Log Off tab that normally appears in Ubuntu. 

All of the other discussions I've found don't include drunken stupidity, and while the "add to panel" option has something that works, it's not quite the same. 

Thanks in advance, 

-skine

D'oh! Fast user switcher?

---

### Post by Nburnes on 2009-08-18
In Terminal

```
gconftool-2 --shutdown

rm -rf ~/.gconf/apps/panel

pkill gnome-panel
```

Copy and paste that and your panel will be default again

---

### Post by Gavinthechop on 2009-08-18
:P:P:P I don't know what you're talking about, but that's seriously funny!

---

### Post by MelDJ on 2009-08-18
right click the panel. press add to panel and then add Quit

---

### Post by mcduck on 2009-08-18
> **skine said:**
> While in a drunken stupor, I deleted the Shut Down/Log Off tab that normally appears in Ubuntu. 

All of the other discussions I've found don't include drunken stupidity, and while the "add to panel" option has something that works, it's not quite the same. 

Thanks in advance, 

-skine

The default applet used for this purpose is called "User Switcher". Just add that back to your panel and you'll be fine (except for the hangover.. :D)

---

