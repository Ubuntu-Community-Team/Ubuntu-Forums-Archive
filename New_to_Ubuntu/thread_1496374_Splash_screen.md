---
title: "Splash screen"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by frozenflames on 2010-05-29
How to change splash screen on startup of ubuntu 10.4 and also the login prompt :(

---

### Post by Flimm on 2010-05-29
The splash screen when booting up uses Plymouth, and the login screen uses Xsplash.

[Epidermis](http://epidermis.tuxfamily.org) (a theme manager for GNOME) supports Xsplash themes, but not Plymouth themes yet.

You can try looking on [gnome-look.org](http://gnome-look.org) for Xsplash and Plymouth themes.

To install an Xsplash theme, copy the files in the archive to /usr/share/images/xsplash (you'll need root access).

Plymouth theming is a bit more complicated in Lucid. I'd recommend searching the repos and installing the ones in there. For example:

```
sudo apt-get install plymouth-theme-glow
```

Then select the theme you want by running: ```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
```

---

### Post by frozenflames on 2010-05-29
:KSThank you So much it worked and i changed my startup splash screen and also on a another note i was living a lie with windows coz linux is more sexy and more reliable:KS

---

