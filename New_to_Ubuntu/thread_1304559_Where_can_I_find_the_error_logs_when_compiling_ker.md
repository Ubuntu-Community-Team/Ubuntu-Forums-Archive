---
title: "Where can I find the error logs when compiling kernel?"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by htm316 on 2009-10-29
Hello I am really new on Linux. I am trying to compile the Kernel but do not know where error logs are stored. 
 
I am using these commands from ubuntu docs...
 
[FONT=Courier New]***fakeroot debian/rules clean***[/FONT]
***[FONT=Courier New]AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules custom-binary-FLAVOUR[/FONT]***
 
Does anybody know where the error logs are stored if there are compile errors?
 
Thanks a lot!!!:D:D:D

---

### Post by phillw on 2009-10-29
> **htm316 said:**
> Hello I am really new on Linux. I am trying to compile the Kernel but do not know where error logs are stored. 
 
I am using these commands from ubuntu docs...
 
[FONT=Courier New]***fakeroot debian/rules clean***[/FONT]
***[FONT=Courier New]AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules custom-binary-FLAVOUR[/FONT]***
 
Does anybody know where the error logs are stored if there are compile errors?
 
Thanks a lot!!!:D:D:D


Can I ask why you're compiling the kernel... It's certainly not for the faint hearted !!!!

Phill.

---

### Post by htm316 on 2009-10-29
Oh I am developing a driver for Linux. I am a windows guy and this is the first time I am working on Linux. 
I am compiling the kernel with printk statements that I added so I can trace the code.
 
Thanks for responding.

---

