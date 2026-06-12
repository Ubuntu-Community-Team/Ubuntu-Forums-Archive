---
title: "driver for agere wireless"
date: 2005-11-23
forum: Networking &amp; Wireless
---

### Post by baboyako on 2005-11-23
Hello, I finally figured out that I have to compile this:
[http://www.agere.com/mobility/docs/wl_lkm_722_abg.tar.gz](http://www.agere.com/mobility/docs/wl_lkm_722_abg.tar.gz)
to make my wireless work.
The problem is, I can't compile on the ubuntu box though I have gcc installed.
I did a sudo apt-get install build-essential
which installed the compilers but I get all sorts of errors and no driver file created. 
I hope someone can help me. thanks!

---

### Post by Lambert on 2005-11-23
Post the error outputs that you get while trying to compile.

---

### Post by bribera on 2005-11-23
I've had the same sort of issues over at [http://ubuntuforums.org/showthread.php?t=93850](http://ubuntuforums.org/showthread.php?t=93850)

Here's a sample of the compilation errors that I get (there are _lots_ of this type, this is just the ending):
```

[snip]
../include/hcf/hcfcfg.h: At top level:
../include/hcf/hcfcfg.h:771: warning: type defaults to ‘int’ in declaration of ‘EXPORT_NO_SYMBOLS’
../include/hcf/hcfcfg.h:771: warning: data definition has no type or storage class
In file included from wl_cs.c:118:
../include/wireless/wl_internal.h:112:26: error: linux/tqueue.h: No such file or directory
In file included from wl_cs.c:118:
../include/wireless/wl_internal.h:411: warning: type defaults to ‘int’ in declaration of ‘EXPORT_NO_SYMBOLS’
../include/wireless/wl_internal.h:411: warning: data definition has no type or storage class
../include/wireless/wl_internal.h:794: error: field ‘task’ has incomplete type
wl_cs.c: In function ‘wl_adapter_attach’:
wl_cs.c:195: error: ‘struct dev_link_t’ has no member named ‘release’
wl_cs.c:196: error: ‘struct dev_link_t’ has no member named ‘release’
wl_cs.c:268: warning: implicit declaration of function ‘CardServices’
wl_cs.c: In function ‘wl_adapter_detach’:
wl_cs.c:344: error: ‘struct dev_link_t’ has no member named ‘release’
wl_cs.c: In function ‘wl_adapter_event’:
wl_cs.c:500: error: ‘struct dev_link_t’ has no member named ‘release’
wl_cs.c:501: error: ‘struct dev_link_t’ has no member named ‘release’
wl_cs.c: In function ‘wl_adapter_close’:
wl_cs.c:789: error: ‘struct dev_link_t’ has no member named ‘release’
wl_cs.c:792: error: ‘struct dev_link_t’ has no member named ‘release’
wl_cs.c: In function ‘wl_adapter_init_module’:
wl_cs.c:823: error: ‘servinfo_t’ undeclared (first use in this function)
wl_cs.c:823: error: (Each undeclared identifier is reported only once
wl_cs.c:823: error: for each function it appears in.)
wl_cs.c:823: error: syntax error before ‘serv’
wl_cs.c:832: error: ‘serv’ undeclared (first use in this function)
wl_cs.c:834: error: ‘CS_RELEASE_CODE’ undeclared (first use in this function)
wl_cs.c:840: error: ‘CS_RELEASE’ undeclared (first use in this function)
wl_cs.c:846: warning: implicit declaration of function ‘register_pcmcia_driver’
wl_cs.c: In function ‘wl_adapter_cleanup_module’:
wl_cs.c:880: warning: implicit declaration of function ‘unregister_pcmcia_driver’
wl_cs.c: In function ‘DbgEvent’:
wl_cs.c:1036: error: ‘CS_EVENT_RESET_COMPLETE’ undeclared (first use in this function)
make[1]: *** [wlags49_h1_cs_stap.o] Error 1
make[1]: Leaving directory `/home/brendan/src/pcmcia-cs-3.2.8/wireless'
make: *** [all] Error 2

```

note that this is attempting to compile these drivers with the pcmcia source.  This is using GCC-4; I tried it with exporting gcc-3.4 to CC as well and got the same crap.

---

### Post by baboyako on 2005-11-24
same results as bribera's above...

---

### Post by some1l8 on 2008-05-27
some thing on my lappy. please help.

---

