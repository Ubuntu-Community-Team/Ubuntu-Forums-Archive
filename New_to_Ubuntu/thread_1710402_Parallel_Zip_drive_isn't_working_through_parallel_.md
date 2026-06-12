---
title: "Parallel Zip drive isn't working through parallel in 10.10"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2011-03-19
i'm trying to get the data off a mac formatted zip100 disk. the drive i got is an external SCSI/Parallel Zip 100 Plus (model Z100PLUS) that i'm trying to use through parallel.

:"cool story, bro" time:
i first tried to get it to work in ubuntu 10.10, but gave up after about an hour. everything i was reading wasnt working in ubuntu (most of it was circa '08 or older), and i read that the drive should work out of the box in XP (and there were programs to access mac formatted disks in XP). since i recently installed 10.10 it wasn't a great loss to install XP in that partition in an effort to get the data. after much wailing and gnashing of teeth i had only managed to see the drive in device manager. i could see the drive but it had a yellow exclamation point (Code: 10 device cannot start) so i gave up and reinstalled ubuntu. (off topic) i followed a guide on [_minimal desktop for ubuntu_]("http://minimal-desktop.blogspot.com/p/guide.html") and i love the result. Ubuntu with none of the fluff!

the reason i told you the story was to explain how i know what the device name that XP showed, which is "IMG VP1".

in my reading of the various guides, i have read that my LPT port should be set to EPP (or SPP, but that is not an option in my BIOS), the IRQ should be set to 7, and the IO address should be 378. i have done all of those already.

what i believe to be the relevant dmesg output:
```
**[14.121821] imm: Version 2.05 (for Linux 2.4.0)**
[14.179723] intel_rng: Firmware space is locked read-only. If you can't or
[14.179727] intel_rng: don't want to disable this in firmware setup, and if
[14.179730] intel_rng: you are certain that your system has a functional
[14.179733] intel_rng: RNG, try using the 'no_fwh_detect' option.
[14.310953] Linux agpgart interface v0.103
[14.401013] agpgart-intel 0000:00:00.0: Intel 915G Chipset
[14.401651] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[14.502081] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[14.522609] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[14.538019] parport_pc 00:06: reported by Plug and Play ACPI
[B][14.538082] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[14.540456] parport0: Device ID was 64 bytes while device told it would be 63 bytes
[14.540479] parport0 (addr 0): SCSI adapter, IMG VP1[/B]
[14.557912] Bluetooth: Core ver 2.15
[14.557946] NET: Registered protocol family 31
[14.557950] Bluetooth: HCI device and connection manager initialized
[14.557954] Bluetooth: HCI socket layer initialized
[14.589449] Bluetooth: Generic Bluetooth USB driver ver 0.6
**[14.611165] imm: Found device at ID 6, Attempting to use EPP 32 bit**
[14.611300] usbcore: registered new interface driver btusb
**[14.614258] imm: Found device at ID 6, Attempting to use PS/2**
[14.616040] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[B][14.616961] imm: Unable to establish communication
[14.623387] ppdev: user-space parallel port driver[/B]
```
NOTE: if i didn't find the right stuff, i would be happy to post the full dmesg output

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

imm
loop
# lp
```

from the dmesg output, it appears that the problem is "[14.540456] parport0: Device ID was 64 bytes while device told it would be 63 bytes" how would i fix that?

---

