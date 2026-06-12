---
title: "messed up booting"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by itsbrad212 on 2009-11-16
I'm running off the live cd right now. When i installed slackware on a separate partition, it worked fine, but when i went to boot up, the option to boot into ubuntu wasnt there. I checked my partitions and the ubuntu one is still there. ANY help will be greatly appreciated. If you need more info, just ask :D

---

### Post by brij on 2009-11-18
so you mean when the grub appears there is no entry for ubuntu? if yes than check the /boot/grub/menu.lst and make sure there is an entry for ubuntu.if its missing then you need to add it

hope this will help

---

