---
title: "Ieee80211 problems"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by blueprints on 2007-01-09
ok, so im fairly new to linux. and i am trying to get my wireless card to work... i have installed the new ieee80211 system on my computer. and when i go to compile my driver i get this mesage


/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
sed: can't read net/ieee80211.h: No such file or directory
/bin/sh: [[: not found
-e
WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem. (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.


-e Aborting the build. You can force the build to continue by adding:

IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1


OK, and so i did this--------------------



make IEEE80211_INC=/usr/include



WICH the right files are in the right place ----------------------------------------




root@blueprints88:/usr/include/net# ls
ieee80211_crypt.h ieee80211.h ieee80211_radiotap.h



But i am still getting an error that it cant find the ieee80211.h file can some one help me out please and tell me what to do, it will help out alot,ive been tryin this for about a week now and still no luck.thanks
Reply With Quote

---

