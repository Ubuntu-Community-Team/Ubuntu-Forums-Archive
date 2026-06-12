---
title: "Onboard NIC not detected (ASUS P5GD1 motherboard)"
date: 2005-05-12
forum: Networking &amp; Wireless
---

### Post by Corné van de Pol on 2005-05-12
Hello,

I have an Intel chipset on my ASUS P5GD1 motherboard. Yesterday I installed Hoary with success except for my onboard network card.  :-| 

Lspci gives

0000:02:00.0 Ethernet Controller: Marvell Technology Group Ltd.: Unknown Device 4632 (rev 15)

I already know that this is caused by the outdated module sk98lin. So I downloaded the latest drivers from marvell however I am new in the Linux world so I don’t know how to install this driver.  ](*,)  Is there somebody who does know?

Thanks in advance,

Corné van de Pol

---

### Post by nad on 2005-05-12
The zip package available from asus has full instructions.

You will need to install the build-essentials package, available through your synaptic package manager, as well as the kernel-headers package for your running kernel ( uname -r ) as described in the README before building the driver module.

---

### Post by Octane on 2005-06-19
[QUOTE=nad]The zip package available from asus has full instructions.

You will need to install the build-essentials package, available through your synaptic package manager, as well as the kernel-headers package for your running kernel ( uname -r ) as described in the README before building the driver module.[/QUOTE]
 I have the A8V-E Deluxe board with the Marvell 88E8053 NIC and I can't get the Asus-supplied NIC driver to compile the module correctly:
```
Create tmp dir (/tmp/Sk98IcWfdKfFFPNqEoISEbLZm)                      [   OK   ]
Check user id (0)                                                    [   OK   ]
Check kernel version (2.6.10-5-amd64-generic)                        [   OK   ]
Check kernel symbol file (/proc/kallsyms)                            [   OK   ]
Check kernel type (SP)                                               [   OK   ]
Check architecture (found)                                           [   OK   ]
Set architecture (x86_64)                                            [   OK   ]
Check compiler (/usr/bin/gcc)                                        [   OK   ]
Check mcmodel flags (64bit)                                          [   OK   ]
Check module support (/sbin/insmod)                                  [   OK   ]
Check make (/usr/bin/make)                                           [   OK   ]
Check archive file (sk98lin)                                         [   OK   ]
Check kernel gcc version (3.3.5) (Kernel:3.3.5 == gcc:3.3.5)         [   OK   ]
Check sk98lin driver availability (not loaded)                       [   OK   ]
Check kernel header files (/usr/src/linux)                           [   OK   ]
Check the mem address space (lowmem)                                 [   OK   ]
Unpack the sources (done)                                            [   OK   ]
Check sources for .config file (/usr/src/linux/.config)              [   OK   ]
Copying file from proc directory (done)                              [   OK   ]
Copy and check .config file (done)                                   [   OK   ]
Execute: make oldconfig (done)                                       [   OK   ]
Check kernel header version (Kernel:2.6.10-5-amd64-generic == Header:2.6.10-5-amd64-generic)                                                         [   OK   ]
Check kernel functions (Changed: nothing)                            [   OK   ]
Compile the kernel (error)                                           [ failed ]

An error has occurred during the compile proces which prevented
the installation from completing.
Take a look at the log file install.log for more informations.
Installation of sk98lin driver module failed.
```
install.log snip:
```
+++ Compile the driver
+++ ====================================
make: Entering directory `/usr/src/linux-source-2.6.10'
  CC [M]  /tmp/Sk98IcWfdKfFFPNqEoISEbLZm/all/skge.o
/tmp/Sk98IcWfdKfFFPNqEoISEbLZm/all/skge.c: In function `sk98lin_init_device':
/tmp/Sk98IcWfdKfFFPNqEoISEbLZm/all/skge.c:398: error: structure has no member na
med `last_stats'
/tmp/Sk98IcWfdKfFFPNqEoISEbLZm/all/skge.c:539: error: structure has no member na
med `last_stats'
make[1]: *** [/tmp/Sk98IcWfdKfFFPNqEoISEbLZm/all/skge.o] Error 1
make: *** [_module_/tmp/Sk98IcWfdKfFFPNqEoISEbLZm/all] Error 2
make: Leaving directory `/usr/src/linux-source-2.6.10'
+++ Compiler error
```

---

