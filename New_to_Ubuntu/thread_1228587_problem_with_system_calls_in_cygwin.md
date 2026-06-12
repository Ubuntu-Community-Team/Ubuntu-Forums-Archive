---
title: "problem with system calls in cygwin"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by amy n. on 2009-08-01
I have a C program in Solaris that contains system calls, something like this:
 
system ("ls -l > file");
 
I installed cygwin and this C program compiled OK on a Windows XP machine. When I go to run it at the cygwin shell, the C program hangs at this system call. To continue, I have to press a carriage return. If not, the C program just hangs.
 
How can I solve this problem in Windows when I use cygwin?

---

### Post by Liolikas on 2009-08-01
Add cygwin's bin directory to window's PATH.

---

