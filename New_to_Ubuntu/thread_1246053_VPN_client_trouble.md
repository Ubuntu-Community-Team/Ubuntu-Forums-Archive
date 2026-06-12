---
title: "VPN client trouble"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by nickco on 2009-08-21
I have been trying to install the Cisco VPN client version: 4.8.01. 

Here is the error I'm Getting:

```
nick@ubuntu:~/Desktop/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 

Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.

Directory containing linux kernel source code [/lib/modules/2.6.28-13-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.28-13-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.28-13-generic/build" will be used to build the module.
Is the above correct [y]
Making module
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/nick/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/nick/Desktop/vpnclient/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/nick/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
```and here is the makefile:

```
#
# KBUILD build parameters.
#
KERNEL_SOURCES  ?= /lib/modules/$(shell uname -r)/build
KERNEL_HEADERS  := -I$(KERNEL_SOURCES)/include
MODULE_ROOT     ?= /lib/modules/$(shell uname -r)/CiscoVPN
SUBARCH         := $(shell uname -m)


MODULE_NAME := cisco_ipsec

SOURCE_OBJS := linuxcniapi.o frag.o IPSecDrvOS_linux.o interceptor.o linuxkernelapi.o

ifeq ($(SUBARCH),x86_64)
CFLAGS += -mcmodel=kernel -mno-red-zone
NO_SOURCE_OBJS := libdriver64.so
else
NO_SOURCE_OBJS := libdriver.so
endif

ifneq ($(KERNELRELEASE),)

obj-m := $(MODULE_NAME).o 

$(MODULE_NAME)-objs :=  $(SOURCE_OBJS) $(NO_SOURCE_OBJS)

EXTRA_CFLAGS += -Wall \
                -D_LOOSE_KERNEL_NAMES \
                -DCNI_LINUX_INTERFACE \
                -DHAVE_CONFIG_H

ifeq ($(PATCHLEVEL), 4)
$(obj)/$(MODULE_NAME).o: $($(MODULE_NAME)-objs)
    $(LD) $(EXTRA_LDFLAGS) -r -o $@ $($(MODULE_NAME)-objs)
endif #PATCHLEVEL

else #KERNRELEASE

default: 
    $(MAKE) -C $(KERNEL_SOURCES) SUBDIRS=$(PWD) modules
clean:
    -rm -f $(SOURCE_OBJS)
    -rm -f $(MODULE_NAME).mod.*
    -rm -f $(MODULE_NAME).{o,ko}

endif #KERNRELEASE
```I don't have much experience and am not sure what is wrong. Thanks for the help.

---

### Post by nickco on 2009-08-21
Bump

---

### Post by xPr0star on 2009-08-21
EDIT: There is a package for it, its called vpnc search for it in Synaptic Package manager




I think you need to apply two kernel patches im not sure. Also do you have the headers? Also did you search for a package? There could be one you should try google. Maybe then you won't have to compile from source

---

