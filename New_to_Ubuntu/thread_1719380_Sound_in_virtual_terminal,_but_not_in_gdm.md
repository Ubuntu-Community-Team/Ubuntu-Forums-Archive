---
title: "Sound in virtual terminal, but not in gdm"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by KIAaze on 2011-04-01
Hi,

I lost sound on Ubuntu 10.04 after an apt-get upgrade.
After trying lots of different things I finally got sound again, but only in the virtual terminals apparently.

I am currently listening to music using mp3blaster running in TTY1, while vlc and amarok fail to produce any sound in gdm/gnome.

Quick rundown of what happened:
===============================
At first I had problems like the gnome volume control telling me:
```

"Waiting for sound system to respond"

```
and the following:
```

$ aplay -l
aplay: device_list:223: no soundcards found...

```

Amarok also asked me if I wanted to disable/remove the HDA intel device, to which I answered no.
"HDA Intel (ALC662 rev1 Analog)" is now greyed out in the KDE sound settings window (from "systemsettings").

I also got an error message like this one when trying to run pulseaudio:
[http://ubuntuforums.org/showthread.php?p=8888503](http://ubuntuforums.org/showthread.php?p=8888503)

I finally got pulseaudio running and gnome-volume-control appearing again by running the following:
```

sudo console-kit-daemon start
pulseaudio --log-level=4

```

But now I still have the problem that the sound works in TTY1, but not the gdm TTY.
Any ideas what's broken on my system?

edit:
After stopping mp3blaster in TTY1, the sound works again in VLC and flash (but not at the same time!).
Sound in amarok still not working.
And while I can open gnome-volume-control, there is no device to configure and changing the volume slider has no effect.

re-edit:
progress again after:
```

sudo usermod -a -G audio $USER

```
and logout+login.
VLC+flash can play sound at same time, device visible in gnome-volume-control, master slide available directly from applet again.

Amarok still not working.

update:
Initial sound problems reappear after reboot.
Shutdown+restart buttons do not work (they just log out and the ones on the welcome screen do nothing)
Cannot run users-admin.
I suspect a dbus problem or similar.

======================
System info:
============
```

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.2 LTS
Release:        10.04
Codename:       lucid

```

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

$ pulseaudio --version
pulseaudio 0.9.21-63-gd3efa-dirty

```

```

$ uname -a
Linux ***** 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011 x86_64 GNU/Linux

```

```

$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82578DM Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.1 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.2 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.1 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.2 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.3 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)

```

```

$ sudo lspci -vn
00:00.0 0600: 8086:d131 (rev 11)
        Subsystem: 8086:0038
        Flags: fast devsel
        Capabilities: [40] #00 [0000]

00:03.0 0604: 8086:d138 (rev 11)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: f8000000-fb0fffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: [40] Subsystem: 8086:0038
        Capabilities: [60] Message Signalled Interrupts: Mask+ 64bit- Queue=0/1 Enable+
        Capabilities: [90] Express Root Port (Slot-), MSI 00
        Capabilities: [e0] Power Management version 3
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [150] Access Controls <?>
        Capabilities: [160] Vendor Specific Information <?>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:08.0 0880: 8086:d155 (rev 11)
        Subsystem: 0086:0038
        Flags: fast devsel
        Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Vendor Specific Information <?>

00:08.1 0880: 8086:d156 (rev 11)
        Subsystem: 0086:0038
        Flags: fast devsel
        Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Vendor Specific Information <?>

00:08.2 0880: 8086:d157 (rev 11)
        Subsystem: 0086:0038
        Flags: fast devsel
        Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Vendor Specific Information <?>

00:08.3 0880: 8086:d158 (rev 11)
        Subsystem: 0086:0038
        Flags: fast devsel

00:10.0 0880: 8086:d150 (rev 11)
        Subsystem: 0086:0038
        Flags: fast devsel

00:10.1 0880: 8086:d151 (rev 11)
        Subsystem: 0086:0038
        Flags: fast devsel

00:16.0 0780: 8086:3b64 (rev 06)
        Subsystem: 8086:3b64
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at fb129000 (64-bit, non-prefetchable) [size=16]
        Capabilities: [50] Power Management version 3
        Capabilities: [8c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:19.0 0200: 8086:10ef (rev 06)
        Subsystem: 8086:0038
        Flags: bus master, fast devsel, latency 0, IRQ 27
        Memory at fb100000 (32-bit, non-prefetchable) [size=128K]
        Memory at fb128000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at f120 [size=32]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [e0] PCIe advanced features <?>
        Kernel driver in use: e1000e
        Kernel modules: e1000e

00:1a.0 0c03: 8086:3b3b (rev 06)
        Subsystem: 8086:0038
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at f100 [size=32]
        Capabilities: [50] PCIe advanced features <?>
        Kernel driver in use: uhci_hcd

00:1a.1 0c03: 8086:3b3e (rev 06)
        Subsystem: 8086:0038
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at f0e0 [size=32]
        Capabilities: [50] PCIe advanced features <?>
        Kernel driver in use: uhci_hcd

00:1a.2 0c03: 8086:3b3f (rev 06)
        Subsystem: 8086:0038
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at f0c0 [size=32]
        Capabilities: [50] PCIe advanced features <?>
        Kernel driver in use: uhci_hcd

00:1a.7 0c03: 8086:3b3c (rev 06) (prog-if 20)
        Subsystem: 8086:0038
        Flags: bus master, medium devsel, latency 0, IRQ 16
        Memory at fb127000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port: BAR=1 offset=00a0
        Capabilities: [98] PCIe advanced features <?>
        Kernel driver in use: ehci_hcd

00:1b.0 0403: 8086:3b56 (rev 06)
        Subsystem: 8086:0038
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fb120000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

00:1c.0 0604: 8086:3b42 (rev 06)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [90] Subsystem: 8086:0038
        Capabilities: [a0] Power Management version 2
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.4 0604: 8086:3b4a (rev 06)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [90] Subsystem: 8086:0038
        Capabilities: [a0] Power Management version 2
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1d.0 0c03: 8086:3b36 (rev 06)
        Subsystem: 8086:0038
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at f0a0 [size=32]
        Capabilities: [50] PCIe advanced features <?>
        Kernel driver in use: uhci_hcd

00:1d.1 0c03: 8086:3b37 (rev 06)
        Subsystem: 8086:0038
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at f080 [size=32]
        Capabilities: [50] PCIe advanced features <?>
        Kernel driver in use: uhci_hcd

00:1d.2 0c03: 8086:3b38 (rev 06)
        Subsystem: 8086:0038
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at f060 [size=32]
        Capabilities: [50] PCIe advanced features <?>
        Kernel driver in use: uhci_hcd

00:1d.3 0c03: 8086:3b39 (rev 06)
        Subsystem: 8086:0038
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at f040 [size=32]
        Capabilities: [50] PCIe advanced features <?>
        Kernel driver in use: uhci_hcd

00:1d.7 0c03: 8086:3b34 (rev 06) (prog-if 20)
        Subsystem: 8086:0038
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at fb126000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port: BAR=1 offset=00a0
        Capabilities: [98] PCIe advanced features <?>
        Kernel driver in use: ehci_hcd

00:1e.0 0604: 8086:244e (rev a6) (prog-if 01)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
        Capabilities: [50] Subsystem: 8086:0038

00:1f.0 0601: 8086:3b0a (rev 06)
        Subsystem: 8086:0038
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information <?>
        Kernel modules: iTCO_wdt

00:1f.2 0106: 8086:3b22 (rev 06) (prog-if 01)
        Subsystem: 8086:0038
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28
        I/O ports at f170 [size=8]
        I/O ports at f160 [size=4]
        I/O ports at f150 [size=8]
        I/O ports at f140 [size=4]
        I/O ports at f020 [size=32]
        Memory at fb125000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [70] Power Management version 3
        Capabilities: [a8] SATA HBA <?>
        Capabilities: [b0] PCIe advanced features <?>
        Kernel driver in use: ahci
        Kernel modules: ahci

00:1f.3 0c05: 8086:3b30 (rev 06)
        Subsystem: 8086:0038
        Flags: medium devsel, IRQ 3
        Memory at fb124000 (64-bit, non-prefetchable) [size=256]
        I/O ports at f000 [size=32]
        Kernel modules: i2c-i801

01:00.0 0300: 10de:06e4 (rev a1)
        Subsystem: 1458:34cd
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at e000 [size=128]
        [virtual] Expansion ROM at fb000000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [128] Power Budgeting <?>
        Capabilities: [600] Vendor Specific Information <?>
        Kernel driver in use: nvidia
        Kernel modules: nvidia-current, nvidiafb, nouveau


```

possibly upgrade-related part of /var/log/dpkg.log:
```

2011-03-30 09:17:49 startup archives unpack
2011-03-30 09:17:52 install ffmpeg2theora <nenio> 0.24-2build2
2011-03-30 09:17:52 status half-installed ffmpeg2theora 0.24-2build2
2011-03-30 09:17:52 status triggers-pending man-db 2.5.7-2ubuntu1
2011-03-30 09:17:52 status half-installed ffmpeg2theora 0.24-2build2
2011-03-30 09:17:54 status unpacked ffmpeg2theora 0.24-2build2
2011-03-30 09:17:54 status unpacked ffmpeg2theora 0.24-2build2
2011-03-30 09:17:54 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2011-03-30 09:17:54 status half-configured man-db 2.5.7-2ubuntu1
2011-03-30 09:17:55 status installed man-db 2.5.7-2ubuntu1
2011-03-30 09:17:56 startup packages configure
2011-03-30 09:17:56 configure ffmpeg2theora 0.24-2build2 0.24-2build2
2011-03-30 09:17:56 status unpacked ffmpeg2theora 0.24-2build2
2011-03-30 09:17:56 status half-configured ffmpeg2theora 0.24-2build2
2011-03-30 09:17:56 status installed ffmpeg2theora 0.24-2build2
2011-03-30 17:10:02 startup archives unpack
2011-03-30 17:10:02 install seahorse-plugins <nenio> 2.30.0-0ubuntu2
2011-03-30 17:10:02 status half-installed seahorse-plugins 2.30.0-0ubuntu2
2011-03-30 17:10:03 status triggers-pending hicolor-icon-theme 0.11-1
2011-03-30 17:10:03 status half-installed seahorse-plugins 2.30.0-0ubuntu2
2011-03-30 17:10:03 status triggers-pending desktop-file-utils 0.16-0ubuntu2
2011-03-30 17:10:03 status half-installed seahorse-plugins 2.30.0-0ubuntu2
2011-03-30 17:10:03 status triggers-pending python-gmenu 2.30.0-0ubuntu4
2011-03-30 17:10:03 status half-installed seahorse-plugins 2.30.0-0ubuntu2
2011-03-30 17:10:03 status triggers-pending man-db 2.5.7-2ubuntu1
2011-03-30 17:10:03 status half-installed seahorse-plugins 2.30.0-0ubuntu2
2011-03-30 17:10:03 status triggers-pending shared-mime-info 0.71-1ubuntu2
2011-03-30 17:10:03 status half-installed seahorse-plugins 2.30.0-0ubuntu2
2011-03-30 17:10:05 status unpacked seahorse-plugins 2.30.0-0ubuntu2
2011-03-30 17:10:05 status unpacked seahorse-plugins 2.30.0-0ubuntu2
2011-03-30 17:10:05 trigproc hicolor-icon-theme 0.11-1 0.11-1
2011-03-30 17:10:05 status half-configured hicolor-icon-theme 0.11-1
2011-03-30 17:10:07 status installed hicolor-icon-theme 0.11-1
2011-03-30 17:10:07 trigproc desktop-file-utils 0.16-0ubuntu2 0.16-0ubuntu2
2011-03-30 17:10:07 status half-configured desktop-file-utils 0.16-0ubuntu2
2011-03-30 17:10:08 status installed desktop-file-utils 0.16-0ubuntu2
2011-03-30 17:10:08 trigproc python-gmenu 2.30.0-0ubuntu4 2.30.0-0ubuntu4
2011-03-30 17:10:08 status half-configured python-gmenu 2.30.0-0ubuntu4
2011-03-30 17:10:09 status installed python-gmenu 2.30.0-0ubuntu4
2011-03-30 17:10:09 status triggers-pending python-support 1.0.4ubuntu1
2011-03-30 17:10:09 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2011-03-30 17:10:09 status half-configured man-db 2.5.7-2ubuntu1
2011-03-30 17:10:09 status installed man-db 2.5.7-2ubuntu1
2011-03-30 17:10:09 trigproc shared-mime-info 0.71-1ubuntu2 0.71-1ubuntu2
2011-03-30 17:10:09 status half-configured shared-mime-info 0.71-1ubuntu2
2011-03-30 17:10:10 status installed shared-mime-info 0.71-1ubuntu2
2011-03-30 17:10:10 trigproc python-support 1.0.4ubuntu1 1.0.4ubuntu1
2011-03-30 17:10:10 status half-configured python-support 1.0.4ubuntu1
2011-03-30 17:10:12 status installed python-support 1.0.4ubuntu1
2011-03-30 17:10:13 startup packages configure
2011-03-30 17:10:13 configure seahorse-plugins 2.30.0-0ubuntu2 2.30.0-0ubuntu2
2011-03-30 17:10:13 status unpacked seahorse-plugins 2.30.0-0ubuntu2
2011-03-30 17:10:13 status unpacked seahorse-plugins 2.30.0-0ubuntu2
2011-03-30 17:10:13 status half-configured seahorse-plugins 2.30.0-0ubuntu2
2011-03-30 17:10:14 status installed seahorse-plugins 2.30.0-0ubuntu2
2011-03-30 17:10:14 status triggers-pending libc-bin 2.11.1-0ubuntu7.8
2011-03-30 17:10:14 trigproc libc-bin 2.11.1-0ubuntu7.8 2.11.1-0ubuntu7.8
2011-03-30 17:10:14 status half-configured libc-bin 2.11.1-0ubuntu7.8
2011-03-30 17:10:14 status installed libc-bin 2.11.1-0ubuntu7.8
2011-03-30 17:37:47 startup archives unpack
2011-03-30 17:37:47 install libecryptfs0 <nenio> 83-0ubuntu3
2011-03-30 17:37:47 status half-installed libecryptfs0 83-0ubuntu3
2011-03-30 17:37:48 status unpacked libecryptfs0 83-0ubuntu3
2011-03-30 17:37:48 status unpacked libecryptfs0 83-0ubuntu3
2011-03-30 17:37:48 install keyutils <nenio> 1.2-12
2011-03-30 17:37:48 status half-installed keyutils 1.2-12
2011-03-30 17:37:48 status triggers-pending man-db 2.5.7-2ubuntu1
2011-03-30 17:37:48 status half-installed keyutils 1.2-12
2011-03-30 17:37:50 status unpacked keyutils 1.2-12
2011-03-30 17:37:50 status unpacked keyutils 1.2-12
2011-03-30 17:37:50 install ecryptfs-utils <nenio> 83-0ubuntu3
2011-03-30 17:37:50 status half-installed ecryptfs-utils 83-0ubuntu3
2011-03-30 17:37:50 status half-installed ecryptfs-utils 83-0ubuntu3
2011-03-30 17:37:50 status triggers-pending ureadahead 0.100.0-4.1.3
2011-03-30 17:37:50 status half-installed ecryptfs-utils 83-0ubuntu3
2011-03-30 17:37:50 status triggers-pending ureadahead 0.100.0-4.1.3
2011-03-30 17:37:52 status unpacked ecryptfs-utils 83-0ubuntu3
2011-03-30 17:37:52 status unpacked ecryptfs-utils 83-0ubuntu3
2011-03-30 17:37:52 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2011-03-30 17:37:52 status half-configured man-db 2.5.7-2ubuntu1
2011-03-30 17:37:53 status installed man-db 2.5.7-2ubuntu1
2011-03-30 17:37:53 trigproc ureadahead 0.100.0-4.1.3 0.100.0-4.1.3
2011-03-30 17:37:53 status half-configured ureadahead 0.100.0-4.1.3
2011-03-30 17:37:53 status installed ureadahead 0.100.0-4.1.3
2011-03-30 17:37:54 startup packages configure
2011-03-30 17:37:54 configure libecryptfs0 83-0ubuntu3 83-0ubuntu3
2011-03-30 17:37:54 status unpacked libecryptfs0 83-0ubuntu3
2011-03-30 17:37:54 status half-configured libecryptfs0 83-0ubuntu3
2011-03-30 17:37:54 status installed libecryptfs0 83-0ubuntu3
2011-03-30 17:37:54 status triggers-pending libc-bin 2.11.1-0ubuntu7.8
2011-03-30 17:37:54 configure keyutils 1.2-12 1.2-12
2011-03-30 17:37:54 status unpacked keyutils 1.2-12
2011-03-30 17:37:54 status unpacked keyutils 1.2-12
2011-03-30 17:37:54 status half-configured keyutils 1.2-12
2011-03-30 17:37:54 status installed keyutils 1.2-12
2011-03-30 17:37:54 configure ecryptfs-utils 83-0ubuntu3 83-0ubuntu3
2011-03-30 17:37:54 status unpacked ecryptfs-utils 83-0ubuntu3
2011-03-30 17:37:54 status unpacked ecryptfs-utils 83-0ubuntu3
2011-03-30 17:37:54 status unpacked ecryptfs-utils 83-0ubuntu3
2011-03-30 17:37:54 status half-configured ecryptfs-utils 83-0ubuntu3
2011-03-30 17:37:55 status installed ecryptfs-utils 83-0ubuntu3
2011-03-30 17:37:55 trigproc libc-bin 2.11.1-0ubuntu7.8 2.11.1-0ubuntu7.8
2011-03-30 17:37:55 status half-configured libc-bin 2.11.1-0ubuntu7.8
2011-03-30 17:37:55 status installed libc-bin 2.11.1-0ubuntu7.8
2011-03-30 17:38:18 startup archives unpack
2011-03-30 17:38:18 upgrade tzdata-java 2011b-0ubuntu0.10.04 2011d-0ubuntu0.10.04
2011-03-30 17:38:18 status half-configured tzdata-java 2011b-0ubuntu0.10.04
2011-03-30 17:38:18 status unpacked tzdata-java 2011b-0ubuntu0.10.04
2011-03-30 17:38:18 status half-installed tzdata-java 2011b-0ubuntu0.10.04
2011-03-30 17:38:21 status half-installed tzdata-java 2011b-0ubuntu0.10.04
2011-03-30 17:38:21 status unpacked tzdata-java 2011d-0ubuntu0.10.04
2011-03-30 17:38:21 status unpacked tzdata-java 2011d-0ubuntu0.10.04
2011-03-30 17:38:21 upgrade tzdata 2011b-0ubuntu0.10.04 2011d-0ubuntu0.10.04
2011-03-30 17:38:21 status half-configured tzdata 2011b-0ubuntu0.10.04
2011-03-30 17:38:21 status unpacked tzdata 2011b-0ubuntu0.10.04
2011-03-30 17:38:21 status half-installed tzdata 2011b-0ubuntu0.10.04
2011-03-30 17:38:23 status half-installed tzdata 2011b-0ubuntu0.10.04
2011-03-30 17:38:23 status unpacked tzdata 2011d-0ubuntu0.10.04
2011-03-30 17:38:23 status unpacked tzdata 2011d-0ubuntu0.10.04
2011-03-30 17:38:24 startup packages configure
2011-03-30 17:38:24 configure tzdata 2011d-0ubuntu0.10.04 2011d-0ubuntu0.10.04
2011-03-30 17:38:24 status unpacked tzdata 2011d-0ubuntu0.10.04
2011-03-30 17:38:24 status half-configured tzdata 2011d-0ubuntu0.10.04
2011-03-30 17:38:25 status installed tzdata 2011d-0ubuntu0.10.04
2011-03-30 17:38:25 startup archives unpack
2011-03-30 17:38:26 upgrade libdbus-1-dev 1.2.16-2ubuntu4.1 1.2.16-2ubuntu4.2
2011-03-30 17:38:26 status half-configured libdbus-1-dev 1.2.16-2ubuntu4.1
2011-03-30 17:38:26 status unpacked libdbus-1-dev 1.2.16-2ubuntu4.1
2011-03-30 17:38:26 status half-installed libdbus-1-dev 1.2.16-2ubuntu4.1
2011-03-30 17:38:27 status half-installed libdbus-1-dev 1.2.16-2ubuntu4.1
2011-03-30 17:38:27 status unpacked libdbus-1-dev 1.2.16-2ubuntu4.2
2011-03-30 17:38:27 status unpacked libdbus-1-dev 1.2.16-2ubuntu4.2
2011-03-30 17:38:27 upgrade libdbus-1-3 1.2.16-2ubuntu4.1 1.2.16-2ubuntu4.2
2011-03-30 17:38:27 status half-configured libdbus-1-3 1.2.16-2ubuntu4.1
2011-03-30 17:38:27 status unpacked libdbus-1-3 1.2.16-2ubuntu4.1
2011-03-30 17:38:28 status half-installed libdbus-1-3 1.2.16-2ubuntu4.1
2011-03-30 17:38:29 status half-installed libdbus-1-3 1.2.16-2ubuntu4.1
2011-03-30 17:38:29 status unpacked libdbus-1-3 1.2.16-2ubuntu4.2
2011-03-30 17:38:29 status unpacked libdbus-1-3 1.2.16-2ubuntu4.2
2011-03-30 17:38:29 upgrade libkrb5-dev 1.8.1+dfsg-2ubuntu0.6 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:29 status half-configured libkrb5-dev 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:29 status unpacked libkrb5-dev 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:29 status half-installed libkrb5-dev 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:29 status triggers-pending man-db 2.5.7-2ubuntu1
2011-03-30 17:38:29 status half-installed libkrb5-dev 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:30 status half-installed libkrb5-dev 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:31 status unpacked libkrb5-dev 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:31 status unpacked libkrb5-dev 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:31 upgrade krb5-multidev 1.8.1+dfsg-2ubuntu0.6 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:31 status half-configured krb5-multidev 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:31 status unpacked krb5-multidev 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:31 status half-installed krb5-multidev 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:32 status half-installed krb5-multidev 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:32 status unpacked krb5-multidev 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:32 status unpacked krb5-multidev 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:32 upgrade libgssrpc4 1.8.1+dfsg-2ubuntu0.6 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:32 status half-configured libgssrpc4 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:32 status unpacked libgssrpc4 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:33 status half-installed libgssrpc4 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:33 status half-installed libgssrpc4 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:34 status unpacked libgssrpc4 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:34 status unpacked libgssrpc4 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:34 upgrade krb5-user 1.8.1+dfsg-2ubuntu0.6 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:34 status half-configured krb5-user 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:34 status unpacked krb5-user 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:34 status half-installed krb5-user 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:34 status half-installed krb5-user 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:35 status half-installed krb5-user 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:35 status unpacked krb5-user 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:35 status unpacked krb5-user 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:36 upgrade libk5crypto3 1.8.1+dfsg-2ubuntu0.6 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:36 status half-configured libk5crypto3 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:36 status unpacked libk5crypto3 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:36 status half-installed libk5crypto3 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:37 status half-installed libk5crypto3 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:37 status unpacked libk5crypto3 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:37 status unpacked libk5crypto3 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:37 upgrade libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.6 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:37 status half-configured libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:37 status unpacked libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:37 status half-installed libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:38 status half-installed libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:38 status unpacked libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:38 status unpacked libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:39 upgrade libkrb5-3 1.8.1+dfsg-2ubuntu0.6 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:39 status half-configured libkrb5-3 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:39 status unpacked libkrb5-3 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:39 status half-installed libkrb5-3 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:40 status half-installed libkrb5-3 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:40 status unpacked libkrb5-3 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:40 status unpacked libkrb5-3 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:40 upgrade libkrb5support0 1.8.1+dfsg-2ubuntu0.6 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:40 status half-configured libkrb5support0 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:40 status unpacked libkrb5support0 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:40 status half-installed libkrb5support0 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:41 status half-installed libkrb5support0 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:42 status unpacked libkrb5support0 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:42 status unpacked libkrb5support0 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:42 upgrade libkadm5clnt-mit7 1.8.1+dfsg-2ubuntu0.6 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:42 status half-configured libkadm5clnt-mit7 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:42 status unpacked libkadm5clnt-mit7 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:42 status half-installed libkadm5clnt-mit7 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:43 status half-installed libkadm5clnt-mit7 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:43 status unpacked libkadm5clnt-mit7 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:43 status unpacked libkadm5clnt-mit7 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:43 upgrade libkdb5-4 1.8.1+dfsg-2ubuntu0.6 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:43 status half-configured libkdb5-4 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:43 status unpacked libkdb5-4 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:44 status half-installed libkdb5-4 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:44 status half-installed libkdb5-4 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:45 status unpacked libkdb5-4 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:45 status unpacked libkdb5-4 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:45 upgrade libkadm5srv-mit7 1.8.1+dfsg-2ubuntu0.6 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:45 status half-configured libkadm5srv-mit7 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:45 status unpacked libkadm5srv-mit7 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:45 status half-installed libkadm5srv-mit7 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:46 status half-installed libkadm5srv-mit7 1.8.1+dfsg-2ubuntu0.6
2011-03-30 17:38:46 status unpacked libkadm5srv-mit7 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:46 status unpacked libkadm5srv-mit7 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:38:46 upgrade openssh-server 1:5.3p1-3ubuntu5 1:5.3p1-3ubuntu6
2011-03-30 17:38:46 status half-configured openssh-server 1:5.3p1-3ubuntu5
2011-03-30 17:38:46 status unpacked openssh-server 1:5.3p1-3ubuntu5
2011-03-30 17:38:47 status half-installed openssh-server 1:5.3p1-3ubuntu5
2011-03-30 17:38:47 status triggers-pending ureadahead 0.100.0-4.1.3
2011-03-30 17:38:47 status half-installed openssh-server 1:5.3p1-3ubuntu5
2011-03-30 17:38:47 status triggers-pending ureadahead 0.100.0-4.1.3
2011-03-30 17:38:47 status triggers-pending ufw 0.30pre1-0ubuntu2
2011-03-30 17:38:47 status half-installed openssh-server 1:5.3p1-3ubuntu5
2011-03-30 17:38:48 status half-installed openssh-server 1:5.3p1-3ubuntu5
2011-03-30 17:38:49 status half-installed openssh-server 1:5.3p1-3ubuntu5
2011-03-30 17:38:49 status unpacked openssh-server 1:5.3p1-3ubuntu6
2011-03-30 17:38:49 status unpacked openssh-server 1:5.3p1-3ubuntu6
2011-03-30 17:38:49 upgrade openssh-client 1:5.3p1-3ubuntu5 1:5.3p1-3ubuntu6
2011-03-30 17:38:49 status half-configured openssh-client 1:5.3p1-3ubuntu5
2011-03-30 17:38:49 status unpacked openssh-client 1:5.3p1-3ubuntu5
2011-03-30 17:38:49 status half-installed openssh-client 1:5.3p1-3ubuntu5
2011-03-30 17:38:49 status half-installed openssh-client 1:5.3p1-3ubuntu5
2011-03-30 17:38:51 status half-installed openssh-client 1:5.3p1-3ubuntu5
2011-03-30 17:38:51 status unpacked openssh-client 1:5.3p1-3ubuntu6
2011-03-30 17:38:51 status unpacked openssh-client 1:5.3p1-3ubuntu6
2011-03-30 17:38:51 upgrade binutils 2.20.1-3ubuntu7 2.20.1-3ubuntu7.1
2011-03-30 17:38:51 status half-configured binutils 2.20.1-3ubuntu7
2011-03-30 17:38:51 status unpacked binutils 2.20.1-3ubuntu7
2011-03-30 17:38:51 status half-installed binutils 2.20.1-3ubuntu7
2011-03-30 17:38:51 status half-installed binutils 2.20.1-3ubuntu7
2011-03-30 17:38:53 status half-installed binutils 2.20.1-3ubuntu7
2011-03-30 17:38:53 status unpacked binutils 2.20.1-3ubuntu7.1
2011-03-30 17:38:53 status unpacked binutils 2.20.1-3ubuntu7.1
2011-03-30 17:38:53 upgrade dbus 1.2.16-2ubuntu4.1 1.2.16-2ubuntu4.2
2011-03-30 17:38:53 status half-configured dbus 1.2.16-2ubuntu4.1
2011-03-30 17:38:53 status unpacked dbus 1.2.16-2ubuntu4.1
2011-03-30 17:38:53 status half-installed dbus 1.2.16-2ubuntu4.1
2011-03-30 17:38:53 status half-installed dbus 1.2.16-2ubuntu4.1
2011-03-30 17:38:53 status half-installed dbus 1.2.16-2ubuntu4.1
2011-03-30 17:38:55 status half-installed dbus 1.2.16-2ubuntu4.1
2011-03-30 17:38:55 status unpacked dbus 1.2.16-2ubuntu4.2
2011-03-30 17:38:55 status unpacked dbus 1.2.16-2ubuntu4.2
2011-03-30 17:38:55 upgrade dbus-x11 1.2.16-2ubuntu4.1 1.2.16-2ubuntu4.2
2011-03-30 17:38:55 status half-configured dbus-x11 1.2.16-2ubuntu4.1
2011-03-30 17:38:55 status unpacked dbus-x11 1.2.16-2ubuntu4.1
2011-03-30 17:38:55 status half-installed dbus-x11 1.2.16-2ubuntu4.1
2011-03-30 17:38:55 status half-installed dbus-x11 1.2.16-2ubuntu4.1
2011-03-30 17:38:57 status half-installed dbus-x11 1.2.16-2ubuntu4.1
2011-03-30 17:38:57 status unpacked dbus-x11 1.2.16-2ubuntu4.2
2011-03-30 17:38:57 status unpacked dbus-x11 1.2.16-2ubuntu4.2
2011-03-30 17:38:57 upgrade libtiff4-dev 3.9.2-2ubuntu0.4 3.9.2-2ubuntu0.5
2011-03-30 17:38:57 status half-configured libtiff4-dev 3.9.2-2ubuntu0.4
2011-03-30 17:38:57 status unpacked libtiff4-dev 3.9.2-2ubuntu0.4
2011-03-30 17:38:57 status half-installed libtiff4-dev 3.9.2-2ubuntu0.4
2011-03-30 17:38:57 status half-installed libtiff4-dev 3.9.2-2ubuntu0.4
2011-03-30 17:38:59 status half-installed libtiff4-dev 3.9.2-2ubuntu0.4
2011-03-30 17:38:59 status unpacked libtiff4-dev 3.9.2-2ubuntu0.5
2011-03-30 17:38:59 status unpacked libtiff4-dev 3.9.2-2ubuntu0.5
2011-03-30 17:38:59 upgrade libtiffxx0c2 3.9.2-2ubuntu0.4 3.9.2-2ubuntu0.5
2011-03-30 17:38:59 status half-configured libtiffxx0c2 3.9.2-2ubuntu0.4
2011-03-30 17:38:59 status unpacked libtiffxx0c2 3.9.2-2ubuntu0.4
2011-03-30 17:38:59 status half-installed libtiffxx0c2 3.9.2-2ubuntu0.4
2011-03-30 17:39:00 status half-installed libtiffxx0c2 3.9.2-2ubuntu0.4
2011-03-30 17:39:00 status unpacked libtiffxx0c2 3.9.2-2ubuntu0.5
2011-03-30 17:39:00 status unpacked libtiffxx0c2 3.9.2-2ubuntu0.5
2011-03-30 17:39:01 upgrade libtiff4 3.9.2-2ubuntu0.4 3.9.2-2ubuntu0.5
2011-03-30 17:39:01 status half-configured libtiff4 3.9.2-2ubuntu0.4
2011-03-30 17:39:01 status unpacked libtiff4 3.9.2-2ubuntu0.4
2011-03-30 17:39:01 status half-installed libtiff4 3.9.2-2ubuntu0.4
2011-03-30 17:39:02 status half-installed libtiff4 3.9.2-2ubuntu0.4
2011-03-30 17:39:02 status unpacked libtiff4 3.9.2-2ubuntu0.5
2011-03-30 17:39:02 status unpacked libtiff4 3.9.2-2ubuntu0.5
2011-03-30 17:39:02 upgrade emacs23-lucid 23.1+1-4ubuntu7.1 23.1+1-4ubuntu7.2
2011-03-30 17:39:02 status half-configured emacs23-lucid 23.1+1-4ubuntu7.1
2011-03-30 17:39:03 status unpacked emacs23-lucid 23.1+1-4ubuntu7.1
2011-03-30 17:39:03 status half-installed emacs23-lucid 23.1+1-4ubuntu7.1
2011-03-30 17:39:03 status half-installed emacs23-lucid 23.1+1-4ubuntu7.1
2011-03-30 17:39:03 status triggers-pending desktop-file-utils 0.16-0ubuntu2
2011-03-30 17:39:04 status half-installed emacs23-lucid 23.1+1-4ubuntu7.1
2011-03-30 17:39:04 status triggers-pending python-gmenu 2.30.0-0ubuntu4
2011-03-30 17:39:04 status half-installed emacs23-lucid 23.1+1-4ubuntu7.1
2011-03-30 17:39:05 status half-installed emacs23-lucid 23.1+1-4ubuntu7.1
2011-03-30 17:39:06 status unpacked emacs23-lucid 23.1+1-4ubuntu7.2
2011-03-30 17:39:06 status unpacked emacs23-lucid 23.1+1-4ubuntu7.2
2011-03-30 17:39:06 upgrade emacs23-bin-common 23.1+1-4ubuntu7.1 23.1+1-4ubuntu7.2
2011-03-30 17:39:06 status half-configured emacs23-bin-common 23.1+1-4ubuntu7.1
2011-03-30 17:39:06 status unpacked emacs23-bin-common 23.1+1-4ubuntu7.1
2011-03-30 17:39:06 status half-installed emacs23-bin-common 23.1+1-4ubuntu7.1
2011-03-30 17:39:07 status half-installed emacs23-bin-common 23.1+1-4ubuntu7.1
2011-03-30 17:39:07 status unpacked emacs23-bin-common 23.1+1-4ubuntu7.2
2011-03-30 17:39:07 status unpacked emacs23-bin-common 23.1+1-4ubuntu7.2
2011-03-30 17:39:07 upgrade emacs23-common 23.1+1-4ubuntu7.1 23.1+1-4ubuntu7.2
2011-03-30 17:39:07 status half-configured emacs23-common 23.1+1-4ubuntu7.1
2011-03-30 17:39:08 status unpacked emacs23-common 23.1+1-4ubuntu7.1
2011-03-30 17:39:08 status half-installed emacs23-common 23.1+1-4ubuntu7.1
2011-03-30 17:39:08 status triggers-pending install-info 4.13a.dfsg.1-5ubuntu1
2011-03-30 17:39:08 status half-installed emacs23-common 23.1+1-4ubuntu7.1
2011-03-30 17:39:08 status half-installed emacs23-common 23.1+1-4ubuntu7.1
2011-03-30 17:39:08 status half-installed emacs23-common 23.1+1-4ubuntu7.1
2011-03-30 17:39:08 status half-installed emacs23-common 23.1+1-4ubuntu7.1
2011-03-30 17:39:09 status triggers-pending hicolor-icon-theme 0.11-1
2011-03-30 17:39:09 status half-installed emacs23-common 23.1+1-4ubuntu7.1
2011-03-30 17:39:11 status half-installed emacs23-common 23.1+1-4ubuntu7.1
2011-03-30 17:39:11 status unpacked emacs23-common 23.1+1-4ubuntu7.2
2011-03-30 17:39:11 status unpacked emacs23-common 23.1+1-4ubuntu7.2
2011-03-30 17:39:11 upgrade firefox-gnome-support 3.6.15+build1+nobinonly-0ubuntu0.10.04.1 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:11 status half-configured firefox-gnome-support 3.6.15+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:11 status unpacked firefox-gnome-support 3.6.15+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:11 status half-installed firefox-gnome-support 3.6.15+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:12 status half-installed firefox-gnome-support 3.6.15+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:13 status unpacked firefox-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:13 status unpacked firefox-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:13 upgrade firefox-branding 3.6.15+build1+nobinonly-0ubuntu0.10.04.1 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:13 status half-configured firefox-branding 3.6.15+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:13 status unpacked firefox-branding 3.6.15+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:13 status half-installed firefox-branding 3.6.15+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:13 status half-installed firefox-branding 3.6.15+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:13 status half-installed firefox-branding 3.6.15+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:14 status half-installed firefox-branding 3.6.15+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:14 status unpacked firefox-branding 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:15 status unpacked firefox-branding 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:15 upgrade firefox 3.6.15+build1+nobinonly-0ubuntu0.10.04.1 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:15 status half-configured firefox 3.6.15+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:15 status unpacked firefox 3.6.15+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:15 status half-installed firefox 3.6.15+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:17 status half-installed firefox 3.6.15+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:18 status unpacked firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:18 status unpacked firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:18 upgrade flashplugin-installer 10.2.152.27ubuntu0.10.04.1 10.2.153.1ubuntu0.10.04.1
2011-03-30 17:39:18 status half-configured flashplugin-installer 10.2.152.27ubuntu0.10.04.1
2011-03-30 17:39:19 update-alternatives: run with --quiet --remove iceape-flashplugin /usr/lib/flashplugin-installer/libflashplayer.so
2011-03-30 17:39:19 update-alternatives: link group iceape-flashplugin fully removed
2011-03-30 17:39:19 update-alternatives: run with --quiet --remove iceweasel-flashplugin /usr/lib/flashplugin-installer/libflashplayer.so
2011-03-30 17:39:19 update-alternatives: link group iceweasel-flashplugin fully removed
2011-03-30 17:39:19 update-alternatives: run with --quiet --remove mozilla-flashplugin /usr/lib/flashplugin-installer/libflashplayer.so
2011-03-30 17:39:19 update-alternatives: link group mozilla-flashplugin fully removed
2011-03-30 17:39:19 update-alternatives: run with --quiet --remove firefox-flashplugin /usr/lib/flashplugin-installer/libflashplayer.so
2011-03-30 17:39:19 update-alternatives: link group firefox-flashplugin fully removed
2011-03-30 17:39:19 update-alternatives: run with --quiet --remove xulrunner-flashplugin /usr/lib/flashplugin-installer/libflashplayer.so
2011-03-30 17:39:19 update-alternatives: link group xulrunner-flashplugin fully removed
2011-03-30 17:39:19 update-alternatives: run with --quiet --remove midbrowser-flashplugin /usr/lib/flashplugin-installer/libflashplayer.so
2011-03-30 17:39:19 update-alternatives: link group midbrowser-flashplugin fully removed
2011-03-30 17:39:19 update-alternatives: run with --quiet --remove xulrunner-addons-flashplugin /usr/lib/flashplugin-installer/libflashplayer.so
2011-03-30 17:39:19 update-alternatives: link group xulrunner-addons-flashplugin fully removed
2011-03-30 17:39:19 status unpacked flashplugin-installer 10.2.152.27ubuntu0.10.04.1
2011-03-30 17:39:19 status half-installed flashplugin-installer 10.2.152.27ubuntu0.10.04.1
2011-03-30 17:39:21 status half-installed flashplugin-installer 10.2.152.27ubuntu0.10.04.1
2011-03-30 17:39:21 status unpacked flashplugin-installer 10.2.153.1ubuntu0.10.04.1
2011-03-30 17:39:21 status unpacked flashplugin-installer 10.2.153.1ubuntu0.10.04.1
2011-03-30 17:39:21 upgrade gcj-4.4-base 4.4.3-1ubuntu4 4.4.3-1ubuntu4.1
2011-03-30 17:39:21 status half-configured gcj-4.4-base 4.4.3-1ubuntu4
2011-03-30 17:39:21 status unpacked gcj-4.4-base 4.4.3-1ubuntu4
2011-03-30 17:39:21 status half-installed gcj-4.4-base 4.4.3-1ubuntu4
2011-03-30 17:39:22 status half-installed gcj-4.4-base 4.4.3-1ubuntu4
2011-03-30 17:39:22 status unpacked gcj-4.4-base 4.4.3-1ubuntu4.1
2011-03-30 17:39:22 status unpacked gcj-4.4-base 4.4.3-1ubuntu4.1
2011-03-30 17:39:22 upgrade libgcj10 4.4.3-1ubuntu4 4.4.3-1ubuntu4.1
2011-03-30 17:39:22 status half-configured libgcj10 4.4.3-1ubuntu4
2011-03-30 17:39:23 status unpacked libgcj10 4.4.3-1ubuntu4
2011-03-30 17:39:23 status half-installed libgcj10 4.4.3-1ubuntu4
2011-03-30 17:39:24 status half-installed libgcj10 4.4.3-1ubuntu4
2011-03-30 17:39:25 status unpacked libgcj10 4.4.3-1ubuntu4.1
2011-03-30 17:39:25 status unpacked libgcj10 4.4.3-1ubuntu4.1
2011-03-30 17:39:25 upgrade gcj-4.4-jre-lib 4.4.3-1ubuntu4 4.4.3-1ubuntu4.1
2011-03-30 17:39:25 status half-configured gcj-4.4-jre-lib 4.4.3-1ubuntu4
2011-03-30 17:39:25 status unpacked gcj-4.4-jre-lib 4.4.3-1ubuntu4
2011-03-30 17:39:25 status half-installed gcj-4.4-jre-lib 4.4.3-1ubuntu4
2011-03-30 17:39:26 status half-installed gcj-4.4-jre-lib 4.4.3-1ubuntu4
2011-03-30 17:39:26 status unpacked gcj-4.4-jre-lib 4.4.3-1ubuntu4.1
2011-03-30 17:39:27 status unpacked gcj-4.4-jre-lib 4.4.3-1ubuntu4.1
2011-03-30 17:39:27 upgrade gnome-screensaver 2.30.0-0ubuntu2 2.30.0-0ubuntu2.1
2011-03-30 17:39:27 status half-configured gnome-screensaver 2.30.0-0ubuntu2
2011-03-30 17:39:32 status unpacked gnome-screensaver 2.30.0-0ubuntu2
2011-03-30 17:39:32 status half-installed gnome-screensaver 2.30.0-0ubuntu2
2011-03-30 17:39:32 status half-installed gnome-screensaver 2.30.0-0ubuntu2
2011-03-30 17:39:32 status half-installed gnome-screensaver 2.30.0-0ubuntu2
2011-03-30 17:39:32 status half-installed gnome-screensaver 2.30.0-0ubuntu2
2011-03-30 17:39:34 status half-installed gnome-screensaver 2.30.0-0ubuntu2
2011-03-30 17:39:34 status unpacked gnome-screensaver 2.30.0-0ubuntu2.1
2011-03-30 17:39:34 status unpacked gnome-screensaver 2.30.0-0ubuntu2.1
2011-03-30 17:39:34 upgrade libservlet2.5-java 6.0.24-2ubuntu1.6 6.0.24-2ubuntu1.7
2011-03-30 17:39:34 status half-configured libservlet2.5-java 6.0.24-2ubuntu1.6
2011-03-30 17:39:34 status unpacked libservlet2.5-java 6.0.24-2ubuntu1.6
2011-03-30 17:39:34 status half-installed libservlet2.5-java 6.0.24-2ubuntu1.6
2011-03-30 17:39:36 status half-installed libservlet2.5-java 6.0.24-2ubuntu1.6
2011-03-30 17:39:36 status unpacked libservlet2.5-java 6.0.24-2ubuntu1.7
2011-03-30 17:39:36 status unpacked libservlet2.5-java 6.0.24-2ubuntu1.7
2011-03-30 17:39:36 upgrade subversion 1.6.6dfsg-2ubuntu1.1 1.6.6dfsg-2ubuntu1.2
2011-03-30 17:39:36 status half-configured subversion 1.6.6dfsg-2ubuntu1.1
2011-03-30 17:39:36 status unpacked subversion 1.6.6dfsg-2ubuntu1.1
2011-03-30 17:39:36 status half-installed subversion 1.6.6dfsg-2ubuntu1.1
2011-03-30 17:39:36 status half-installed subversion 1.6.6dfsg-2ubuntu1.1
2011-03-30 17:39:38 status half-installed subversion 1.6.6dfsg-2ubuntu1.1
2011-03-30 17:39:38 status unpacked subversion 1.6.6dfsg-2ubuntu1.2
2011-03-30 17:39:38 status unpacked subversion 1.6.6dfsg-2ubuntu1.2
2011-03-30 17:39:38 upgrade libsvn1 1.6.6dfsg-2ubuntu1.1 1.6.6dfsg-2ubuntu1.2
2011-03-30 17:39:38 status half-configured libsvn1 1.6.6dfsg-2ubuntu1.1
2011-03-30 17:39:38 status unpacked libsvn1 1.6.6dfsg-2ubuntu1.1
2011-03-30 17:39:38 status half-installed libsvn1 1.6.6dfsg-2ubuntu1.1
2011-03-30 17:39:39 status half-installed libsvn1 1.6.6dfsg-2ubuntu1.1
2011-03-30 17:39:40 status unpacked libsvn1 1.6.6dfsg-2ubuntu1.2
2011-03-30 17:39:40 status unpacked libsvn1 1.6.6dfsg-2ubuntu1.2
2011-03-30 17:39:40 upgrade libtiff-tools 3.9.2-2ubuntu0.4 3.9.2-2ubuntu0.5
2011-03-30 17:39:40 status half-configured libtiff-tools 3.9.2-2ubuntu0.4
2011-03-30 17:39:40 status unpacked libtiff-tools 3.9.2-2ubuntu0.4
2011-03-30 17:39:40 status half-installed libtiff-tools 3.9.2-2ubuntu0.4
2011-03-30 17:39:40 status half-installed libtiff-tools 3.9.2-2ubuntu0.4
2011-03-30 17:39:42 status half-installed libtiff-tools 3.9.2-2ubuntu0.4
2011-03-30 17:39:42 status unpacked libtiff-tools 3.9.2-2ubuntu0.5
2011-03-30 17:39:42 status unpacked libtiff-tools 3.9.2-2ubuntu0.5
2011-03-30 17:39:42 upgrade smbclient 2:3.4.7~dfsg-1ubuntu3.4 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:39:42 status half-configured smbclient 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:42 status unpacked smbclient 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:42 status half-installed smbclient 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:43 status half-installed smbclient 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:44 status half-installed smbclient 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:45 status unpacked smbclient 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:39:45 status unpacked smbclient 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:39:45 upgrade winbind 2:3.4.7~dfsg-1ubuntu3.4 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:39:45 status half-configured winbind 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:45 status unpacked winbind 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:45 status half-installed winbind 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:45 status half-installed winbind 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:45 status half-installed winbind 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:47 status half-installed winbind 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:47 status unpacked winbind 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:39:47 status unpacked winbind 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:39:47 upgrade samba-common 2:3.4.7~dfsg-1ubuntu3.4 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:39:47 status half-configured samba-common 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:47 status unpacked samba-common 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:47 status half-installed samba-common 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:48 status half-installed samba-common 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:49 status unpacked samba-common 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:39:49 status unpacked samba-common 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:39:49 upgrade libwbclient0 2:3.4.7~dfsg-1ubuntu3.4 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:39:49 status half-configured libwbclient0 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:49 status unpacked libwbclient0 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:49 status half-installed libwbclient0 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:50 status half-installed libwbclient0 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:50 status unpacked libwbclient0 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:39:50 status unpacked libwbclient0 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:39:50 upgrade linux-libc-dev 2.6.32-29.58 2.6.32-30.59
2011-03-30 17:39:50 status half-configured linux-libc-dev 2.6.32-29.58
2011-03-30 17:39:51 status unpacked linux-libc-dev 2.6.32-29.58
2011-03-30 17:39:51 status half-installed linux-libc-dev 2.6.32-29.58
2011-03-30 17:39:52 status half-installed linux-libc-dev 2.6.32-29.58
2011-03-30 17:39:53 status unpacked linux-libc-dev 2.6.32-30.59
2011-03-30 17:39:53 status unpacked linux-libc-dev 2.6.32-30.59
2011-03-30 17:39:53 upgrade samba-common-bin 2:3.4.7~dfsg-1ubuntu3.4 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:39:53 status half-configured samba-common-bin 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:53 status unpacked samba-common-bin 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:53 status half-installed samba-common-bin 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:53 status half-installed samba-common-bin 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:54 status half-installed samba-common-bin 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:39:55 status unpacked samba-common-bin 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:39:55 status unpacked samba-common-bin 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:39:55 upgrade ssh 1:5.3p1-3ubuntu5 1:5.3p1-3ubuntu6
2011-03-30 17:39:55 status half-configured ssh 1:5.3p1-3ubuntu5
2011-03-30 17:39:55 status unpacked ssh 1:5.3p1-3ubuntu5
2011-03-30 17:39:55 status half-installed ssh 1:5.3p1-3ubuntu5
2011-03-30 17:39:56 status half-installed ssh 1:5.3p1-3ubuntu5
2011-03-30 17:39:56 status unpacked ssh 1:5.3p1-3ubuntu6
2011-03-30 17:39:56 status unpacked ssh 1:5.3p1-3ubuntu6
2011-03-30 17:39:57 upgrade ssh-askpass-gnome 1:5.3p1-3ubuntu5 1:5.3p1-3ubuntu6
2011-03-30 17:39:57 status half-configured ssh-askpass-gnome 1:5.3p1-3ubuntu5
2011-03-30 17:39:57 status unpacked ssh-askpass-gnome 1:5.3p1-3ubuntu5
2011-03-30 17:39:57 status half-installed ssh-askpass-gnome 1:5.3p1-3ubuntu5
2011-03-30 17:39:57 status half-installed ssh-askpass-gnome 1:5.3p1-3ubuntu5
2011-03-30 17:39:58 status half-installed ssh-askpass-gnome 1:5.3p1-3ubuntu5
2011-03-30 17:39:58 status unpacked ssh-askpass-gnome 1:5.3p1-3ubuntu6
2011-03-30 17:39:58 status unpacked ssh-askpass-gnome 1:5.3p1-3ubuntu6
2011-03-30 17:39:58 upgrade xulrunner-1.9.2 1.9.2.15+build1+nobinonly-0ubuntu0.10.04.1 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:58 status half-configured xulrunner-1.9.2 1.9.2.15+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:58 update-alternatives: run with --remove xulrunner /usr/bin/xulrunner-1.9.2
2011-03-30 17:39:58 update-alternatives: link group xulrunner fully removed
2011-03-30 17:39:58 status unpacked xulrunner-1.9.2 1.9.2.15+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:39:58 status half-installed xulrunner-1.9.2 1.9.2.15+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:00 status half-installed xulrunner-1.9.2 1.9.2.15+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:01 status unpacked xulrunner-1.9.2 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:01 status unpacked xulrunner-1.9.2 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:01 upgrade libsmbclient 2:3.4.7~dfsg-1ubuntu3.4 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:01 status half-configured libsmbclient 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:40:01 status unpacked libsmbclient 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:40:01 status half-installed libsmbclient 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:40:02 status half-installed libsmbclient 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:40:03 status half-installed libsmbclient 2:3.4.7~dfsg-1ubuntu3.4
2011-03-30 17:40:03 status unpacked libsmbclient 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:03 status unpacked libsmbclient 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:03 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2011-03-30 17:40:03 status half-configured man-db 2.5.7-2ubuntu1
2011-03-30 17:40:05 status installed man-db 2.5.7-2ubuntu1
2011-03-30 17:40:05 trigproc ureadahead 0.100.0-4.1.3 0.100.0-4.1.3
2011-03-30 17:40:05 status half-configured ureadahead 0.100.0-4.1.3
2011-03-30 17:40:05 status installed ureadahead 0.100.0-4.1.3
2011-03-30 17:40:05 trigproc ufw 0.30pre1-0ubuntu2 0.30pre1-0ubuntu2
2011-03-30 17:40:05 status half-configured ufw 0.30pre1-0ubuntu2
2011-03-30 17:40:06 status installed ufw 0.30pre1-0ubuntu2
2011-03-30 17:40:06 trigproc desktop-file-utils 0.16-0ubuntu2 0.16-0ubuntu2
2011-03-30 17:40:06 status half-configured desktop-file-utils 0.16-0ubuntu2
2011-03-30 17:40:06 status installed desktop-file-utils 0.16-0ubuntu2
2011-03-30 17:40:06 trigproc python-gmenu 2.30.0-0ubuntu4 2.30.0-0ubuntu4
2011-03-30 17:40:06 status half-configured python-gmenu 2.30.0-0ubuntu4
2011-03-30 17:40:07 status installed python-gmenu 2.30.0-0ubuntu4
2011-03-30 17:40:07 status triggers-pending python-support 1.0.4ubuntu1
2011-03-30 17:40:07 trigproc install-info 4.13a.dfsg.1-5ubuntu1 4.13a.dfsg.1-5ubuntu1
2011-03-30 17:40:07 status half-configured install-info 4.13a.dfsg.1-5ubuntu1
2011-03-30 17:40:08 status installed install-info 4.13a.dfsg.1-5ubuntu1
2011-03-30 17:40:08 trigproc hicolor-icon-theme 0.11-1 0.11-1
2011-03-30 17:40:08 status half-configured hicolor-icon-theme 0.11-1
2011-03-30 17:40:09 status installed hicolor-icon-theme 0.11-1
2011-03-30 17:40:09 trigproc python-support 1.0.4ubuntu1 1.0.4ubuntu1
2011-03-30 17:40:09 status half-configured python-support 1.0.4ubuntu1
2011-03-30 17:40:09 status installed python-support 1.0.4ubuntu1
2011-03-30 17:40:10 startup packages configure
2011-03-30 17:40:10 configure tzdata-java 2011d-0ubuntu0.10.04 2011d-0ubuntu0.10.04
2011-03-30 17:40:10 status unpacked tzdata-java 2011d-0ubuntu0.10.04
2011-03-30 17:40:10 status half-configured tzdata-java 2011d-0ubuntu0.10.04
2011-03-30 17:40:10 status installed tzdata-java 2011d-0ubuntu0.10.04
2011-03-30 17:40:10 configure libdbus-1-3 1.2.16-2ubuntu4.2 1.2.16-2ubuntu4.2
2011-03-30 17:40:10 status unpacked libdbus-1-3 1.2.16-2ubuntu4.2
2011-03-30 17:40:10 status half-configured libdbus-1-3 1.2.16-2ubuntu4.2
2011-03-30 17:40:10 status installed libdbus-1-3 1.2.16-2ubuntu4.2
2011-03-30 17:40:10 status triggers-pending libc-bin 2.11.1-0ubuntu7.8
2011-03-30 17:40:10 configure libdbus-1-dev 1.2.16-2ubuntu4.2 1.2.16-2ubuntu4.2
2011-03-30 17:40:10 status unpacked libdbus-1-dev 1.2.16-2ubuntu4.2
2011-03-30 17:40:10 status half-configured libdbus-1-dev 1.2.16-2ubuntu4.2
2011-03-30 17:40:11 status installed libdbus-1-dev 1.2.16-2ubuntu4.2
2011-03-30 17:40:11 configure libkrb5support0 1.8.1+dfsg-2ubuntu0.8 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 status unpacked libkrb5support0 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 status half-configured libkrb5support0 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 status installed libkrb5support0 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 configure libk5crypto3 1.8.1+dfsg-2ubuntu0.8 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 status unpacked libk5crypto3 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 status half-configured libk5crypto3 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 status installed libk5crypto3 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 configure libkrb5-3 1.8.1+dfsg-2ubuntu0.8 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 status unpacked libkrb5-3 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 status half-configured libkrb5-3 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 status installed libkrb5-3 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 configure libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.8 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 status unpacked libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 status half-configured libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 status installed libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 configure libgssrpc4 1.8.1+dfsg-2ubuntu0.8 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 status unpacked libgssrpc4 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 status half-configured libgssrpc4 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 status installed libgssrpc4 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 configure libkdb5-4 1.8.1+dfsg-2ubuntu0.8 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 status unpacked libkdb5-4 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 status half-configured libkdb5-4 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:11 status installed libkdb5-4 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:12 configure libkadm5srv-mit7 1.8.1+dfsg-2ubuntu0.8 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:12 status unpacked libkadm5srv-mit7 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:12 status half-configured libkadm5srv-mit7 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:12 status installed libkadm5srv-mit7 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:12 configure libkadm5clnt-mit7 1.8.1+dfsg-2ubuntu0.8 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:12 status unpacked libkadm5clnt-mit7 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:12 status half-configured libkadm5clnt-mit7 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:12 status installed libkadm5clnt-mit7 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:12 configure krb5-multidev 1.8.1+dfsg-2ubuntu0.8 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:12 status unpacked krb5-multidev 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:12 status half-configured krb5-multidev 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:12 status installed krb5-multidev 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:12 configure libkrb5-dev 1.8.1+dfsg-2ubuntu0.8 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:12 status unpacked libkrb5-dev 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:12 status half-configured libkrb5-dev 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:13 status installed libkrb5-dev 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:13 configure krb5-user 1.8.1+dfsg-2ubuntu0.8 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:13 status unpacked krb5-user 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:13 status half-configured krb5-user 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:13 status installed krb5-user 1.8.1+dfsg-2ubuntu0.8
2011-03-30 17:40:13 configure openssh-client 1:5.3p1-3ubuntu6 1:5.3p1-3ubuntu6
2011-03-30 17:40:13 status unpacked openssh-client 1:5.3p1-3ubuntu6
2011-03-30 17:40:13 status unpacked openssh-client 1:5.3p1-3ubuntu6
2011-03-30 17:40:13 status unpacked openssh-client 1:5.3p1-3ubuntu6
2011-03-30 17:40:13 status half-configured openssh-client 1:5.3p1-3ubuntu6
2011-03-30 17:40:13 update-alternatives: run with --quiet --remove rlogin /usr/bin/ssh
2011-03-30 17:40:13 update-alternatives: run with --quiet --remove rcp /usr/bin/ssh
2011-03-30 17:40:13 status installed openssh-client 1:5.3p1-3ubuntu6
2011-03-30 17:40:13 configure openssh-server 1:5.3p1-3ubuntu6 1:5.3p1-3ubuntu6
2011-03-30 17:40:13 status unpacked openssh-server 1:5.3p1-3ubuntu6
2011-03-30 17:40:13 status unpacked openssh-server 1:5.3p1-3ubuntu6
2011-03-30 17:40:14 status unpacked openssh-server 1:5.3p1-3ubuntu6
2011-03-30 17:40:14 status unpacked openssh-server 1:5.3p1-3ubuntu6
2011-03-30 17:40:14 status unpacked openssh-server 1:5.3p1-3ubuntu6
2011-03-30 17:40:14 status unpacked openssh-server 1:5.3p1-3ubuntu6
2011-03-30 17:40:14 status unpacked openssh-server 1:5.3p1-3ubuntu6
2011-03-30 17:40:14 status half-configured openssh-server 1:5.3p1-3ubuntu6
2011-03-30 17:40:14 status installed openssh-server 1:5.3p1-3ubuntu6
2011-03-30 17:40:14 configure binutils 2.20.1-3ubuntu7.1 2.20.1-3ubuntu7.1
2011-03-30 17:40:14 status unpacked binutils 2.20.1-3ubuntu7.1
2011-03-30 17:40:15 status half-configured binutils 2.20.1-3ubuntu7.1
2011-03-30 17:40:15 status installed binutils 2.20.1-3ubuntu7.1
2011-03-30 17:40:15 configure dbus 1.2.16-2ubuntu4.2 1.2.16-2ubuntu4.2
2011-03-30 17:40:15 status unpacked dbus 1.2.16-2ubuntu4.2
2011-03-30 17:40:15 status unpacked dbus 1.2.16-2ubuntu4.2
2011-03-30 17:40:15 status unpacked dbus 1.2.16-2ubuntu4.2
2011-03-30 17:40:15 status unpacked dbus 1.2.16-2ubuntu4.2
2011-03-30 17:40:15 status unpacked dbus 1.2.16-2ubuntu4.2
2011-03-30 17:40:15 status half-configured dbus 1.2.16-2ubuntu4.2
2011-03-30 17:40:16 status installed dbus 1.2.16-2ubuntu4.2
2011-03-30 17:40:16 configure dbus-x11 1.2.16-2ubuntu4.2 1.2.16-2ubuntu4.2
2011-03-30 17:40:16 status unpacked dbus-x11 1.2.16-2ubuntu4.2
2011-03-30 17:40:16 status unpacked dbus-x11 1.2.16-2ubuntu4.2
2011-03-30 17:40:16 status half-configured dbus-x11 1.2.16-2ubuntu4.2
2011-03-30 17:40:16 status installed dbus-x11 1.2.16-2ubuntu4.2
2011-03-30 17:40:16 configure libtiff4 3.9.2-2ubuntu0.5 3.9.2-2ubuntu0.5
2011-03-30 17:40:16 status unpacked libtiff4 3.9.2-2ubuntu0.5
2011-03-30 17:40:16 status half-configured libtiff4 3.9.2-2ubuntu0.5
2011-03-30 17:40:16 status installed libtiff4 3.9.2-2ubuntu0.5
2011-03-30 17:40:16 configure libtiffxx0c2 3.9.2-2ubuntu0.5 3.9.2-2ubuntu0.5
2011-03-30 17:40:16 status unpacked libtiffxx0c2 3.9.2-2ubuntu0.5
2011-03-30 17:40:16 status half-configured libtiffxx0c2 3.9.2-2ubuntu0.5
2011-03-30 17:40:17 status installed libtiffxx0c2 3.9.2-2ubuntu0.5
2011-03-30 17:40:17 configure libtiff4-dev 3.9.2-2ubuntu0.5 3.9.2-2ubuntu0.5
2011-03-30 17:40:17 status unpacked libtiff4-dev 3.9.2-2ubuntu0.5
2011-03-30 17:40:17 status half-configured libtiff4-dev 3.9.2-2ubuntu0.5
2011-03-30 17:40:17 status installed libtiff4-dev 3.9.2-2ubuntu0.5
2011-03-30 17:40:17 configure emacs23-common 23.1+1-4ubuntu7.2 23.1+1-4ubuntu7.2
2011-03-30 17:40:17 status unpacked emacs23-common 23.1+1-4ubuntu7.2
2011-03-30 17:40:17 status half-configured emacs23-common 23.1+1-4ubuntu7.2
2011-03-30 17:40:17 status installed emacs23-common 23.1+1-4ubuntu7.2
2011-03-30 17:40:17 configure emacs23-bin-common 23.1+1-4ubuntu7.2 23.1+1-4ubuntu7.2
2011-03-30 17:40:17 status unpacked emacs23-bin-common 23.1+1-4ubuntu7.2
2011-03-30 17:40:17 status half-configured emacs23-bin-common 23.1+1-4ubuntu7.2
2011-03-30 17:40:17 update-alternatives: run with --install /usr/bin/b2m b2m /usr/bin/b2m.emacs23 26 --slave /usr/share/man/man1/b2m.1.gz b2m.1.gz /usr/share/man/man1/b2m.emacs23.1.gz
2011-03-30 17:40:17 update-alternatives: run with --install /usr/bin/ctags ctags /usr/bin/ctags.emacs23 26 --slave /usr/share/man/man1/ctags.1.gz ctags.1.gz /usr/share/man/man1/ctags.emacs23.1.gz
2011-03-30 17:40:17 update-alternatives: run with --install /usr/bin/ebrowse ebrowse /usr/bin/ebrowse.emacs23 26 --slave /usr/share/man/man1/ebrowse.1.gz ebrowse.1.gz /usr/share/man/man1/ebrowse.emacs23.1.gz
2011-03-30 17:40:17 update-alternatives: run with --install /usr/bin/emacsclient emacsclient /usr/bin/emacsclient.emacs23 26 --slave /usr/share/man/man1/emacsclient.1.gz emacsclient.1.gz /usr/share/man/man1/emacsclient.emacs23.1.gz
2011-03-30 17:40:17 update-alternatives: run with --install /usr/bin/etags etags /usr/bin/etags.emacs23 26 --slave /usr/share/man/man1/etags.1.gz etags.1.gz /usr/share/man/man1/etags.emacs23.1.gz
2011-03-30 17:40:17 update-alternatives: run with --install /usr/bin/grep-changelog grep-changelog /usr/bin/grep-changelog.emacs23 26 --slave /usr/share/man/man1/grep-changelog.1.gz grep-changelog.1.gz /usr/share/man/man1/grep-changelog.emacs23.1.gz
2011-03-30 17:40:17 update-alternatives: run with --install /usr/bin/rcs-checkin rcs-checkin /usr/bin/rcs-checkin.emacs23 26 --slave /usr/share/man/man1/rcs-checkin.1.gz rcs-checkin.1.gz /usr/share/man/man1/rcs-checkin.emacs23.1.gz
2011-03-30 17:40:17 status installed emacs23-bin-common 23.1+1-4ubuntu7.2
2011-03-30 17:40:17 configure emacs23-lucid 23.1+1-4ubuntu7.2 23.1+1-4ubuntu7.2
2011-03-30 17:40:17 status unpacked emacs23-lucid 23.1+1-4ubuntu7.2
2011-03-30 17:40:18 status half-configured emacs23-lucid 23.1+1-4ubuntu7.2
2011-03-30 17:40:18 update-alternatives: run with --install /usr/bin/emacs emacs /usr/bin/emacs23-lucid 26 --slave /usr/share/man/man1/emacs.1.gz emacs.1.gz /usr/share/man/man1/emacs.emacs23.1.gz --slave /usr/share/icons/hicolor/scalable/apps/emacs.svg emacs.svg /usr/share/icons/hicolor/scalable/apps/emacs23.svg --slave /usr/share/icons/hicolor/scalable/mimetypes/emacs-document.svg emacs-document.svg /usr/share/icons/hicolor/scalable/mimetypes/emacs23-document.svg --slave /usr/share/icons/hicolor/16x16/apps/emacs.png emacs-16x16.png /usr/share/icons/hicolor/16x16/apps/emacs23.png --slave /usr/share/icons/hicolor/24x24/apps/emacs.png emacs-24x24.png /usr/share/icons/hicolor/24x24/apps/emacs23.png --slave /usr/share/icons/hicolor/32x32/apps/emacs.png emacs-32x32.png /usr/share/icons/hicolor/32x32/apps/emacs23.png --slave /usr/share/icons/hicolor/48x48/apps/emacs.png emacs-48x48.png /usr/share/icons/hicolor/48x48/apps/emacs23.png --slave /usr/share/icons/hicolor/128x128/apps/emacs.png emacs-128x128.png /usr/share/icons/hicolor/128x128/apps/emacs23.png
2011-03-30 17:40:18 update-alternatives: run with --install /usr/bin/editor editor /usr/bin/emacs23 0 --slave /usr/share/man/man1/editor.1.gz editor.1.gz /usr/share/man/man1/emacs.1emacs23.1.gz
2011-03-30 17:40:21 status installed emacs23-lucid 23.1+1-4ubuntu7.2
2011-03-30 17:40:21 configure flashplugin-installer 10.2.153.1ubuntu0.10.04.1 10.2.153.1ubuntu0.10.04.1
2011-03-30 17:40:21 status unpacked flashplugin-installer 10.2.153.1ubuntu0.10.04.1
2011-03-30 17:40:21 status half-configured flashplugin-installer 10.2.153.1ubuntu0.10.04.1
2011-03-30 17:40:22 update-alternatives: run with --quiet --install /usr/lib/iceape/plugins/flashplugin-alternative.so iceape-flashplugin /var/lib/flashplugin-installer/npwrapper.libflashplayer.so 50
2011-03-30 17:40:22 update-alternatives: link group iceape-flashplugin updated to point to /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
2011-03-30 17:40:22 update-alternatives: run with --quiet --install /usr/lib/iceweasel/plugins/flashplugin-alternative.so iceweasel-flashplugin /var/lib/flashplugin-installer/npwrapper.libflashplayer.so 50
2011-03-30 17:40:22 update-alternatives: link group iceweasel-flashplugin updated to point to /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
2011-03-30 17:40:22 update-alternatives: run with --quiet --install /usr/lib/mozilla/plugins/flashplugin-alternative.so mozilla-flashplugin /var/lib/flashplugin-installer/npwrapper.libflashplayer.so 50
2011-03-30 17:40:22 update-alternatives: link group mozilla-flashplugin updated to point to /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
2011-03-30 17:40:22 update-alternatives: run with --quiet --install /usr/lib/firefox/plugins/flashplugin-alternative.so firefox-flashplugin /var/lib/flashplugin-installer/npwrapper.libflashplayer.so 50
2011-03-30 17:40:22 update-alternatives: link group firefox-flashplugin updated to point to /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
2011-03-30 17:40:22 update-alternatives: run with --quiet --install /usr/lib/xulrunner/plugins/flashplugin-alternative.so xulrunner-flashplugin /var/lib/flashplugin-installer/npwrapper.libflashplayer.so 50
2011-03-30 17:40:22 update-alternatives: link group xulrunner-flashplugin updated to point to /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
2011-03-30 17:40:22 update-alternatives: run with --quiet --install /usr/lib/midbrowser/plugins/flashplugin-alternative.so midbrowser-flashplugin /var/lib/flashplugin-installer/npwrapper.libflashplayer.so 50
2011-03-30 17:40:22 update-alternatives: link group midbrowser-flashplugin updated to point to /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
2011-03-30 17:40:22 update-alternatives: run with --quiet --install /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so xulrunner-addons-flashplugin /var/lib/flashplugin-installer/npwrapper.libflashplayer.so 50
2011-03-30 17:40:22 update-alternatives: link group xulrunner-addons-flashplugin updated to point to /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
2011-03-30 17:40:22 status installed flashplugin-installer 10.2.153.1ubuntu0.10.04.1
2011-03-30 17:40:23 configure gcj-4.4-base 4.4.3-1ubuntu4.1 4.4.3-1ubuntu4.1
2011-03-30 17:40:23 status unpacked gcj-4.4-base 4.4.3-1ubuntu4.1
2011-03-30 17:40:23 status half-configured gcj-4.4-base 4.4.3-1ubuntu4.1
2011-03-30 17:40:23 status installed gcj-4.4-base 4.4.3-1ubuntu4.1
2011-03-30 17:40:23 configure libgcj10 4.4.3-1ubuntu4.1 4.4.3-1ubuntu4.1
2011-03-30 17:40:23 status unpacked libgcj10 4.4.3-1ubuntu4.1
2011-03-30 17:40:23 status half-configured libgcj10 4.4.3-1ubuntu4.1
2011-03-30 17:40:23 status installed libgcj10 4.4.3-1ubuntu4.1
2011-03-30 17:40:23 configure gcj-4.4-jre-lib 4.4.3-1ubuntu4.1 4.4.3-1ubuntu4.1
2011-03-30 17:40:23 status unpacked gcj-4.4-jre-lib 4.4.3-1ubuntu4.1
2011-03-30 17:40:23 status half-configured gcj-4.4-jre-lib 4.4.3-1ubuntu4.1
2011-03-30 17:40:23 status installed gcj-4.4-jre-lib 4.4.3-1ubuntu4.1
2011-03-30 17:40:23 configure gnome-screensaver 2.30.0-0ubuntu2.1 2.30.0-0ubuntu2.1
2011-03-30 17:40:23 status unpacked gnome-screensaver 2.30.0-0ubuntu2.1
2011-03-30 17:40:23 status unpacked gnome-screensaver 2.30.0-0ubuntu2.1
2011-03-30 17:40:23 status unpacked gnome-screensaver 2.30.0-0ubuntu2.1
2011-03-30 17:40:23 status unpacked gnome-screensaver 2.30.0-0ubuntu2.1
2011-03-30 17:40:23 status half-configured gnome-screensaver 2.30.0-0ubuntu2.1
2011-03-30 17:40:24 status installed gnome-screensaver 2.30.0-0ubuntu2.1
2011-03-30 17:40:24 configure libservlet2.5-java 6.0.24-2ubuntu1.7 6.0.24-2ubuntu1.7
2011-03-30 17:40:24 status unpacked libservlet2.5-java 6.0.24-2ubuntu1.7
2011-03-30 17:40:24 status half-configured libservlet2.5-java 6.0.24-2ubuntu1.7
2011-03-30 17:40:24 status installed libservlet2.5-java 6.0.24-2ubuntu1.7
2011-03-30 17:40:24 configure libsvn1 1.6.6dfsg-2ubuntu1.2 1.6.6dfsg-2ubuntu1.2
2011-03-30 17:40:24 status unpacked libsvn1 1.6.6dfsg-2ubuntu1.2
2011-03-30 17:40:24 status half-configured libsvn1 1.6.6dfsg-2ubuntu1.2
2011-03-30 17:40:24 status installed libsvn1 1.6.6dfsg-2ubuntu1.2
2011-03-30 17:40:24 configure subversion 1.6.6dfsg-2ubuntu1.2 1.6.6dfsg-2ubuntu1.2
2011-03-30 17:40:24 status unpacked subversion 1.6.6dfsg-2ubuntu1.2
2011-03-30 17:40:24 status unpacked subversion 1.6.6dfsg-2ubuntu1.2
2011-03-30 17:40:24 status unpacked subversion 1.6.6dfsg-2ubuntu1.2
2011-03-30 17:40:24 status unpacked subversion 1.6.6dfsg-2ubuntu1.2
2011-03-30 17:40:24 status unpacked subversion 1.6.6dfsg-2ubuntu1.2
2011-03-30 17:40:24 status half-configured subversion 1.6.6dfsg-2ubuntu1.2
2011-03-30 17:40:25 status installed subversion 1.6.6dfsg-2ubuntu1.2
2011-03-30 17:40:25 configure libtiff-tools 3.9.2-2ubuntu0.5 3.9.2-2ubuntu0.5
2011-03-30 17:40:25 status unpacked libtiff-tools 3.9.2-2ubuntu0.5
2011-03-30 17:40:25 status half-configured libtiff-tools 3.9.2-2ubuntu0.5
2011-03-30 17:40:25 status installed libtiff-tools 3.9.2-2ubuntu0.5
2011-03-30 17:40:25 configure samba-common 2:3.4.7~dfsg-1ubuntu3.5 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:25 status unpacked samba-common 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:25 status unpacked samba-common 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:25 status unpacked samba-common 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:25 status unpacked samba-common 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:25 status half-configured samba-common 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:26 status installed samba-common 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:26 configure libwbclient0 2:3.4.7~dfsg-1ubuntu3.5 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:26 status unpacked libwbclient0 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:26 status half-configured libwbclient0 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:26 status installed libwbclient0 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:26 configure smbclient 2:3.4.7~dfsg-1ubuntu3.5 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:26 status unpacked smbclient 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:26 status half-configured smbclient 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:26 status installed smbclient 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:26 configure winbind 2:3.4.7~dfsg-1ubuntu3.5 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:26 status unpacked winbind 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:26 status unpacked winbind 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:26 status unpacked winbind 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:26 status unpacked winbind 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:26 status half-configured winbind 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:27 status installed winbind 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:27 configure linux-libc-dev 2.6.32-30.59 2.6.32-30.59
2011-03-30 17:40:27 status unpacked linux-libc-dev 2.6.32-30.59
2011-03-30 17:40:27 status half-configured linux-libc-dev 2.6.32-30.59
2011-03-30 17:40:27 status installed linux-libc-dev 2.6.32-30.59
2011-03-30 17:40:27 configure samba-common-bin 2:3.4.7~dfsg-1ubuntu3.5 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:27 status unpacked samba-common-bin 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:27 status half-configured samba-common-bin 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:27 update-alternatives: run with --install /usr/bin/nmblookup nmblookup /usr/bin/nmblookup.samba3 0 --slave /usr/share/man/man1/nmblookup.1.gz nmblookup.1.gz /usr/share/man/man1/nmblookup.samba3.1.gz
2011-03-30 17:40:27 update-alternatives: run with --install /usr/bin/net net /usr/bin/net.samba3 10 --slave /usr/share/man/man8/net.8.gz net.8.gz /usr/share/man/man8/net.samba3.8.gz
2011-03-30 17:40:27 update-alternatives: run with --install /usr/bin/testparm testparm /usr/bin/testparm.samba3 10 --slave /usr/share/man/man1/testparm.1.gz testparm.1.gz /usr/share/man/man1/testparm.samba3.1.gz
2011-03-30 17:40:27 status installed samba-common-bin 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:27 configure ssh 1:5.3p1-3ubuntu6 1:5.3p1-3ubuntu6
2011-03-30 17:40:27 status unpacked ssh 1:5.3p1-3ubuntu6
2011-03-30 17:40:27 status half-configured ssh 1:5.3p1-3ubuntu6
2011-03-30 17:40:27 status installed ssh 1:5.3p1-3ubuntu6
2011-03-30 17:40:27 configure ssh-askpass-gnome 1:5.3p1-3ubuntu6 1:5.3p1-3ubuntu6
2011-03-30 17:40:27 status unpacked ssh-askpass-gnome 1:5.3p1-3ubuntu6
2011-03-30 17:40:27 status half-configured ssh-askpass-gnome 1:5.3p1-3ubuntu6
2011-03-30 17:40:27 update-alternatives: run with --quiet --install /usr/bin/ssh-askpass ssh-askpass /usr/lib/openssh/gnome-ssh-askpass 30 --slave /usr/share/man/man1/ssh-askpass.1.gz ssh-askpass.1.gz /usr/share/man/man1/gnome-ssh-askpass.1.gz
2011-03-30 17:40:27 status installed ssh-askpass-gnome 1:5.3p1-3ubuntu6
2011-03-30 17:40:28 configure xulrunner-1.9.2 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:28 status unpacked xulrunner-1.9.2 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:28 status unpacked xulrunner-1.9.2 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:28 status unpacked xulrunner-1.9.2 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:28 status half-configured xulrunner-1.9.2 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:28 update-alternatives: run with --install /usr/bin/xulrunner xulrunner /usr/bin/xulrunner-1.9.2 50
2011-03-30 17:40:28 update-alternatives: link group xulrunner updated to point to /usr/bin/xulrunner-1.9.2
2011-03-30 17:40:28 status installed xulrunner-1.9.2 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:28 configure libsmbclient 2:3.4.7~dfsg-1ubuntu3.5 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:28 status unpacked libsmbclient 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:28 status half-configured libsmbclient 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:28 status installed libsmbclient 2:3.4.7~dfsg-1ubuntu3.5
2011-03-30 17:40:28 configure firefox-branding 3.6.16+build1+nobinonly-0ubuntu0.10.04.1 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:28 status unpacked firefox-branding 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:28 status half-configured firefox-branding 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:28 status installed firefox-branding 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:28 configure firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:28 status unpacked firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:28 status unpacked firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:28 status unpacked firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:28 status unpacked firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:29 status unpacked firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:29 status unpacked firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:29 status unpacked firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:29 status unpacked firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:29 status unpacked firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:29 status unpacked firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:29 status half-configured firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:29 update-alternatives: run with --install /usr/bin/x-www-browser x-www-browser /usr/bin/firefox 40
2011-03-30 17:40:29 status installed firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:29 configure firefox-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:29 status unpacked firefox-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:29 status half-configured firefox-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:29 update-alternatives: run with --install /usr/bin/gnome-www-browser gnome-www-browser /usr/bin/firefox 40
2011-03-30 17:40:29 status installed firefox-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-03-30 17:40:29 trigproc libc-bin 2.11.1-0ubuntu7.8 2.11.1-0ubuntu7.8
2011-03-30 17:40:29 status half-configured libc-bin 2.11.1-0ubuntu7.8
2011-03-30 17:40:30 status installed libc-bin 2.11.1-0ubuntu7.8
2011-03-30 18:18:50 startup archives unpack
2011-03-30 18:18:50 install libsexy2 <nenio> 0.1.11-2build2
2011-03-30 18:18:50 status half-installed libsexy2 0.1.11-2build2
2011-03-30 18:18:51 status unpacked libsexy2 0.1.11-2build2
2011-03-30 18:18:51 status unpacked libsexy2 0.1.11-2build2
2011-03-30 18:18:51 install xchat-common <nenio> 2.8.6-4ubuntu5
2011-03-30 18:18:51 status half-installed xchat-common 2.8.6-4ubuntu5
2011-03-30 18:18:52 status unpacked xchat-common 2.8.6-4ubuntu5
2011-03-30 18:18:52 status unpacked xchat-common 2.8.6-4ubuntu5
2011-03-30 18:18:52 install xchat <nenio> 2.8.6-4ubuntu5
2011-03-30 18:18:52 status half-installed xchat 2.8.6-4ubuntu5
2011-03-30 18:18:53 status triggers-pending man-db 2.5.7-2ubuntu1
2011-03-30 18:18:53 status half-installed xchat 2.8.6-4ubuntu5
2011-03-30 18:18:53 status triggers-pending desktop-file-utils 0.16-0ubuntu2
2011-03-30 18:18:53 status half-installed xchat 2.8.6-4ubuntu5
2011-03-30 18:18:53 status triggers-pending python-gmenu 2.30.0-0ubuntu4
2011-03-30 18:18:53 status half-installed xchat 2.8.6-4ubuntu5
2011-03-30 18:18:54 status unpacked xchat 2.8.6-4ubuntu5
2011-03-30 18:18:54 status unpacked xchat 2.8.6-4ubuntu5
2011-03-30 18:18:54 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2011-03-30 18:18:54 status half-configured man-db 2.5.7-2ubuntu1
2011-03-30 18:18:55 status installed man-db 2.5.7-2ubuntu1
2011-03-30 18:18:55 trigproc desktop-file-utils 0.16-0ubuntu2 0.16-0ubuntu2
2011-03-30 18:18:55 status half-configured desktop-file-utils 0.16-0ubuntu2
2011-03-30 18:18:55 status installed desktop-file-utils 0.16-0ubuntu2
2011-03-30 18:18:55 trigproc python-gmenu 2.30.0-0ubuntu4 2.30.0-0ubuntu4
2011-03-30 18:18:55 status half-configured python-gmenu 2.30.0-0ubuntu4
2011-03-30 18:18:56 status installed python-gmenu 2.30.0-0ubuntu4
2011-03-30 18:18:56 status triggers-pending python-support 1.0.4ubuntu1
2011-03-30 18:18:56 trigproc python-support 1.0.4ubuntu1 1.0.4ubuntu1
2011-03-30 18:18:56 status half-configured python-support 1.0.4ubuntu1
2011-03-30 18:18:56 status installed python-support 1.0.4ubuntu1
2011-03-30 18:18:57 startup packages configure
2011-03-30 18:18:57 configure libsexy2 0.1.11-2build2 0.1.11-2build2
2011-03-30 18:18:57 status unpacked libsexy2 0.1.11-2build2
2011-03-30 18:18:57 status half-configured libsexy2 0.1.11-2build2
2011-03-30 18:18:57 status installed libsexy2 0.1.11-2build2
2011-03-30 18:18:57 status triggers-pending libc-bin 2.11.1-0ubuntu7.8
2011-03-30 18:18:57 configure xchat-common 2.8.6-4ubuntu5 2.8.6-4ubuntu5
2011-03-30 18:18:57 status unpacked xchat-common 2.8.6-4ubuntu5
2011-03-30 18:18:57 status half-configured xchat-common 2.8.6-4ubuntu5
2011-03-30 18:18:58 status installed xchat-common 2.8.6-4ubuntu5
2011-03-30 18:18:58 configure xchat 2.8.6-4ubuntu5 2.8.6-4ubuntu5
2011-03-30 18:18:58 status unpacked xchat 2.8.6-4ubuntu5
2011-03-30 18:18:58 status half-configured xchat 2.8.6-4ubuntu5
2011-03-30 18:18:58 status installed xchat 2.8.6-4ubuntu5
2011-03-30 18:18:58 trigproc libc-bin 2.11.1-0ubuntu7.8 2.11.1-0ubuntu7.8
2011-03-30 18:18:58 status half-configured libc-bin 2.11.1-0ubuntu7.8
2011-03-30 18:18:58 status installed libc-bin 2.11.1-0ubuntu7.8
2011-03-30 18:19:04 startup archives unpack
2011-03-30 18:19:05 install xchat-gnome-common <nenio> 1:0.26.1-1ubuntu2
2011-03-30 18:19:05 status half-installed xchat-gnome-common 1:0.26.1-1ubuntu2
2011-03-30 18:19:05 status triggers-pending hicolor-icon-theme 0.11-1
2011-03-30 18:19:05 status half-installed xchat-gnome-common 1:0.26.1-1ubuntu2
2011-03-30 18:19:05 status triggers-pending desktop-file-utils 0.16-0ubuntu2
2011-03-30 18:19:05 status half-installed xchat-gnome-common 1:0.26.1-1ubuntu2
2011-03-30 18:19:05 status triggers-pending python-gmenu 2.30.0-0ubuntu4
2011-03-30 18:19:05 status half-installed xchat-gnome-common 1:0.26.1-1ubuntu2
2011-03-30 18:19:07 status unpacked xchat-gnome-common 1:0.26.1-1ubuntu2
2011-03-30 18:19:07 status unpacked xchat-gnome-common 1:0.26.1-1ubuntu2
2011-03-30 18:19:07 install xchat-gnome <nenio> 1:0.26.1-1ubuntu2
2011-03-30 18:19:07 status half-installed xchat-gnome 1:0.26.1-1ubuntu2
2011-03-30 18:19:07 status triggers-pending man-db 2.5.7-2ubuntu1
2011-03-30 18:19:07 status half-installed xchat-gnome 1:0.26.1-1ubuntu2
2011-03-30 18:19:08 status unpacked xchat-gnome 1:0.26.1-1ubuntu2
2011-03-30 18:19:08 status unpacked xchat-gnome 1:0.26.1-1ubuntu2
2011-03-30 18:19:08 trigproc hicolor-icon-theme 0.11-1 0.11-1
2011-03-30 18:19:08 status half-configured hicolor-icon-theme 0.11-1
2011-03-30 18:19:09 status installed hicolor-icon-theme 0.11-1
2011-03-30 18:19:09 trigproc desktop-file-utils 0.16-0ubuntu2 0.16-0ubuntu2
2011-03-30 18:19:09 status half-configured desktop-file-utils 0.16-0ubuntu2
2011-03-30 18:19:09 status installed desktop-file-utils 0.16-0ubuntu2
2011-03-30 18:19:09 trigproc python-gmenu 2.30.0-0ubuntu4 2.30.0-0ubuntu4
2011-03-30 18:19:09 status half-configured python-gmenu 2.30.0-0ubuntu4
2011-03-30 18:19:09 status installed python-gmenu 2.30.0-0ubuntu4
2011-03-30 18:19:09 status triggers-pending python-support 1.0.4ubuntu1
2011-03-30 18:19:09 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2011-03-30 18:19:09 status half-configured man-db 2.5.7-2ubuntu1
2011-03-30 18:19:10 status installed man-db 2.5.7-2ubuntu1
2011-03-30 18:19:10 trigproc python-support 1.0.4ubuntu1 1.0.4ubuntu1
2011-03-30 18:19:10 status half-configured python-support 1.0.4ubuntu1
2011-03-30 18:19:10 status installed python-support 1.0.4ubuntu1
2011-03-30 18:19:11 startup packages configure
2011-03-30 18:19:11 configure xchat-gnome-common 1:0.26.1-1ubuntu2 1:0.26.1-1ubuntu2
2011-03-30 18:19:11 status unpacked xchat-gnome-common 1:0.26.1-1ubuntu2
2011-03-30 18:19:11 status half-configured xchat-gnome-common 1:0.26.1-1ubuntu2
2011-03-30 18:19:12 status installed xchat-gnome-common 1:0.26.1-1ubuntu2
2011-03-30 18:19:12 configure xchat-gnome 1:0.26.1-1ubuntu2 1:0.26.1-1ubuntu2
2011-03-30 18:19:12 status unpacked xchat-gnome 1:0.26.1-1ubuntu2
2011-03-30 18:19:12 status half-configured xchat-gnome 1:0.26.1-1ubuntu2
2011-03-30 18:19:12 status installed xchat-gnome 1:0.26.1-1ubuntu2

```

Some playing around:
```

$ pulseaudio --log-level=4
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
I: core-util.c: Failed to acquire high-priority scheduling: Input/output error
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: x86_64-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux x86_64 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011
D: main.c: Found 8 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 6d706bc343f22a6dacc38adc4d6cead4.
I: main.c: Session ID is 6d706bc343f22a6dacc38adc4d6cead4-1301694897.547086-77214559.
I: main.c: Using runtime directory $HOME/.pulse/6d706bc343f22a6dacc38adc4d6cead4-runtime.
I: main.c: Using state directory $HOME/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
[0_0->ret=1][5][user@PC][~]$  rm -rf $HOME/.pulse*
forvi&#349;i&#285;is '$HOME/.pulse/6d706bc343f22a6dacc38adc4d6cead4-default-sink'
forvi&#349;i&#285;is '$HOME/.pulse/6d706bc343f22a6dacc38adc4d6cead4-default-source'
forvi&#349;i&#285;is '$HOME/.pulse/6d706bc343f22a6dacc38adc4d6cead4-stream-volumes.tdb'
forvi&#349;i&#285;is '$HOME/.pulse/6d706bc343f22a6dacc38adc4d6cead4-runtime'
forvi&#349;i&#285;is '$HOME/.pulse/6d706bc343f22a6dacc38adc4d6cead4-device-volumes.tdb'
forvi&#349;i&#285;is '$HOME/.pulse/6d706bc343f22a6dacc38adc4d6cead4-card-database.tdb'
rm: ne eblas forigi '$HOME/.pulse/.nfs0000000000781f8700000030': Device or resource busy
forvi&#349;i&#285;is '$HOME/.pulse-cookie'
[0_0->ret=1][6][user@PC][~]$  pulseaudio --log-level=4
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
I: core-util.c: Failed to acquire high-priority scheduling: Input/output error
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: x86_64-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux x86_64 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011
D: main.c: Found 8 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 6d706bc343f22a6dacc38adc4d6cead4.
I: main.c: Session ID is 6d706bc343f22a6dacc38adc4d6cead4-1301694897.547086-77214559.
I: main.c: Using runtime directory $HOME/.pulse/6d706bc343f22a6dacc38adc4d6cead4-runtime.
I: main.c: Using state directory $HOME/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3 SSE4_1 SSE4_2
I: svolume_mmx.c: Initialising MMX optimized functions.
I: remap_mmx.c: Initialising MMX optimized remappers.
I: svolume_sse.c: Initialising SSE2 optimized functions.
I: remap_sse.c: Initialising SSE2 optimized remappers.
I: sconv_sse.c: Initialising SSE2 optimized conversions.
D: memblock.c: Using shared memory pool with 1024 slots of size 64,0 KiB each, total size is 64,0 MiB, maximum usable slot size is 65472
D: database-tdb.c: Opened TDB database '$HOME/.pulse/6d706bc343f22a6dacc38adc4d6cead4-device-volumes.tdb'
I: module-device-restore.c: Sucessfully opened database file '$HOME/.pulse/6d706bc343f22a6dacc38adc4d6cead4-device-volumes'.
I: module.c: Loaded "module-device-restore" (index: #0; argument: "").
D: database-tdb.c: Opened TDB database '$HOME/.pulse/6d706bc343f22a6dacc38adc4d6cead4-stream-volumes.tdb'
I: module-stream-restore.c: Sucessfully opened database file '$HOME/.pulse/6d706bc343f22a6dacc38adc4d6cead4-stream-volumes'.
I: module.c: Loaded "module-stream-restore" (index: #1; argument: "").
D: database-tdb.c: Opened TDB database '$HOME/.pulse/6d706bc343f22a6dacc38adc4d6cead4-card-database.tdb'
I: module-card-restore.c: Sucessfully opened database file '$HOME/.pulse/6d706bc343f22a6dacc38adc4d6cead4-card-database'.
I: module.c: Loaded "module-card-restore" (index: #2; argument: "").
I: module.c: Loaded "module-augment-properties" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-udev-detect.so': success
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
D: module-udev-detect.c: /devices/pci0000:00/0000:00:1b.0/sound/card0 is busy: yes
I: module-udev-detect.c: Found 1 cards.
I: module.c: Loaded "module-udev-detect" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-bluetooth-discover.so': success
D: dbus-util.c: Successfully connected to D-Bus system bus 57e8292213597f836acecbc64d963e0c as :1.502
D: bluetooth-util.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: bluetooth-util.c: Bluetooth daemon is apparently not available.
I: module.c: Loaded "module-bluetooth-discover" (index: #5; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-esound-protocol-unix.so': success
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
I: module.c: Unloading "module-device-restore" (index: #0).
I: module.c: Unloaded "module-device-restore" (index: #0).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-stream-restore" (index: #1).
I: module.c: Unloaded "module-stream-restore" (index: #1).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-card-restore" (index: #2).
I: module.c: Unloaded "module-card-restore" (index: #2).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-augment-properties" (index: #3).
I: module.c: Unloaded "module-augment-properties" (index: #3).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-udev-detect" (index: #4).
I: module.c: Unloaded "module-udev-detect" (index: #4).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-bluetooth-discover" (index: #5).
I: module.c: Unloaded "module-bluetooth-discover" (index: #5).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: main.c: Daemon terminated.

```

```

$  dpkg -l | grep pulseaudio*
ii  gstreamer0.10-pulseaudio              0.10.21-1ubuntu3                                GStreamer plugin for PulseAudio
ii  libsdl1.2debian-pulseaudio            1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and Pulse
ii  pulseaudio                            1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 PulseAudio sound server
ii  pulseaudio-esound-compat              1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 PulseAudio ESD compatibility layer
ii  pulseaudio-module-bluetooth           1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 Bluetooth module for PulseAudio sound server
ii  pulseaudio-module-gconf               1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 GConf module for PulseAudio sound server
ii  pulseaudio-module-x11                 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 X11 module for PulseAudio sound server
ii  pulseaudio-utils                      1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 Command line tools for the PulseAudio sound 
$  dpkg -l | grep alsa*
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  alsamixergui                          0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard
ii  alsaplayer-alsa                       0.99.80-5                                       PCM player designed for ALSA (ALSA output mo
ii  alsaplayer-common                     0.99.80-5                                       PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                        0.99.80-5                                       PCM player designed for ALSA (GTK+ version)
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                       0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
ii  libboost-signals1.40-dev              1.40.0-4ubuntu4                                 managed signals and slots library for C++
ii  libboost-signals1.40.0                1.40.0-4ubuntu4                                 managed signals and slots library for C++
ii  libcanberra-gtk-module                0.22-1ubuntu2                                   translates Gtk+ widgets signals to event sou

```

What I got when starting Amarok:
```

KDE detected that one or more internal sound devices were removed.
Do you want KDE to permanently forget about these devices?
This is the list of devices KDE thinks can be removed:
Capture: HDA Intel (ALC662 rev1 Analog)
Output: HDA Intel (ALC662 rev1 Analog)

```

```

$ groups $USER
me : audio *****

```

---

### Post by lidex on 2011-04-01
You're running kde on top of gnome or just kubuntu?
Try removing your pulse config and then reboot:
```

rm -r ~/.pulse ~/.pulse-cookie 

```
**Reboot**
Now this - alsa info script:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by KIAaze on 2011-04-04
Here's the result:
[http://www.alsa-project.org/db/?f=2b94230f979e1bda7ef5ddba44aa3ea18428fca6](http://www.alsa-project.org/db/?f=2b94230f979e1bda7ef5ddba44aa3ea18428fca6)

Here's a second one:
[http://www.alsa-project.org/db/?f=605d7e090b092b4bfd68b0d4dc9833a8cd15ef8b](http://www.alsa-project.org/db/?f=605d7e090b092b4bfd68b0d4dc9833a8cd15ef8b)

This one is from after running:
```
$  pulseaudio --log-level=4 >debug.log 2>&1
$  sudo console-kit-daemon start
$  pulseaudio --log-level=4 >debug2.log 2>&1

```

debug.log:
```
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
I: core-util.c: Failed to acquire high-priority scheduling: Input/output error
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: x86_64-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux x86_64 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011
D: main.c: Found 8 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 6d706bc343f22a6dacc38adc4d6cead4.
I: main.c: Using runtime directory ~/.pulse/6d706bc343f22a6dacc38adc4d6cead4-runtime.
I: main.c: Using state directory ~/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3 SSE4_1 SSE4_2 
I: svolume_mmx.c: Initialising MMX optimized functions.
I: remap_mmx.c: Initialising MMX optimized remappers.
I: svolume_sse.c: Initialising SSE2 optimized functions.
I: remap_sse.c: Initialising SSE2 optimized remappers.
I: sconv_sse.c: Initialising SSE2 optimized conversions.
D: memblock.c: Using shared memory pool with 1024 slots of size 64,0 KiB each, total size is 64,0 MiB, maximum usable slot size is 65472
D: database-tdb.c: Opened TDB database '~/.pulse/6d706bc343f22a6dacc38adc4d6cead4-device-volumes.tdb'
I: module-device-restore.c: Sucessfully opened database file '~/.pulse/6d706bc343f22a6dacc38adc4d6cead4-device-volumes'.
I: module.c: Loaded "module-device-restore" (index: #0; argument: "").
D: database-tdb.c: Opened TDB database '~/.pulse/6d706bc343f22a6dacc38adc4d6cead4-stream-volumes.tdb'
I: module-stream-restore.c: Sucessfully opened database file '~/.pulse/6d706bc343f22a6dacc38adc4d6cead4-stream-volumes'.
I: module.c: Loaded "module-stream-restore" (index: #1; argument: "").
D: database-tdb.c: Opened TDB database '~/.pulse/6d706bc343f22a6dacc38adc4d6cead4-card-database.tdb'
I: module-card-restore.c: Sucessfully opened database file '~/.pulse/6d706bc343f22a6dacc38adc4d6cead4-card-database'.
I: module.c: Loaded "module-card-restore" (index: #2; argument: "").
I: module.c: Loaded "module-augment-properties" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-udev-detect.so': success
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
D: module-udev-detect.c: /devices/pci0000:00/0000:00:1b.0/sound/card0 is busy: no
D: module-udev-detect.c: Loading module-alsa-card with arguments 'device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"'
D: dbus-util.c: Successfully connected to D-Bus session bus 9003b163f3d20abaa5973ff64d99b5d4 as :1.422
D: reserve-wrap.c: Successfully acquired reservation lock on device 'Audio0'
D: alsa-mixer.c: Looking at profile output:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-mono+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-mono+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-mono+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-mono+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:analog-stereo supported.
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:analog-stereo+input:analog-stereo supported.
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround40:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-41
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround41:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-50
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround50:0
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-51
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround51:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:surround71:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:iec958-stereo supported.
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:iec958-stereo+input:analog-stereo supported.
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:hdmi-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-mixer.c: Looking at profile input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile input:analog-stereo supported.
D: alsa-mixer.c: Looking at profile input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
I: card.c: Created 0 "alsa_card.pci-0000_00_1b.0"
D: reserve-wrap.c: Successfully create reservation lock monitor for device 'Audio0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
I: alsa-sink.c: Successfully opened device front:0.
I: alsa-sink.c: Selected mapping 'Analog Stereo' (analog-stereo).
I: alsa-sink.c: Successfully enabled mmap() mode.
I: alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-mixer.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-mixer.c: Successfully attached to mixer 'hw:0'
D: alsa-mixer.c: Probing path 'analog-output'
D: alsa-mixer.c: Probing path 'analog-output-speaker'
D: alsa-mixer.c: Probing path 'analog-output-speaker'
D: alsa-mixer.c: Probe of element 'Desktop Speaker' failed.
D: alsa-mixer.c: Probing path 'analog-output-headphones'
D: alsa-mixer.c: Probing path 'analog-output-headphones'
D: alsa-mixer.c: Probe of element 'Headphone2' failed.
D: alsa-mixer.c: Probing path 'analog-output-mono'
D: alsa-mixer.c: Probe of element 'Master Mono' failed.
D: alsa-mixer.c: Probing path 'analog-output-lfe-on-mono'
D: alsa-mixer.c: Probe of element 'Master Mono' failed.
D: alsa-sink.c: Probed mixer paths:
D: alsa-mixer.c: Path Set 0x1a1f4a0, direction=1, probed=yes
D: alsa-mixer.c: Path analog-output (Analog Output), direction=1, priority=99, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=64, min_dB=-179, max_dB=0
D: alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
D: alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=3, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: alsa-mixer.c: Element Speaker, direction=1, switch=1, volume=2, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: alsa-mixer.c: Element Front, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=yes
D: alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Path analog-output-speaker (Analog Speakers), direction=1, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=64, min_dB=-243, max_dB=0
D: alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
D: alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=3, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: alsa-mixer.c: Element Speaker, direction=1, switch=1, volume=1, enumeration=0, required=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Front, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=yes
D: alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Path analog-output-headphones (Analog Headphones), direction=1, priority=90, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=64, min_dB=-179, max_dB=0
D: alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
D: alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=1, enumeration=0, required=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Speaker, direction=1, switch=2, volume=2, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: alsa-mixer.c: Element Front, direction=1, switch=2, volume=2, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Added 3 ports
I: sink.c: Created sink 0 "alsa_output.pci-0000_00_1b.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink.c:     alsa.resolution_bits = "16"
I: sink.c:     device.api = "alsa"
I: sink.c:     device.class = "sound"
I: sink.c:     alsa.class = "generic"
I: sink.c:     alsa.subclass = "generic-mix"
I: sink.c:     alsa.name = "ALC662 rev1 Analog"
I: sink.c:     alsa.id = "ALC662 rev1 Analog"
I: sink.c:     alsa.subdevice = "0"
I: sink.c:     alsa.subdevice_name = "subdevice #0"
I: sink.c:     alsa.device = "0"
I: sink.c:     alsa.card = "0"
I: sink.c:     alsa.card_name = "HDA Intel"
I: sink.c:     alsa.long_card_name = "HDA Intel at 0xfb120000 irq 22"
I: sink.c:     alsa.driver_name = "snd_hda_intel"
I: sink.c:     device.bus_path = "pci-0000:00:1b.0"
I: sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: sink.c:     device.bus = "pci"
I: sink.c:     device.vendor.id = "8086"
I: sink.c:     device.vendor.name = "Intel Corporation"
I: sink.c:     device.product.id = "3b56"
I: sink.c:     device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
I: sink.c:     device.form_factor = "internal"
I: sink.c:     device.string = "front:0"
I: sink.c:     device.buffering.buffer_size = "352768"
I: sink.c:     device.buffering.fragment_size = "176384"
I: sink.c:     device.access_mode = "mmap+timer"
I: sink.c:     device.profile.name = "analog-stereo"
I: sink.c:     device.profile.description = "Analog Stereo"
I: sink.c:     device.description = "Internal Audio Analog Stereo"
I: sink.c:     alsa.mixer_name = "Realtek ALC662 rev1"
I: sink.c:     alsa.components = "HDA:10ec0662,80860038,00100101"
I: sink.c:     module-udev-detect.discovered = "1"
I: sink.c:     device.icon_name = "audio-card-pci"
D: core-subscribe.c: Dropped redundant event due to change event.
I: source.c: Created source 0 "alsa_output.pci-0000_00_1b.0.analog-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of Internal Audio Analog Stereo"
I: source.c:     device.class = "monitor"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "HDA Intel"
I: source.c:     alsa.long_card_name = "HDA Intel at 0xfb120000 irq 22"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "pci-0000:00:1b.0"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "8086"
I: source.c:     device.vendor.name = "Intel Corporation"
I: source.c:     device.product.id = "3b56"
I: source.c:     device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
I: source.c:     device.form_factor = "internal"
I: source.c:     device.string = "0"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-sink.c: Using 2,0 fragments of size 176384 bytes (999,91ms), buffer size is 352768 bytes (1999,82ms)
I: alsa-sink.c: Time scheduling watermark is 20,00ms
D: alsa-sink.c: hwbuf_unused=0
D: alsa-sink.c: setting avail_min=87310
D: alsa-mixer.c: Activating path analog-output-speaker
D: alsa-mixer.c: Path analog-output-speaker (Analog Speakers), direction=1, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=64, min_dB=-243, max_dB=0
D: alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
D: alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=3, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: alsa-mixer.c: Element Speaker, direction=1, switch=1, volume=1, enumeration=0, required=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Front, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=yes
D: alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
I: alsa-sink.c: Hardware volume ranges from -243,00 dB to 0,00 dB.
I: alsa-sink.c: No particular base volume set, fixing to 0 dB
I: alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
I: alsa-sink.c: Using hardware mute control.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 88192
D: alsa-util.c:   period_size  : 44096
D: alsa-util.c:   period_time  : 999909
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 87310
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 6205960286516543488
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 6205960286516543488
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 88192
D: alsa-util.c:   period_size  : 44096
D: alsa-util.c:   period_time  : 999909
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 87310
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 6205960286516543488
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 6205960286516543488
D: alsa-util.c:   appl_ptr     : 0
D: alsa-util.c:   hw_ptr       : 0
D: alsa-sink.c: Read hardware volume: 0:  71% 1:  71%
D: alsa-sink.c: Thread starting up
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 4, which is lower than the requested 5.
I: alsa-sink.c: Starting playback.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
I: alsa-source.c: Successfully opened device front:0.
I: alsa-source.c: Selected mapping 'Analog Stereo' (analog-stereo).
I: alsa-source.c: Successfully enabled mmap() mode.
I: alsa-source.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-mixer.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-mixer.c: Successfully attached to mixer 'hw:0'
D: alsa-mixer.c: Probing path 'analog-input'
D: alsa-mixer.c: Probing path 'analog-input-microphone'
D: alsa-mixer.c: Probe of element 'Mic' failed.
D: alsa-mixer.c: Probing path 'analog-input-linein'
D: alsa-mixer.c: Probe of element 'Line' failed.
D: alsa-mixer.c: Probing path 'analog-input'
D: alsa-mixer.c: Probe of element 'Aux' failed.
D: alsa-mixer.c: Probing path 'analog-input-video'
D: alsa-mixer.c: Probe of element 'Video' failed.
D: alsa-mixer.c: Probing path 'analog-input-video'
D: alsa-mixer.c: Probe of element 'TV Tuner' failed.
D: alsa-mixer.c: Probing path 'analog-input-radio'
D: alsa-mixer.c: Probe of element 'FM' failed.
D: alsa-mixer.c: Probing path 'analog-input'
D: alsa-mixer.c: Probe of element 'Mic/Line' failed.
D: alsa-source.c: Probed mixer paths:
D: alsa-mixer.c: Path Set 0x1a33b20, direction=2, probed=yes
D: alsa-mixer.c: Path analog-input (Analog Input), direction=2, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=31, min_dB=-13,5, max_dB=33
D: alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, enumeration=0, required=2, required_absent=0, mask=0x4043e00000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Input Source, direction=2, switch=0, volume=0, enumeration=1, required=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
D: alsa-mixer.c: Option Mic (input-microphone-1/Microphone 1) index=0, priority=20
D: alsa-mixer.c: Option Front Mic (input-microphone-2/Microphone 2) index=1, priority=19
D: alsa-mixer.c: Option Line (input-linein/Line-In) index=2, priority=18
D: alsa-mixer.c: Setting input-microphone-1 (Microphone 1) priority=20
D: alsa-mixer.c: Setting input-microphone-2 (Microphone 2) priority=19
D: alsa-mixer.c: Setting input-linein (Line-In) priority=18
D: alsa-mixer.c: Added 3 ports
D: core-subscribe.c: Dropped redundant event due to change event.
I: source.c: Created source 1 "alsa_input.pci-0000_00_1b.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     alsa.resolution_bits = "16"
I: source.c:     device.api = "alsa"
I: source.c:     device.class = "sound"
I: source.c:     alsa.class = "generic"
I: source.c:     alsa.subclass = "generic-mix"
I: source.c:     alsa.name = "ALC662 rev1 Analog"
I: source.c:     alsa.id = "ALC662 rev1 Analog"
I: source.c:     alsa.subdevice = "0"
I: source.c:     alsa.subdevice_name = "subdevice #0"
I: source.c:     alsa.device = "0"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "HDA Intel"
I: source.c:     alsa.long_card_name = "HDA Intel at 0xfb120000 irq 22"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "pci-0000:00:1b.0"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "8086"
I: source.c:     device.vendor.name = "Intel Corporation"
I: source.c:     device.product.id = "3b56"
I: source.c:     device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
I: source.c:     device.form_factor = "internal"
I: source.c:     device.string = "front:0"
I: source.c:     device.buffering.buffer_size = "352768"
I: source.c:     device.buffering.fragment_size = "176384"
I: source.c:     device.access_mode = "mmap+timer"
I: source.c:     device.profile.name = "analog-stereo"
I: source.c:     device.profile.description = "Analog Stereo"
I: source.c:     device.description = "Internal Audio Analog Stereo"
I: source.c:     alsa.mixer_name = "Realtek ALC662 rev1"
I: source.c:     alsa.components = "HDA:10ec0662,80860038,00100101"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-source.c: Using 2,0 fragments of size 176384 bytes (999,91ms), buffer size is 352768 bytes (1999,82ms)
I: alsa-source.c: Time scheduling watermark is 20,00ms
D: alsa-source.c: hwbuf_unused=0
D: alsa-source.c: setting avail_min=87310
D: alsa-mixer.c: Activating path analog-input
D: alsa-mixer.c: Path analog-input (Analog Input), direction=2, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=31, min_dB=-13,5, max_dB=33
D: alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, enumeration=0, required=2, required_absent=0, mask=0x4043e00000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Input Source, direction=2, switch=0, volume=0, enumeration=1, required=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
D: alsa-mixer.c: Option Mic (input-microphone-1/Microphone 1) index=0, priority=20
D: alsa-mixer.c: Option Front Mic (input-microphone-2/Microphone 2) index=1, priority=19
D: alsa-mixer.c: Option Line (input-linein/Line-In) index=2, priority=18
D: alsa-mixer.c: Setting input-microphone-1 (Microphone 1) priority=20
D: alsa-mixer.c: Setting input-microphone-2 (Microphone 2) priority=19
D: alsa-mixer.c: Setting input-linein (Line-In) priority=18
I: alsa-source.c: Hardware volume ranges from -13,50 dB to 33,00 dB.
I: alsa-source.c: Fixing base volume to -33,00 dB
I: alsa-source.c: Using hardware volume control. Hardware dB scale supported.
I: alsa-source.c: Using hardware mute control.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 88192
D: alsa-util.c:   period_size  : 44096
D: alsa-util.c:   period_time  : 999909
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 87310
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 6205960286516543488
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 6205960286516543488
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 88192
D: alsa-util.c:   period_size  : 44096
D: alsa-util.c:   period_time  : 999909
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 87310
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 6205960286516543488
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 6205960286516543488
D: alsa-util.c:   appl_ptr     : 0
D: alsa-util.c:   hw_ptr       : 0
D: alsa-source.c: Read hardware volume: 0:  17% 1:  17%
D: alsa-source.c: Thread starting up
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 4, which is lower than the requested 5.
I: module.c: Loaded "module-alsa-card" (index: #4; argument: "device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"").
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:1b.0/sound/card0 (alsa_card.pci-0000_00_1b.0) module loaded.
I: module-udev-detect.c: Found 1 cards.
I: module.c: Loaded "module-udev-detect" (index: #5; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-bluetooth-discover.so': success
D: dbus-util.c: Successfully connected to D-Bus system bus f9a28c0758c07376cf84688a4d99b5c5 as :1.301
D: bluetooth-util.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: bluetooth-util.c: Bluetooth daemon is apparently not available.
I: module.c: Loaded "module-bluetooth-discover" (index: #6; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #7; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #8; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #9; argument: "").
I: module.c: Loaded "module-default-device-restore" (index: #10; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #11; argument: "").
I: module.c: Loaded "module-always-sink" (index: #12; argument: "").
I: module.c: Loaded "module-intended-roles" (index: #13; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.analog-stereo becomes idle, timeout in 5 seconds.
D: module-suspend-on-idle.c: Source alsa_input.pci-0000_00_1b.0.analog-stereo becomes idle, timeout in 5 seconds.
I: module.c: Loaded "module-suspend-on-idle" (index: #14; argument: "").
E: module-console-kit.c: GetSessionsForUnixUser() call failed: org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program /lib/dbus-1.0/dbus-daemon-launch-helper: Success
E: module.c: Failed to load  module "module-console-kit" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
I: module.c: Unloading "module-device-restore" (index: #0).
I: module.c: Unloaded "module-device-restore" (index: #0).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-stream-restore" (index: #1).
I: module.c: Unloaded "module-stream-restore" (index: #1).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-card-restore" (index: #2).
I: module.c: Unloaded "module-card-restore" (index: #2).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-augment-properties" (index: #3).
I: module.c: Unloaded "module-augment-properties" (index: #3).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-alsa-card" (index: #4).
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: core-subscribe.c: Dropped redundant event due to remove event.
D: core-subscribe.c: Dropped redundant event due to remove event.
D: core-subscribe.c: Dropped redundant event due to remove event.
D: core-subscribe.c: Dropped redundant event due to remove event.
D: alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 0 "alsa_output.pci-0000_00_1b.0.analog-stereo"
I: source.c: Freeing source 0 "alsa_output.pci-0000_00_1b.0.analog-stereo.monitor"
D: core-subscribe.c: Dropped redundant event due to remove event.
D: core-subscribe.c: Dropped redundant event due to remove event.
D: alsa-source.c: Thread shutting down
I: source.c: Freeing source 1 "alsa_input.pci-0000_00_1b.0.analog-stereo"
I: card.c: Freed 0 "alsa_card.pci-0000_00_1b.0"
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloaded "module-alsa-card" (index: #4).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-udev-detect" (index: #5).
I: module.c: Unloaded "module-udev-detect" (index: #5).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-bluetooth-discover" (index: #6).
I: module.c: Unloaded "module-bluetooth-discover" (index: #6).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-esound-protocol-unix" (index: #7).
I: module.c: Unloaded "module-esound-protocol-unix" (index: #7).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-native-protocol-unix" (index: #8).
I: module.c: Unloaded "module-native-protocol-unix" (index: #8).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-gconf" (index: #9).
I: module.c: Unloaded "module-gconf" (index: #9).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-default-device-restore" (index: #10).
I: module.c: Unloaded "module-default-device-restore" (index: #10).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-rescue-streams" (index: #11).
I: module.c: Unloaded "module-rescue-streams" (index: #11).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-always-sink" (index: #12).
I: module.c: Unloaded "module-always-sink" (index: #12).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-intended-roles" (index: #13).
I: module.c: Unloaded "module-intended-roles" (index: #13).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-suspend-on-idle" (index: #14).
I: module.c: Unloaded "module-suspend-on-idle" (index: #14).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: main.c: Daemon terminated.
```
debug2.log:
```
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
I: core-util.c: Failed to acquire high-priority scheduling: Input/output error
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: x86_64-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux x86_64 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011
D: main.c: Found 8 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 6d706bc343f22a6dacc38adc4d6cead4.
I: main.c: Using runtime directory ~/.pulse/6d706bc343f22a6dacc38adc4d6cead4-runtime.
I: main.c: Using state directory ~/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
```

Amarok still asks for removal of the intel device on first start and does not have sound, while VLC works correctly.
I have to start console-kit and pulseaudio after each reboot for this result.

---

### Post by KIAaze on 2011-04-04
Ok, problem "solved" with a potentially dangerous hack...

I noticed that I couldn't run users-admin.
Running it from a terminal gave me another dbus error message:
```
Liboobs-WARNING **: There was an unknown error communicating with the backends: Failed to execute program /lib/dbus-1.0/dbus-daemon-launch-helper: Success

```

Which led me to the following bug reports:
[http://bugs.gentoo.org/305309](http://bugs.gentoo.org/305309)
[https://bugs.launchpad.net/ubuntu/+source/system-tools-backends/+bug/574078](https://bugs.launchpad.net/ubuntu/+source/system-tools-backends/+bug/574078)

So I did a:
```
sudo chmod o+x /lib/dbus-1.0/dbus-daemon-launch-helper
```

Result:
```
$ ls -l /lib/dbus-1.0/dbus-daemon-launch-helper /usr/lib/dbus-1.0/dbus-daemon-launch-helper
-rwsr-xr-x 1 root messagebus 47520 2011-03-04 18:22 /lib/dbus-1.0/dbus-daemon-launch-helper
lrwxrwxrwx 1 root root          39 2011-03-30 17:38 /usr/lib/dbus-1.0/dbus-daemon-launch-helper -> /lib/dbus-1.0/dbus-daemon-launch-helper

```

Everything works again now after reboot: sounds, users-admin, restart button (shutdown probably too). :)

However, I'm just a bit worried about making dbus-daemon-launch-helper executable for others.
[B]What are its permissions on a normal ubuntu install?
Is it safe to make it executable for others, users?
[/B]

Should I add myself to the messagebus group instead?
Or should the whole sound/dbus stuff be set up so that it starts before I even log in?

edit: Problem solved by changing the GID for the messagebus user in /etc/passwd. It should match the messagebus group in /etc/group. Just fix that using a text editor as root, and it should work without the workaround.
cf:
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/295405](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/295405)
[https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/475503](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/475503)
[https://bugs.launchpad.net/ubuntu/+source/system-tools-backends/+bug/574078](https://bugs.launchpad.net/ubuntu/+source/system-tools-backends/+bug/574078)
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/750468](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/750468)

---

