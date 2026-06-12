---
title: "compizconfig settings"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by deep.3997 on 2011-06-25
Hey guys,
 I am new to linux and I was trying some effects using compizconfig-settings-manager (ccsm) and I screwed everything. Following are the problems:

1: when i maximize any window it wont show the close,minimize,restore options in top corner.
2: my shortcut keys for eg: cltr+alt+t for terminal are not working.
3: The top right corner of my desktop is not showing any options like network,sound,system options like shutdown,restart etc.

What should I do to restore my previous settings?
I am using Ubuntu 11.04 unity interface.

Thanks in advace!

---

### Post by yetiman64 on 2011-06-25
Changing settings with ccsm is known to cause problems in unity, use ccsm with care.

If you can't get a terminal with ctrl + alt + T (may be compiz related) use ALT + F2, and put in the command,
```
unity --reset
``` this should put all your settings back to default.

Some info from web upd8 on this topic is [[COLOR=Blue]--here--,[/COLOR]]("http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html") be very careful and note their warnings with regard to the last command they show, I don't think you need to use it.

---

### Post by deep.3997 on 2011-06-25
yeah its working fine now.
Thanks!

---

