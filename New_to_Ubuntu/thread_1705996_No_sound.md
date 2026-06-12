---
title: "No sound"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by Themiband on 2011-03-13
So i've got no sound at the moment, and never do have any sound when i boot up in Ubuntu does anybody know why this would be

themiband@Themiband80-00:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc R423 UK [Radeon X800SE (PCIE)]
01:00.1 Display controller: ATI Technologies Inc Radeon R423 UK (PCIE) [X800 SE] (Secondary)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by Dutch70 on 2011-03-13
[[COLOR="Blue"]https://help.ubuntu.com/community/SoundTroubleshooting[/COLOR]]("https://help.ubuntu.com/community/SoundTroubleshooting")
_

---

### Post by Themiband on 2011-03-13
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Packard Bell B.V. Device e011
        Flags: bus master, fast devsel, latency 0, IRQ 42
        Memory at f0100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

ok so this is my audio device thingy right? i've checked the other steps and there doesn't seem to be any problems there so it looks like maybe my sound card isn't supported by ALSA?

---

### Post by Themiband on 2011-03-13
hmmm  okay so hda-intel isn't in the list but this thread looks like it might help 

[http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)

---

