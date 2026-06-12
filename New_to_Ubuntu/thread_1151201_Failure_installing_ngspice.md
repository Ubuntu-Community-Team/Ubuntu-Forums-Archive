---
title: "Failure installing ngspice"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by kotg on 2009-05-06
Total newbie. Dell Mini 9 with Ubuntu 8.1..

I installed Oregano with no problems. Now I need ngspice which will not install.

Tried this:

**********

terry@terry:~$ sudo /home/terry/Desktop/ngspice/ngspice-19/configure;make;make install
[sudo] password for terry: 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

********

Can anyone suggest what to do at this point? Haven't got a clue.

Thanks...

---

### Post by kotg on 2009-05-08
BUMP - sorry.

Could someone please help me with this?

TIA

---

### Post by taurus on 2009-05-08
Do you have a gcc compiler on your machine?  You need to install the build-essential package first before you can compile anything from source.

```
sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop/ngspice/ngspice-19
./configure
```

p.s.  No need to include _sudo_ for both ./configure && make.

---

### Post by kotg on 2009-05-08
edit

---

### Post by sdaau on 2011-05-03
Sorry to bump an old thread - maybe this wiki entry will help: 

[From_PSpice_to_ngspice-gEDA - Ubuntu Wiki](https://wiki.ubuntu.com/From_PSpice_to_ngspice-gEDA)

---

