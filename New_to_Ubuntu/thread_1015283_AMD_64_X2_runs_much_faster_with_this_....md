---
title: "AMD 64 X2 runs much faster with this ..."
date: 2008-12-18
forum: New to Ubuntu
---

### Post by cwmoser on 2008-12-18
I found that my AMD 64 X2 runs much vaster with this switch:

When you get the Grub boot menu, edit the "kernel" boot string by adding the following switch:

**pci=nomsi**


Any other special tweaks for the AMD Processor or special ones for the Intel processor?

Carl

---

### Post by bobnutfield on 2008-12-18
I have that processor in my laptop.  What does that switch do?  What is it turning off and are there any other effects you've noticed?

---

### Post by PocketDog on 2008-12-18
Crikey. [http://lwn.net/Articles/44139/](http://lwn.net/Articles/44139/) I'm still none the wiser [img]http://geocities.com/mrpock2002/heh.gif[/img]

---

### Post by Izek on 2008-12-18
> **PocketDog said:**
> Crikey. [http://lwn.net/Articles/44139/](http://lwn.net/Articles/44139/) I'm still none the wiser [img]http://geocities.com/mrpock2002/heh.gif[/img]

Glad I'm not disabling MSI then, I have PCI Express slots.

---

### Post by PocketDog on 2008-12-18
Me too. I'm going to try it after work and watch the pretty error messages

---

