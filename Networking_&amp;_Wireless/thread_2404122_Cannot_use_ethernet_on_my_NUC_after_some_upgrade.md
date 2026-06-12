---
title: "Cannot use ethernet on my NUC after some upgrade"
date: 2018-10-20
forum: Networking &amp; Wireless
---

### Post by pbidkar on 2018-10-20
I was able to use the ethernet of my NUC running Ubuntu 18.04 for a few days. but for the last 2 days it is not working.
I have searched the not for a solution but non work.
I have downloaded e100e driver source and compiled it.

```

Ganapati:pbidkar:47:~/Downloads/e1000e-3.4.2.1/src >sudo modprobe -v e1000e
insmod /lib/modules/4.15.0-36-generic/updates/drivers/net/ethernet/intel/e1000e/e1000e.ko 
modprobe: ERROR: could not insert 'e1000e': Unknown symbol in module, or unknown parameter (see dmesg)
Ganapati:pbidkar:48:~/Downloads/e1000e-3.4.2.1/src >

Ganapati:pbidkar:49:~/Downloads/e1000e-3.4.2.1/src >dmesg | grep e100
[    1.148920] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    1.148921] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    1.172302] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    2.052180] e1000e: probe of 0000:00:19.0 failed with error -2
[ 2292.941588] e1000e: loading out-of-tree module taints kernel.
[ 2292.941941] e1000e: module verification failed: signature and/or required key missing - tainting kernel
[ 2292.942165] e1000e: Unknown symbol mcount (err 0)
[ 2473.161959] e1000e: Unknown symbol mcount (err 0)
[ 2770.803530] e1000e: Unknown symbol mcount (err 0)
[ 4515.894542] e1000e: Unknown symbol mcount (err 0)
[ 6464.810326] e1000e: Unknown symbol mcount (err 0)

```

How can I get this wired net working ?

NOTE wireless net is working.

Thanks in advance

BR
Pravin

---

### Post by chili555 on 2018-10-20
We see this in your dmesg:

```
e1000e: probe of 0000:00:19.0 failed with error -2

```
It is highly debatable whether a newer driver would fix the error. Also, we hope that is we fix that error, it will fix the susequent errors as well.

```
e1000e: Unknown symbol mcount (err 0)
```

Did the 3.4.2.1 version get installed correctly?

```
modinfo e1000e | grep version
```

If so, since it won’t load without error, I suggest that you uninstall it:

```
~/Downloads/e1000e-3.4.2.1/src
sudo make uninstall
sudo modprobe -r e1000e && sudo modprobe e1000e
```

Check:

```
modinfo e1000e | grep version
```

We hope it is back to 3.2.6-k.

This suggests that the issue is wake-on-lan: [https://www.whtop.com/blog/e1000e-probe-failed-with-error-2/](https://www.whtop.com/blog/e1000e-probe-failed-with-error-2/)

> Now, disable in BIOS any wake on Lan (or boot from Lan ..

I also suggest that you be certain that your NUC uses the latest BIOS.

---

### Post by pbidkar on 2018-10-20
Thanks chili555 for looking into my issue.

```

Ganapati:pbidkar:51:~/Downloads/e1000e-3.4.2.1/src >sudo make uninstall
if [ -e /lib/modules/4.15.0-36-generic/updates/drivers/net/ethernet/intel/e1000e/e1000e.ko ] ; then \
    rm -f /lib/modules/4.15.0-36-generic/updates/drivers/net/ethernet/intel/e1000e/e1000e.ko ; \
fi
/sbin/depmod -a
if [ -e /usr/share/man/man7/e1000e.7.gz ] ; then \
    rm -f /usr/share/man/man7/e1000e.7.gz ; \
fi

Ganapati:pbidkar:52:~/Downloads/e1000e-3.4.2.1/src >sudo modprobe -r e1000e && sudo modprobe e1000e
modprobe: FATAL: Module e1000e not found.

Ganapati:pbidkar:55:~/Downloads/e1000e-3.4.2.1/src >sudo make install
make -C /lib/modules/4.15.0-36-generic/build CC=gcc SUBDIRS=/home/pbidkar/Downloads/e1000e-3.4.2.1/src modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-36-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "mcount" [/home/pbidkar/Downloads/e1000e-3.4.2.1/src/e1000e.ko] undefined!
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-36-generic'
# remove all old versions of the driver
find /lib/modules/4.15.0-36-generic -name e1000e.ko -exec rm -f {} \; || true
find /lib/modules/4.15.0-36-generic -name e1000e.ko.gz -exec rm -f {} \; || true
install -D -m 644 e1000e.ko /lib/modules/4.15.0-36-generic/updates/drivers/net/ethernet/intel/e1000e/e1000e.ko
/sbin/depmod -a 4.15.0-36-generic || true
install -D -m 644 e1000e.7.gz /usr/share/man/man7/e1000e.7.gz
man -c -P'cat > /dev/null' e1000e || true
man: 
cannot write to /var/cache/man/cat7/e1000e.7.gz in catman mode
e1000e.

Ganapati:pbidkar:56:~/Downloads/e1000e-3.4.2.1/src >modinfo e1000e | grep version
version:        3.4.2.1-NAPI
srcversion:     E5F32C887AD994C0D1E3F43


```

BIOS is latest as I am using this NUC for 2+ years first with 16.04 and from a month back with 18.04
I will try the BIOS setting after this.

BR 
Pravin

---

### Post by chili555 on 2018-10-20
> Ganapati:pbidkar:56:~/Downloads/e1000e-3.4.2.1/src >modinfo e1000e | grep version
version:        3.4.2.1-NAPI
srcversion:     E5F32C887AD994C0D1E3F43It appears that the driver *was* installed successfully. Does it load without error or with any interesting clues:```
sudo modprobe e1000e
dmesg | grep e100
```

---

### Post by pbidkar on 2018-10-21
Thanks for you reply.

Module does get install correctly. 

```

Ganapati:pbidkar:14:~ >sudo modinfo e1000e | grep ver
filename:       /lib/modules/4.18.0-041800-generic/updates/drivers/net/ethernet/intel/e1000e/e1000e.ko
version:        3.4.2.1-NAPI
description:    Intel(R) PRO/1000 Network Driver
srcversion:     649A00099E603CB6BB114F6
vermagic:       4.18.0-041800-generic SMP mod_unload 

```

After reboot it some how still loads ver 3.2.6-k instead of 3.4.2.1-NAPI
I am not sure where it is getting this module.
Is it compiled in the kernel ?

```

Ganapati:pbidkar:15:~ >dmesg | grep e1000e
[    1.376329] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    1.376330] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    1.376969] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    2.256160] e1000e: probe of 0000:00:19.0 failed with error -2

```

I have upgraded the BIOS to the latest.
I have upgrade the kernel to 4.18.0
Wake on LAN was already disabled.

BR
Pravin

---

### Post by dino99 on 2018-10-21
Have you made a fresh install or a dist-upgrade ?
In case of dist-upgrade, then think to purge orphans with: autoremove, gtkorphan, bleachbit (as root, carefully select features)

---

### Post by chili555 on 2018-10-22
> I am not sure where it is getting this module.
Is it compiled in the kernel ?Yes, exactly.

Please try unloading the in-kernel version:```
sudo modprobe -r e1000e
```Locate the later compiled version:```
sudo updatedb
locate e1000e.ko
```I suspect it is in ~/Downloads/e1000e-3.4.2.1/src. See if you can load it instead:```
 cd ~/Downloads/e1000e-3.4.2.1/src 
```...or wherever you found it.```
sudo insmod e1000e.ko
```Check the log:```
dmesg | grep e100
```You should see the module load with a newer timestamp, newer than on boot here:> [    1.376329] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    1.376330] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    1.376969] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    [COLOR="#FF0000"]2.256160[/COLOR]] e1000e: probe of 0000:00:19.0 failed with error -2Is the 'probe failed' error still present or not?

---

### Post by pbidkar on 2018-10-22
Yes the probe error is still present.

Does it mean a real hardware issue ?

```

dmesg | grep e1000
[    1.445664] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    1.445665] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    1.445905] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    2.312151] e1000e: probe of 0000:00:19.0 failed with error -2
[  330.019223] e1000e: loading out-of-tree module taints kernel.
[  330.019406] e1000e: module verification failed: signature and/or required key missing - tainting kernel
[  330.021556] e1000e: Intel(R) PRO/1000 Network Driver - 3.4.2.1-NAPI
[  330.021557] e1000e: Copyright(c) 1999 - 2018 Intel Corporation.
[  330.021895] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[  330.902795] e1000e: probe of 0000:00:19.0 failed with error -2
[  387.243422] e1000e: Intel(R) PRO/1000 Network Driver - 3.4.2.1-NAPI
[  387.243423] e1000e: Copyright(c) 1999 - 2018 Intel Corporation.
[  387.243676] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[  388.130827] e1000e: probe of 0000:00:19.0 failed with error -2

```

BR
Pravin

---

### Post by chili555 on 2018-10-23
> Does it mean a real hardware issue ?That's about all there is left to suspect. 

I haven't looked around the BIOS/EFI of my older NUC is a while to see if there are any settings aside from Wake on LAN that may have an effect, but mine boots and connects normally, also using e1000e, with no unusual settings. Sorry.

There are a number of inexpensive USB to ethernet adapters that you might try or, of course, you could simply use the working wireless.

---

### Post by pbidkar on 2018-11-02
Thanks

I think it is a hardware issue.

I am using the WiFi currently but will look into USB -> Ethernet adapter.

BR 
Pravin

---

