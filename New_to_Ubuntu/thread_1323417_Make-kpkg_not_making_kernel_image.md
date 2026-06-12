---
title: "Make-kpkg not making kernel image"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by abhiram7 on 2009-11-11
Hi

i am trying to compile a custom linux kernel by using the [http://newbiedoc.sourceforge.net/system/kernel-pkg.html](http://newbiedoc.sourceforge.net/system/kernel-pkg.html) as a guide. After completing the normal process of downloading the source kernel and blah blah, i am left with the final part of building the kernel image using make-kpkg -append-to-version=-abhi-kernel command which ends with a note saying "nothing to be done" and fails to create a new kernel package.

can some one throw some light on this??

---

### Post by abhiram7 on 2009-11-11
OK. i tried making a new package from another guide by using the command
"sudo make-kpkg --initrd --append-to-version=-custom-kernel-image kernel_headers" and the following is the error i get

  CC [M]  ubuntu/ndiswrapper/divdi3.o
  LD [M]  ubuntu/ndiswrapper/ndiswrapper.o
  CC [M]  ubuntu/rfkill/av5100.o
  CC [M]  ubuntu/rfkill/pbe5.o
  CC [M]  lib/lzo/lzo1x_compress.o
  CC [M]  lib/lzo/lzo1x_decompress.o
  LD [M]  lib/lzo/lzo_compress.o
  LD [M]  lib/lzo/lzo_decompress.o
  Building modules, stage 2.
  MODPOST 27 modules
ERROR: "xor_blocks" [ubuntu/dm-raid4-5/dm-raid45.ko] undefined!
WARNING: modpost: Found 1 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.31'
make: *** [debian/stamp/build/kernel] Error 2

And ofcourse the package is not created!!!!

any suggestions?

---

### Post by abhiram7 on 2009-11-12
Figured out how build a kernel image. finally!!
make-kpkg bzImage did the work.

I compiled and booted the system with my custom kernel, but i like check it twice before being excited.

 Is there a way to check the name of the kernel image(as it appears in the grub menu) using which the system has booted??.


thanks

---

### Post by robkey on 2010-06-01
You need to do make-kpkg --initrd --append-to-version='abhi-kernel12' kernel_image kernel_headers.

there must be targets kernel_image   and optionally kernel_headers.

The appendage must contain a digit.
Rob Key

---

