---
title: "trash wont empty"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by bu2971x on 2009-04-14
whats with the trash ,it doesnt empty, delete..???

---

### Post by scragar on 2009-04-14
> **bu2971x said:**
> whats with the trash ,it doesnt empty, delete..???

I can't remember if Hardy's trash is in ~/.local/share/Trash or ~/.Trash

Sounds like for some reason you moved something to trash while using sudo to gain temp root perms. It should be solved by running:
```
sudo rm -Rf ~/.local/share/Trash/* ~/.Trash/*
```
You can find the terminal under applications in the gnome-menu, or system under the k-menu.

---

### Post by bu2971x on 2009-04-15
good one
solved

---

