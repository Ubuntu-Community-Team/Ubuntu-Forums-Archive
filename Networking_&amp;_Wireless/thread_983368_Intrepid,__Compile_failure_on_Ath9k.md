---
title: "Intrepid,  Compile failure on Ath9k"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by needlern32724 on 2008-11-15
Been struggling for several days to get some performance out of the kernel provided ath9k wireless driver. Decided to rm it and build the compat-wireless-2.6 version found here [URL="http://linuxwireless.org/en/users/Download"].

I now find that I can not get it to compile for the following reason(s):
> bill@hb5:~/wireless/compat-wireless-2008-11-15$ make
make -C /lib/modules/2.6.27-7-generic/build M=/home/bill/wireless/compat-wireless-2008-11-15 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.27-7-generic/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/bill/wireless/compat-wireless-2008-11-15/drivers/net/b44.o
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from include/linux/textsearch.h:7,
                 from include/linux/skbuff.h:26,
                 from include/linux/if_ether.h:114,
                 from /home/bill/wireless/compat-wireless-2008-11-15/include/net/compat.h:9,
                 from <command-line>:0:
include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
include/linux/mmzone.h:197:5: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from include/linux/textsearch.h:7,
                 from include/linux/skbuff.h:26,
                 from include/linux/if_ether.h:114,
                 from /home/bill/wireless/compat-wireless-2008-11-15/include/net/compat.h:9,
                 from <command-line>:0:
include/linux/mmzone.h:218: error: ‘MAX_NR_ZONES’ undeclared here (not in a function)
In file included from include/linux/scatterlist.h:6,
                 from include/asm/dma-mapping.h:9,
                 from include/linux/dma-mapping.h:52,
                 from include/linux/dmaengine.h:29,
                 from include/linux/skbuff.h:29,
                 from include/linux/if_ether.h:114,
                 from /home/bill/wireless/compat-wireless-2008-11-15/include/net/compat.h:9,
                 from <command-line>:0:
include/linux/mm.h:438:63: warning: "NR_PAGEFLAGS" is not defined
include/linux/mm.h:486:62: warning: "NR_PAGEFLAGS" is not defined
make[2]: *** [/home/bill/wireless/compat-wireless-2008-11-15/drivers/net/b44.o] Error 1
make[1]: *** [_module_/home/bill/wireless/compat-wireless-2008-11-15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2
Searching has not provided any usable info. I did have this compiled a couple of weeks back, but some upgrade killed it and I had to start again. I just tried re-making the kernel modules and it, too, failed.
I'm kind  of stuck. Need your help. I'm a 5yr gentoo user new to the ubuntu field. Don't really want to muck around too much for fear of breaking things.

System vitals:

amd64, kernel-2.6.27-7 generic, D-Link DWA-552.
>  Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
	Subsystem: D-Link System Inc Device 3a6d
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 3
	Region 0: Memory at d3000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath9k  
What else you need to help me?

Thanks,
Bill

---

### Post by dionblundell on 2009-11-04
I suspect the issue is with an upgrade to GCC and how it works.
I'm having a simlar problem compiling a kernel module on Ubuntu 9.10

I remember reading in the mail list that GCC was being upgraded and that header files would need to be changed and therefore things wouldn't compile from source. I reckon the issue is with GCC and that our source files need updating. This unfortunately updating source is above/beyond me and I don't know where to from here.

---

### Post by t0mppa on 2009-11-04
Considering the original post is one year old, he probably wasn't running same version of GCC (or then you have downgraded yours) and from a quick googling people suggested either ignoring the warning and focusing on the real errors or then reinstalling the kernel headers in case they were corrupted.

A workaround to the original problem is simply installing the linux backports modules, which features the latest version of compat wireless prebuilt for Ubuntu.

---

### Post by dionblundell on 2009-11-04
Oh, I miss-read the date. My mistake.

Anyway, I had the same problem and the issue was not with GCC, I did a remove of the linux-headers, linux-source, build-essential and an autoremove and purge. This got rid of all kernel-headers and build "stuff." I then re-installed build-essential and everything compiles. So I was wrong.

It was an installation error with the kernel headers or build-essential (and its dependencies) a complete purge and re-install fixed it.

---

