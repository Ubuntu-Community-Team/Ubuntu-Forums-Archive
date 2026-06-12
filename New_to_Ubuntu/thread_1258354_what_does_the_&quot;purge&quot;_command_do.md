---
title: "what does the &quot;purge&quot; command do?"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by thomz92 on 2009-09-04
so i've heard...the purge command is used when uninstalling packages from the command line. but what does it mean?

---

### Post by bear24rw on 2009-09-04
Example:

$ sudo aptitude purge apache2

would completely remove the apache 2 package

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by thomz92 on 2009-09-04
so its the same thing as going into synaptic and right clicking on a package and selecting "completely remove", right?

---

### Post by bear24rw on 2009-09-04
yep

---

### Post by thomz92 on 2009-09-04
soo...its also the same thing as "sudo apt-get autoremove xyz"?

---

### Post by bear24rw on 2009-09-04
yeah i believe so

---

### Post by Windows Nerd on 2009-09-04
> **thomz92 said:**
> soo...its also the same thing as "sudo apt-get autoremove xyz"?
Yep. Sudo apt-get uninstall* xyz-program* works as well. 

Scott

---

### Post by thomz92 on 2009-09-04
ok thank y'alls

---

### Post by CatKiller on 2009-09-05
> **thomz92 said:**
> soo...its also the same thing as "sudo apt-get autoremove xyz"?

No. From **man apt-get**:

>        purge
           purge is identical to remove except that packages are removed and
           purged (any configuration files are deleted too).

       autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.

You don't specify a package name with *autoremove*.

---

### Post by bear24rw on 2009-09-05
> **CatKiller said:**
> No. From **man apt-get**:



You don't specify a package name with *autoremove*.

Touche

---

### Post by karthick87 on 2009-09-05
What is the difference between apt-get and aptitude?

---

### Post by CatKiller on 2009-09-05
> **getyourkarthick said:**
> What is the difference between apt-get and aptitude?

In a Terminal window, just run **apt-get** (without any options). Then run **aptitude** (again, without any options). That's the main difference.

---

### Post by wojox on 2009-09-05
And super cow powers. :D

---

