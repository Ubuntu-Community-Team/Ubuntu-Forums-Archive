---
title: "zd1211 help"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by skooge on 2007-02-21
I got one of these Wifi max dealys for christmas-->[http://gear.ign.com/articles/704/704528p1.html]("http://gear.ign.com/articles/704/704528p1.html"), but I was never able to figure out how to set it up windows.  Well I was look a what was on the disk last night and I saw there was an installer for linux.  I have Ubuntu 6.06 and I was woundering, how mght I go about installing it? this what it says in the makefile:

#
# .zd1211 - USB2.0 802.11b/g driver for Zydas ZD1211 chipsets
#
#
#

CC=gcc
CPP=g++
LD=ld
rM=rm -f -r

# if the kernel is 2.6.x, trun on this
KERN_26=y
KERNEL_SOURCE=/usr/src/linux-2.6.9

# if the kernel is 2.4.x, trun on this
#KERN_24=y
#KERNEL_SOURCE=/usr/src/linux-2.4.26

SRC_DIR=src
DEFINES=-D__KERNEL__ -DMODULE=1


KERNRELEASE := $(shell uname -r;)
MODPATH := /lib/modules/$(KERNRELEASE)


ifeq ($(KERN_26), y)

ifeq ($(ZD1211REV_B),1)
MODULE = zd1211b.ko
endif
ifeq ($(ZD1211REV_B),0)
MODULE = zd1211.ko
endif

INCLUDES=-I$(KERNEL_SOURCE)/include -I$(SRC_DIR)/include/ -I$(SRC_DIR)

EXTRA_CFLAGS += -I$(PWD)/src/include

ifndef CONFIG_FRAME_POINTER
EXTRA_CFLAGS += -fomit-frame-pointer
endif
         
ifdef CONFIG_SMP
EXTRA_CFLAGS += -D__SMP__ -DSMP
endif

KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)

WLAN_SRC=$(PWD)


EXTRA_CFLAGS += -O2 -Wall -Wstrict-prototypes -pipe 
#EXTRA_CFLAGS += -Wa,-a,-ad -g
EXTRA_CFLAGS += -DHOST_IF_USB
EXTRA_CFLAGS += -DAMAC
EXTRA_CFLAGS += -DGCCK
EXTRA_CFLAGS += -DOFDM
EXTRA_CFLAGS += -DHOSTAPD_SUPPORT
EXTRA_CFLAGS += -DUSE_EP4_SET_REG
EXTRA_CFLAGS += -DDOWNLOADFIRMWARE
EXTRA_CFLAGS += -DfTX_GAIN_OFDM=0
EXTRA_CFLAGS += -DfNEW_CODE_MAP=1
EXTRA_CFLAGS += -DfWRITE_WORD_REG=1
EXTRA_CFLAGS += -DfREAD_MUL_REG=1
EXTRA_CFLAGS += -DENHANCE_RX=1

EXTRA_CFLAGS += -DZDCONF_MENUDBG
EXTRA_CFLAGS += -DZDCONF_APDBG
ifeq ($(ZD1211REV_B),1)
	EXTRA_CFLAGS += -DZD1211B
endif
ifeq ($(ZD1211REV_B),0)
	EXTRA_CFLAGS += -DZD1211
endif
#EXTRA_CFLAGS += $(INCLUDES)

ifeq ($(ZD1211REV_B),1)
	obj-m := zd1211b.o
endif
ifeq ($(ZD1211REV_B),0)
	obj-m := zd1211.o
endif
zd1211-objs := $(SRC_DIR)/zd1205.o \
$(SRC_DIR)/zdasocsvc.o \
$(SRC_DIR)/zdauthreq.o \
$(SRC_DIR)/zdauthrsp.o \
$(SRC_DIR)/zdmmrx.o \
$(SRC_DIR)/zdshared.o \
$(SRC_DIR)/zdhci.o \
$(SRC_DIR)/zdglobal.o \
$(SRC_DIR)/zdencrypt.o \
$(SRC_DIR)/zdpmfilter.o \
$(SRC_DIR)/zdpsmon.o \
$(SRC_DIR)/zdsynch.o \
$(SRC_DIR)/zdbuf.o \
$(SRC_DIR)/zd1205_proc.o \
$(SRC_DIR)/zdhw.o \
$(SRC_DIR)/zddebug.o \
$(SRC_DIR)/zdtkipseed.o \
$(SRC_DIR)/zdmic.o \
$(SRC_DIR)/zddebug2.o \
$(SRC_DIR)/zdusb.o 
ifeq ($(ZD1211REV_B),1)
zd1211-objs += $(SRC_DIR)/zd1211.o
zd1211b-objs = $(zd1211-objs)
endif
ifeq ($(ZD1211REV_B),0)
zd1211-objs += $(SRC_DIR)/zd1211.o
endif

all:

ifneq ($(KERNELRELEASE),)

else
ifndef ZD1211REV_B
		make both
else
		@echo -e $(KDIR)
		@echo -e $(PWD)
		@echo -e $(EXTRA_CFLAGS)
		@echo -e $(zd1211-objs)
		$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules
endif

endif

else # kernel 2.4

INCLUDES=-I$(KERNEL_SOURCE)/include -I$(SRC_DIR)/include/ -I$(SRC_DIR)
ifeq ($(ZD1211REV_B),1)
	MODULE = zd1211b.o
endif
ifeq ($(ZD1211REV_B),0)
	MODULE = zd1211.o
endif

OBJECTS=$(SRC_DIR)/zd1205.o \
    $(SRC_DIR)/zdasocsvc.o \
    $(SRC_DIR)/zdauthreq.o \
    $(SRC_DIR)/zdauthrsp.o \
    $(SRC_DIR)/zdmmrx.o \
    $(SRC_DIR)/zdshared.o \
    $(SRC_DIR)/zdhci.o \
    $(SRC_DIR)/zdglobal.o \
    $(SRC_DIR)/zdencrypt.o \
    $(SRC_DIR)/zdpmfilter.o \
    $(SRC_DIR)/zdpsmon.o \
    $(SRC_DIR)/zdsynch.o \
    $(SRC_DIR)/zdbuf.o \
    $(SRC_DIR)/zd1205_proc.o \
    $(SRC_DIR)/zdhw.o \
    $(SRC_DIR)/zddebug.o \
    $(SRC_DIR)/zdtkipseed.o \
    $(SRC_DIR)/zdmic.o \
	$(SRC_DIR)/zddebug2.o \
    $(SRC_DIR)/zdusb.o 
    OBJECTS += $(SRC_DIR)/zd1211.o

CFLAGS=-O -Wall -Wstrict-prototypes -pipe  #-Wa,-a,-ad -g

ifdef CONFIG_MODVERSIONS
CFLAGS += -DMODVERSIONS -include $(KERNEL_SOURCE)/include/linux/modversions.h   #kernel 2.4
endif

ifndef CONFIG_FRAME_POINTER
CFLAGS += -fomit-frame-pointer
endif

ifdef CONFIG_SMP
CFLAGS += -D__SMP__ -DSMP
endif

CFLAGS += -DHOST_IF_USB
CFLAGS += -DAMAC
CFLAGS += -DGCCK
CFLAGS += -DOFDM
CFLAGS += -DHOSTAPD_SUPPORT
CFLAGS += -DUSE_EP4_SET_REG
CFLAGS += -DDOWNLOADFIRMWARE
CFLAGS += -DfTX_GAIN_OFDM=0
CFLAGS += -DfNEW_CODE_MAP=1
CFLAGS += -DfWRITE_WORD_REG=1
CFLAGS += -DfREAD_MUL_REG=1
CFLAGS += -DZDCONF_MENUDBG
CFLAGS += -DZDCONF_APDBG
ifeq ($(ZD1211REV_B),1)
	CFLAGS += -DZD1211B
endif
ifeq ($(ZD1211REV_B),0)
	CFLAGS += -DZD1211
endif
CFLAGS += -DENHANCE_RX=1

ifndef ZD1211REV_B
all:
	make both
else
all: $(MODULE)
endif

$(MODULE): $(OBJECTS)
	$(LD) -static  -r $(OBJECTS) -o $(MODULE)
	chmod -x $(MODULE)

%.o: %.c
	$(CC) -static $(CFLAGS) $(INCLUDES) $(DEFINES) $(DEBUG) -c $< -o $@                              
    
endif
both:
	make clean
	make ZD1211REV_B=0
	make ZD1211REV_B=0 install
	make clean
	make ZD1211REV_B=1
	make ZD1211REV_B=1 install

menuconfig:
	sh scripts/Menuconfig 

oldconfig:
	@cp -f .oldconfig .config
	@echo Default configuration is applied.
	@echo Now, run make menuconfig to make custom configuration

inst:
	make
	make install

	

install: all
	mkdir -p $(MODPATH)/net
#	mkdir -p /etc/zd1211
	cp $(MODULE) $(MODPATH)/net
	depmod -a

debug:
	gcc -o apdbg apdbg.c
	chmod +x apdbg
	cp ./apdbg /sbin/apdbg   
	make -C Menudbg
	mv Menudbg/menudbg .
	chmod +x menudbg
	cp ./menudbg /sbin

clean:
	rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o $(SRC_DIR)/*.o  $(SRC_DIR)/.*.o.cmd menudbg apdbg

---

### Post by Forlornity on 2007-02-21
Try opening a terminal into the folder where the makefile is, then type make, followed by sudo make install although i'm a bit of a nublet, so I sure as hell won't be able to help beyond that.

---

### Post by abyssknight on 2007-02-21
I'll try to help you more on IM, but I did find this: [http://ubuntuforums.org/showthread.php?t=288753](http://ubuntuforums.org/showthread.php?t=288753)

Basically, just copy the driver off the CD into a directory and do a make, then make install. After that I'm lost, but if you follow the directions in that one post you should be fine.

---

