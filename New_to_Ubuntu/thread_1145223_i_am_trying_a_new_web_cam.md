---
title: "i am trying a new web cam"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by DarinB on 2009-05-01
i am trying a new web cam how do i know if it works wha tis supposed to happen? 
or how do i use it?

---

### Post by Cypher on 2009-05-01
I presume this is a USB based webcam. If so, plug it in and then type "dmesg" from the console. You should see some information about your webcam being detected.

You can then run mplayer to stream the video and test it out:
```

mplayer -tv driver=v4l2:device=/dev/video0 tv:///

```

---

### Post by DarinB on 2009-05-01
[    0.496531] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.496721] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.496910] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.497100] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.497290] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[    0.497481] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.497671] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.497862] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.498052] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.498243] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.498432] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.498622] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.498813] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.499003] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.499193] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.499326] ACPI: WMI: Mapper loaded
[    0.499353] SCSI subsystem initialized
[    0.499353] libata version 3.00 loaded.
[    0.499353] usbcore: registered new interface driver usbfs

---

### Post by DarinB on 2009-05-01
darin@darin-desktop:~$ mplayer -tv driver=v4l2:device=/dev/video0 tv:///
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz (Family: 6, Model: 23, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Creating config file: /home/darin/.mplayer/config
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv:///.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: UVC Camera (046d:09a1)
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: MJPEG
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
FPS not specified in the header or invalid, use the -fps option.
No stream found.

v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.

Exiting... (End of file)
darin@darin-desktop:~$

---

