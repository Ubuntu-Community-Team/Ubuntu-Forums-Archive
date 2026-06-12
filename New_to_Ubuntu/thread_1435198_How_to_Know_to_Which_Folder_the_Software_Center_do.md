---
title: "How to Know to Which Folder the Software Center downloads"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by fizmhd on 2010-03-21
Hellow ,

i just want to know to which folder does the UBUNTU SOFTWARE CENTER downloads pakages. 

i have to sytems .. i want to install them on the other .. if i know to which folder the pakages are downloaded .. else i have to download in both computer 

please help me ...

---

### Post by Elfy on 2010-03-21
Hi - var/cache/apt/archives

---

### Post by fizmhd on 2010-03-21
thnkx very much for the help. ..

---

### Post by gmargo on 2010-03-21
I run **approx**, the "caching proxy server for Debian archive files", on one machine and have all machines go through it.  So in general each .deb file only gets downloaded once. [http://packages.ubuntu.com/karmic/approx](http://packages.ubuntu.com/karmic/approx)

---

