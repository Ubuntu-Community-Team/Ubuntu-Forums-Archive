---
title: "[SOLVED] Hyperthreading"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by biggiemokey on 2008-12-24
I have Hyperthreading technology on my PC and am going to install Ubuntu soon.  Can someone explain to me how I would take advantage of HT?  I was reading a thread where people were talking about an SMP kernel and editing the grub list but I do not know what any of that means.  Any help is greatly appreciated.

---

### Post by taurus on 2008-12-24
The generic kernel (the default) gives you both CPU0 & CPU1.

---

### Post by Rocket2DMn on 2008-12-24
If you install Ubuntu, it will automatically recognize your hardware type, so when you run this command to check info about your kernel:
```
uname -a
```
You will see something like
```
Linux compy686 2.6.24-20-generic #1 SMP Mon Jul 28 13:49:52 UTC 2008 i686 GNU/Linux
```
SMP is autodetected.

---

