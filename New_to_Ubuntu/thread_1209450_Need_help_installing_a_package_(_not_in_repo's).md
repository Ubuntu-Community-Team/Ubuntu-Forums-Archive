---
title: "Need help installing a package ( not in repo's)"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by natman on 2009-07-10
Hi,
I am trying to install a package not in the repos. its called Coin3d software for graphics. 
[Coin3D]("http://www.coin3d.org/lib/coin/releases/3.1.0")
I took the .tar.gz and untar'd it as it told me. I then ran the configure command and all was fine ( i have gcc,g++,fortran and stuff ) the next step was to run "make" every time i tried this i just get the error no make file found. Could someone tell me whats wrong, or even have a go themselves at installing it? and post the commands back to me?

Thanks:

---

### Post by Majorix on 2009-07-10
Not all software is installed the same way. I am almost sure they included instructions on how to install the software in their .tar.gz. Please look for a README or INSTALL file.

---

### Post by natman on 2009-07-10
ya i followed extactly what was in the INSTALL file,
> cd /tmp
gzip -cd Coin-3.1.0.tar.gz | tar xvf -
mkdir coin-build
cd coin-build
../Coin-3.1.0/configure
all that works perfect, the next instrruction says " build the coin library"
> make
This is where i get my error and am stuck, i can find anything in there FAQ or help files either.
( may have mispell'd a command above but only cause i typed from hand )

---

### Post by sisco311 on 2009-07-10
make sure you have build-essential installed:
```
sudo aptitude install build-essential
```

---

