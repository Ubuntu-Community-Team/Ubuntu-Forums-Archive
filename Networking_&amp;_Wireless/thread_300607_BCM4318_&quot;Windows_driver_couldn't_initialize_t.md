---
title: "BCM4318 &quot;Windows driver couldn't initialize the device (C0000001)&quot;"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by Bentley on 2006-11-15
Hello all,

I'm running x86_64 Etch, and am hoping someone can help me with getting ndiswrapper to work with my network card:

```
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 1355
        Flags: fast devsel, IRQ 177
        Memory at c0204000 (32-bit, non-prefetchable) [size=8K]
```

I'm using ndiswrapper-utils-1.8. I've blacklisted bcm43xx. I have the 64 bit windows drivers.

```
$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present
```

When I check dmesg, I see:

```
[   39.477454] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[   39.577666] ndiswrapper (load_pe_images:573): fixing KI_USER_SHARED_DATA address in the driver
[   39.578721] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[   39.586688] ndiswrapper (NdisWriteErrorLogEntry:241): log: 6F20F9B0, count: 1, return_address: ffffffff883cf13e
[   39.586694] ndiswrapper (NdisWriteErrorLogEntry:244): code: 267
[   39.586770] ndiswrapper (miniport_init:264): couldn't initialize device: C0000001
[   39.586778] ndiswrapper (pnp_start_device:428): Windows driver couldn't initialize the device (C0000001)
[   39.586798] ndiswrapper (miniport_halt:327): device ffff81006dbb6500 is not initialized - not halting
[   39.586807] ndiswrapper: device eth%d removed
[   39.586838] ndiswrapper: probe of 0000:05:02.0 failed with error -22

```


I've used ndiswrapper successfully in the past (with other laptops). I just can't seem to get this particular laptop working - it's driving me up the wall ](*,) .  Any help would be appreciated.

Thanks
Bentley

---

### Post by het.idee on 2006-11-20
I had exactly the same problem you have. 
I solved it by installing ndiswrapper from source ([https://help.ubuntu.com/community/WifiDocs/NdiswrapperOnAMD64](https://help.ubuntu.com/community/WifiDocs/NdiswrapperOnAMD64))

I'm posting this with my wireless connection now :)

---

