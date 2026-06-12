---
title: "[SOLVED] Trash Bin Root Access?"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by mapes12 on 2008-12-14
I've ended up with a folder with some files in it in my trash bin but I need root access to remove it. I can't even find the path to enter a command line ```
sudo rm
``` to get rid of it. Any ideas?

---

### Post by Moop on 2008-12-14
```
gksudo nautilus
``` will open a nautilus window with sudo privileges and you can empty the trash.

---

### Post by bluefrog on 2008-12-14
apps/accessories/terminal

sudo rm -rf ~/.local/share/Trash/*

---

### Post by northern lights on 2008-12-14
Run ```
sudo rm -rf ~/.local/share/Trash/*
``` from a terminal.

[EDIT]
late...
[/EDIT]

---

