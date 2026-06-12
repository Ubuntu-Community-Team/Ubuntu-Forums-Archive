---
title: "problem with dual monitor"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by supererki on 2009-04-28
Hello

im having some difficulties setting up dual monitors on ubuntu 8.04.
The thing is that it shows TTY1 on my TV (its mirrored when i switch to TTY1) but GUI is running in TTY7 . so how can i chance it ?
lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)

thanks.

---

### Post by Kareeser on 2009-04-28
Can't you set it up in gnome-display-properties?

Also check System -> Administration for an ATi configuration tool.

---

