---
title: "How do I fix? Kpackage kit wont add repositories"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by TechDragon on 2009-05-11
Every time I try to add a third party source, and I am only trying to unable the two that come with ubuntu\kubuntu. Kpackage kit crashes with a fatal error.

"The appliciaton software sources crashed and caused the signal 11"

Help plz

---

### Post by bswilson on 2009-05-13
Perhaps there are some illegal/inappropriate characters in your sources file?  How about post a copy here and we'll see if we can help you.

---

### Post by Mr_Bumpy on 2009-07-24
I have the same problem.  It appears this has been fixed (for some future version, I'm guessing), based on [this KDE bug report]("https://bugs.kde.org/show_bug.cgi?id=192325").

---

### Post by markharding557 on 2009-07-24
in the mean time add it to the sources list manually
sudo kate /etc/apt/sources.list

---

