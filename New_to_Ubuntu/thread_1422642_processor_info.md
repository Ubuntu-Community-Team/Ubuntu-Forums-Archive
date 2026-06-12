---
title: "processor info"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by stevepoppers on 2010-03-05
For a machine with an i686 processor, the i386 version of ubuntu should be used, correct? Also, how do I check which version is installed? Would it have been possible to install the 64 bit version on this machine?

---

### Post by patchwork on 2010-03-05
Yes, you should use the 32 bit, and I don't think you can install the 64 bit on it.

To see what you have, type in the terminal:

```
uname -a
```as you can see, my system is x86_64, or the 64 bit version.  Your's should be x86


kevin@crystalpepsi:~$ uname -a
Linux crystalpepsi 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 **x86_64** GNU/Linux

---

### Post by gordintoronto on 2010-03-05
Sysinfo will tell you exactly what processor you have.

---

### Post by Shark_AtK12 on 2010-03-05
> **stevepoppers said:**
> For a machine with an i686 processor, the i386 version of ubuntu should be used, correct? Also, how do I check which version is installed? Would it have been possible to install the 64 bit version on this machine?

It depends on your processor. If its an AMD 64 then either 32 or 64 bit can be installed.

---

### Post by stevepoppers on 2010-03-08
Thanks guys. Couldn't remember what I had installed on a friend's computer and though I might have somehow put the x64 on an i686, and also just didn't know what i686 meant.

---

### Post by JerichoKru on 2010-03-08
> **stevepoppers said:**
> Thanks guys. Couldn't remember what I had installed on a friend's computer and though I might have somehow put the x64 on an i686, and also just didn't know what i686 meant.

i386, i586, and i686 are just 32bit subtypes, IIRC.

---

