---
title: "NVIDIA driver update"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by etiennechausse on 2010-07-03
Hi, this is the third time i upgrade my ubuntu and every single time i have to manually update my NVIDIA driver and every single time I have to google for about an hour on how to update/install/reinstall

Is there a way to do an automatic update on the driver because evrytime i have to install it to be able to run games as HoN, use compiz or the Docky

Remember I am the biggest noob ever so step by step would be great XD

thanks

I don't know if this can be usefull but my graphic card is a NVIDIA Geforce 9600 gt

---

### Post by wojox on 2010-07-03
Can't you go into Hardware Drivers and activate you driver?

---

### Post by etiennechausse on 2010-07-03
Well whenever i open it, it says No proprietary drivers are in use on this system

---

### Post by philinux on 2010-07-03
> **etiennechausse said:**
> Well whenever i open it, it says No proprietary drivers are in use on this system

Does it offer to activate any? Is this a clean install?

If so update using update manager and try the hardware drivers again.

---

### Post by etiennechausse on 2010-07-03
> **philinux said:**
> Does it offer to activate any? Is this a clean install?

If so update using update manager and try the hardware drivers again.

Well I had Ubuntu 9.10 before and hadn't used ubuntu for a while so i did the partial upgrade in the update manager

Now if i check, it says my system is up to date.

---

### Post by lkjoel on 2010-07-03
> **etiennechausse said:**
> Hi, this is the third time i upgrade my ubuntu and every single time i have to manually update my NVIDIA driver and every single time I have to google for about an hour on how to update/install/reinstall

Is there a way to do an automatic update on the driver because evrytime i have to install it to be able to run games as HoN, use compiz or the Docky

Remember I am the biggest noob ever so step by step would be great XD

thanks

I don't know if this can be usefull but my graphic card is a NVIDIA Geforce 9600 gt
Is this before your NVIDIA install thread?
Because it looks like you did download it, and you just need to run it.

---

### Post by etiennechausse on 2010-07-03
No i still haven't installed the driver. The thing is it worked perfectly until I upgraded Ubuntu to 10.04. Docky, compiz and HoN stopped working

I have been trying for about an hour to install the NVIDIA driver but it hasn't taken me this much time to uninstal reinstall before

I have purged NVIDIA from my comp but the install isn't working 
when i run the package as root it asks me to stop x
when i stop gdm it doesn't recognize the package

I really don't know what to do :(

---

### Post by stderr on 2010-07-03
So I take it you had previously installing the proprietary NVIDIA driver frmo NVIDIA's website, and now your kernel has been updated and you want to reinstall it?

If that's the case you don't need to reinstall the whole driver, just the kernerl module (IF you have the same nvidia .run file you used to install last time). You can do this by passing the parameter **--kernel-module-only** to it. 

What do you mean by "it doesn't recognise the package"?

---

### Post by etiennechausse on 2010-07-03
> **stderr said:**
> So I take it you had previously installing the proprietary NVIDIA driver frmo NVIDIA's website, and now your kernel has been updated and you want to reinstall it?

If that's the case you don't need to reinstall the whole driver, just the kernerl module (IF you have the same nvidia .run file you used to install last time). You can do this by passing the parameter **--kernel-module-only** to it. 

What do you mean by "it doesn't recognise the package"?

Actually I tried to do as you said but there seems to be an error with the kernel. I have also tried to install the latest driver and it also doesn't work.

since i cant attach the nvidia installer log i will copy/paste it below
I am kinda desperate right now... 

(Note that i have tried the same thing using the 185.18.36 driver pkg)
_______________________________________________________
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Jul  3 15:37:12 2010
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
-> There appears to already be a driver installed on your system (version: 185.
   18.36).  As part of installing this driver (version: 256.35), the existing d
   river will be uninstalled.  Are you sure you want to continue? ('no' will ab
   ort installation) (Answer: Yes)
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/usr/src/linux'
-> Kernel output path: '/usr/src/linux'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./kernel; make clean'...
-> Building kernel module:
   executing: 'cd ./kernel; make module SYSSRC=/usr/src/linux SYSOUT=/usr/src/l
   inux'...
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
   mkdir -p /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/.tmp_versions ; rm -
   f /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/.tmp_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz3485/NVIDIA-Linux-x86-256.35/k
   ernel
     cc -Wp,-MD,/tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/.nv.o.d  -nostdi
   nc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr/src
   /linux-headers-2.6.31-17-generic-pae/arch/x86/include -include include/linux
   /autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes
   -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-de
   claration -Wno-format-security -fno-delete-null-pointe
   r-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-s
   tack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestandi
   ng -fstack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asyn
   chronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger
   -than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration
   -after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm 
   -I/tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel -Wall -MD -Wsign-compare -W
   no-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"2
   56.35\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_B
   ASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/s
   elfgz3485/NVIDIA-Linux-x86-256.35/kernel/.tmp_nv.o /tmp/selfgz3485/NVIDIA-Li
   nux-x86-256.35/kernel/nv.c
     cc -Wp,-MD,/tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/.nv_gvi.o.d  -no
   stdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr
   /src/linux-headers-2.6.31-17-generic-pae/arch/x86/include -include include/l
   inux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-functi
   on-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32
   -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -m
   arch=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-protect
   or -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-ta
   bles -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-om
   it-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -
   Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/tmp/selfgz3485/
   NVIDIA-Linux-x86-256.35/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-
   error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.35\" -UDEBUG -U
   _DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR
   (nv_gvi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvid
   ia)"  -c -o /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/.tmp_nv_gvi.o /tm
   p/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/nv_gvi.c
     cc -Wp,-MD,/tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/.nv-vm.o.d  -nos
   tdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr/
   src/linux-headers-2.6.31-17-generic-pae/arch/x86/include -include include/li
   nux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototy
   pes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-functio
   n-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 
   -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -m
   arch=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-protect
   or -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-ta
   bles -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-om
   it-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -
   Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -
   I/tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel -Wall -MD -Wsign-compare -Wn
   o-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"25
   6.35\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BA
   SENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp
   /selfgz3485/NVIDIA-Linux-x86-256.35/kernel/.tmp_nv-vm.o /tmp/selfgz3485/NVID
   IA-Linux-x86-256.35/kernel/nv-vm.c
     cc -Wp,-MD,/tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/.os-agp.o.d  -no
   stdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr
   /src/linux-headers-2.6.31-17-generic-pae/arch/x86/include -include include/l
   inux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-functi
   on-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32
   -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -m
   arch=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-protect
   or -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-ta
   bles -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-om
   it-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -
   Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/tmp/selfgz3485/
   NVIDIA-Linux-x86-256.35/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-
   error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.35\" -UDEBUG -U
   _DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR
   (os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz3485/NVID
   IA-Linux-x86-256.35/kernel/.tmp_os-agp.o /tmp/selfgz3485/NVIDIA-Linux-x86-25
   6.35/kernel/os-agp.c
     cc -Wp,-MD,/tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/.os-interface.o.
   d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  
   -I/usr/src/linux-headers-2.6.31-17-generic-pae/arch/x86/include -include inc
   lude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-
   prototypes -Wno
   -trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declar
   ation -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-f
   loat -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i58
   6 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-protector -fsta
   ck-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mn
   o-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame
   -pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-poin
   ter-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/tmp/selfgz3485/NVIDIA-L
   inux-x86-256.35/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D
   __KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.35\" -UDEBUG -U_DEBUG -
   DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_inte
   rface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz3485/NVIDIA
   -Linux-x86-256.35/kernel/.tmp_os-interface.o /tmp/selfgz3485/NVIDIA-Linux-x8
   6-256.35/kernel/os-interface.c
     cc -Wp,-MD,/tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/.os-registry.o.d
    -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I
   /usr/src/linux-headers-2.6.31-17-generic-pae/arch/x86/include -include inclu
   de/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-pr
   ototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fu
   nction-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 
   -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary
   =2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-pr
   otector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwi
   nd-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -f
   no-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statem
   ent -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/tmp/selfgz
   3485/NVIDIA-Linux-x86-256.35/kernel -Wall -MD -Wsign-compare -Wno-cast-qual 
   -Wno-error -D__KERNEL__ -DMODULE -DNVRM 
   -DNV_VERSION_STRING=\"256.35\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD
   _STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME=K
   BUILD_STR(nvidia)"  -c -o /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/.tm
   p_os-registry.o /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/os-registry.c
     cc -Wp,-MD,/tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/.nv-i2c.o.d  -no
   stdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr
   /src/linux-headers-2.6.31-17-generic-pae/arch/x86/include -include include/l
   inux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-functi
   on-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32
   -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -m
   arch=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-protect
   or -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-ta
   bles -mno-sse -mno-mmx -mno-sse2 -
   mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sib
   ling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overf
   low -fno-dwarf2-cfi-asm -I/tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel -Wa
   ll -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM
   -DNV_VERSION_STRING=\"256.35\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD
   _STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD
   _STR(nvidia)"  -c -o /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/.tmp_nv-
   i2c.o /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/nv-i2c.c
     cc -Wp,-MD,/tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/.nvacpi.o.d  -no
   stdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr
   /src/linux-headers-2.6.31-17-generic-pae/arch/x86/include -include include/l
   inux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-functi
   on-declaration -Wno-format-security -fno-delete-n
   ull-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mp
   referred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -f
   freestanding -fstack-protector -fstack-protector-all -pipe -Wno-sign-compare
   -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wfra
   me-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wde
   claration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2
   -cfi-asm -I/tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel -Wall -MD -Wsign-c
   ompare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_S
   TRING=\"256.35\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D
   "KBUILD_BASENAME=KBUILD_STR(nvacpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" 
   -c -o /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/.tmp_nvacpi.o /tmp/self
   gz3485/NVIDIA-Linux-x86-256.35/kernel/nvacpi.c
     ld -m elf_i386   -r -o /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/nvid
   ia.o /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/nv-kernel.o /tmp/selfgz3
   485/NVIDIA-Linux-x86-256.35/kernel/nv.o /tmp/selfgz3485/NVIDIA-Linux-x86-256
   .35/kernel/nv_gvi.o /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/nv-vm.o /
   tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/os-agp.o /tmp/selfgz3485/NVIDI
   A-Linux-x86-256.35/kernel/os-interface.o /tmp/selfgz3485/NVIDIA-Linux-x86-25
   6.35/kernel/os-registry.o /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/nv-
   i2c.o /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel
   /nvidia.ko;) > /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/modules.order
   make -f /usr/src/linux-headers-2.6.31-17-generic-pae/scripts/Makefile.modpos
   t
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.31-17-generic-pae/
   Module.symvers -I /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/Module.symv
   ers  -o /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/Module.symvers -S -K 
   /usr/src/linux-headers-2.6.31-17-generic-pae/Module.markers -M /tmp/selfgz34
   85/NVIDIA-Linux-x86-256.35/kernel/
   Module.markers -w  -s
   WARNING: could not find /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/.nv-k
   ernel.o.cmd for /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/.nvidia.mod.o.d 
   -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/
   usr/src/linux-headers-2.6.31-17-generic-pae/arch/x86/include -include includ
   e/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -
   m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=
   2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-pro
   tector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwin
   d-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fn
   o-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-stateme
   nt -Wno-pointe
   r-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/tmp/selfgz3485/NVIDIA-Lin
   ux-x86-256.35/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__
   KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.35\" -UDEBUG -U_DEBUG -DN
   DEBUG  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia.mod)"  -D"K
   BUILD_MODNAME=KBUILD_STR(nvidia)"  -DMODULE -c -o /tmp/selfgz3485/NVIDIA-Lin
   ux-x86-256.35/kernel/nvidia.mod.o /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/ke
   rnel/nvidia.mod.c
     ld -r -m elf_i386  --build-id -o /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/k
   ernel/nvidia.ko /tmp/selfgz3485/NVIDIA-Linux-x86-256.35/kernel/nvidia.o /tmp
   /selfgz3485/NVIDIA-Linux-x86-256.35/kernel/nvidia.mod.o
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
   Invalid module format
-> Kernel messages:
   [   31.917189] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector
   without authentication
   [   31.917197] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 3a 63 ba 00 00 02
   00
   [   31.917207] end_request: I/O error, dev sr0, sector 15306472
   [   31.917211] Buffer I/O error on device sr0, logical block 3826618
   [   31.917215] Buffer I/O error on device sr0, logical block 3826619
   [   31.962085] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK
   driverbyte=DRIVER_SENSE
   [   31.962090] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
   [   31.962095] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector
   without authentication
   [   31.962102] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 3a 63 ba 00 00 02
   00
   [   31.962111] end_request: I/O error, dev sr0, sector 15306472
   [   31.962116] Buffer I/O error on device sr0, logical block 3826618
   [   31.962120] Buffer I/O error on device sr0, logical block 3826619
   [   32.873830] UDF-fs: Partition marked readonly; forcing readonly mount
   [   32.899295] UDF-fs INFO UDF: Mounting volume
   'CURIOUS_CASE_BEN_BUTTON_DOM', timestamp 2009/03/18 04:51 (1f10)
   [   34.072019] eth0: no IPv6 routers present
   [   35.270238] iwlagn 0000:02:00.0: RF_KILL bit toggled to disable radio.
   [   35.270762] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on
   isa0060/serio0).
   [   35.270765] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
   [   35.276522] atkbd.c: Unknown key released (translated set 2, code 0x94 on
   isa0060/serio0).
   [   35.276525] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
   [  199.146170] CE: hpet increasing min_delta_ns to 15000 nsec
   [  199.146283] CE: hpet increasing min_delta_ns to 22500 nsec
   [  506.298597] CE: hpet increasing min_delta_ns to 33750 nsec
   [  620.978237] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing
   fifo 2
   [  730.041157] nvidia: disagrees about version of symbol module_layout
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by stderr on 2010-07-03
Could you try the following:

1) Visit the NVIDIA support website and download the latest NVIDIA driver for Linux. Stick it somewhere like your home directory.

2) Download the headers for your kernel version:

```
sudo apt-get install linux-headers-`uname -r`
```

3) Log out, switch to tty1 (Ctrl+Alt+F1), log in, and run the installer file you downloaded as root (i.e. with sudo), with no parameters.

---

### Post by wojox on 2010-07-03
Manually installing the Nvidia driver has changed a bit with 10.04. Try this to do a [Manual Install]("http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx")

---

### Post by etiennechausse on 2010-07-04
I have tried this step by step manual and it didn't work. Yhe log i posted previously was the one obtained once i did it.

stderr I'll try what you said, thanks 
and i'll give you the update asap

---

### Post by etiennechausse on 2010-07-04
> **stderr said:**
> Could you try the following:

1) Visit the NVIDIA support website and download the latest NVIDIA driver for Linux. Stick it somewhere like your home directory.

2) Download the headers for your kernel version:

```
sudo apt-get install linux-headers-`uname -r`
```

3) Log out, switch to tty1 (Ctrl+Alt+F1), log in, and run the installer file you downloaded as root (i.e. with sudo), with no parameters.

Still not working :(

i'm loosing hope here... Is there a way to quickly overwrite all ubuntu. I have nothing of worth on it as I am dualbooting.

without a CD if possible :)

---

### Post by stderr on 2010-07-04
Sorry to hear it's still not working out! 

What exactly goes wrong during the steps I gave you? I'm assuming from your response that the driver appears to install correctly, but after a reboot you still don't have X? Any error messages you get, etc, and a description of what happens when you boot the box would be of help. E.g. do you get the "low graphics" popup message before the graphical login, etc? 

With regard to your question, sure, but the easiest way is to burn an Ubuntu CD and start over. Given that you'd be installing Ubuntu after Windows, you don't need to worry about overwriting the boot sector, you should still have the ability to boot into your Windows partition afterwards. I would note, however, that there's no *absolute guarantee* that graphics will automagically work again without further intervention, although we would all hope so(!), and you may want to hold back a bit for some more responses before attempting a reinstall just for a graphics driver issue.

Just so we know what we're dealing with, what graphics card do you have?

If you're not sure, the following command should tell us:

```
lspci | grep -i nvidia
```

---

### Post by lkjoel on 2010-07-05
> **etiennechausse said:**
> Still not working :(

i'm loosing hope here... Is there a way to quickly overwrite all ubuntu. I have nothing of worth on it as I am dualbooting.

without a CD if possible :)
Yes there is a way, by the synaptic package manager.
But try this first:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by lidex on 2010-07-07
> **etiennechausse said:**
> Still not working :(

i'm loosing hope here... Is there a way to quickly overwrite all ubuntu. I have nothing of worth on it as I am dualbooting.

without a CD if possible :)
Did you try this:
```
sudo nvidia-xconfig
```
Then rebooting

---

### Post by etiennechausse on 2010-07-07
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

lkjoel, This upgraded 1 thing or 2 but the nvidia driver stayed as it was
stderr, my nvidia card is a 9600M GT

lidex, whenever i try to sudo nvidia-xconfig

it gives me this message: 

WARNING: Unable to locate/open X configuration file.
New X configuration file written to 'etc/x11/xorg.conf'

I reckon the problem might be here

---

### Post by lidex on 2010-07-07
That just means that there was no xorg.conf, which is default behavior. It creates one for you but you have to reboot for it to take effect. Then I would try enabling desktop effects.

---

### Post by lkjoel on 2010-07-07
> **etiennechausse said:**
> sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

lkjoel, This upgraded 1 thing or 2 but the nvidia driver stayed as it was
stderr, my nvidia card is a 9600M GT

lidex, whenever i try to sudo nvidia-xconfig

it gives me this message: 

WARNING: Unable to locate/open X configuration file.
New X configuration file written to 'etc/x11/xorg.conf'

I reckon the problem might be here
Oh one question... Did your NVidia card work before?

---

