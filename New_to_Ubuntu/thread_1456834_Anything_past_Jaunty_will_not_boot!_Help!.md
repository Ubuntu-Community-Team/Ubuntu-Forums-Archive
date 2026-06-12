---
title: "Anything past Jaunty will not boot! Help!"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by bpowell2005 on 2010-04-17
Hi Gang,

Well, I wanted to upgrade the home computer with another computer I had sitting around...now it won't boot! Here's the details:

"New computer" is an Intel dual-core 2.66 ghz processor, 64-bit, 4 gig of ram. This computer has Windows installed, and I can install and run Jaunty...,but if I upgrade to Karmic, it fails.

Karmic and Lucid Live CD's also do not boot on this computer!

I upgraded Jaunty, and now it's not booting...I can boot an older kernel into recovery mode, but the CPU pings at 100% for some reason (xorg) and I don't like leaving the computer in that state...Also, my objective is to have Karmic on this computer!

The boot freezes with a call-trace...but I can't find that on the hard-drive to post, so I'll type the parts I can:

Call Trace:
1.640028 [<ffffffffa00781b5>] i915_gem_object_bint_to_gtt_0x11b/0x2b0 [i915]
i915_gem_object_pin+0x185/0x1d0 [i915]
i915_gem_init_hws
(some other i915 failures)
? do_work_for_cpu+0x0/0x30
(some more i915 failures)
Local_pci_probe
do_work_for_cpu
kthread
child_rip
? kthread
? child_rip
drm_mm_search_free
RSP
CR2
[ end trace ]

After 180 seconds...I get an Ubuntu logo (white on black) and then this:

udevd[127]: worker [147] unexpectedly returned with status 0x0100
udevd[127]: worker [147] failed while handling '/devices/pci0000:00/0000:00:02.0]
udevadm settle - timeout of 180 seconds reached, the event queue contains:
/sys/devices/pci0000:00/0000:00:02.0/drm/controlID64 (1004)
/sys/devices/pci0000:00/0000:00:02.0/drm/card0 (1005)

At this point, I can log on to the shell.



Any help, please?

Thanks!

Brendan

---

### Post by bpowell2005 on 2010-04-17
A quick update...

I've been fighting this all day...different distros, you name it.

The system runs fine on Jaunty, but later kernels crash it out. I've found (just preliminary) that if I change my shared video memory from 256m to 128m, then Karmic boots, no problem. I'll try installing Lucid tomorrow and see how that works.

Why would Jaunty be able to handle the larger shared memory, but a more recent release can not?

---

