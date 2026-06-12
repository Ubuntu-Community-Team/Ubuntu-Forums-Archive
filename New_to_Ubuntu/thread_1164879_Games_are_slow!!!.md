---
title: "Games are slow!!!"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by sharks on 2009-05-20
I have been playing games on window$ and they are fine . But when i installed games on Ubuntu(not through wine and supported by ubuntu) they are slow. The acceleration isnt good enough.. Its the same with Google Earth. I dont have a graphic card. Whats the prob? The specs are for the games are more compatible with my system specs.

---

### Post by skymera on 2009-05-20
What graphics chip do you have?
What version of Ubuntu are you running?

---

### Post by sharks on 2009-05-20
I use Intel processor which is quite fast and good with integrated graphics card. I use Intrepid Ibex. I have been updating every time.

---

### Post by skymera on 2009-05-20
> **sharks said:**
> I use Intel processor which is quite fast and good with integrated graphics card. I use Intrepid Ibex. I have been updating every time.

Trying to think of the right command now :P
Can you post the output of:

```
 lspci 
```

---

### Post by jordanmthomas on 2009-05-20
Odds are OP has an integrated Intel graphics.  While Intel is usually pretty awesome about having good free drivers, the current state of graphics is in a bit of disarray.  Hopefully soon, the performance that the old drivers had will be back.  I dual boot Arch Linux and Exherbo, and luckily someone packaged up the old drivers for Arch so I can still play games if I boot up Arch.

You can read more about what's up with Intel graphics here:
[http://keithp.com/blogs/Sharpening_the_Intel_Driver_Focus/](http://keithp.com/blogs/Sharpening_the_Intel_Driver_Focus/)

---

### Post by skymera on 2009-05-20
I thought it may be Intel, but it could be an old ATi.

If you have Intel this should work:
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

If you have ATi you need to use the open-source driver

---

### Post by sharks on 2009-05-20
Lspci result :
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751F Fast Ethernet PCI Express (rev 11)
0a:00.0 Communication controller: Conexant Systems, Inc. Device 2702 (rev 01)

---

### Post by clhsharky on 2009-05-20
Check in Multimedia section there a good sticky for intel cards

---

### Post by Mark Phelps on 2009-05-20
If you find anything useful, please report back.  Like you, I have the infamous "915" Intel chipset and, there aren't even real Vista drivers for it, let alone accelerated drivers. I'm using the ones that Ubuntu installed by default.

---

