---
title: "[SOLVED] usb not recognized"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by vbn_newbie on 2007-12-18
Hi,
I have a netgear wg111v2 dongle. I tried installing the driver. ndiswrapper said the driver had been installed, but didn't find the hardware. i tried lsusb and i get

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000

The last lines of the output of dmesg are

[83795.192002] BUG: at drivers/usb/core/driver.c:1166 usb_autopm_do_device()
[83795.192032]  [<e0881255>] usb_autopm_do_device+0xd5/0xe0 [usbcore]
[83795.192079]  [<e08877d5>] usbdev_release+0x75/0xc0 [usbcore]
[83795.192106]  [<c0177747>] __fput+0xa7/0x190
[83795.192135]  [<c0174ae7>] filp_close+0x47/0x80
[83795.192150]  [<c0175e4b>] sys_close+0x6b/0xd0
[83795.192161]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[83795.192208]  =======================

Can some one tell me what's going on?

System info : Feisty Fawn (Ubuntu 7.04). 
Kernel: 2.6.20-15-generic

Let me know if anything else is needed?

Thanks!
VBN:confused:

---

### Post by vbn_newbie on 2007-12-20
i upgraded to ubuntu  7.10 and the usb port is now recognized. in fact, the netgear dongle worked straightaway without me having to ndiswrapper the driver.

---

