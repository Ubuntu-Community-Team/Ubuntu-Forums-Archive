---
title: "Intel 536 Modem/Edgy"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by ijfoster on 2006-10-25
Hi All
I have just upgraded to 6.10
I installed a modem previously using the How To and it worked very well.
Does anyone have an alternative solution for getting the Modem to Work 

I use the Modem for Faxing 

Hope You Can Help

---

### Post by aasodi on 2006-11-02
Same here...

When I need to compile driver (make 536) error ocurs

[HTML]aasodi@asodi:~/Install/Dialup Modem/Intel-536$ make 536
   Module precompile check
   Current running kernel is: 2.6.17-10-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
uname -r|grep "2.6" && \
        cd coredrv && make 536core_26 && \
        cp Intel536.ko .. && cd .. && \
        strip --strip-debug Intel536.ko && \
        exit; \
        ls Intel536.ko >/dev/null 2>&1 ||  uname -r | grep "2.6" && echo "Failed to build driver" && exit; \
        if [  ]; then \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_SOURCE_PATH= "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        else \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_INCLUDES=/lib/modules/`uname -r`/build/include \
       "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        fi ; \
        cp Intel536.o .. ; \
        if [ -a /boot/vmlinuz.version.h ]; then \
        cp /boot/vmlinuz.version.h /lib/modules/`uname -r`/build/include/linux/version.h;\
        fi
2.6.17-10-generic
make[1]: Entering directory `/home/aasodi/Install/Dialup Modem/Intel-536/coredrv'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/aasodi/Install/Dialup Modem/Intel-536/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
make[2]: *** No rule to make target `Modem/Intel-536/coredrv'.  Stop.
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [536core_26] Error 2
make[1]: Leaving directory `/home/aasodi/Install/Dialup Modem/Intel-536/coredrv'
2.6.17-10-generic
Failed to build driver
[/HTML]

Thanks in advance!

---

### Post by Turin Turambar on 2006-11-04
I think the problem lies in 2.6.17 kernel. There's little you can do without finding (or writing) the appropriate patch for Intel 536 driver.

My girlfriend has I536EP, while I have a Lucent agere modem.

I couldn't compile the Lucent drivers without the patch that Gentoo team wrote. That fixed some driver issues with a new kernel.

Before I found a patch for my Lucent, I tried compiling the driver for 536EP and got almost the same errors as for Lucent.

So... my opinion is that Ubuntu team REALLY needs to make a proper support for Intel 536, Lucent Agere (mars chip included) and other winmodems that are known to work with Linux!! The lack of support for these modems makes many users avoid Ubuntu at all costs.

---

### Post by proxp on 2006-11-14
Here is a [Dialup Modem How to]("https://help.ubuntu.com/community/DialupModemHowto") wiki that should help. The updated intel 536 drivers can be found at [http://phep2.technion.ac.il/linmodems/packages/intel/Philippe.Vouters/]("http://phep2.technion.ac.il/linmodems/packages/intel/Philippe.Vouters/").

I just installed it on Edgy and it works like a charm. Before that I compiled the latest linux kernel for ubuntu.

Hope that helps.

---

### Post by FLPCGuy on 2007-01-02
Lack of a current driver for the Intel 536EP chipset is what is keeping Ubuntu off my primary PC.  It doesn't have a serial port for my real external modems and I can't find a USB-serial connector that has any useful Linux drivers either.

---

