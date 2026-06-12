---
title: "Netgear WG311v3 / ndiswrapper / please help!"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by postred on 2007-07-27
Hi folks,

I'm rather new to ubuntu (read: about 1hr, most of it trying to get this damn wireless card working) and am having difficulty getting the Netgear WG311v3 working on Ubuntu 7.04 / amd64. I've tried a couple of things:

Compiling ndiswrapper 1.38 from source then:
ndiswrapper -i WG311v3.INF (works)
modprobe ndiswrapper ..... this dies with the following in /var/log/syslog:

ndiswrapper: using IRQ 17
Unable to handle kernel paging request at ffffc200c0405a08 RIP:
phys_startup_64+1823953/2147483392
PGD : bbce7067 PUD 0
Oops: 0000 [1] SMP

So I make uninstall and tried to use the ubuntu ndiswrapper packages (common, utils 1.9) but when I run modprobe ndiswrapper it seems the kernel module is not there

Have I missed something really obvious here?

I might add that the drivers I'm tring to use are for the marvell chipset, which lspci indicates mine is. They're also NOT the ones from the Netgear CD, I downloaded these from a link in a forum thread where people stated these would work with amd64

Can someone please help? This is rather irritating...

---

### Post by kevdog on 2007-07-27
Isnt this command :
modprobe ndiswrapper

suppose to be:
sudo modprobe ndiswrapper

Could you post more of the dmesg file???

---

### Post by postred on 2007-07-27
Thanks kevdog

Yes, sorry, was run with sudo ;)

Will have to get back to you on the syslog... I tried screwing around with different drivers and now the system hangs during boot (when 'configuring network')

I did manage for a while there to stop it from 'oopsing', however when that was achieved there was no wlan0 and upon inspection, syslog contained something about being unable to initialize the device :|

---

### Post by postred on 2007-07-27
Nevermind, I gave up and downloaded the i386 version... works like a charm :D

Thanks anyway, kevdog!

---

### Post by kevdog on 2007-07-27
The 64 bit version is much more error prone since there are fewer 64 bit drivers available.  That was most likely your problem -- you were using a 32 bit driver.

---

### Post by faux_05 on 2007-12-12
I am having a similar issue. The marvell chipset drivers (x64) worked perfectly, until i reinstalled kubuntu default settings (my housemate demands kubuntu... it's prettier...). Now ndiswrapper  outputs the following error in /var/log/syslog

```

Dec 12 20:23:16 rogue NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Dec 12 20:23:16 rogue dhclient: bound to 192.168.0.98 -- renewal in 286 seconds.
Dec 12 20:23:18 rogue kernel: [  963.763370] ndiswrapper version 1.45 loaded (smp=yes)
Dec 12 20:23:18 rogue kernel: [  963.815576] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
Dec 12 20:23:18 rogue kernel: [  963.816222] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
Dec 12 20:23:18 rogue kernel: [  963.816186] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 18
Dec 12 20:23:18 rogue kernel: [  963.816199] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [LNKA] -> GSI 18 (level, low) -> IRQ 18
Dec 12 20:23:18 rogue kernel: [  963.817778] ndiswrapper: using IRQ 18
Dec 12 20:23:18 rogue kernel: [  963.875047] Unable to handle kernel paging request at ffffc20174681110 RIP: 
Dec 12 20:23:18 rogue kernel: [  963.875054]  [phys_startup_64+17007676/-2147483648]
Dec 12 20:23:18 rogue kernel: [  963.875061] PGD 37876067 PUD 0 
Dec 12 20:23:18 rogue kernel: [  963.875064] Oops: 0000 [1] SMP 
Dec 12 20:23:18 rogue kernel: [  963.875067] CPU 0 
Dec 12 20:23:18 rogue kernel: [  963.875068] Modules linked in: ndiswrapper af_packet ipv6 rfcomm l2cap bluetooth fglrx(P) ppdev sg sd_mod cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative video sbs button dock container ac battery lp loop snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd quickcam soundcore usb_storage libusual videodev v4l2_common v4l1_compat snd_page_alloc parport_pc parport psmouse shpchp pci_hotplug pcspkr k8temp serio_raw i2c_nforce2 i2c_core evdev ext2 mbcache ide_cd cdrom ide_disk sata_nv usbhid hid ata_generic libata scsi_mod floppy forcedeth amd74xx ide_core ehci_hcd ohci_hcd usbcore thermal processor fan fuse apparmor commoncap
Dec 12 20:23:18 rogue kernel: [  963.875100] Pid: 6229, comm: modprobe Tainted: P       2.6.22-14-generic #1
Dec 12 20:23:18 rogue kernel: [  963.875103] RIP: 0010:[phys_startup_64+17007676/-2147483648]  [phys_startup_64+17007676/-2147483648]
Dec 12 20:23:18 rogue kernel: [  963.875107] RSP: 0018:ffff810024f137f0  EFLAGS: 00010216
Dec 12 20:23:18 rogue kernel: [  963.875109] RAX: 00000001734007c0 RBX: ffffc20001289000 RCX: 0000000000000005
Dec 12 20:23:18 rogue kernel: [  963.875111] RDX: 0000000000000000 RSI: 0000000000000000 RDI: 0000000000000005
Dec 12 20:23:18 rogue kernel: [  963.875113] RBP: ffff810024d06780 R08: 0000000000000000 R09: 0000000000000000
Dec 12 20:23:18 rogue kernel: [  963.875116] R10: ffffffff88472140 R11: ffffffff80422150 R12: 0000000005cd001f
Dec 12 20:23:18 rogue kernel: [  963.875119] R13: 0000000000000000 R14: 0000000000000000 R15: ffffc20001280950
Dec 12 20:23:18 rogue kernel: [  963.875122] FS:  00002b6131a586e0(0000) GS:ffffffff80560000(0000) knlGS:00000000f7e328c0
Dec 12 20:23:18 rogue kernel: [  963.875124] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Dec 12 20:23:18 rogue kernel: [  963.875127] CR2: ffffc20174681110 CR3: 0000000024e70000 CR4: 00000000000006e0
Dec 12 20:23:18 rogue kernel: [  963.875130] Process modprobe (pid: 6229, threadinfo ffff810024f12000, task ffff810024ee6000)
Dec 12 20:23:18 rogue kernel: [  963.875131] Stack:  ffffc20001289000 ffffc20001255cb9 0000000000000000 ffffc20001235c20
Dec 12 20:23:18 rogue kernel: [  963.875137]  000000000000001b 0000000000000000 ffff810047f57800 ffff810047f57e30
Dec 12 20:23:18 rogue kernel: [  963.875140]  0000000000000160 0000000000000000 ffffc20001289000 ffffc2000124583e
Dec 12 20:23:18 rogue kernel: [  963.875144] Call Trace:
Dec 12 20:23:18 rogue kernel: [  963.875179]  [_end+132260399/2130332920] :ndiswrapper:win2lin2+0xe/0x11
Dec 12 20:23:18 rogue kernel: [  963.875201]  [_end+132219175/2130332920] :ndiswrapper:IofCallDriver+0x5f/0xc0
Dec 12 20:23:18 rogue kernel: [  963.875216]  [_end+132219132/2130332920] :ndiswrapper:IofCallDriver+0x34/0xc0
Dec 12 20:23:18 rogue kernel: [  963.875232]  [_end+132246221/2130332920] :ndiswrapper:mp_init+0xa5/0x190
Dec 12 20:23:18 rogue kernel: [  963.875248]  [_end+132224440/2130332920] :ndiswrapper:IoSyncForwardIrp+0x90/0xd0
Dec 12 20:23:18 rogue kernel: [  963.875266]  [_end+132248099/2130332920] :ndiswrapper:NdisDispatchPnp+0xdb/0xd40
Dec 12 20:23:18 rogue kernel: [  963.875271]  [task_rq_lock+76/144] task_rq_lock+0x4c/0x90
Dec 12 20:23:18 rogue kernel: [  963.875276]  [__activate_task+41/80] __activate_task+0x29/0x50
Dec 12 20:23:18 rogue kernel: [  963.875281]  [kprobe_flush_task+88/176] kprobe_flush_task+0x58/0xb0
Dec 12 20:23:18 rogue kernel: [  963.875286]  [thread_return+1093/1737] thread_return+0x445/0x6c9
Dec 12 20:23:18 rogue kernel: [  963.875305]  [_end+132220867/2130332920] :ndiswrapper:IoInitializeIrp+0x3b/0x70
Dec 12 20:23:18 rogue kernel: [  963.875324]  [_end+132260399/2130332920] :ndiswrapper:win2lin2+0xe/0x11
Dec 12 20:23:18 rogue kernel: [  963.875339]  [_end+132219175/2130332920] :ndiswrapper:IofCallDriver+0x5f/0xc0
Dec 12 20:23:18 rogue kernel: [  963.875355]  [_end+132219132/2130332920] :ndiswrapper:IofCallDriver+0x34/0xc0
Dec 12 20:23:18 rogue kernel: [  963.875369]  [_end+132222967/2130332920] :ndiswrapper:IoBuildSynchronousFsdRequest+0x2f/0x50
Dec 12 20:23:18 rogue kernel: [  963.875386]  [_end+132240148/2130332920] :ndiswrapper:IoSendIrpTopDev+0xac/0x100
Dec 12 20:23:18 rogue kernel: [  963.875407]  [_end+132240919/2130332920] :ndiswrapper:pnp_start_device+0x4f/0xa0
Dec 12 20:23:18 rogue kernel: [  963.875428]  [_end+132241484/2130332920] :ndiswrapper:wrap_pnp_start_device+0x1e4/0x280
Dec 12 20:23:18 rogue kernel: [  963.875448]  [_end+132241720/2130332920] :ndiswrapper:wrap_pnp_start_pci_device+0x50/0x60
Dec 12 20:23:18 rogue kernel: [  963.875455]  [sysfs_make_dirent+48/80] sysfs_make_dirent+0x30/0x50
Dec 12 20:23:18 rogue kernel: [  963.875462]  [pci_device_probe+241/368] pci_device_probe+0xf1/0x170
Dec 12 20:23:18 rogue kernel: [  963.875470]  [driver_probe_device+163/432] driver_probe_device+0xa3/0x1b0
Dec 12 20:23:18 rogue kernel: [  963.875476]  [__driver_attach+201/208] __driver_attach+0xc9/0xd0
Dec 12 20:23:18 rogue kernel: [  963.875480]  [__driver_attach+0/208] __driver_attach+0x0/0xd0
Dec 12 20:23:18 rogue kernel: [  963.875484]  [bus_for_each_dev+77/128] bus_for_each_dev+0x4d/0x80
Dec 12 20:23:18 rogue kernel: [  963.875492]  [bus_add_driver+175/496] bus_add_driver+0xaf/0x1f0
Dec 12 20:23:18 rogue kernel: [  963.875497]  [__pci_register_driver+102/176] __pci_register_driver+0x66/0xb0
Dec 12 20:23:18 rogue kernel: [  963.875509]  [_end+132176468/2130332920] :ndiswrapper:loader_init+0x13c/0x260
Dec 12 20:23:18 rogue kernel: [  963.875519]  [_end+128019885/2130332920] :ndiswrapper:wrapper_init+0xb5/0xc2
Dec 12 20:23:18 rogue kernel: [  963.875525]  [sys_init_module+411/6576] sys_init_module+0x19b/0x19b0
Dec 12 20:23:18 rogue kernel: [  963.875538]  [__up_write+33/304] __up_write+0x21/0x130
Dec 12 20:23:18 rogue kernel: [  963.875547]  [system_call+126/131] system_call+0x7e/0x83
Dec 12 20:23:18 rogue kernel: [  963.875555] 
Dec 12 20:23:18 rogue kernel: [  963.875556] 
Dec 12 20:23:18 rogue kernel: [  963.875556] Code: 4a 8b 1c 38 48 8b 05 c1 8c 04 00 48 8d 88 b8 1f 00 00 ff 15 
Dec 12 20:23:18 rogue kernel: [  963.875563] RIP  [phys_startup_64+17007676/-2147483648]
Dec 12 20:23:18 rogue kernel: [  963.875566]  RSP <ffff810024f137f0>
Dec 12 20:23:18 rogue kernel: [  963.875568] CR2: ffffc20174681110
```

i hope that shows enough, its from the first to last ndiswrapper reference i could see.

Also, when i run in konsole sudo modprobe ndiswrapper or sudo modprobe -r ndiswrapper, the konsole hangs. on first entry sudo modprobe ndiswrapper shows "Killed" though.

i have tried removing, purging and reinstalling ndiswrapper (not sure how to take it out of the kernel at boot time tho). i've removed and attempted reinstalling the driver, but can't insert it into the kernel because of the problem above,

Also, sorry if i sound like a n00b, it's prolly just because i am lol.

i appreciate any help though, and i don't really want to do a re-install, i had a lot of grub, out-of-sync and problems getting it to run in the first place...

---

