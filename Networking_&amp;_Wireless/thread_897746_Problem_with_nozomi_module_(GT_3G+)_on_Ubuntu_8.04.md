---
title: "Problem with nozomi module (GT 3G+) on Ubuntu 8.04 64bit"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by kronk2002de on 2008-08-22
Hi.

I just got my "new" GlobeTrotter Option 3G+ UMTS PCMCIA card today and tried to install it. But if any process wants to use it, it causes a kernel oops. Here is what dmesg say about it:

```
[  465.866390] Unable to handle kernel NULL pointer dereference at 000000000000000c RIP: 
[  465.866400]  [<ffffffff8885f893>] :nozomi:ntty_chars_in_buffer+0x23/0x60
[  465.866414] PGD 1183d6067 PUD 10dc77067 PMD 0 
[  465.866421] Oops: 0000 [1] SMP 
[  465.866426] CPU 0 
[  465.866430] Modules linked in: usbserial nozomi aes_x86_64 aes_generic af_packet rfcomm l2cap bluetooth tun vboxdrv ppdev acpi_cpufreq cpufreq_ondemand cpufreq_userspace cpufreq_powersave cpufreq_conservative cpufreq_stats freq_table bay dock sbs sbshc bridge iptable_filter ip_tables x_tables ext2 sbp2 lp arc4 ecb blkcipher snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event iwl4965 snd_seq iwlwifi_mac80211 joydev pcmcia snd_timer snd_seq_device uvcvideo acer_acpi ipv6 fglrx(P) cfg80211 compat_ioctl32 videodev v4l1_compat v4l2_common sdhci snd battery container video output serio_raw yenta_socket rsrc_nonstatic pcmcia_core led_class ac button mmc_core pcspkr intel_agp tpm_infineon tpm tpm_bios iTCO_wdt iTCO_vendor_support parport_pc parport shpchp pci_hotplug psmouse evdev wmi_acer soundcore ext3 jbd mbcache sr_mod cdrom ata_generic sg sd_mod ata_piix ahci pata_acpi ohci1394 ieee1394 libata scsi_mod ehci_hcd uhci_hcd usbcore e1000 thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  465.866583] Pid: 7757, comm: wvdial Tainted: P        2.6.24-21-generic #1
[  465.866587] RIP: 0010:[<ffffffff8885f893>]  [<ffffffff8885f893>] :nozomi:ntty_chars_in_buffer+0x23/0x60
[  465.866598] RSP: 0018:ffff8101146ad9e0  EFLAGS: 00010202
[  465.866602] RAX: 0000000000000000 RBX: ffff81011c842800 RCX: ffffffff8054e624
[  465.866607] RDX: 0000000000000001 RSI: ffff81011c842a10 RDI: ffff81011c842800
[  465.866611] RBP: 0000000000000000 R08: 0000000000000000 R09: 0000000000000005
[  465.866615] R10: 0000000000000005 R11: 0000000000000246 R12: 0000000000000000
[  465.866620] R13: ffff8101361f8540 R14: 0000000000000000 R15: 00007fff029e4c30
[  465.866625] FS:  00007f7ffa9ca700(0000) GS:ffffffff805b9000(0000) knlGS:0000000000000000
[  465.866630] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  465.866634] CR2: 000000000000000c CR3: 000000010dc98000 CR4: 00000000000006e0
[  465.866638] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  465.866643] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  465.866648] Process wvdial (pid: 7757, threadinfo ffff8101146ac000, task ffff81011b0037a0)
[  465.866652] Stack:  ffffffff8039eb3d ffff81000102ef80 ffff8101361f8540 ffff81011c842800
[  465.866661]  0000000000000000 ffff81011c842818 ffffffff80399af6 0000000000000010
[  465.866669]  ffff8101361f8540 0000000000000004 0000000000000004 00007fff029e4bb0
[  465.866676] Call Trace:
[  465.866688]  [<ffffffff8039eb3d>] normal_poll+0x15d/0x190
[  465.866705]  [<ffffffff80399af6>] tty_poll+0x86/0xa0
[  465.866723]  [<ffffffff802c18ae>] do_select+0x2de/0x560
[  465.866772]  [<ffffffff802c20c0>] __pollwait+0x0/0x130
[  465.866789]  [<ffffffff8046664f>] thread_return+0x3a/0x57b
[  465.866800]  [<ffffffff8033b5a5>] submit_bio+0x75/0x100
[  465.866818]  [<ffffffff8025391c>] bit_waitqueue+0x1c/0xb0
[  465.866843]  [<ffffffff802a9a1f>] shmem_get_acl+0x1f/0x70
[  465.866860]  [<ffffffff80292a8d>] zone_statistics+0x7d/0x80
[  465.866917]  [<ffffffff88860436>] :nozomi:ntty_ioctl+0x26/0x630
[  465.866927]  [<ffffffff8028508d>] find_lock_page+0x3d/0xc0
[  465.866944]  [<ffffffff80287428>] filemap_fault+0x188/0x390
[  465.866965]  [<ffffffff802343d3>] __wake_up+0x43/0x70
[  465.866993]  [<ffffffff802c1d39>] core_sys_select+0x209/0x300
[  465.867036]  [<ffffffff802b5e40>] chrdev_open+0x0/0x1d0
[  465.867048]  [<ffffffff8034d531>] __up_read+0x21/0xb0
[  465.867061]  [<ffffffff8046a4c0>] do_page_fault+0x1d0/0x840
[  465.867071]  [<ffffffff802b0d37>] __dentry_open+0x1a7/0x200
[  465.867123]  [<ffffffff802c22c1>] sys_select+0xd1/0x1c0
[  465.867152]  [<ffffffff8020c37e>] system_call+0x7e/0x83
[  465.867186] 
[  465.867188] 
[  465.867189] Code: 8b 50 0c 2b 50 10 89 d0 c3 48 8b 58 70 48 8d 7b 70 e8 37 d0 
[  465.867208] RIP  [<ffffffff8885f893>] :nozomi:ntty_chars_in_buffer+0x23/0x60
[  465.867218]  RSP <ffff8101146ad9e0>
[  465.867221] CR2: 000000000000000c
[  465.867283] ---[ end trace c63775b63c496292 ]---

```

After this Oops the system get instable / unusable right after ejecting the PCMCIA card. If a Teminal is open, it flips all last commands and the keyboard is out-of-order :(

Can anybody help me?

My specs: Acer Travelmate 6592G, Ubuntu 8.04 64bit, kernel: 2.6.24-21-generic.

So long,
Holger

---

