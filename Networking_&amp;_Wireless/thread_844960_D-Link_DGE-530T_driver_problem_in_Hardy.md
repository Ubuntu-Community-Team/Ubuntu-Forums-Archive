---
title: "D-Link DGE-530T driver problem in Hardy"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by phenning on 2008-06-30
the network card was detected by hardy without problems - but it is running extremely slow. I tus tried to install the Linux driver that ships with the card. 

to get the install script to run i changed:
  /bin/sh to /bin/bash
and created a symlink to point 
  ln -s /usr/src/linux-headers /usr/src/linux-2.6.24-19-generic/

when i run the install script it fails during the kernel compiling I suspect due to unrecognized kernel header version.

can anyone help? the output of the install script and log is:

Create tmp dir (/tmp/Sk98IFXGIaJCMAASXaDFPKnWk)                      [   OK   ]
Check user id (0)                                                    [   OK   ]
Check kernel version (2.6.24-19-generic)                             [   OK   ]
Check kernel symbol file (/proc/kallsyms)                            [   OK   ]
Check kernel type (SMP)                                              [   OK   ]
Check number of CPUs (2)                                             [   OK   ]
Check architecture./install.sh: line 414: arch: command not found
 (found)                                                             [   OK   ]
Set architecture
 (ppc)                                                               [   OK   ]
Check compiler (/usr/bin/gcc)                                        [   OK   ]
Check mcmodel flags (none)                                           [   OK   ]
Check module support (/sbin/insmod)                                  [   OK   ]
Check make (/opt/eldk/usr/bin/make)                                  [   OK   ]
Check archive file (sk98lin)                                         [   OK   ]
Check kernel gcc version (4.2.3) (Kernel:4.2.3 == gcc:4.2.3)         [   OK   ]
Check sk98lin driver availability (not loaded)                       [   OK   ]
Check kernel header files (/usr/src/linux)                           [   OK   ]
Unpack the sources (done)                                            [   OK   ]
Check sources for .config file (/usr/src/linux/.config)              [   OK   ]
Copy and check .config file (done)                                   [   OK   ]
Check the mem address space (highmem)                                [   OK   ]
Change IOMMU (disabled)                                              [   OK   ]
Create new .config file (done)                                       [   OK   ]
Execute: make oldconfig (done)                                       [   OK   ]
Check kernel header version (not recognized)                         [  warn  ]
Check kernel functions (Changed: nothing)                            [   OK   ]
Compile the kernel (error)                                           [ failed ]


log file only gives:+++ Compile the driver
+++ ====================================
make: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
+++ Compiler error

---

### Post by wenhui100 on 2009-01-13
i have the same Problem modpost 0 module ... my kernel version is way ealier than urs ..Linux 2.6.22-14-server on i686

---

