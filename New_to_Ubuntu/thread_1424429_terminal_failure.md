---
title: "terminal failure?"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by lakofrune on 2010-03-07
so i was getting used to terminal and i went into settings and i put just "Sudo" in the command line in settings, the one that makes it automatically do it, (not directly into terminal) and it fails to even open, a friend said that i need to reinstall gnome terminal something or other.
basically, its not starting up.
in the mean time, im using guake, which is very similar and does the same things (as far as i can tell), but with some different characteristics. but i would still like to try and fix terminal.
any ideas?
i don't know what to call the place where i put it, but it WAS NOT directly into the command line. it was into the preferences/settings menu.
i have tried un-installing and re-installing.

---

### Post by asmoore82 on 2010-03-08
open the "Run" dialog, Alt+F2 by default, and run:
```
gconf-editor
```

In the left pane, navigate down to "/apps/gnome-terminal/profiles/Default/"
In the right pane, scroll down and un-check "use_custom_command"

---

### Post by lakofrune on 2010-03-08
we got a pro in the house, thnx. i give u props.

---

