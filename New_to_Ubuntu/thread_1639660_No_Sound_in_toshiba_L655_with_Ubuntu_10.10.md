---
title: "No Sound in toshiba L655 with Ubuntu 10.10"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by Tr0Y_L33 on 2010-12-06
there is no sound in my toshiba series L655....
what must i do...????

this is my **lshw** info :
> 
*-multimedia UNCLAIMED  
       description: Audio device
       product: Redwood HDMI Audio [Radeon HD 5600 Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:d6020000-d6023fff
  *-multimedia UNCLAIMED
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d6100000-d6103fff


and this is for the ** lspci :**> 00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
02:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02) 

HELP ME PLEASE

---

### Post by canucked on 2010-12-09
Tr0Y_L33: I recently configured a Toshiba Satellite L655-S5115 for a friend.  This is what I did to fix the non-functional built-in microphone, microphone jack, and headphone jack.  (The built-in speakers worked fine.)

Running this in Terminal:
```
cat /proc/asound/card0/codec#* | grep Codec
```

...revealed that the audio is Conexant CX20585.

To fix the audio, I did this:
Edit /etc/modprobe.d/alsa-base.conf and add:
```
options snd-hda-intel model=thinkpad
```

I provide more detail in a thread I started about that laptop:
[http://ubuntuforums.org/showthread.php?t=1641931](http://ubuntuforums.org/showthread.php?t=1641931)

Hope this works for you!

---

