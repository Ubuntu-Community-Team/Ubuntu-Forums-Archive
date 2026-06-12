---
title: "zd1201 make drivers"
date: 2005-11-28
forum: Networking &amp; Wireless
---

### Post by vega113 on 2005-11-28
So, like many before me i downloaded firmware and driver for wlna usb card - zd1201.
the firmware was succesfully installed with "make"
but the driver would give me error 

```
vega@ubuntu:~/Desktop/zd1201-014$ dir
makefile  Makefile  README  zd1201.c  zd1201.h
vega@ubuntu:~/Desktop/zd1201-014$ sudo make
make -C /lib/modules/`uname -r`/build/ M=/home/vega/Desktop/zd1201-014 modules
make[1]: Entering directory `/lib/modules/2.6.12-10-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-10-386/build'
make: *** [modules] Error 2

```
this is content of "makefile"
```
#
#	Makefile for zd1201 driver
#

#ifndef KERNEL_SOURCE
KERNEL_SOURCE=/lib/modules/`uname -r`/build/
#endif

#ifndef KERNEL_VERSION
KERNEL_VERSION=$(basename $(shell uname -r))
#endif

#ifndef FIRMWARE
FIRMWARE=zd1201.fw zd1201-ap.fw
#endif

ifneq ($(KERNEL_VERSION),2.6)
$(error Kernel version ${KERNEL_VERSION} not supported by this driver.)
endif

INSTALL = cp -p -f

default: modules

modules:
	make -C ${KERNEL_SOURCE} M=${PWD} modules

clean:
	make -C ${KERNEL_SOURCE} M=${PWD} clean

install:	modules_install

modules_install:
	make -C ${KERNEL_SOURCE} M=${PWD} modules_install

```

what is the meaning of this error?

---

### Post by vega113 on 2005-11-29
come on, is the question too stupid, or no one knows the answer? :confused: 
i think i just lack some component...

---

### Post by vega113 on 2005-11-29
nevermind. i checked, and the driver is already there, don't know how...
i guess the kernel already had the driver.

---

