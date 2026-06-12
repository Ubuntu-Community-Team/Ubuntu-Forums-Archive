---
title: "Gdebi.....Where are you?"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by wormturns on 2009-08-12
Hey,

I have to load some packages in order to get a modem online (ie. don't yet have access to the internet).

Have Gdebi ("local" package installer included with 9.04) installed through Synaptic and Gdebi is supposed to include GUI. How do I access Gdebi through Ubuntu 9.04? In other words, it's installed but I don't know how to find it to get it running.

Thanks.

---

### Post by angry_johnnie on 2009-08-12
Alt + F2

```
gdebi-gtk
```

or

double click whichever *.deb package you're trying to install.  it will automatically open it with gdebi.

:-)

---

### Post by oldos2er on 2009-08-12
Follow the menus Applications, System Tools, GDebi Package Installer. Or simply double-click on a *.deb file, and it should open in GDebi.

---

### Post by wormturns on 2009-08-12
Thanks for the replies. 
I thought it would show up in "Applications, System Tools" menu, but it did not (might I need to reboot?). Was thinking there may be a manual way to put it in the menu through preferences or some such. I'll try the double click on the file approach.

---

### Post by CatKiller on 2009-08-12
It's there but hidden by default, as I understand it. Right click on the menu and select Edit Menus, find it in the list and put a tick in the box if you really want it in the menu for some reason.

---

