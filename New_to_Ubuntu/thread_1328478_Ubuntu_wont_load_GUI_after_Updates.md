---
title: "Ubuntu wont load GUI after Updates"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by JREAM on 2009-11-16
I went from 9.04 to 9.10 (this is a clean install by the way),
and now I only get a terminal and I dont know how to load the GUI :(

---

### Post by BQAggie2006 on 2009-11-16
Have you tried either of the following commands from the command prompt:

```
startx
```or

```
sudo /etc/init.d/gdm start
```

---

### Post by JREAM on 2009-11-16
I did 
sudo lspci | grep -i vga
grep -i driver /etc/X11/xorg.conf

They say a monitor is there,
I had installed the NVidia drivers but i dont think i changed the xorg.conf file 

it says Fatal Error no screen found now

---

