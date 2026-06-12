---
title: "Editing Wireless Drivers"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by josephst18 on 2008-10-31
Will installing new wireless drivers/ changing drivers for Broadcom 4306 in Ubuntu 8.10 make the wireless driver in Windows XP stop working? I plan to use Wubi to make a dual boot, and want to know if this will mess anything up before doing it. I also have a static IP address on my home network, and wanted to know if Ubuntu supports have a static IP address on my home network.

---

### Post by Ayuthia on 2008-10-31
> **josephst18 said:**
> Will installing new wireless drivers/ changing drivers for Broadcom 4306 in Ubuntu 8.10 make the wireless driver in Windows XP stop working? I plan to use Wubi to make a dual boot, and want to know if this will mess anything up before doing it. I also have a static IP address on my home network, and wanted to know if Ubuntu supports have a static IP address on my home network.

So far, there has not been any reports on this happening with the Broadcom cards.  The drivers are just talking to the wireless card so it should not affect Windows at all.  The open source driver for the Broadcom card does require a firmware file to make it work.  However, it is just taking some information from the firmware to make the driver work.  It is not altering the card as far as I know.

Just to let you know, I have a laptop with a Broadcom 4311 card using various versions of Linux along with Vista (still need it for BIOS updates) and I also have a laptop with a 4306 card that is using Hardy in Wubi and it has XP.  The wireless card has never had any problems on either Linux or Windows.

---

