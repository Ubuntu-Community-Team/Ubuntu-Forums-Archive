---
title: "Compiling ndiswrapper"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by edsmaffs on 2007-12-16
Hello.
I am trying to compile ndiswrapper 1.6. Although Synaptic is good, it has the newer version (I need the old version with the load_fw_ar5523 command to set up my WPN111 driver)

OK. I downloaded the tar package from sourceforge, and unpacked it. I removed the new version of ndiswrapper using Synaptics, and then ran the instructions in the INSTALL file.

Here were the results from the different make commands:

sudo make uninstall:

NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper': Is a directory
make: *** [uninstall] Error 1



sudo make

make -C driver
make[1]: Entering directory `/home/edward/Desktop/Ndiswrapper/driver'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/edward/Desktop/Ndiswrapper/driver \
                DRIVER_VERSION=1.6
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/edward/Desktop/Ndiswrapper/driver/loader.o
/home/edward/Desktop/Ndiswrapper/driver/loader.c: In function ‘register_devices’:
/home/edward/Desktop/Ndiswrapper/driver/loader.c:669: error: ‘struct usb_driver’ has no member named ‘owner’
make[3]: *** [/home/edward/Desktop/Ndiswrapper/driver/loader.o] Error 1
make[2]: *** [_module_/home/edward/Desktop/Ndiswrapper/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/edward/Desktop/Ndiswrapper/driver'
make: *** [all] Error 2



sudo make install

make -C driver install
make[1]: Entering directory `/home/edward/Desktop/Ndiswrapper/driver'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/edward/Desktop/Ndiswrapper/driver \
                DRIVER_VERSION=1.6
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/edward/Desktop/Ndiswrapper/driver/loader.o
/home/edward/Desktop/Ndiswrapper/driver/loader.c: In function ‘register_devices’:
/home/edward/Desktop/Ndiswrapper/driver/loader.c:669: error: ‘struct usb_driver’ has no member named ‘owner’
make[3]: *** [/home/edward/Desktop/Ndiswrapper/driver/loader.o] Error 1
make[2]: *** [_module_/home/edward/Desktop/Ndiswrapper/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/edward/Desktop/Ndiswrapper/driver'
make: *** [install] Error 2





There were quite a few errors there. :( Can anybody explain how to fix and compile it?

Or, alternatively, can anyone explain how to install the older version using Synaptics?

---

### Post by HermanAB on 2007-12-16
Hmm, never go to the next step if the previous step failed...

A good way to ensure success is to first compile your kernel, to ensure that your development system is set up properly, before trying to compile other software.

Cheers,

Herman

---

### Post by edsmaffs on 2007-12-16
BIG ?

I just followed the instructions, I didn't realise there were errors.
Is there a way to fix the errors? Or a way to get ndiswrapper 1.6 as a *.deb or on Synaptics?

---

### Post by Erwin Criddle on 2008-03-05
You need to install the build-essential package.
Run 'sudo apt-get install build-essential from the terminal and try compiling ndiswrapper again.

---

