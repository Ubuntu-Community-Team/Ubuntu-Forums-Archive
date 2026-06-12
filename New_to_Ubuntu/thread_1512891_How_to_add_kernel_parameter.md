---
title: "How to add kernel parameter?"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by pk3 on 2010-06-18
I need to replace "quiet splash" with "nomodeset" permanently. I know how to get to GRUB, edit it out, replace it, but how do I make this change permanent? I'm on Ubuntu 10.04. Please give step by step instructions, I'm new to this.

---

### Post by drs305 on 2010-06-18
Open the following file as root (to get to the terminal: Applications, Accessories, Terminal):
```
gksu gedit /etc/default/grub
```

Find the following line and add your instruction to, or replace what is already there (as desired). 
> GRUB_CMDLINE_LINUX_DEFAULT=
Make the addition, save the file, then run:
```
sudo update-grub
```
to automatically place the instructions into the grub menu instructions (in /boot/grub/grub.cfg).

---

### Post by pk3 on 2010-06-18
> **drs305 said:**
> Open the following file as root (to get to the terminal: Applications, Accessories, Terminal):
```
gksu gedit /etc/default/grub
```Find the following line and add your instruction to, or replace what is already there (as desired). 

Make the addition, save the file, then run:
```
sudo update-grub
```to automatically place the instructions into the grub menu instructions (in /boot/grub/grub.cfg).

Thank you!!@

---

