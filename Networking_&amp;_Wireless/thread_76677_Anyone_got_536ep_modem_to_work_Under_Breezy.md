---
title: "Anyone got 536ep modem to work Under Breezy?"
date: 2005-10-15
forum: Networking &amp; Wireless
---

### Post by magomago on 2005-10-15
I've tried using the hoary guide to no avail.  I tried using the latest drivers on my own (4.71) but I couldn't modprobe Intel536.ko   I tried using the SL source (From multiverse) and compiling it, but it said kernel version incompatability.

Has anyone using breezy successfully gotten the 536ep modem to work?  LMK, thanks!!

---

### Post by magomago on 2005-10-16
a still-looking-for-a-solution-bump

---

### Post by magomago on 2005-10-18
[QUOTE=magomago]a still-looking-for-a-solution-bump[/QUOTE]

Bump again :9

---

### Post by blastus on 2005-10-18
[QUOTE=magomago]I've tried using the hoary guide to no avail.  I tried using the latest drivers on my own (4.71) but I couldn't modprobe Intel536.ko   I tried using the SL source (From multiverse) and compiling it, but it said kernel version incompatability.

Has anyone using breezy successfully gotten the 536ep modem to work?  LMK, thanks!![/QUOTE]

To compile kernel modules under Breezy you need to install gcc-3.4. This is probably why you are getting a kernel version incompatability error. This is a nasty issue with Breezy that no-one seems to have figured out a solution to yet. The problem is that the Breezy kernel was compiled with gcc 3.4.5 but the installation CD does not have gcc 3.4 on it. Instead, Breezy installs gcc 4.0. That's fine except that you can only compile kernel modules with the same compiler that was used to compile the kernel.

These threads explain the issue...

[Compiling kernel modules (GCC3.4 / 4.0) problem](http://ubuntuforums.org/showthread.php?t=77851)
[breezy badger - cannot compile Lucent modem drivers](http://ubuntuforums.org/showthread.php?t=77537)

---

### Post by magomago on 2005-10-18
Ahh, but I did install GCC 3.4 and tried compiling and loading the modules.  I could compile the kernel but modprobing it does not work.  Sorry for not being as clear as before

---

### Post by magomago on 2005-10-20
[QUOTE=magomago]Ahh, but I did install GCC 3.4 and tried compiling and loading the modules.  I could compile the kernel but modprobing it does not work.  Sorry for not being as clear as before[/QUOTE]
bump again :'(
I really want to install Ubuntu on my brother's pc, but they still use a 56k modem at home.  Should I just go 5.04 Hoary?

---

