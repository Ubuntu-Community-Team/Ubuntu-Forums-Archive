---
title: "First 9.04 installation Wine question"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by paynek716 on 2009-07-12
Just finished first installation of 9.04, happy so far with the switch from Vista.

Regarding Wine, should I install the stable 1.0.1, or the dev version 1.1.25? The only Windows apps I use much are MS Office 2007 and Quicken Basic 2007. I prefer Open Office and only use MS Office when I have to.

Computer is a Dell Inspiron 1501 laptop, 500GB HD, 2GB RAM. AMD Sempron 1.8GHz processor.

Thanks!

---

### Post by LewRockwell on 2009-07-12
when in doubt, go stable

.

---

### Post by AndThenWhat on 2009-07-12
Looks like WINE 1.1.24 is a good version to use with Office 2007 according to this Wine HQ entry:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12811&iTestingId=41803](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12811&iTestingId=41803)

You're probably going to have to run these commands in a terminal in order to get it working:

Applications -> Accessories -> Terminal

```
wget http://www.kegel.com/wine/winetricks
sh winetricks vcrun2005sp1
sh winetricks dotnet20
sh winetricks msxml3 gdiplus riched20 riched30

```

---

### Post by paynek716 on 2009-07-13
Thanks for your responses. I'll likely try stable first, upgrade to 1.1.24 as required.

---

