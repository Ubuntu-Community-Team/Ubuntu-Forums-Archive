---
title: "Pls explain  on my boot log error????"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by migrate from windows on 2011-01-26
I have installed ubuntu 10.10 in my desktop with VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

By default the VESA driver is enabled (No 3d or acceleration) Whenever I try to manually enable the intel driver by editing the xorg.conf file the system boots only to text mode (ctrl+alt+f7) also does not give GUI. This is the error i see in the boot llog  pleas etell me what it means.

.....................

[    20.453] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    20.453] (II) Module intel: vendor="X.Org Foundation"
[    20.453]     compiled for 1.9.0, module version = 2.14.0
[    20.453]     Module class: X.Org Video Driver
[    20.453]     ABI class: X.Org Video Driver, version 8.0
[    20.453] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    20.454] (--) using VT number 7

[    20.472] (EE) No devices detected.
[    20.472] 
Fatal server error:
[    20.472] no screens found
[    20.472] 


Pls help

---

### Post by cariboo on 2011-01-26
I'd suggest you remove the /etc/X11/xorg.conf file and reboot, you shouldn't need one. Once you are at the desktop, open a terminal and check to see if the i915 driver has been loaded:

```
lsmod | grep i915
``` 

If it isn't, you can load it using the following command:

```
sudo modprobe i915
```

if the module loads successfully, you won't see anything echoed back. You may have to reboot after loading the module.

---

### Post by migrate from windows on 2011-01-27
> **cariboo907 said:**
> I'd suggest you remove the /etc/X11/xorg.conf file and reboot, you shouldn't need one. Once you are at the desktop, open a terminal and check to see if the i915 driver has been loaded:

```
lsmod | grep i915
```If it isn't, you can load it using the following command:

```
sudo modprobe i915
```if the module loads successfully, you won't see anything echoed back. You may have to reboot after loading the module.

This is the response????

srikanth@srikanth-desktop:~$ sudo modprobe i915
[sudo] password for srikanth: 
WARNING: Error inserting i2c_algo_bit (/lib/modules/2.6.35-24-generic/kernel/drivers/i2c/algos/i2c-algo-bit.ko): No such device
WARNING: Error inserting agpgart (/lib/modules/2.6.35-24-generic/kernel/drivers/char/agp/agpgart.ko): No such device
WARNING: Error inserting intel_agp (/lib/modules/2.6.35-24-generic/kernel/drivers/char/agp/intel-agp.ko): No such device
WARNING: Error inserting drm (/lib/modules/2.6.35-24-generic/kernel/drivers/gpu/drm/drm.ko): No such device
WARNING: Error inserting drm_kms_helper (/lib/modules/2.6.35-24-generic/kernel/drivers/gpu/drm/drm_kms_helper.ko): No such device
FATAL: Error inserting i915 (/lib/modules/2.6.35-24-generic/kernel/drivers/gpu/drm/i915/i915.ko): No such device

---

