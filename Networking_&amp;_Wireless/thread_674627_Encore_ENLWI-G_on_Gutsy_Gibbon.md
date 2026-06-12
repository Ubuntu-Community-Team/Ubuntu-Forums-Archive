---
title: "Encore ENLWI-G on Gutsy Gibbon"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by ishkabibble on 2008-01-21
Running a Intel Celeron D CPU 3.06GHz and trying to install a wireless adapter.  I've gone thru all the HowTos I can find.  lspci shows the device is there.  Windows Wireless Drivers shows the appropriate driver is loaded and hardware is found.  When I check tail -f /var/log/messages it shows:
```
Jan 21 21:42:22 elmo kernel: [  985.478552] ndiswrapper: using IRQ 11
Jan 21 21:42:23 elmo kernel: [  986.281141] ndiswrapper (mp_init:263): couldn't initialize device: C0000001
Jan 21 21:42:23 elmo kernel: [  986.281153] ndiswrapper (pnp_start_device:440): Windows driver couldn't initialize the device (C0000001)
Jan 21 21:42:23 elmo kernel: [  986.281170] ndiswrapper (mp_halt:305): device f5e5d500 is not initialized - not halting
Jan 21 21:42:23 elmo kernel: [  986.281180] ndiswrapper: device eth%%d removed
Jan 21 21:42:23 elmo kernel: [  986.281201] ACPI: Unable to derive IRQ for device 0000:04:04.0
Jan 21 21:42:23 elmo kernel: [  986.281213] ndiswrapper: probe of 0000:04:04.0 failed with error -22
```
Neither ifconfig nor iwconfig shows a wireless connection. 

What am I doing wrong?

---

### Post by ishkabibble on 2008-01-22
Nonne has any ideas?

---

