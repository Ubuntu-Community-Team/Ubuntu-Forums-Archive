---
title: "compiling d-link DFE-520Tx driver"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by manish_m on 2007-06-09
HI,
i am using ubuntu 7.04. Recently, the onborad nic stopped working. So, i bought a new one, D-Link DFE520TX. Itis detected by ubuntu. But if try to get ip through dhcp, i m not getting one. Its works flawlessly on windows xp.
So, i tried using drivers given with the card. 
when i try to compile them, i get the following error. can somebody pls help in resolving this issue.
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/manish/dlink modules
make[1]: Entering directory `/usr/src/linux-source-2.6.20'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.20/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/manish/dlink/rhine_main.o
In file included from /home/manish/dlink/rhine_main.c:28:
/home/manish/dlink/rhine.h:56:26: error: linux/config.h: No such file or directory
/home/manish/dlink/rhine_main.c:59: error: expected ) before string constant
/home/manish/dlink/rhine_main.c:64: error: expected ) before string constant
/home/manish/dlink/rhine_main.c:73: error: expected ) before string constant
/home/manish/dlink/rhine_main.c:85: error: expected ) before string constant
/home/manish/dlink/rhine_main.c:100: error: expected ) before string constant
/home/manish/dlink/rhine_main.c:115: error: expected ) before string constant
/home/manish/dlink/rhine_main.c:122: error: expected ) before string constant
/home/manish/dlink/rhine_main.c:131: error: expected ) before string constant
/home/manish/dlink/rhine_main.c:139: error: expected ) before string constant
/home/manish/dlink/rhine_main.c:148: error: expected ) before string constant
/home/manish/dlink/rhine_main.c:159: error: expected ) before string constant
/home/manish/dlink/rhine_main.c:175: error: expected ) before string constant
/home/manish/dlink/rhine_main.c:182: error: expected ) before string constant
/home/manish/dlink/rhine_main.c:194: error: expected ) before string constant
/home/manish/dlink/rhine_main.c:200: error: expected ) before string constant
/home/manish/dlink/rhine_main.c: In function rhine_open:
/home/manish/dlink/rhine_main.c:1585: warning: passing argument 2 of request_irq from incompatible pointer type
/home/manish/dlink/rhine_main.c: In function rhine_xmit:
/home/manish/dlink/rhine_main.c:1723: error: CHECKSUM_HW undeclared (first use in this function)
/home/manish/dlink/rhine_main.c:1723: error: (Each undeclared identifier is reported only once
/home/manish/dlink/rhine_main.c:1723: error: for each function it appears in.)
/home/manish/dlink/rhine_main.c: At top level:
/home/manish/dlink/rhine_main.c:2018: warning: initialization from incompatible pointer type
/home/manish/dlink/rhine_main.c: In function rhine_ethtool_ioctl:
/home/manish/dlink/rhine_main.c:2752: error: struct pci_dev has no member named slot_name
/home/manish/dlink/rhine_main.c: In function rhine_suspend:
/home/manish/dlink/rhine_main.c:2925: error: too many arguments to function pci_save_state
/home/manish/dlink/rhine_main.c: In function rhine_resume:
/home/manish/dlink/rhine_main.c:2959: error: too many arguments to function pci_restore_state
make[2]: *** [/home/manish/dlink/rhine_main.o] Error 1
make[1]: *** [_module_/home/manish/dlink] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.20'
make: *** [default] Error 2

---

### Post by manish_m on 2007-06-11
Hi,
i tried using ubuntu 6.06. The card worked on it.
it does not work in feisty, even with 6.06 kernel.
i looked into syslog for feisty, i get the following error :
Jun 11 23:19:14 hawkeye kernel: [   44.757188] irq 16: nobody cared (try booting with the "irqpoll" option)
Jun 11 23:19:14 hawkeye kernel: [   44.757212]  [__report_bad_irq+36/128] __report_bad_irq+0x24/0x80
Jun 11 23:19:14 hawkeye kernel: [   44.757237]  [note_interrupt+606/656] note_interrupt+0x25e/0x290
Jun 11 23:19:14 hawkeye kernel: [   44.757270]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Jun 11 23:19:14 hawkeye kernel: [   44.757290]  [handle_fasteoi_irq+193/240] handle_fasteoi_irq+0xc1/0xf0
Jun 11 23:19:14 hawkeye kernel: [   44.757310]  [do_IRQ+64/128] do_IRQ+0x40/0x80
Jun 11 23:19:14 hawkeye kernel: [   44.757334]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Jun 11 23:19:14 hawkeye kernel: [   44.757410]  =======================
Jun 11 23:19:14 hawkeye kernel: [   44.757412] handlers:
Jun 11 23:19:14 hawkeye kernel: [   44.757413] [<f885cdd0>] (rhine_interrupt+0x0/0xb80 [via_rhine])
Jun 11 23:19:14 hawkeye kernel: [   44.757425] [<f8f3c480>] (via_driver_irq_handler+0x0/0x1d0 [via])
Jun 11 23:19:14 hawkeye kernel: [   44.757432] Disabling IRQ #16
##############
if i use irqpoll option, system becomes slow.I get the following error:
Jun 11 23:37:06 hawkeye kernel: [   58.171175] irq 1: nobody cared (try booting with the "irqpoll" option)
Jun 11 23:37:06 hawkeye kernel: [   58.171197]  [__report_bad_irq+36/128] __report_bad_irq+0x24/0x80
Jun 11 23:37:06 hawkeye kernel: [   58.171221]  [note_interrupt+606/656] note_interrupt+0x25e/0x290
Jun 11 23:37:06 hawkeye kernel: [   58.171272]  [handle_edge_irq+195/304] handle_edge_irq+0xc3/0x130
Jun 11 23:37:06 hawkeye kernel: [   58.171291]  [do_IRQ+64/128] do_IRQ+0x40/0x80
Jun 11 23:37:06 hawkeye kernel: [   58.171314]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Jun 11 23:37:06 hawkeye kernel: [   58.171358]  [__do_softirq+94/256] __do_softirq+0x5e/0x100
Jun 11 23:37:06 hawkeye kernel: [   58.171392]  [do_softirq+85/96] do_softirq+0x55/0x60
Jun 11 23:37:06 hawkeye kernel: [   58.171399]  [do_IRQ+69/128] do_IRQ+0x45/0x80
Jun 11 23:37:06 hawkeye kernel: [   58.171420]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Jun 11 23:37:06 hawkeye kernel: [   58.171463]  [cfb_imageblit+1275/1328] cfb_imageblit+0x4fb/0x530
Jun 11 23:37:06 hawkeye kernel: [   58.171531]  [do_IRQ+69/128] do_IRQ+0x45/0x80
Jun 11 23:37:06 hawkeye kernel: [   58.171537]  [<f8b91266>] ehci_irq+0x26/0x170 [ehci_hcd]
Jun 11 23:37:06 hawkeye kernel: [   58.171561]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Jun 11 23:37:06 hawkeye kernel: [   58.171612]  [<f88025d1>] bit_putcs+0x391/0x630 [bitblit]
Jun 11 23:37:06 hawkeye kernel: [   58.171619]  [ack_ioapic_quirk_irq+64/160] ack_ioapic_quirk_irq+0x40/0xa0
Jun 11 23:37:06 hawkeye kernel: [   58.171634]  [handle_fasteoi_irq+155/240] handle_fasteoi_irq+0x9b/0xf0
Jun 11 23:37:06 hawkeye kernel: [   58.171651]  [do_IRQ+69/128] do_IRQ+0x45/0x80
Jun 11 23:37:06 hawkeye kernel: [   58.171704]  [aer_probe+319/336] aer_probe+0x13f/0x150
Jun 11 23:37:06 hawkeye kernel: [   58.171723]  [<f885d46a>] rhine_interrupt+0x69a/0xb80 [via_rhine]
Jun 11 23:37:06 hawkeye kernel: [   58.171745]  [<f8bd983c>] ata_interrupt+0xcc/0x200 [libata]
Jun 11 23:37:06 hawkeye kernel: [   58.171769]  [i8042_interrupt+482/592] i8042_interrupt+0x1e2/0x250
Jun 11 23:37:06 hawkeye kernel: [   58.171841]  [ack_ioapic_quirk_irq+64/160] ack_ioapic_quirk_irq+0x40/0xa0
Jun 11 23:37:06 hawkeye kernel: [   58.171854]  [handle_fasteoi_irq+155/240] handle_fasteoi_irq+0x9b/0xf0
Jun 11 23:37:06 hawkeye kernel: [   58.171873]  [<f883081d>] fbcon_putcs+0x18d/0x2c0 [fbcon]
Jun 11 23:37:06 hawkeye kernel: [   58.171907]  [<f8802240>] bit_putcs+0x0/0x630 [bitblit]
Jun 11 23:37:06 hawkeye kernel: [   58.171939]  [do_update_region+294/352] do_update_region+0x126/0x160
Jun 11 23:37:06 hawkeye kernel: [   58.171984]  [redraw_screen+311/480] redraw_screen+0x137/0x1e0
Jun 11 23:37:06 hawkeye kernel: [   58.171990]  [<f8bd983c>] ata_interrupt+0xcc/0x200 [libata]
Jun 11 23:37:06 hawkeye kernel: [   58.172010]  [i8042_interrupt+482/592] i8042_interrupt+0x1e2/0x250
Jun 11 23:37:06 hawkeye kernel: [   58.172031]  [<f8835476>] fbcon_blank+0x216/0x220 [fbcon]
Jun 11 23:37:06 hawkeye kernel: [   58.172191]  [do_unblank_screen+153/352] do_unblank_screen+0x99/0x160
Jun 11 23:37:06 hawkeye kernel: [   58.172216]  [complete_change_console+122/224] complete_change_console+0x7a/0xe0
Jun 11 23:37:06 hawkeye kernel: [   58.172230]  [vt_ioctl+5141/6208] vt_ioctl+0x1415/0x1840
Jun 11 23:37:06 hawkeye kernel: [   58.172240]  [<f8b91266>] ehci_irq+0x26/0x170 [ehci_hcd]
Jun 11 23:37:06 hawkeye kernel: [   58.172279]  [note_interrupt+402/656] note_interrupt+0x192/0x290
Jun 11 23:37:06 hawkeye kernel: [   58.172307]  [vt_ioctl+0/6208] vt_ioctl+0x0/0x1840
Jun 11 23:37:06 hawkeye kernel: [   58.172319]  [tty_ioctl+261/3488] tty_ioctl+0x105/0xda0
Jun 11 23:37:06 hawkeye kernel: [   58.172347]  [<f885d46a>] rhine_interrupt+0x69a/0xb80 [via_rhine]
Jun 11 23:37:06 hawkeye kernel: [   58.172368]  [<f8bd983c>] ata_interrupt+0xcc/0x200 [libata]
Jun 11 23:37:06 hawkeye kernel: [   58.172388]  [i8042_interrupt+482/592] i8042_interrupt+0x1e2/0x250
Jun 11 23:37:06 hawkeye kernel: [   58.172396]  [<f8b91266>] ehci_irq+0x26/0x170 [ehci_hcd]
Jun 11 23:37:06 hawkeye kernel: [   58.172415]  [<f8d3e127>] snd_via8233_interrupt+0x17/0xf0 [snd_via82xx]
Jun 11 23:37:06 hawkeye kernel: [   58.172442]  [note_interrupt+402/656] note_interrupt+0x192/0x290
Jun 11 23:37:06 hawkeye kernel: [   58.172471]  [ack_ioapic_quirk_irq+64/160] ack_ioapic_quirk_irq+0x40/0xa0
Jun 11 23:37:06 hawkeye kernel: [   58.172483]  [handle_fasteoi_irq+155/240] handle_fasteoi_irq+0x9b/0xf0
Jun 11 23:37:06 hawkeye kernel: [   58.172499]  [do_IRQ+69/128] do_IRQ+0x45/0x80
Jun 11 23:37:06 hawkeye kernel: [   58.172524]  [do_ioctl+120/144] do_ioctl+0x78/0x90
Jun 11 23:37:06 hawkeye kernel: [   58.172543]  [vfs_ioctl+92/672] vfs_ioctl+0x5c/0x2a0
Jun 11 23:37:06 hawkeye kernel: [   58.172565]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
Jun 11 23:37:06 hawkeye kernel: [   58.172583]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Jun 11 23:37:06 hawkeye kernel: [   58.172643]  =======================
Jun 11 23:37:06 hawkeye kernel: [   58.172645] handlers:
Jun 11 23:37:06 hawkeye kernel: [   58.172646] [i8042_interrupt+0/592] (i8042_interrupt+0x0/0x250)
Jun 11 23:37:06 hawkeye kernel: [   58.172649] Disabling IRQ #1
Jun 11 23:37:06 hawkeye kernel: [   58.307631] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Jun 11 23:37:06 hawkeye kernel: [   58.307636] ide: failed opcode was: unknown
Jun 11 23:37:06 hawkeye kernel: [   58.307665] hda: drive not ready for command
Jun 11 23:37:06 hawkeye kernel: [   58.318213] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Jun 11 23:37:06 hawkeye kernel: [   58.318216] ide: failed opcode was: unknown
Jun 11 23:37:06 hawkeye kernel: [   58.318243] hda: drive not ready for command
Jun 11 23:37:06 hawkeye kernel: [   58.337254] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Jun 11 23:37:06 hawkeye kernel: [   58.337257] ide: failed opcode was: unknown
Jun 11 23:37:06 hawkeye kernel: [   58.337283] hda: drive not ready for command
Jun 11 23:37:06 hawkeye kernel: [   58.346985] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Jun 11 23:37:06 hawkeye kernel: [   58.346987] ide: failed opcode was: unknown
Jun 11 23:37:06 hawkeye kernel: [   58.347015] hda: drive not ready for command
Jun 11 23:37:06 hawkeye kernel: [   58.356252] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Jun 11 23:37:06 hawkeye kernel: [   58.356254] ide: failed opcode was: unknown
Jun 11 23:37:06 hawkeye kernel: [   58.356281] hda: drive not ready for command
Jun 11 23:37:07 hawkeye kernel: [   58.866914] irq 16: nobody cared (try booting with the "irqpoll" option)
Jun 11 23:37:07 hawkeye kernel: [   58.874494]  [__report_bad_irq+36/128] __report_bad_irq+0x24/0x80
Jun 11 23:37:07 hawkeye kernel: [   58.874518]  [note_interrupt+606/656] note_interrupt+0x25e/0x290
Jun 11 23:37:07 hawkeye kernel: [   58.874566]  [handle_fasteoi_irq+193/240] handle_fasteoi_irq+0xc1/0xf0
Jun 11 23:37:07 hawkeye kernel: [   58.874585]  [do_IRQ+64/128] do_IRQ+0x40/0x80
Jun 11 23:37:07 hawkeye kernel: [   58.874607]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Jun 11 23:37:07 hawkeye kernel: [   58.874675]  =======================
Jun 11 23:37:07 hawkeye kernel: [   58.874676] handlers:
Jun 11 23:37:07 hawkeye kernel: [   58.882231] [<f885cdd0>] (rhine_interrupt+0x0/0xb80 [via_rhine])
Jun 11 23:37:07 hawkeye kernel: [   58.890071] [<f8f3e480>] (via_driver_irq_handler+0x0/0x1d0 [via])
Jun 11 23:37:07 hawkeye kernel: [   58.897973] Disabling IRQ #16
Jun 11 23:37:08 hawkeye kernel: [   60.336714] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Jun 11 23:37:08 hawkeye kernel: [   60.336720] ide: failed opcode was: unknown
Jun 11 23:37:08 hawkeye kernel: [   60.336724] hda: drive not ready for command
Jun 11 23:37:08 hawkeye kernel: [   60.352458] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Jun 11 23:37:08 hawkeye kernel: [   60.352461] ide: failed opcode was: unknown
Jun 11 23:37:08 hawkeye kernel: [   60.352463] hda: drive not ready for command
Jun 11 23:37:08 hawkeye kernel: [   60.360855] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Jun 11 23:37:08 hawkeye kernel: [   60.360858] ide: failed opcode was: unknown
Jun 11 23:37:08 hawkeye kernel: [   60.360860] hda: drive not ready for command
Jun 11 23:37:08 hawkeye kernel: [   60.368905] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Jun 11 23:37:08 hawkeye kernel: [   60.368908] ide: failed opcode was: unknown
Jun 11 23:37:08 hawkeye kernel: [   60.368910] hda: drive not ready for command
Jun 11 23:37:08 hawkeye kernel: [   60.376899] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Jun 11 23:37:08 hawkeye kernel: [   60.376901] ide: failed opcode was: unknown
Jun 11 23:37:08 hawkeye kernel: [   60.376903] hda: drive not ready for command

---

