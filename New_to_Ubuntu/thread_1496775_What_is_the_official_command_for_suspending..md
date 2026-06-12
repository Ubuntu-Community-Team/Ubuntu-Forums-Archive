---
title: "What is the official command for suspending."
date: 2010-05-29
forum: New to Ubuntu
---

### Post by Kafubie on 2010-05-29
I am running Xubuntu 10.04 (I believe).
When I go to Xfce settings -> keyboard -> and add a shortcut.
I don't know any commands for suspending my laptop.

You guys have any idea?
-Nathan

---

### Post by kerry_s on 2010-05-29
**gksudo pm-suspend**

if you don't want to enter a password, then you need to add to the sudoers file.

```
your-name ALL=NOPASSWD: /usr/sbin/pm-suspend
```

edit the file with "**sudo visudo**"

---

