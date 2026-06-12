---
title: "Graphics Card Driver Issues"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by sideffects on 2009-08-28
Last month I plugged my laptop into my HDTV via an S-Video cable, and then a VGA cable, and used extended desktop. After, I was having tons of trouble getting my resolution back. The highest resolution it would let me use was 1024x768. After some struggle, I got it working (although, I don't remember what I did exactly.) Now, it's back to 1280x800, which is where I like it. I don't know how much of that will help with my question, but I can't use desktop effects now, and it says that no proprietary drivers are in use, and there is not one to select. I know I used to use one for my graphics card. Can anyone tell me how to fix this and/or get my proprietary driver back? Thanks!

---

### Post by utnubuuser on 2009-08-28
specs?  What card?

Post the output of > lspcifrom a terminal.

---

### Post by sideffects on 2009-08-28
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by gradinaruvasile on 2009-08-28
> **sideffects said:**
> 
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)


I dont think there are restricted drivers for that card. Linux has its open source drivers included for intel cards.

---

### Post by sideffects on 2009-08-28
Well, I used to use desktop effects just fine, but now I can't. Is there a fix?

---

### Post by Xnst on 2009-08-28
It could be xorg.conf have been changed, or something like that. To reset graphics issues there is a recommendation in the xorg.conf to run dpkg-reconfigure.

Be sure to backup your xorg.conf file first
```

$> cd /etc/X11
$> sudo cp xorg.conf xorg.conf.backup
$> sudo dpkg-reconfigure -phigh xserver-xorg
```

It could work, but if it doesn't it is easy to redo.

---

### Post by sideffects on 2009-08-28
> **Xnst said:**
> It could be xorg.conf have been changed, or something like that. To reset graphics issues there is a recommendation in the xorg.conf to run dpkg-reconfigure.

Be sure to backup your xorg.conf file first
```

$> cd /etc/X11
$> sudo cp xorg.conf xorg.conf.backup
$> sudo dpkg-reconfigure -phigh xserver-xorg
```It could work, but if it doesn't it is easy to redo.
Didn't work. Tried it though. I'll mess around with my xorg.conf file and see what I can do. If anyone else has any ideas though...

---

### Post by sideffects on 2009-09-12
Anyone?

---

