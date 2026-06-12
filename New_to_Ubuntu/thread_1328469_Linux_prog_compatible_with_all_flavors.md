---
title: "Linux prog compatible with all flavors?"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by Call My Function on 2009-11-16
I need to download a program designed to run on Fedora. If a program runs on a different type of linux, will it run on Ubuntu? Figured I'd just ask for future reference.

---

### Post by SPazzo on 2009-11-16
What program is it?

---

### Post by NoaHall on 2009-11-16
If you can get the source, then yes. You can compile it yourself. As for auto-installers(.deb on ubuntu), there is .rpm on Fedora. You can convert the .rpm if you must.

---

### Post by Locke_99GS on 2009-11-16
The biggest difference between rpm packages (for Fedora/Red Hat) and deb packages (for Debian/Ubuntu) is the internal structure and control of the package. *Most of the time, *an rpm can be converted to a deb without any issues.

---

### Post by Call My Function on 2009-11-16
The program is xSPIM -- I was able to get a Ubuntu-compatible version via the Software Center. But it's good to know that I can compile programs to make them work with Ubuntu.

What are the commands for compiling source code? I only know how to compile C++ progs, LoL.

---

### Post by coldReactive on 2009-11-16
> **Call My Function said:**
> The program is xSPIM -- I was able to get a Ubuntu-compatible version via the Software Center. But it's good to know that I can compile programs to make them work with Ubuntu.

What are the commands for compiling source code? I only know how to compile C++ progs, LoL.

When in terminal, in the source root dir:

./configure
make
make install

in that order

---

### Post by Call My Function on 2009-11-17
> **coldReactive said:**
> When in terminal, in the source root dir:

./configure
make
make install

in that order
Thank you coldReactive. Are those the same commands for Mac, by any chance? (I have a friend who needs to compile a prog on her iBook.)

---

### Post by koleoptero on 2009-11-17
Before compiling anything be sure to read any readme files you find with the source package. Many times you have to use some flags when running ./configure

---

### Post by teward on 2009-11-17
> **Call My Function said:**
> Thank you coldReactive. Are those the same commands for Mac, by any chance? (I have a friend who needs to compile a prog on her iBook.)

Mac and Linux may use similar prompts, but they don't operate on the same framework, so those commands MIGHT not work.

---

