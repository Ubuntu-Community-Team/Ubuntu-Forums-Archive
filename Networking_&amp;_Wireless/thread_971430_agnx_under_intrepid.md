---
title: "agnx under intrepid"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by wesmo on 2008-11-05
Hi all,

I'm trying to compile the AGNX (Airgo wireless) driver ([http://git.sipsolutions.net/?p=agnx.git](http://git.sipsolutions.net/?p=agnx.git)) on Ubuntu 8.10 AMD 64 with the 2.6.27-7-generic kernel. This compiles fine, but I can't insert the module into the kernel :S

Running nm on agnx.ko returns unidentified symbols and the developer of the agnx driver advised me to build the module against the latest wireless-testing tree ([http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)).

I've pulled the kernel, but when I run make xconfig I get:

```

user@amd64:~/Desktop/Wireless/git/wireless-testing$ make xconfig
  CHECK   qt
*
* Unable to find the QT3 installation. Please make sure that
* the QT3 development package is correctly installed and
* either install pkg-config or set the QTDIR environment
* variable to the correct location.
*
make[1]: *** No rule to make target `scripts/kconfig/.tmp_qtcheck', needed by `scripts/kconfig/qconf.o'.  Stop.
make: *** [xconfig] Error 2
user@amd64:~/Desktop/Wireless/git/wireless-testing$
```

I've installed qt3-dev-tools_3.3.8-b5ubuntu1_amd64.deb from packages.ubuntu.com and still no luck :S

kernel-package, libncurses5-dev & fakeroot are also installed.

Attempting to run make menuconfig returns lots of errors:

```

drivers/crypto/Kconfig:187: unknown option "The"
drivers/crypto/Kconfig:188: unknown option "as"
drivers/crypto/Kconfig:190: unknown option "To"
drivers/crypto/Kconfig:191: unknown option "will"
arch/x86/kvm/Kconfig:16: unknown option "If"
arch/x86/kvm/Kconfig:32: unknown option "This"
arch/x86/kvm/Kconfig:33: unknown option "a"
arch/x86/kvm/Kconfig:35: unknown option "To"
arch/x86/kvm/Kconfig:36: unknown option "will"
arch/x86/kvm/Kconfig:38: unknown option "If"
drivers/lguest/Kconfig:12: unknown option "If"
drivers/virtio/Kconfig:21: unknown option "Currently"
drivers/virtio/Kconfig:22: unknown option "that"
drivers/virtio/Kconfig:24: unknown option "If"
drivers/virtio/Kconfig:34: unknown option "If"
make[1]: *** [menuconfig] Error 1
make: *** [menuconfig] Error 2

```

I tried to copy the existing (running) kernel configuration over with no success. If someone can show me where I am going wrong or point me in the right direction it would be much appreciated.

Is it necessary to place the wireless-testing source in /usr/src?

I've noticed some guides symlink the source to /usr/src/linux - why? 

Thanks in advance :)

---

