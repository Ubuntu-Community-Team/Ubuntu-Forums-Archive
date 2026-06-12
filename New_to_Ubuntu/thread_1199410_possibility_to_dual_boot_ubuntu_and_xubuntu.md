---
title: "possibility to dual boot ubuntu and xubuntu?"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by cirabisi2009 on 2009-06-28
yes indeed, i want to dual boot ubuntu and xubuntu. why? i honestly just want to explore what each one has ( kubuntu, xubuntu, edubuntu, and fedora 10 ) . i already realized that wubi will not allow this. and i cannot find a .iso for each one of these, only ubuntu ( i honestly havent explored for fedora ).
but thank you for the help guys <edit> and girls :)

---

### Post by zeroseven0183 on 2009-06-28
> **cirabisi2009 said:**
> yes indeed, i want to dual boot ubuntu and xubuntu. why? i honestly just want to explore what each one has ( kubuntu, xubuntu, edubuntu, and fedora 10 ) . i already realized that wubi will not allow this. and i cannot find a .iso for each one of these, only ubuntu ( i honestly havent explored for fedora ).
but thank you for the help guys <edit> and girls :)


Of course you can download .ISOs for each of the flavors you mentioned. If you're already using Ubuntu, you can download/install Xubuntu with

```
sudo apt-get install xubuntu-desktop
```If you want to switch desktops, log out from that session and select the other from the log in screen.

---

### Post by cirabisi2009 on 2009-06-28
indeed, but i did forget to mention i am also booting windows xp? so maybe like a multi-bootable ? and im guessing that command line, i can just substitute the xubuntu with another flavor name to boot from as well?

---

### Post by brewkakke on 2009-06-28
It doesn't matter, it's not really dual-booting in the same sense as running two operating systems.  You still have the same Linux kernel, it's basically just installing the xfce desktop in addition to the gnome desktop.

I have Ubuntu and Kubuntu running right now.  When you install the other one, just logout and on the bottom left of the login screen you can click "Options" and then choose another session.  You'll see a selection for GNOME or XFCE desktop, just choose your poison and it will ask you if you want to make it the default for everytime you login.

I'd take the route of installing Ubuntu first and then installing Xubuntu from the terminal in Ubuntu.  Just go by the instructions zeroseven posted.

---

### Post by ~sHyLoCk~ on 2009-06-28
Youcan just install different Desktop Environments and try them out. If you already have ubuntu{which is GNOME} then you can download xubuntu-desktop and also kde4 from synaptic

---

### Post by cirabisi2009 on 2009-07-06
```
sudo apt-get install easypeasy-desktop
```

will that work? and

```
sudo apt-get install kubuntu-desktop
```

and will that work?

---

### Post by DCGStudios on 2009-07-06
It really does not make much sense to do this unless you plan on playing with different versions of Ubuntu. Follow the steps given from the posts before me and just log out and press "Change session" to change your desktop/window manager. That way your not stuck complicating yourself with dual booting and having to restart just to change something as simple as a desktop manager.

---

### Post by cirabisi2009 on 2009-07-06
> **DCGStudios said:**
>  plan on playing with different versions of Ubuntu. 

thats what im gonna do, i just wasnt sure if those would properly install those flavors or would it just put a bunch of unnecessary stuff on my computer

---

