---
title: "Ubuntu 32bit -- 4GB RAM Problem"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by nebu on 2008-12-12
I just installed a Ubuntu 8.10 32 bit edition....

it does not support the 4gb of ram that i have.....


is there a way for me to upgrade to the 64 bit kernel so as to use my ram??

or is there any way i can use the ram without upgrading??

---

### Post by hyper_ch on 2008-12-12
simplest way: Install the -server kernel from the repos (and boot the server kernel). Not so simple way, recompile the kernel with PAE enabled.

---

### Post by LowSky on 2008-12-12
If you just installed then you are better off just reinstalling the 64bit version.

For the most part the .8GB of ram  isn't really going to do much on a standard desktop/laptop install. My machine barely ever sees f0% of the RAM being used., and as for SWAP I've onlt ever seen .05% of it being used.

---

### Post by hyper_ch on 2008-12-12
well, my two ways will let you use the 32-bit OS that you have installed but make full use of the ram.

If you want to go into real 64-bit mode, then yuo need to reinstall.

---

