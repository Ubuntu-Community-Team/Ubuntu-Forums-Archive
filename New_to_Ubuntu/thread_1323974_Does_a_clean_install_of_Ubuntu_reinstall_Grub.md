---
title: "Does a clean install of Ubuntu reinstall Grub?"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-11-12
Hi

Quick query - if I format the extended partition that my Ubuntu install is on (using gparted live cd) and reinstall Ubuntu, will that reinstall / overwrite any existing Grub settings?

To explain - I helped a friend in her time of need (WinXP corrupted registry) - I installed ubuntu so as to be able to access her windows files and fix the offending file.  Mission was a total success - but when I installed Ubuntu originally i put in on  a small partition that meant there was no room to install updates etc that would show what Ubuntu could do.

That lead me to go in with gparted live, delete an unecessary backup partition, and extend the original ubuntu partition into the free space created.  However this mucked up Grub, and all I get now on startup is a Grub Error 17.

---

### Post by Kevbert on 2009-11-12
Ubuntu will re-install Grub and look for any installed operating systems and include start-up entries for them.

---

### Post by suitedaces on 2009-11-12
if you only want to fix grub, then a full reinstall is unnecessary.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by laidback on 2009-11-12
There is a Grub web site:-

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

---

