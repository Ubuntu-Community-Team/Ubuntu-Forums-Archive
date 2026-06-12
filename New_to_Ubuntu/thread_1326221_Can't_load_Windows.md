---
title: "Can't load Windows"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by Kenta92 on 2009-11-14
I installed Wubi and everything works fine, exept i can't access to Windows anymore. I had Windows boot manager and Grub 1.94beta at every start, so using Windows i chose to not showing the Windows boot manager everytime, and going with Ubuntu directly. I did this because Grub did let me chose between Windows and Ubuntu everytime, but it doesn't do it anymore.
It only asks me if i want to load:
Ubuntu Linux 2-6.31-14-generic
Ubuntu Linux 2-6.31-14 recovery mode
Ubuntu

before removing the windows boot manager, the 3rd was Windows.

I really don't know how to load Windows and i really need to fix this as soon as possible.

Thanks

---

### Post by Paqman on 2009-11-14
You still need the Windows boot manager, as Grub chainloads into NTLDR, which in turn launches Windows. Grub can't actually launch Windows on it's own.

---

