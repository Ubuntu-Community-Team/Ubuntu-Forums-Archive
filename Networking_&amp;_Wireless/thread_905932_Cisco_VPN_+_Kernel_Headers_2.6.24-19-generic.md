---
title: "Cisco VPN + Kernel Headers 2.6.24-19-generic"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by Network Nurd on 2008-08-30
I'm having issues getting the Cisco VPN Client for Linux to install.  I've been able to get it up and running w/o issues on a recent VMWare build (using Hardy Heron as well.)  Now I keep getting errors.  I've followed the steps posted in many topics with patching of the vpnclient, but was not successful (see post here for example:  [http://ubuntuforums.org/showthread.php?t=769273](http://ubuntuforums.org/showthread.php?t=769273))

Here are my errors:
```

dbough@dbough-laptop:/etc/tmp/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-19-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-19-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-19-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/etc/tmp/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/etc/tmp/vpnclient/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/etc/tmp/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
dbough@dbough-laptop:/etc/tmp/vpnclient$ 
```

Are my headers not compatible with this client?

---

### Post by casevh on 2008-08-31
Try following these instructions.

[http://www.lamnk.com/blog/domain/how-to-install-cisco-vpn-client-on-ubuntu-hardy-heron-804/](http://www.lamnk.com/blog/domain/how-to-install-cisco-vpn-client-on-ubuntu-hardy-heron-804/)

They worked for me.

casevh

---

### Post by Network Nurd on 2008-09-01
Awesome, I'll take a look and let you know if it works.

---

### Post by qwertyking on 2008-09-01
You don't need to patch that release. 

all you have to do is install or upgrade your kernel headers

sudo apt-get install linux-headers-2.6.24-19-generic 

and then try installing the VPN- It should work

---

### Post by Network Nurd on 2008-09-01
No good - still issues.  Is there a way find and remove anything associated w/the VPN install?  I'd like to start from scratch.

```

dbough@dbough-laptop:/etc/tmp/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-19-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-19-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-19-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/etc/tmp/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /etc/tmp/vpnclient/linuxcniapi.o
/etc/tmp/vpnclient/linuxcniapi.c: In function &#8216;CniInjectReceive&#8217;:
/etc/tmp/vpnclient/linuxcniapi.c:341: warning: cast from pointer to integer of different size
/etc/tmp/vpnclient/linuxcniapi.c:342: warning: cast from pointer to integer of different size
/etc/tmp/vpnclient/linuxcniapi.c: In function &#8216;CniInjectSend&#8217;:
/etc/tmp/vpnclient/linuxcniapi.c:481: warning: cast from pointer to integer of different size
/etc/tmp/vpnclient/linuxcniapi.c:482: warning: cast from pointer to integer of different size
/etc/tmp/vpnclient/linuxcniapi.c:491: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/linuxcniapi.c:491: warning: cast from pointer to integer of different size
  CC [M]  /etc/tmp/vpnclient/frag.o
/etc/tmp/vpnclient/frag.c: In function &#8216;queue_fragment&#8217;:
/etc/tmp/vpnclient/frag.c:50: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:50: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:50: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:50: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:52: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:52: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:52: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:52: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:70: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:70: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:70: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:70: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:73: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:73: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:73: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:73: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c: In function &#8216;have_all_fragments&#8217;:
/etc/tmp/vpnclient/frag.c:126: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:126: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:126: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:126: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:134: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:134: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:134: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:134: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:141: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:141: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:141: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:141: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:142: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:146: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:146: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:146: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c:146: warning: cast to pointer from integer of different size
/etc/tmp/vpnclient/frag.c: In function &#8216;need_reorder_frag&#8217;:
/etc/tmp/vpnclient/frag.c:198: warning: cast to pointer from integer of different size
  CC [M]  /etc/tmp/vpnclient/IPSecDrvOS_linux.o
  CC [M]  /etc/tmp/vpnclient/interceptor.o
/etc/tmp/vpnclient/interceptor.c: In function &#8216;recv_ip_packet_handler&#8217;:
/etc/tmp/vpnclient/interceptor.c:655: warning: assignment makes integer from pointer without a cast
/etc/tmp/vpnclient/interceptor.c:676: warning: passing argument 2 of &#8216;CniNewFragment&#8217; makes pointer from integer without a cast
/etc/tmp/vpnclient/interceptor.c: In function &#8216;do_cni_send&#8217;:
/etc/tmp/vpnclient/interceptor.c:794: error: invalid operands to binary -
make[2]: *** [/etc/tmp/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/etc/tmp/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
dbough@dbough-laptop:/etc/tmp/vpnclient$ 

```
```

dbough@dbough-laptop:/etc/tmp/vpnclient$ cat Makefile 
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
EXTRA_CFLAGS += -mcmodel=kernel -mno-red-zone
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
dbough@dbough-laptop:/etc/tmp/vpnclient$ 

```

---

### Post by qwertyking on 2008-09-01
as i said- you dont need to patch that release.
delete the vpnclient folder and start over

---

### Post by Network Nurd on 2008-09-01
> **qwertyking said:**
> You don't need to patch that release. 

all you have to do is install or upgrade your kernel headers

sudo apt-get install linux-headers-2.6.24-19-generic 

and then try installing the VPN- It should work

dbough@dbough-laptop:/etc/tmp/vpnclient$ sudo apt-get install linux-headers-2.6.24-19-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-19-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dbough@dbough-laptop:/etc/tmp/vpnclient$

---

### Post by qwertyking on 2008-09-01
Im guessing the vpn is the k9 release?

---

### Post by qwertyking on 2008-09-01
if it isnt- please head to [http://tuxx-home.at/archives/2007/05/29/T16_34_26/](http://tuxx-home.at/archives/2007/05/29/T16_34_26/)

---

### Post by Network Nurd on 2008-09-01
I've tried  vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz and 4.8.02.  I was able to get 4.8.02 running on a VMWare instance, but not on the real thing (the VMWare instance was a straight install of the vpn software.  I didnt have to patch it or anything else.)

I have access to whichever release works.

I'll peek at the link you've posted - thanks.

---

### Post by Network Nurd on 2008-09-01
Still no good - same errors.  I've re-downloaded all files and followed instructions exactly.  This distro was installed with wubi - would that cause issues?

---

