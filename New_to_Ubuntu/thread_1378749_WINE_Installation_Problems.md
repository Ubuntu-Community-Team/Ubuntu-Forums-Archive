---
title: "WINE Installation Problems"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by BeanInvasion on 2010-01-11
When I try installing WINE through the software center, it gives me an error saying "Fix Broken Packages First". I went to the Package Manager and Fixed Broken Packages, tried to install again, and it gave me the same message.  I have no idea which packages I'm supposed to fix, and I've searched everywhere. I tried everything these pages suggested:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=947124](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=947124)
[http://www.pubbs.net/wine/200912/76957/](http://www.pubbs.net/wine/200912/76957/)
But I still get the same message. When I go to my terminal and try to install it through there by entering 'sudo apt-get install wine1.2' it when it asks me if I'm sure I want to, after I enter y it tells me 'abort' and nothing happens.

I'm on Karmic Koala, I followed all the instructions from the Wine Ubuntu installation page, and added *ppa:ubuntu-wine/ppa *to my other software list in software sources.
Can somebody please help me?!

---

### Post by ubudog on 2010-01-11
> **BeanInvasion said:**
> When I try installing WINE through the software center, it gives me an error saying "Fix Broken Packages First". I went to the Package Manager and Fixed Broken Packages, tried to install again, and it gave me the same message.  I have no idea which packages I'm supposed to fix, and I've searched everywhere. I tried everything these pages suggested:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=947124](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=947124)
[http://www.pubbs.net/wine/200912/76957/](http://www.pubbs.net/wine/200912/76957/)
But I still get the same message. When I go to my terminal and try to install it through there by entering 'sudo apt-get install wine1.2' it when it asks me if I'm sure I want to, after I enter y it tells me 'abort' and nothing happens.

I'm on Karmic Koala, I followed all the instructions from the Wine Ubuntu installation page, and added *ppa:ubuntu-wine/ppa *to my other software list in software sources.
Can somebody please help me?!

First, do this for the broken packages: ```
dpkg --configure -a
``` Second, I think the package is called "wine", not "wine1.2" so try ```
sudo apt-get install wine
```

---

