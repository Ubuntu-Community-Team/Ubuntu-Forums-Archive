---
title: "change grub settings"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-12-25
first like always i tried to figure this out my self  ref this link

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

all i want to do is set grub so the screen stays open until i select an option
cant figure out what to comment or uncomment and where to put the -1

here is a copy of my current grub settings

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" quiet"

---

### Post by Verbeck on 2010-12-25
you should change the GRUB_TIMEOUT=**10 **to[B] -1


[/B]

---

### Post by XeonBloomfield on 2010-12-25
```
GRUB_TIMEOUT=86400
GRUB_HIDDEN_TIMEOUT=1
```
Set it like I write.

Timeout = 86400 = 24 hours
Uncoment line "GRUB_HIDDEN_TIMEOUT=0" and set to "1".

It will wait one day until you select system and counter will be hiden.

---

### Post by karthick87 on 2010-12-25
Change the grub timeout value to -1 and update your grub.
> GRUB_TIMEOUT=-1```
sudo update-grub
```

---

### Post by rburkartjo on 2010-12-25
tks  ya'll i had to also remove the # from
#GRUB_HIDDEN_TIMEOUT=0

and then change time out to -1 as you suggested
works great

---

### Post by karthick87 on 2010-12-25
Mark this as[COLOR=Red] [SOLVED][/COLOR]

---

