---
title: "Permission to edit /etc/modprobe.d/alsa-base"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by webwiller on 2009-03-08
It's surely a sillt question but...
I need to edit the above mentioned file...but with nautilus I get the answer that I have no permission. Obviously the file is owned by root and I dont know how to switch to root.

Otherwise..which code do I have to use in terminal to open that file as root to edit?

sudo....???

ty;)

---

### Post by webwiller on 2009-03-08
I have Ubuntu...not Ku..

---

### Post by HavocXphere on 2009-03-08
Hit alt-f2. Type in:
```
kdesudo kate /etc/modprobe.d/alsa-base
```
:KS

---

### Post by taurus on 2009-03-08
```
gksudo gedit /etc/modprobe.d/alsa-base
```

---

### Post by webwiller on 2009-03-08
I made a mistake...dont have kubuntu, have ubuntu...
so it's sudo then...which is the terminal command for "edit"?

---

### Post by xpod on 2009-03-08
> so it's sudo then...which is the terminal command for "edit"?

See taurus` post above yours.You should use "gksudo" as apose to "sudo" when opening graphical applications.

---

### Post by nyk on 2009-03-08
gedit will open a simple text editor GUI. If you want an editor based completely in the terminal, use vim.

---

### Post by HavocXphere on 2009-03-08
> **webwiller said:**
> I made a mistake...dont have kubuntu, have ubuntu...
My bad..kinda missed the second post.:oops:

---

