---
title: "Network Error, what the?"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-21
Can anyone shed light on this when I try to access network?

---

### Post by Sealbhach on 2009-06-21
Have you got gvfs installed? Copy this into a terminal and see what comes up:

```

dpkg -l | grep gvfs
```

.

---

### Post by Metallion on 2009-06-21
It seems to be looking for this gvfs process which isn't present. Perhaps you still need to install it. What happens when you type the following command and try again?

```
sudo apt-get install gvfs
```

---

### Post by Gp. on 2009-06-21
Related to this.
[http://ubuntuforums.org/showthread.php?t=1193631](http://ubuntuforums.org/showthread.php?t=1193631)

---

