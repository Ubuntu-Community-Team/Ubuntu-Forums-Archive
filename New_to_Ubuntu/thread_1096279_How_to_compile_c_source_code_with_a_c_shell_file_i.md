---
title: "How to compile c source code with a c shell file in LINUX??"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by jmmalo03 on 2009-03-14
Hi everyone,
I have some C source code that exists in several files.  The creator of the source code says to run a specific file (we'll call it 'mainfile') that will compile all the C code.  I looked at the file type and it is an 'x-csh' file type.  I've spent hours but for some reason I absolutely cannot get this thing to execute...can anyone help??  I am very new to LINUX.

---

### Post by taurus on 2009-03-14
If it's a C code, then you need to install the build-essential package first since you need gcc compiler to compile it.

```
sudo apt-get update
sudo apt-get install build-essential
gcc *mainfile*
```
Assuming you are in the directory where *mainfile* is.

---

### Post by snova on 2009-03-15
> **jmmalo03 said:**
> Hi everyone,
I have some C source code that exists in several files.  The creator of the source code says to run a specific file (we'll call it 'mainfile') that will compile all the C code.  I looked at the file type and it is an 'x-csh' file type.  I've spent hours but for some reason I absolutely cannot get this thing to execute...can anyone help??  I am very new to LINUX.

Judging by that mimetype (x-csh), it's a script, but its a script written for Csh, an alternative shell (comparable to Bash in purpose) which is not installed by default.

You will need **build-essential** as taurus suggested, but to run this script you will also need to install the **csh** package.

After that, it should hopefully be as simple as:

```
csh *mainfile*
```

---

### Post by jmmalo03 on 2009-03-15
Thanks for your help guys.  I think your suggestions are correct and I used them, however, I found a new error in the C source code itself :(   The error is described in some notes by the distributor.

To make this a little more interesting, I'll explain my story.  I'm an electrical engineer doing research on digital mammographic images. This software I'm trying to use is a special software to decompress LJPEG files (some obscure filetype) from the University of South Florida Mammography database.  So far it has been a pain

---

