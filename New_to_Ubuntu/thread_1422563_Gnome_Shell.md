---
title: "Gnome Shell"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by Dobbie03 on 2010-03-05
How do I replace metacity with gnome shell permanently? 

I have it running know and I started it through the terminal using 

gnome-shell --replace

but I want to close the terminal and it says there s still a process running, I assume that is gnome shell.

What do I need to do?

---

### Post by Ozymandias_117 on 2010-03-05
System -> Preferences -> Startup Applications then click "Add" name it whatever you want then for command use the gnome-shell --replace Then log out and log back in.

edit: Or if you're only wanting to do it on a one time kind of a thing, you can, in a terminal, use the command "gnome-shell --replace &"

---

### Post by Kulgan on 2010-03-05
> **Ozymandias_117 said:**
> Or if you're only wanting to do it on a one time kind of a thing, you can, in a terminal, use the command "gnome-shell --replace &"

Gnome-shell will still end when the terminal is closed. 

Hit Alt-F2 and run it from there.

---

### Post by Dobbie03 on 2010-03-05
> **Ozymandias_117 said:**
> System -> Preferences -> Startup Applications then click "Add" name it whatever you want then for command use the gnome-shell --replace Then log out and log back in.

edit: Or if you're only wanting to do it on a one time kind of a thing, you can, in a terminal, use the command "gnome-shell --replace &"

Thanks works perfectly.

---

