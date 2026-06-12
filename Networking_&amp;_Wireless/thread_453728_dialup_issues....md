---
title: "dialup issues..."
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by poncenby on 2007-05-24
Greetings,

Can't believe I've spent all evening trying to get a 56k modem to work.
I then noticed this document:
[https://help.ubuntu.com/community/DialupModemHowto/Smartlink](https://help.ubuntu.com/community/DialupModemHowto/Smartlink)

During the following the step:
```
sudo module-assistant auto-install sl-modem
```

I get to a dialog and the option to view the build log. 
in this build log is the following:

```

dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean SUPPORT_ALSA=1
make[1]: Entering directory `/usr/src/modules/sl-modem'
make[1]: Leaving directory `/usr/src/modules/sl-modem'
cd modem; /usr/bin/make clean SUPPORT_ALSA=1
make[1]: Entering directory `/usr/src/modules/sl-modem/modem'
make[1]: Leaving directory `/usr/src/modules/sl-modem/modem'
dh_clean
/usr/bin/make -C drivers clean
make[1]: Entering directory `/usr/src/modules/sl-modem/drivers'
rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~
rm -f -r .tmp_versions
make[1]: Leaving directory `/usr/src/modules/sl-modem/drivers'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/sl-modem'
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean SUPPORT_ALSA=1
make[2]: Entering directory `/usr/src/modules/sl-modem'
make[2]: *** No rule to make target `clean'. Stop.
make[2]: Leaving directory `/usr/src/modules/sl-modem'
make[1]: [clean] Error 2 (ignored)
cd modem; /usr/bin/make clean SUPPORT_ALSA=1
make[2]: Entering directory `/usr/src/modules/sl-modem/modem'
make[2]: *** No rule to make target `clean'. Stop.
make[2]: Leaving directory `/usr/src/modules/sl-modem/modem'
make[1]: [clean] Error 2 (ignored)
dh_clean
/usr/bin/make -C drivers clean
make[2]: Entering directory `/usr/src/modules/sl-modem/drivers'
rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~
rm -f -r .tmp_versions
make[2]: Leaving directory `/usr/src/modules/sl-modem/drivers'
for templ in /usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst /usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst.backup /us
r/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst.modules.in; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.20-15-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.20-15-generic/g ;s/#KVERS#/2.6.20-15-generic/g ; s/_KVERS_/2.6.20-15-generic/g ; s/##KDREV##/2.6.20-15.27/g ; s/#KDREV#/2.6.20-15
.27/g ; s/_KDREV_/2.6.20-15.27/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_clean -k
dh_installdirs lib/modules/2.6.20-15-generic/misc usr/lib/sl-modem
if ! test -e drivers/Makefile ; then echo "Please update the package, extract the tarball!"; exit 1 ; fi
/usr/bin/make -C drivers KERNEL_DIR=/lib/modules/2.6.20-15-generic/build KVERS=2.6.20-15-generic
make[2]: Entering directory `/usr/src/modules/sl-modem/drivers'
gcc-4.1 -I/lib/modules/2.6.20-15-generic/build/include -o kernel-ver kernel-ver.c
kernel-ver.c: In function ‘main’:
kernel-ver.c:11: error: ‘UTS_RELEASE’ undeclared (first use in this function)
kernel-ver.c:11: error: (Each undeclared identifier is reported only once
kernel-ver.c:11: error: for each function it appears in.)
make[2]: *** [kernel-ver] Error 1
make[2]: Leaving directory `/usr/src/modules/sl-modem/drivers'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/sl-modem'
make: *** [kdist_build] Error 2

```

googling found this post:
[https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/103072](https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/103072)

i followed the the bottom post, meaning I:
- added ```
#include <linux/utsrelease.h>
``` to kernel-ver.c in the drivers directory in /usr/src/modules/sl-modem

then ran the modules-assistant command from above and this is now the build log output:

```

dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean SUPPORT_ALSA=1
make[1]: Entering directory `/usr/src/modules/sl-modem'
make[1]: Leaving directory `/usr/src/modules/sl-modem'
cd modem; /usr/bin/make clean SUPPORT_ALSA=1
make[1]: Entering directory `/usr/src/modules/sl-modem/modem'
make[1]: Leaving directory `/usr/src/modules/sl-modem/modem'
dh_clean
/usr/bin/make -C drivers clean
make[1]: Entering directory `/usr/src/modules/sl-modem/drivers'
rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~
rm -f -r .tmp_versions
make[1]: Leaving directory `/usr/src/modules/sl-modem/drivers'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/sl-modem'
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean SUPPORT_ALSA=1
make[2]: Entering directory `/usr/src/modules/sl-modem'
make[2]: *** No rule to make target `clean'. Stop.
make[2]: Leaving directory `/usr/src/modules/sl-modem'
make[1]: [clean] Error 2 (ignored)
cd modem; /usr/bin/make clean SUPPORT_ALSA=1
make[2]: Entering directory `/usr/src/modules/sl-modem/modem'
make[2]: *** No rule to make target `clean'. Stop.
make[2]: Leaving directory `/usr/src/modules/sl-modem/modem'
make[1]: [clean] Error 2 (ignored)
dh_clean
/usr/bin/make -C drivers clean
make[2]: Entering directory `/usr/src/modules/sl-modem/drivers'
rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~
rm -f -r .tmp_versions
make[2]: Leaving directory `/usr/src/modules/sl-modem/drivers'
for templ in /usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst /usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst.backup /us
r/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst.modules.in; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.20-15-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.20-15-generic/g ;s/#KVERS#/2.6.20-15-generic/g ; s/_KVERS_/2.6.20-15-generic/g ; s/##KDREV##/2.6.20-15.27/g ; s/#KDREV#/2.6.20-15
.27/g ; s/_KDREV_/2.6.20-15.27/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_clean -k
dh_installdirs lib/modules/2.6.20-15-generic/misc usr/lib/sl-modem
if ! test -e drivers/Makefile ; then echo "Please update the package, extract the tarball!"; exit 1 ; fi
/usr/bin/make -C drivers KERNEL_DIR=/lib/modules/2.6.20-15-generic/build KVERS=2.6.20-15-generic
make[2]: Entering directory `/usr/src/modules/sl-modem/drivers'
gcc-4.1 -I/lib/modules/2.6.20-15-generic/build/include -o kernel-ver kernel-ver.c
/usr/bin/make all KERNEL_VER=2.6.20-15-generic
make[3]: Entering directory `/usr/src/modules/sl-modem/drivers'
gcc-4.1 -Wall -pipe -O3 -fomit-frame-pointer -D__KERNEL__ -DMODULE -DEXPORT_SYMTAB `test -f /lib/modules/2.6.20-15-generic/build/include/linux/modversions.h 
&& echo -DMODVERSIONS --include /lib/modules/2.6.20-15-generic/build/include/linux/modversions.h -I/lib/modules/2.6.20-15-generic/build/include`  -I. -I./../
modem   -o amrmo_init.o -c amrmo_init.c
amrmo_init.c:46:26: error: linux/config.h: No such file or directory
amrmo_init.c:47:26: error: linux/module.h: No such file or directory
amrmo_init.c:49:24: error: linux/init.h: No such file or directory
amrmo_init.c:52:29: error: linux/interrupt.h: No such file or directory
amrmo_init.c:55:25: error: asm/uaccess.h: No such file or directory
amrmo_init.c:56:35: error: linux/devfs_fs_kernel.h: No such file or directory
amrmo_init.c:65:26: error: linux/device.h: No such file or directory
amrmo_init.c:183: error: expected specifier-qualifier-list before ‘spinlock_t’
amrmo_init.c:191: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘extern’
amrmo_init.c:192: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘extern’
amrmo_init.c:193: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘extern’
amrmo_init.c:194: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘extern’
amrmo_init.c:195: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘extern’
amrmo_init.c:196: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘extern’
amrmo_init.c:197: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘extern’
amrmo_init.c:198: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘extern’
amrmo_init.c:199: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘extern’
amrmo_init.c:200: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘extern’
amrmo_init.c:227: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__devinitdata’
amrmo_init.c:292: warning: data definition has no type or storage class
amrmo_init.c:292: warning: type defaults to ‘int’ in declaration of ‘MODULE_DEVICE_TABLE’
amrmo_init.c:292: warning: parameter names (without types) in function declaration
amrmo_init.c:307: error: expected declaration specifiers or ‘...’ before ‘va_list’
amrmo_init.c: In function ‘amrmo_vprintf’:
amrmo_init.c:310: error: storage size of ‘tv’ isn’t known
amrmo_init.c:314: warning: implicit declaration of function ‘strlen’
amrmo_init.c:314: warning: incompatible implicit declaration of built-in function ‘strlen’
amrmo_init.c:316: warning: implicit declaration of function ‘do_gettimeofday’
amrmo_init.c:320: warning: implicit declaration of function ‘sprintf’
amrmo_init.c:320: warning: incompatible implicit declaration of built-in function ‘sprintf’
amrmo_init.c:321: warning: implicit declaration of function ‘in_interrupt’
amrmo_init.c:324: warning: implicit declaration of function ‘vsprintf’
amrmo_init.c:324: error: ‘args’ undeclared (first use in this function)
amrmo_init.c:324: error: (Each undeclared identifier is reported only once
amrmo_init.c:324: error: for each function it appears in.)
amrmo_init.c:330: warning: implicit declaration of function ‘printk’
amrmo_init.c:330: error: ‘KERN_DEBUG’ undeclared (first use in this function)
amrmo_init.c:330: error: expected ‘)’ before string constant
amrmo_init.c:310: warning: unused variable ‘tv’
amrmo_init.c: At top level:
amrmo_init.c:334: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘int’
amrmo_init.c:351: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘void’
amrmo_init.c:361: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘amrmo_read’
amrmo_init.c:376: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘amrmo_write’
amrmo_init.c:392: error: expected declaration specifiers or ‘...’ before ‘poll_table’
amrmo_init.c:392: warning: ‘struct file’ declared inside parameter list
amrmo_init.c:392: warning: its scope is only this definition or declaration, which is probably not what you want
amrmo_init.c: In function ‘amrmo_poll’:
amrmo_init.c:394: error: dereferencing pointer to incomplete type
amrmo_init.c:397: warning: implicit declaration of function ‘poll_wait’
amrmo_init.c:397: error: ‘struct amrmo_struct’ has no member named ‘wait’
amrmo_init.c:397: error: ‘wait’ undeclared (first use in this function)
amrmo_init.c:398: warning: implicit declaration of function ‘spin_lock_irqsave’
amrmo_init.c:398: error: ‘struct amrmo_struct’ has no member named ‘lock’
amrmo_init.c:407: warning: implicit declaration of function ‘spin_unlock_irqrestore’
amrmo_init.c:407: error: ‘struct amrmo_struct’ has no member named ‘lock’
amrmo_init.c: At top level:
amrmo_init.c:413: warning: ‘struct file’ declared inside parameter list
amrmo_init.c:413: warning: ‘struct inode’ declared inside parameter list
amrmo_init.c: In function ‘amrmo_ioctl’:
amrmo_init.c:415: error: dereferencing pointer to incomplete type
amrmo_init.c:419: error: ‘KERN_DEBUG’ undeclared (first use in this function)
amrmo_init.c:419: error: expected ‘)’ before string constant
amrmo_init.c:423: error: ‘struct amrmo_struct’ has no member named ‘lock’
amrmo_init.c:426: error: ‘struct amrmo_struct’ has no member named ‘lock’
amrmo_init.c:427: warning: implicit declaration of function ‘put_user’
amrmo_init.c:428: error: ‘EFAULT’ undeclared (first use in this function)
amrmo_init.c:431: warning: implicit declaration of function ‘amrmo_card_start’
amrmo_init.c:435: warning: implicit declaration of function ‘amrmo_card_stop’
amrmo_init.c:439: warning: implicit declaration of function ‘amrmo_card_ctl’
amrmo_init.c:441: error: ‘EINVAL’ undeclared (first use in this function)
amrmo_init.c: At top level:
amrmo_init.c:444: warning: ‘struct file’ declared inside parameter list
amrmo_init.c:444: warning: ‘struct inode’ declared inside parameter list
amrmo_init.c: In function ‘amrmo_open’:
amrmo_init.c:447: warning: implicit declaration of function ‘iminor’
amrmo_init.c:449: error: ‘ENODEV’ undeclared (first use in this function)
amrmo_init.c:453: error: ‘KERN_DEBUG’ undeclared (first use in this function)
amrmo_init.c:453: error: expected ‘)’ before string constant
amrmo_init.c:455: error: ‘EBUSY’ undeclared (first use in this function)
amrmo_init.c:457: error: dereferencing pointer to incomplete type
amrmo_init.c:461: warning: implicit declaration of function ‘init_waitqueue_head’
amrmo_init.c:461: error: ‘struct amrmo_struct’ has no member named ‘wait’
amrmo_init.c: At top level:
amrmo_init.c:465: warning: ‘struct file’ declared inside parameter list
amrmo_init.c:465: warning: ‘struct inode’ declared inside parameter list
amrmo_init.c: In function ‘amrmo_release’:
amrmo_init.c:467: error: dereferencing pointer to incomplete type
amrmo_init.c:468: error: ‘KERN_DEBUG’ undeclared (first use in this function)
amrmo_init.c:468: error: expected ‘)’ before string constant
amrmo_init.c: At top level:
amrmo_init.c:479: error: variable ‘amrmo_fops’ has initializer but incomplete type
amrmo_init.c:480: error: unknown field ‘owner’ specified in initializer
amrmo_init.c:480: error: ‘THIS_MODULE’ undeclared here (not in a function)
amrmo_init.c:480: warning: excess elements in struct initializer
amrmo_init.c:480: warning: (near initialization for ‘amrmo_fops’)
amrmo_init.c:481: error: unknown field ‘llseek’ specified in initializer
amrmo_init.c:481: error: ‘no_llseek’ undeclared here (not in a function)
amrmo_init.c:481: warning: excess elements in struct initializer
amrmo_init.c:481: warning: (near initialization for ‘amrmo_fops’)
amrmo_init.c:482: error: unknown field ‘read’ specified in initializer
amrmo_init.c:482: error: ‘amrmo_read’ undeclared here (not in a function)
amrmo_init.c:482: warning: excess elements in struct initializer
amrmo_init.c:482: warning: (near initialization for ‘amrmo_fops’)
amrmo_init.c:483: error: unknown field ‘write’ specified in initializer
amrmo_init.c:483: error: ‘amrmo_write’ undeclared here (not in a function)
amrmo_init.c:483: warning: excess elements in struct initializer
amrmo_init.c:483: warning: (near initialization for ‘amrmo_fops’)
amrmo_init.c:484: error: unknown field ‘poll’ specified in initializer
amrmo_init.c:484: warning: excess elements in struct initializer
amrmo_init.c:484: warning: (near initialization for ‘amrmo_fops’)
amrmo_init.c:485: error: unknown field ‘ioctl’ specified in initializer
amrmo_init.c:485: warning: excess elements in struct initializer
amrmo_init.c:485: warning: (near initialization for ‘amrmo_fops’)
amrmo_init.c:486: error: unknown field ‘open’ specified in initializer
amrmo_init.c:486: warning: excess elements in struct initializer
amrmo_init.c:486: warning: (near initialization for ‘amrmo_fops’)
amrmo_init.c:487: error: unknown field ‘release’ specified in initializer
amrmo_init.c:487: warning: excess elements in struct initializer
amrmo_init.c:487: warning: (near initialization for ‘amrmo_fops’)
amrmo_init.c:504: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘amrmo_pci_interrupt’
amrmo_init.c:513: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘amrmo_pci_probe’
amrmo_init.c:659: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘amrmo_pci_remove’
amrmo_init.c:692: error: variable ‘amrmo_pci_driver’ has initializer but incomplete type
amrmo_init.c:693: error: unknown field ‘name’ specified in initializer
amrmo_init.c:693: warning: excess elements in struct initializer
amrmo_init.c:693: warning: (near initialization for ‘amrmo_pci_driver’)
amrmo_init.c:694: error: unknown field ‘id_table’ specified in initializer
amrmo_init.c:694: error: ‘amrmo_pci_tbl’ undeclared here (not in a function)
amrmo_init.c:694: warning: excess elements in struct initializer
amrmo_init.c:694: warning: (near initialization for ‘amrmo_pci_driver’)
amrmo_init.c:695: error: unknown field ‘probe’ specified in initializer
amrmo_init.c:695: error: ‘amrmo_pci_probe’ undeclared here (not in a function)
amrmo_init.c:695: warning: excess elements in struct initializer
amrmo_init.c:695: warning: (near initialization for ‘amrmo_pci_driver’)
amrmo_init.c:696: error: unknown field ‘remove’ specified in initializer
amrmo_init.c:696: error: ‘amrmo_pci_remove’ undeclared here (not in a function)
amrmo_init.c:696: warning: excess elements in struct initializer
amrmo_init.c:696: warning: (near initialization for ‘amrmo_pci_driver’)
amrmo_init.c:704: error: expected ‘)’ before string constant
amrmo_init.c:705: error: expected ‘)’ before string constant
amrmo_init.c:707: error: expected declaration specifiers or ‘...’ before string constant
amrmo_init.c:707: warning: data definition has no type or storage class
amrmo_init.c:707: warning: type defaults to ‘int’ in declaration of ‘MODULE_AUTHOR’
amrmo_init.c:708: error: expected declaration specifiers or ‘...’ before string constant
amrmo_init.c:708: warning: data definition has no type or storage class
amrmo_init.c:708: warning: type defaults to ‘int’ in declaration of ‘MODULE_DESCRIPTION’
amrmo_init.c:709: error: expected declaration specifiers or ‘...’ before string constant
amrmo_init.c:709: warning: data definition has no type or storage class
amrmo_init.c:709: warning: type defaults to ‘int’ in declaration of ‘MODULE_LICENSE’
amrmo_init.c:712: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘amrmo_init’
amrmo_init.c:789: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘amrmo_exit’
amrmo_init.c:799: warning: data definition has no type or storage class
amrmo_init.c:799: warning: type defaults to ‘int’ in declaration of ‘module_init’
amrmo_init.c:799: warning: parameter names (without types) in function declaration
amrmo_init.c:800: warning: data definition has no type or storage class
amrmo_init.c:800: warning: type defaults to ‘int’ in declaration of ‘module_exit’
amrmo_init.c:800: warning: parameter names (without types) in function declaration
make[3]: *** [amrmo_init.o] Error 1
make[3]: Leaving directory `/usr/src/modules/sl-modem/drivers'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/modules/sl-modem/drivers'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/sl-modem'
make: *** [kdist_build] Error 2

```

my system is Feisty Desktop 7.04 with uname -a...
 
```
Linux idler 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
```

is anyone able to offer any help?

many thanks

---

### Post by jbernardo on 2007-05-25
I'm stuck here too. TIme to see if there are more recent sources for sl-modem drivers...

---

### Post by darkali on 2007-05-26
Instead of compiling it you can simply download it from ubuntu repos, possibly from another computer at:

[http://packages.ubuntu.com/feisty/misc/sl-modem-daemon]("http://packages.ubuntu.com/feisty/misc/sl-modem-daemon")

All dependencies are already met at the default install. Just double click to install it.
If your modem have a Smartlink chipset it will work and I'm using it right now.

---

### Post by jbernardo on 2007-05-26
Two problems - 1st, that package needs to be rebuilt in some cases because it was compiled without alsa support; 2nd, the kernel drivers - slamr & slusb are not in any package, and should be installed by 
sudo module-assistant auto-install sl-modemwhich fails, as ponceby wrote.

---

### Post by michaelzap on 2007-06-09
> **jbernardo said:**
> Two problems - 1st, that package needs to be rebuilt in some cases because it was compiled without alsa support; 2nd, the kernel drivers - slamr & slusb are not in any package, and should be installed by 
sudo module-assistant auto-install sl-modemwhich fails, as ponceby wrote.

Indeed. Same problem here with a Compaq Presario 2100 laptop. Has anyone discovered a fix for this yet?

---

