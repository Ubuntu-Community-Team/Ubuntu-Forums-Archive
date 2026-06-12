---
title: "Wireless connection problem"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by krikett on 2010-10-10
**alfa awus036nh** 			
 			 			 		   		 		 		[COLOR=#000000]how do I install the alpha awus036nh on my ubuntu distro. [/COLOR]step by step. I do not really understand what I need to configure.

---

### Post by Matt__ on 2010-10-10
theres a thread here for 9.10
[http://ubuntuforums.org/showthread.php?t=1387475](http://ubuntuforums.org/showthread.php?t=1387475)

---

### Post by krikett on 2010-10-10
I have made a mistake.  not awus036hn but awus036h

---

### Post by krikett on 2010-10-10
I use the guide [http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing)



and when i try to make this is whats hapening. 
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

