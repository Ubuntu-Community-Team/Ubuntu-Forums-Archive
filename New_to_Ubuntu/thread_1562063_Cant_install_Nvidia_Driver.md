---
title: "Cant install Nvidia Driver"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by guerrillaMonKey on 2010-08-27
hi everyone i need help with this i been trying so much ways to install the driver of my video card nvidia GeForce4 MX 440 AGP 8X its an old card but the drivers that i get from the driver tool is not the best for me and the one that i get from the nvidia is NVIDIA-Linux-x86-256.44.run i read so much ways to install it but i cant :( i need your help as a newby

i did

sudo gedit /etc/modprobe.d/blacklist.conf

```
blacklist nouveau
blacklist nvidiafb
blacklist rivatv
blacklist rivafb
blacklist vga16fb

but i dont know if i add the files to the black list correctly

i tried 

sudo apt-get --purge remove nvidia-*
sudo apt-get --purge remove xserver-xorg-video-nouveau

the fist one told me the cant not find nvidia-*
the second is telling me that its not installed

i uninstall from the  Synaptic everything about nvidia

and i been trying to install it typing this 

sudo /etc/init.d/gdm stop

that is to get out of the graphic mode and i get this log



nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Aug 27 02:45:34 2010
installer version: 256.44

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
WARNING: The NVIDIA GeForce4 MX 440 with AGP8X GPU installed in this system is
         supported through the NVIDIA 96.43.xx legacy Linux graphics drivers. 
         Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
         information.  The 256.44 NVIDIA Linux graphics driver will ignore this
         GPU.
WARNING: You do not appear to have an NVIDIA GPU supported by the 256.44 NVIDIA
         Linux graphics driver installed in this system.  For further details,
         please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README
         available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).
-> License accepted.
-> Installing NVIDIA driver version 256.44.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.32-24-generic-pae/build'
-> Kernel output path: '/lib/modules/2.6.32-24-generic-pae/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./kernel; make clean'...
-> Building kernel module:
   executing: 'cd ./kernel; make module SYSSRC=/lib/modules/2.6.32-24-generic-p
   ae/build SYSOUT=/lib/modules/2.6.32-24-generic-pae/build'...
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
   mkdir -p /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/.tmp_versions ; rm -
   f /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/.tmp_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz1860/NVIDIA-Linux-x86-256.44/k
   ernel
     cc -Wp,-MD,/tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/.nv.o.d  -nostdi
   nc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr/src
   /linux-headers-2.6.32-24-generic-pae/arch/x86/include -include include/linux
   /autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes
   -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-de
   claration -Wno-format-security -fno-delete-null-pointe
   r-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-s
   tack-boundary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-m
   tune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_A
   S_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables
   -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-fr
   ame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -W
   no-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I
   /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel -Wall -MD -Wsign-compare -Wno
   -cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256
   .44\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BAS
   ENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/sel
   fgz1860/NVIDIA-Linux-x86-256.44/kernel/.tmp_nv.o /tmp/selfgz1860/NVIDIA-Linu
   x-x86-256.44/kernel/nv.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic-pae/scripts/recordm
   count.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/self
   gz1860/NVIDIA-Linux-x86-256.44/kernel/nv.o";
     cc -Wp,-MD,/tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/.nv_gvi.o.d  -no
   stdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr
   /src/linux-headers-2.6.32-24-generic-pae/arch/x86/include -include include/l
   inux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-functi
   on-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32
   -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -m
   arch=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ff
   reestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME
   =1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx
   -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-o
   ptimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -
   fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz1860/N
   VIDIA-Linux-x86-256.44/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-e
   rror -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.44\" -UDEBUG -U_
   DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(
   nv_gvi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz1860/NVIDI
   A-Linux-x86-256.44/kernel/.tmp_nv_gvi.o /tmp/selfgz1860/NVIDIA-Linux-x86-256
   .44/kernel/nv_gvi.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic-pae/scripts/recordm
   count.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/self
   gz1860/NVIDIA-Linux-x86-256.44/kernel/nv_gvi.o";
     cc -Wp,-MD,/tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/.nv-vm.o.d  -nos
   tdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr/
   src/linux-headers-2.6.32-24-generic-pae/arch/x86/include -include include/li
   nux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototy
   pes -Wno-trigraphs -fno-strict-aliasing -fn
   o-common -Werror-implicit-function-declaration -Wno-format-security -fno-del
   ete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-retur
   n -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -maccumulate-outgo
   ing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_C
   FI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronou
   s-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1
   024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-af
   ter-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fc
   onserve-stack -I/tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel -Wall -MD -Ws
   ign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERS
   ION_STRING=\"256.44\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#
   s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidi
   a)"  -c -o /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/.tmp_nv-vm.o /tmp/
   selfgz1860/NVIDIA-Linux-x86-256.44/k
   ernel/nv-vm.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic-pae/scripts/recordm
   count.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/self
   gz1860/NVIDIA-Linux-x86-256.44/kernel/nv-vm.o";
     cc -Wp,-MD,/tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/.os-agp.o.d  -no
   stdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr
   /src/linux-headers-2.6.32-24-generic-pae/arch/x86/include -include include/l
   inux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-functi
   on-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32
   -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -m
   arch=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ff
   reestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME
   =1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx
   -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -f
   no-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-st
   atement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserv
   e-stack -I/tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel -Wall -MD -Wsign-co
   mpare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_ST
   RING=\"256.44\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"
   KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  
   -c -o /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/.tmp_os-agp.o /tmp/self
   gz1860/NVIDIA-Linux-x86-256.44/kernel/os-agp.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic-pae/scripts/recordm
   count.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/self
   gz1860/NVIDIA-Linux-x86-256.44/kernel/os-agp.o";
     cc -Wp,-MD,/tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/.os-interface.o.
   d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  
   -I/usr/src/linux-headers-2.6.32-24-generic-pae/arch/x86/include -include inc
   lude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-
   prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-
   function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O
   2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-bounda
   ry=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generi
   c32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNA
   L_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -
   mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointe
   r -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer
   -sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfg
   z1860/NVIDIA-Linux-x86-256.44/kernel -Wall -MD -Wsign-compare -Wno-cast-qual
   -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.44\" -UDEB
   UG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUIL
   D_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(
   nvidia)"  -c -o /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/.tmp_os-inter
   face.o /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/os-interface.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic-pae/scripts/recordm
   count.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/self
   gz1860/NVIDIA-Linux-x86-256.44/kernel/os-interface.o";
     cc -Wp,-MD,/tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/.os-registry.o.d
    -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I
   /usr/src/linux-headers-2.6.32-24-generic-pae/arch/x86/include -include inclu
   de/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-pr
   ototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fu
   nction-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 
   -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary
   =2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic3
   2 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_A
   S_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables
   -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-fr
   ame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -W
   no-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I
   /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel -Wall -MD -Wsign-compare -Wno
   -cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256
   .44\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BAS
   ENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o
   /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/.tmp_os-registry.o /tmp/selfg
   z1860/NVIDIA-Linux-x86-256.44/kernel/os-registry.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic-pae/scripts/recordm
   count.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/self
   gz1860/NVIDIA-Linux-x86-256.44/kernel/os-registry.o";
     cc -Wp,-MD,/tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/.nv-i2c.o.d  -no
   stdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr
   /src/linux-headers-2.6.32-24-generic-pae/arch/x86/include -include include/l
   inux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-functi
   on-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32
   -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -m
   arch=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ff
   reestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME
   =1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx
   -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-o
   ptimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -f
   no-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz1860/NV
   IDIA-Linux-x86-256.44/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-er
   ror -D__KERNEL__ -DMODULE -DNVRM -DNV_V
   ERSION_STRING=\"256.44\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s
   )=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_STR(n
   vidia)"  -c -o /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/.tmp_nv-i2c.o 
   /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/nv-i2c.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic-pae/scripts/recordm
   count.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/self
   gz1860/NVIDIA-Linux-x86-256.44/kernel/nv-i2c.o";
     cc -Wp,-MD,/tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/.nvacpi.o.d  -no
   stdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr
   /src/linux-headers-2.6.32-24-generic-pae/arch/x86/include -include include/l
   inux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-functi
   on-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32
   -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -m
   arch=i
   586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreesta
   nding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pi
   pe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-
   sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimi
   ze-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-st
   rict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz1860/NVIDIA-
   Linux-x86-256.44/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -
   D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.44\" -UDEBUG -U_DEBUG 
   -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvacpi
   )"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz1860/NVIDIA-Linu
   x-x86-256.44/kernel/.tmp_nvacpi.o /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/ke
   rnel/nvacpi.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic-pae/scripts/recordm
   count.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/self
   gz1860/NVIDIA-Linux-x86-256.44/kernel/nvacpi.o";
     ld -m elf_i386   -r -o /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/nvid
   ia.o /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/nv-kernel.o /tmp/selfgz1
   860/NVIDIA-Linux-x86-256.44/kernel/nv.o /tmp/selfgz1860/NVIDIA-Linux-x86-256
   .44/kernel/nv_gvi.o /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/nv-vm.o /
   tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/os-agp.o /tmp/selfgz1860/NVIDI
   A-Linux-x86-256.44/kernel/os-interface.o /tmp/selfgz1860/NVIDIA-Linux-x86-25
   6.44/kernel/os-registry.o /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/nv-
   i2c.o /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel
   /nvidia.ko;) > /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/modules.order
   make -f /usr/src/linux-headers-2.6.32-24-generic-pae/scripts/Makefile.modpos
   t
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.32-24-generic-pae/
   Module.symvers -I /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/Module.symv
   ers  -o /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/Module.symvers -S -w 
   -s
   WARNING: could not find /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/.nv-k
   ernel.o.cmd for /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/.nvidia.mod.o.d 
   -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/
   usr/src/linux-headers-2.6.32-24-generic-pae/arch/x86/include -include includ
   e/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -
   m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=
   2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32
   -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FR
   AME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-
   mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -
   fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-s
   tatement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconser
   ve-stack -I/tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel -Wall -MD -Wsign-c
   ompare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_S
   TRING=\"256.44\" -UDEBUG -U_DEBUG -DNDEBUG  -D"KBUILD_STR(s)=#s" -D"KBUILD_B
   ASENAME=KBUILD_STR(nvidia.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -DMO
   DULE -c -o /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/nvidia.mod.o /tmp/
   selfgz1860/NVIDIA-Linux-x86-256.44/kernel/nvidia.mod.c
     ld -r -m elf_i386 -T /usr/src/linux-headers-2.6.32-24-generic-pae/scripts/
   module-common.lds --build-id -o /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kern
   el/nvidia.ko /tmp/selfgz1860/NVIDIA-Linux-x86-256.44/kernel/nvidia.o /tmp/se
   lfgz1860/NVIDIA-Linux-x86-256.44/kernel/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb, nvidiafb, or nouveau is present and prevents the NVIDIA kernel
       module from obtaining ownership of the NVIDIA graphics device(s), or
       NVIDIA GPU installed in this system is not supported by this NVIDIA
       Linux graphics driver release.
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './kernel/nvidia.ko': -1
   No such device
-> Kernel messages:
   [   21.148109]   domain 1: span 0-1 level MC
   [   21.148113]    groups: 0-1 (cpu_power = 1178)
   [   21.148123] CPU1 attaching sched-domain:
   [   21.148127]  domain 0: span 0-1 level SIBLING
   [   21.148131]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
   [   21.148140]   domain 1: span 0-1 level MC
   [   21.148144]    groups: 0-1 (cpu_power = 1178)
   [   21.968027] eth0: no IPv6 routers present
   [   84.997297] operapluginwrap[1379]: segfault at 0 ip (null) sp bf92562c
   error 4 in libXext.so.6.4.0[110000+e000]
   [   85.022127] operapluginwrap[1380]: segfault at 0 ip (null) sp bfb837dc
   error 4 in libICE.so.6.3.0[110000+15000]
   [   85.049697] operapluginwrap[1381]: segfault at 0 ip (null) sp bfc744dc
   error 4 in libSM.so.6.0.1[110000+7000]
   [   85.134913] operapluginwrap[1383]: segfault at 0 ip (null) sp bfef200c
   error 4 in libX11.so.6.3.0[110000+119000]
   [   85.472926] operapluginwrap[1386]: segfault at 0 ip (null) sp bfa4b13c
   error 4 in libuuid.so.1.3.0[110000+3000]
   [   85.488247] operapluginwrap[1387]: segfault at 0 ip (null) sp bffadafc
   error 4 in libICE.so.6.3.0[110000+15000]
   [   85.500777] operapluginwrap[1388]: segfault at 0 ip (null) sp bfe61f4c
   error 4 in libstdc++.so.6.0.13[110000+e9000]
   [   85.513482] operapluginwrap[1389]: segfault at 0 ip (null) sp bfcac9dc
   error 4 in libX11.so.6.3.0[110000+119000]
   [  349.844165] opera[1747]: segfault at 78 ip 0805abeb sp bf86d070 error 4
   in opera[8048000+eea000]
   [  462.646917] nvidia: module license 'NVIDIA' taints kernel.
   [  462.646923] Disabling lock debugging due to kernel taint
   [  463.830094] NVRM: The NVIDIA GeForce4 MX 440 with AGP8X GPU installed in
   this system is
   [  463.830098] NVRM:  supported through the NVIDIA 96.43.xx Legacy drivers.
   Please
   [  463.830100] NVRM:  visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
   [  463.830101] NVRM:  information.  The 256.44 NVIDIA driver will ignore
   [  463.830103] NVRM:  this GPU.  Continuing probe...
   [  463.830119] NVRM: No NVIDIA graphics adapter found!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).


```

as i say im really newby with ubuntu this is my second day with it and trying to install the driver hope you can help and plz i need you to take me by the hand step by step 


Thank you everyone.

---

### Post by vitothegreat on 2010-08-27
Assuming you have already cleaned your system of anything related to nvidia:
download latest driver;
ctrl+alt+f1;
sudo service gdm stop;
cd <driver_location>;
sudo sh <driver_name>.run;
follow the on-screen instructions;
when installation is finished "sudo service gdm start".

I guess you'd like to tweak some settings later so installing nvidia-settings is probably a good idea as well.

---

### Post by jonnywombat on 2010-08-27
just fyi but the "256" driver doesn't support your card

It is only compatible with 6000 series cards and above.

just basic drivers (version 96) within the software centre should offer all the functionality your card can handle.

---

### Post by guerrillaMonKey on 2010-08-27
> **jonnywombat said:**
> just fyi but the "256" driver doesn't support your card

It is only compatible with 6000 series cards and above.

just basic drivers (version 96) within the software centre should offer all the functionality your card can handle.

I think thats the reason why tyvm Jonny and vito i will instale the right driver ;D

---

