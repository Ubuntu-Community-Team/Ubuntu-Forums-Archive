---
title: "Trying to compile wifi driver, getting strange error..."
date: 2009-08-17
forum: New to Ubuntu
---

### Post by alecwh on 2009-08-17
Hello, I recently purchased a Lenovo X200, and I'm following this page to install a driver for my wifi card:

[http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing)

Now, while trying to make it, I get this error:

```

alecwh@alecwh-laptop:~/rtl-wifi$ sudo make
make -C /lib/modules/2.6.28-14-generic/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-14-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-14-generic'
make: *** [modules] Error 2
alecwh@alecwh-laptop:~/rtl-wifi$ 

```

What does "make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop." mean?

Does anyone know what the problem is? Do I need to provide more information?

---

### Post by Technoviking on 2009-08-17
Is Linux kernel headers installed?
```
sudo apt-get install linux-headers-`uname -r` 
```

T-V

---

