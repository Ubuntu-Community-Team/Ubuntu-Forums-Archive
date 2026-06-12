---
title: "Version install"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by dyrer on 2009-04-27
I have downloaded and burned Ubuntu 9.04 i386
after installation
my system is i686, is this correct?
and Filezilla refuse to install due to system version

---

### Post by kpkeerthi on 2009-04-27
Yes. For an i686 PC, you should use i386 ISO.

How are you installing filezilla?

---

### Post by dyrer on 2009-04-27
I have installed desktop i386
why is i686
for filezilla i use add/remove

---

### Post by 3rdalbum on 2009-04-27
> **dyrer said:**
> I have installed desktop i386
why is i686

i686 is just a description of what instructions your processor supports. If it supports i686 then by definition it also supports i386. It's completely normal, nothing to worry about.

> for filezilla i use add/remove

Can you please give us the exact error message? And are you aware that you can log into FTP sites through Places > Connect To Server?

---

### Post by dyrer on 2009-04-27
[[IMG]http://img144.imagevenue.com/loc440/th_40712_filezilla_122_440lo.jpg[/IMG]](http://img144.imagevenue.com/img.php?image=40712_filezilla_122_440lo.jpg)

---

### Post by scheuri on 2009-04-27
Hi there

Can you please tell us what "uname -a" says in the terminal/console?

Thanks

---

### Post by dyrer on 2009-04-27
Linux dyrer-linux 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

---

### Post by 3rdalbum on 2009-04-27
Is this software from the normal repositories or from a PPA? If it's from a PPA, then the person who compiles the software for the PPA might have only made it for 64-bit.

If it's from the regular repositories, have you tried refreshing the package list?

Also, the site [www.getdeb.net](www.getdeb.net) has a copy of Filezilla that should be compiled for 32-bit for you.

---

### Post by dyrer on 2009-04-28
I dont know how but worked the 32bit version from getdeb

---

