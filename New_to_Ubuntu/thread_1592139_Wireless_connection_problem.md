---
title: "Wireless connection problem"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by krikett on 2010-10-10
i have a alfa awus036 h. I follow the guide [http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing).
When i try Sudo make this is what i got. '

krikettmannen@flesken:~/rtl-wifi$ sudo make
make -C /lib/modules/2.6.35-22-generic/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function ‘conf_askvalue’:
scripts/kconfig/conf.c:105: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function ‘conf_choice’:
scripts/kconfig/conf.c:307: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  UPD     include/generated/utsrelease.h
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [modules] Error 2

---

### Post by krikett on 2010-10-10
btw i run the latest version of ubuntu.

---

