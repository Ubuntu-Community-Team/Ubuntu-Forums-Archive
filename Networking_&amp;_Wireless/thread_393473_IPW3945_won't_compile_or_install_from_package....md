---
title: "IPW3945 won't compile or install from package..."
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by Starks on 2007-03-25
Before I learned about restricted-modules, I was using ipw3945-modules-2.6.18-4-xen-686_2.6.18+1.1.3-4_i386.deb to install wireless on my laptop, but a week or two ago the wireless just stopped working after a kernel update and I have been unable to get wireless working anymore (even with the restricted manager). I tried compiling but I came up with this error...


```
root@freelance:~# cd ieee80211-1.2.16
root@freelance:~/ieee80211-1.2.16# make
Checking in /lib/modules/2.6.20-13-generic for ieee80211 components...
make -C /lib/modules/2.6.20-13-generic/build M=/home/eric/ieee80211-1.2.16 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-13-generic'
  Building modules, stage 2.
  MODPOST 5 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-13-generic'
root@freelance:~/ieee80211-1.2.16# cd /home/eric/ipw-1.2.0
bash: cd: /home/eric/ipw-1.2.0: No such file or directory
root@freelance:~/ieee80211-1.2.16# cd /home/eric/ipw3945-1.2.0
root@freelance:~/ipw3945-1.2.0# make
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
-e 
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

```

---

### Post by Kobalt on 2007-03-26
Before compiling the new manager you need to uninstall completely the old one. You should uninstall that package you used, through Synaptic for example, then try to compile...

---

