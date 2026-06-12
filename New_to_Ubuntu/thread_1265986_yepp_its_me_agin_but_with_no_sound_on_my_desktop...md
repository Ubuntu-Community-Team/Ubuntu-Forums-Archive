---
title: "yepp its me agin but with no sound on my desktop..."
date: 2009-09-14
forum: New to Ubuntu
---

### Post by I WILL DO IT on 2009-09-14
i reinstall ubuntu on my desktop b/c i installed a but lode of programs from the synaptic and had some problems from itt....\

when i reinstall it theres no sound!!!!

---

### Post by nothingspecial on 2009-09-14
Yepp it`s me again too.

And once again you have to post your info

```
aplay -l
```

---

### Post by I WILL DO IT on 2009-09-14
cool@cool-desktop:~$ aplay -l
aplay: device_list:217: no soundcards found...
cool@cool-desktop:~$

---

### Post by nothingspecial on 2009-09-14
oh dear

```
lspci -v
```

---

### Post by I WILL DO IT on 2009-09-14
cool@cool-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 28100000-281fffff
	Prefetchable memory behind bridge: 20000000-27ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 28200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: 28300000-283fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: 28400000-284fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: 28500000-285fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Memory behind bridge: 28600000-286fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 3080 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 3060 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 3040 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 3020 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at 28204000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 28000000-280fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 30b0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 30c8 [size=8]
	I/O ports at 30e4 [size=4]
	I/O ports at 30c0 [size=8]
	I/O ports at 30e0 [size=4]
	I/O ports at 30a0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
	Subsystem: Gateway 2000 Device 4037
	Flags: medium devsel, IRQ 10
	I/O ports at 3000 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc RV380 [Radeon X600 (PCIE)]
	Subsystem: ATI Technologies Inc Device 0602
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 20000000 (64-bit, prefetchable) [size=128M]
	Memory at 28100000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at 2000 [size=256]
	Expansion ROM at 28120000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeonfb

01:00.1 Display controller: ATI Technologies Inc RV380 [Radeon X600]
	Subsystem: ATI Technologies Inc Device 0603
	Flags: bus master, fast devsel, latency 0
	Memory at 28110000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

06:01.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
	Subsystem: Conexant Systems, Inc. Device 2000
	Flags: bus master, fast Back2Back, medium devsel, latency 32, IRQ 11
	Memory at 28000000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at 1040 [size=8]
	Capabilities: <access denied>

06:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61) (prog-if 10)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, fast Back2Back, medium devsel, latency 32, IRQ 17
	Memory at 28011000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at 28010000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100

---

### Post by nothingspecial on 2009-09-14
Try loading this kernel module

```
sudo modprobe snd_intel8x0m
```

---

### Post by I WILL DO IT on 2009-09-14
cool@cool-desktop:~$ sudo modprobe snd_intel8x0m
[sudo] password for cool: 
WARNING: Could not open '/lib/modules/2.6.28-15-generic/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.28-15-generic/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.28-15-generic/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.28-15-generic/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.28-15-generic/kernel/sound/ac97_bus.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.28-15-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-intel8x0m.ko': No such file or directory
cool@cool-desktop:~$

---

### Post by nothingspecial on 2009-09-14
Scratch that then. Lets see what it is using

```
lsmod
```

---

### Post by I WILL DO IT on 2009-09-14
cool@cool-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96424  3 radeon
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
lp                     17156  0 
arc4                    9856  2 
ecb                    10752  2 
rt73usb                33412  0 
crc_itu_t              10112  1 rt73usb
rt2500usb              27904  0 
rt2x00usb              18688  2 rt73usb,rt2500usb
rt2x00lib              37888  3 rt73usb,rt2500usb,rt2x00usb
ppdev                  15620  0 
led_class              12036  1 rt2x00lib
psmouse                61972  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
serio_raw              13444  0 
mac80211              217592  2 rt2x00usb,rt2x00lib
pcspkr                 10496  0 
cfg80211               38288  2 rt2x00lib,mac80211
usb_storage            99648  0 
usbhid                 42336  0 
parport_pc             40100  1 
soundcore              15200  0 
intel_agp              34108  0 
parport                42220  3 lp,ppdev,parport_pc
agpgart                42696  2 drm,intel_agp
ohci1394               38576  0 
e100                   41740  0 
mii                    13312  1 e100
ieee1394               94660  1 ohci1394
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

### Post by nothingspecial on 2009-09-14
Try loading this driver
```
sudo modprobe snd-hda-intel
```

If that doesn`t work...

Have a look [[COLOR="Magenta"]here[/COLOR]]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

You may have to edit your /etc/modprobe.d/alsa-base.conf to include a line smething like options snd-hda-intel model=MODEL.

---

### Post by I WILL DO IT on 2009-09-14
i tryed that code and look what happend

cool@cool-desktop:~$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
cool@cool-desktop:~$

---

### Post by nothingspecial on 2009-09-14
[[COLOR="Magenta"]This[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1043568") describes the important bit.

Just bear in mind that /etc/modprobe.d/alsa-base is now called
/etc/modprobe.d/alsa-base.conf

Notice the .conf at the end.

---

### Post by I WILL DO IT on 2009-09-14
Code:

options snd-hda-intel xxx...=xxxx....

replacing the xxxx with the option you found. More than one option may be necessary and can be placed on the same line. You will see examples below. If there is more than one line listed after your machine, use them as listed.


were can i find xxx value?

---

