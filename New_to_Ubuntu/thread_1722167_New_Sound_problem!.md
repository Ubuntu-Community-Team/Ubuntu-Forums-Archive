---
title: "New Sound problem!"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by Mike1962 on 2011-04-05
Now I've got all my sound cards working a really strange thing happened this afternoon that I've not experienced before.
I finally reconnected my amp, eq and monitors. 
There is a noise that is coming from the on-board sound card that sounds like old fashioned static on a valve radio, including a 'swirling' noise. It seems to be intermittent as to when it starts but once started it doesn't go away. It starts sometimes when I move the mouse!! Starts with a few crackles like a dirty volume pot on an amp, then goes into the static and swirling.
I also have XP on the machine and it's fine on that side of things.
I have the output of the sound card in to a patch bay then routed either to amp or a headphone amp yesterday it was fine. Now the noise is on the headphone as well, so not an out -board problem.
I tried unplugging the  amp, eq and monitors and no change. 


Cheers

Mike

---

### Post by Mike1962 on 2011-04-06
OK. 
Just switched on and it was about 5 mins before if started being noisey.  Without touching the mouse!!

---

### Post by khelben1979 on 2011-04-06
What sound card do you have installed? ```
lspci
``` will tell us.

---

### Post by Mike1962 on 2011-04-25
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
04:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
05:01.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
05:01.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
05:02.0 USB Controller: NEC Corporation USB (rev 41)
05:02.1 USB Controller: NEC Corporation USB (rev 41)
05:02.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
05:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:04.0 Mass storage controller: Integrated Technology Express, Inc. ITE 8211F Single Channel UDMA 133 (rev 11)
0a:00.0 Multimedia audio controller: Xilinx Corporation RME Hammerfall DSP (rev 11)

---

