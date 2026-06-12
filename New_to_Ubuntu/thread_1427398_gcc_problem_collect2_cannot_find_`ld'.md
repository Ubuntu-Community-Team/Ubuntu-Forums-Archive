---
title: "gcc problem collect2: cannot find `ld'"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by lolzwut on 2010-03-11
Everytime I try to compile anything it gives me this error. I checked to see if I had ld installed and I do


```
which ld
``````
ld: /usr/bin/ld /usr/share/man/man1/ld.1.gz
  
```So what's wrong and now can I fix this?

---

### Post by lolzwut on 2010-03-12
bump......

---

### Post by gmargo on 2010-03-12
Could be a version mismatch problem?  What version(s) of gcc and binutils do you have installed?  Are you messing with cross compilers or something?

---

### Post by frozz_night on 2010-11-24
I made a stupid mistake unintendedly deleting ld in /usr/bin/ .
How can I restore the ld file? Do I have to reinstall gcc and other packages too?

---

### Post by frozz_night on 2010-11-24
I fixed the problem now.
I reinstall binutils using synaptic package manager.
Thanks

---

### Post by hamidvosugh on 2011-01-28
Thanks frozz_night. I did the same mistake, and was pondering for hours.

---

