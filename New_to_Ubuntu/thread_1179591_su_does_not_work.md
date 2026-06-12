---
title: "su does not work"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by Mattaus on 2009-06-05
Kind of embaressing but when i'm in the terminal and type 

> su

and then enter my password which works for everything else, it says permission denied.

It's a pain in the bum because I cannot edit the blacklist folder which in turn does not allow me to use ndiswrapper properly and hence makes my wireless card problem even worse. In fact if I use gedit or vi to edit the modprobe file (to blacklist old wireless drivers) I can't save it at all because it says permission denied...

I know I am missing something very obvious but I'm so sick of trawling through the forums turning up dead ends.

Help please!!!

---

### Post by DGortze380 on 2009-06-05
The root account is disabled by default in Ubuntu.

Official Answer: Use sudo and gksudo

Disclaimer: It is possible to enable the root account. There are valid reasons to do it. But it's against forum rules to say how.

---

### Post by Mattaus on 2009-06-05
I figured it was along those lines...thanks for that. Worked a charm.

---

### Post by binbash on 2009-06-05
sudo su -

---

### Post by Celauran on 2009-06-05
> **binbash said:**
> sudo su -

That's just asking for trouble.

---

### Post by jnw222 on 2009-06-05
lol  asking for trouble

---

