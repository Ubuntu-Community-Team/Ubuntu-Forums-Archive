---
title: "Ubuntu Not Starting"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by peace.gangsta on 2010-01-23
I installed Ubuntu Advanced Compiz fusion effects.I was checking features like reflection,3D effects etc. when suddenly it hanged .
Now when I am restarting ubuntu (9.10) and it gets stuck on the screen which comes after the login screen.The start-up music gets played well but the desktop is simply not loading.
Help please!

---

### Post by cariboo on 2010-01-23
Use your Live CD to repair the file system.

[list]
[*] boot from the Live CD
[*] once at the desktop, open an Applications->Accessories-> Terminal
[*] Type sudo fsck -a /dev/sda
[*] when fsck is finished reboot
[/list]

Substitute your partition for /dev/sda

---

