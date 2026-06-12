---
title: "GDM wont pop up but usplash will"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2010-01-12
Using Ubuntu Minimal. When I turn on my computer. Usplash will pop the ubuntu logo up but it will take me directly to command line and I have to sign in and type startx rather then take me to gdm. Is there some sort of update command I'm forgetting?

---

### Post by cenzorrll on 2010-01-12
you probably don't have gdm installed, gnome and gdm are separate processes.

to install gdm:
```
sudo apt-get install gdm
```
if you want a more minimal login, you can also install xdm instead, although xdm isn't very good if you want to choose between different desktop environments.

---

### Post by LunaticHiatus on 2010-01-12
nope, its installed. Using lxde as well.

---

### Post by LunaticHiatus on 2010-01-12
didnt get GDM to work, I installed xdm and that worked but everything was huge but it seems to be a known bug. So I tried wdm and that worked, although its ugly as all heck.Would have tried slim but I couldn't find the package for it.

---

