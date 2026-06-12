---
title: "Tarballs!!!"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by doppel.ganger on 2011-04-12
I just downloaded Thunderbird 3.1 and have no idea how to 'compile' a tar.bz2 file. I place all my tarballs in a folder called Tarballs in my home folder. I've already extracted it and need help from there. It's in thunderbird under Tarballs under Home.

---

### Post by wolfen69 on 2011-04-12
You don't need to do all that.
```
sudo apt-get install thunderbird
```
will install version 3.1

---

### Post by doppel.ganger on 2011-04-12
Oh. Idiot me.

---

### Post by qyot27 on 2011-04-12
Moreover, if this was the .tar.bz2 file distributed from the official Mozilla site, it doesn't look like it needs to be compiled anyway.

Something like
```
cd thunderbird
./thunderbird
```
Is all that would be necessary.


If it was source code that needed to be compiled, you'd see Makefiles, various run scripts, headers, and so forth.

---

### Post by rosencrantz on 2011-04-12
a) Why do you need to install Thunderbird via tarball? Installing a .deb from the repositories is so much easier to manage...
b) Tarballs can contain anything, it's just a compression format.
If it's C with a Makefile and a configure script (look for those files, no extension, in the untarred folder), you can run
./configure
make
sudo make install
configure checks you system for dependencies. If you're missing something, it's going to complain.
make invokes the gcc compiler according to the settings in the Makefile.
make install copies the compiles binaries to the right place.
I'd also recommend installing checkinstall and replacing
'sudo make install' with 'sudo checkinstall'
This builds a .deb package from your tarball, which is much easier to update or uninstall

---

### Post by imac_89 on 2011-04-12
rosencrantz:

> **wolfen69 said:**
> You don't need to do all that.
```
sudo apt-get install thunderbird
```
will install version 3.1

Someone has beaten you to it!

---

### Post by wolfen69 on 2011-04-13
> **imac_89 said:**
> Someone has already pointed that out.

Uh yeah, since I was that person. :o

---

### Post by rosencrantz on 2011-04-13
> **imac_89 said:**
> rosencrantz:



Someone has beaten you to it!
So? Mine is longer.

rosencrantz
(Hon. President of the More Useless Posts on the Ubuntuforms League)

---

