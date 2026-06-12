---
title: "Install an update, lose your panels! GREAT! Help?"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by RAZRBAKK on 2009-07-23
Hey folks,

I installed an update which did some Firefox update. It asked me to restart the browser, which I did, but then everything froze. 'No Big' I thought, and restarted the system. Upon arriving at my desktop, I found that I have no panels. I also don't have the ability to open terminal. 

I did get into the TTY and issued 
```

rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

To no avail. I also tried to create a launcher, but the screen flickers once, then remains the same.

Are there any suggestions other than a good ol' back up/re-install?

---

### Post by jimmy the saint on 2009-07-23
does alt-f2 work?  if it does, try hitting alt-f2 and type in ```
nautilus
```
if you have no icons, that may mean that nautilus isn't running
do it again and type in ```
metacity --replace
```
if windows wont open, it could be that you have no window manager running

If you want to play with a terminal, do it again (or first) and tyep in ```
gnome-terminal
```

Without seeing your desktop or having more details, I can't say for sure what your problem is, but this should cover a lot of the bases.

---

### Post by RAZRBAKK on 2009-07-23
> **jimmy the saint said:**
> does alt-f2 work?  if it does, try hitting alt-f2 and type in ```
nautilus
```
if you have no icons, that may mean that nautilus isn't running
do it again and type in ```
metacity --replace
```
if windows wont open, it could be that you have no window manager running

If you want to play with a terminal, do it again (or first) and tyep in ```
gnome-terminal
```

Without seeing your desktop or having more details, I can't say for sure what your problem is, but this should cover a lot of the bases.

alt+F2 does NOT work, I can open windows, and I can't get a terminal open. I got one open by opening the terminal session session at the login menu...

By the way, I'm running Jaunty.

---

