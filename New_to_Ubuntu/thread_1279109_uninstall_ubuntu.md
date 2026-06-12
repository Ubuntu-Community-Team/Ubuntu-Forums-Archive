---
title: "uninstall ubuntu?"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by akshep on 2009-09-30
Is there a way to uninstall ubuntu with out it screwing up my laptop. Right now i am dual booting vista and 9.04.

---

### Post by madprofessor on 2009-09-30
Delete the partition in Vista and boot from the Vista startup disk and choose repair. There should be an option to repair the boot loader. Run that and reboot.

---

### Post by halitech on 2009-09-30
how did you install it to start with?

if you used wubi, just remove it from add/remove in windows. If you did a true dual boot, use your windows install cd and repair the mbr first then format the partition in windows.

---

### Post by dwinks on 2009-09-30
You may need to run the command window on the Vista install disk and do the following:

```
bootrec /fixboot
bootrec /fixmbr
```

---

