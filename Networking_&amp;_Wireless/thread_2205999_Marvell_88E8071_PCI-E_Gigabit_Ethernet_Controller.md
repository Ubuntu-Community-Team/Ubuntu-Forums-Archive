---
title: "Marvell 88E8071 PCI-E Gigabit Ethernet Controller"
date: 2014-02-16
forum: Networking &amp; Wireless
---

### Post by ryan54 on 2014-02-16
New to linux and having some issues getting my on-board NIC recognized.  Spent a day trolling the internet and have gotten a little further than when I started , but still can't seem to get it installed on 12.04.4 LTS.  Here's the output from the driver install and the install.log.

> Action: 3
Disconnect alternative devices:  (done)                                                                                                                                                             [   OK   ]
Unload alternative driver (done)                                                                                                                                                                    [   OK   ]
Create tmp dir (/tmp/Sk98IbbiAMQaakYiGRXROiNUq)                                                                                                                                                     [   OK   ]
Check user id (0)                                                                                                                                                                                   [   OK   ]
Check kernel version (3.11.0-15-generic)                                                                                                                                                            [   OK   ]
Check kernel symbol file (/proc/kallsyms)                                                                                                                                                           [   OK   ]
Check kernel type (SMP)                                                                                                                                                                             [   OK   ]
Check number of CPUs (2)                                                                                                                                                                            [   OK   ]
Check architecture (found)                                                                                                                                                                          [   OK   ]
Set architecture (x86_64)                                                                                                                                                                           [   OK   ]
Check compiler (/usr/bin/gcc)                                                                                                                                                                       [   OK   ]
Check mcmodel flags (kernel)                                                                                                                                                                        [   OK   ]
Check module support (/sbin/insmod)                                                                                                                                                                 [   OK   ]
Check make (/usr/bin/make)                                                                                                                                                                          [   OK   ]
Check kernel gcc version (4.6.3) (Kernel:4.6.3 == gcc:4.6.3)                                                                                                                                        [   OK   ]
Check sk98lin driver availability (not loaded)                                                                                                                                                      [   OK   ]
Check kernel header files (/lib/modules/3.11.0-15-generic/build)                                                                                                                                    [   OK   ]
Check driver location (/lib/modules/3.11.0-15-generic/build/drivers/net/ethernet/marvell)                                                                                                           [   OK   ]
Check sources for .config file (/lib/modules/3.11.0-15-generic/build/.config)                                                                                                                       [   OK   ]
Copy and check .config file (done)                                                                                                                                                                  [   OK   ]
Check the mem address space (lowmem)                                                                                                                                                                [   OK   ]
Change IOMMU (enabled)                                                                                                                                                                              [   OK   ]
Create new .config file (done)                                                                                                                                                                      [   OK   ]
Execute: make oldconfig (done)                                                                                                                                                                      [   OK   ]
Check modpost availability (available)                                                                                                                                                              [   OK   ]
Unpack the sources (done)                                                                                                                                                                           [   OK   ]
Check firmware availability (done)                                                                                                                                                                  [   OK   ]
Execute: make prepare (done)                                                                                                                                                                        [   OK   ]
Check kernel header versiongrep: /lib/modules/3.11.0-15-generic/build/include/linux/version.h: No such file or directory
./functions: line 1117: [: !=: unary operator expected
grep: /lib/modules/3.11.0-15-generic/build/include/linux/version.h: No such file or directory
./functions: line 1126: [: !=: unary operator expected
 (Kernel:3.11.0 == Header:)                                                                                                                                                                         [   OK   ]
Check kernel functions (Changed: nothing)                                                                                                                                                           [   OK   ]
Compile the kernel (error)                                                                                                                                                                          [ failed ]


> +++ Install mode: User
+++ Driver version: 10.93.3.3 (Aug-22-2012)
+++ Kernel version 3.11.0-15-generic
+++ smp_count=1
+++ cpu_number=2
+++ kernel_machine=x86_64
+++ Architecture: x86_64
+++ modpost available
+++ Unpack the sources
+++ ====================================
+++ tar xfv sk98lin.tar
2.6/
2.6/sky2.c
2.6/skethtool.c
2.6/skproc.c
2.6/Makefile
2.6/skge.c
2.6/h/
2.6/h/skdrv1st.h
2.6/h/skdrv2nd.h
2.6/skdim.c
common/
common/skaddr.c
common/fwos.c
common/skgeinit.c
common/skgehwt.c
common/skspi.c
common/sk98lin.htm
common/fwapp.c
common/sktimer.c
common/fwhci.c
common/fwptrn.c
common/flashfun.c
common/fwfunctions.c
common/skgemib.c
common/vpdcheck.c
common/skvpd.c
common/skpflash.c
common/sky2le.c
common/fwimage.c
common/fwoids.c
common/skgesirq.c
common/sk98lin.4
common/fwmain.c
common/sktwsi.c
common/skgepnmi.c
common/sklm80.c
common/skgespilole.c
common/skxmac2.c
common/sk98lin.txt
common/h/
common/h/sktimer.h
common/h/fwimage.h
common/h/sktypes.h
common/h/fwptrn.h
common/h/skdebug.h
common/h/skaddr.h
common/h/skversion.h
common/h/skgeasfapi.h
common/h/lm80.h
common/h/skvpd.h
common/h/skgetwsi.h
common/h/skgeinit.h
common/h/skgesirq.h
common/h/skpflash.h
common/h/skqueue.h
common/h/fwoids.h
common/h/skcsum.h
common/h/skgepnm2.h
common/h/skspi.h
common/h/fwapp.h
common/h/skpcidevid.h
common/h/fwos.h
common/h/mvyexhw.h
common/h/sktwsi.h
common/h/fwmain.h
common/h/xmac_ii.h
common/h/fwhci.h
common/h/skgehw.h
common/h/skgedrv.h
common/h/sky2le.h
common/h/skgepnmi.h
common/h/flash.h
common/h/fwcommon.h
common/h/skgehwt.h
common/h/skerror.h
common/skqueue.c
common/skgeasfapi.c
common/skcsum.c
misc/
misc/Kconfig
misc/Configure.help

+++ Compile the driver
+++ ====================================
make: Entering directory `/usr/src/linux-headers-3.11.0-15-generic'
make -C /lib/modules/3.11.0-15-generic/build \
        KBUILD_SRC=/usr/src/linux-headers-3.11.0-15-generic \
        KBUILD_EXTMOD="/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all" -f /usr/src/linux-headers-3.11.0-15-generic/Makefile \

test -e include/generated/autoconf.h -a -e include/config/auto.conf || (                \
        echo >&2;                                                       \
        echo >&2 "  ERROR: Kernel configuration is invalid.";           \
        echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
        echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";      \
        echo >&2 ;                                                      \
        /bin/false)
mkdir -p /tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/.tmp_versions ; rm -f /tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/.tmp_versions/*
make -f /usr/src/linux-headers-3.11.0-15-generic/scripts/Makefile.build obj=/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all
   rm -f /tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/built-in.o; ar rcsD /tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/built-in.o
  cc -Wp,-MD,/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/.skge.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include -I/usr/src/linux-headers-lbm- -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/inclu
de -Iarch/x86/include/generated  -I/usr/src/linux-headers-3.11.0-15-generic/include -Iinclude -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/lin
ux-headers-3.11.0-15-generic/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-15-generic/include/linux/kconfig.h -Iubuntu/include -I/usr/src/linux-headers-3.11.0-15-generic/ubuntu
/include   -I/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-
delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FR
AME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-lar
ger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-s
tack -DCC_HAVE_ASM_GOTO   -I/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_NO_RLMT -DSK_LINUX -DUSE_SK_RSS_SUPPORT -DSK98LIN_DIAG  -DMODULE
-D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(skge)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)" -c -o /tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.o /tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c
  cc -Wp,-MD,/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/.sky2.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include -I/usr/src/linux-headers-lbm- -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/inclu
de -Iarch/x86/include/generated  -I/usr/src/linux-headers-3.11.0-15-generic/include -Iinclude -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/lin
ux-headers-3.11.0-15-generic/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-15-generic/include/linux/kconfig.h -Iubuntu/include -I/usr/src/linux-headers-3.11.0-15-generic/ubuntu
/include   -I/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-
delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FR
AME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-lar
ger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-s
tack -DCC_HAVE_ASM_GOTO   -I/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_NO_RLMT -DSK_LINUX -DUSE_SK_RSS_SUPPORT -DSK98LIN_DIAG  -DMODULE
-D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(sky2)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)" -c -o /tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/sky2.o /tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/sky2.c
In file included from /tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c:78:0:
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/h/skpcidevid.h:32:47: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__devinitdata’
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c:112:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sk98lin_init_device’
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c:390:14: error: ‘sk98lin_pci_tbl’ undeclared here (not in a function)
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c:391:12: error: ‘sk98lin_init_device’ undeclared here (not in a function)
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c:392:2: error: implicit declaration of function ‘__devexit_p’ [-Werror=implicit-function-declaration]
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c:392:2: error: initializer element is not constant
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c:392:2: error: (near initialization for ‘sk98lin_driver.remove’)
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c:449:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sk98lin_init_device’
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c:2170:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘SkGeBoardInit’
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c:142:12: warning: ‘SkGeBoardInit’ declared ‘static’ but never defined [-Wunused-function]
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c:2491:13: warning: ‘BoardInitMem’ defined but not used [-Wunused-function]
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c:5256:13: warning: ‘GetConfiguration’ defined but not used [-Wunused-function]
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c:6045:13: warning: ‘ProductStr’ defined but not used [-Wunused-function]
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c:3504:12: warning: ‘SkGePoll’ defined but not used [-Wunused-function]
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c:877:12: warning: ‘SkGeInitPCI’ defined but not used [-Wunused-function]
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c:306:20: warning: ‘BootString’ defined but not used [-Wunused-variable]
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c:319:27: warning: ‘sk98lin_ethtool_ops’ defined but not used [-Wunused-variable]
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.c:386:1: error: ‘__mod_pci_device_table’ aliased to undefined symbol ‘sk98lin_pci_tbl’
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/sky2.c: In function ‘HandleReceives’:
/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/sky2.c:1986:4: error: too few arguments to function ‘__vlan_hwaccel_put_tag’
/usr/src/linux-headers-3.11.0-15-generic/include/linux/if_vlan.h:236:31: note: declared here
cc1: some warnings being treated as errors
make[2]: *** [/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/skge.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[2]: *** [/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all/sky2.o] Error 1
make[1]: *** [_module_/tmp/Sk98IbbiAMQaakYiGRXROiNUq/all] Error 2
make: *** [sub-make] Error 2
make: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'
+++ Compiler error

---

