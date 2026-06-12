---
title: "How 2 Install LXDE without Installing Lubuntu . . ?"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by GregA on 2010-05-07
I have an older PC that runs gnome fairly well, but I'd like to check into LXDE without actually installing Lubuntu . . . in other words, can LXDE be installed in parallel to gnome, and then switched to at user login?   I've never tried concurrently running more than one desktop (gnome or kde)  - - is it problematic?

---

### Post by rax0 on 2010-05-07
Hello, 

You should be able to install LXDE by going to Synaptic and search "lubuntu-desktop" and install it and everything that comes with it!

Have fun.

---

### Post by patchwork on 2010-05-07
The answer is yes, you can install and switch between them.  Your options are the lubuntu-desktop, and LXDE proper. 

```
 sudo apt-get install lxde
```
or
```
 sudo apt-get install lubuntu-desktop
```

---

### Post by dustinmarlowe56 on 2010-05-07
yes, and after you run the sudo apt-get install lxde command, logout, and then change your session option to lxde and log back in.

---

### Post by degarb on 2011-02-21
Where do we do this?     I see nothing in desktop sessions in old environment.  I did however manually run sudo lxsession, where I get a bonus tool bar.  But old tool bars still here.  In the new tool bar, only lxde exists.

---

