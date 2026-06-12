---
title: "Problem in Package manager (9.10)"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by anup.techonly on 2010-02-25
I am a Ubuntu 9.10 user. I was trying to install SAGE. Something went wrong I think. Now if I try to install or remove something it gives the following error.

The error message looks like this : libdsdp-5.8gf: dependency problems - leaving unconfigured.

Any help is appreciated...

Anup.

---

### Post by gallifrey on 2010-02-25
If you try installing it through Synaptic, it should install all dependencies automatically. Otherwise, check out this link:

[http://packages.ubuntu.com/karmic/sagemath](http://packages.ubuntu.com/karmic/sagemath)

It lists all dependencies required.

---

### Post by anup.techonly on 2010-02-25
Thanx. Actaully I checked them before installing SAGE, everything was OK except ranlib. I went with installation and now I can't install a thing. I don't know how to get my system back working even if at the expense of deleting SAGE.

regards,

Anup

---

### Post by sdlm on 2010-02-25
I would load aptitude and see if the packages are broken. If so it can usually be fixed

---

### Post by anup.techonly on 2010-02-25
Cython and libdsdp-5.8gf is giving error from synaptic.

---

### Post by sdlm on 2010-02-25
> **anup.techonly said:**
> Cython and libdsdp-5.8gf is giving error from synaptic.

If Edit-fix broken packages in the synaptic menu doesn't work then try to use dpkg --remove [package with the error] you could also use dpkg --purge but, that will also remove the config files for what you are removing

if that is successful I recommend attempting to reinstall through synaptic and pay close attention to what it says are the dependencies, it should download then automatically (assuming it in a proper .deb file)

---

### Post by anup.techonly on 2010-02-25
when I tried to remove it the following errors occur..


anup@anup-laptop:~/Libraries/SAGE/sage-4.3.3$ sudo dpkg --remove libdsdp-5.8gf 
[sudo] password for anup: 
dpkg: status database area is locked by another process
anup@anup-laptop:~/Libraries/SAGE/sage-4.3.3$ sudo dpkg --remove libdsdp-5.8gf 
(Reading database ... 298611 files and directories currently installed.)
Removing libdsdp-5.8gf ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libdsdp-5.8gf (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 libdsdp-5.8gf

---

### Post by gallifrey on 2010-02-25
If the installation of libsdspd58 is broken, you could try reinstallling that single package. I can only find it as source though:
[http://packages.ubuntu.com/karmic/libdsdp-5.8gf](http://packages.ubuntu.com/karmic/libdsdp-5.8gf)

---

### Post by DirtyBeets on 2010-02-25
libdsdp-5.8gf is available in the default repositories.



```
sudo apt-get autoremove libdsdp-5.8gf

Then
sudo apt-get install libdsdp-5.8gf
```

Aptitude will automatically resolve any dependencies you may run into. IIRC dpkg will not.

---

### Post by anup.techonly on 2010-02-25
i downloaded the package from source and double clicked on it.

Error : Error: Failed to satisfy all dependencies (broken cache)

---

### Post by DirtyBeets on 2010-02-25
Have you tried removing it with apt-get or synaptic manager?

---

### Post by anup.techonly on 2010-02-26
Through synaptic manager it shows..

E: libgmpxx4ldbl: subprocess installed post-installation script returned error exit status 2
E: libgmp3-dev: dependency problems - leaving unconfigured
E: libcdd0: dependency problems - leaving unconfigured
E: gfan: dependency problems - leaving unconfigured
E: lcalc: dependency problems - leaving unconfigured
E: libcdd-test: dependency problems - leaving unconfigured
E: liblinbox0: dependency problems - leaving unconfigured
E: python-excelerator: subprocess installed post-installation script returned error exit status 2
E: python-foolscap: subprocess installed post-installation script returned error exit status 2
E: python-numpy: subprocess installed post-installation script returned error exit status 2
E: python-gnuplot: dependency problems - leaving unconfigured
E: python-gnutls: subprocess installed post-installation script returned error exit status 2
E: python-pyparsing: subprocess installed post-installation script returned error exit status 2


sudo aptitude -f install failed.. 

anup@anup-laptop:/var/lib/dpkg/info$ sudo aptitude -f install
[sudo] password for anup: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following partially installed packages will be configured:
  gfan lcalc libcdd-test libcdd0 libgmp3-dev libgmpxx4ldbl liblinbox0 
  python-excelerator python-foolscap python-gnuplot python-gnutls 
  python-numpy python-pyparsing 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up libgmpxx4ldbl (2:4.3.1+dfsg-1ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libgmpxx4ldbl (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libgmp3-dev:
 libgmp3-dev depends on libgmpxx4ldbl (= 2:4.3.1+dfsg-1ubuntu3); however:
  Package libgmpxx4ldbl is not configured yet.
dpkg: error processing libgmp3-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcdd0:
 libcdd0 depends on libgmp3-dev; however:
  Package libgmp3-dev is not configured yet.
dpkg: error processing libcdd0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gfan:
 gfan depends on libcdd0; however:
  Package libcdd0 is not configured yet.
dpkg: error processing gfan (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of No apport report written because the error message indicates its a followup error from a previous failure.
                                                                             No apport report written because the error message indicates its a followup error from a previous failure.
                       No apport report written because MaxReports is reached already
     No apport report written because MaxReports is reached already
                                                                   No apport report written because MaxReports is reached already
                                                 No apport report written because MaxReports is reached already
                               lcalc:
 lcalc depends on libgmpxx4ldbl; however:
  Package libgmpxx4ldbl is not configured yet.
dpkg: error processing lcalc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcdd-test:
 libcdd-test depends on libcdd0; however:
  Package libcdd0 is not configured yet.
dpkg: error processing libcdd-test (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblinbox0:
 liblinbox0 depends on libgmpxx4ldbl; however:
  Package libgmpxx4ldbl is not configured yet.
dpkg: error processing liblinbox0 (--configure):
 dependency problems - leaving unconfigured
Setting up python-excelerator (0.6.3a-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-excelerator (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-foolscap (0.4.2+dfsg-1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-foolscap (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-numpy (1:1.3.0-3) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-numpy (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python-gnuplot:
 python-gnuplot depends on python-numpy; however:
  Package python-numpy is not configured yet.
dpkg: error processing python-gnuplot (--configure):
 dependency problems - leaving unconfigured
Setting up python-gnutls (1.1.8-1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-gnutls (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-pyparsing (1.5.2-1ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-pyparsing (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libgmpxx4ldbl
 libgmp3-dev
 libcdd0
 gfan
 lcalc
 libcdd-test
 liblinbox0
 python-excelerator
 python-foolscap
 python-numpy
 python-gnuplot
 python-gnutls
 python-pyparsing
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libgmpxx4ldbl (2:4.3.1+dfsg-1ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libgmpxx4ldbl (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-foolscap (0.4.2+dfsg-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-foolscap (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-pyparsing (1.5.2-1ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-pyparsing (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of liblinbox0:
 liblinbox0 depends on libgmpxx4ldbl; however:
  Package libgmpxx4ldbl is not configured yet.
dpkg: error processing liblinbox0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgmp3-dev:
 libgmp3-dev depends on libgmpxx4ldbl (= 2:4.3.1+dfsg-1ubuntu3); however:
  Package libgmpxx4ldbl is not configured yet.
dpkg: error processing libgmp3-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcdd0:
 libcdd0 depends on libgmp3-dev; however:
  Package libgmp3-dev is not configured yet.
dpkg: error processing libcdd0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcdd-test:
 libcdd-test depends on libcdd0; however:
  Package libcdd0 is not configured yet.
dpkg: error processing libcdd-test (--configure):
 dependency problems - leaving unconfigured
Setting up python-gnutls (1.1.8-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-gnutls (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-numpy (1:1.3.0-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-numpy (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-excelerator (0.6.3a-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-excelerator (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of lcalc:
 lcalc depends on libgmpxx4ldbl; however:
  Package libgmpxx4ldbl is not configured yet.
dpkg: error processing lcalc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gfan:
 gfan depends on libcdd0; however:
  Package libcdd0 is not configured yet.
dpkg: error processing gfan (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnuplot:
 python-gnuplot depends on python-numpy; however:
  Package python-numpy is not configured yet.
dpkg: error processing python-gnuplot (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgmpxx4ldbl
 python-foolscap
 python-pyparsing
 liblinbox0
 libgmp3-dev
 libcdd0
 libcdd-test
 python-gnutls
 python-numpy
 python-excelerator
 lcalc
 gfan
 python-gnuplot
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

---

### Post by DirtyBeets on 2010-02-26
You could try the suggestions listed here:
[http://www.linux.com/archive/feature/48910](http://www.linux.com/archive/feature/48910)

Starting at 4. It looks like you've tried everything they suggest before that.

---

