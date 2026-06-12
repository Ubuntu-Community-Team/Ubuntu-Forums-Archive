---
title: "where is the boot message located?"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by 007casper on 2011-07-25
Where can I locate the boot message on the computer? Is it written to a log?

---

### Post by wallywally on 2011-07-25
System > Administration  > Log File Viewer

Then within Log File Viewer:

File  >Open > boot.log

---

### Post by 007casper on 2011-07-25
where is boot.log located?

I need to get to it through the terminal.

Thank you.

---

### Post by AlphaLexman on 2011-07-25
```
cat /var/log/boot.log
```

---

### Post by 007casper on 2011-07-25
thank you

---

