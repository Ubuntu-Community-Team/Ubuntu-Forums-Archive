---
title: "I can't get my wireless card to work!"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by ArnsteinK on 2009-01-02
I can't get wireless internett on my computer. I got a Packard Bell Easy Note A5, with Ubuntu 8.04! What can I do to get wireless internet? It really bugs me because the only thing that doesn't work on this computer now is wireless internet.

---

### Post by LowSky on 2009-01-02
open a terminal and type

```
lspci
```

then copy and paste the results here. this will tell us the model of the wireless card

---

### Post by ArnsteinK on 2009-01-02
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller

---

### Post by ArnsteinK on 2009-01-02
Anyone?

---

### Post by ArnsteinK on 2009-01-02
Is there no way I can fix this?

---

### Post by handydan918 on 2009-01-02
> **ArnsteinK said:**
> Is there no way I can fix this?

A quick google shows there are no native linux drivers for this card yet. You will have to use ndiswrapper and a windows xp driver. Vista drivers will not work, AFAIK. Neither will 64bit.

---

### Post by Michael.Godawski on 2009-01-02
hi,

try to use ndiswrapper as described here:


[LIST]
[*][http://godawski.oxyhost.com/solvingwireless.html](http://godawski.oxyhost.com/solvingwireless.html)
[/LIST]
 
and have a look at the site

[LIST]
[*]_ _[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[/LIST]
 
Just search there for a guide, we will see if there is a solution for your card and if we can assist you somehow.

---

### Post by ArnsteinK on 2009-01-02
> **handydan918 said:**
> A quick google shows there are no native linux drivers for this card yet. You will have to use ndiswrapper and a windows xp driver. Vista drivers will not work, AFAIK. Neither will 64bit.

Thanks! It worked, but I still have to write in the network name manually! How can I fix it so that I can see the networks I can connect to?

---

### Post by handydan918 on 2009-01-02
Try installing wicd. It seems to help with a lot of wireless issues.

---

### Post by ArnsteinK on 2009-01-02
Thanks, worked :D

---

### Post by ArnsteinK on 2009-01-02
Update: It didn't work :p 

When I restarted it still didn't find any networks!

---

### Post by nothingspecial on 2009-01-02
No garuntee

Try ```
sudo modprobe ndiswrapper
```

---

### Post by ArnsteinK on 2009-01-02
Didn't work I'm afraid :(

---

