---
title: "Ubuntu 11.04 Natty - Sound Volume far lower than Lucid?"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by novelty07 on 2011-07-17
Hi All

Natty upgrade has driven me quite Nutty. So with that in mind here is the problem..

I used Lucid for about 9 months and the sound volume on my Sony Vaio was incredibly loud (in a good way). After I have upgraded to Natty 11.04 . The sound is there but it is quite low compared to the original. This laptop has some pretty solid (internal) speakers . So it should be able to pump up the volume.

Could someone help with this.

Thanks in advance for this.

Sony Vaio FJ-66GP-W (asia -pacific model)

---

### Post by SkippoGuangiacomo on 2011-07-17
did you check your system settings. It might be that the default volume of the audio was changed in the upgrading procedure. You should also check the volume of your notifications settings. 
HTH

---

### Post by novelty07 on 2011-07-17
hey there
if you mean have i gone to system settings and changed the volume. Yes I have all of it is set to almost max. Still no joy.

---

### Post by novelty07 on 2011-07-17
This is the output of lspci if it helps.
```
mickey@YO-VGN-FJ66GP-W:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:09.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:09.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:0a.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

```

Thanks

---

### Post by novelty07 on 2011-07-19
hello WORLD

Is there anyone out there, out there, out there...... Help Please

---

### Post by computerandu on 2011-07-19
> **novelty07 said:**
> hello WORLD

Is there anyone out there, out there, out there...... Help Please

Even I feel that the volume in Ubuntu is almost half of what I get in Windows 7...trying for quite a long time..still no solution...:(

---

### Post by Quackers on 2011-07-19
I must agree. In my Vaio the volume is significantly reduced over previous Ubuntu versions I think.

---

### Post by novelty07 on 2011-07-20
I would have thought the drivers were at problem (in windows) or the AC3 filter thing. But I am not sure how to work with drivers in ubuntu & do not want to lose whatever sound I do have.

So any thoughts about intel onboard HD sound drivers?

Thanks in advance.

---

### Post by kaloasd on 2011-07-20
VLC can go up to 200% volume

---

### Post by computerandu on 2011-07-20
> **kaloasd said:**
> VLC can go up to 200% volume

Yeah...but thats not the solution...vlc is not a good player for music...
we need to find the reason why is the volume so low in Ubuntu 11.04 as compared to Windows 7.....

---

### Post by novelty07 on 2011-07-20
Its true VLC can go upto 200%

But as a refernce point a particular avi file i used to play on vlc in lucid (10.10) was so loud that I had to reduce it down to 40-50%.

The same file in Natty when I play on VLC I have to crank it up to almost 200% and it its still not loud enough.

Also system startup sound which was incredibly loud in lucid sound like a stray cat meowing a mile away (more or less).

So there is something we are definitely missing

---

