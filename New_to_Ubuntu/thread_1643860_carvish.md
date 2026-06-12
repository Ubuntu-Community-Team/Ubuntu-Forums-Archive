---
title: "carvish"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by carvish on 2010-12-12
ok, Ive downloaded the newest version 10.10 I have made a stick drive out of the iso, should I uninstall the Wubi version and proceed to install the new version? What happens if the grub2 acts up again and I can't load either OSes? Why is it that Ubuntu is so user friendly, but in order to use grub 2 you need a 18 page user manual?

so many questions, so little time!!!
carvish

---

### Post by TeoBigusGeekus on 2010-12-12
If lucid works for you, stay with it. Maverick is too buggy (IMO).

---

### Post by carvish on 2010-12-12
tks for the "honest" answer, you are right, I'll just put up with the short memory span(LOL)maybe I'll just upgrade through lucid to 10.10

---

### Post by TeoBigusGeekus on 2010-12-13
> **carvish said:**
> tks for the "honest" answer, you are right, I'll just put up with the short memory span(LOL)maybe I'll just upgrade through lucid to 10.10

Nah, wait for natty.

---

### Post by QLee on 2010-12-13
[QUOTE=carvish]... should I uninstall the Wubi version and proceed to install the new version? What happens if the grub2 acts up again and I can't load either OSes? Why is it that Ubuntu is so user friendly, but in order to use grub 2 you need a 18 page user manual [/QUOTE]

The answer to this is that the GRUB bootloader wasn't meant to be used with a Wubi install.

Wubi was crafted to be an easy way for Windows users to try Ubuntu and easy to uninstall. Wubi installs like other Windows programs and has an uninstaller like other windows programs. Wubi uses the Windows bootloader and menu and exists on a Windows partition as a virtual filesystem.

Many of the experienced users in the forum recommend using a "real" Ubuntu install after a user has tried Ubuntu out and decided to keep it. A confusion comes when GRUB is installed and/or upgraded on a Wubi install, thus overwriting the Windows Master Boot Record which is needed to get to the Windows menu that is installed with a Wubi install.

Many people do a simple Ubuntu install on a separate Linux type partition using the GRUB2 bootloader on a dual boot system and don't have trouble. Some make mistakes and mistakes and problems are what we see in the help forums, obviously people who don't have trouble don't post for help.

The reason an "18 page user manual" is needed is that GRUB2 is relatively new and many people haven't learned all about it yet, they make mistakes trying to use it like legacy GRUB. Once the GRUB2 methods are learned, it works well for users. ...and there are lots of people here on the forums to help.

---

### Post by amjjawad on 2010-12-13
> **carvish said:**
> ok, Ive downloaded the newest version 10.10 I have made a stick drive out of the iso, should I uninstall the Wubi version and proceed to install the new version? What happens if the grub2 acts up again and I can't load either OSes? Why is it that Ubuntu is so user friendly, but in order to use grub 2 you need a 18 page user manual?

so many questions, so little time!!!
carvish


Few words: GRUB2 RULES :)
Enough said!

I'm saying this because simply without GRUB2 and its amazing features, I would never be able to set my two PCs the way these are at the moment.

---

### Post by carvish on 2010-12-14
whats with the "grub puts not found"then?

---

### Post by amjjawad on 2010-12-15
> **carvish said:**
> whats with the "grub puts not found"then?

1) Please, read more about GRUB2 so that you'll be more familiar with it. 
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)


2) After that, please post the result of the below link here and please wrap up the page with "#" or "CODE" tags.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

