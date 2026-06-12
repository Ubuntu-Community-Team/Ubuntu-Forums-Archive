---
title: "I can't compile driver for LAN NS DP8381X"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by -luk- on 2007-09-14
Hi,
I have board with integrated LAN NationalSemicon. DP8381X and I found out driver for linux (kernel 2.6.x , 2.4.x)

So now I need to kompile with make, makefile for kernel 2.6.x is included. No config file there.

When I try to make, there show this errors:

```

make -C /usr/src/2.6.20-15-generic/ M=/usr/src/DP8381X modules
make[1]: Entering directory `/usr/src/2.6.20-15-generic'

  WARNING: Symbol version dump /usr/src/2.6.20-15-generic/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /usr/src/DP8381X/nsmos.o
/usr/src/DP8381X/nsmos.c:46: error: expected â)â before string constant
/usr/src/DP8381X/nsmos.c:50: error: expected â)â before string constant
/usr/src/DP8381X/nsmos.c:54: error: expected â)â before string constant
/usr/src/DP8381X/nsmos.c:58: error: expected â)â before string constant
/usr/src/DP8381X/nsmos.c:63: error: expected â)â before string constant
/usr/src/DP8381X/nsmos.c:69: error: expected â)â before string constant
/usr/src/DP8381X/nsmos.c:75: error: expected â)â before string constant
/usr/src/DP8381X/nsmos.c:83: error: expected â)â before string constant
/usr/src/DP8381X/nsmos.c:88: error: expected â)â before string constant
/usr/src/DP8381X/nsmos.c:93: error: expected â)â before string constant
/usr/src/DP8381X/nsmos.c:98: error: expected â)â before string constant
/usr/src/DP8381X/nsmos.c:104: error: expected â)â before string constant
/usr/src/DP8381X/nsmos.c:114: error: expected â)â before string constant
/usr/src/DP8381X/nsmos.c:187: warning: initialization from incompatible pointer type
/usr/src/DP8381X/nsmos.c: In function âNsmOpenâ:
-bash: user@ubuntu:/usr/src/DP8381X$: No such file or directory
/usr/src/DP8381X/nsmos.c:582: warning: passing argument 2 of ârequest_irqâ from incompatible pointer type
make[2]: *** [/usr/src/DP8381X/nsmos.o] Error 1
make[1]: *** [_module_/usr/src/DP8381X] Error 2
make[1]: Leaving directory `/usr/src/2.6.20-15-generic'
make: *** [all] Error 2

```

nmos.c file si included in attachment

I'm a begginer with linux, so mybe I do any stupid mistake... 

thank U for any suggestion

---

### Post by JinxAu on 2007-09-14
Gday Luk,

I am not expert on compiling kernel modules, but after a brief search through Google, it appears there might already be support for this network card in Ubuntu already...

Try "modprobe natsemi" in the command line. Then run "dmesg" as well... I get the following output:
> [88280.936000] natsemi dp8381x driver, version 2.1, Sept 11, 2006
[88280.936000]   originally by Donald Becker <becker@scyld.com>
[88280.936000]   [http://www.scyld.com/network/natsemi.html](http://www.scyld.com/network/natsemi.html)
[88280.936000]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder

You should then be able to see if you have an ethernet adapter by running "ifconfig" (look for eth0).

Cya round
Jinx

---

### Post by -luk- on 2007-09-17
Thank U, it's working now :)

---

