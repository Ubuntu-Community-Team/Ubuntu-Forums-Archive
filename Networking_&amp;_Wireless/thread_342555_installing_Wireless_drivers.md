---
title: "installing Wireless drivers"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by TisTatos on 2007-01-20
ive tried to install the drivers to my wireless card, INTEL Pro/wireless 3945ABG ive downloaded the tgz for it but when i do %sudo make
i get this msg
```
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
could any1 plz give me a little hint how to solve this since im kinda new to ubuntu and linux, ty

---

### Post by teaker1s on 2007-01-20
terminal type

[COLOR="Red"]iwconfig [/COLOR]

post output

---

