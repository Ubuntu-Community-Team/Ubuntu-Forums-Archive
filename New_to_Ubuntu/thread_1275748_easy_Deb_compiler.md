---
title: "easy Deb compiler"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by coldReactive on 2009-09-26
Does anyone know of a deb compiler that takes in a source tar (IE: tar.bz2) and asks you questions about it, then outputs a deb for you easily? Someone told me there is such a thing, but can't remember where he got it from.

---

### Post by khughitt on 2009-09-26
Try [Giftwrap]("http://www.stefanoforenza.com/giftwrap-helps-you-create-debs/").

---

### Post by 3rdalbum on 2009-09-26
I don't believe it compiles the software for you.

If you can compile software, then it's only a small extra step to create a Debian package. Just set the target for the compile to another directory (using the ./configure script's "prefix" option), compile as usual, create a folder and a CONTROL file, and run one command in the terminal.

---

### Post by coldReactive on 2009-09-26
> **pwnedd said:**
> Try [Giftwrap]("http://www.stefanoforenza.com/giftwrap-helps-you-create-debs/").

I need 32-bit libraries to make what I want (WINE) on amd64 (arch I use.)

How do I get them?

---

### Post by 3rdalbum on 2009-09-26
```
sudo apt-get install ia32-libs
```

---

### Post by coldReactive on 2009-09-26
> **3rdalbum said:**
> ```
sudo apt-get install ia32-libs
```

Sorry, I meant 32-bit development libraries. (libc6-dev-i386)

Edit: After so many extra packages to install manually (IE: xfree86 development stuff, freetype 32-bit stuff, etc.) (because giftwrap doesn't install them for you, which I think it should) it's finally building, I think (Well it isn't telling me anything, the progress bar is just going from left to right and back to left, bouncing back and forth.)

---

### Post by coldReactive on 2009-09-26
So it finally built the deb, but after I installed the wine deb, my wine folder in the applications menu has been stripped, and only shows the wine applications (IE: Angels Online) that I have installed.

Great....

---

