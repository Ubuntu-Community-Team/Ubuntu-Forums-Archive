---
title: "uninstalled and reinstalled wine..now i get an error"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by jager8113 on 2009-01-15
I updated wine to get a game working...this messed up my old games so I removed wine...then i reinstalled it..Now when I try to reinstall my game (morriwind) it give me this error:
The install shield Engine (ikernal.exe) could not be launched. (0x8002802b).

Last tiem this happened I reinstalled Ubuntu..but I dont wanna do that again...Plz help!!! And thank you for taking your time to help!!!

BTW:ubuntu 7.04

---

### Post by albinootje on 2009-01-15
> **jager8113 said:**
>  Last tiem this happened I reinstalled Ubuntu..but I dont wanna do that again...

With PlayOnLinux you can use separate games in separate Wine "bottles". And you can also easily manage different Wine versions.

[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

---

### Post by jager8113 on 2009-01-15
I installed playonlinux...but when i run it and ask it to install morrwind..same message appears as before....

---

### Post by stefangr1 on 2009-01-15
What you can try is:
sudo apt-get purge wine

and then reinstall:
sudo apt-get install wine

---

### Post by jager8113 on 2009-01-15
> **stefangr1 said:**
> What you can try is:
sudo apt-get purge wine

and then reinstall:
sudo apt-get install wine


I just did this, but it didnt help..it seems as though all wine files are not removed when its uninstalled..i have look for hours trying to find a way to delete all the "loose ends" as well...with no luck

---

### Post by stefangr1 on 2009-01-15
OK, I thought maybe purge in stead of uninstall would help, since it usually removes all configuration files as well.

---

### Post by jager8113 on 2009-01-15
> **stefangr1 said:**
> OK, I thought maybe purge in stead of uninstall would help, since it usually removes all configuration files as well.

np man...thank you for trying to help...i apprecate it alot

---

### Post by albinootje on 2009-01-15
> **jager8113 said:**
> I installed playonlinux...but when i run it and ask it to install morrwind..same message appears as before....

Can you do the following :
```

mv ~/.wine ~/.wine-old-copy

```
And then try again.

---

