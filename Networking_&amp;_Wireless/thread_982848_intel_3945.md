---
title: "intel 3945"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by Toost on 2008-11-15
Well,, after having so much trouble with my atheros wireless interface for about 10 months now.... i decided, why not buy another... searched on the internet for a nice card.... searched on the internet for compatibility..... 

So made my choice.... Intel 3945, 2 weeks later... still trying to get this thing up....


Cant find it with commands like lspci lshw or something... nothing when i call out any dmesg.... 

so would someone please help me...

---

### Post by Toost on 2008-11-16
Tried install ipw3945 drivers... gives me an error, wich says me to install ieee80211 patch kernel... i downloaded newer version of ieee that gives me an error like this

[PHP]
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e  Aborting the build.  You can force the build to continue by adding:

	IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1
a@ubuntu:~/ipw3945-1.2.2$ sudo make install
Makefile:53: 
Makefile:54: WARNING: $SHELL not set to bash.
Makefile:55: If you experience build errors, try
Makefile:56: 'make SHELL=/bin/bash'.
Makefile:57: 
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
install -d /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/
install -m 644 -c ipw3945.ko /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/
install: cannot stat `ipw3945.ko': No such file or directory
make: *** [install] Error 1
[/PHP]

---

### Post by Toost on 2008-11-16
tried installing hardy... worked with intrepid ibex... but still nothing

---

