---
title: "How do you install tar.bz2"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by Extract_Here on 2009-12-19
can someone explain to me how to install that file type i know how to install tar.gz but not bz2

---

### Post by s.fox on 2009-12-19
Hello.

[This]("http://ubuntuforums.org/showthread.php?t=292982") may be of some use to you.

-Silver Fox

---

### Post by szymon_g on 2009-12-19
whatever you do, check for it in repos first :)

---

### Post by spiderbatdad on 2009-12-19
Slight misconception here is that the package is the program. Source packages contain programs, and hopefully "Readme" or "Install" files; that's the place to start. Many use autoconf, or are binaries to run from within their own directories. others are compiled with ./configure, make, and sudo makeinstall. Looking through 3 different links...they all either neglected to mention makeinstall as root, or else they compiled as root, a general no no. So read the instructions.

---

