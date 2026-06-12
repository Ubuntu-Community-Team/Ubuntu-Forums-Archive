---
title: "How do I determine architecture?"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by cricketeer on 2011-01-21
I'm trying to install some software but I don't know which binary to  download.  The authors have made it available for various platforms :
Alpah/Unix (OSF1, Digital Unix, Tru64 Unix, Linux)
PPC/Linux
PPC/MacOSX
RS6000/AIX
x86_64/linux
x86/Linux
x86/FreeBSD
x86/MacOSX
SPARC - UltraSPARC/Solaris
SGI/Irix

I want to run this software on a Dell Precision T7500 with Intel Xeon 64-bit processors running Ubuntu 10.10.

Can anyone help me determine which binary to download?  Do you need further information?  If so, what do you need to know?

---

### Post by matt_symes on 2011-01-21
Hi

Either of these are the ones you want..

x86_64/linux
x86/Linux

But i would go for x86_64/linux as you have a 64-bit processor.

Kind regards

---

### Post by andymorton on 2011-01-21
x86_64/linux.

---

### Post by alarme on 2011-01-21
on console, type
uname -a

at the end, you see the architecture

---

