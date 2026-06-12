---
title: "Kernel update exacerbates problem with NDISwrapper load"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by kpjoyce on 2007-05-30
I've been very happy with NDISwrapper ... when it loads properly.  With the original Feisty kernel (15), it would sometimes load quickly and perfectly, sometimes take a long time at startup to load but then work perfectly (most often), and sometimes take a long time at startup but never load properly.  When it failed to load, other usb devices were also adversely affected: my mouse was too sluggish to use.

After the update to the new kernel (16), It always boots slowly and doesn't work.  Here are what I believe are the related messages:

From /var/log/dmesg:
> 
[   23.624000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   23.732000] ndiswrapper: driver net5211 (,09/17/2003,2.4.2.14) loaded
[   25.784000] irq 11: nobody cared (try booting with the "irqpoll" option)
[   25.784000]  [<c01543a4>] __report_bad_irq+0x24/0x80
[   25.784000]  [<c015465e>] note_interrupt+0x25e/0x290
[   25.784000]  [<e087df32>] usb_hcd_irq+0x22/0x60 [usbcore]
[   25.784000]  [<c01538d0>] handle_IRQ_event+0x30/0x60
[   25.784000]  [<c01551db>] handle_level_irq+0xeb/0x120
[   25.784000]  [<c0105b70>] do_IRQ+0x40/0x80
[   25.784000]  [<c0104233>] common_interrupt+0x23/0x30
[   25.784000]  [<c012b3fb>] __do_softirq+0x5b/0x100
[   25.784000]  [<c012b4f5>] do_softirq+0x55/0x60
[   25.784000]  [<c0105b75>] do_IRQ+0x45/0x80
[   25.784000]  [<c0104233>] common_interrupt+0x23/0x30
[   25.784000]  [<c02ee94d>] _spin_unlock_irqrestore+0xd/0x20
[   25.784000]  [<c0275682>] pci_conf1_write+0x92/0xd0
[   25.784000]  [<c020c997>] acpi_os_write_pci_configuration+0x78/0x88
[   25.784000]  [<c02185f5>] acpi_ex_pci_config_space_handler+0x0/0x61
[   25.784000]  [<c021166c>] acpi_ev_address_space_dispatch+0x16c/0x1b9
[   25.784000]  [<c02156eb>] acpi_ex_access_region+0x224/0x23c
[   25.784000]  [<c0215816>] acpi_ex_field_datum_io+0x113/0x1a7
[   25.784000]  [<c012f657>] run_timer_softirq+0x37/0x1a0
[   25.784000]  [<c0215c04>] acpi_ex_write_with_update_rule+0x12a/0x132
[   25.784000]  [<c0215eb6>] acpi_ex_insert_into_field+0x2aa/0x2b4
[   25.784000]  [<c0215953>] acpi_ex_extract_from_field+0xa9/0x230
[   25.784000]  [<c0214405>] acpi_ex_write_data_to_field+0x231/0x24c
[   25.784000]  [<c020c7dd>] acpi_os_release_object+0x5/0x8
[   25.784000]  [<c0218956>] acpi_ex_store_object_to_node+0x72/0xab
[   25.784000]  [<c0218af2>] acpi_ex_store+0xeb/0x23d
[   25.784000]  [<c020fd2a>] acpi_ds_create_operand+0x1ca/0x1d6
[   25.784000]  [<c02167a0>] acpi_ex_opcode_1A_1T_1R+0x3dc/0x554
[   25.784000]  [<c0216fce>] acpi_ex_resolve_operands+0x23d/0x57f
[   25.784000]  [<c020ecef>] acpi_ds_exec_end_op+0xc2/0x3cf
[   25.784000]  [<c021e0a1>] acpi_ps_append_arg+0x16/0x75
[   25.784000]  [<c021dd3c>] acpi_ps_parse_loop+0x5b0/0x8cc
[   25.784000]  [<c021d3a2>] acpi_ps_parse_aml+0x60/0x1ff
[   25.784000]  [<c0210d64>] acpi_ds_init_aml_walk+0xb4/0xfe
[   25.784000]  [<c021e48c>] acpi_ps_execute_pass+0x81/0x94
[   25.784000]  [<c021e58d>] acpi_ps_execute_method+0xbe/0x14d
[   25.784000]  [<c021b961>] acpi_ns_evaluate+0x9d/0xfc
[   25.784000]  [<c021f8ac>] acpi_rs_set_srs_method_data+0xd0/0xec
[   25.784000]  [<c021f245>] acpi_set_current_resources+0x2a/0x34
[   25.784000]  [<c0226d48>] acpi_pci_link_set+0x108/0x1c3
[   25.784000]  [<c0228af4>] acpi_bus_data_handler+0x0/0x1
[   25.784000]  [<c021b19e>] acpi_get_data+0x4a/0x58
[   25.784000]  [<c022706a>] acpi_pci_link_allocate_irq+0x126/0x1eb
[   25.784000]  [<c0223f3f>] acpi_ut_release_mutex+0x5b/0x63
[   25.784000]  [<c0227534>] acpi_pci_allocate_irq+0x25/0x4d
[   25.784000]  [<c022734b>] acpi_pci_irq_lookup+0x3a/0x8e
[   25.784000]  [<c0227673>] acpi_pci_irq_enable+0x8d/0x1da
[   25.784000]  [<c022750f>] acpi_pci_allocate_irq+0x0/0x4d
[   25.784000]  [<c0276c24>] pcibios_enable_device+0x14/0x20
[   25.784000]  [<c01f90e4>] pci_enable_device_bars+0x24/0x60
[   25.784000]  [<c01f9136>] __pci_enable_device+0x16/0x40
[   25.784000]  [<c01f9187>] pci_enable_device+0x27/0x40
[   25.784000]  [<e0c4143a>] pdoDispatchPnp+0xaa/0x420 [ndiswrapper]
[   25.784000]  [<c01e259e>] blk_remove_plug+0x2e/0x70
[   25.784000]  [<e0c3c12a>] IofCallDriver+0x3a/0xa0 [ndiswrapper]
[   25.784000]  [<e0c3d554>] IoSyncForwardIrp+0x64/0xb0 [ndiswrapper]
[   25.784000]  [<e0c431b7>] NdisDispatchPnp+0xc7/0xd80 [ndiswrapper]
[   25.784000]  [<c011e341>] __activate_task+0x21/0x40
[   25.784000]  [<c0120706>] try_to_wake_up+0x46/0x480
[   25.784000]  [<c0102236>] __switch_to+0xc6/0x1f0
[   25.784000]  [<c02f1424>] kprobe_flush_task+0x44/0x90
[   25.784000]  [<c02ecd05>] __sched_text_start+0x8d5/0xa90
[   25.784000]  [<c02f1424>] kprobe_flush_task+0x44/0x90
[   25.784000]  [<c02ecd05>] __sched_text_start+0x8d5/0xa90
[   25.784000]  [<e0c3c488>] IoAllocateIrp+0x68/0xa0 [ndiswrapper]
[   25.784000]  [<e0c3cf95>] IoBuildAsynchronousFsdRequest+0x35/0x170 [ndiswrapper]
[   25.784000]  [<e0c375c1>] get_current_nt_thread+0xc1/0xf0 [ndiswrapper]
[   25.784000]  [<e0c3d0eb>] IoQueueThreadIrp+0x1b/0x130 [ndiswrapper]
[   25.784000]  [<e0c3c12a>] IofCallDriver+0x3a/0xa0 [ndiswrapper]
[   25.784000]  [<e0c418ab>] IoSendIrpTopDev+0xbb/0x120 [ndiswrapper]
[   25.784000]  [<e0c41c03>] pnp_start_device+0x53/0xb0 [ndiswrapper]
[   25.784000]  [<e0c41e33>] wrap_pnp_start_device+0x1d3/0x280 [ndiswrapper]
[   25.784000]  [<e0c41f25>] wrap_pnp_start_pci_device+0x45/0x50 [ndiswrapper]
[   25.784000]  [<c01b8015>] sysfs_dirent_exist+0x45/0x70
[   25.784000]  [<c01b8eee>] sysfs_create_link+0x6e/0x160
[   25.784000]  [<c01fb963>] pci_match_device+0x13/0xc0
[   25.784000]  [<e0c41ee0>] wrap_pnp_start_pci_device+0x0/0x50 [ndiswrapper]
[   25.784000]  [<e0c41ee0>] wrap_pnp_start_pci_device+0x0/0x50 [ndiswrapper]
[   25.784000]  [<c01fba86>] pci_device_probe+0x56/0x80
[   25.784000]  [<c0257a86>] really_probe+0x66/0x190
[   25.784000]  [<c0257bf9>] driver_probe_device+0x49/0xc0
[   25.784000]  [<c0257dce>] __driver_attach+0x9e/0xa0
[   25.784000]  [<c0256f5b>] bus_for_each_dev+0x3b/0x60
[   25.784000]  [<c0257924>] driver_attach+0x24/0x30
[   25.784000]  [<c0257d30>] __driver_attach+0x0/0xa0
[   25.784000]  [<c02572eb>] bus_add_driver+0x7b/0x1a0
[   25.784000]  [<c01fbc54>] __pci_register_driver+0x74/0xc0
[   25.784000]  [<e0c2fe62>] loader_init+0x102/0x220 [ndiswrapper]
[   25.784000]  [<e0c3e66f>] wrap_procfs_init+0x3f/0xb0 [ndiswrapper]
[   25.784000]  [<e09900c7>] wrapper_init+0xc7/0xd3 [ndiswrapper]
[   25.784000]  [<c014422d>] sys_init_module+0x15d/0x1ba0
[   25.784000]  [<c0107a5d>] sys_mmap2+0xcd/0xd0
[   25.784000]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[   25.784000]  [<c013007b>] do_timer+0x74b/0x820
[   25.784000]  =======================
[   25.784000] handlers:
[   25.784000] [<e087df10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[   25.784000] [<e087df10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[   25.784000] [<e087df10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[   25.784000] [<e086e720>] (e100_intr+0x0/0xc0 [e100])
[   25.784000] [<e09998b0>] (yenta_interrupt+0x0/0xe0 [yenta_socket])
[   25.784000] [<e09998b0>] (yenta_interrupt+0x0/0xe0 [yenta_socket])
[   25.784000] [<e087df10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[   25.784000] [<e0acd0e0>] (snd_intel8x0_interrupt+0x0/0x240 [snd_intel8x0])
[   25.784000] [<e087df10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[   25.784000] [<e087df10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[   25.784000] Disabling IRQ #11
[   25.788000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[   25.788000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[   26.180000] ndiswrapper: using IRQ 11
[   26.680000] wlan0: ethernet device 00:90:96:3d:73:6a using serialized NDIS driver: net5211, version: 0x20004, NDIS version: 0x501, vendor: '', 168C:0012.5.conf
[   26.680000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[   26.688000] usbcore: registered new interface driver ndiswrapper

Thank you for your help.  Would any more information be helpful?

---

### Post by kpjoyce on 2007-05-30
Any ideas what's wrong with ndiswrapper?

What's the deal with IRQ 11?  I think that I only get the "irq 11: nobody cared" message when ndiswrapper fails to load properly, but I don't know enough about what that means.  Eventually IRQ 11 is disabled and *then* assigned to ndiswrapper?

What would you try first?

Thanks.

---

### Post by greatwolf on 2007-11-06
See? this is why Linux will never be mainstream with the masses. I posted a major issue I had with my wireless adapter [here]("http://ubuntuforums.org/showthread.php?t=395912") and to this day it still hasn't gotten a single reply. I mean I putted in my fair share of time and effort of trying to get it to work and I did as much research as I can on my own in trying to troubleshoot the problem and still to no avail. 

I consider myself to be computer savvy -- like a lot of people on this board, but if someone like me can't even get this to work how is the average joe even suppose to use this?

---

