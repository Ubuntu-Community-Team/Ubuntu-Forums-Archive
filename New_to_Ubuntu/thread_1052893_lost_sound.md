---
title: "lost sound"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by gj_clt on 2009-01-28
Just downloaded and installed latest updates and now have no sound from my sound blaster live . Any help appreciated.

---

### Post by gj_clt on 2009-01-28
Booted from the live cd and finding sound was working,booted from hd and no sound. Had a look at all the settings and everything seemed ok. Rebooted from  hd and sound works.

---

### Post by euopun on 2009-01-28
Theres some alsa command that restarts sound and everything... which version do you have installed?

---

### Post by sirdouglas on 2009-01-28
I have the same problem!  I have version 8.10, and absolutely no sound exists... except one time when I restarted I heard a loud beep, but that's it.  How do we resolve this?!

Thanks!

Doug

---

### Post by sproaty on 2009-01-28
me too, see here: [http://ubuntuforums.org/showthread.php?t=1053460](http://ubuntuforums.org/showthread.php?t=1053460)

what sound drivers do you have installed?

---

### Post by sirdouglas on 2009-01-28
I don't know which drivers I have. How do I find out?  

Doug

---

### Post by sirdouglas on 2009-01-29
Anybody?  I still haven't figured this out.:(

---

### Post by sirdouglas on 2009-02-06
... still no sound:(

---

### Post by DigiTan on 2009-02-06
Well...no one would answer my questions either, so I'll take a crack at this.  When you say you installed updates, exactly what where they?  Also, can you show us the output of **lshw -class multimedia**?

---

### Post by cjv8888 on 2009-02-06
The following commands may give you a few ideas

```
aplay -l
```

```
lspci -v
```

```
sudo modprobe snd-
```
use Tab key to find the right driver

Find the driver for your soundcard at
[http://www.alsa-project.org/alsa-doc/]("http://www.alsa-project.org/alsa-doc/")

---

### Post by sirdouglas on 2009-02-07
My update manager says the package was updated last 59 days ago, but I don't think that can be right because I have successfully gotten a few updates.  This is the error that appears when I try to update usually though: 

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.


And here's my terminal:
------------------------------------------------------------------------
sirdouglas@sirdouglas-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
sirdouglas@sirdouglas-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3080
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3080
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at b0000000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3080
	Flags: fast devsel
	Memory at 54000000 (32-bit, non-prefetchable) [disabled] [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
	Subsystem: Hewlett-Packard Company Device 3080
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
	Subsystem: Hewlett-Packard Company Device 3080
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
	Subsystem: Hewlett-Packard Company Device 3080
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
	Subsystem: Hewlett-Packard Company Device 3080
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 3080
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at b0040000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=0a, sec-latency=216
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: b0100000-b01fffff
	Prefetchable memory behind bridge: 0000000050000000-0000000053ffffff
	Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3080
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at b0040800 (32-bit, non-prefetchable) [size=512]
	Memory at b0040400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3080
	Flags: medium devsel, IRQ 20
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0m

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
	Subsystem: Hewlett-Packard Company Device 3080
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 3080
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3080
	Flags: medium devsel, IRQ 3
	I/O ports at 20a0 [size=32]
	Kernel modules: i2c-i801

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Hewlett-Packard Company Device 3080
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at 3000 [size=256]
	Memory at b0106000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp

06:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
	Subsystem: Hewlett-Packard Company Device 12f5
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at b0107000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ipw2200
	Kernel modules: ipw2200

06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
	Subsystem: Hewlett-Packard Company Device 3080
	Flags: bus master, medium devsel, latency 168, IRQ 20
	Memory at b0109000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
	Memory window 0: 50000000-53fff000 (prefetchable)
	Memory window 1: 58000000-5bfff000
	I/O window 0: 00003400-000034ff
	I/O window 1: 00003800-000038ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3080
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at b0106800 (32-bit, non-prefetchable) [size=2K]
	Memory at b0100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
	Subsystem: Hewlett-Packard Company Device 3080
	Flags: bus master, medium devsel, latency 57, IRQ 20
	Memory at b0104000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

06:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
	Subsystem: Hewlett-Packard Company Device 3080
	Flags: bus master, medium devsel, latency 57, IRQ 20
	Memory at b0108400 (32-bit, non-prefetchable) [size=256]
	Memory at b0108000 (32-bit, non-prefetchable) [size=256]
	Memory at b0106400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

sirdouglas@sirdouglas-laptop:~$ sudo modprobe snd-
FATAL: Module snd_ not found.

sirdouglas@sirdouglas-laptop:~$ lshw -class multimedia
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Multimedia audio controller
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1e.2
       bus info: pci@0000:00:1e.2
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0
sirdouglas@sirdouglas-laptop:~$ 


Thanks for the help!

Doug

---

### Post by cjv8888 on 2009-02-07
I found this bug report regarding your Intel ICH6 soundcard:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/276599]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/276599")

```
Solved: For others who may have this same problem, here is how I fixed it. If this helps you, please post to this thread so that the developers can accurately gauge the magnitude of this bug. Perhaps it was just my Gateway M250 laptop. To enable sound, downloaded and run the "gnome alsa mixer". You should see that "external amplifier" is checked as the default. Uncheck it to swtich to your internal amplifier and enable sound. Until I downloaded the "gnome alsa mixer" application, I had no way to see that the external amplifier setting was the default when ubuntu was loaded. Hopefully, the external amplifier selection will not be the default in future versions if others concur. Or perhaps this could be added to answers if there is good rational for the current default.
```

so try:

```
sudo apt-get install gnome-alsamixer
```

also check to see in the alsamixer to see if any of the volumes are muted.

---

### Post by sirdouglas on 2009-02-07
Thanks you so much!  It works.  Woohoo.  "External Amplifier" had been checked, so I unchecked, but there was still no sound.  But after tweaking with some of the volume bars it worked.  They can all just be put on max volume right?  I don't even know what some of that stuff is, like IEC958 P, Capture, Misc, but I'll keep them all turned up:D

Thanks for the help!

Doug

---

### Post by cjv8888 on 2009-02-07
Glad to hear your sound is working.

Not sure about your update errors though.

try

```
sudo apt-get update && sudo apt-get upgrade
```

If that does not work, then perhaps you can post a new thread about the errors to let others have a look.

---

### Post by diablo75 on 2009-02-07
HERE'S THE SOLUTION:

The latest kernel update SWITCHED the definition of the analog/digital check-box in the volume controls.  Open up your volume controls, find your analog/digital checkbox, and uncheck it.

Viola!  

This happened to me too.  I used google and found the original bug report about this which contained the solution.  Don't you wish you'd get a memo about stupid things like this, too?

---

