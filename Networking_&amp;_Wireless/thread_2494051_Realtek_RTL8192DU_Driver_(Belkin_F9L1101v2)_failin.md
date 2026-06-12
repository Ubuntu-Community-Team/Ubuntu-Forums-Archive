---
title: "Realtek RTL8192DU Driver (Belkin F9L1101v2) failing at Ubuntu 22.04"
date: 2024-01-03
forum: Networking &amp; Wireless
---

### Post by darklord-dr on 2024-01-03
I've been using git lwfinger 8192du driver for a long time under Ubuntu 20.04 requiring frequent rebuilds of driver at kernel updates.  It no longer functions following install of 22.04 (Ubuntu 22.04.3 LTS), kernel 6.2.0-1018-lowlatency.  The build complains:

[FONT=monospace][COLOR=#000000]warning: the compiler differs from the one used to build the kernel [/COLOR]
  The kernel was built by: x86_64-linux-gnu-gcc-11 (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0 
  You are using:           gcc-11 (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0
[/FONT]
But I interpret that as a non-issue."Wireless-info" produced the attached tar.

"lsusb" returns: 
Bus 003 Device 004: ID 050d:110a Belkin Components F9L1101v2 802.11abgn Wireless Adapter [Realtek RTL8192DU]
Bus 003 Device 005: ID 07d1:3c04 D-Link System WUA-134* (my fallback)*

Any help in getting this working, or in troubleshooting will be greatly appreciated.  I'm a mainframe SYSPROG but only a "user" of Ubuntu/Linux (though eager to learn).

Thanking all in advance for your time/effort.

-Dale

---

### Post by darklord-dr on 2024-01-03
Addtional detail...
sudo dmesg | egrep -i '8192du|wifi|80211|Foxnet|WUA-1340|_u_n_S|phy|xe6S'

[   16.269107] cfg80211: Loading compiled-in X.509 certificates for regulatory database
[   16.269800] cfg80211: Loaded X.509 cert 'sforshee: (redacted)'
[   16.912460] 8192du: loading out-of-tree module taints kernel.
[   16.913842] 8192du: module verification failed: signature and/or required key missing - tainting kernel
[   17.002291] RTL8192DU: module init start
[   17.002295] RTL8192DU: rtl8192du v4.0.10_25039.20171107
[   17.231001] RTL8192DU: rtw_ndev_init(\xb4u\x0en\xe6S)
[   17.231252] usbcore: registered new interface driver rtl8192du
[   17.231254] RTL8192DU: module init ret=0
[   17.233861] rtl8192du 3-5.1:1.0 _u_n_S: renamed from \xb4u\x0en\xe6S
[   18.087564] ieee80211 phy1: rt2x00_set_chip: Info - Chipset detected - rt: 2573, rf: 0002, rev: 000a
[   18.088211] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
[   36.668927] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt73.bin'
[   36.948200] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 1.7
[   64.789122] Modules linked in: binfmt_misc snd_hda_codec_via snd_hda_codec_generic snd_hda_codec_hdmi ledtrig_audio snd_hda_intel snd_intel_dspcfg rt73usb snd_usb_audio rt2x00usb snd_intel_sdw_acpi rt2x00lib gspca_zc3xx snd_hda_codec mac80211 snd_usbmidi_lib gspca_main 8192du(OE) snd_hda_core snd_hwdep videobuf2_vmalloc snd_seq_midi videobuf2_memops videobuf2_v4l2 snd_seq_midi_event cfg80211 snd_rawmidi libarc4 videodev edac_mce_amd videobuf2_common snd_seq snd_pcm mc kvm_amd ccp snd_seq_device joydev kvm input_leds snd_timer snd irqbypass soundcore k10temp fam15h_power serio_raw wmi_bmof mac_hid sch_fq_codel cuse msr parport_pc ppdev lp parport efi_pstore ip_tables x_tables autofs4 btrfs blake2b_generic xor raid6_pq libcrc32c dm_mirror dm_region_hash dm_log amdgpu iommu_v2 drm_buddy gpu_sched hid_plantronics uas usb_storage radeon i2c_algo_bit drm_ttm_helper ttm drm_display_helper cec hid_generic crct10dif_pclmul crc32_pclmul rc_core polyval_clmulni polyval_generic ghash_clmulni_intel
[ 5206.571235] ieee80211 phy1: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced reset
[ 5379.670377] ieee80211 phy1: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced reset
[ 5730.977927] ieee80211 phy1: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced reset
[ 5963.217195] ieee80211 phy1: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced reset
[ 7748.302308] ieee80211 phy1: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced reset

---

