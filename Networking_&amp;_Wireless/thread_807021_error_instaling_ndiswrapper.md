---
title: "error instaling ndiswrapper"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by uinarffraniu on 2008-05-25
Hi,

trying to make wireless card ( Broadcom Corporation BCM94311MCG wlan mini-PCI) on my laptop work i found this guide

[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/) 

which looks simple enough for me to follow, but i get this message installing ndiwrapper

:~/bcm43xx/ndiswrapper/ndiswrapper-1.49$ sudo make install
make -C driver install
make[1]: Wej&#347;cie do katalogu `/home/agamemnon/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver'
make -C /usr/src/linux-headers-2.6.24-16-generic SUBDIRS=/home/agamemnon/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver
make[2]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/agamemnon/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[2]: *** [_module_/home/agamemnon/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver] B&#322;&#261;d 2
make[2]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [default] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/home/agamemnon/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver'
make: *** [install] B&#322;&#261;d 2

can anybody give me a clue what's wrong?

hope those few polish words do not make it illegible. bl&#261;d means error ... 

thanks

uinarf



***ok, made it work the easy way through synaptic***

---

### Post by Ayuthia on 2008-05-25
> **uinarffraniu said:**
> Hi,

trying to make wireless card ( Broadcom Corporation BCM94311MCG wlan mini-PCI) on my laptop work i found this guide

[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/) 

which looks simple enough for me to follow, but i get this message installing ndiwrapper

:~/bcm43xx/ndiswrapper/ndiswrapper-1.49$ sudo make install
make -C driver install
make[1]: Wej&#347;cie do katalogu `/home/agamemnon/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver'
make -C /usr/src/linux-headers-2.6.24-16-generic SUBDIRS=/home/agamemnon/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver
make[2]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/agamemnon/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[2]: *** [_module_/home/agamemnon/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver] B&#322;&#261;d 2
make[2]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [default] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/home/agamemnon/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver'
make: *** [install] B&#322;&#261;d 2

can anybody give me a clue what's wrong?

hope those few polish words do not make it illegible. bl&#261;d means error ... 

thanks

uinarf



***ok, made it work the easy way through synaptic***

I can read the numbers!!!!  Luckily, that is all that was needed.  NDISwrapper 1.49 does not compile with Hardy.  You will need to use a newer version (1.50 or higher).  You can either install ndiswrapper-utils from the Hardy CD or you can download the other versions from [here]("http://sourceforge.net/project/showfiles.php?group_id=93482").

---

