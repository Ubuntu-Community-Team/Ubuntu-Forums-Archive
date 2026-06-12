---
title: "How to set up Hardy as an access point?"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by squeakysystem on 2008-06-15
Hi,

I'm trying to set up a machine with Ubuntu 8.04 as a wireless access point. I've got a PCI card with the Broadcom BCM4318 chips. I'm using the b43 driver and custom firmware, not ndiswrapper (could never get that to work).

I want to set it up as a wireless access point than connects through to my ISP via an ADSL modem, but when I get to "iwconfig wlan0 mode master" I receive an error.

Some people say this means the card doesn't support master mode, but I've also seen discussions on the linux wireless list that claim b43 *does* support master mode if some patches are applied to the kernel. Is this correct?

However, I can't find a clear step-by-step guide that explains how to actually do this, written for someone who has never modified a Linux kernel before. All the stuff on the Linux wireless list seems to be for developers working on the project.

Any pointers? URLs?

Thanks!

---

