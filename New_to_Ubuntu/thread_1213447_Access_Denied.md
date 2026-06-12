---
title: "Access Denied"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by bobheaps on 2009-07-14
I am trying to use grsync to make my home folder on my laptop the same as my home folder on my desktop. When I run it I get the following message:-
rsync: mkstemp "/home/bobheaps/.gvfs/bobheaps on laptop on bobheaps-laptop/Accounts/.network test.9YjUgs" failed: Permission denied (13)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1058) [sender=3.0.5]
Could someone help me please?

---

### Post by gackt on 2009-07-15
Sudo? Have you try to call it from terminal with sudo? sudo grsync

---

