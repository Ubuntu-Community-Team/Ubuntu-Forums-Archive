---
title: "D-Link DWA-140 with ndiswrapper"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by malloq on 2007-12-02
Hi

I'm having trouble with my DWA-140 wireless adapter on one of my computers. In dmesg, I get this:

[  983.076000] BUG: unable to handle kernel paging request at virtual address f8e74004
[  983.076000]  printing eip:
[  983.076000] f8c982e1
[  983.076000] *pde = 1fe59067
[  983.076000] *pte = 00000000
[  983.076000] Oops: 0000 [#1]
[  983.076000] SMP 
[  983.076000] Modules linked in: nfs lockd sunrpc af_packet binfmt_misc rfcomm l2cap bluetooth ppdev ipv6 cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table video container sbs button dock ac battery nls_iso8859_1 nls_cp437 vfat fat ndiswrapper lp snd_via82xx snd_mpu401_uart snd_seq_dummy snd_ens1371 snd_seq_oss xpad gameport snd_ac97_codec nvidia(P) parport_pc parport i2c_viapro via_ircc ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_midi snd_seq_midi_event snd_seq snd_timer snd_rawmidi snd_seq_device pcspkr psmouse serio_raw snd i2c_core soundcore irda snd_page_alloc crc_ccitt shpchp pci_hotplug via_agp agpgart joydev evdev reiserfs ide_cd cdrom ide_disk usbhid hid via82cxxx ide_core floppy via_rhine mii ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
[  983.076000] CPU:    0
[  983.076000] EIP:    0060:[<f8c982e1>]    Tainted: P       VLI
[  983.076000] EFLAGS: 00010246   (2.6.22-14-generic #1)
[  983.076000] EIP is at 0xf8c982e1
[  983.076000] eax: f8e73ff4   ebx: e4528b38   ecx: 00000000   edx: f8e73ff4
[  983.076000] esi: e4528a80   edi: 00000002   ebp: dfd87f18   esp: dfd87e30
[  983.076000] ds: 007b   es: 007b   fs: 00d8  gs: 0000  ss: 0068
[  983.076000] Process ntos_wq (pid: 3886, ti=dfd86000 task=c1942000 task.ti=dfd86000)
[  983.076000] Stack: 00000002 e4528a80 00380000 c1809b00 00000003 00000003 00006000 c1981048 
[  983.076000]        00000000 c0108edf 00000000 dfb676f0 c1981048 dfb676c0 dfb6b500 f7dcfa40 
[  983.076000]        000000d0 f8eff029 00000000 00000000 00000003 e4528a80 c0408380 f8e6ec66 
[  983.076000] Call Trace:
[  983.076000]  [<c0108edf>] dma_alloc_coherent+0xcf/0x100
[  983.076000]  [<f8eff029>] wrap_alloc_urb+0x1b9/0x2d0 [ndiswrapper]
[  983.076000]  [<c0408380>] af_unix_init+0x20/0x70
[  983.076000]  [<c0408380>] af_unix_init+0x20/0x70
[  983.076000]  [<f8eff7b3>] wrap_submit_irp+0x4c3/0xb60 [ndiswrapper]
[  983.076000]  [<f8ef4d65>] IofCallDriver+0x55/0xc0 [ndiswrapper]
[  983.076000]  [<f8ef551c>] IofCompleteRequest+0x3c/0x1a0 [ndiswrapper]
[  983.076000]  [<f8effe96>] wrap_urb_complete_worker+0x46/0x120 [ndiswrapper]
[  983.076000]  [<f8effe50>] wrap_urb_complete_worker+0x0/0x120 [ndiswrapper]
[  983.076000]  [<c0138331>] run_workqueue+0x81/0x110
[  983.076000]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  983.076000]  [<c0138d30>] worker_thread+0x0/0x100
[  983.076000]  [<c0138dd0>] worker_thread+0xa0/0x100
[  983.076000]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  983.076000]  [<c0138d30>] worker_thread+0x0/0x100
[  983.076000]  [<c013bb12>] kthread+0x42/0x70
[  983.076000]  [<c013bad0>] kthread+0x0/0x70
[  983.076000]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  983.076000]  =======================
[  983.076000] Code: dc 8b 4d d0 8b 11 c1 ea 10 81 e2 ff 0f 00 00 66 89 55 d8 8b 45 d0 8b 48 04 c1 e9 1e 83 e1 03 83 e1 02 74 04 c6 45 bf 01 8b 55 e0 <0f> b6 42 10 83 f8 40 74 58 8b 4d e0 0f b6 51 10 83 fa 50 74 4c 
[  983.076000] EIP: [<f8c982e1>] 0xf8c982e1 SS:ESP 0068:dfd87e30

I've upgraded ndiswrapper to 1.50 now (from source), but the problem is still there. I'm using Ubuntu 7.10. The strange thing here is that the same adapter works fine on one of my other computers, also running Ubuntu 7.10. 

The computer that it fails on is rather old, but it supports USB 2.0. I've not had any trouble with other USB devices. Anyone had similar problems, and know a/the solution?

---

