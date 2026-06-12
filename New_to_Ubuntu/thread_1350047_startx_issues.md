---
title: "startx issues"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by drinkingbeer on 2009-12-08
I am sure this has been answered many times but I searched for hours and with over 1000 pages of returns I gave up.  I just installed ubuntu 9.10 and when I enter the command startx I get the following error: Xsession: warning: xrdb command not found; X resources not merged.  I am running windows on an ASUS netbook and installed ubuntu with my vmware workstation 6.5.  Any help you can provide would be greatly appreciated as this is my first time using ubuntu or any linux platform.

Thanks,
John

---

### Post by Locke_99GS on 2009-12-08
Did you install the minimal CD? Installing from the conventional LiveCD should result in a fully functional desktop.

Try ```
sudo apt-get install ubuntu-desktop
```

---

### Post by sotris99 on 2010-04-26
i have a pentium ii 366mhz and i installed ubuntu karmic netboot with icewm...
 
when i type startx i get the message above...
 
on debian linux i just type X -configure and i put xorg.conf to /etc/X11
 
in ubuntu where is xorg.conf
 
please i don't want gnome or sth like that...
 
my p ii kicks *** with icewm...

---

