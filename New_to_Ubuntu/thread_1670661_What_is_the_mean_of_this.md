---
title: "What is the mean of this?"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by adeee on 2011-01-19
[INDENT]```
sudo aptitude install ubuntu-desktop
```if it is about to install genome again?
or
it is about to default genome logon screen.
well i install kde and chose default splash and login screen kde. and have no any knowledge how to change it to genome. both(splash and login)

[/INDENT]

---

### Post by ajgreeny on 2011-01-19
Did you originally install Ubuntu or Kubuntu?

If it was Kubuntu, the command above will add everything that is needed to give you standard Ubuntu as well, which means the gnome desktop and login screen.

Kubuntu runs with the KDE desktop and login screen.

You can choose which desktop to use at the login screen using the session menu bottom right, but it only appears after you have chosen the username to login to.  You can also choose to have either of the login screens take over with the command ```
sudo dpkg-reconfigure kdm
```and choose from the ones available.

---

