---
title: "running: Scripts/innit"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by Hawhaw1 on 2010-08-24
Hey, every time i start up ubuntu, before it reaches the log-in screen  a whloe load of numbers and letters appear very quickly on a black screen.
At the bottom it says running/scripts/innit.
Does anyone know what this is?

Also, sometimes when i log in my internet will not work, it is connected but i just cannot connect to firefox.
Any help?
Cheers

---

### Post by jtarin on 2010-08-24
Do you have more than one kernel to boot with? If yes try to boot with the other kernel and post the results. Also run the command after the next boot ```
gksudo gedit /var/log/boot.log
``` and post that.

---

