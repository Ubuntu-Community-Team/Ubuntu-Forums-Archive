---
title: "anyone install intellinux.org dirvers?"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by SDE on 2007-04-12
i wanted to update my system per [this](http://tinyshell.be/aircrackng/forum/index.php?topic=1387) tutorial.

when i compiled it, i got errors because it couldn't find a make file in /lib/modules/2.6.20.14-generic/source

that directory didn't exist.

i then used apt-get to get the source, but the linux-source doesn't have the -generic in the name.  so i created a link:

**ln -s /usr/src/linux-src-2.6.20 /lib/modules/2.6.20.14-generic/source**

first of all .. was that right? .. it compiled anyway.

well now the tutorial tells me to go to /lib/modules/2.6.20.14-generic/build and run

**sudo make menucfg**

when i do, i get this error:```
make[1]: *** [scripts/kconfig/lxdialog/checklist.o] Error 1
make: *** [menuconfig] error 2
```

any ideas on how i can fix this?  i don't think it's related to this article, but rather something else.

---

