---
title: "g77 Ubuntu 8.10"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by ncoupe on 2009-01-08
I just installed Ubuntu 8.10 and I do need to run some code on g77 (GNU fortran 77). However, it is not included on the already installed gcc. How can I install g77? Everything I found was for previous versions of Ubuntu.

---

### Post by Tim Sharitt on 2009-01-08
In a terminal
```
sudo apt-get install g77
```

---

### Post by ncoupe on 2009-01-09
I already try that, but I get:

sudo apt-get install g77
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package g77 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package g77 has no installation candidate

any ideas?

---

### Post by LowSky on 2009-01-09
apt-cache search g77

---

### Post by mali2297 on 2009-01-09
I did a search here:
[http://packages.ubuntu.com/search?keywords=g77](http://packages.ubuntu.com/search?keywords=g77)

It does not seem to be available for Ubuntu 8.10. Can't you use the Fortran 95 compiler (gfortran)?

---

### Post by ncoupe on 2009-01-09
apt-cache search g77
f2c - A FORTRAN 77 to C/C++ translator
ratfor - Rational Fortran preprocessor for Fortran 77


Unfortunately I can not use gfortran or Fortran 95. I am afraid to use any translator as I am running  a huge pice of code that someone else wrote.

thanks

---

### Post by mali2297 on 2009-01-09
Have you tried installing g77 for Ubuntu 8.04? You can fetch a .deb file at [http://packages.ubuntu.com/hardy-updates/g77-3.4](http://packages.ubuntu.com/hardy-updates/g77-3.4).

EDIT:
See this thread: [http://ubuntuforums.org/showthread.php?t=969198](http://ubuntuforums.org/showthread.php?t=969198).

---

### Post by ncoupe on 2009-01-09
I try:
Download Page for g77-3.4_3.4.6-6ubuntu5_i386.deb on Intel x86 machines
My Synaptic Pack pops up and gives the message:

Error: Wrong architecture 'i386'

My computer has an Intel processor

I also try installing  gcc-3.4 thinking that g77 could be included by default. However, I did not have any luck

---

### Post by mali2297 on 2009-01-09
> **ncoupe said:**
> I try:
Download Page for g77-3.4_3.4.6-6ubuntu5_i386.deb on Intel x86 machines
My Synaptic Pack pops up and gives the message:

Error: Wrong architecture 'i386'

My computer has an Intel processor

I also try installing  gcc-3.4 thinking that g77 could be included by default. However, I did not have any luck

Read the thread that I linked.

Also, in a terminal, type
```

uname -m

```
If it says x86_64, then you have a 64-bit OS and should use compatible binaries (which are labeled amd64 even if you have an Intel processor).

---

### Post by ncoupe on 2009-01-09
million thanks,
it did work!

---

### Post by mali2297 on 2009-01-09
> **ncoupe said:**
> million thanks,
it did work!

How did you solve it exactly? It might be useful to know for others with the same problem. Also, mark the thread as solved (via the Thread Tools menu).

---

### Post by gansvv on 2010-05-04
Edit your /etc/apt/sources.list to add:
> deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) hardy-updates main universe

Then use:
> sudo apt-get update
sudo apt-get install g77


---

