---
title: "Display problems with ubuntu 11.04"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by Phrostbite on 2011-06-06
I did a fresh install of Ubuntu 11.04 on my dell Inspiron 6000 and I have this crazy display problem where the best way I can explain it is a 1x1 pixel haze type of thing over everything.

Here is a screenshot that I hope can further explain what I am talking about. I went to the dirver section int he options and there are no proprietary drivers that I can install either. Any help would be appreciated.

[[IMG]http://img143.imageshack.us/img143/1293/displayproblem.png[/IMG]](http://img143.imageshack.us/i/displayproblem.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by seawolf167 on 2011-06-06
Is your resolution set to the highest possible resolution supported by your hardware?

Can you post the output of 

```
lspci
```

You may have the option of installing proprietary graphics drivers.

---

### Post by Phrostbite on 2011-06-06
Here is the output.

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
```

My resolution is at 1280 X 800

---

### Post by seawolf167 on 2011-06-06
It looks like 1280x800 is your native screen resolution. The graphics card you have, Mobility Radeon X300, has moved to legacy support by AMD, so you are already running with it fully configured.

I think the "fuzziness" is just because it is displaying everything at a low [relative to modern cards] resolution.

---

### Post by Phrostbite on 2011-06-06
So does that mean there is nothing I can do to fix this?

---

### Post by seawolf167 on 2011-06-06
Someone else may have an idea, solution or have seen this before and have a better idea what is going on - I'd wait for more responses before you give up!

---

### Post by Phrostbite on 2011-06-06
Thank you for looking into it :)

---

### Post by Phrostbite on 2011-06-07
Ok so don't ask me why this worked. I spent all day upgrading to 11.04 from 10.04 rather than doing a clean install right into 11.04. I am not sure why it worked but it did. Clean install of 10.04 then upgraded via ubuntu update to 10.10 then again to 11.04 and works perfect.

---

### Post by seawolf167 on 2011-06-07
Regardless of how you got there - glad it worked!

---

### Post by Phrostbite on 2011-06-07
Well it would seem it didn't work after i rebooted it came back :(.

---

