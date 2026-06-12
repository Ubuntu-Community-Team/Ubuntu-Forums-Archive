---
title: "Terminal Query"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by guv999 on 2009-04-20
hi
I am stuck on something and it is probably quite simple to fix.   I am trying to access the config of Mediatomb, and am entering the following line of text:

sudo /home/dave/.mediatomb/config.xml

The response I get is...

sudo: /home/dave/.mediatomb/config.xml: command not found

Not sure what I am doing wrong. 

Thanks

---

### Post by LowSky on 2009-04-20
gedit /home/dave/.mediatomb/config.xml

shouldnt need sudo, its in your home folder, meaning the local user is the owner, not root

---

### Post by SuperSonic4 on 2009-04-20
You'll need to use a text editor such as nano, vi or gedit

---

### Post by ddrichardson on 2009-04-20
```
gedit /home/dave/.mediatomb/config.xml
```Back it up first```
cp ~/.mediatomb/config.xml ~/.mediatomb/config.xml.old
```

---

### Post by guv999 on 2009-04-20
Thanks very much - all sorted now

---

### Post by Penguin Guy on 2009-04-20
Typho, don't run this code:
> **ddrichardson said:**
> ```
cp ~/.mediatomb/config.[COLOR="Red"]c[/COLOR]ml ~/.mediatomb/config.xml.old
```
Fixed code: [COLOR="DimGray"]cp ~/.mediatomb/config.xml ~/.mediatomb/config.xml.old[/COLOR]

---

### Post by ddrichardson on 2009-04-20
Well spotted, FWIW using tab completion avoids mistypes so I'd advise it to new users rather than copy/pasting.

---

