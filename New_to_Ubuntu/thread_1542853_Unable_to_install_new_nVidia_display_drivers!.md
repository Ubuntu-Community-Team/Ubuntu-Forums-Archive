---
title: "Unable to install new nVidia display drivers!"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by 7mm on 2010-07-31
**I've just downloaded new nVidia drivers for my GeForce 9400GT 1GB. When I tried to install it in command prompt, it shows as not proper command. Please help installing these drivers, may be the better / proper way to doing it. Thanx.**

---

### Post by limestone on 2010-07-31
what package format is it? .bin / .run?
frist you need to make it executable with chmod then you probably need to run it with sudo
```
chmod +x driver.bin
sudo ./driver.bin
```

---

### Post by 7mm on 2010-07-31
**Ok, it's [.run] file!**

---

### Post by limestone on 2010-07-31
> **7mm said:**
> **Ok, it's [.run] file!**

Then do the same as my first answer and change .bin to .run

---

### Post by 7mm on 2010-07-31
**Thank you "pont.andersson" for your help. Sure it started a process smoothly, completed & then died screaming something about kernel not the same OR some more reasons I couldn't understand. So I may need more help from here, I'm posting a log created after the installation process was done unsuccessfully!**



> nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Jul 31 19:52:22 2010
installer version: 256.35

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
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 256.35.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation 
   anyway? (Answer: Yes)
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.32-24-generic/build'
-> Kernel output path: '/lib/modules/2.6.32-24-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./kernel; make clean'...
-> Building kernel module:
   executing: 'cd ./kernel; make module SYSSRC=/lib/modules/2.6.32-24-generic/b
   uild SYSOUT=/lib/modules/2.6.32-24-generic/build'...
   NVIDIA: calling KBUILD...
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/.tmp_versions ; rm -
   f /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/.tmp_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz1403/NVIDIA-Linux-x86-256.35/k
   ernel
     cc -Wp,-MD,/tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/.nv.o.d  -nostdi
   nc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr/src
   /linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/aut
   oconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wn
   o-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-decla
   ration -Wno-format-security -fno-delete-null-pointer-ch
   ecks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack
   -boundary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune
   =generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CF
   I_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mn
   o-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame
   -pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-
   pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tm
   p/selfgz1403/NVIDIA-Linux-x86-256.35/kernel -Wall -MD -Wsign-compare -Wno-ca
   st-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.35
   \" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENA
   ME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz
   1403/NVIDIA-Linux-x86-256.35/kernel/.tmp_nv.o /tmp/selfgz1403/NVIDIA-Linux-x
   86-256.35/kernel/nv.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz14
   03/NVIDIA-Linux-x86-256.35/kernel/nv.o";
     cc -Wp,-MD,/tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/.nv_gvi.o.d  -no
   stdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr
   /src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux
   /autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes
   -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-de
   claration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -mso
   ft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march
   =i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffrees
   tanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -
   pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mn
   o-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-opti
   mize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-
   strict-o
   verflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz1403/NVIDIA-Linux-
   x86-256.35/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KER
   NEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.35\" -UDEBUG -U_DEBUG -DNDEB
   UG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_gvi)"  -D
   "KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz1403/NVIDIA-Linux-x86-
   256.35/kernel/.tmp_nv_gvi.o /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/n
   v_gvi.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz14
   03/NVIDIA-Linux-x86-256.35/kernel/nv_gvi.o";
     cc -Wp,-MD,/tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/.nv-vm.o.d  -nos
   tdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr/
   src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/
   autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes 
   -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-imp
   licit-function-declaration -Wno-format-security -fno-delete-null-pointer-che
   cks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-
   boundary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=
   generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI
   _SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno
   -sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-
   pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-p
   ointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp
   /selfgz1403/NVIDIA-Linux-x86-256.35/kernel -Wall -MD -Wsign-compare -Wno-cas
   t-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.35\
   " -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAM
   E=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/self
   gz1403/NVIDIA-Linux-x86-256.35/kernel/.tmp_nv-vm.o /tmp/selfgz1403/NVIDIA-Li
   nux-x86-256.35/kernel/nv-vm.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz14
   03/NVIDIA-Linux-x86-256.35/kernel/nv-vm.o";
     cc -Wp,-MD,/tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/.os-agp.o.d  -no
   stdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr
   /src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux
   /autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes
   -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-de
   claration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -mso
   ft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march
   =i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffrees
   tanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -
   pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mn
   o-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-o
   ptimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -f
   no-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz1403/NV
   IDIA-Linux-x86-256.35/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-er
   ror -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.35\" -UDEBUG -U_D
   EBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(o
   s_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz1403/NVIDIA
   -Linux-x86-256.35/kernel/.tmp_os-agp.o /tmp/selfgz1403/NVIDIA-Linux-x86-256.
   35/kernel/os-agp.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz14
   03/NVIDIA-Linux-x86-256.35/kernel/os-agp.o";
     cc -Wp,-MD,/tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/.os-interface.o.
   d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  
   -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include
   /linux/autoconf.h -Iubuntu/include  -D__KERNEL__
    -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-
   common -Werror-implicit-function-declaration -Wno-format-security -fno-delet
   e-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return 
   -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -maccumulate-outgoin
   g-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI
   =1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-
   unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=102
   4 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-afte
   r-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fcon
   serve-stack -I/tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel -Wall -MD -Wsig
   n-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSIO
   N_STRING=\"256.35\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s"
   -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(n
   vidia)"  -c -o /tmp/selfgz1403/NVID
   IA-Linux-x86-256.35/kernel/.tmp_os-interface.o /tmp/selfgz1403/NVIDIA-Linux-
   x86-256.35/kernel/os-interface.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz14
   03/NVIDIA-Linux-x86-256.35/kernel/os-interface.o";
     cc -Wp,-MD,/tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/.os-registry.o.d
    -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/l
   inux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-functi
   on-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32
   -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -m
   arch=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ff
   reestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME
   =1 -pipe -Wno-sign-compare
    -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wfr
   ame-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg
   -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dw
   arf2-cfi-asm -fconserve-stack -I/tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kern
   el -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE 
   -DNVRM -DNV_VERSION_STRING=\"256.35\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D
   "KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MO
   DNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/ker
   nel/.tmp_os-registry.o /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/os-reg
   istry.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz14
   03/NVIDIA-Linux-x86-256.35/kernel/os-registry.o";
     cc -Wp,-MD,/tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/.nv-i2c.o.d  -no
   stdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr
   /src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux
   /autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes
   -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-de
   claration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -mso
   ft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march
   =i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffrees
   tanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -
   pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mn
   o-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-opti
   mize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-
   strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz1403/NVIDI
   A-Linux-x86-256.35/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error
   -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.35\" -UDEBUG -U_DEBUG
   -DNDEBUG  
   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBU
   ILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz1403/NVIDIA-Linux-x86-256.
   35/kernel/.tmp_nv-i2c.o /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/nv-i2
   c.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz14
   03/NVIDIA-Linux-x86-256.35/kernel/nv-i2c.o";
     cc -Wp,-MD,/tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/.nvacpi.o.d  -no
   stdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr
   /src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux
   /autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes
   -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-de
   claration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -mso
   ft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march
   =i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=gen
   eric32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SI
   GNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-ss
   e -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-poi
   nter -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-poin
   ter-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/se
   lfgz1403/NVIDIA-Linux-x86-256.35/kernel -Wall -MD -Wsign-compare -Wno-cast-q
   ual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.35\" -
   UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=K
   BUILD_STR(nvacpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz
   1403/NVIDIA-Linux-x86-256.35/kernel/.tmp_nvacpi.o /tmp/selfgz1403/NVIDIA-Lin
   ux-x86-256.35/kernel/nvacpi.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz14
   03/NVIDIA-Linux-x86-256.35/kernel/nvacpi.o";
     ld -m elf_i386   -r -o /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/nvid
   ia.o /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/nv-kernel.o /tmp/selfgz1
   403/NVIDIA-Linux-x86-256.35/kernel/nv.o /tmp/selfgz1403/NVIDIA-Linux-x86-256
   .35/kernel/nv_gvi.o /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/nv-vm.o /
   tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/os-agp.o /tmp/selfgz1403/NVIDI
   A-Linux-x86-256.35/kernel/os-interface.o /tmp/selfgz1403/NVIDIA-Linux-x86-25
   6.35/kernel/os-registry.o /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/nv-
   i2c.o /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel
   /nvidia.ko;) > /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/modules.order
   make -f /usr/src/linux-headers-2.6.32-24-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.32-24-generic/Modu
   le.symvers -I /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/Module.symvers 
   -o /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/Module.symvers -S -w  -s
   WARNING: could not find /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/.nv-k
   ernel.o.cmd for /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/.nvidia.mod.o.d 
   -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/
   usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/li
   nux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototy
   pes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-functio
   n-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 
   -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -m
   arch=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ff
   reestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME
   =1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx
   -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-o
   ptimize-sibling-calls -pg -Wdeclaration-after-s
   tatement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconser
   ve-stack -I/tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel -Wall -MD -Wsign-c
   ompare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_S
   TRING=\"256.35\" -UDEBUG -U_DEBUG -DNDEBUG  -D"KBUILD_STR(s)=#s" -D"KBUILD_B
   ASENAME=KBUILD_STR(nvidia.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -DMO
   DULE -c -o /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/nvidia.mod.o /tmp/
   selfgz1403/NVIDIA-Linux-x86-256.35/kernel/nvidia.mod.c
     ld -r -m elf_i386 -T /usr/src/linux-headers-2.6.32-24-generic/scripts/modu
   le-common.lds --build-id -o /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/n
   vidia.ko /tmp/selfgz1403/NVIDIA-Linux-x86-256.35/kernel/nvidia.o /tmp/selfgz
   1403/NVIDIA-Linux-x86-256.35/kernel/nvidia.mod.o
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
-> Kernel module load error: insmod: error inserting './kernel/nvidia.ko': -1
   No such device
-> Kernel messages:
   [   12.120206] NVRM: No NVIDIA graphics adapter probed!
   [   12.154238] Console: switching to colour frame buffer device 200x56
   [   12.155036] [drm] nouveau 0000:02:00.0: 0xC200: parsing output script 1
   [   12.155048] [drm] nouveau 0000:02:00.0: 0xC20E: parsing output script 2
   [   12.155080] [drm] nouveau 0000:02:00.0: 0xBEEC: parsing clock script 0
   [   12.155389] [drm] nouveau 0000:02:00.0: 0xB7F6: parsing clock script 1
   [   16.740474] ppdev: user-space parallel port driver
   [   16.911800] CPU0 attaching NULL sched-domain.
   [   16.911805] CPU1 attaching NULL sched-domain.
   [   16.932077] CPU0 attaching sched-domain:
   [   16.932080]  domain 0: span 0-1 level MC
   [   16.932082]   groups: 0 1
   [   16.932087] CPU1 attaching sched-domain:
   [   16.932088]  domain 0: span 0-1 level MC
   [   16.932090]   groups: 1 0
   [   20.552010] eth0: no IPv6 routers present
   [  112.221412] NVRM: The NVIDIA probe routine was not called for 1
   device(s).
   [  112.221423] NVRM: This can occur when a driver such as nouveau, rivafb,
   [  112.221427] NVRM: nvidiafb, or rivatv was loaded and obtained ownership
   of
   [  112.221430] NVRM: the NVIDIA device(s).
   [  112.221439] NVRM: Try unloading the conflicting kernel module (and/or
   [  112.221442] NVRM: reconfigure your kernel without the conflicting
   [  112.221444] NVRM: driver(s)), then try loading the NVIDIA kernel module
   [  112.221447] NVRM: again.
   [  112.221452] NVRM: No NVIDIA graphics adapter probed!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by limestone on 2010-07-31
Ye. it seems like the kernel missing the module nvidia.ko and the kernel config is invalid.
I only did this install once myself and everything worked but I think you'll need to edit your kernel conf and add the nvidia.ko module.. I'm sorry I can't help you further more. :/

Btw.. Did Ubuntu not suggest a driver in jockey (a.k.a Hardware drivers)?

---

### Post by ratcheer on 2010-07-31
First, make sure all three parts of the kernel you are using are installed.  E.g., on my system, they are linux-image-2.6.32-24-generic, linux-headers-2.6.32-24, and linux-headers-2.6.32-24-generic. If all are not installed, remedy that, first.

1) If an nVidia driver shows as installed in Hardware Drivers (jockey) applet, remove it and reboot.

2) Do "Ctrl-Alt-F1" to get to a system console. This is not a normal terminal window, but a black text screen.

3) sudo service gdm stop

4) cd to the directory where the .run file is.

5) sudo sh ./the_run _filename

6) When it asks if you want to autoconfigure xorg, select Yes

7) sudo reboot

This is the correct procedure and it should work. If it does not, something else is wrong with your system.

Tim

---

### Post by 7mm on 2010-08-04
[B]Thank you "ratcheer" for your support here. Though I tried your way a bit late with same result as previous attempt. after executing command as *sudo sh ./NVIDIA-Linux-x86-256.35.run,* it returned with error as > The distribution-provided pre-install script failed. Continue anyway?
Though, after hitting yes, it completed some kernel process to 100% & the died just as last time. Same thing happ'n to the previous version of drivers as well, thought it's a bad driver file but now it's something more which is needed. Please help![/B]

---

### Post by RiceMonster on 2010-08-04
Why not just enable the restricted driver? This way you will not have to reinstall the driver at each kernel update.

---

### Post by ratcheer on 2010-08-04
I have seen that before, but I don't remember how I worked my way out of it. Did you see any kind of error message prior to that one? Can you find any sort of log file from the running of the installation script?

Tim

---

### Post by ratcheer on 2010-08-04
According to your previous post, there should be a log file at '/var/log/nvidia-installer.log'.

Also, another question. When you booted the system at step one of my instructions, did it come up with the nouveau driver or the low-res VGA driver?

An alternate way you might try installing is to add the x-swat ppa to your software sources, then update whatever software installer you use (e.g., apt-get, aptitude), then see if you can install the driver via the Hardware Drivers applet, where it would be called the current driver. I have started doing this as opposed to manual installation, because of all the problems with manual installation since Lucid.

You can find instructions to load the ppa at:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Tim

---

### Post by 7mm on 2010-08-04
[B]Hi there "RiceMonster", thanx for the effort. Yes, I've tried the restricted drivers, yet being a Windows user, I always stayed up-to-date with my softwares (including drivers). Never miss a chance to update my drivers, then why not in linux, why use way outdated versions?

For "ratcheer" question, yes I already posted that nvidia-installer.log file as quote. I didn't get any instructions about low-res VGA drivers too.[/B]

---

### Post by nickopen on 2010-08-08
Looking at the log, it seems you are having the same problem as I am. The Nouveau drivers won't unload, so you can't install the NVIDIA ones. See my post here: 
[http://ubuntuforums.org/showpost.php?p=9691650&postcount=14](http://ubuntuforums.org/showpost.php?p=9691650&postcount=14)

---

### Post by 7mm on 2010-09-03
**Sorry I couldn't post for the last few weeks, just got busy with real life. So, I had a success with the latest drivers downloaded on 31st August, version 256.53. This one just worked very well with special effects on. Thank you everyone for helping & spending valuable time for my problem. Hope for the further support (If I need one) in the future, CHEERS!**

---

