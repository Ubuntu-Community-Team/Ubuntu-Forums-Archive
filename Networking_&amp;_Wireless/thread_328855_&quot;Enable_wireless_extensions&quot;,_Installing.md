---
title: "&quot;Enable wireless extensions&quot;, Installing madwifi help please"
date: 2006-12-31
forum: Networking &amp; Wireless
---

### Post by darkmediator on 2006-12-31
Hi,
I tried ti install madwifi drivers with
```

make KERNELPATH=/usr/src/linux-headers-2.6.17-10

```
 But it says...
```

Checking requirements... ok.
Checking kernel configuration... FAILED
Please enable wireless extensions.
make: *** [configcheck] Error 1

```

How to enable wireless extensions?? Please give me all the details if possible!
Thanx!

---

### Post by tturrisi on 2006-12-31
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

---

### Post by darkmediator on 2006-12-31
That worked thanx......BUT NOW there's a new problem.

When at last I did => "sudo modprobe ath_pci"

It said
> 
WARNING: Error inserting ath_rate_sample (/lib/modules/2.6.17-10-generic/net/ath_rate_sample.ko): Invalid module format
FATAL: Error inserting ath_pci (/lib/modules/2.6.17-10-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)


Now what??

---

### Post by tturrisi on 2006-12-31
(see dmesg)
look at /var/log/dmesg

---

### Post by 7up on 2007-01-02
Hi, i'm trying to install Madwifi, and having some problems at "make" stage, too.

tried:
```
make KERNELPATH=/usr/src/linux-headers-2.6.17-20-generic
```

got:
```
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/box/madwifi-0.9.2.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-20-generic'
   CC [M]   /home/box/madwifi-0.9.2.1/ath/ah_osdep.o
   HOSTCC /home/box/madwifi-0.9.2.1/ath/uudecode
/home/box/madwifi-0.9.2.1/ath/uudecode.c:26:19:error: stdio.h: No such file or directory
/home/box/madwifi-0.9.2.1/ath/uudecode.c:27:19:error: errno.h: No such file or directory
/home/box/madwifi-0.9.2.1/ath/uudecode.c:28:20:error: getopt.h: No such file or directory
....
A BUNCH OF MESSAGES SIMILAR TO THE LAST 3
....
make[3]: *** [/home/box/madwifi-0.9.2.1/ath/uudecode] Error 1
make[2]: *** [/home/box/madwifi-0.9.2.1/ath] Error 2
make[3]: *** [_modules_/home/box/madwifi-0.9.2.1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-20-generic'
make: *** [modules] Error 2

```

btw, i've already had **linux-restricted-modules-2.6.17-10-generic** installed

I'd greatly appreciate any comments or suggestions.

---

