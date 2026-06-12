---
title: "scim unable to type chinese in  openoffice or firefox"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by afeasfaerw23231233 on 2008-12-17
hi, i followed this tutorial and install scim for my kubuntu 8.04. I can type chinese in kate or renaming file. But I can't type chinese in firefox , openoffice , or any other things else. I don't know what to do. Thanks!!

---

### Post by mrbiggbrain on 2008-12-17
> **afeasfaerw23231233 said:**
> hi, i followed this tutorial and install scim for my kubuntu 8.04. I can type chinese in kate or renaming file. But I can't type chinese in firefox , openoffice , or any other things else. I don't know what to do. Thanks!!

firefox is based off of GTK (if im right) im not firmilure with scim, but maybe it can only affect some applications which use the kernel for things, like open office which is built off a diffrent set of systems. not everything supports it.

also try useing a unicode format for openoffice if its not already, i belive that supports chineese (might be ur issue)

---

### Post by Metallion on 2009-01-18
Is the problem still there? For openoffice you need to type this command

```
scim -d -c socket -f x11 -e socket
```

For firefox:

```
sudo apt-get install scim-gtk2-immodule
```

---

### Post by Kosimo on 2009-01-18
scim is **[COLOR="Red"]bul·lshit[/COLOR]** guys....  I've always had problems when trying to have catalan/korean keyboard.... When someone works, the other won't... Then I can write korean in some apps, but not in nautilus, or vice versa...

There is a lot of job to do here. We REALLY need something new to choose the keyboard layout that can actually works in ALL apps changing layout with just one click, in QT, GTK+, FLASH, JAVA...

---

### Post by lanruisen on 2009-01-21
These two posts got scim working for me on all my apps for Chinese both traditional and simplified. 

[HTML] http://ubuntuforums.org/showthread.php?t=528382[/HTML]

[HTML] http://www.debian.org.tw/index.php/scim[/HTML]

---

