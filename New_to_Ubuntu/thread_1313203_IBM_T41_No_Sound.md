---
title: "IBM T41 No Sound"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by coldReactive on 2009-11-03
Yes, there's no sound in Xubuntu 9.10 for the famous IBM T41 Laptop. I got this laptop recently, hoping I'd never need another laptop again. Please help me to get sound working.

LSPCI
```
ian@ian-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
```

---

### Post by LowSky on 2009-11-03
Dumb question but have you check the sound preferences to make sure its not muted or set wrong?

---

### Post by coldReactive on 2009-11-03
> **LowSky said:**
> Dumb question but have you check the sound preferences to make sure its not muted or set wrong?

Nothing is muted except for sound input (since I have no mic, etc.)

---

### Post by coldReactive on 2009-11-03
Wow, that was... weird.

Pressing the UP Volume button (at the top of the keyboard) solved the issue. o_O

---

