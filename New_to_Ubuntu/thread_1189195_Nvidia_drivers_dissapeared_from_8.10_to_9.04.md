---
title: "Nvidia drivers dissapeared from 8.10 to 9.04?"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by fredscripts on 2009-06-16
Hi there!

Just upgraded to 9.04 in Macbook Santa Rosa (3,1). I cannot get enabled desktop effects (and in Hardware Drivers I don't see any nvidia drivers available to enable). I have also swapped the < and º keys.

Please could you help me?

Thank you very much in advance.

---

### Post by jimv on 2009-06-16
You can install the drivers from the command line with this command:

sudo apt-get install nvidia-glx-180 && sudo nvidia-xconfig

Then reboot.

---

### Post by fredscripts on 2009-06-17
it did not work. After rebooting the graphics system didn't load, some error message like "type1" no such device, I imagine this is for the famous xorg.conf that isn't well written by nvidia-xconfig. then I pressed load generics and then I'm back again without drivers.


Any other ideas, please release an update from updatemanager to enable drivers in macbook 3.1. I can't believe 8.10 had the drivers installed after a fresh install by default and 9.04 not, and furthermore it's not trivial how to install them.

---

### Post by achase79 on 2009-06-17
use envy-ng to find and download the correct nvidia drivers

---

### Post by jimv on 2009-06-17
I suppose the next thing to try is the manual installation.

First, download the latest driver from Nvidia's site.  It should be the 185 version.

Then, log out and press Control+Alt+F1.  This will bring up a terminal.  Log in.  Type:

```
sudo /etc/init.d/gdm stop
```

Now we need to uninstall all the current NVIDIA stuff:

```
sudo apt-get remove nvidia*
```

Then cd to whatever directory you downloaded the Nvidia drivers to and type:

```
sudo sh [whatever the driver file is called]
```

Reboot and see if it works now.

---

### Post by fredscripts on 2009-06-21
> **achase79 said:**
> use envy-ng to find and download the correct nvidia drivers

didn't work, after rebooting the graphical system won't boot without going back to generics (no drivers then)

---

### Post by fredscripts on 2009-06-21
> **jimv said:**
> I suppose the next thing to try is the manual installation.

First, download the latest driver from Nvidia's site.  It should be the 185 version.

Then, log out and press Control+Alt+F1.  This will bring up a terminal.  Log in.  Type:

```
sudo /etc/init.d/gdm stop
```

Now we need to uninstall all the current NVIDIA stuff:

```
sudo apt-get remove nvidia*
```

Then cd to whatever directory you downloaded the Nvidia drivers to and type:

```
sudo sh [whatever the driver file is called]
```

Reboot and see if it works now.

Didn't work either:

cat /var/log/nvidia-installer.log 

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Jun 21 21:19:10 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
WARNING: You do not appear to have an NVIDIA GPU supported by the 185.18.14
         NVIDIA Linux graphics driver installed in this system.  For further
         details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in
         the README available on the Linux driver download page at
         www.nvidia.com.
-> License accepted.
-> Installing NVIDIA driver version 185.18.14.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.28-13-generic/build'
-> Kernel output path: '/lib/modules/2.6.28-13-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.28-13-gener
   ic/build SYSOUT=/lib/modules/2.6.28-13-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.28-13-generic/build SUBDIRS
   =/tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz5266/NVIDIA-Linux-x86-185.18.1
   4-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERNEL
   __  -Iinclude  -I/usr/src/linux-headers-2.6.28-13-generic/arch/x86/include -
   include include/linux/autoc
   onf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fn
   o-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32
   -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -m
   arch=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign
   -compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3d
   now -Iarch/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame
   -pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-poin
   ter-sign -fwrapv -I/tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/n
   v -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparen
   theses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-comp
   are -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRI
   NG=\"185.18.14\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"
   KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -
   o /tmp/selfgz5266/NVIDIA-Linux-x86-
   185.18.14-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.
   14-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2025: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.nv-
   vm.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KER
   NEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-13-generic/arch/x86/includ
   e -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit
   -function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return 
   -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32
   -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-
   sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-s
   tack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclara
   tion-after-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz5266/NVIDIA-
   Linux-x86-185.18.14-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch 
   -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Wer
   ror -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__
   -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.14\" -UDEBUG -U_DEBUG -DNDEBUG 
   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUI
   LD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz5266/NVIDIA-Linux-x86-185.1
   8.14-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14
   -pkg1/usr/src/nv/nv-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2025: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.os-
   agp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KE
   RNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-13-generic/arch/x86/inclu
   de -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno
   -common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregpar
   m=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=gene
   ric -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -fno-asynchr
   onous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/includ
   e/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimiz
   e-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -I/t
   mp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv -Wall -Wimplicit -W
   return-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arit
   h -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -W
   no-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.14\" -UDE
   BUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUIL
   D_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz5266
   /NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.tmp_os-agp.o /tmp/selfgz5266/NV
   IDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2025: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.os-
   interface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include 
   -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-13-generic/arch/x86
   /include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -
   Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-i
   mplicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-
   return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=ge
   neric32 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tabl
   es -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-defaul
   t -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -
   Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz5266/NVI
   DIA-Linux-x86-185.18.14-pkg1/usr/src/nv -Wall -Wimplicit -W
   return-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arit
   h -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -W
   no-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.14\" -UDE
   BUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUIL
   D_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/self
   gz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.tmp_os-interface.o /tmp/s
   elfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2025: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.os-
   registry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -
   D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-13-generic/arch/x86/
   include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-
   aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-f
   loat -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i58
   6 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare
   -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarc
   h/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer 
   -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign 
   -fwrapv -I/tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv -Wall -
   Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -W
   pointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-
   cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.
   18.14\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BA
   SENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -
   o /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.tmp_os-registr
   y.o /tmp/selfgz5266/NVIDIA-Linux-x8
   6-185.18.14-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-registry.c:15:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2025: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.nv-
   i2c.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KE
   RNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-13-generic/arch/x86/inclu
   de -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return
   -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32
   -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-
   sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-s
   tack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclara
   tion-after-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz5266/NVIDIA-Lin
   ux-x86-185.18.14-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wf
   ormat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror
   -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DM
   ODULE -DNVRM -DNV_VERSION_STRING=\"185.18.14\" -UDEBUG -U_DEBUG -DNDEBUG -DM
   ODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD
   _MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.
   14-pkg1/usr/src/nv/.tmp_nv-i2c.o /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-
   pkg1/usr/src/nv/nv-i2c.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2025: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.nva
   cpi.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KE
   RNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-13-generic/arch/x86/inclu
   de -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno
   -common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregpar
   m=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=gene
   ric -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -fno-asynchr
   onous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/includ
   e/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimiz
   e-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -I/t
   mp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv -Wall -Wimplicit -W
   return-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arit
   h -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -W
   no-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.14\" -UDE
   BUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUIL
   D_STR(nvacpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz5266
   /NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.tmp_nvacpi.o /tmp/selfgz5266/NV
   IDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nvacpi.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2025: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     ld -m elf_i386   -r -o /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr
   /src/nv/nvidia.o /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/
   nv-kernel.o /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/nv.o 
   /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/nv-vm.o /tmp/self
   gz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/os-agp.o /tmp/selfgz5266/N
   VIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/os-interface.o /tmp/selfgz5266/NVI
   DIA-Linux-x86-185.18.14-pkg1/usr/src/nv/os-registry.o /tmp/selfgz5266/NVIDIA
   -Linux-x86-185.18.14-pkg1/usr/src/nv/nv-i2c.o /tmp/selfgz5266/NVIDIA-Linux-x
   86-185.18.14-pkg1/usr/src/nv/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg
   1/usr/src/nv/nvidia.ko;) > /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/u
   sr/src/nv/modules.order
     Building modules, stage 2.
   make -f /usr/src/linux-headers-2.6.28-13-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.28-13-generic/Modu
   le.symvers -I /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/Mod
   ule.symvers  -o /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/M
   odule.symvers -S -K /usr/src/linux-headers-2.6.28-13-generic/Module.markers 
   -M /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/Module.markers
   -w  -s
   WARNING: could not find /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/
   src/nv/.nv-kernel.o.cmd for /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/
   usr/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/.nvi
   dia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D
   __KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-13-generic/arch/x86/i
   nclude -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Ws
   trict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-imp
   licit-function-declaration -O2 -m32 -msoft-float -
   mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtu
   ne=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -fno-
   asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86
   /include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-
   optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwra
   pv -I/tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv -Wall -Wimpl
   icit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpoint
   er-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-
   qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.14
   \" -UDEBUG -U_DEBUG -DNDEBUG  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD
   _STR(nvidia.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -DMODULE -c -o /tm
   p/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/nvidia.mod.o /tmp/se
   lfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/nv/nvidia.mod.c
   In file included from include/linux/bitops.h:17,
                    from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/cpufeature.h:166,
                    from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/incl
   ude/asm/processor.h:16,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nvidia.mod.c:1:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/sr
   c/nv/nvidia.mod.c:1:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
     ld -r -m elf_i386  --build-id -o /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.1
   4-pkg1/usr/src/nv/nvidia.ko /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/
   usr/src/nv/nvidia.o /tmp/selfgz5266/NVIDIA-Linux-x86-185.18.14-pkg1/usr/src/
   nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 No such device
-> Kernel messages:
   [  166.398645] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.4 DST=192.168.2.255
   LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
   [  167.399968] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.4 DST=192.168.2.255
   LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
   [  167.400032] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.4 DST=192.168.2.255
   LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
   [  167.400078] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.4 DST=192.168.2.255
   LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
   [  167.400120] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.4 DST=192.168.2.255
   LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
   [  167.400162] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.4 DST=192.168.2.255
   LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
   [  228.461620] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.2 DST=192.168.2.255
   LEN=247 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=227 
   [  238.468175] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.4 DST=192.168.2.255
   LEN=247 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=227 
   [  300.463234] mtrr: no MTRR for 40000000,10000000 found
   [  338.563057] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.2 DST=192.168.2.255
   LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
   [  338.563150] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.2 DST=192.168.2.255
   LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
   [  340.565696] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.2 DST=192.168.2.255
   LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
   [  340.565762] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.2 DST=192.168.2.255
   LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
   [  341.567073] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.2 DST=192.168.2.255
   LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
   [  341.567137] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.2 DST=192.168.2.255
   LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
   [  341.900066] Inbound IN=eth0 OUT=
   MAC=ff:ff:ff:ff:ff:ff:00:18:39:0d:1e:c0:08:00 SRC=192.168.2.7
   DST=192.168.2.255 LEN=256 TOS=0x00 PREC=0x00 TTL=128 ID=24245 PROTO=UDP
   SPT=138 DPT=138 LEN=236 
   [  342.568457] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.2 DST=192.168.2.255
   LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
   [  342.568518] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.2 DST=192.168.2.255
   LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
   [  354.581571] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.2 DST=192.168.2.255
   LEN=218 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=198 
   [  356.584449] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.2 DST=192.168.2.255
   LEN=218 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=198 
   [  358.587190] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.2 DST=192.168.2.255
   LEN=218 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=198 
   [  360.589945] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.2 DST=192.168.2.255
   LEN=218 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=198 
   [  362.592927] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.2 DST=192.168.2.255
   LEN=218 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=198 
   [  412.644769] Inbound IN=eth0 OUT= MAC= SRC=192.168.2.2 DST=192.168.2.255
   LEN=247 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=227 
   [  547.436219] NVRM: No NVIDIA graphics adapter found!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

Running on macbook santa rosa (3,1), lshw gives:
```

fredlab
    description: Computer
    product: MacBook3,1
    vendor: Apple Inc.
    version: 1.0
    serial: W880276SZ63
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal uuid=9CFE245E-D0C8-BD45-A79F-54EA5FBD3D97
  *-core
       description: Motherboard
       product: Mac-F22788C8
       vendor: Apple Inc.
       physical id: 0
       version: PVT
       serial: 1
       slot: Part Component
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          slot: U2E1
          size: 800MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
        *-cache:0
             description: L2 cache
             physical id: 1
             slot: Unknown
             size: 4MiB
             capacity: 4MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 3
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-cache:0
          description: L1 cache
          physical id: 2
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-cpu:1
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 4
          bus info: cpu@1
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          slot: U2E1
          size: 800MHz
          capacity: 2200MHz
          clock: 200MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-cache:0
             description: L2 cache
             physical id: 5
             slot: Unknown
             size: 4MiB
             capacity: 4MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 7
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-cache:1
          description: L1 cache
          physical id: 6
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-memory
          description: System Memory
          physical id: 8
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: 0x4D342037305436353534455A332D43453620
             vendor: 0xCE00000000000000
             physical id: 0
             serial: 0x44230AD6
             slot: DIMM0
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: 0x4D342037305436353534455A332D43453620
             vendor: 0xCE00000000000000
             physical id: 1
             serial: 0x44230AAA
             slot: DIMM1
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-firmware
          description: BIOS
          vendor: Apple Inc.
          physical id: 10
          version: MB31.88Z.008E.B01.0711151547 (11/15/07)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect acpi ieee1394boot smartbattery netboot
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: BCM4328 802.11a/b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 03
                serial: 00:1e:c2:9e:83:79
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.2.4 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 13
                serial: 00:1e:c2:09:2a:cb
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.2.2 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW323
                vendor: Agere Systems
                physical id: 3
                bus info: pci@0000:04:03.0
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=248 maxlatency=24 mingnt=12 module=ohci1394
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-cdrom
                description: DVD writer
                product: DVD-R   UJ-857E
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: ZF1E
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-ide:1
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: FUJITSU MHY2120B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 0081
                serial: K439T7C2H7S2
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000023f1
              *-volume:0 UNCLAIMED
                   description: EFI GPT partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   capacity: 200MiB
                   capabilities: primary nofs
              *-volume:1
                   description: Primary partition
                   vendor: Mac OS X (journaled)
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 4
                   serial: 1c197d61-245c-54c4-0000-000000147000
                   size: 40GiB
                   capacity: 40GiB
                   capabilities: primary journaled bootable osx hfsplus initialized
                   configuration: boot=osx checked=2008-03-08 23:12:42 created=2008-03-08 14:12:42 filesystem=hfsplus lastmountedby=HFSJ modified=2009-06-12 14:11:01 state=clean
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 59f88eea-d118-41a7-a000-111df1c924eb
                   size: 29GiB
                   capacity: 29GiB
                   capabilities: primary bootable journaled large_files recover ext3 ext2 initialized
                   configuration: created=2008-03-10 23:25:08 filesystem=ext3 modified=2009-06-21 21:11:04 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-06-21 21:11:04 state=mounted
              *-volume:3
                   description: Windows NTFS volume
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   logical name: /media/sda4
                   version: 3.1
                   serial: fa6fca80-264d-6344-82d5-588c792d4cf6
                   size: 19GiB
                   capacity: 20GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-03-09 18:11:39 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-battery
       product: Unknown
       vendor: Unknown
       physical id: 1
       version: Unknown
       serial: Unknown
       slot: Unknown
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f2:11:ab:22:27:19
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```


Still can't believe how in Ubuntu 8.10 the nvidia drivers were installed out of the box without doing anything and in 9.04 I'm living this kinda nightmare.

Thanks for the help!

---

### Post by markbuntu on 2009-06-21
You need to remove the old nvidia driver. You should have done it before upgrading.

---

### Post by fredscripts on 2009-06-22
> **markbuntu said:**
> You need to remove the old nvidia driver. You should have done it before upgrading.

I ran:

```
sudo apt-get remove nvidia*
```

Isn't that enough? I removed almost 190MB of stuff.


Thanks for the help.

---

### Post by sadaruwan12 on 2009-06-22
Do you know the model of you nvidia graphic card ?

---

### Post by Zimmer on 2009-06-22
> Using: nvidia-installer ncurses user interface
WARNING: You do not appear to have an NVIDIA GPU supported by the 185.18.14
         NVIDIA Linux graphics driver installed in this system.  For further
         details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in
         the README available on the Linux driver download page at
         [www.nvidia.com](www.nvidia.com).
According to your computer you DO NOT have an Nvidia card !
> 
*-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0

from your installer log....

---

### Post by fredscripts on 2009-06-22
Wow I thought quite new macbooks had some kind of Nvidia. So how can I know my graphics card? I've read the lshw output but can't find out.


Thanks for the help!

---

### Post by fredscripts on 2009-06-22
I've been searching and I've found out that the graphics card is an **Intel x3100** 

Anyone knows then how to proceed in Ubuntu 9.04?

---

### Post by Zimmer on 2009-06-23
[http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_X3100](http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_X3100)

May be of interest to you, but I am sure if you have a look at the graphics documentation for Ubuntu or search for x3100 on the forum there should be a bit more info.. I will have a look when I am not so busy, just in case I can find it first ;)

[http://ubuntuforums.org/showthread.php?t=1060049&highlight=Intel+x3100](http://ubuntuforums.org/showthread.php?t=1060049&highlight=Intel+x3100)

[http://ubuntuforums.org/showthread.php?t=1075122&highlight=intel+x3100+dri](http://ubuntuforums.org/showthread.php?t=1075122&highlight=intel+x3100+dri)

---

