---
title: "Network dropping after install of External HD"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by vadar007 on 2006-09-26
I recently installed and mounted an external USB hard disk. I have no problems reading and writing to it and the configuration seems stable. My problem occurs when I attempt to tar my Video directory (180GB+) to my external HD. The tar runs fine and will complete successfully, however, the network drops after a short period of time and the only way to recover is by rebooting the server.

1) Deactivating and re-activating the eth0 interface does not fix the issue.

2) Syslog indicates a repeating network drop and reactivation and what appears to be an IRQ conflict:

Sep 26 03:23:05 localhost kernel: [42976711.580000] irq 177: nobody cared (try booting with the "irqpoll" option)
Sep 26 03:23:05 localhost kernel: [42976711.580000]  [__report_bad_irq+42/160] __report_bad_irq+0x2a/0xa0
Sep 26 03:23:05 localhost kernel: [42976711.580000]  [handle_IRQ_event+61/112] handle_IRQ_event+0x3d/0x70
Sep 26 03:23:05 localhost kernel: [42976711.580000]  [note_interrupt+135/240] note_interrupt+0x87/0xf0
Sep 26 03:23:05 localhost kernel: [42976711.580000]  [__do_IRQ+239/256] __do_IRQ+0xef/0x100
Sep 26 03:23:05 localhost kernel: [42976711.580000]  [do_IRQ+25/48] do_IRQ+0x19/0x30
Sep 26 03:23:05 localhost kernel: [42976711.580000]  [common_interrupt+26/32] common_interrupt+0x1a/0x20
Sep 26 03:23:05 localhost kernel: [42976711.580000]  [vfs_getattr+0/240] vfs_getattr+0x0/0xf0
Sep 26 03:23:05 localhost kernel: [42976711.580000]  [vfs_fstat+57/80] vfs_fstat+0x39/0x50
Sep 26 03:23:05 localhost kernel: [42976711.580000]  [sys_fstat64+24/64] sys_fstat64+0x18/0x40
Sep 26 03:23:05 localhost kernel: [42976711.580000]  [__do_IRQ+185/256] __do_IRQ+0xb9/0x100
Sep 26 03:23:05 localhost kernel: [42976711.580000]  [sysenter_past_esp+84/117] sysenter_past_esp+0x54/0x75
Sep 26 03:23:05 localhost kernel: [42976711.580000] handlers:
Sep 26 03:23:05 localhost kernel: [42976711.580000] [pg0+944267648/1069167616] (usb_hcd_irq+0x0/0x70 [usbcore])
Sep 26 03:23:05 localhost kernel: [42976711.580000] [pg0+945171504/1069167616] (e100_intr+0x0/0x170 [e100])
Sep 26 03:23:05 localhost kernel: [42976711.580000] [pg0+948755136/1069167616] (i915_driver_irq_handler+0x0/0x130 [i915])
Sep 26 03:23:05 localhost kernel: [42976711.580000] Disabling IRQ #177
Sep 26 03:23:55 localhost kernel: [42976761.710000] NETDEV WATCHDOG: eth0: transmit timed out
Sep 26 03:23:55 localhost kernel: [42976761.740000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Sep 26 03:26:24 localhost kernel: [42976910.730000] NETDEV WATCHDOG: eth0: transmit timed out
Sep 26 03:26:24 localhost kernel: [42976910.760000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Sep 26 03:28:31 localhost kernel: [42977037.750000] NETDEV WATCHDOG: eth0: transmit timed out
Sep 26 03:28:31 localhost kernel: [42977037.780000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Sep 26 03:30:34 localhost kernel: [42977160.770000] NETDEV WATCHDOG: eth0: transmit timed out
Sep 26 03:30:34 localhost kernel: [42977160.800000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Sep 26 03:32:35 localhost kernel: [42977281.790000] NETDEV WATCHDOG: eth0: transmit timed out
Sep 26 03:32:35 localhost kernel: [42977281.820000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Sep 26 03:35:10 localhost kernel: [42977436.810000] NETDEV WATCHDOG: eth0: transmit timed out
Sep 26 03:35:10 localhost kernel: [42977436.840000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex

Anyone have a clue why this is occuring and steps to fix it?

---

### Post by antgod on 2007-01-16
I've the same problem but without the IDE part... the network cards just doesn't work on the laptop...

---

