---
title: "Ethernet stopped working after upgrade to 23.4"
date: 2023-08-16
forum: Networking &amp; Wireless
---

### Post by ahmed-hanafi-data on 2023-08-16
hello,
it is my first time reporting a pug hope it is the last
I have similar problem
my network work fine at startup keep working for hours then disconnect and cannot reconnect without a restart
I tested the cable using another pc and it was working repluged with no difference
I use systemd-networkd


**uname -a**
```
Linux ahmed-OptiPlex-3090 6.2.0-27-generic #28-Ubuntu SMP PREEMPT_DYNAMIC Wed Jul 12 22:39:51 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
```


lspci:
```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 1b)
```


dmesg:```
[Mon Aug  7 12:36:47 2023] audit: type=1400 audit(1691401007.881:150): apparmor="ALLOWED" operation="file_perm" class="file" profile="libreoffice-oosplash" name="/tmp/OSL_PIPE_1000_SingleOfficeIPC_74ed987bff2950ad36eaf76d6640d9dc" pid=14414 comm="oosplash" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
[Mon Aug  7 12:39:19 2023] ------------[ cut here ]------------
[Mon Aug  7 12:39:19 2023] NETDEV WATCHDOG: enp2s0 (r8169): transmit queue 0 timed out
[Mon Aug  7 12:39:19 2023] WARNING: CPU: 4 PID: 0 at net/sched/sch_generic.c:525 dev_watchdog+0x23a/0x250
[Mon Aug  7 12:39:19 2023] Modules linked in: snd_seq_dummy snd_hrtimer nvidia_uvm(PO) bridge stp llc cfg80211 binfmt_misc nvidia_drm(PO) nls_iso8859_1 snd_ctl_led nvidia_modeset(PO) snd_sof_pci_intel_cnl snd_sof_intel_hda_common soundwire_intel soundwire_generic_allocation soundwire_cadence snd_sof_intel_hda snd_sof_pci snd_hda_codec_realtek snd_sof_xtensa_dsp snd_hda_codec_generic snd_sof snd_sof_utils snd_soc_hdac_hda snd_hda_ext_core snd_soc_acpi_intel_match snd_soc_acpi soundwire_bus snd_soc_core snd_hda_codec_hdmi snd_compress ac97_bus snd_pcm_dmaengine snd_hda_intel snd_intel_dspcfg snd_intel_sdw_acpi snd_hda_codec intel_rapl_msr intel_rapl_common snd_hda_core intel_tcc_cooling x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp nvidia(PO) snd_pcm kvm_intel snd_seq_midi i915 snd_seq_midi_event mei_hdcp mei_pxp snd_rawmidi kvm drm_buddy snd_seq ttm irqbypass drm_display_helper snd_seq_device crct10dif_pclmul cec polyval_clmulni snd_timer polyval_generic dell_wmi ghash_clmulni_intel rc_core
[Mon Aug  7 12:39:19 2023]  sha512_ssse3 cmdlinepart aesni_intel drm_kms_helper snd mei_me spi_nor crypto_simd i2c_algo_bit dell_smbios cryptd soundcore dcdbas syscopyarea sysfillrect ledtrig_audio dell_wmi_sysman sysimgblt mei rapl mtd sparse_keymap dell_wmi_descriptor intel_pch_thermal intel_cstate wmi_bmof firmware_attributes_class ee1004 input_leds acpi_pad mac_hid msr parport_pc ppdev lp drm parport efi_pstore dmi_sysfs ip_tables x_tables autofs4 hid_generic usbhid hid ahci crc32_pclmul r8169 video intel_lpss_pci spi_intel_pci i2c_i801 libahci xhci_pci spi_intel intel_lpss realtek i2c_smbus xhci_pci_renesas idma64 wmi pinctrl_cannonlake
[Mon Aug  7 12:39:19 2023] CPU: 4 PID: 0 Comm: swapper/4 Tainted: P           O       6.2.0-26-generic #26-Ubuntu
[Mon Aug  7 12:39:19 2023] Hardware name: Dell Inc. OptiPlex 3090/0492YX, BIOS 2.13.1 05/10/2023
[Mon Aug  7 12:39:19 2023] RIP: 0010:dev_watchdog+0x23a/0x250
[Mon Aug  7 12:39:19 2023] Code: 00 e9 2b ff ff ff 48 89 df c6 05 ba a6 d5 01 01 e8 3b 07 f8 ff 44 89 f1 48 89 de 48 c7 c7 f8 25 67 9d 48 89 c2 e8 06 09 29 ff <0f> 0b e9 1c ff ff ff 66 66 2e 0f 1f 84 00 00 00 00 00 0f 1f 40 00
[Mon Aug  7 12:39:19 2023] RSP: 0018:ffffb40c40254e38 EFLAGS: 00010246
[Mon Aug  7 12:39:19 2023] RAX: 0000000000000000 RBX: ffff997996868000 RCX: 0000000000000000
[Mon Aug  7 12:39:19 2023] RDX: 0000000000000000 RSI: 0000000000000000 RDI: 0000000000000000
[Mon Aug  7 12:39:19 2023] RBP: ffffb40c40254e68 R08: 0000000000000000 R09: 0000000000000000
[Mon Aug  7 12:39:19 2023] R10: 0000000000000000 R11: 0000000000000000 R12: ffff9979968684c8
[Mon Aug  7 12:39:19 2023] R13: ffff99799686841c R14: 0000000000000000 R15: 0000000000000000
[Mon Aug  7 12:39:19 2023] FS:  0000000000000000(0000) GS:ffff997da9300000(0000) knlGS:0000000000000000
[Mon Aug  7 12:39:19 2023] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[Mon Aug  7 12:39:19 2023] CR2: 00000c4c01aa8000 CR3: 0000000329810004 CR4: 00000000003726e0
[Mon Aug  7 12:39:19 2023] Call Trace:
[Mon Aug  7 12:39:19 2023]  <IRQ>
[Mon Aug  7 12:39:19 2023]  ? __pfx_dev_watchdog+0x10/0x10
[Mon Aug  7 12:39:19 2023]  call_timer_fn+0x29/0x160
[Mon Aug  7 12:39:19 2023]  ? __pfx_dev_watchdog+0x10/0x10
[Mon Aug  7 12:39:19 2023]  __run_timers+0x259/0x310
[Mon Aug  7 12:39:19 2023]  run_timer_softirq+0x1d/0x40
[Mon Aug  7 12:39:19 2023]  __do_softirq+0xd6/0x346
[Mon Aug  7 12:39:19 2023]  ? hrtimer_interrupt+0x11f/0x250
[Mon Aug  7 12:39:19 2023]  __irq_exit_rcu+0xa2/0xd0
[Mon Aug  7 12:39:19 2023]  irq_exit_rcu+0xe/0x20
[Mon Aug  7 12:39:19 2023]  sysvec_apic_timer_interrupt+0x92/0xd0
[Mon Aug  7 12:39:19 2023]  </IRQ>
[Mon Aug  7 12:39:19 2023]  <TASK>
[Mon Aug  7 12:39:19 2023]  asm_sysvec_apic_timer_interrupt+0x1b/0x20
[Mon Aug  7 12:39:19 2023] RIP: 0010:cpuidle_enter_state+0xde/0x6f0
[Mon Aug  7 12:39:19 2023] Code: 7e 6e 63 e8 c4 57 42 ff 8b 53 04 49 89 c7 0f 1f 44 00 00 31 ff e8 a2 3f 41 ff 80 7d d0 00 0f 85 eb 00 00 00 fb 0f 1f 44 00 00 <45> 85 f6 0f 88 12 02 00 00 4d 63 ee 49 83 fd 09 0f 87 c7 04 00 00
[Mon Aug  7 12:39:19 2023] RSP: 0018:ffffb40c40147e28 EFLAGS: 00000246
[Mon Aug  7 12:39:19 2023] RAX: 0000000000000000 RBX: ffffd40c3fb00200 RCX: 0000000000000000
[Mon Aug  7 12:39:19 2023] RDX: 0000000000000004 RSI: 0000000000000000 RDI: 0000000000000000
[Mon Aug  7 12:39:19 2023] RBP: ffffb40c40147e78 R08: 0000000000000000 R09: 0000000000000000
[Mon Aug  7 12:39:19 2023] R10: 0000000000000000 R11: 0000000000000000 R12: ffffffff9e6c31a0
[Mon Aug  7 12:39:19 2023] R13: 0000000000000003 R14: 0000000000000003 R15: 00000a2b379e6fd3
[Mon Aug  7 12:39:19 2023]  ? cpuidle_enter_state+0xce/0x6f0
[Mon Aug  7 12:39:19 2023]  ? tick_nohz_stop_tick+0x13a/0x210
[Mon Aug  7 12:39:19 2023]  cpuidle_enter+0x2e/0x50
[Mon Aug  7 12:39:19 2023]  cpuidle_idle_call+0x153/0x1e0
[Mon Aug  7 12:39:19 2023]  do_idle+0x82/0x100
[Mon Aug  7 12:39:19 2023]  cpu_startup_entry+0x1d/0x20
[Mon Aug  7 12:39:19 2023]  start_secondary+0x122/0x160
[Mon Aug  7 12:39:19 2023]  secondary_startup_64_no_verify+0xe5/0xeb
[Mon Aug  7 12:39:19 2023]  </TASK>
[Mon Aug  7 12:39:19 2023] ---[ end trace 0000000000000000 ]---
[Mon Aug  7 12:39:19 2023] r8169 0000:02:00.0 enp2s0: rtl_chipcmd_cond == 1 (loop: 100, delay: 100).
[Mon Aug  7 12:39:19 2023] r8169 0000:02:00.0 enp2s0: rtl_ephyar_cond == 1 (loop: 100, delay: 10).
[Mon Aug  7 12:39:19 2023] r8169 0000:02:00.0 enp2s0: rtl_ephyar_cond == 1 (loop: 100, delay: 10).
[Mon Aug  7 12:39:19 2023] r8169 0000:02:00.0 enp2s0: rtl_ephyar_cond == 1 (loop: 100, delay: 10).
[Mon Aug  7 12:39:19 2023] r8169 0000:02:00.0 enp2s0: rtl_ephyar_cond == 1 (loop: 100, delay: 10).
[Mon Aug  7 12:39:19 2023] r8169 0000:02:00.0 enp2s0: rtl_ephyar_cond == 1 (loop: 100, delay: 10).
[Mon Aug  7 12:39:19 2023] r8169 0000:02:00.0 enp2s0: rtl_ephyar_cond == 1 (loop: 100, delay: 10).
[Mon Aug  7 12:39:19 2023] r8169 0000:02:00.0 enp2s0: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[Mon Aug  7 12:39:19 2023] r8169 0000:02:00.0 enp2s0: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[Mon Aug  7 12:39:19 2023] r8169 0000:02:00.0 enp2s0: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[Mon Aug  7 12:40:02 2023] net_ratelimit: 9 callbacks suppressed
[Mon Aug  7 12:40:02 2023] r8169 0000:02:00.0 enp2s0: rtl_chipcmd_cond == 1 (loop: 100, delay: 100).
```

---

### Post by slickymaster on 2023-08-16
Moved to a thread of its own.

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

