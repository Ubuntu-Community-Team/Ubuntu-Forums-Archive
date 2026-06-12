---
title: "can't open pm-suspend-log??"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by soryu on 2010-02-03
how do i open it?  pc not waking up from hibernation. properly.
when i go check it thru var/log/pm suspend-log. i get a red sign telling me i cant access it.

---

### Post by cariboo on 2010-02-05
You need to be root to open that log file, press Alt-F2 and type:

```
gksu nautilus
```

the above command will open the file manager as root, allowing you to view the log file.

---

