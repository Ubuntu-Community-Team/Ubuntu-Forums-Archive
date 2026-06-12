---
title: "How do I install 9.04 without Grub?"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Razerblader on 2009-01-28
I'm trying to install 9.04 without GRUB but my XP MBR isn't recognizing it if I install it without GRUB. I hate GRUB, but if I have to install it I will. how do I set XP as my first boot option?

---

### Post by bodhi.zazen on 2009-01-28
As you aer finishing the install, on the last box of questions is an advanced tab

In the advanced tab install grub into your UBUNTU PARTITION and NOT you MBR

(you do need grub somewhere).

You will then either need to make a boot disk or configure the windows boot loader

---

### Post by Razerblader on 2009-01-28
Ho do I configure my Windows boot loader?

---

### Post by bodhi.zazen on 2009-01-28
> **Razerblader said:**
> Ho do I configure my Windows boot loader?

I have no idea, I use grub :twisted:

This page has some info : [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

---

### Post by sports fan Matt on 2009-01-28
just slightly off tiopic do you mean 9.04, which hasnt been released and I beleive is in development stage or 8.04 Hardy Heron? Im just curious

---

### Post by Gulyan on 2009-01-28
> **Razerblader said:**
> how do I set XP as my first boot option?

You edit the /boot/grub/menu.lst file.

There is a line:
```
default         0
```
It represents the number of the default operating system as listed in the menu (counting from 0).

*Note that you should also count the "Other operating systems" line.

---

### Post by Razerblader on 2009-01-28
I'm using a jaunty alternate on my laptop :D

---

