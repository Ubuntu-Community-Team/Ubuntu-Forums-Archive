---
title: "How to find my current Display Manager"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by katochd46 on 2011-08-23
Please suggest the command for.

How to find my current Display Manager ?

BR,

Katoch

---

### Post by sam1948 on 2011-08-23
what do you mean?
window manager?
run in terminal
```
env | grep -i DESKTOP_SESSION
```
video device (card)?
run in terminal
```
lspci | grep -i vga
```

---

### Post by lkjoel on 2011-08-23
To find your current Display Manager:
```
cat /etc/X11/default-display-manager

```

---

