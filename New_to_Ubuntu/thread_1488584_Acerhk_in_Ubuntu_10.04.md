---
title: "Acerhk in Ubuntu 10.04"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by darkeale on 2010-05-20
Hi,

I am trying to add the Acerhk module in Ubuntu 10.04 to get the wireless on my fujitsu siemens amilo li 1718 laptop.  When I try to do the make command I get the following error:-

alex@alex-laptop:~/acerhk-0.5.35$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/alex/acerhk-0.5.35 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/alex/acerhk-0.5.35/acerhk.o
gcc: -pg and -fomit-frame-pointer are incompatible
make[2]: *** [/home/alex/acerhk-0.5.35/acerhk.o] Error 1
make[1]: *** [_module_/home/alex/acerhk-0.5.35] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [acerhk.ko] Error 2
alex@alex-laptop:~/acerhk-0.5.35$ 

Can anyone please help me with this?

Thanks,
Alex

---

### Post by tronshort on 2010-07-08
Same problem, please help !

---

### Post by darkeale on 2010-07-09
Hi,

I got my wireless working by searching for instructions for my specific wireless chipset, in my case an athero ar5007 i think.  If you search for instructions for your chipset instead of trying to get the acerhk to work you should be ok.

Hope this helps,
Alex

---

### Post by cj13579 on 2010-07-09
Before compiling the driver you could try running:

```
sudo apt-get install build-essential linux-headers-($uname -r)
```

---

