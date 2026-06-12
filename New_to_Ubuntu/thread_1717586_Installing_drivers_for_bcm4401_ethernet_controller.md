---
title: "Installing drivers for bcm4401 ethernet controller"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by igiforenzik on 2011-03-30
Hello. I have just installed a fresh copy on my computer, and found out that most of my hardware does not have its drivers included with the installation. I presume i would be able to solve that online, but one of the devices that are not working is the integrated Broadcom BCM4401 ethernet controller. I have managed to find the drivers ([http://www.broadcom.com/support/ethernet_nic/4401.php](http://www.broadcom.com/support/ethernet_nic/4401.php)) and I got a tar.gz archive. I have managed to extract it to my Documents folder, but the next instruction in the README doesn't make sense to a total beginner like myself. Its says: ```
Build the driver b44.o (or b44.ko) as a loadable module for the
running kernel:

   cd src
   make
```
So I was unable to install the driver required to connect to the internet.

I am gratefulll for any and all help you can provide me. :)

---

### Post by Paqman on 2011-03-30
Before installing a driver manually (yuk) have you checked System > Admin > Additional Drivers?

---

### Post by owiknowi on 2011-03-30
had a more or less same problem and i was able to solve it by installing the os with a connected and active ethernet cable.
really have no clue on why, how or what, but it worked... hope this info helps in any way.

---

### Post by igiforenzik on 2011-03-30
It says:```
No proprietary drivers are in use on this system.
```

Also, it tries downloading something when starting, but is unable to, as the machine is unable to connect to the internet without the driver I am attempting to install.

EDiT: Also, the ethernet cable is connected, but the ethernet controller doesn't have a driver. It also said during installation that it can not connect to the internet (recommended option).

---

### Post by stoogiebuncho on 2011-03-30
Hmmm.  It should be able to work with that card.  What's the output of:
```
dmesg | grep eth0
```?

---

### Post by igiforenzik on 2011-03-30
It is:
```


[    2.149206] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0e:a6:14:30:79
[   14.609687] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.816211] b44 ssb0:0: eth0: Link is up at 100 Mbps, full duplex
[   18.816217] b44 ssb0:0: eth0: Flow control is off for TX and off for RX
[   18.816487] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   29.344040] eth0: no IPv6 routers present

```

EDiT2: It seems I have googled myself out of this one. Thanks for the help.

EDiT: I figured out what that cd src meant.
I went to the directory where I extracted the driver files(as instructed in the readme) and tried the "make" command and this is the error it gave:
```

make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/username/Documents/b44-1.00g modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/username/Documents/b44-1.00g/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/username/Documents/b44-1.00g] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [default] Error 2


```

---

