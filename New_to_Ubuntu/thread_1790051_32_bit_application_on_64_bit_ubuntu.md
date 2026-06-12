---
title: "32 bit application on 64 bit ubuntu"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by mwesolow on 2011-06-24
Hello all,
 
I am running x86_64 Ubuntu, and I have ia32-libs installed. The software I want to run is of type 'ELF 32-bit'. It also depends on libgmp, but the shell complains that libgmp.so.3 is 'wrong ELF class: ELFCLASS64'. It is clear to me that I need 32 bit gnu mp installed, but how do I do that? Synaptic shows that I already have libgmp3c2 installed. 
 
Thanks,
-mwesolow

---

### Post by Bachstelze on 2011-06-24
You can install the 32 bit version with the package *lib32gmp3*. If you have the same problem for another library that does not exist as a lib32 package, you can also download the i386 package for the lib in questions (e.g. from [http://packages.ubuntu.com](http://packages.ubuntu.com)), extract it with *dpkg -x* and manually copy the .so* files into /usr/lib32.

---

