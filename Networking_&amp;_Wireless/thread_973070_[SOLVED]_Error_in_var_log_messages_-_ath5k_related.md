---
title: "[SOLVED] Error in var log messages - ath5k related?"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by pmsumner on 2008-11-06
Can anyone shed any light on why I get this repeated every ~10mins in /var/log/messages?  The exact error varies but it always has a reference to ath5k

> Nov  6 15:53:46 home-laptop kernel: [62243.213983] ------------[ cut here ]------------
Nov  6 15:53:46 home-laptop kernel: [62243.214001] WARNING: at /build/buildd/linux-backports-modules-2.6.27-2.6.27/debian/build/build-generic/compat-wireless-2.6/net/mac80211/rx.c:2200 lbm_cw___lbm_cw_ieee80211_rx+0x19f/0x600 [lbm_cw_mac80211]()
Nov  6 15:53:46 home-laptop kernel: [62243.214012] Modules linked in: usbhid hid af_packet binfmt_misc rfcomm bridge stp bnep sco l2cap bluetooth ppdev ipv6 acpi_cpufreq cpufreq_ondemand cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_conservative pci_slot sbs sbshc container iptable_filter ip_tables x_tables acerhk parport_pc lp parport joydev snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy evdev battery arc4 snd_seq_oss ecb ac video crypto_blkcipher snd_seq_midi output snd_rawmidi snd_seq_midi_event snd_seq ath5k snd_timer snd_seq_device psmouse serio_raw lbm_cw_mac80211 fglrx(P) snd lbm_cw_cfg80211 led_class wmi button pcspkr i2c_piix4 soundcore snd_page_alloc ati_agp i2c_core agpgart shpchp pci_hotplug ext3 jbd mbcache sd_mod crc_t10dif sr_mod cdrom sg ata_generic pata_acpi 8139too pata_atiixp sata_sil 8139cp mii libata ehci_hcd ohci_hcd scsi_mod dock usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Nov  6 15:53:46 home-laptop kernel: [62243.214222] Pid: 0, comm: swapper Tainted: P        W 2.6.27-7-generic #1
Nov  6 15:53:46 home-laptop kernel: [62243.214230]  [<c037c406>] ? printk+0x1d/0x1f
Nov  6 15:53:46 home-laptop kernel: [62243.214247]  [<c0131de9>] warn_on_slowpath+0x59/0x90
Nov  6 15:53:46 home-laptop kernel: [62243.214275]  [<c0214ba8>] ? cap_socket_sock_rcv_skb+0x8/0x10
Nov  6 15:53:46 home-laptop kernel: [62243.214291]  [<c02feb65>] ? sk_filter+0x85/0xc0
Nov  6 15:53:46 home-laptop kernel: [62243.214305]  [<c0335148>] ? tcp_v4_rcv+0x508/0x6f0
Nov  6 15:53:46 home-laptop kernel: [62243.214316]  [<c037dfae>] ? account_scheduler_latency+0xe/0x220
Nov  6 15:53:46 home-laptop kernel: [62243.214327]  [<c025151a>] ? rb_insert_color+0xca/0x100
Nov  6 15:53:46 home-laptop kernel: [62243.214339]  [<c02dfe98>] ? acpi_pm_read+0x8/0x20
Nov  6 15:53:46 home-laptop kernel: [62243.214351]  [<c014e63b>] ? getnstimeofday+0x4b/0x100
Nov  6 15:53:46 home-laptop kernel: [62243.214364]  [<c0136976>] ? set_normalized_timespec+0x16/0x90
Nov  6 15:53:46 home-laptop kernel: [62243.214387]  [<f8a919af>] lbm_cw___lbm_cw_ieee80211_rx+0x19f/0x600 [lbm_cw_mac80211]
Nov  6 15:53:46 home-laptop kernel: [62243.214420]  [<c02eae1c>] ? skb_put+0xc/0xa0
Nov  6 15:53:46 home-laptop kernel: [62243.214431]  [<c014d255>] ? sched_clock_cpu+0xd5/0x170
Nov  6 15:53:46 home-laptop kernel: [62243.214451]  [<f8abdc83>] ath5k_tasklet_rx+0x2e3/0x550 [ath5k]
Nov  6 15:53:46 home-laptop kernel: [62243.214469]  [<c014e63b>] ? getnstimeofday+0x4b/0x100
Nov  6 15:53:46 home-laptop kernel: [62243.214481]  [<c0137258>] tasklet_action+0x78/0x100
Nov  6 15:53:46 home-laptop kernel: [62243.214491]  [<c0137682>] __do_softirq+0x92/0x120
Nov  6 15:53:46 home-laptop kernel: [62243.214500]  [<c013776d>] do_softirq+0x5d/0x60
Nov  6 15:53:46 home-laptop kernel: [62243.214508]  [<c01378e5>] irq_exit+0x55/0x90
Nov  6 15:53:46 home-laptop kernel: [62243.214516]  [<c0106c1a>] do_IRQ+0x4a/0x80
Nov  6 15:53:46 home-laptop kernel: [62243.214526]  [<c013791c>] ? irq_exit+0x8c/0x90
Nov  6 15:53:46 home-laptop kernel: [62243.214535]  [<c0113f8d>] ? smp_apic_timer_interrupt+0x5d/0x90
Nov  6 15:53:46 home-laptop kernel: [62243.214548]  [<c0105003>] common_interrupt+0x23/0x30
Nov  6 15:53:46 home-laptop kernel: [62243.214558]  [<c011aba5>] ? native_safe_halt+0x5/0x10
Nov  6 15:53:46 home-laptop kernel: [62243.214585]  [<f8859ab4>] acpi_safe_halt+0x2f/0x47 [processor]
Nov  6 15:53:46 home-laptop kernel: [62243.214609]  [<f885a501>] acpi_idle_do_entry+0x21/0x30 [processor]
Nov  6 15:53:46 home-laptop kernel: [62243.214632]  [<f885a577>] acpi_idle_enter_c1+0x67/0x88 [processor]
Nov  6 15:53:46 home-laptop kernel: [62243.214654]  [<f885a65f>] acpi_idle_enter_bm+0xc7/0x2b7 [processor]
Nov  6 15:53:46 home-laptop kernel: [62243.214673]  [<c02dbf7b>] cpuidle_idle_call+0x7b/0xd0
Nov  6 15:53:46 home-laptop kernel: [62243.214682]  [<c010288d>] cpu_idle+0x7d/0x140
Nov  6 15:53:46 home-laptop kernel: [62243.214690]  [<c036edd3>] rest_init+0x53/0x60
Nov  6 15:53:46 home-laptop kernel: [62243.214702]  =======================
Nov  6 15:53:46 home-laptop kernel: [62243.214707] ---[ end trace bc8f8f120a6b0be2 ]---


---

### Post by pmsumner on 2008-11-06
It looks like a process was running in the background without telling me - WoW.exe.  Must have been running since I quit the game last night and messing things up.  I found and killed it and the errors stopped...

---

