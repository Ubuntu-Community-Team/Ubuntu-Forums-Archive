---
title: "problems installing .deb package -- dependency problems/how to install needed files"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by GMachine_24 on 2009-10-25
I am attempting to install TheLastRipper software - it came as a .deb package but it needs files which are not installed on my version of Ubuntu 8.04 LTS .... so I'm wondering what to do. Here is the output:

```




user@user-desktop:/usr/share/thelastripper$ sudo dpkg -i thelastripper_1.4.1-1_all.deb
Selecting previously deselected package thelastripper.
(Reading database ... 140231 files and directories currently installed.)
Unpacking thelastripper (from thelastripper_1.4.1-1_all.deb) ...
dpkg: dependency problems prevent configuration of thelastripper:
 thelastripper depends on libglib2.0-cil (>= 2.12.7); however:
  Version of libglib2.0-cil on system is 2.12.0-2ubuntu3.
 thelastripper depends on libgtk2.0-cil (>= 2.12.7); however:
  Version of libgtk2.0-cil on system is 2.12.0-2ubuntu3.
 thelastripper depends on libmono-posix2.0-cil (>= 1.0); however:
  Package libmono-posix2.0-cil is not installed.
 thelastripper depends on libmono-system2.0-cil (>= 2.0); however:
  Version of libmono-system2.0-cil on system is 1.2.6+dfsg-6ubuntu3.1.
 thelastripper depends on libtaglib2.0-cil (>= 2.0.3.2); however:
  Package libtaglib2.0-cil is not installed.
dpkg: error processing thelastripper (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 thelastripper
user@user-desktop:/usr/share/thelastripper$


```

I checked whether the dependency packages are available via Synaptic and Synaptic either shows they are already installed or not available.

Thanks!!

---

### Post by coolbrook on 2009-10-25
[http://thelastripper.com/download.html](http://thelastripper.com/download.html)

It looks like you need Jaunty's dependencies.  Now might not be such a bad time to upgrade to that or possibly Karmic since the latter will be supported for almost as long as what's left of 8.04.

Post pics of Thela once you get this installed.  Cheers.

---

### Post by GMachine_24 on 2009-10-25
Coolbrook:

Thanks for your prompt reply. I had been installing updates to various files that were listed in my previous post but I could never get all of them installed. Then my computer crashed. Which is ok because I have a good back up.

I have v. 9.04 on a laptop and, after updating one package, TheLastRipper installed and runs fine. I don't think all the updates are compatible with HH 8.04 though.

Anyway, I will upgrade my desktop at some point in the not-too-distant future. I always avoid it as long as possible because of previous disasters . . . . 

Thanks again.

GM

---

