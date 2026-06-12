---
title: "Error: No such file..."
date: 2009-03-01
forum: New to Ubuntu
---

### Post by laura167 on 2009-03-01
Hi there!

I just got ubuntu up and running (I must confess I'm an absolute beginner...) and now need to install VclVI, which requires Tcl/Tk. After "make" complained about not finding tcl.h, I added -I/usr/include/tcl8.4 in the makefile. So now, it can find tcl.h, but it complains about not finding tk.h:
```
main.c:1:16: Fehler: tk.h: No such file or directory
```
which is in the same directory :confused:

can someone, please, give me a hint?

best wishes, Laura

---

### Post by Perryg on 2009-03-01
> **laura167 said:**
> Hi there!

I just got ubuntu up and running (I must confess I'm an absolute beginner...) and now need to install VclVI, which requires Tcl/Tk. After "make" complained about not finding tcl.h, I added -I/usr/include/tcl8.4 in the makefile. So now, it can find tcl.h, but it complains about not finding tk.h:
```
main.c:1:16: Fehler: tk.h: No such file or directory
```
which is in the same directory :confused:

can someone, please, give me a hint?

best wishes, Laura

Don't know if this will help but from what I have found:
Most of the time when something can not find a file or directory is due to the case of the wording.  Caps matter.

---

### Post by taurus on 2009-03-01
Try installing both tcl8.4-dev and tk8.4-dev from the repos first before you try build that program again.

---

### Post by laura167 on 2009-03-01
First of all, thank you for your quick responses!

Perryg: I fear that's not the case, because the path worked for tcl.h. - but thanks anyway.

Thanks taurus, I've checked that, but they're already installed, both of them.

---

### Post by asmoore82 on 2009-03-01
This applies to all Debian based distributions such as Ubuntu ...
to save space on systems that don't need it; packages **do not** contain
the extra development files needed to compile sofware from source that depends on existing packages -
any packages that have such extra development files available
will have a "*-dev" package that must be installed separately...

```
**$** apt-cache search tk8.4
bottlerocket - Utility to control X10 Firecracker devices for home automation
erlang-nox - Concurrent, real-time, distributed functional language (no X11 deps)
erlang-x11 - Concurrent, real-time, distributed functional language (X11 deps)
libpurple0 - multi-protocol instant messaging library
**tk8.4** - Tk toolkit for Tcl and X11, v8.4 - run-time files
**tk8.4-dev** - Tk toolkit for Tcl and X11, v8.4 - development files
**tk8.4-doc** - Tk toolkit for Tcl and X11, v8.4 - manual pages

```[emphasis added]

you only need that "tk8.4" packages to use tk -
but to compile software that uses tk, you need the tk8.4-dev package as well

---

### Post by asmoore82 on 2009-03-01
also, make sure you have the **"build-essential"** package of software dev tools
as well as both the C and C++ variants of the GNU Compiler Collection.
I'm not sure that g++ is a must have for your situation - but it couldn't hurt
```
sudo apt-get install build-essential gcc g++
```

---

### Post by laura167 on 2009-03-01
Thanks for your answer, asmoore82, yah I understand that they're separate and I've installed the -dev packages, for it says in the TclVI readme that they're required (correct me if I'm wrong but if I hadn't, I wouldn't see the .h files, would I?)

edit: about the build-essential package, thanks, I'll check that..

---

### Post by laura167 on 2009-03-01
> **asmoore82 said:**
> also, make sure you have the **"build-essential"** package of software dev tools
as well as both the C and C++ variants of the GNU Compiler Collection.
I'm not sure that g++ is a must have for your situation - but it couldn't hurt
```
sudo apt-get install build-essential gcc g++
```

Alright, I did that, didn't work though, same old problem. Thanks anyway

---

