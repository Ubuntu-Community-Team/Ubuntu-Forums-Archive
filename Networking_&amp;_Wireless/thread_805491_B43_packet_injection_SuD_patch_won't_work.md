---
title: "B43 packet injection SuD patch won't work"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by Anolis on 2008-05-24
When i try to patch my b43 module i get this.

```
anolis@anolis-laptop:/usr/src/linux-source-2.6.24$ sudo make modules; sudo make modules_install
scripts/kconfig/conf -s arch/x86/Kconfig
***
*** You have not yet configured your kernel!
*** (missing kernel .config file)
***
*** Please run some configurator (e.g. "make oldconfig" or
*** "make menuconfig" or "make xconfig").
***
make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2

The present kernel configuration has modules disabled.
Type 'make config' and enable loadable module support.
Then build a kernel with module support enabled.

make: *** [modules] Error 1
scripts/kconfig/conf -s arch/x86/Kconfig
***
*** You have not yet configured your kernel!
*** (missing kernel .config file)
***
*** Please run some configurator (e.g. "make oldconfig" or
*** "make menuconfig" or "make xconfig").
***
make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2

The present kernel configuration has modules disabled.
Type 'make config' and enable loadable module support.
Then build a kernel with module support enabled.

make: *** [modules_install] Error 1
anolis@anolis-laptop:/usr/src/linux-source-2.6.24$ 

```

the patch file is located in "/usr/src/linux-source-2.6.24/"

AFAIK I am doing everything correctly.. as this worked when i did the patch for the bcm43xx drivers


--Anolis :guitar:

---

### Post by Anolis on 2008-05-24
bump

---

### Post by Joker5bb on 2008-06-12
b43 works wery well, i have made a how-to. please visit it here
[http://tinyshell.be/aircrackng/forum/index.php?topic=3597.0](http://tinyshell.be/aircrackng/forum/index.php?topic=3597.0)

---

