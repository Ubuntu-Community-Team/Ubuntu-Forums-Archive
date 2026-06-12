---
title: "no wireless with broadcom card using ndiswrapper"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by tmske on 2007-12-27
Hi,

I have a HP Compaq 6720s

wireless card:
Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

I tried to get my wireless working following this guide:
[Bcm43...]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

It didn't work so I tried with compiling ndiswrapper.  Now I have ndiswrapper 1.51.

```
dmesg | grep nidwrapper
[  311.667191] ndiswrapper version 1.51 loaded (smp=yes, preempt=no)
[  311.674271] usbcore: registered new interface driver ndiswrapper

```

But nothing showing anything about wlan0
Anyone an idea why this doesn't work?

Thanks

---

### Post by KCPokes on 2007-12-27
Did you install an actual driver with ndiswrapper?  I ask because your output shows that ndiswrapper is being loaded but not that actual driver you are trying to use.  For example, here is the same command on my machine:

```

dmesg | grep ndiswrapper
[   20.572000] ndiswrapper version 1.45 loaded (smp=yes)
[   20.940000] ndiswrapper: driver netrtuw (Realtek Semiconductor Corp.,01/29/2007,5.1279.0129.2007) loaded
[   23.240000] usbcore: registered new interface driver ndiswrapper

```

Post the output of "ndiswrapper -l".

---

### Post by tmske on 2007-12-27
yes, I have.

```
ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)
```

also I have blacklisted bcm43xx and not loaded it
and loaded ndiswrapper

```
lsmod | grep bcm

lsmod | grep ndis
ndiswrapper           192988  0
usbcore               145644  6 ndiswrapper,usbhid,ohci_hcd,ehci_hcd,uhci_hcd

```

---

