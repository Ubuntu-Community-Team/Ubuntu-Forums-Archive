---
title: "Boot screen help!"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by samoht83 on 2011-08-23
Hey all, I am a very new user of Ubuntu love it. So I decided to install kubuntu and xubuntu from the terminal to give those a try also. Now my startup screen says edubuntu and my shutdown screen says ubuntu. I have tried many options to get them both to say Ubuntu like it does when you only have Ubuntu installed, such as gnome-splashscreen-manager and a terminal command that let me change the shutdown screen. Is there anything I can do to get my Ubuntu startup screen back?

---

### Post by sisco311 on 2011-08-23
Hi and welcome to the forums!

Open a terminal and run:
```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
```

The first command will list available themes to choose from, the second command with update initramfs with a new theme.

---

### Post by samoht83 on 2011-08-23
Thank you! That did the trick.

---

### Post by sisco311 on 2011-08-23
You are welcome!

---

