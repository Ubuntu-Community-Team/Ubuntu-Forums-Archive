---
title: "AMD driver reports an error and freezes everything"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by -JP- on 2011-06-01
Hi,
I've been running 10.04 LTS (64bit) without problems. After I lost the root pw I decided to go for an 11.04 fresh install.

At first everything seemed to work ok. But now when I logon I get the music and then the screen freezes (with standard purple background, I never get a desktop).
After some time it flickers to black and then purple background again. All keys are locked eg no CTRL+ALT+(anything)

From the syslog I could recover this:
May 31 21:50:35 HP-EliteBook-8530p wpa_supplicant[750]: WPA: Group rekeying completed with 00:1c:10:ab:81:6b [GTK=CCMP]
May 31 21:50:35 HP-EliteBook-8530p NetworkManager[621]: <info> (wlan0): supplicant connection state:  completed -> group handshake
May 31 21:50:35 HP-EliteBook-8530p NetworkManager[621]: <info> (wlan0): supplicant connection state:  group handshake -> completed
May 31 21:51:42 HP-EliteBook-8530p NetworkManager[621]: <info> (wlan0): roamed from BSSID 00:1C:10:AB:81:6B (HomeNet) to 00:1C:10:AB:81:6B (HomeNet)
May 31 21:59:12 HP-EliteBook-8530p NetworkManager[621]: <info> (wlan0): roamed from BSSID 00:1C:10:AB:81:6B (HomeNet) to 00:1C:10:AB:81:6B (HomeNet)
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.690298] radeon 0000:01:00.0: GPU lockup CP stall for more than 10000msec
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694515] ------------[ cut here ]------------
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694564] WARNING: at /build/buildd/linux-2.6.38/drivers/gpu/drm/radeon/radeon_fence.c:248 radeon_fence_wait+0x36f/0x3e0 [radeon]()
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694572] Hardware name: HP EliteBook 8530p
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694576] GPU lockup (waiting for 0x0000025F last fence id 0x0000025E)
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694581] Modules linked in: cryptd aes_x86_64 aes_generic snd_hda_codec_hdmi snd_hda_codec_analog tpm_infineon pata_pcmcia binfmt_misc arc4 snd_hda_intel radeon snd_hda_codec iwlagn snd_hwdep rfcomm iwlcore ttm snd_pcm snd_seq_midi mac80211 snd_rawmidi drm_kms_helper sco uvcvideo bnep ppdev l2cap snd_seq_midi_event joydev r852 pcmcia drm sm_common cfg80211 snd_seq hp_wmi sparse_keymap videodev v4l2_compat_ioctl32 snd_timer snd_seq_device btusb tpm_tis psmouse tpm yenta_socket tpm_bios nand bluetooth nand_ids nand_ecc parport_pc pcmcia_rsrc mtd serio_raw pcmcia_core snd video i2c_algo_bit soundcore hp_accel lis3lv02d snd_page_alloc input_polldev lp parport ahci libahci firewire_ohci sdhci_pci sdhci firewire_core crc_itu_t e1000e
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694722] Pid: 1500, comm: compiz Tainted: G        W   2.6.38-8-generic #42-Ubuntu
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694727] Call Trace:
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694742]  [<ffffffff81065cef>] ? warn_slowpath_common+0x7f/0xc0
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694751]  [<ffffffff81065de6>] ? warn_slowpath_fmt+0x46/0x50
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694788]  [<ffffffffa04446df>] ? radeon_fence_wait+0x36f/0x3e0 [radeon]
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694799]  [<ffffffff81087f30>] ? autoremove_wake_function+0x0/0x40
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694835]  [<ffffffffa0444fc1>] ? radeon_sync_obj_wait+0x11/0x20 [radeon]
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694851]  [<ffffffffa0312b0d>] ? ttm_bo_wait+0xfd/0x1b0 [ttm]
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694865]  [<ffffffffa0312e88>] ? ttm_bo_list_ref_sub+0x28/0x30 [ttm]
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694906]  [<ffffffffa045d9e3>] ? radeon_gem_wait_idle_ioctl+0x93/0x110 [radeon]
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694931]  [<ffffffffa00bf384>] ? drm_ioctl+0x3e4/0x4c0 [drm]
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694941]  [<ffffffff81131d4d>] ? handle_mm_fault+0x16d/0x250
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694982]  [<ffffffffa045d950>] ? radeon_gem_wait_idle_ioctl+0x0/0x110 [radeon]
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.694993]  [<ffffffff815c6af8>] ? do_page_fault+0x258/0x540
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.695003]  [<ffffffff8117648f>] ? do_vfs_ioctl+0x8f/0x360
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.695012]  [<ffffffff811767f1>] ? sys_ioctl+0x91/0xa0
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.695021]  [<ffffffff8100c002>] ? system_call_fastpath+0x16/0x1b
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.695027] ---[ end trace 31d0451382567011 ]---
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.695045] [drm] Disabling audio support
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.695135] HDMI hot plug event: Pin=3 Presence_Detect=0 ELD_Valid=0
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.696571] radeon 0000:01:00.0: GPU softreset 
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.696577] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0xE57024E0
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.696583] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00110303
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.696589] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.696602] radeon 0000:01:00.0:   R_008020_GRBM_SOFT_RESET=0x00007FEE
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.711614] radeon 0000:01:00.0: R_008020_GRBM_SOFT_RESET=0x00000001
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.727620] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0xA0003030
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.727626] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000003
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.727632] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200080C0
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.728639] radeon 0000:01:00.0: GPU reset succeed
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.748746] radeon 0000:01:00.0: WB enabled
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.780116] [drm] ring test succeeded in 1 usecs
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.780123] [drm] ib test succeeded in 1 usecs
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.780125] [drm] Enabling audio support
May 31 21:59:26 HP-EliteBook-8530p kernel: [  727.780153] HDMI hot plug event: Pin=3 Presence_Detect=0 ELD_Valid=0

I hope this make sence to someone?
laptop is a HP elitebook8530p
lspci reports:
 sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.2 IDE interface: Intel Corporation Mobile 4 Series Chipset PT IDER Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
03:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
86:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 06)
86:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 25)
86:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 14)
86:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 14)
86:09.4 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev bb)

---

### Post by LowSky on 2011-06-02
looks like you graphics driver is messed up.. try uninstalling the driver from safe mode and then reinstalling it.

---

### Post by -JP- on 2011-06-02
I installed the Catalyst drivers and that solved the problem. logs during boot/shut are no longer clean but at least it works. Strange though. Thnx for the hint

---

