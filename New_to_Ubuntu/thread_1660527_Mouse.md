---
title: "Mouse"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by Metungkp on 2011-01-05
Belkin #F8e825-USB

Micrsoft says it only works with 32 BIT systems.  

I've only been on Ubuntu a week, it has been great so far and everyone has been very helpful.  I have a 64 bit PC, I wanted to know, since I have now Ubuntu on my computer, will this work on my computer? I plugged it in and it doesn't, is there something I can do to make it work?

Any help is appreciated.

Thanks!

---

### Post by khelben1979 on 2011-01-06
From the Belkin homepage they don't offer any drivers for your mouse, so the only thing to do is to check the following in /etc/X11/xorg.conf:
> Section "ServerLayout"
        InputDevice    "Configured Mouse"
EndSection

If the Ubuntu system don't recoqnize that attached USB mouse with the above setting, then there is nothing you can do other than to attach another mouse if you got one.

---

### Post by Metungkp on 2011-01-06
metungkp@MetungKP:~$ /etc/X11/xorg.conf:
bash: /etc/X11/xorg.conf:: No such file or directory
metungkp@MetungKP:~$

---

### Post by khelben1979 on 2011-01-07
> **Metungkp said:**
> metungkp@MetungKP:~$ /etc/X11/xorg.conf:
bash: /etc/X11/xorg.conf:: No such file or directory
metungkp@MetungKP:~$

I forgot that they have removed xorg.conf with newer releases of Ubuntu. There is a possibility to recreate one, but I don't think it will help in this case.

Just try with another mouse, would be my suggestion.

---

