---
title: "how to change default session?"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by mamamia88 on 2010-01-11
i installed xubuntu but i want to make gnome the default de can someone help me?  i have gnome, kde, and xcfe installed

---

### Post by perlluver on 2010-01-11
When you are logging in, you can select which DE to load, under sessions.  This will be the default desktop until you change it.

---

### Post by mamamia88 on 2010-01-11
ah thanks in the last version it would ask you when logging in if you wanted to make session default

---

### Post by LarsO on 2011-11-05
I found that in 11.10 this didn't work.
Using the following command in the /usr/lib/lightdm/ directory did work:
[FONT="Courier New"]sudo ./lightdm-set-defaults --session xubuntu[/FONT]

If you want to change it back just replace xubuntu with ubuntu
Just posting so it won't take someone else as long as it took me to figure out...

---

