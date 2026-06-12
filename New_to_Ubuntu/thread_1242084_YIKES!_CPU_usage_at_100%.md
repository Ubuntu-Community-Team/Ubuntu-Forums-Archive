---
title: "YIKES! CPU usage at 100%"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by Bill Sheppard on 2009-08-16
Title says it all. How do you fix this when it happens? BTW, what does 'CPU' stand for anyhow? Thanks

Bill

---

### Post by nhasian on 2009-08-16
Yikes!  CPU stands for central processing unit.  its like the engine of your computer.  you dont want it to overheat.

in a terminal type:

```
top
```

find which line is eating up your cpu cycles and then press k to kill it with the process ID (pid)

---

### Post by coldReactive on 2009-08-16
And if it's xorg, don't kill it.

---

### Post by aesis05401 on 2009-08-16
Maybe post the top output here before killing anything... just in case ;)

---

