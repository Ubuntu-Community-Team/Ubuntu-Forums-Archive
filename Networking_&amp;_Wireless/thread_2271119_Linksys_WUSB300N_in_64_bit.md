---
title: "Linksys WUSB300N in 64 bit?"
date: 2015-03-27
forum: Networking &amp; Wireless
---

### Post by stchman on 2015-03-27
I have a Linksys WUSB300N USB wireless adapter.  I have tried to get it to work on Ubuntu 14.04 64 bit but with no success.

The Windows driver works perfectly in 32 bit but not 64 bit.  Using ndiswrapper in 32 bit Ubuntu using the NdisGTK is a snap.

Is there a 64 bit driver for this adapter or should I just try a different adapter?

Thanks.

---

### Post by chili555 on 2015-03-27
> **stchman said:**
> I have a Linksys WUSB300N USB wireless adapter.  I have tried to get it to work on Ubuntu 14.04 64 bit but with no success.

The Windows driver works perfectly in 32 bit but not 64 bit.  Using ndiswrapper in 32 bit Ubuntu using the NdisGTK is a snap.

Is there a 64 bit driver for this adapter or should I just try a different adapter?

Thanks.Please run and post:```
arch
lsusb
```Thanks.

---

### Post by stchman on 2015-03-27
arch
```

x86_64

```

lsusb
```

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13b1:0029 Linksys WUSB300N 802.11bgn Wireless Adapter [Marvell 88W8362+88W8060]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by chili555 on 2015-03-27
So far, so good. Let's have a look at:```
dmesg | grep ndis
ndiswrapper -l
```That's a lower-case L for 'list.'

I believe some Windows .inf files are architecture agnostic; that is, they work with either 32- or 64-bit. I know for certain that others are not.

If your driver works perfectly, as you said, why are you interested in something different?

---

### Post by stchman on 2015-03-27
> **chili555 said:**
> So far, so good. Let's have a look at:```
dmesg | grep ndis
ndiswrapper -l
```That's a lower-case L for 'list.'

I believe some Windows .inf files are architecture agnostic; that is, they work with either 32- or 64-bit. I know for certain that others are not.

If your driver works perfectly, as you said, why are you interested in something different?

dmesg | grep ndis
```

[   13.265417] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   13.266214] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   13.490127] usbcore: registered new interface driver ndiswrapper
[   65.846162] usbcore: deregistering interface driver ndiswrapper
[   65.851033] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   66.099662] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   66.099666] ndiswrapper (load_sys_files:200): couldn't prepare driver 'netmw245'
[   66.099908] ndiswrapper (load_wrap_driver:103): couldn't load driver netmw245; check system log for messages from 'loadndisdriver'
[   66.099951] usbcore: registered new interface driver ndiswrapper
[  122.665744] usbcore: deregistering interface driver ndiswrapper
[  122.674197] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  122.927928] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  122.927934] ndiswrapper (load_sys_files:200): couldn't prepare driver 'netmw245'
[  122.928272] ndiswrapper (load_wrap_driver:103): couldn't load driver netmw245; check system log for messages from 'loadndisdriver'
[  122.928318] usbcore: registered new interface driver ndiswrapper

```

ndiswrapper -l
```

netmw245 : driver installed
    device (13B1:0029) present

```

Reason being the netmw245.inf file works in 32 bit Ubuntu 14.04 but does not work in 64 bit.

---

### Post by chili555 on 2015-03-28
I have been unable to find any 64-bit files. Unless you wish to replace the device with some other, better supported device, I suggest you stick with a 32-bit installation.

---

### Post by stchman on 2015-03-28
> **chili555 said:**
> I have been unable to find any 64-bit files. Unless you wish to replace the device with some other, better supported device, I suggest you stick with a 32-bit installation.

I kind of figured the same thing.  It seems Linksys is no longer supporting that device.  I will get another adapter.

Thank you for looking.

---

