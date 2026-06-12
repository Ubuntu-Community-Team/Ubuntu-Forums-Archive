---
title: "Odd problem... kind of an annoyance"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by djyoung4 on 2009-10-31
ok so everytime I open a new window other then firefox the top bar with close, minimize, maximize is out of the screen at the very top.  earlier i was trying to get compiz running and typed ```
compiz
``` in a terminal and ever since then this has been happening.  its not really a problem just an annoyance.  anybody know how to fix it.

---

### Post by lavinog on 2009-11-11
you should enable compiz by turning on visual effects in the appearance prefrences.
by running compiz in a terminal, you were likely to terminate compiz when the terminal was closed.

You could try:
```
metacity --replace
```

---

