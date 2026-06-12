---
title: "Really need some help with wireless"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by rob reza on 2008-01-14
**Hi I've just installed ubunto four days ago and am having trouble trying to get wireless it don't show up in my network manger  and my atheros says unclaimed and i'm having trouble installing ndiswrappers and i can't find window drivers with 64bit some one please help?**

---

### Post by Hightide on 2008-01-14
Hi, you may find the this thread useful 

[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

:)

---

### Post by rob reza on 2008-01-14
hey thanks but i have a atheros ar5006eg build in card but it might be ar5007eg i've been reading some thread and alot  say ubuntu reads it as a  ar5006eg:confused:

---

### Post by rustybronco on 2008-01-14
> **rob reza said:**
>  i have a atheros ar5006eg build in card but it might be ar5007eg i've been reading some thread and alot  say ubuntu reads it as a  ar5006eg:confused:That is correct.

there is thread that may help you [http://ubuntuforums.org/showthread.php?p=4085733#post4085733](http://ubuntuforums.org/showthread.php?p=4085733#post4085733)
starting with post 24'ish

---

### Post by wirelessmonkey on 2008-01-14
If you have a network connection, you may just want to: sudo apt-get install madwifi-ng

---

### Post by rob reza on 2008-01-14
**hey thanks but  That what got back but i have 64bit and ever patch i have read about is for 32bit so does any one know of a 64bit drive compatible with atheros ar5007eg**

razer@razer-laptop:~$ sudo apt-get install madwifi-ng
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package madwifi-ng

---

