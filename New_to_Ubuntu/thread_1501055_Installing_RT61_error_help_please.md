---
title: "Installing RT61 error help please"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by The-IRS on 2010-06-03
i was roughly following this guide:
[http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)

but when I do the "sudo make all" command this is what i get:

```
stewart@stewart-desktop:~/Desktop/2010_0412_RT61_Linux_STA_v1.1.2.5/Module$ sudo make all
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/home/stewart/Desktop/2010_0412_RT61_Linux_STA_v1.1.2.5/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/stewart/Desktop/2010_0412_RT61_Linux_STA_v1.1.2.5/Module/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/stewart/Desktop/2010_0412_RT61_Linux_STA_v1.1.2.5/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [all] Error 2
```

any ideas on how to remedy the problem?

---

### Post by clhsharky on 2010-06-03
The-IRS

I have RT61 wifi card, driver already in kernel. Never had to install driver or build module. Whats is your problem?

Sharky

---

### Post by The-IRS on 2010-06-03
What I really have is an Airlink AWLC5025. after some research i determined that it had a RT61 chipset but ubuntu isn't recognizing it.

---

### Post by Tarragon6 on 2010-06-13
I have the same problem with a SparkLan WL-850r miniPCI card. Downloading the RT61 driver and following the instructions linked above, when I get to the make all  command I first get CFLAGS was changed. Fix it to use extra CFLAGS.
I then type 
$ KBUILD_NOPEDANTIC=1 make
but get errors 
'struct net_device' has no member named 'priv'
'struct net_device' has no member named 'open'
'struct net_device' has no member named 'hard_start_xmit'
'struct net_device' has no member named 'stop'
'struct net_device' has no member named 'priv'

Is this due to the kernel version and is there a patch or fix?

---

