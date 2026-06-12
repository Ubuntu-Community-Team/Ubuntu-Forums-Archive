---
title: "What is the best way to unistall windows 7?"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by robro on 2011-03-04
Hello community,
I have had ubuntu for over a month now, and am fully impressed of it and I want to unistall windows,
what would be the best way to do it? besides a complete reinstall of ubuntu.

Thanks for your help :)

---

### Post by TeoBigusGeekus on 2011-03-04
Boot up with a live cd, open terminal, give
gksu gparted
delete your windows partitions and expand your linux ones.

---

### Post by robro on 2011-03-04
Thanks for the fast reply, I am having problems figuring out which one the the windows partition is :|

---

### Post by TeoBigusGeekus on 2011-03-04
Well, it probably has ntfs as its system file for starters, whereas your linux partitions will be ext3/4.

PS: I hope we're not talking about a wubi installation.

---

### Post by colmesany on 2011-03-04
Run a new install and it will ask if you want a fresh install, in which case it will wipe the hard disk.

---

### Post by wilee-nilee on 2011-03-04
Take a screen shot of gparted and post it, or in the Ubutnu terminal run and post the out put of...
fdisk -l

---

### Post by robro on 2011-03-04
i have 3 ntfs partitions:
```

PQSERVICE
SYSTEM RESERVED
Acer

```I'm pretty sure its the Acer, but I want to double check

---

### Post by DavidMorton on 2011-03-04
You can always boot into Windows and check the volume name that shows up as the C: drive in Windows.  It's probably showing up as "Acer".

---

### Post by wilee-nilee on 2011-03-04
> **robro said:**
> i have 3 ntfs partitions:
```

PQSERVICE
SYSTEM RESERVED
Acer

```I'm pretty sure its the Acer, but I want to double check

I was wondering if you have a wubi install can you confirm this?

If it is a wubi Ubuntu is inside of Windows, but can be moved to a partition. Otherwise when you remove Windows Ubuntu goes as well. Here is a thread on migrating the wubi.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

I'm just giving you information, ask any questions if needed.

---

### Post by robro on 2011-03-04
no, ubuntu has a partition of it's own

---

### Post by robro on 2011-03-04
> **DavidMorton said:**
> You can always boot into Windows and check the volume name that shows up as the C: drive in Windows.  It's probably showing up as "Acer".
ahh, I already know its acer, thanks :)
problem solved.

---

