---
title: "irq disable kills NIC"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by Sangoma on 2007-05-30
Hi all,

First up I would like to say I am a new Ubuntu (and hence Linux) user, having been intending to 'make the leap' for many a year - being a windows system administrator, it's quite a big leap.
Anyway, loving Ubuntu and Linux in my home media centre with MythTV up and playing wonderfully for the last few months....but :D I have just one final issue to resolve.
After what appears to be a random length of time Ubuntu disables irq 21, my nic, thus obviously killing all LAN and net access. I have tried everything i could find on the net. Using the boot option irqpoll appears to resolve the issue BUT it kills my HDD (SATA) with a dozen or so I/O errors per second until the system falls over - so not a good solution. Rebooting the machine obvously re-enables the IRQ until it randomly kills it again. I've played with the acpi boot options and tried all the possible combinations of BIOS settings to do with acpi and irq, but with no luck. Below is a copy from my syslog:

May 30 20:58:36 Media-Centre kernel: [16424.184000] irq 21: nobody cared (try booting with the "irqpoll" option)
May 30 20:58:37 Media-Centre kernel: [16424.184000]  [__report_bad_irq+36/128] __report_bad_irq+0x24/0x80
May 30 20:58:37 Media-Centre kernel: [16424.184000]  [note_interrupt+606/656] note_interrupt+0x25e/0x290
May 30 20:58:37 Media-Centre kernel: [16424.184000]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
May 30 20:58:37 Media-Centre kernel: [16424.184000]  [handle_fasteoi_irq+193/240] handle_fasteoi_irq+0xc1/0xf0
May 30 20:58:37 Media-Centre kernel: [16424.184000]  [do_IRQ+64/128] do_IRQ+0x40/0x80
May 30 20:58:37 Media-Centre kernel: [16424.184000]  [common_interrupt+35/48] common_interrupt+0x23/0x30
May 30 20:58:37 Media-Centre kernel: [16424.184000]  [default_idle+0/96] default_idle+0x0/0x60
May 30 20:58:37 Media-Centre kernel: [16424.184000]  [native_safe_halt+2/16] native_safe_halt+0x2/0x10
May 30 20:58:37 Media-Centre kernel: [16424.184000]  [default_idle+61/96] default_idle+0x3d/0x60
May 30 20:58:37 Media-Centre kernel: [16424.184000]  [cpu_idle+73/208] cpu_idle+0x49/0xd0
May 30 20:58:37 Media-Centre kernel: [16424.184000]  [start_kernel+869/1056] start_kernel+0x365/0x420
May 30 20:58:37 Media-Centre kernel: [16424.184000]  [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260
May 30 20:58:37 Media-Centre kernel: [16424.184000]  =======================
May 30 20:58:37 Media-Centre kernel: [16424.184000] handlers:
May 30 20:58:37 Media-Centre kernel: [16424.184000] [<f88f0f10>] (usb_hcd_irq+0x0/0x60 [usbcore])
May 30 20:58:37 Media-Centre kernel: [16424.184000] [<f88cddd0>] (rhine_interrupt+0x0/0xb80 [via_rhine])
May 30 20:58:37 Media-Centre kernel: [16424.184000] Disabling IRQ #21

If anyone has any ideas as to where I could look next it would be much appreciated. I've even set up a cron job that fires every 5 mins loading a webpage with lynx to see if that helps keep the irq alive!

Thanks in advance.

---

