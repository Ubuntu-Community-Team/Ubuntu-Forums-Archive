---
title: "Webpage display gets funky"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by RLCGRN on 2011-04-24
Sometimes websites display like the attached image.  Scrolling up or down, then back, changes the way the strangeness appears, but it doesn't fix the problem.  Occasionally reloading the page helps, but this time it didn't.  What's going on, and how do I fix it?

---

### Post by mynameisnotbob on 2011-04-24
If restarting doesn't work, press CTRL+ALT+F2. Then type: ```
sudo /etc/init.d/gdm restart
```.
NOTE: This will close all programs you are running (in GUI). But it should fix the problem.

---

### Post by RLCGRN on 2011-04-25
As you can see, restarting didn't solve the issue.  Next I'll try the ```
sudo /etc/init.d/gdm restart
``` option, but if I lose my GUI, how do I operate and get it back?

---

### Post by mynameisnotbob on 2011-04-25
it should restart, but with no open programs. If for some reason not:
```
sudo /etc/init.d/gdm start
```

---

### Post by RLCGRN on 2011-05-13
no issues for a while.  Will report if this occurs again.

---

