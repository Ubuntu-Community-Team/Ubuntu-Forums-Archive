---
title: "Concrete5 / GD library"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by mörgæs on 2010-05-16
Hi everybody

I am trying to install Concrete5 on a LAMP server on an Ubuntu 9.10 (minimal), but I get the error message

Concrete requires GD library 2.0.1 or greater

Does anybody know what needs to be installed?

---

### Post by mörgæs on 2010-05-17
Installing **php5-gd** after the LAMP installation did the trick.

---

### Post by kapi on 2011-04-17
Perfect! I'm using 10.04 Lucid lynx and already had lamp installed via an installer whose name escapes me, anyway I just opened the synaptic package manager and searched for php5-gd

then selected the program, installed and rebooted the machine.

Now all sections for C5 installer are green and ready to go. 

hope it helps someone ;)

---

