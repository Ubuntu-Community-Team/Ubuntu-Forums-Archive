---
title: "[SOLVED] initransfs prompt"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by rfbeck on 2008-12-04
After last week I was told how to reinstall a bad GRUB menu. Well, it was partially successful, except now when I try to boot into Ubuntu ( I dual boot Ubuntu and WinXP) I get the colorful Ubuntu boot screen for a long time followed by the text:

"BusyBox v1.1.13 (Debian 1:1 1.3-5 ubuntu12) Built in shell (Ash) Enter 'help' for a list of built in commands
(initranfs)_" 
instead of my GNOME GUI. What gives?

Thanks for the help.
______
Robert

---

### Post by maybeway36 on 2008-12-04
You can look at log files:
```
ls /var/log
cat /var/log/name-of-file
```

---

### Post by rfbeck on 2008-12-05
Okay well, I tried to enter:

ls /var/log
and the screen returned:

no such file or directory

guys,
I'm thinking about just re-installing Ubuntu, can I do this on top of the old installation or do I have to remove the old installation first? Thanks
______
Robert

---

