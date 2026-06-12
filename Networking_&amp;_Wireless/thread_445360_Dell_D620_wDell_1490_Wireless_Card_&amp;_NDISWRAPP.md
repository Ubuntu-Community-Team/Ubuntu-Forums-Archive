---
title: "Dell D620 w/Dell 1490 Wireless Card &amp; NDISWRAPPER - Interesting issue"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by abray on 2007-05-15
I have set my laptop up with a dual boot - Windows XP and Ubuntu Feisty 64-bit.  I setup the wireless card using ndiswrapper and the only way I can get it to function it to boot to windows XP, reboot, and boot Ubuntu.  By doing this, the wi-fi led stay's lit and everything works.  

If I don't do this oI get the following fault:

May 15 20:42:19 abray-laptop kernel: [   25.434531] Modules linked in: ndiswrapper parport_pc lp parport fuse joydev snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pc
m snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq af_packet pcmcia nvidia(P) snd_timer snd_seq_device hci_usb bluetooth i2c_core yenta_socket rsrc_
nonstatic pcmcia_core psmouse intel_agp snd shpchp pci_hotplug iTCO_wdt iTCO_vendor_support serio_raw soundcore snd_page_alloc tsdev evdev ext3 jbd mbcache sg sr_mod cdrom sd_mo
d generic ata_generic ata_piix libata scsi_mod tg3 ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb cfbcopyarea cfbimgblt cfbfillrec
t capability commoncap
May 15 20:42:19 abray-laptop kernel: [   25.434567] Pid: 4316, comm: modprobe Tainted: P      2.6.20-15-generic #2
May 15 20:42:19 abray-laptop kernel: [   25.434570] RIP: 0010:[phys_startup_64+754183/2147483392]  [phys_startup_64+754183/2147483392]
May 15 20:42:19 abray-laptop kernel: [   25.434573] RSP: 0018:ffff81007453d6e0  EFLAGS: 00010282
May 15 20:42:19 abray-laptop kernel: [   25.434576] RAX: ffffc20000383a19 RBX: ffffc20000057000 RCX: ffffc2000004d000
May 15 20:42:19 abray-laptop kernel: [   25.434578] RDX: 00000000fffffffb RSI: 0000000000070000 RDI: ffffc2000004d000
May 15 20:42:19 abray-laptop kernel: [   25.434581] RBP: ffff810075d23580 R08: 0000000000000000 R09: ffffc20000048000
May 15 20:42:19 abray-laptop kernel: [   25.434583] R10: ffffffff88a44a00 R11: 00000000000000a5 R12: 0000000000000000
May 15 20:42:19 abray-laptop kernel: [   25.434585] R13: ffffc2000004d000 R14: ffffc20000383639 R15: 0000000000000001
May 15 20:42:19 abray-laptop kernel: [   25.434588] FS:  00002b34cf5486f0(0000) GS:ffffffff8054e000(0000) knlGS:0000000000000000
May 15 20:42:19 abray-laptop kernel: [   25.434591] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
May 15 20:42:19 abray-laptop kernel: [   25.434593] CR2: ffffc20000383a19 CR3: 00000000739bc000 CR4: 00000000000006e0
May 15 20:42:19 abray-laptop kernel: [   25.434596] Process modprobe (pid: 4316, threadinfo ffff81007453c000, task ffff81007428e860)
May 15 20:42:19 abray-laptop kernel: [   25.434598] Stack:  4243812a7466a720 0000000000000100 ffff8100745b4312 ffffc2000004d000
May 15 20:42:19 abray-laptop kernel: [   25.434603]  ffff810037dc9200 0000000000000001 0000000000000000 ffffc2000025812a
May 15 20:42:19 abray-laptop kernel: [   25.434607]  0000000000000800 0000000000000000 ffffffff88a5c317 0000000000000000
May 15 20:42:19 abray-laptop kernel: [   25.434610] Call Trace:
May 15 20:42:19 abray-laptop kernel: [   25.434635]  [_end+138572679/2130489456] :ndiswrapper:win2lin2+0xe/0x11
May 15 20:42:19 abray-laptop kernel: [   25.434652]  [pci_request_region+206/416] pci_request_region+0xce/0x1a0
May 15 20:42:19 abray-laptop kernel: [   25.434670]  [_end+138532344/2130489456] :ndiswrapper:IofCompleteRequest+0x48/0x160
May 15 20:42:19 abray-laptop kernel: [   25.434692]  [_end+138554554/2130489456] :ndiswrapper:miniport_init+0xaa/0x180
May 15 20:42:19 abray-laptop kernel: [   25.434710]  [_end+138535376/2130489456] :ndiswrapper:IoSyncForwardIrp+0x90/0xd0
May 15 20:42:19 abray-laptop kernel: [   25.434729]  [_end+138555067/2130489456] :ndiswrapper:NdisDispatchPnp+0xab/0xcb0
May 15 20:42:19 abray-laptop kernel: [   25.434735]  [thread_return+104/245] thread_return+0x68/0xf5
May 15 20:42:19 abray-laptop kernel: [   25.434756]  [_end+138531627/2130489456] :ndiswrapper:IoInitializeIrp+0x3b/0x70
May 15 20:42:19 abray-laptop kernel: [   25.434776]  [_end+138572679/2130489456] :ndiswrapper:win2lin2+0xe/0x11
May 15 20:42:19 abray-laptop kernel: [   25.434794]  [_end+138529947/2130489456] :ndiswrapper:IofCallDriver+0x8b/0xc0
May 15 20:42:19 abray-laptop kernel: [   25.434811]  [_end+138529904/2130489456] :ndiswrapper:IofCallDriver+0x60/0xc0
May 15 20:42:19 abray-laptop kernel: [   25.434829]  [_end+138533743/2130489456] :ndiswrapper:IoBuildSynchronousFsdRequest+0x2f/0x50
May 15 20:42:19 abray-laptop kernel: [   25.434847]  [_end+138539548/2130489456] :ndiswrapper:IoSendIrpTopDev+0xac/0x100
May 15 20:42:19 abray-laptop kernel: [   25.434867]  [_end+138540303/2130489456] :ndiswrapper:pnp_start_device+0x4f/0xb0
May 15 20:42:19 abray-laptop kernel: [   25.434888]  [_end+138540923/2130489456] :ndiswrapper:wrap_pnp_start_device+0x20b/0x250
May 15 20:42:19 abray-laptop kernel: [   25.434909]  [_end+138541072/2130489456] :ndiswrapper:wrap_pnp_start_pci_device+0x50/0x60
May 15 20:42:19 abray-laptop kernel: [   25.434915]  [sysfs_make_dirent+41/176] sysfs_make_dirent+0x29/0xb0
May 15 20:42:19 abray-laptop kernel: [   25.434921]  [pci_device_probe+225/368] pci_device_probe+0xe1/0x170
May 15 20:42:19 abray-laptop kernel: [   25.434926]  [really_probe+229/400] really_probe+0xe5/0x190
May 15 20:42:19 abray-laptop kernel: [   25.434930]  [__driver_attach+124/208] __driver_attach+0x7c/0xd0
May 15 20:42:19 abray-laptop kernel: [   25.434934]  [__driver_attach+0/208] __driver_attach+0x0/0xd0
May 15 20:42:19 abray-laptop kernel: [   25.434937]  [bus_for_each_dev+73/128] bus_for_each_dev+0x49/0x80
May 15 20:42:19 abray-laptop kernel: [   25.434943]  [bus_add_driver+126/480] bus_add_driver+0x7e/0x1e0
May 15 20:42:19 abray-laptop kernel: [   25.434947]  [__pci_register_driver+135/208] __pci_register_driver+0x87/0xd0
May 15 20:42:19 abray-laptop kernel: [   25.434961]  [_end+138491244/2130489456] :ndiswrapper:loader_init+0x15c/0x250
May 15 20:42:19 abray-laptop kernel: [   25.434972]  [_end+128159982/2130489456] :ndiswrapper:wrapper_init+0x7e/0xb6
May 15 20:42:19 abray-laptop kernel: [   25.434977]  [sys_init_module+6405/6832] sys_init_module+0x1905/0x1ab0
May 15 20:42:19 abray-laptop kernel: [   25.434986]  [__up_write+33/304] __up_write+0x21/0x130
May 15 20:42:19 abray-laptop kernel: [   25.434994]  [system_call+126/131] system_call+0x7e/0x83
May 15 20:42:19 abray-laptop kernel: [   25.435000] 
May 15 20:42:19 abray-laptop kernel: [   25.435001] 
May 15 20:42:19 abray-laptop kernel: [   25.435002] Code: 66 8b 00 66 89 44 24 30 44 0f b7 44 24 30 41 8b c8 c1 e9 08 
May 15 20:42:19 abray-laptop kernel: [   25.435014]  RSP <ffff81007453d6e0>
May 15 20:42:19 abray-laptop kernel: [   25.435017]  <3>ibm_acpi: ec object not found

If I suspend and resume my laptop, I get this fault:

May 15 20:01:27 abray-laptop kernel: [ 1793.939986] Pid: 7425, comm: modprobe Tainted: P      2.6.20-15-generic #2
May 15 20:01:27 abray-laptop kernel: [ 1793.939989] RIP: 0010:[_end+138527537/2130489456]  [_end+138527537/2130489456] :ndiswrapper:NdisMDeregisterInterrupt+0x11/0x60
May 15 20:01:27 abray-laptop kernel: [ 1793.940005] RSP: 0018:ffff81004d58db30  EFLAGS: 00010286
May 15 20:01:27 abray-laptop kernel: [ 1793.940008] RAX: 0000000000000246 RBX: ffffc200000360f8 RCX: ffff81000000c000
May 15 20:01:27 abray-laptop kernel: [ 1793.940010] RDX: 0000000000000047 RSI: 0000000000000000 RDI: ffffc200000360f8
May 15 20:01:27 abray-laptop kernel: [ 1793.940012] RBP: ffff81007632c500 R08: 0000000000000000 R09: ffff810078d1c3c0
May 15 20:01:27 abray-laptop kernel: [ 1793.940015] R10: ffffffff88a50590 R11: 0000000000000020 R12: ffff81007632c500
May 15 20:01:27 abray-laptop kernel: [ 1793.940017] R13: ffff81006be30600 R14: 00000000c0000001 R15: 000000000000001b
May 15 20:01:27 abray-laptop kernel: [ 1793.940020] FS:  00002aab23dd56f0(0000) GS:ffffffff8054e000(0000) knlGS:0000000000000000
May 15 20:01:27 abray-laptop kernel: [ 1793.940023] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
May 15 20:01:27 abray-laptop kernel: [ 1793.940025] CR2: ffffc20000036160 CR3: 0000000067b55000 CR4: 00000000000006e0
May 15 20:01:27 abray-laptop kernel: [ 1793.940028] Process modprobe (pid: 7425, threadinfo ffff81004d58c000, task ffff810037e05180)
May 15 20:01:27 abray-laptop kernel: [ 1793.940030] Stack:  ffff810078d1c3c0 0000000000000000 ffff81007632c500 ffffffff88a5132b
May 15 20:01:27 abray-laptop kernel: [ 1793.940035]  00000000c0000001 0000000000000000 ffff81007632c500 ffff81007632c7d0
May 15 20:01:27 abray-laptop kernel: [ 1793.940039]  ffff81006be30600 ffffffff88a5e713 ffff810037cb4630 ffff81007632c500
May 15 20:01:27 abray-laptop kernel: [ 1793.940043] Call Trace:
May 15 20:01:27 abray-laptop kernel: [ 1793.940061]  [_end+138527643/2130489456] :ndiswrapper:ndis_exit_device+0x1b/0xe0
May 15 20:01:27 abray-laptop kernel: [ 1793.940082]  [_end+138581891/2130489456] :ndiswrapper:wrap_ndis_remove_device+0x183/0x210
May 15 20:01:27 abray-laptop kernel: [ 1793.940102]  [_end+138586690/2130489456] :ndiswrapper:NdisDispatchPnp+0xc32/0xcb0
May 15 20:01:27 abray-laptop kernel: [ 1793.940113]  [vsnprintf+1451/1536] vsnprintf+0x5ab/0x600
May 15 20:01:27 abray-laptop kernel: [ 1793.940119]  [task_rq_lock+76/144] task_rq_lock+0x4c/0x90
May 15 20:01:27 abray-laptop kernel: [ 1793.940122]  [__activate_task+56/96] __activate_task+0x38/0x60
May 15 20:01:27 abray-laptop kernel: [ 1793.940128]  [try_to_wake_up+988/1024] try_to_wake_up+0x3dc/0x400
May 15 20:01:27 abray-laptop kernel: [ 1793.940147]  [_end+138560299/2130489456] :ndiswrapper:IoInitializeIrp+0x3b/0x70
May 15 20:01:27 abray-laptop kernel: [ 1793.940170]  [_end+138601351/2130489456] :ndiswrapper:win2lin2+0xe/0x11
May 15 20:01:27 abray-laptop kernel: [ 1793.940189]  [_end+138558619/2130489456] :ndiswrapper:IofCallDriver+0x8b/0xc0
May 15 20:01:27 abray-laptop kernel: [ 1793.940208]  [_end+138558576/2130489456] :ndiswrapper:IofCallDriver+0x60/0xc0
May 15 20:01:27 abray-laptop kernel: [ 1793.940227]  [_end+138562415/2130489456] :ndiswrapper:IoBuildSynchronousFsdRequest+0x2f/0x50
May 15 20:01:27 abray-laptop kernel: [ 1793.940246]  [_end+138568220/2130489456] :ndiswrapper:IoSendIrpTopDev+0xac/0x100
May 15 20:01:27 abray-laptop kernel: [ 1793.940250]  [bit_waitqueue+71/224] bit_waitqueue+0x47/0xe0
May 15 20:01:27 abray-laptop kernel: [ 1793.940274]  [_end+138568436/2130489456] :ndiswrapper:pnp_remove_device+0x84/0x1b0
May 15 20:01:27 abray-laptop kernel: [ 1793.940282]  [pci_device_remove+44/96] pci_device_remove+0x2c/0x60
May 15 20:01:27 abray-laptop kernel: [ 1793.940288]  [__device_release_driver+145/192] __device_release_driver+0x91/0xc0
May 15 20:01:27 abray-laptop kernel: [ 1793.940293]  [driver_detach+200/272] driver_detach+0xc8/0x110
May 15 20:01:27 abray-laptop kernel: [ 1793.940299]  [bus_remove_driver+129/176] bus_remove_driver+0x81/0xb0
May 15 20:01:27 abray-laptop kernel: [ 1793.940304]  [driver_unregister+13/32] driver_unregister+0xd/0x20
May 15 20:01:27 abray-laptop kernel: [ 1793.940308]  [pci_unregister_driver+24/144] pci_unregister_driver+0x18/0x90
May 15 20:01:27 abray-laptop kernel: [ 1793.940323]  [_end+138516263/2130489456] :ndiswrapper:unregister_devices+0x97/0xb0
May 15 20:01:27 abray-laptop kernel: [ 1793.940337]  [_end+138516622/2130489456] :ndiswrapper:loader_exit+0x1e/0xa0
May 15 20:01:27 abray-laptop kernel: [ 1793.940356]  [_end+138595145/2130489456] :ndiswrapper:module_cleanup+0x9/0x40
May 15 20:01:27 abray-laptop kernel: [ 1793.940361]  [sys_delete_module+432/512] sys_delete_module+0x1b0/0x200
May 15 20:01:27 abray-laptop kernel: [ 1793.940367]  [__up_write+33/304] __up_write+0x21/0x130
May 15 20:01:27 abray-laptop kernel: [ 1793.940377]  [system_call+126/131] system_call+0x7e/0x83
May 15 20:01:27 abray-laptop kernel: [ 1793.940386] 
May 15 20:01:27 abray-laptop kernel: [ 1793.940387] 
May 15 20:01:27 abray-laptop kernel: [ 1793.940388] Code: 4c 8b 67 68 49 8b bc 24 f0 02 00 00 48 83 c7 28 e8 ba 34 00 
May 15 20:01:27 abray-laptop kernel: [ 1793.940413]  RSP <ffff81004d58db30>

Any ideas on how I can fix this so at least I don't have to boot to Windows XP first to initialize the card.

:guitar:

---

### Post by abray on 2007-05-15
Sorry, forgot to mention I'm using NDISWRAPPER 1.43 compiled from the tarball.

utils version: 1.9
driver filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.43
vermagic:       2.6.20-15-generic SMP mod_unload

Below are the log entries after booting to Windows and then rebooting into Ubuntu and the network card working:

May 15 20:43:18 abray-laptop kernel: [   26.472839] ndiswrapper version 1.43 loaded (smp=yes)
May 15 20:43:18 abray-laptop kernel: [   26.566832] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
May 15 20:43:18 abray-laptop kernel: [   26.568441] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
May 15 20:43:18 abray-laptop kernel: [   26.568709] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
May 15 20:43:18 abray-laptop kernel: [   26.577166] ndiswrapper: using IRQ 17
May 15 20:43:18 abray-laptop kernel: [   26.954695] wlan0: ethernet device 00:16:cf:b1:61:6c using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: '', 14E4
:4312.5.conf
May 15 20:43:18 abray-laptop kernel: [   26.954765] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
May 15 20:43:18 abray-laptop kernel: [   26.957201] ndiswrapper: changing interface name from 'wlan0' to 'eth1'

---

### Post by abray on 2007-05-16
Interesting point.  If my laptop is docked in the docking station, the wireless adapter will initialize without me needing to boot to Windows first.

:confused:

---

### Post by abray on 2007-05-19
Okay,

So I've been tinkering around and have found that at times I can boot up my laptop without going to Windows 1st and the WiFI LED will light up and everything will work fine.  It's approximately 50% of the time I'll boot up the system and get the following failure:

May 19 08:44:10 abray-laptop kernel: [   24.738007] ndiswrapper version 1.43 loaded (smp=yes)
May 19 08:44:10 abray-laptop kernel: [   24.816669] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
May 19 08:44:10 abray-laptop kernel: [   24.818264] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
May 19 08:44:10 abray-laptop kernel: [   24.818537] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
May 19 08:44:10 abray-laptop kernel: [   24.826218] PGD 7c832067 PUD 7c833067 PMD 7c29c067 PTE 0
May 19 08:44:10 abray-laptop kernel: [   24.826224] CPU 0 
May 19 08:44:10 abray-laptop kernel: [   24.826226] Modules linked in: ndiswrapper parport_pc lp parport fuse joydev snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pc
m snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi pcmcia snd_seq_midi_event nvidia(P) af_packet snd_seq hci_usb i2c_core snd_timer snd_seq_device bluetooth serio_raw yenta_so
cket rsrc_nonstatic pcmcia_core snd soundcore snd_page_alloc iTCO_wdt iTCO_vendor_support shpchp psmouse pci_hotplug intel_agp evdev tsdev ext3 jbd mbcache sg sr_mod cdrom sd_mo
d generic ata_generic tg3 ata_piix libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb cfbcopyarea cfbimgblt cfbfillrec
t capability commoncap
May 19 08:44:10 abray-laptop kernel: [   24.826262] Pid: 4302, comm: modprobe Tainted: P      2.6.20-15-generic #2
May 19 08:44:10 abray-laptop kernel: [   24.826265] RIP: 0010:[phys_startup_64+754183/2147483392]  [phys_startup_64+754183/2147483392]
May 19 08:44:10 abray-laptop kernel: [   24.826268] RSP: 0018:ffff8100762df6e0  EFLAGS: 00010286
May 19 08:44:10 abray-laptop kernel: [   24.826271] RAX: ffffc20000323814 RBX: ffffc20000057000 RCX: ffffc2000004d000
May 19 08:44:10 abray-laptop kernel: [   24.826273] RDX: 00000000fffffffb RSI: 0000000000070000 RDI: ffffc2000004d000
May 19 08:44:10 abray-laptop kernel: [   24.826276] RBP: ffff81007d13fa40 R08: 0000000000000000 R09: ffffc20000048000
May 19 08:44:10 abray-laptop kernel: [   24.826278] R10: ffffffff88a4da00 R11: 00000000000000a5 R12: 0000000000000000
May 19 08:44:10 abray-laptop kernel: [   24.826280] R13: ffffc2000004d000 R14: ffffc20000323434 R15: 0000000000000001
May 19 08:44:10 abray-laptop kernel: [   24.826283] FS:  00002af3078856f0(0000) GS:ffffffff8054e000(0000) knlGS:0000000000000000
May 19 08:44:10 abray-laptop kernel: [   24.826286] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
May 19 08:44:10 abray-laptop kernel: [   24.826288] CR2: ffffc20000323814 CR3: 0000000074984000 CR4: 00000000000006e0
May 19 08:44:10 abray-laptop kernel: [   24.826291] Process modprobe (pid: 4302, threadinfo ffff8100762de000, task ffff81007c27c100)
May 19 08:44:10 abray-laptop kernel: [   24.826293] Stack:  4243812a740bd540 0000000000000100 ffff810074644312 ffffc2000004d000
May 19 08:44:10 abray-laptop kernel: [   24.826298]  ffff810037f57c00 0000000000000001 0000000000000000 ffffc2000025812a
May 19 08:44:10 abray-laptop kernel: [   24.826302]  0000000000000800 0000000000000000 ffffffff88a65317 0000000000000000
May 19 08:44:10 abray-laptop kernel: [   24.826305] Call Trace:
May 19 08:44:10 abray-laptop kernel: [   24.826331]  [_end+138609543/2130489456] :ndiswrapper:win2lin2+0xe/0x11
May 19 08:44:10 abray-laptop kernel: [   24.826349]  [pci_request_region+206/416] pci_request_region+0xce/0x1a0
May 19 08:44:10 abray-laptop kernel: [   24.826366]  [_end+138569208/2130489456] :ndiswrapper:IofCompleteRequest+0x48/0x160
May 19 08:44:10 abray-laptop kernel: [   24.826388]  [_end+138591418/2130489456] :ndiswrapper:miniport_init+0xaa/0x180
May 19 08:44:10 abray-laptop kernel: [   24.826406]  [_end+138572240/2130489456] :ndiswrapper:IoSyncForwardIrp+0x90/0xd0
May 19 08:44:10 abray-laptop kernel: [   24.826425]  [_end+138591931/2130489456] :ndiswrapper:NdisDispatchPnp+0xab/0xcb0
May 19 08:44:10 abray-laptop kernel: [   24.826431]  [thread_return+104/245] thread_return+0x68/0xf5
May 19 08:44:10 abray-laptop kernel: [   24.826452]  [_end+138568491/2130489456] :ndiswrapper:IoInitializeIrp+0x3b/0x70
May 19 08:44:10 abray-laptop kernel: [   24.826472]  [_end+138609543/2130489456] :ndiswrapper:win2lin2+0xe/0x11
May 19 08:44:10 abray-laptop kernel: [   24.826490]  [_end+138566811/2130489456] :ndiswrapper:IofCallDriver+0x8b/0xc0
May 19 08:44:10 abray-laptop kernel: [   24.826508]  [_end+138566768/2130489456] :ndiswrapper:IofCallDriver+0x60/0xc0
May 19 08:44:10 abray-laptop kernel: [   24.826525]  [_end+138570607/2130489456] :ndiswrapper:IoBuildSynchronousFsdRequest+0x2f/0x50
May 19 08:44:10 abray-laptop kernel: [   24.826543]  [_end+138576412/2130489456] :ndiswrapper:IoSendIrpTopDev+0xac/0x100
May 19 08:44:10 abray-laptop kernel: [   24.826563]  [_end+138577167/2130489456] :ndiswrapper:pnp_start_device+0x4f/0xb0
May 19 08:44:10 abray-laptop kernel: [   24.826584]  [_end+138577787/2130489456] :ndiswrapper:wrap_pnp_start_device+0x20b/0x250
May 19 08:44:10 abray-laptop kernel: [   24.826605]  [_end+138577936/2130489456] :ndiswrapper:wrap_pnp_start_pci_device+0x50/0x60
May 19 08:44:10 abray-laptop kernel: [   24.826611]  [sysfs_make_dirent+41/176] sysfs_make_dirent+0x29/0xb0
May 19 08:44:10 abray-laptop kernel: [   24.826617]  [pci_device_probe+225/368] pci_device_probe+0xe1/0x170
May 19 08:44:10 abray-laptop kernel: [   24.826623]  [really_probe+229/400] really_probe+0xe5/0x190
May 19 08:44:10 abray-laptop kernel: [   24.826627]  [__driver_attach+124/208] __driver_attach+0x7c/0xd0
May 19 08:44:10 abray-laptop kernel: [   24.826631]  [__driver_attach+0/208] __driver_attach+0x0/0xd0
May 19 08:44:10 abray-laptop kernel: [   24.826634]  [bus_for_each_dev+73/128] bus_for_each_dev+0x49/0x80
May 19 08:44:10 abray-laptop kernel: [   24.826639]  [bus_add_driver+126/480] bus_add_driver+0x7e/0x1e0
May 19 08:44:10 abray-laptop kernel: [   24.826643]  [__pci_register_driver+135/208] __pci_register_driver+0x87/0xd0
May 19 08:44:10 abray-laptop kernel: [   24.826657]  [_end+138528108/2130489456] :ndiswrapper:loader_init+0x15c/0x250
May 19 08:44:10 abray-laptop kernel: [   24.826669]  [_end+128159982/2130489456] :ndiswrapper:wrapper_init+0x7e/0xb6
May 19 08:44:10 abray-laptop kernel: [   24.826674]  [sys_init_module+6405/6832] sys_init_module+0x1905/0x1ab0
May 19 08:44:10 abray-laptop kernel: [   24.826683]  [__up_write+33/304] __up_write+0x21/0x130
May 19 08:44:10 abray-laptop kernel: [   24.826690]  [system_call+126/131] system_call+0x7e/0x83
May 19 08:44:10 abray-laptop kernel: [   24.826696] 
May 19 08:44:10 abray-laptop kernel: [   24.826697] 
May 19 08:44:10 abray-laptop kernel: [   24.826698] Code: 66 8b 00 66 89 44 24 30 44 0f b7 44 24 30 41 8b c8 c1 e9 08 
May 19 08:44:10 abray-laptop kernel: [   24.826710]  RSP <ffff8100762df6e0>
May 19 08:44:10 abray-laptop kernel: [   24.826714]  <3>ibm_acpi: ec object not found


Any ideas?

---

### Post by abray on 2007-05-21
FYI,

Just discovered NDISWRAPPER v1.44 was released and resolves an issue with 64-bit systems with a gig of more of RAM and Broadcom adapters.  That matches perfectly! :P

Just updated and so far it worked - only booted once.

:popcorn:

---

### Post by abray on 2007-05-23
Issue seems to be resolved - upgrading to Ndiswrapper 1.44 worked.

---

### Post by abray on 2007-06-04
Issue actually returned - I've tried both 1.44 and 1.45 :(  

Seems to Oops about 25 - 50% of the time.

If anyone else hits this, please let me know.  Thanks.

---

