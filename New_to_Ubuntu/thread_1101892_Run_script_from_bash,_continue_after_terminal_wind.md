---
title: "Run script from bash, continue after terminal window is closed"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by sargant on 2009-03-20
Hi, this seems like such a simple problem, but I've got no idea how to do it. Basically, what I'm trying to do is:

- Log in to SSH
- Run test.sh by any means
- Quit SSH, but have test.sh still running on remote computer

Any help would be much appreciated!

---

### Post by taurus on 2009-03-20
Use the nohup command.

```
nohup test.sh
-or-
nohup ./test.sh
(If test.sh is not in your path.)
```

---

### Post by kanikilu on 2009-03-20
As already suggested, nohup is probably what you are looking for, but if you're not already familiar with *screen*, it's a very useful tool to detach an entire session and resume it at a later time/place.

---

