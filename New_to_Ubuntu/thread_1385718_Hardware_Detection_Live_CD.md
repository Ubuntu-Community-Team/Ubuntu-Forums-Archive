---
title: "Hardware Detection Live CD"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by Goveynetcom on 2010-01-19
This is relating to Ubuntu to directly but more to live cd's and Linux in general. Is there a tool/ live cd that can detect and list the name of different hardware pieces, I reinstalled Windows on my old desktop so that I could play my old PC Games and Emulators without slowdown (I don't know why the old console emulators run so poorly on Linux, they run perfect on Windows), and I need to find a bunch of drivers to get them to work. So, know of any?

---

### Post by garvinrick4 on 2010-01-19
> **Goveynetcom said:**
> This is relating to Ubuntu to directly but more to live cd's and Linux in general. Is there a tool/ live cd that can detect and list the name of different hardware pieces, I reinstalled Windows on my old desktop so that I could play my old PC Games and Emulators without slowdown (I don't know why the old console emulators run so poorly on Linux, they run perfect on Windows), and I need to find a bunch of drivers to get them to work. So, know of any?

lspci -v | less

---

### Post by sandyd on 2010-01-19
[http://ubuntuforums.org/showthread.php?t=1385347](http://ubuntuforums.org/showthread.php?t=1385347)

---

### Post by Goveynetcom on 2010-01-19
Thanks, SOLVED!

---

### Post by PenguinInside on 2010-01-20
There's also a graphical program hardinfo that displays hardware information, sort of like some programs in Windows do.

sudo apt-get install hardinfo
[apt://hardinfo]("apt://hardinfo")

---

