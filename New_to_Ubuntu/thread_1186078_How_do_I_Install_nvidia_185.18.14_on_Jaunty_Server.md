---
title: "How do I Install nvidia 185.18.14 on Jaunty Server 32Bit?"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by ninja_numbnuts on 2009-06-13
I have already installed make, binutils and gcc, but now it says;

Unable to find the kernel source tree for the currently running kernel. Please make sure you have installed the kernel source files for your kernel and that they are properly configured; on Red Hat Linux systems, for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM installed. If you know the correct kernel source files are installed, you may specify the kernel source path with the '--kernel-source-path' command line option.

What else do I need too install?

---

### Post by ninja_numbnuts on 2009-06-13
Tiny bump :D

---

### Post by Elfy on 2009-06-13
thread moved to Absolute Beginners - please do not bump so soon.

---

### Post by ninja_numbnuts on 2009-06-13
Nevermind I solved it.

If anyone is ever in the same situation, you need to install these files;

make
binutils
gcc

and run this command 

sudo aptitude install linux-headers-server

It works!

---

