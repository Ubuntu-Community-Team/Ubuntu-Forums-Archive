---
title: "Command to Exit in Recovery Mode terminal"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by onaridge on 2010-11-15
If you are stuck, let's say in recovery mode in what looks like the terminal window, how do you exit and shutdown gracefully. What is the command?

---

### Post by DaithiF on 2010-11-15
there are several commands that can do this, .e.g:

```
shutdown -h now
init 0
halt -p

```

---

### Post by onaridge on 2010-11-15
Thank you. At the time I didn't have them and nervously turned it off by the switch.

---

### Post by uRock on 2010-11-15
Or ```
reboot
```

---

