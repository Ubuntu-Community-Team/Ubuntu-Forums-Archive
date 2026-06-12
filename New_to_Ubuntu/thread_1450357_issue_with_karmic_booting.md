---
title: "issue with karmic booting"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by garrett1 on 2010-04-08
I just installed 9.10 on my new HP Mini 311 netbook. I downloaded karmic from this website and burned the ISO to a CD. I used an external disk drive to preview ubuntu, and then chose the install option from the live cd os. I partitioned down my drive, taking 50 gb away to give to ubuntu from the windows xp that came loaded on the netbook, and continued through to the end of the install process. The install seemed to go perfectly smoothly, the progress bar reached 100%, i was prompted to remove the boot disk, and the system restarted. Upon restart, I chose the normal ubuntu boot option in grub. Everything works fine up until this point. However, after I select that, the system runs into problems. 

Ubuntu won't boot. After I select ubuntu in grub, the system just sits at a dark screen with a white flashing cursor in the upper left corner. I've left it like this for more than 15 minutes in case there was some other configuration/installation process that was taking place, but there's been no change at all. XP boots without issue. I'm almost entirely new to ubuntu and linux in general so I may be missing something obvious, but if I am it escapes me. Any ideas/suggestions are greatly appreciated.

---

### Post by MooPi on 2010-04-09
Did you recently update or add new applications? Can you tell us what you did last before the problem started.

---

### Post by garrett1 on 2010-04-09
not on ubuntu since i've been unable to boot it thus far. all i've done in xp since it's been out of the box is get rid of bloatware and install firefox.

---

### Post by MooPi on 2010-04-09
Try a reboot and at the grub window select recovery mode.
At the prompt type ```
dpkg --configure -a
```This should attempt to correct a interrupted update or partial install process. 
Not certain if this is your issue but it's a good start.

---

### Post by garrett1 on 2010-04-09
it seems to stall a good portion of the time booting through recovery mode. the last few lines before it stalls out are ```
Loading, please wait...
[   2.000525] Clocksource tsc unstable (delta = -132737277 ns)
[   2.273426] acpi device:30: registered as cooling_device2
[   2.274836] input: Video Bus as /devices.LNXSYSTM:00/device:00/PNP0A08:00/dev
ice:2e/device:2f/input/input6
[   2.275029] ACPI: Video Device [IGPU] (multi-head: yes rom: no post :no)
[   2.391369] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.6
.4
[   2.392673] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[   2.392762] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 22 (level,
 low) -> IRQ 22
[ 2.451309] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[AX3A] -> GSI 16 (l
evel, low) -> IRQ16

```

---

### Post by garrett1 on 2010-04-09
I think the problem most likely has something to do with the code I just posted. Upon repeated trials I've discovered that I can boot in to the OS with the GUI and everything functioning normally, but only a percentage of the time. When it fails, it always fails at the same place when running recovery mode, and stalls in the way I described in my first post when attempting to boot in normally. Any idea what the issue might be?

---

### Post by MooPi on 2010-04-09
I see your issue. Clocksource tsc unstable, 
Check this thread for solutions: [http://ubuntuforums.org/showthread.php?t=698211](http://ubuntuforums.org/showthread.php?t=698211)
This is a tough issue good luck.

---

### Post by garrett1 on 2010-04-09
Thanks. Your assistance is greatly appreciated.

---

