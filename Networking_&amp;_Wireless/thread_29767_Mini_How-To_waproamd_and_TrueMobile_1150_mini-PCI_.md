---
title: "Mini How-To: waproamd and TrueMobile 1150 mini-PCI wireless NIC"
date: 2005-04-25
forum: Networking &amp; Wireless
---

### Post by kmyram on 2005-04-25
Hi everybody!

Do you like me enjoy the luxury of having WLAN-access both at home, at school/work and some third place but hate that fthe "factory-delivered" orinoco-driver in Hoary can't deliver scan-possibilities? Well, just make your own.

In my case I needed to make some adjustments, so that the TrueMobile 1150 mini-PCI wireless NIC on my Dell Latitude C840 would work:

[list=1]
[*]Download newer driver [http://ozlabs.org/people/dgibson/dldwd/](http://ozlabs.org/people/dgibson/dldwd/)
[*]Unpack and edit the Makefile (sudo gedit $pwd/Makefile)
[*]Comment out the 3 lines  including "ifdef CONFIG_PCI" (I did this because it wouldn't compile otherwise)
[*]make!
[*]Locate the orinoco and orinoco_cs modules (/lib/modules/<kernel>/kernel/drivers/net/wireless) and rename these
[*]copy the new modules from the root of where you compiled (orinoco.ko and orinoco_cs.ko)
[*]Reboot
[*]Set up waproamd accordingly (make the files in the keys-directory with the MAC-address of your AP's and put the WEP-key in them, ie. $ cat $WEPKEY >> /etc/waproamd/keys/$MACADDRESS.wep
[*]Roam away
[/list]

**Disclaimer:** As this is my first attempt to write a help or guide like this your comments are much appreciated.

Many thanks in advance

---

### Post by vladypus on 2005-09-26
downloaded new orinico driver (.15rc2), edited the Makefile, but when i try to make, it gives the following error: 
Makefile:36: *** The kernel source is not configured.  Stop.

i think it might be this line:
KERNEL_SRC = $(shell readlink -f /lib/modules/`uname -r`/build)
because when i run this from the shell in verbose it says: no such file or directory

i have also tried:
KERNEL_SRC = $(shell readlink -f /lib/modules/`uname -r`)
and i've tried just typing out the actual path

Here are the first 36 lines of the file:
> 
KERNEL_SRC = $(shell readlink -f /lib/modules/`uname -r`/build)

# Output directory that you used when building Linux kernel, if any.
# Note: this driver will be compiled to the current directory regardless.
O = $(KERNEL_SRC)

# You don't need to change anything below this line in most cases

CONF_DIR = /etc/pcmcia
                                                                               
ORINOCODIR = $(shell pwd)
KERNEL_VERSION = $(shell sed -ne 's/"//g;s/^\#define UTS_RELEASE //p' \
		   $(O)/include/linux/version.h)

MODULE_DIR_TOP = /lib/modules/$(KERNEL_VERSION)
MODULE_DIR_PCMCIA = $(MODULE_DIR_TOP)/pcmcia
MODULE_DIR_WIRELESS = $(MODULE_DIR_TOP)/kernel/drivers/net/wireless

DOT_CONFIG = $(wildcard $(O)/.config)
ifeq (,$(DOT_CONFIG))
$(error The kernel source is not configured)
endif
include $(DOT_CONFIG)

i'm a newbie, any help would be appreciated.

---

