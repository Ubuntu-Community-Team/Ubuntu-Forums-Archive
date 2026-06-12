---
title: "Lucent modem in Edgy - not functioning! Help!"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by Turin Turambar on 2006-11-01
There's no way for me to compile (alk8 & martian) drivers for Lucent modem in Edgy!! I get some error.... I tried gcc 4.1, 3.4 and 3.3 but with no luck.

Did anyone try this? Any solution? Help, I don't have internet connection in Ubuntu. :(

Thanks!

---

### Post by Turin Turambar on 2006-11-01
I tried to compile with different versions of GCC.

Here are the errors:

GCC 3.4
```
ivan@ivan:~/ltmodem-2.6-alk-8$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/ivan/ltmodem-2.6-alk-8 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
CC [M] /home/ivan/ltmodem-2.6-alk-8/lt_modem.o
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:123: error: parse error before string constant
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:123: warning: type defaults to `int' in declaration of `MODULE_PARM'
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:123: warning: function declaration isn't a prototype
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:123: warning: data definition has no type or storage class
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:125: error: parse error before string constant
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:125: warning: type defaults to `int' in declaration of `MODULE_PARM'
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:125: warning: function declaration isn't a prototype
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:125: warning: data definition has no type or storage class
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:130: error: parse error before string constant
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:130: warning: type defaults to `int' in declaration of `MODULE_PARM'
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:130: warning: function declaration isn't a prototype
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:130: warning: data definition has no type or storage class
make[2]: *** [/home/ivan/ltmodem-2.6-alk-8/lt_modem.o] Error 1
make[1]: *** [_module_/home/ivan/ltmodem-2.6-alk-8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [module] Error 2 
```

GCC 4.0

```
ivan@ivan:~/ltmodem-2.6-alk-8$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/ivan/ltmodem-2.6-alk-8 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
CC [M] /home/ivan/ltmodem-2.6-alk-8/lt_modem.o
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:123: error: syntax error before string constant
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:123: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:123: warning: function declaration isn’t a prototype
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:123: warning: data definition has no type or storage class
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:125: error: syntax error before string constant
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:125: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:125: warning: function declaration isn’t a prototype
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:125: warning: data definition has no type or storage class
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:130: error: syntax error before string constant
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:130: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:130: warning: function declaration isn’t a prototype
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:130: warning: data definition has no type or storage class
make[2]: *** [/home/ivan/ltmodem-2.6-alk-8/lt_modem.o] Error 1
make[1]: *** [_module_/home/ivan/ltmodem-2.6-alk-8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [module] Error 2 
```

GCC 4.1

```
 ivan@ivan:~/ltmodem-2.6-alk-8$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/ivan/ltmodem-2.6-alk-8 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
CC [M] /home/ivan/ltmodem-2.6-alk-8/lt_modem.o
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:123: error: expected ‘)’ before string constant
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:125: error: expected ‘)’ before string constant
/home/ivan/ltmodem-2.6-alk-8/lt_modem.c:130: error: expected ‘)’ before string constant
make[2]: *** [/home/ivan/ltmodem-2.6-alk-8/lt_modem.o] Error 1
make[1]: *** [_module_/home/ivan/ltmodem-2.6-alk-8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [module] Error 2 
```

As you see, GCC 4.1 gives the least amount of errors. The same happens for both 386 & generic kernels.

Can anyone help? What "expected ')' before string constant" mean and how can I fix it? Thanks!

---

### Post by GCR on 2006-11-01
DUDE!

You are not gonna believe me, but I finally got it to work somehow. It was with the Martian Driver. I posted a HOWTO that is waiting for approval on mods, so check sooner or later it will hopefully be added!

---

### Post by GCR on 2006-11-02
Here's the link to what I did. Hopefully it'll work for you too!

[Lucent Modem in Edgy]("http://ubuntuforums.org/showthread.php?t=290963")

---

### Post by Turin Turambar on 2006-11-02
Thanks man I really appreciate it, however I made ltmodem to work!!!

I just patched the driver with the patch you provided in your post "can't compile..." and wow, it compiled with no problems!!

That makes me think - did you patch the files correctly?

However, this driver cannot be used with k7/generic kernel, only with 386!!!

Yeah! :D

---

### Post by GCR on 2006-11-02
I did patched it correctly, but did not succeded. But then again I was using the generic kernel so that could have been the cause. Anyway if there's anyone using the generic kernel like me, then the Martian Drivers ocmpile perfectly :)

Cheers to you for setting up the modules 8)

---

### Post by Matchless on 2006-11-04
> **Turin Turambar said:**
> Thanks man I really appreciate it, however I made ltmodem to work!!!

I just patched the driver with the patch you provided in your post "can't compile..." and wow, it compiled with no problems!!

That makes me think - did you patch the files correctly?

However, this driver cannot be used with k7/generic kernel, only with 386!!!

Yeah! :D

Where can I find this patch please

---

### Post by Turin Turambar on 2006-11-05
> **Matchless said:**
> Where can I find this patch please

I already posted it in another thread where you can also download the patched driver:

[http://ubuntuforums.org/showthread.php?t=290963](http://ubuntuforums.org/showthread.php?t=290963)

---

