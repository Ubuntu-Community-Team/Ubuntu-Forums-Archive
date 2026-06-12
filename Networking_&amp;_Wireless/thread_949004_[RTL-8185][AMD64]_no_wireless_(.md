---
title: "[RTL-8185][AMD64] no wireless :("
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by TagUrIt on 2008-10-15
I'm running Ubuntu 8.04 (64 bit) on my gateway laptop (AMD64).  The wireless adapter, according to **lshw**, is RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller.  (This sounds right to me).

However, I can't get it to work.  I found a bunch of different suggestions for doing this.  I tried using **ndiswrapper** with WinME and also WinXP drivers for the 8185, but neither worked fully.  I'd get to the point that it seemed to have worked (ndiswrapper didn't say any errors), but looking at **dmesg** output informed me that the problem was due to using a 32bit driver on the 64bit system.

```
[  272.149046] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  272.163242] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  272.163250] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8185'
[  272.164671] ndiswrapper (load_wrap_driver:108): couldn't load driver net8185; check system log for messages from 'loadndisdriver'
[  272.164711] usbcore: registered new interface driver ndiswrapper

```

I tried using the Realtek 8185 driver for 64 bit Windows, but it seems to have locked up trying a very long time ago.  After killing the process, I checked **dmesg** again, only to find a lovely long block explaining the failure (I think), but I can't figure out what any of it means.

```
[  662.046346] ndiswrapper (ntoskernel_exit:2671): object ffff8100396f3e30(2) was not freed, freeing it now
[  662.074414] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  662.092298] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
[  662.093647] ndiswrapper: driver net8185x64 (Realtek,03/21/2008,5.1105.0321.2008) loaded
[  662.095007] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 22 (level, low) -> IRQ 22
[  662.357245] ndiswrapper: using IRQ 22
[  662.815404] general protection fault: 0000 [1] SMP 
[  662.815412] CPU 0 
[  662.815414] Modules linked in: ndiswrapper af_packet ipv6 radeon drm rfcomm l2cap bluetooth ppdev powernow_k8 cpufreq_stats cpufreq_ondemand freq_table cpufreq_conservative cpufreq_userspace cpufreq_powersave container sbs sbshc dock iptable_filter ip_tables x_tables nls_iso8859_1 nls_cp437 vfat fat sbp2 parport_pc lp parport joydev pcmcia snd_atiixp sky2 video output snd_seq_dummy snd_seq_oss serio_raw snd_seq_midi sdhci snd_atiixp_modem snd_ac97_codec snd_rawmidi tifm_7xx1 psmouse ac97_bus mmc_core snd_seq_midi_event tifm_core yenta_socket rsrc_nonstatic pcmcia_core snd_pcm_oss snd_mixer_oss snd_seq snd_seq_device battery ac i2c_piix4 button snd_pcm snd_timer shpchp pci_hotplug k8temp evdev i2c_core snd soundcore snd_page_alloc pcspkr ext3 jbd mbcache sg sr_mod cdrom sd_mod atiixp ide_core pata_acpi pata_atiixp ohci1394 ieee1394 ata_generic libata scsi_mod ehci_hcd ohci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  662.815461] Pid: 8067, comm: ntos_wq Tainted: P        2.6.24-16-generic #1
[  662.815463] RIP: 0010:[<ffffc20001050b8a>]  [<ffffc20001050b8a>]
[  662.815467] RSP: 0018:ffff81001dce7be8  EFLAGS: 00010246
[  662.815469] RAX: 0000c20001085538 RBX: ffffc20001092000 RCX: ffffc20001092000
[  662.815471] RDX: ffff81000de15000 RSI: ffffc20001092000 RDI: 0000000000004000
[  662.815473] RBP: ffffffff80624760 R08: 0000000000000000 R09: ffff810039810000
[  662.815475] R10: ffffffff883276d0 R11: ffff81001dce7dc0 R12: ffff81001de66000
[  662.815477] R13: 0000000000000000 R14: 0000000000000000 R15: 0000000000000010
[  662.815479] FS:  00007f28d1fc56e0(0000) GS:ffffffff805b0000(0000) knlGS:0000000000000000
[  662.815481] CS:  0010 DS: 0018 ES: 0018 CR0: 0000000080050033
[  662.815482] CR2: 00007f35d37aef10 CR3: 000000000dd1e000 CR4: 00000000000006e0
[  662.815484] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  662.815486] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  662.815488] Process ntos_wq (pid: 8067, threadinfo ffff81001dce6000, task ffff81000debef80)
[  662.815490] Stack:  0000000011018023 0300003c0b010a3c 0000000011018823 0300003cbd010b3c
[  662.815494]  3b3c080800019023 00003c1d01040000 08080000003b5105 3c2f010400003c11
[  662.815497]  0000003c2f050000 0808000039aa0808 0257011c00003c23 2f0500003c500000
[  662.815500] Call Trace:
[  662.815526]  [<ffffffff80231bec>] update_curr+0xac/0xc0
[  662.815536]  [<ffffffff802477c4>] lock_timer_base+0x34/0x70
[  662.815542]  [<ffffffff80247992>] __mod_timer+0xc2/0xe0
[  662.815591]  [<ffffffff88325c64>] :ndiswrapper:deserialized_irq_handler+0x14/0x30
[  662.815617]  [<ffffffff8833a9d2>] :ndiswrapper:win2lin4+0x14/0x17
[  662.815634]  [<ffffffff8832b471>] :ndiswrapper:kdpc_worker+0xc1/0x140
[  662.815640]  [<ffffffff804614d9>] mutex_lock+0x9/0x20
[  662.815655]  [<ffffffff8832b458>] :ndiswrapper:kdpc_worker+0xa8/0x140
[  662.815672]  [<ffffffff8832b3b0>] :ndiswrapper:kdpc_worker+0x0/0x140
[  662.815676]  [<ffffffff8024f21c>] run_workqueue+0xcc/0x170
[  662.815678]  [<ffffffff8024fda0>] worker_thread+0x0/0x110
[  662.815683]  [<ffffffff8024fda0>] worker_thread+0x0/0x110
[  662.815687]  [<ffffffff8024fe43>] worker_thread+0xa3/0x110
[  662.815691]  [<ffffffff80253960>] autoremove_wake_function+0x0/0x30
[  662.815697]  [<ffffffff8024fda0>] worker_thread+0x0/0x110
[  662.815701]  [<ffffffff8024fda0>] worker_thread+0x0/0x110
[  662.815704]  [<ffffffff8025359b>] kthread+0x4b/0x80
[  662.815709]  [<ffffffff8020d198>] child_rip+0xa/0x12
[  662.815721]  [<ffffffff80253550>] kthread+0x0/0x80
[  662.815724]  [<ffffffff8020d18e>] child_rip+0x0/0x12
[  662.815728] 
[  662.815728] 
[  662.815729] Code: 66 0f 7f b4 24 a0 01 00 00 0f 84 5d 04 00 00 66 66 90 66 66 
[  662.815735] RIP  [<ffffc20001050b8a>]
[  662.815737]  RSP <ffff81001dce7be8>
[  662.815740] ---[ end trace 569a13690ad00970 ]---

```

(I also tried using Realtek's old Linux drivers, but I couldn't even get them to build correctly, due to several errors with things no longer being defined.)

I haven't yet been able to see the device listed when I do **iwconfig** or **ifconfig**, but I think that is because it doesn't have any valid drivers.  Here's the relevant output from **lshw -C network**

```
*-network
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ndiswrapper latency=64 maxlatency=64 mingnt=32

```
(It used to have some word in all caps after `*-network` but I can't remember it, and it isn't there now, even though I've unloaded all drivers.)

-----

Does anyone have any suggestions?

---

### Post by TagUrIt on 2008-10-16
Eh, I decided to just run the 32 bit version, and now it works as advertised.

---

