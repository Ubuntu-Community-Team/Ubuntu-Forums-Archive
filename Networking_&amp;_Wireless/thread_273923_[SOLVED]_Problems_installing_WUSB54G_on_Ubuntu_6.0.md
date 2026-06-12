---
title: "[SOLVED] Problems installing WUSB54G on Ubuntu 6.06"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by JawsThemeSwimming428 on 2006-10-09
I have been trying to get my WUSB54G wireless adapter working for about 2 weeks now, with no luck. I get pretty much the same instructions everywhere and I finally got to the point where you run:

 sudo make install
 sudo make

   And that's as far as I got, because when I run make the output returns errors and I am not quite sure what they mean. I was wondering if it was possible for me to post the output from that here and see if anyone can let me know what to do to correct the errors. 

   Also, in the instructions it says int Admin -> Networking there should be something listed called rausb0 or something like that. I don't see that, I see Modem and eth0. Any help would be appreciated.

---

### Post by koshari on 2006-10-09
the first thing to post would be the output of dmesg.

---

### Post by JawsThemeSwimming428 on 2006-10-09
I installed the linux-source package from Synaptic. Once I was in the ndiswrapper directory I ran 'make distclean' and that ran with no errors. Then I ran 'make' and it returned the following output, with errors:

willy@willy-desktop:~/Desktop/ndiswrapper-1.23$ make distclean
make -C driver clean
make[1]: Entering directory `/home/willy/Desktop/ndiswrapper-1.23/driver'
rm -rf ndiswrapper.ko ndiswrapper.o hal.o iw_ndis.o loader.o misc_funcs.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o wrapmem.o wrapndis.o wrapper.o divdi3.o usb.o win2lin_stubs.o \
divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/willy/Desktop/ndiswrapper-1.23/driver'
make -C utils clean
make[1]: Entering directory `/home/willy/Desktop/ndiswrapper-1.23/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/willy/Desktop/ndiswrapper-1.23/utils'
rm -f *~
rm -fr ndiswrapper-1.23 ndiswrapper-1.23.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/willy/Desktop/ndiswrapper-1.23/driver'
rm -rf ndiswrapper.ko ndiswrapper.o hal.o iw_ndis.o loader.o misc_funcs.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o wrapmem.o wrapndis.o wrapper.o divdi3.o usb.o win2lin_stubs.o \
divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h
make[1]: Leaving directory `/home/willy/Desktop/ndiswrapper-1.23/driver'
make -C utils distclean
make[1]: Entering directory `/home/willy/Desktop/ndiswrapper-1.23/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/willy/Desktop/ndiswrapper-1.23/utils'
rm -f .\#*
willy@willy-desktop:~/Desktop/ndiswrapper-1.23$ make
make -C driver
make[1]: Entering directory `/home/willy/Desktop/ndiswrapper-1.23/driver'
Can't find kernel build files in /lib/modules/2.6.15-23-386/build;
give the path to kernel build directory with
KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/willy/Desktop/ndiswrapper-1.23/driver'
make: *** [all] Error 2
willy@willy-desktop:~/Desktop/ndiswrapper-1.23$

What did I do wrong?

---

