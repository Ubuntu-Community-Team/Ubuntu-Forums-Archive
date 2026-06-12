---
title: "error while loading shared libraries: libfftw3.so.3: wrong ELF class: ELFCLASS64"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by pirveli on 2009-07-30
Hi!
I installed fftw3. I managed to compile my friend's program that is using it, but I'm unable to run it --- I'm getting the following error:
```
error while loading shared libraries: libfftw3.so.3: wrong ELF class: ELFCLASS64
```
My Ubuntu is x86_64 and that is probably causing the problem. How to make the program work?

!P

---

### Post by cozmicharlie on 2009-07-30
> **pirveli said:**
> 
My Ubuntu is x86_64 and that is probably causing the problem. How to make the program work?


You are correct.  Go here and install a package for 64 bit systems.  Search for fftw3 using the amd 64 filter.
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Hope this helps

---

### Post by pirveli on 2009-07-31
Thanks :) It helped :)

!P

---

