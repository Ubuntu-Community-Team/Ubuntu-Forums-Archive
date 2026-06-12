---
title: "Top part of the windows disappeared"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by WubiAR on 2011-08-09
This is happening to me again, just like it did in Ubuntu. But this time, I didn't install Compiz. Is there any way of bringing back the title bar of each window opened?

---

### Post by Toz on 2011-08-09
Alt-F2 and run:
```
xfwm4 --display=:0.0 --replace
```

---

### Post by WubiAR on 2011-08-10
> **Toz said:**
> Alt-F2 and run:
```
xfwm4 --display=:0.0 --replace
```

Thank you very much. Also, how did you know this? I am just curious to find out. :o

---

### Post by Toz on 2011-08-10
Glad to hear it worked. If you don't mind, can you mark this thread as solved. 

The xfce forums over at [http://forum.xfce.org/]("http://forum.xfce.org/") are another good resource. As well as, of course, google. And experience ;)

---

