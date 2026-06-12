---
title: "tint2"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by chris200x9 on 2009-10-16
I'm running compiz + xfdesktop with tint2 but tint2 will not stay above other windows. How do I make tint2 "always on top"?

edit: I moved it to the top and this became a moot point :P

---

### Post by ibuclaw on 2009-10-16
> **chris200x9 said:**
> I'm running compiz + xfdesktop with tint2 but tint2 will not stay above other windows. How do I make tint2 "always on top"?

edit: I moved it to the top and this became a moot point :P

Tint opens with the "always on top" hint by default.

If for whatever reason this doesn't work, it may be an issue with your window manager not adhering to that hint.

Just trying it out in Gnome, I have no issues as such, am running without using a specific configuration file.

Regards
Iain

---

### Post by danger89 on 2011-04-25
If however you want to know what setting does this trick or if you want to setup your tint2 config file from scratch:
```
panel_layer = top
strut_policy = follow_size
```

**panel_layer **set it always on top. **strut_policy** force all the windows to not overlay the tint2 bar.

---

