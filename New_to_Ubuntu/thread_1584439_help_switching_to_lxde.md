---
title: "help switching to lxde"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by jonnny_j22 on 2010-09-29
Hi all, 

Whilst on my last holiday the hotel let you rent out netbooks and they had LXDE on them. I got to liking this so now I'm back I've put it on my own netbook but I can't seem to get the wireless to work. Ubuntu found all my hardware straight away with gnome so I don't actually know how to fix this. does anyone know any good pages they could point me in the direction of please?

Thankyou in advance

---

### Post by KIAaze on 2010-09-29
I use Lubuntu:
[http://lubuntu.net/](http://lubuntu.net/)

You should be able to install it with:
```
sudo apt-get install lubuntu-desktop
```

I currently use "NetworkManager Applet 0.8", which I think is "nm-applet" from the "network-manager-gnome" package, i.e. the same default networking manager as in Gnome.

On my first installation of Lubuntu, I think I had wicd:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
(also in the repositories)

---

### Post by philinux on 2010-09-29
> **jonnny_j22 said:**
> Hi all, 

Whilst on my last holiday the hotel let you rent out netbooks and they had LXDE on them. I got to liking this so now I'm back I've put it on my own netbook but I can't seem to get the wireless to work. Ubuntu found all my hardware straight away with gnome so I don't actually know how to fix this. does anyone know any good pages they could point me in the direction of please?

Thankyou in advance

```
sudo apt-get install lxde
```

Then at the login page choose your session.

---

