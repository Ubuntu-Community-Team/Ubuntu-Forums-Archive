---
title: "vmware player install issue"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by speedygonzalas on 2009-02-21
When i try to install vmware player version 2.0.5 build - 109488 using compiler gcc-4.3 which is wat my comp was compiled with, it installs most of vmware, except i always get an error when it tries to build a new vmmon module. this keeps popping up at the end:

```

In file included from /tmp/vmware-config2/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:115:
/tmp/vmware-config2/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module. 
```


i really dont know wats going on, do i need to download a new kernel, or do i need to down load another compiler?

---

### Post by ibuclaw on 2009-02-21
For reasons beyond my understanding (I personally don't use VMWare2), the vmware script isn't copying the header file "compat_semaphore.h" into the designated directory where it should be when the module is compiled/recompiled.

Have you tried re-downloading the VMWare tarball and running an md5sum check on it to ensure its integrity?
After you are certain that nothing is wrong with it, then try installing again with the newly downloaded install package.

Regards
Iain

---

### Post by speedygonzalas on 2009-02-21
i haven't tried running that, but if theres a different version of vmware with the tar extension that u know of that will work i'd be willing to try that approach to, i'v already redownloaded vmware twice now and still same results...

---

