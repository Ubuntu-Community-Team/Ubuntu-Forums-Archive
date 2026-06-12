---
title: "not able to find available wifi with pci card ax210 6E"
date: 2022-02-18
forum: Networking &amp; Wireless
---

### Post by ocmjunior on 2022-02-18
Hello,

When i install ubuntu 21.10 with a kernel that should support intel based chip ax210 (fenvi) i am not able to see any wifi connection available.

i tried download driver iwlwifi-ty-a0-gf-a0-59.ucode and copy to /lib/firmware but no success

---

### Post by chili555 on 2022-02-19
Please run and post the result of these terminal commands:

```
uname -r
sudo dmesg | grep iwl

```
Thanks.

---

### Post by ocmjunior on 2022-02-20
this is the results:

```
junior@ubuntuDesktop:~$ uname -r
5.13.0-19-generic
junior@ubuntuDesktop:~$ sudo dmesg | grep iwl
[    2.024602] iwlwifi 0000:05:00.0: api flags index 2 larger than supported by driver
[    2.024626] iwlwifi 0000:05:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 0.0.2.25
[    2.025017] iwlwifi 0000:05:00.0: loaded firmware version 63.c04f3485.0 ty-a0-gf-a0-63.ucode op_mode iwlmvm
[    2.068469] iwlwifi 0000:05:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420
[    2.232326] iwlwifi 0000:05:00.0: loaded PNVM version 0xd35929d8
[    2.315493] iwlwifi 0000:05:00.0: base HW address: 84:14:4d:06:04:0f
[    2.332930] iwlwifi 0000:05:00.0 wlp5s0: renamed from wlan0
[   10.097589] iwlwifi 0000:05:00.0: Microcode SW error detected. Restarting 0x0.
[   10.126389] WARNING: CPU: 15 PID: 595 at drivers/net/wireless/intel/iwlwifi/pcie/trans.c:2028 __iwl_trans_pcie_grab_nic_access.part.0+0x18e/0x1c0 [iwlwifi]
[   10.126414] Modules linked in: hid_logitech_hidpp joydev input_leds hid_logitech_dj snd_usb_audio snd_usbmidi_lib rtl8xxxu hid_generic mc usbhid hid intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp coretemp snd_hda_codec_realtek kvm_intel snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi iwlmvm radeon snd_hda_intel snd_intel_dspcfg kvm snd_intel_sdw_acpi snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul snd_hwdep ghash_clmulni_intel drm_ttm_helper aesni_intel ttm snd_pcm libarc4 crypto_simd cryptd drm_kms_helper snd_seq_midi snd_seq_midi_event cec snd_rawmidi rapl iwlwifi rc_core i2c_algo_bit fb_sys_fops syscopyarea mxm_wmi sysfillrect intel_cstate serio_raw snd_seq sysimgblt snd_seq_device cfg80211 snd_timer snd soundcore sch_fq_codel msr mac_hid parport_pc ppdev lp parport drm ip_tables x_tables autofs4 gpio_ich crc32_pclmul ahci psmouse libahci nvme r8169 i2c_i801 i2c_smbus xhci_pci lpc_ich realtek nvme_core xhci_pci_renesas wmi
[   10.126457] CPU: 15 PID: 595 Comm: irq/68-iwlwifi: Not tainted 5.13.0-19-generic #19-Ubuntu
[   10.126460] RIP: 0010:__iwl_trans_pcie_grab_nic_access.part.0+0x18e/0x1c0 [iwlwifi]
[   10.126487]  iwl_trans_pcie_grab_nic_access+0x47/0x70 [iwlwifi]
[   10.126498]  iwl_trans_pcie_read_mem+0x45/0xf0 [iwlwifi]
[   10.126509]  iwl_mvm_dump_lmac_error_log+0xf3/0x550 [iwlmvm]
[   10.126524]  iwl_mvm_dump_nic_error_log+0x2a/0x190 [iwlmvm]
[   10.126533]  iwl_mvm_nic_error+0x37/0x40 [iwlmvm]
[   10.126541]  iwl_pcie_irq_handle_error+0xb3/0x120 [iwlwifi]
[   10.126551]  iwl_pcie_irq_msix_handler+0x196/0x520 [iwlwifi]
[   10.126586] iwlwifi 0000:05:00.0: iwlwifi transaction failed, dumping registers
[   10.126589] iwlwifi 0000:05:00.0: iwlwifi device config registers:
[   10.126747] iwlwifi 0000:05:00.0: 00000000: 27258086 00100406 0280001a 00000010 fbc00004 00000000 00000000 00000000
[   10.126749] iwlwifi 0000:05:00.0: 00000020: 00000000 00000000 00000000 00248086 00000000 000000c8 00000000 00000103
[   10.126751] iwlwifi 0000:05:00.0: 00000040: 00028010 10008ec0 00190c00 0045e812 10120042 00000000 00000000 00000000
[   10.126753] iwlwifi 0000:05:00.0: 00000060: 00000000 00080812 00000000 00000006 00000002 00000000 00000000 00000000
[   10.126754] iwlwifi 0000:05:00.0: 00000080: 800f0011 00002000 00003000 00000000 00000000 00000000 00000000 00000000
[   10.126756] iwlwifi 0000:05:00.0: 000000a0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   10.126758] iwlwifi 0000:05:00.0: 000000c0: 00000000 00000000 c823d001 0d000008 00804005 00000000 00000000 00000000
[   10.126759] iwlwifi 0000:05:00.0: 000000e0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   10.126761] iwlwifi 0000:05:00.0: 00000100: 14c10001 00000000 00000000 00462031 00000000 00000000 00000014 04000001
[   10.126762] iwlwifi 0000:05:00.0: 00000120: 0000000f 05070000 00000000 00000000 00000000 00000000 00000000 00000000
[   10.126764] iwlwifi 0000:05:00.0: 00000140: 14c00000 ff000000 000000ff 15410018 00000000 0001001e 00481e1f 00000000
[   10.126765] iwlwifi 0000:05:00.0: iwlwifi device memory mapped registers:
[   10.126798] iwlwifi 0000:05:00.0: 00000000: 18c89002 00000040 00000000 00000000 00000000 00000000 00000000 00000000
[   10.126800] iwlwifi 0000:05:00.0: 00000020: 00000010 0c04000c 00000420 d55555d5 d55555d5 d55555d5 80008040 041f0042
[   10.126809] iwlwifi 0000:05:00.0: iwlwifi device AER capability structure:
[   10.126833] iwlwifi 0000:05:00.0: 00000000: 14c10001 00000000 00000000 00462031 00000000 00000000 00000014 04000001
[   10.126834] iwlwifi 0000:05:00.0: 00000020: 0000000f 05070000 00000000
[   10.126835] iwlwifi 0000:05:00.0: iwlwifi parent port (0000:00:1c.2) config registers:
[   10.126930] iwlwifi 0000:00:1c.2: 00000000: 8c148086 00100407 060400d5 00810010 00000000 00000000 00050500 200000f0
[   10.126931] iwlwifi 0000:00:1c.2: 00000020: fbc0fbc0 0001fff1 00000000 00000000 00000000 00000040 00000000 00120303
[   10.126933] iwlwifi 0000:00:1c.2: 00000040: 01428010 00008000 00100000 03313c12 70120042 0014b200 00400000 00000008
[   10.126934] iwlwifi 0000:00:1c.2: 00000060: 00000000 00000817 00000000 00000000 00000002 00000000 00000000 00000000
[   10.126936] iwlwifi 0000:00:1c.2: 00000080: 00019005 fee002f8 00000000 00000000 0000a00d 72708086 00000000 00000000
[   10.126937] iwlwifi 0000:00:1c.2: 000000a0: c8030001 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   10.126939] iwlwifi 0000:00:1c.2: 000000c0: 00000000 00000000 00000000 00000000 01000000 00001842 09918008 00000000
[   10.126940] iwlwifi 0000:00:1c.2: 000000e0: 00000300 00000000 00000001 00000000 00000050 0c000040 08060fb1 03000000
[   10.126942] iwlwifi 0000:00:1c.2: 00000100: 00000000 00000000 00000000 00060011 00000000 00002000 00000000 00000000
[   10.126944] iwlwifi 0000:00:1c.2: 00000120: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   10.126945] iwlwifi 0000:00:1c.2: 00000140: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   10.126946] iwlwifi 0000:00:1c.2: 00000160: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   10.126948] iwlwifi 0000:00:1c.2: 00000180: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   10.126949] iwlwifi 0000:00:1c.2: 000001a0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   10.126951] iwlwifi 0000:00:1c.2: 000001c0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   10.126952] iwlwifi 0000:00:1c.2: 000001e0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   10.126954] iwlwifi 0000:00:1c.2: 00000200: 00000000 00000000 00000000
[   10.126981] WARNING: CPU: 15 PID: 595 at drivers/net/wireless/intel/iwlwifi/mvm/../iwl-trans.h:1335 iwl_mvm_dump_lmac_error_log+0x4f7/0x550 [iwlmvm]
[   10.126991] Modules linked in: hid_logitech_hidpp joydev input_leds hid_logitech_dj snd_usb_audio snd_usbmidi_lib rtl8xxxu hid_generic mc usbhid hid intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp coretemp snd_hda_codec_realtek kvm_intel snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi iwlmvm radeon snd_hda_intel snd_intel_dspcfg kvm snd_intel_sdw_acpi snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul snd_hwdep ghash_clmulni_intel drm_ttm_helper aesni_intel ttm snd_pcm libarc4 crypto_simd cryptd drm_kms_helper snd_seq_midi snd_seq_midi_event cec snd_rawmidi rapl iwlwifi rc_core i2c_algo_bit fb_sys_fops syscopyarea mxm_wmi sysfillrect intel_cstate serio_raw snd_seq sysimgblt snd_seq_device cfg80211 snd_timer snd soundcore sch_fq_codel msr mac_hid parport_pc ppdev lp parport drm ip_tables x_tables autofs4 gpio_ich crc32_pclmul ahci psmouse libahci nvme r8169 i2c_i801 i2c_smbus xhci_pci lpc_ich realtek nvme_core xhci_pci_renesas wmi
[   10.127027] CPU: 15 PID: 595 Comm: irq/68-iwlwifi: Tainted: G        W         5.13.0-19-generic #19-Ubuntu
[   10.127029] RIP: 0010:iwl_mvm_dump_lmac_error_log+0x4f7/0x550 [iwlmvm]
[   10.127051]  iwl_mvm_dump_nic_error_log+0x2a/0x190 [iwlmvm]
[   10.127060]  iwl_mvm_nic_error+0x37/0x40 [iwlmvm]
[   10.127069]  iwl_pcie_irq_handle_error+0xb3/0x120 [iwlwifi]
[   10.127080]  iwl_pcie_irq_msix_handler+0x196/0x520 [iwlwifi]
[   10.127110] iwlwifi 0000:05:00.0: HW error, resetting before reading
[   10.133386] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[   10.133390] iwlwifi 0000:05:00.0: Status: 0x00000040, count: -1125693205
[   10.133392] iwlwifi 0000:05:00.0: Loaded firmware version: 63.c04f3485.0 ty-a0-gf-a0-63.ucode
[   10.133394] iwlwifi 0000:05:00.0: 0xC5E6C678 | ADVANCED_SYSASSERT          
[   10.133396] iwlwifi 0000:05:00.0: 0xC95D07A7 | trm_hw_status0
[   10.133398] iwlwifi 0000:05:00.0: 0xA4696F28 | trm_hw_status1
[   10.133399] iwlwifi 0000:05:00.0: 0x0DE7DAC0 | branchlink2
[   10.133400] iwlwifi 0000:05:00.0: 0x9FCE97AC | interruptlink1
[   10.133402] iwlwifi 0000:05:00.0: 0x1CE850E0 | interruptlink2
[   10.133403] iwlwifi 0000:05:00.0: 0x0558BEC3 | data1
[   10.133404] iwlwifi 0000:05:00.0: 0x44BF9F88 | data2
[   10.133405] iwlwifi 0000:05:00.0: 0x3F8C9210 | data3
[   10.133407] iwlwifi 0000:05:00.0: 0x47EF12FD | beacon time
[   10.133408] iwlwifi 0000:05:00.0: 0x2F238258 | tsf low
[   10.133409] iwlwifi 0000:05:00.0: 0xF993F4C3 | tsf hi
[   10.133410] iwlwifi 0000:05:00.0: 0xB300C8C1 | time gp1
[   10.133412] iwlwifi 0000:05:00.0: 0x8AA46DD0 | time gp2
[   10.133413] iwlwifi 0000:05:00.0: 0xC225B609 | uCode revision type
[   10.133414] iwlwifi 0000:05:00.0: 0x5C3FCAFF | uCode version major
[   10.133416] iwlwifi 0000:05:00.0: 0x2A40D205 | uCode version minor
[   10.133417] iwlwifi 0000:05:00.0: 0xBC3357F0 | hw version
[   10.133418] iwlwifi 0000:05:00.0: 0xE0C0910C | board version
[   10.133419] iwlwifi 0000:05:00.0: 0xC3AAE0E5 | hcmd
[   10.133421] iwlwifi 0000:05:00.0: 0x72029FC9 | isr0
[   10.133422] iwlwifi 0000:05:00.0: 0xFA73D872 | isr1
[   10.133423] iwlwifi 0000:05:00.0: 0x1733AE80 | isr2
[   10.133424] iwlwifi 0000:05:00.0: 0xB3AD5135 | isr3
[   10.133426] iwlwifi 0000:05:00.0: 0x791EF739 | isr4
[   10.133427] iwlwifi 0000:05:00.0: 0xDF636299 | last cmd Id
[   10.133428] iwlwifi 0000:05:00.0: 0xD4FEC960 | wait_event
[   10.133429] iwlwifi 0000:05:00.0: 0x2FEBA33B | l2p_control
[   10.133430] iwlwifi 0000:05:00.0: 0x2DFB6C65 | l2p_duration
[   10.133432] iwlwifi 0000:05:00.0: 0xB48B6E0C | l2p_mhvalid
[   10.133433] iwlwifi 0000:05:00.0: 0x58AD5B57 | l2p_addr_match
[   10.133434] iwlwifi 0000:05:00.0: 0xE3130AF7 | lmpm_pmg_sel
[   10.133436] iwlwifi 0000:05:00.0: 0x9ADA4B2F | timestamp
[   10.133437] iwlwifi 0000:05:00.0: 0xB285994B | flow_handler
[   10.133477] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[   10.133478] iwlwifi 0000:05:00.0: Status: 0x00000040, count: -405821045
[   10.133480] iwlwifi 0000:05:00.0: 0xD95E498A | ADVANCED_SYSASSERT
[   10.133482] iwlwifi 0000:05:00.0: 0xF4397864 | umac branchlink1
[   10.133483] iwlwifi 0000:05:00.0: 0x9B86B41B | umac branchlink2
[   10.133484] iwlwifi 0000:05:00.0: 0x1BA6F857 | umac interruptlink1
[   10.133485] iwlwifi 0000:05:00.0: 0xA8FD9197 | umac interruptlink2
[   10.133487] iwlwifi 0000:05:00.0: 0xA87D7296 | umac data1
[   10.133488] iwlwifi 0000:05:00.0: 0x7487F415 | umac data2
[   10.133489] iwlwifi 0000:05:00.0: 0x3222F718 | umac data3
[   10.133490] iwlwifi 0000:05:00.0: 0x55366BC5 | umac major
[   10.133491] iwlwifi 0000:05:00.0: 0xF87F48BD | umac minor
[   10.133493] iwlwifi 0000:05:00.0: 0xF9CFA976 | frame pointer
[   10.133494] iwlwifi 0000:05:00.0: 0xC276D76D | stack pointer
[   10.133495] iwlwifi 0000:05:00.0: 0x7AE44EEB | last host cmd
[   10.133496] iwlwifi 0000:05:00.0: 0xAA6C76C4 | isr status reg
[   10.133514] iwlwifi 0000:05:00.0: IML/ROM dump:
[   10.133515] iwlwifi 0000:05:00.0: 0x00000000 | IML/ROM error/state
[   10.133533] iwlwifi 0000:05:00.0: 0x00000000 | IML/ROM data1
[   10.133543] iwlwifi 0000:05:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[   10.133550] iwlwifi 0000:05:00.0: Fseq Registers:
[   10.133561] iwlwifi 0000:05:00.0: 0x60000100 | FSEQ_ERROR_CODE
[   10.133572] iwlwifi 0000:05:00.0: 0x80440003 | FSEQ_TOP_INIT_VERSION
[   10.133585] iwlwifi 0000:05:00.0: 0x00080009 | FSEQ_CNVIO_INIT_VERSION
[   10.133598] iwlwifi 0000:05:00.0: 0x0000A652 | FSEQ_OTP_VERSION
[   10.133610] iwlwifi 0000:05:00.0: 0x00000002 | FSEQ_TOP_CONTENT_VERSION
[   10.133623] iwlwifi 0000:05:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN
[   10.133635] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVI_ID
[   10.133648] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVR_ID
[   10.133660] iwlwifi 0000:05:00.0: 0x00400410 | CNVI_AUX_MISC_CHIP
[   10.133674] iwlwifi 0000:05:00.0: 0x00400410 | CNVR_AUX_MISC_CHIP
[   10.133689] iwlwifi 0000:05:00.0: 0x00009061 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[   10.133704] iwlwifi 0000:05:00.0: 0x00000061 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[   10.133861] iwlwifi 0000:05:00.0: WRT: Collecting data: ini trigger 4 fired (delay=0ms).
[   10.133875] iwlwifi 0000:05:00.0: FW error in SYNC CMD MAC_CONTEXT_CMD
[   10.133895]  iwl_trans_txq_send_hcmd_sync+0x345/0x350 [iwlwifi]
[   10.133917]  iwl_trans_txq_send_hcmd+0xaa/0x140 [iwlwifi]
[   10.133937]  iwl_trans_send_cmd+0x98/0xf0 [iwlwifi]
[   10.133949]  iwl_mvm_send_cmd_pdu+0x5c/0xa0 [iwlmvm]
[   10.133961]  iwl_mvm_mac_ctxt_cmd_p2p_device+0xbc/0x110 [iwlmvm]
[   10.133971]  iwl_mvm_mac_ctx_send+0x21/0x70 [iwlmvm]
[   10.133980]  iwl_mvm_mac_ctxt_add+0x3e/0xd0 [iwlmvm]
[   10.133989]  iwl_mvm_mac_add_interface+0x127/0x350 [iwlmvm]
[   10.134264] iwlwifi 0000:05:00.0: Failed to send MAC context (action:1): -5
[   10.954523] iwlwifi 0000:05:00.0: Failed to send recovery cmd blob was invalid 1
[   11.000705] iwlwifi 0000:05:00.0: Microcode SW error detected. Restarting 0x0.
[   11.029534] WARNING: CPU: 15 PID: 595 at drivers/net/wireless/intel/iwlwifi/mvm/../iwl-trans.h:1335 iwl_mvm_dump_lmac_error_log+0x4f7/0x550 [iwlmvm]
[   11.029553] Modules linked in: hid_logitech_hidpp joydev input_leds hid_logitech_dj snd_usb_audio snd_usbmidi_lib rtl8xxxu hid_generic mc usbhid hid intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp coretemp snd_hda_codec_realtek kvm_intel snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi iwlmvm radeon snd_hda_intel snd_intel_dspcfg kvm snd_intel_sdw_acpi snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul snd_hwdep ghash_clmulni_intel drm_ttm_helper aesni_intel ttm snd_pcm libarc4 crypto_simd cryptd drm_kms_helper snd_seq_midi snd_seq_midi_event cec snd_rawmidi rapl iwlwifi rc_core i2c_algo_bit fb_sys_fops syscopyarea mxm_wmi sysfillrect intel_cstate serio_raw snd_seq sysimgblt snd_seq_device cfg80211 snd_timer snd soundcore sch_fq_codel msr mac_hid parport_pc ppdev lp parport drm ip_tables x_tables autofs4 gpio_ich crc32_pclmul ahci psmouse libahci nvme r8169 i2c_i801 i2c_smbus xhci_pci lpc_ich realtek nvme_core xhci_pci_renesas wmi
[   11.029598] CPU: 15 PID: 595 Comm: irq/68-iwlwifi: Tainted: G        W         5.13.0-19-generic #19-Ubuntu
[   11.029601] RIP: 0010:iwl_mvm_dump_lmac_error_log+0x4f7/0x550 [iwlmvm]
[   11.029625]  iwl_mvm_dump_nic_error_log+0x2a/0x190 [iwlmvm]
[   11.029635]  iwl_mvm_nic_error+0x37/0x40 [iwlmvm]
[   11.029643]  iwl_pcie_irq_handle_error+0xb3/0x120 [iwlwifi]
[   11.029660]  iwl_pcie_irq_msix_handler+0x196/0x520 [iwlwifi]
[   11.029695] iwlwifi 0000:05:00.0: HW error, resetting before reading
[   11.035952] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[   11.035955] iwlwifi 0000:05:00.0: Status: 0x00000040, count: -1394130709
[   11.035957] iwlwifi 0000:05:00.0: Loaded firmware version: 63.c04f3485.0 ty-a0-gf-a0-63.ucode
[   11.035959] iwlwifi 0000:05:00.0: 0xCDC6C66A | ADVANCED_SYSASSERT          
[   11.035960] iwlwifi 0000:05:00.0: 0xCB5D07A7 | trm_hw_status0
[   11.035962] iwlwifi 0000:05:00.0: 0xA4616F68 | trm_hw_status1
[   11.035963] iwlwifi 0000:05:00.0: 0x0C67DAC0 | branchlink2
[   11.035964] iwlwifi 0000:05:00.0: 0xDEE697AE | interruptlink1
[   11.035965] iwlwifi 0000:05:00.0: 0x1CE840C0 | interruptlink2
[   11.035966] iwlwifi 0000:05:00.0: 0x05DCBF82 | data1
[   11.035967] iwlwifi 0000:05:00.0: 0x54BF5FA0 | data2
[   11.035968] iwlwifi 0000:05:00.0: 0x3F9C9290 | data3
[   11.035970] iwlwifi 0000:05:00.0: 0x4DEFD2FD | beacon time
[   11.035971] iwlwifi 0000:05:00.0: 0x0F2B8259 | tsf low
[   11.035972] iwlwifi 0000:05:00.0: 0xFA93D4CB | tsf hi
[   11.035973] iwlwifi 0000:05:00.0: 0xF309C8C1 | time gp1
[   11.035974] iwlwifi 0000:05:00.0: 0x8AA56F90 | time gp2
[   11.035975] iwlwifi 0000:05:00.0: 0xC225A609 | uCode revision type
[   11.035976] iwlwifi 0000:05:00.0: 0x5C3BC2FF | uCode version major
[   11.035977] iwlwifi 0000:05:00.0: 0x0A409201 | uCode version minor
[   11.035979] iwlwifi 0000:05:00.0: 0xBEB117F8 | hw version
[   11.035980] iwlwifi 0000:05:00.0: 0x64C29109 | board version
[   11.035981] iwlwifi 0000:05:00.0: 0xC3AAE2C5 | hcmd
[   11.035982] iwlwifi 0000:05:00.0: 0x7082BFC9 | isr0
[   11.035983] iwlwifi 0000:05:00.0: 0xFA73D8F6 | isr1
[   11.035984] iwlwifi 0000:05:00.0: 0x3733AE80 | isr2
[   11.035985] iwlwifi 0000:05:00.0: 0x7BAD5125 | isr3
[   11.035986] iwlwifi 0000:05:00.0: 0xD91EF7B8 | isr4
[   11.035987] iwlwifi 0000:05:00.0: 0xDE736219 | last cmd Id
[   11.035988] iwlwifi 0000:05:00.0: 0xC4FEC363 | wait_event
[   11.035989] iwlwifi 0000:05:00.0: 0xAFEBA37B | l2p_control
[   11.035991] iwlwifi 0000:05:00.0: 0x2D7B6C65 | l2p_duration
[   11.035992] iwlwifi 0000:05:00.0: 0xB48B6E0C | l2p_mhvalid
[   11.035993] iwlwifi 0000:05:00.0: 0x58AD5BD7 | l2p_addr_match
[   11.035994] iwlwifi 0000:05:00.0: 0x63114AF7 | lmpm_pmg_sel
[   11.035995] iwlwifi 0000:05:00.0: 0x98DA1B27 | timestamp
[   11.035996] iwlwifi 0000:05:00.0: 0xB0C5995B | flow_handler
[   11.036036] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[   11.036037] iwlwifi 0000:05:00.0: Status: 0x00000040, count: -472929909
[   11.036038] iwlwifi 0000:05:00.0: 0xD84C4D8A | ADVANCED_SYSASSERT
[   11.036040] iwlwifi 0000:05:00.0: 0xF4287074 | umac branchlink1
[   11.036041] iwlwifi 0000:05:00.0: 0xBB84B05B | umac branchlink2
[   11.036042] iwlwifi 0000:05:00.0: 0x9B66F857 | umac interruptlink1
[   11.036043] iwlwifi 0000:05:00.0: 0xAA7D9597 | umac interruptlink2
[   11.036044] iwlwifi 0000:05:00.0: 0x89757296 | umac data1
[   11.036045] iwlwifi 0000:05:00.0: 0x6487E415 | umac data2
[   11.036046] iwlwifi 0000:05:00.0: 0x32827718 | umac data3
[   11.036047] iwlwifi 0000:05:00.0: 0x51346BC5 | umac major
[   11.036049] iwlwifi 0000:05:00.0: 0xF87B49BD | umac minor
[   11.036050] iwlwifi 0000:05:00.0: 0xF9C7A176 | frame pointer
[   11.036051] iwlwifi 0000:05:00.0: 0xC272D74D | stack pointer
[   11.036052] iwlwifi 0000:05:00.0: 0x7AE44EEB | last host cmd
[   11.036053] iwlwifi 0000:05:00.0: 0xAAAC76C6 | isr status reg
[   11.036070] iwlwifi 0000:05:00.0: IML/ROM dump:
[   11.036072] iwlwifi 0000:05:00.0: 0x00000000 | IML/ROM error/state
[   11.036085] iwlwifi 0000:05:00.0: 0x00000000 | IML/ROM data1
[   11.036095] iwlwifi 0000:05:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[   11.036101] iwlwifi 0000:05:00.0: Fseq Registers:
[   11.036119] iwlwifi 0000:05:00.0: 0x60000100 | FSEQ_ERROR_CODE
[   11.036130] iwlwifi 0000:05:00.0: 0x80440003 | FSEQ_TOP_INIT_VERSION
[   11.036137] iwlwifi 0000:05:00.0: 0x00080009 | FSEQ_CNVIO_INIT_VERSION
[   11.036148] iwlwifi 0000:05:00.0: 0x0000A652 | FSEQ_OTP_VERSION
[   11.036159] iwlwifi 0000:05:00.0: 0x00000002 | FSEQ_TOP_CONTENT_VERSION
[   11.036166] iwlwifi 0000:05:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN
[   11.036172] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVI_ID
[   11.036178] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVR_ID
[   11.036185] iwlwifi 0000:05:00.0: 0x00400410 | CNVI_AUX_MISC_CHIP
[   11.036191] iwlwifi 0000:05:00.0: 0x00400410 | CNVR_AUX_MISC_CHIP
[   11.036197] iwlwifi 0000:05:00.0: 0x00009061 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[   11.036211] iwlwifi 0000:05:00.0: 0x00000061 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[   11.036353] iwlwifi 0000:05:00.0: WRT: Collecting data: ini trigger 4 fired (delay=0ms).
[   11.036388] iwlwifi 0000:05:00.0: FW error in SYNC CMD SCAN_REQ_UMAC
[   11.036410]  iwl_trans_txq_send_hcmd_sync+0x345/0x350 [iwlwifi]
[   11.036433]  iwl_trans_txq_send_hcmd+0xaa/0x140 [iwlwifi]
[   11.036449]  iwl_trans_send_cmd+0x66/0xf0 [iwlwifi]
[   11.036463]  iwl_mvm_send_cmd+0x1f/0x60 [iwlmvm]
[   11.036477]  iwl_mvm_reg_scan_start+0x2af/0x3a0 [iwlmvm]
[   11.036495]  iwl_mvm_mac_hw_scan+0x50/0x70 [iwlmvm]
[   11.036835] iwlwifi 0000:05:00.0: Scan failed! ret -5
[   11.036941] Modules linked in: hid_logitech_hidpp joydev input_leds hid_logitech_dj snd_usb_audio snd_usbmidi_lib rtl8xxxu hid_generic mc usbhid hid intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp coretemp snd_hda_codec_realtek kvm_intel snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi iwlmvm radeon snd_hda_intel snd_intel_dspcfg kvm snd_intel_sdw_acpi snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul snd_hwdep ghash_clmulni_intel drm_ttm_helper aesni_intel ttm snd_pcm libarc4 crypto_simd cryptd drm_kms_helper snd_seq_midi snd_seq_midi_event cec snd_rawmidi rapl iwlwifi rc_core i2c_algo_bit fb_sys_fops syscopyarea mxm_wmi sysfillrect intel_cstate serio_raw snd_seq sysimgblt snd_seq_device cfg80211 snd_timer snd soundcore sch_fq_codel msr mac_hid parport_pc ppdev lp parport drm ip_tables x_tables autofs4 gpio_ich crc32_pclmul ahci psmouse libahci nvme r8169 i2c_i801 i2c_smbus xhci_pci lpc_ich realtek nvme_core xhci_pci_renesas wmi
[   11.867421] iwlwifi 0000:05:00.0: Failed to send recovery cmd blob was invalid 1
```

---

### Post by chili555 on 2022-02-20
Please try:

```
cd /usr/lib/firmware
sudo mv iwlwifi-ty-a0-gf-a0-63.ucode  iwlwifi-ty-a0-gf-a0-63.bak
sudo mv iwlwifi-ty-a0-gf-a0.pnvm   iwlwifi-ty-a0-gf-a0.bak
```Reboot and show us:

```
sudo dmesg | grep iwl
```

Reference: [https://askubuntu.com/questions/1390071/is-there-any-permanent-fix-for-no-wifi-with-iwlwifi-other-than-removing-the-pnv](https://askubuntu.com/questions/1390071/is-there-any-permanent-fix-for-no-wifi-with-iwlwifi-other-than-removing-the-pnv)

---

### Post by ocmjunior on 2022-02-20
the result after reboot:

```
junior@ubuntuDesktop:~$ sudo dmesg | grep iwl
[sudo] password for junior: 
[    2.049024] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-ty-a0-gf-a0-63.ucode failed with error -2
[    2.051702] iwlwifi 0000:05:00.0: api flags index 2 larger than supported by driver
[    2.051721] iwlwifi 0000:05:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 0.59.2.22
[    2.052065] iwlwifi 0000:05:00.0: loaded firmware version 62.49eeb572.0 ty-a0-gf-a0-62.ucode op_mode iwlmvm
[    2.108652] iwlwifi 0000:05:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420
[    2.272729] iwlwifi 0000:05:00.0: Microcode SW error detected. Restarting 0x0.
[    2.272820] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    2.272822] iwlwifi 0000:05:00.0: Status: 0x00000040, count: 6
[    2.272825] iwlwifi 0000:05:00.0: Loaded firmware version: 62.49eeb572.0 ty-a0-gf-a0-62.ucode
[    2.272827] iwlwifi 0000:05:00.0: 0x00000071 | NMI_INTERRUPT_UMAC_FATAL    
[    2.272829] iwlwifi 0000:05:00.0: 0x002002F1 | trm_hw_status0
[    2.272831] iwlwifi 0000:05:00.0: 0x00000000 | trm_hw_status1
[    2.272833] iwlwifi 0000:05:00.0: 0x004DA02C | branchlink2
[    2.272835] iwlwifi 0000:05:00.0: 0x004D070E | interruptlink1
[    2.272837] iwlwifi 0000:05:00.0: 0x004D070E | interruptlink2
[    2.272838] iwlwifi 0000:05:00.0: 0x004D8E06 | data1
[    2.272840] iwlwifi 0000:05:00.0: 0x00000010 | data2
[    2.272854] iwlwifi 0000:05:00.0: 0x00000000 | data3
[    2.272855] iwlwifi 0000:05:00.0: 0x00000000 | beacon time
[    2.272857] iwlwifi 0000:05:00.0: 0x000122EC | tsf low
[    2.272859] iwlwifi 0000:05:00.0: 0x00000000 | tsf hi
[    2.272860] iwlwifi 0000:05:00.0: 0x00000000 | time gp1
[    2.272862] iwlwifi 0000:05:00.0: 0x0002634C | time gp2
[    2.272864] iwlwifi 0000:05:00.0: 0x00000001 | uCode revision type
[    2.272866] iwlwifi 0000:05:00.0: 0x0000003E | uCode version major
[    2.272868] iwlwifi 0000:05:00.0: 0x49EEB572 | uCode version minor
[    2.272870] iwlwifi 0000:05:00.0: 0x00000420 | hw version
[    2.272872] iwlwifi 0000:05:00.0: 0x18C89002 | board version
[    2.272874] iwlwifi 0000:05:00.0: 0x8008FF00 | hcmd
[    2.272876] iwlwifi 0000:05:00.0: 0x00120000 | isr0
[    2.272877] iwlwifi 0000:05:00.0: 0x60000000 | isr1
[    2.272879] iwlwifi 0000:05:00.0: 0x58F00002 | isr2
[    2.272881] iwlwifi 0000:05:00.0: 0x00C0001C | isr3
[    2.272883] iwlwifi 0000:05:00.0: 0x00000000 | isr4
[    2.272884] iwlwifi 0000:05:00.0: 0x00000000 | last cmd Id
[    2.272886] iwlwifi 0000:05:00.0: 0x004D8E06 | wait_event
[    2.272888] iwlwifi 0000:05:00.0: 0x00000000 | l2p_control
[    2.272890] iwlwifi 0000:05:00.0: 0x00000820 | l2p_duration
[    2.272892] iwlwifi 0000:05:00.0: 0x00000000 | l2p_mhvalid
[    2.272893] iwlwifi 0000:05:00.0: 0x00000000 | l2p_addr_match
[    2.272895] iwlwifi 0000:05:00.0: 0x00000009 | lmpm_pmg_sel
[    2.272897] iwlwifi 0000:05:00.0: 0x00000000 | timestamp
[    2.272899] iwlwifi 0000:05:00.0: 0x00000024 | flow_handler
[    2.272939] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    2.272941] iwlwifi 0000:05:00.0: Status: 0x00000040, count: 7
[    2.272943] iwlwifi 0000:05:00.0: 0x2010070D | ADVANCED_SYSASSERT
[    2.272945] iwlwifi 0000:05:00.0: 0x00000000 | umac branchlink1
[    2.272947] iwlwifi 0000:05:00.0: 0x8045C7E4 | umac branchlink2
[    2.272949] iwlwifi 0000:05:00.0: 0x0108D0B2 | umac interruptlink1
[    2.272951] iwlwifi 0000:05:00.0: 0x00000000 | umac interruptlink2
[    2.272953] iwlwifi 0000:05:00.0: 0x00000005 | umac data1
[    2.272954] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data2
[    2.272956] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data3
[    2.272958] iwlwifi 0000:05:00.0: 0x0000003E | umac major
[    2.272960] iwlwifi 0000:05:00.0: 0x49EEB572 | umac minor
[    2.272961] iwlwifi 0000:05:00.0: 0x00026344 | frame pointer
[    2.272963] iwlwifi 0000:05:00.0: 0xC0885E90 | stack pointer
[    2.272965] iwlwifi 0000:05:00.0: 0x00010C00 | last host cmd
[    2.272967] iwlwifi 0000:05:00.0: 0x00000000 | isr status reg
[    2.272985] iwlwifi 0000:05:00.0: IML/ROM dump:
[    2.272986] iwlwifi 0000:05:00.0: 0x00000B03 | IML/ROM error/state
[    2.273004] iwlwifi 0000:05:00.0: 0x000080DC | IML/ROM data1
[    2.273014] iwlwifi 0000:05:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[    2.273025] iwlwifi 0000:05:00.0: Fseq Registers:
[    2.273036] iwlwifi 0000:05:00.0: 0x60000100 | FSEQ_ERROR_CODE
[    2.273047] iwlwifi 0000:05:00.0: 0x80440003 | FSEQ_TOP_INIT_VERSION
[    2.273058] iwlwifi 0000:05:00.0: 0x00070008 | FSEQ_CNVIO_INIT_VERSION
[    2.273070] iwlwifi 0000:05:00.0: 0x0000A652 | FSEQ_OTP_VERSION
[    2.273081] iwlwifi 0000:05:00.0: 0x00000002 | FSEQ_TOP_CONTENT_VERSION
[    2.273092] iwlwifi 0000:05:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN
[    2.273103] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVI_ID
[    2.273115] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVR_ID
[    2.273126] iwlwifi 0000:05:00.0: 0x00400410 | CNVI_AUX_MISC_CHIP
[    2.273150] iwlwifi 0000:05:00.0: 0x00400410 | CNVR_AUX_MISC_CHIP
[    2.273163] iwlwifi 0000:05:00.0: 0x00009061 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    2.273177] iwlwifi 0000:05:00.0: 0x00000061 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    2.273216] iwlwifi 0000:05:00.0: WRT: Collecting data: ini trigger 13 fired (delay=0ms).
[    3.041969] iwlwifi 0000:05:00.0: Failed to run INIT ucode: -5
[/QUOTE]


/usr/lib/firmware content:


[QUOTE]junior@ubuntuDesktop:~$ cd /usr/lib/firmware
junior@ubuntuDesktop:/usr/lib/firmware$ ls
1a98-INTEL-EDK2-2-tplg.bin   htc_7010.fw              iwlwifi-8000C-31.ucode             iwlwifi-so-a0-hr-b0-64.ucode   rsi_91x.fw
3com                         htc_9271.fw              iwlwifi-8000C-34.ucode             iwlwifi-so-a0-jf-b0-64.ucode   rt2561.bin
a300_pfp.fw                  i2400m-fw-usb-1.4.sbcf   iwlwifi-8000C-36.ucode             iwlwifi-ty-a0-gf-a0-59.ucode   rt2561s.bin
a300_pm4.fw                  i2400m-fw-usb-1.5.sbcf   iwlwifi-8265-21.ucode              iwlwifi-ty-a0-gf-a0-62.ucode   rt2661.bin
acenic                       i6050-fw-usb-1.5.sbcf    iwlwifi-8265-22.ucode              iwlwifi-ty-a0-gf-a0-63.bak     rt2860.bin
adaptec                      i915                     iwlwifi-8265-27.ucode              iwlwifi-ty-a0-gf-a0-66.ucode   rt2870.bin
advansys                     imx                      iwlwifi-8265-31.ucode              iwlwifi-ty-a0-gf-a0.bak        rt3070.bin
agere_ap_fw.bin              inside-secure            iwlwifi-8265-34.ucode              kaweth                         rt3071.bin
agere_sta_fw.bin             intel                    iwlwifi-8265-36.ucode              keyspan                        rt3090.bin
amd                          intel-ucode              iwlwifi-9000-pu-b0-jf-b0-33.ucode  keyspan_pda                    rt3290.bin
amdgpu                       ipw2100-1.3.fw           iwlwifi-9000-pu-b0-jf-b0-34.ucode  korg                           rt73.bin
amd-ucode                    ipw2100-1.3-i.fw         iwlwifi-9000-pu-b0-jf-b0-38.ucode  lbtf_usb.bin                   RTL8192E
ar3k                         ipw2100-1.3-p.fw         iwlwifi-9000-pu-b0-jf-b0-41.ucode  lgs8g75.fw                     rtl_bt
ar5523.bin                   ipw2200-bss.fw           iwlwifi-9000-pu-b0-jf-b0-43.ucode  libertas                       rtl_nic
as102_data1_st.hex           ipw2200-ibss.fw          iwlwifi-9000-pu-b0-jf-b0-46.ucode  liquidio                       rtlwifi
as102_data2_st.hex           ipw2200-sniffer.fw       iwlwifi-9260-th-b0-jf-b0-33.ucode  lt9611uxc_fw.bin               rtw88
asihpi                       isci                     iwlwifi-9260-th-b0-jf-b0-34.ucode  matrox                         rtw89
ath10k                       iwlwifi-1000-5.ucode     iwlwifi-9260-th-b0-jf-b0-38.ucode  mediatek                       s2250.fw
ath11k                       iwlwifi-100-5.ucode      iwlwifi-9260-th-b0-jf-b0-41.ucode  mellanox                       s2250_loader.fw
ath3k-1.fw                   iwlwifi-105-6.ucode      iwlwifi-9260-th-b0-jf-b0-43.ucode  meson                          s5p-mfc.fw
ath6k                        iwlwifi-135-6.ucode      iwlwifi-9260-th-b0-jf-b0-46.ucode  microchip                      s5p-mfc-v6.fw
ath9k_htc                    iwlwifi-2000-6.ucode     iwlwifi-cc-a0-46.ucode             moxa                           s5p-mfc-v6-v2.fw
atmel                        iwlwifi-2030-6.ucode     iwlwifi-cc-a0-48.ucode             mrvl                           s5p-mfc-v7.fw
atmel_at76c504_2958.bin      iwlwifi-3160-10.ucode    iwlwifi-cc-a0-50.ucode             mt7601u.bin                    s5p-mfc-v8.fw
atmel_at76c504a_2958.bin     iwlwifi-3160-12.ucode    iwlwifi-cc-a0-53.ucode             mt7650.bin                     sb16
atmsar11.fw                  iwlwifi-3160-13.ucode    iwlwifi-cc-a0-55.ucode             mt7662.bin                     sdd_sagrad_1091_1098.bin
atusb                        iwlwifi-3160-16.ucode    iwlwifi-cc-a0-59.ucode             mt7662_rom_patch.bin           silabs
av7110                       iwlwifi-3160-17.ucode    iwlwifi-cc-a0-62.ucode             mts_cdma.fw                    skl_hda_dsp_generic-tplg.bin
bnx2                         iwlwifi-3160-7.ucode     iwlwifi-cc-a0-63.ucode             mts_edge.fw                    slicoss
bnx2x                        iwlwifi-3160-8.ucode     iwlwifi-Qu-b0-hr-b0-48.ucode       mts_gsm.fw                     sun
brcm                         iwlwifi-3160-9.ucode     iwlwifi-Qu-b0-hr-b0-50.ucode       mts_mt9234mu.fw                tehuti
cadence                      iwlwifi-3168-21.ucode    iwlwifi-Qu-b0-hr-b0-53.ucode       mts_mt9234zba.fw               ti
carl9170-1.fw                iwlwifi-3168-22.ucode    iwlwifi-Qu-b0-hr-b0-55.ucode       mwl8k                          ti_3410.fw
cavium                       iwlwifi-3168-27.ucode    iwlwifi-Qu-b0-hr-b0-59.ucode       mwlwifi                        ti_5052.fw
cbfw-3.2.1.1.bin             iwlwifi-3168-29.ucode    iwlwifi-Qu-b0-hr-b0-62.ucode       myri10ge_eth_big_z8e.dat       ti-connectivity
cbfw-3.2.3.0.bin             iwlwifi-3945-2.ucode     iwlwifi-Qu-b0-hr-b0-63.ucode       myri10ge_ethp_big_z8e.dat      tigon
cbfw-3.2.5.1.bin             iwlwifi-4965-2.ucode     iwlwifi-Qu-b0-jf-b0-48.ucode       myri10ge_ethp_z8e.dat          ti-keystone
cis                          iwlwifi-5000-5.ucode     iwlwifi-Qu-b0-jf-b0-50.ucode       myri10ge_eth_z8e.dat           tlg2300_firmware.bin
cpia2                        iwlwifi-5150-2.ucode     iwlwifi-Qu-b0-jf-b0-53.ucode       myri10ge_rss_eth_big_z8e.dat   ttusb-budget
ct2fw-3.2.1.1.bin            iwlwifi-6000-4.ucode     iwlwifi-Qu-b0-jf-b0-55.ucode       myri10ge_rss_ethp_big_z8e.dat  ueagle-atm
ct2fw-3.2.3.0.bin            iwlwifi-6000g2a-5.ucode  iwlwifi-Qu-b0-jf-b0-59.ucode       myri10ge_rss_ethp_z8e.dat      usbduxfast_firmware.bin
ct2fw-3.2.5.1.bin            iwlwifi-6000g2a-6.ucode  iwlwifi-Qu-b0-jf-b0-62.ucode       myri10ge_rss_eth_z8e.dat       usbdux_firmware.bin
ctefx.bin                    iwlwifi-6000g2b-6.ucode  iwlwifi-Qu-b0-jf-b0-63.ucode       netronome                      usbduxsigma_firmware.bin
ctfw-3.2.1.1.bin             iwlwifi-6050-5.ucode     iwlwifi-Qu-c0-hr-b0-48.ucode       nvidia                         v4l-cx231xx-avcore-01.fw
ctfw-3.2.3.0.bin             iwlwifi-7260-10.ucode    iwlwifi-Qu-c0-hr-b0-50.ucode       ositech                        v4l-cx23418-apu.fw
ctfw-3.2.5.1.bin             iwlwifi-7260-12.ucode    iwlwifi-Qu-c0-hr-b0-53.ucode       phanfw.bin                     v4l-cx23418-cpu.fw
ctspeq.bin                   iwlwifi-7260-13.ucode    iwlwifi-Qu-c0-hr-b0-55.ucode       qat_895xcc.bin                 v4l-cx23418-dig.fw
cxgb3                        iwlwifi-7260-16.ucode    iwlwifi-Qu-c0-hr-b0-59.ucode       qat_895xcc_mmp.bin             v4l-cx2341x-dec.fw
cxgb4                        iwlwifi-7260-17.ucode    iwlwifi-Qu-c0-hr-b0-62.ucode       qat_c3xxx.bin                  v4l-cx2341x-enc.fw
cypress                      iwlwifi-7260-7.ucode     iwlwifi-Qu-c0-hr-b0-63.ucode       qat_c3xxx_mmp.bin              v4l-cx2341x-init.mpg
dpaa2                        iwlwifi-7260-8.ucode     iwlwifi-Qu-c0-jf-b0-48.ucode       qat_c62x.bin                   v4l-cx23885-avcore-01.fw
dsp56k                       iwlwifi-7260-9.ucode     iwlwifi-Qu-c0-jf-b0-50.ucode       qat_c62x_mmp.bin               v4l-cx25840.fw
dvb-fe-xc4000-1.4.1.fw       iwlwifi-7265-10.ucode    iwlwifi-Qu-c0-jf-b0-53.ucode       qat_mmp.bin                    v4l-pvrusb2-24xxx-01.fw
dvb-fe-xc5000-1.6.114.fw     iwlwifi-7265-12.ucode    iwlwifi-Qu-c0-jf-b0-55.ucode       qca                            v4l-pvrusb2-29xxx-01.fw
dvb-fe-xc5000c-4.1.30.7.fw   iwlwifi-7265-13.ucode    iwlwifi-Qu-c0-jf-b0-59.ucode       qcom                           vicam
dvb-usb-dib0700-1.20.fw      iwlwifi-7265-16.ucode    iwlwifi-Qu-c0-jf-b0-62.ucode       qed                            vntwusb.fw
dvb-usb-it9135-01.fw         iwlwifi-7265-17.ucode    iwlwifi-Qu-c0-jf-b0-63.ucode       ql2100_fw.bin                  vpu_d.bin
dvb-usb-it9135-02.fw         iwlwifi-7265-8.ucode     iwlwifi-QuZ-a0-hr-b0-48.ucode      ql2200_fw.bin                  vpu_p.bin
dvb-usb-terratec-h5-drxk.fw  iwlwifi-7265-9.ucode     iwlwifi-QuZ-a0-hr-b0-50.ucode      ql2300_fw.bin                  vxge
e100                         iwlwifi-7265D-10.ucode   iwlwifi-QuZ-a0-hr-b0-53.ucode      ql2322_fw.bin                  whiteheat.fw
ea                           iwlwifi-7265D-12.ucode   iwlwifi-QuZ-a0-hr-b0-55.ucode      ql2400_fw.bin                  whiteheat_loader.fw
edgeport                     iwlwifi-7265D-13.ucode   iwlwifi-QuZ-a0-hr-b0-59.ucode      ql2500_fw.bin                  wil6210.brd
emi26                        iwlwifi-7265D-16.ucode   iwlwifi-QuZ-a0-hr-b0-62.ucode      qlogic                         wil6210.fw
emi62                        iwlwifi-7265D-17.ucode   iwlwifi-QuZ-a0-hr-b0-63.ucode      r128                           wsm_22.bin
ene-ub6250                   iwlwifi-7265D-21.ucode   iwlwifi-QuZ-a0-jf-b0-48.ucode      r8a779x_usb3_v1.dlmem          yam
ess                          iwlwifi-7265D-22.ucode   iwlwifi-QuZ-a0-jf-b0-50.ucode      r8a779x_usb3_v2.dlmem          yamaha
f2255usb.bin                 iwlwifi-7265D-27.ucode   iwlwifi-QuZ-a0-jf-b0-53.ucode      r8a779x_usb3_v3.dlmem          zd1201-ap.fw
go7007                       iwlwifi-7265D-29.ucode   iwlwifi-QuZ-a0-jf-b0-55.ucode      radeon                         zd1201.fw
hfi1_dc8051.fw               iwlwifi-8000C-13.ucode   iwlwifi-QuZ-a0-jf-b0-59.ucode      regulatory.db                  zd1211
hfi1_fabric.fw               iwlwifi-8000C-16.ucode   iwlwifi-QuZ-a0-jf-b0-62.ucode      regulatory.db.p7s
hfi1_pcie.fw                 iwlwifi-8000C-21.ucode   iwlwifi-QuZ-a0-jf-b0-63.ucode      rockchip
hfi1_sbus.fw                 iwlwifi-8000C-22.ucode   iwlwifi-so-a0-gf-a0-64.ucode       rp2.fw
hp                           iwlwifi-8000C-27.ucode   iwlwifi-so-a0-gf-a0.pnvm           rsi
```

---

### Post by chili555 on 2022-02-20
Please try istalling the 5.16 kernel version as described here: [https://askubuntu.com/questions/1388335/intel-wifi-6-ax210-driver-issue](https://askubuntu.com/questions/1388335/intel-wifi-6-ax210-driver-issue)

---

### Post by ocmjunior on 2022-02-20
unfortunately it is not working when i try update the kernel 

```
root@ubuntuDesktop:/home/junior/Downloads# wget -c [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16/amd64/linux-headers-5.16.0-051600_5.16.0-051600.202201092355_all.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16/amd64/linux-headers-5.16.0-051600_5.16.0-051600.202201092355_all.deb)
--2022-02-20 22:17:00--  [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16/amd64/linux-headers-5.16.0-051600_5.16.0-051600.202201092355_all.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16/amd64/linux-headers-5.16.0-051600_5.16.0-051600.202201092355_all.deb)
Resolving kernel.ubuntu.com (kernel.ubuntu.com)... 91.189.94.216
Connecting to kernel.ubuntu.com (kernel.ubuntu.com)|91.189.94.216|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12286872 (12M) [application/x-debian-package]
Saving to: &#8216;linux-headers-5.16.0-051600_5.16.0-051600.202201092355_all.deb&#8217;

linux-headers-5.16. 100%[===================>]  11,72M  1,30MB/s    in 11s     

2022-02-20 22:17:12 (1,08 MB/s) - &#8216;linux-headers-5.16.0-051600_5.16.0-051600.202201092355_all.deb&#8217; saved [12286872/12286872]

root@ubuntuDesktop:/home/junior/Downloads# wget -c [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16/amd64/linux-headers-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16/amd64/linux-headers-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb)
--2022-02-20 22:17:19--  [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16/amd64/linux-headers-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16/amd64/linux-headers-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb)
Resolving kernel.ubuntu.com (kernel.ubuntu.com)... 91.189.94.216
Connecting to kernel.ubuntu.com (kernel.ubuntu.com)|91.189.94.216|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2934516 (2,8M) [application/x-debian-package]
Saving to: &#8216;linux-headers-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb&#8217;

linux-headers-5.16. 100%[===================>]   2,80M   168KB/s    in 18s     

2022-02-20 22:17:38 (158 KB/s) - &#8216;linux-headers-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb&#8217; saved [2934516/2934516]

root@ubuntuDesktop:/home/junior/Downloads# wget -c [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16/amd64/linux-image-unsigned-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16/amd64/linux-image-unsigned-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb)
--2022-02-20 22:17:41--  [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16/amd64/linux-image-unsigned-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16/amd64/linux-image-unsigned-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb)
Resolving kernel.ubuntu.com (kernel.ubuntu.com)... 91.189.94.216
Connecting to kernel.ubuntu.com (kernel.ubuntu.com)|91.189.94.216|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10332162 (9,9M) [application/x-debian-package]
Saving to: &#8216;linux-image-unsigned-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb&#8217;

linux-image-unsigne 100%[===================>]   9,85M  1,06MB/s    in 30s     

2022-02-20 22:18:12 (340 KB/s) - &#8216;linux-image-unsigned-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb&#8217; saved [10332162/10332162]

root@ubuntuDesktop:/home/junior/Downloads# wget -c [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16/amd64/linux-modules-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16/amd64/linux-modules-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb)
--2022-02-20 22:18:15--  [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16/amd64/linux-modules-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.16/amd64/linux-modules-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb)
Resolving kernel.ubuntu.com (kernel.ubuntu.com)... 91.189.94.216
Connecting to kernel.ubuntu.com (kernel.ubuntu.com)|91.189.94.216|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 80973318 (77M) [application/x-debian-package]
Saving to: &#8216;linux-modules-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb&#8217;

linux-modules-5.16. 100%[===================>]  77,22M   986KB/s    in 2m 28s  

2022-02-20 22:20:44 (534 KB/s) - &#8216;linux-modules-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb&#8217; saved [80973318/80973318]

root@ubuntuDesktop:/home/junior/Downloads# sudo dpkg -i *.deb
Selecting previously unselected package linux-headers-5.16.0-051600.
(Reading database ... 182433 files and directories currently installed.)
Preparing to unpack linux-headers-5.16.0-051600_5.16.0-051600.202201092355_all.deb ...
Unpacking linux-headers-5.16.0-051600 (5.16.0-051600.202201092355) ...
Selecting previously unselected package linux-headers-5.16.0-051600-generic.
Preparing to unpack linux-headers-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb ...
Unpacking linux-headers-5.16.0-051600-generic (5.16.0-051600.202201092355) ...
Selecting previously unselected package linux-image-unsigned-5.16.0-051600-generic.
Preparing to unpack linux-image-unsigned-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb ...
Unpacking linux-image-unsigned-5.16.0-051600-generic (5.16.0-051600.202201092355) ...
Selecting previously unselected package linux-modules-5.16.0-051600-generic.
Preparing to unpack linux-modules-5.16.0-051600-generic_5.16.0-051600.202201092355_amd64.deb ...
Unpacking linux-modules-5.16.0-051600-generic (5.16.0-051600.202201092355) ...
Setting up linux-headers-5.16.0-051600 (5.16.0-051600.202201092355) ...
dpkg: dependency problems prevent configuration of linux-headers-5.16.0-051600-generic:
 linux-headers-5.16.0-051600-generic depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3 is not installed.

dpkg: error processing package linux-headers-5.16.0-051600-generic (--install):
 dependency problems - leaving unconfigured
Setting up linux-image-unsigned-5.16.0-051600-generic (5.16.0-051600.202201092355) ...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-5.13.0-28-generic
I: /boot/initrd.img.old is now a symlink to initrd.img-5.13.0-28-generic
I: /boot/vmlinuz is now a symlink to vmlinuz-5.16.0-051600-generic
I: /boot/initrd.img is now a symlink to initrd.img-5.16.0-051600-generic
Setting up linux-modules-5.16.0-051600-generic (5.16.0-051600.202201092355) ...
Processing triggers for linux-image-unsigned-5.16.0-051600-generic (5.16.0-051600.202201092355) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.16.0-051600-generic
I: The initramfs will attempt to resume from /dev/nvme0n1p2
I: (UUID=8b5bef6d-4832-4a65-b48a-2a5b0e12c803)
I: Set the RESUME variable to override this.
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.16.0-051600-generic
Found initrd image: /boot/initrd.img-5.16.0-051600-generic
Found linux image: /boot/vmlinuz-5.13.0-28-generic
Found initrd image: /boot/initrd.img-5.13.0-28-generic
Found linux image: /boot/vmlinuz-5.13.0-19-generic
Found initrd image: /boot/initrd.img-5.13.0-19-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment on /dev/sda1
Found Linux Mint 20.3 Una (20.3) on /dev/sdb2
done
Errors were encountered while processing:
 linux-headers-5.16.0-051600-generic
root@ubuntuDesktop:/home/junior/Downloads# sudo apt -f install
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  linux-headers-5.16.0-051600-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 25,0 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 217917 files and directories currently installed.)
Removing linux-headers-5.16.0-051600-generic (5.16.0-051600.202201092355) ...

```

---

### Post by chili555 on 2022-02-21
> dpkg: dependency problems prevent configuration of linux-headers-5.16.0-051600-generic:
 linux-headers-5.16.0-051600-generic depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3 is not installed.

Please do: 

```
sudo apt update
sudo apt install libc6 debconf
wget http://mirrors.kernel.org/ubuntu/pool/main/o/openssl/libssl3_3.0.1-0ubuntu1_amd64.deb
sudo dpkg -i libssl3_3.0.1-0ubuntu1_amd64.deb
sudo apt -f install
```

---

### Post by ocmjunior on 2022-02-21
now i was able to update the kernel, but still having problem with the wifi

```
junior@ubuntuDesktop:~$ uname -a
Linux ubuntuDesktop 5.16.0-051600-generic #202201092355 SMP PREEMPT Mon Jan 10 00:21:11 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
junior@ubuntuDesktop:~$ sudo dmesg | grep iwl
[sudo] password for junior: 
[    1.988065] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-ty-a0-gf-a0-67.ucode failed with error -2
[    1.990817] iwlwifi 0000:05:00.0: api flags index 2 larger than supported by driver
[    1.990842] iwlwifi 0000:05:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 0.63.2.1
[    1.991209] iwlwifi 0000:05:00.0: loaded firmware version 66.55c64978.0 ty-a0-gf-a0-66.ucode op_mode iwlmvm
[    2.234638] iwlwifi 0000:05:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420
[    2.241337] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 1, ret=-1
[    2.241340] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 2, ret=-1
[    2.241342] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 3, ret=-1
[    2.400678] iwlwifi 0000:05:00.0: Detected RF GF, rfid=0x10d000
[    2.401671] iwlwifi 0000:05:00.0: Microcode SW error detected. Restarting 0x0.
[    2.401764] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    2.401767] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 6
[    2.401770] iwlwifi 0000:05:00.0: Loaded firmware version: 66.55c64978.0 ty-a0-gf-a0-66.ucode
[    2.401786] iwlwifi 0000:05:00.0: 0x00000071 | NMI_INTERRUPT_UMAC_FATAL    
[    2.401789] iwlwifi 0000:05:00.0: 0x002002F0 | trm_hw_status0
[    2.401791] iwlwifi 0000:05:00.0: 0x00000000 | trm_hw_status1
[    2.401793] iwlwifi 0000:05:00.0: 0x004DA1A2 | branchlink2
[    2.401795] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink1
[    2.401797] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink2
[    2.401799] iwlwifi 0000:05:00.0: 0x004D8F5A | data1
[    2.401801] iwlwifi 0000:05:00.0: 0x00000010 | data2
[    2.401803] iwlwifi 0000:05:00.0: 0x00000000 | data3
[    2.401805] iwlwifi 0000:05:00.0: 0x00000000 | beacon time
[    2.401807] iwlwifi 0000:05:00.0: 0x000128E6 | tsf low
[    2.401809] iwlwifi 0000:05:00.0: 0x00000000 | tsf hi
[    2.401811] iwlwifi 0000:05:00.0: 0x00000000 | time gp1
[    2.401813] iwlwifi 0000:05:00.0: 0x00026756 | time gp2
[    2.401815] iwlwifi 0000:05:00.0: 0x00000001 | uCode revision type
[    2.401817] iwlwifi 0000:05:00.0: 0x00000042 | uCode version major
[    2.401820] iwlwifi 0000:05:00.0: 0x55C64978 | uCode version minor
[    2.401822] iwlwifi 0000:05:00.0: 0x00000420 | hw version
[    2.401824] iwlwifi 0000:05:00.0: 0x18C89002 | board version
[    2.401826] iwlwifi 0000:05:00.0: 0x8008FF05 | hcmd
[    2.401829] iwlwifi 0000:05:00.0: 0x00020000 | isr0
[    2.401831] iwlwifi 0000:05:00.0: 0x60000000 | isr1
[    2.401833] iwlwifi 0000:05:00.0: 0x48F00002 | isr2
[    2.401835] iwlwifi 0000:05:00.0: 0x00C0000C | isr3
[    2.401837] iwlwifi 0000:05:00.0: 0x00000000 | isr4
[    2.401839] iwlwifi 0000:05:00.0: 0x00000000 | last cmd Id
[    2.401841] iwlwifi 0000:05:00.0: 0x004D8F5A | wait_event
[    2.401843] iwlwifi 0000:05:00.0: 0x00000000 | l2p_control
[    2.401845] iwlwifi 0000:05:00.0: 0x00000000 | l2p_duration
[    2.401847] iwlwifi 0000:05:00.0: 0x00000000 | l2p_mhvalid
[    2.401849] iwlwifi 0000:05:00.0: 0x00000000 | l2p_addr_match
[    2.401851] iwlwifi 0000:05:00.0: 0x00000009 | lmpm_pmg_sel
[    2.401853] iwlwifi 0000:05:00.0: 0x00000000 | timestamp
[    2.401855] iwlwifi 0000:05:00.0: 0x00000024 | flow_handler
[    2.401896] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    2.401898] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 7
[    2.401900] iwlwifi 0000:05:00.0: 0x2010070D | ADVANCED_SYSASSERT
[    2.401903] iwlwifi 0000:05:00.0: 0x00000000 | umac branchlink1
[    2.401905] iwlwifi 0000:05:00.0: 0x8045DFC6 | umac branchlink2
[    2.401907] iwlwifi 0000:05:00.0: 0x0109012A | umac interruptlink1
[    2.401910] iwlwifi 0000:05:00.0: 0x00000000 | umac interruptlink2
[    2.401912] iwlwifi 0000:05:00.0: 0x00000005 | umac data1
[    2.401914] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data2
[    2.401916] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data3
[    2.401918] iwlwifi 0000:05:00.0: 0x00000042 | umac major
[    2.401920] iwlwifi 0000:05:00.0: 0x55C64978 | umac minor
[    2.401922] iwlwifi 0000:05:00.0: 0x0002674E | frame pointer
[    2.401924] iwlwifi 0000:05:00.0: 0xC0885E88 | stack pointer
[    2.401926] iwlwifi 0000:05:00.0: 0x00010C00 | last host cmd
[    2.401928] iwlwifi 0000:05:00.0: 0x00000000 | isr status reg
[    2.401947] iwlwifi 0000:05:00.0: IML/ROM dump:
[    2.401949] iwlwifi 0000:05:00.0: 0x00000B03 | IML/ROM error/state
[    2.401966] iwlwifi 0000:05:00.0: 0x00007EA9 | IML/ROM data1
[    2.401981] iwlwifi 0000:05:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[    2.401992] iwlwifi 0000:05:00.0: Fseq Registers:
[    2.402003] iwlwifi 0000:05:00.0: 0x60000000 | FSEQ_ERROR_CODE
[    2.402014] iwlwifi 0000:05:00.0: 0x80440003 | FSEQ_TOP_INIT_VERSION
[    2.402025] iwlwifi 0000:05:00.0: 0x00080009 | FSEQ_CNVIO_INIT_VERSION
[    2.402037] iwlwifi 0000:05:00.0: 0x0000A652 | FSEQ_OTP_VERSION
[    2.402048] iwlwifi 0000:05:00.0: 0x00000002 | FSEQ_TOP_CONTENT_VERSION
[    2.402059] iwlwifi 0000:05:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN
[    2.402070] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVI_ID
[    2.402082] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVR_ID
[    2.402093] iwlwifi 0000:05:00.0: 0x00400410 | CNVI_AUX_MISC_CHIP
[    2.402106] iwlwifi 0000:05:00.0: 0x00400410 | CNVR_AUX_MISC_CHIP
[    2.402119] iwlwifi 0000:05:00.0: 0x00009061 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    2.402133] iwlwifi 0000:05:00.0: 0x00000061 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    2.402175] iwlwifi 0000:05:00.0: WRT: Collecting data: ini trigger 13 fired (delay=0ms).
[    3.210326] iwlwifi 0000:05:00.0: Failed to run INIT ucode: -5
[    3.222712] iwlwifi 0000:05:00.0: retry init count 0
[    3.223004] iwlwifi 0000:05:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420
[    3.229384] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 1, ret=-1
[    3.229386] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 2, ret=-1
[    3.229388] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 3, ret=-1
[    3.388759] iwlwifi 0000:05:00.0: Microcode SW error detected. Restarting 0x0.
[    3.388941] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    3.388958] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 6
[    3.388978] iwlwifi 0000:05:00.0: Loaded firmware version: 66.55c64978.0 ty-a0-gf-a0-66.ucode
[    3.389003] iwlwifi 0000:05:00.0: 0x00000071 | NMI_INTERRUPT_UMAC_FATAL    
[    3.389024] iwlwifi 0000:05:00.0: 0x002002F0 | trm_hw_status0
[    3.389040] iwlwifi 0000:05:00.0: 0x00000000 | trm_hw_status1
[    3.389057] iwlwifi 0000:05:00.0: 0x004DA1A2 | branchlink2
[    3.389073] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink1
[    3.389089] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink2
[    3.389106] iwlwifi 0000:05:00.0: 0x004D8F5A | data1
[    3.389120] iwlwifi 0000:05:00.0: 0x00000010 | data2
[    3.389135] iwlwifi 0000:05:00.0: 0x00000000 | data3
[    3.389149] iwlwifi 0000:05:00.0: 0x00000000 | beacon time
[    3.389165] iwlwifi 0000:05:00.0: 0x000128EA | tsf low
[    3.389181] iwlwifi 0000:05:00.0: 0x00000000 | tsf hi
[    3.389196] iwlwifi 0000:05:00.0: 0x00000000 | time gp1
[    3.389211] iwlwifi 0000:05:00.0: 0x0002675A | time gp2
[    3.389226] iwlwifi 0000:05:00.0: 0x00000001 | uCode revision type
[    3.389244] iwlwifi 0000:05:00.0: 0x00000042 | uCode version major
[    3.389262] iwlwifi 0000:05:00.0: 0x55C64978 | uCode version minor
[    3.389280] iwlwifi 0000:05:00.0: 0x00000420 | hw version
[    3.389296] iwlwifi 0000:05:00.0: 0x18C89002 | board version
[    3.389312] iwlwifi 0000:05:00.0: 0x8008FF05 | hcmd
[    3.389327] iwlwifi 0000:05:00.0: 0x00020000 | isr0
[    3.389341] iwlwifi 0000:05:00.0: 0x60000000 | isr1
[    3.389882] iwlwifi 0000:05:00.0: 0x48F00002 | isr2
[    3.390412] iwlwifi 0000:05:00.0: 0x00C0000C | isr3
[    3.390959] iwlwifi 0000:05:00.0: 0x00000000 | isr4
[    3.391492] iwlwifi 0000:05:00.0: 0x00000000 | last cmd Id
[    3.392006] iwlwifi 0000:05:00.0: 0x004D8F5A | wait_event
[    3.392500] iwlwifi 0000:05:00.0: 0x00000000 | l2p_control
[    3.392993] iwlwifi 0000:05:00.0: 0x00000000 | l2p_duration
[    3.393491] iwlwifi 0000:05:00.0: 0x00000000 | l2p_mhvalid
[    3.394152] iwlwifi 0000:05:00.0: 0x00000000 | l2p_addr_match
[    3.395098] iwlwifi 0000:05:00.0: 0x00000009 | lmpm_pmg_sel
[    3.396030] iwlwifi 0000:05:00.0: 0x00000000 | timestamp
[    3.396859] iwlwifi 0000:05:00.0: 0x00000024 | flow_handler
[    3.397710] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    3.398503] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 7
[    3.399370] iwlwifi 0000:05:00.0: 0x2010070D | ADVANCED_SYSASSERT
[    3.400208] iwlwifi 0000:05:00.0: 0x00000000 | umac branchlink1
[    3.400796] iwlwifi 0000:05:00.0: 0x8045DFC6 | umac branchlink2
[    3.401234] iwlwifi 0000:05:00.0: 0x0109012A | umac interruptlink1
[    3.401655] iwlwifi 0000:05:00.0: 0x00000000 | umac interruptlink2
[    3.402072] iwlwifi 0000:05:00.0: 0x00000005 | umac data1
[    3.402477] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data2
[    3.402947] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data3
[    3.403384] iwlwifi 0000:05:00.0: 0x00000042 | umac major
[    3.403771] iwlwifi 0000:05:00.0: 0x55C64978 | umac minor
[    3.404148] iwlwifi 0000:05:00.0: 0x00026752 | frame pointer
[    3.404521] iwlwifi 0000:05:00.0: 0xC0885E88 | stack pointer
[    3.404889] iwlwifi 0000:05:00.0: 0x00010C00 | last host cmd
[    3.405238] iwlwifi 0000:05:00.0: 0x00000000 | isr status reg
[    3.405596] iwlwifi 0000:05:00.0: IML/ROM dump:
[    3.405933] iwlwifi 0000:05:00.0: 0x00000B03 | IML/ROM error/state
[    3.406282] iwlwifi 0000:05:00.0: 0x00007EA9 | IML/ROM data1
[    3.406646] iwlwifi 0000:05:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[    3.407026] iwlwifi 0000:05:00.0: Fseq Registers:
[    3.407380] iwlwifi 0000:05:00.0: 0x60000000 | FSEQ_ERROR_CODE
[    3.407940] iwlwifi 0000:05:00.0: 0x80440003 | FSEQ_TOP_INIT_VERSION
[    3.408500] iwlwifi 0000:05:00.0: 0x00080009 | FSEQ_CNVIO_INIT_VERSION
[    3.409052] iwlwifi 0000:05:00.0: 0x0000A652 | FSEQ_OTP_VERSION
[    3.409605] iwlwifi 0000:05:00.0: 0x00000002 | FSEQ_TOP_CONTENT_VERSION
[    3.410161] iwlwifi 0000:05:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN
[    3.410759] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVI_ID
[    3.411375] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVR_ID
[    3.411963] iwlwifi 0000:05:00.0: 0x00400410 | CNVI_AUX_MISC_CHIP
[    3.412804] iwlwifi 0000:05:00.0: 0x00400410 | CNVR_AUX_MISC_CHIP
[    3.413373] iwlwifi 0000:05:00.0: 0x00009061 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    3.413957] iwlwifi 0000:05:00.0: 0x00000061 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    3.414428] iwlwifi 0000:05:00.0: WRT: Collecting data: ini trigger 13 fired (delay=0ms).
[    4.226629] iwlwifi 0000:05:00.0: Failed to run INIT ucode: -5
[    4.238604] iwlwifi 0000:05:00.0: retry init count 1
[    4.238963] iwlwifi 0000:05:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420
[    4.245381] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 1, ret=-1
[    4.245383] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 2, ret=-1
[    4.245384] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 3, ret=-1
[    4.404536] iwlwifi 0000:05:00.0: Microcode SW error detected. Restarting 0x0.
[    4.404628] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    4.404630] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 6
[    4.404632] iwlwifi 0000:05:00.0: Loaded firmware version: 66.55c64978.0 ty-a0-gf-a0-66.ucode
[    4.404634] iwlwifi 0000:05:00.0: 0x00000071 | NMI_INTERRUPT_UMAC_FATAL    
[    4.404636] iwlwifi 0000:05:00.0: 0x002002F0 | trm_hw_status0
[    4.404638] iwlwifi 0000:05:00.0: 0x00000000 | trm_hw_status1
[    4.404640] iwlwifi 0000:05:00.0: 0x004DA1A2 | branchlink2
[    4.404641] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink1
[    4.404643] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink2
[    4.404644] iwlwifi 0000:05:00.0: 0x004D8F5A | data1
[    4.404646] iwlwifi 0000:05:00.0: 0x00000010 | data2
[    4.404647] iwlwifi 0000:05:00.0: 0x00000000 | data3
[    4.404649] iwlwifi 0000:05:00.0: 0x00000000 | beacon time
[    4.404650] iwlwifi 0000:05:00.0: 0x000128AC | tsf low
[    4.404651] iwlwifi 0000:05:00.0: 0x00000000 | tsf hi
[    4.404653] iwlwifi 0000:05:00.0: 0x00000000 | time gp1
[    4.404654] iwlwifi 0000:05:00.0: 0x0002671D | time gp2
[    4.404656] iwlwifi 0000:05:00.0: 0x00000001 | uCode revision type
[    4.404657] iwlwifi 0000:05:00.0: 0x00000042 | uCode version major
[    4.404659] iwlwifi 0000:05:00.0: 0x55C64978 | uCode version minor
[    4.404660] iwlwifi 0000:05:00.0: 0x00000420 | hw version
[    4.404662] iwlwifi 0000:05:00.0: 0x18C89002 | board version
[    4.404663] iwlwifi 0000:05:00.0: 0x8008FF05 | hcmd
[    4.404665] iwlwifi 0000:05:00.0: 0x00020000 | isr0
[    4.404666] iwlwifi 0000:05:00.0: 0x60000000 | isr1
[    4.404667] iwlwifi 0000:05:00.0: 0x48F00002 | isr2
[    4.404669] iwlwifi 0000:05:00.0: 0x00C0000C | isr3
[    4.404670] iwlwifi 0000:05:00.0: 0x00000000 | isr4
[    4.404671] iwlwifi 0000:05:00.0: 0x00000000 | last cmd Id
[    4.404673] iwlwifi 0000:05:00.0: 0x004D8F5A | wait_event
[    4.404674] iwlwifi 0000:05:00.0: 0x00000000 | l2p_control
[    4.404676] iwlwifi 0000:05:00.0: 0x00000000 | l2p_duration
[    4.404677] iwlwifi 0000:05:00.0: 0x00000000 | l2p_mhvalid
[    4.404678] iwlwifi 0000:05:00.0: 0x00000000 | l2p_addr_match
[    4.404680] iwlwifi 0000:05:00.0: 0x00000009 | lmpm_pmg_sel
[    4.404681] iwlwifi 0000:05:00.0: 0x00000000 | timestamp
[    4.404683] iwlwifi 0000:05:00.0: 0x00000024 | flow_handler
[    4.404723] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    4.404724] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 7
[    4.404726] iwlwifi 0000:05:00.0: 0x2010070D | ADVANCED_SYSASSERT
[    4.404727] iwlwifi 0000:05:00.0: 0x00000000 | umac branchlink1
[    4.404729] iwlwifi 0000:05:00.0: 0x8045DFC6 | umac branchlink2
[    4.404730] iwlwifi 0000:05:00.0: 0x0109012A | umac interruptlink1
[    4.404732] iwlwifi 0000:05:00.0: 0x00000000 | umac interruptlink2
[    4.404733] iwlwifi 0000:05:00.0: 0x00000005 | umac data1
[    4.404734] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data2
[    4.404736] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data3
[    4.404737] iwlwifi 0000:05:00.0: 0x00000042 | umac major
[    4.404738] iwlwifi 0000:05:00.0: 0x55C64978 | umac minor
[    4.404740] iwlwifi 0000:05:00.0: 0x00026715 | frame pointer
[    4.404741] iwlwifi 0000:05:00.0: 0xC0885E88 | stack pointer
[    4.404742] iwlwifi 0000:05:00.0: 0x00010C00 | last host cmd
[    4.404744] iwlwifi 0000:05:00.0: 0x00000000 | isr status reg
[    4.404761] iwlwifi 0000:05:00.0: IML/ROM dump:
[    4.404763] iwlwifi 0000:05:00.0: 0x00000B03 | IML/ROM error/state
[    4.404780] iwlwifi 0000:05:00.0: 0x00007EAA | IML/ROM data1
[    4.404790] iwlwifi 0000:05:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[    4.404797] iwlwifi 0000:05:00.0: Fseq Registers:
[    4.404803] iwlwifi 0000:05:00.0: 0x60000000 | FSEQ_ERROR_CODE
[    4.404815] iwlwifi 0000:05:00.0: 0x80440003 | FSEQ_TOP_INIT_VERSION
[    4.404826] iwlwifi 0000:05:00.0: 0x00080009 | FSEQ_CNVIO_INIT_VERSION
[    4.404837] iwlwifi 0000:05:00.0: 0x0000A652 | FSEQ_OTP_VERSION
[    4.404848] iwlwifi 0000:05:00.0: 0x00000002 | FSEQ_TOP_CONTENT_VERSION
[    4.404859] iwlwifi 0000:05:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN
[    4.404871] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVI_ID
[    4.404882] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVR_ID
[    4.404893] iwlwifi 0000:05:00.0: 0x00400410 | CNVI_AUX_MISC_CHIP
[    4.404906] iwlwifi 0000:05:00.0: 0x00400410 | CNVR_AUX_MISC_CHIP
[    4.404920] iwlwifi 0000:05:00.0: 0x00009061 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    4.404933] iwlwifi 0000:05:00.0: 0x00000061 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    4.404968] iwlwifi 0000:05:00.0: WRT: Collecting data: ini trigger 13 fired (delay=0ms).
[    5.208099] iwlwifi 0000:05:00.0: Failed to run INIT ucode: -5
[    5.220398] iwlwifi 0000:05:00.0: retry init count 2
```

---

### Post by chili555 on 2022-02-21
Please try:

```
cd /usr/lib/firmware
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/iwlwifi-ty-a0-gf-a0-67.ucode
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/iwlwifi-ty-a0-gf-a0-68.ucode
```Reboot and show us:

```
sudo dmesg | grep iwl
```

---

### Post by ocmjunior on 2022-02-21
done, i am think that maybe kernel is not fully compatible yet

```

junior@ubuntuDesktop:~$ sudo dmesg | grep iwl
[sudo] password for junior: 
[    2.058070] iwlwifi 0000:05:00.0: uCode file size 9866284 does not match expected size
[    2.062526] iwlwifi 0000:05:00.0: api flags index 2 larger than supported by driver
[    2.062555] iwlwifi 0000:05:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 0.63.2.1
[    2.062984] iwlwifi 0000:05:00.0: loaded firmware version 66.55c64978.0 ty-a0-gf-a0-66.ucode op_mode iwlmvm
[    2.162246] iwlwifi 0000:05:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420
[    2.172654] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 1, ret=-1
[    2.172658] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 2, ret=-1
[    2.172661] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 3, ret=-1
[    2.336149] iwlwifi 0000:05:00.0: Detected RF GF, rfid=0x10d000
[    2.337137] iwlwifi 0000:05:00.0: Microcode SW error detected. Restarting 0x0.
[    2.337229] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    2.337232] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 6
[    2.337235] iwlwifi 0000:05:00.0: Loaded firmware version: 66.55c64978.0 ty-a0-gf-a0-66.ucode
[    2.337238] iwlwifi 0000:05:00.0: 0x00000071 | NMI_INTERRUPT_UMAC_FATAL    
[    2.337240] iwlwifi 0000:05:00.0: 0x002002F0 | trm_hw_status0
[    2.337243] iwlwifi 0000:05:00.0: 0x00000000 | trm_hw_status1
[    2.337245] iwlwifi 0000:05:00.0: 0x004DA1A2 | branchlink2
[    2.337247] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink1
[    2.337249] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink2
[    2.337251] iwlwifi 0000:05:00.0: 0x004D8F5A | data1
[    2.337253] iwlwifi 0000:05:00.0: 0x00000010 | data2
[    2.337255] iwlwifi 0000:05:00.0: 0x00000000 | data3
[    2.337268] iwlwifi 0000:05:00.0: 0x00000000 | beacon time
[    2.337270] iwlwifi 0000:05:00.0: 0x000128EC | tsf low
[    2.337272] iwlwifi 0000:05:00.0: 0x00000000 | tsf hi
[    2.337274] iwlwifi 0000:05:00.0: 0x00000000 | time gp1
[    2.337276] iwlwifi 0000:05:00.0: 0x0002675E | time gp2
[    2.337277] iwlwifi 0000:05:00.0: 0x00000001 | uCode revision type
[    2.337279] iwlwifi 0000:05:00.0: 0x00000042 | uCode version major
[    2.337282] iwlwifi 0000:05:00.0: 0x55C64978 | uCode version minor
[    2.337284] iwlwifi 0000:05:00.0: 0x00000420 | hw version
[    2.337286] iwlwifi 0000:05:00.0: 0x18C89002 | board version
[    2.337288] iwlwifi 0000:05:00.0: 0x8008FF05 | hcmd
[    2.337290] iwlwifi 0000:05:00.0: 0x00020000 | isr0
[    2.337292] iwlwifi 0000:05:00.0: 0x60000000 | isr1
[    2.337294] iwlwifi 0000:05:00.0: 0x48F00002 | isr2
[    2.337296] iwlwifi 0000:05:00.0: 0x00C0000C | isr3
[    2.337298] iwlwifi 0000:05:00.0: 0x00000000 | isr4
[    2.337299] iwlwifi 0000:05:00.0: 0x00000000 | last cmd Id
[    2.337301] iwlwifi 0000:05:00.0: 0x004D8F5A | wait_event
[    2.337303] iwlwifi 0000:05:00.0: 0x00000000 | l2p_control
[    2.337305] iwlwifi 0000:05:00.0: 0x00000000 | l2p_duration
[    2.337307] iwlwifi 0000:05:00.0: 0x00000000 | l2p_mhvalid
[    2.337309] iwlwifi 0000:05:00.0: 0x00000000 | l2p_addr_match
[    2.337311] iwlwifi 0000:05:00.0: 0x00000009 | lmpm_pmg_sel
[    2.337313] iwlwifi 0000:05:00.0: 0x00000000 | timestamp
[    2.337315] iwlwifi 0000:05:00.0: 0x00000024 | flow_handler
[    2.337356] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    2.337358] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 7
[    2.337360] iwlwifi 0000:05:00.0: PNVM data is missing, please install iwlwifi-ty-a0-gf-a0.pnvm
[    2.337363] iwlwifi 0000:05:00.0: 0x2010070D | PNVM_MISSING
[    2.337365] iwlwifi 0000:05:00.0: 0x00000000 | umac branchlink1
[    2.337367] iwlwifi 0000:05:00.0: 0x8045DFC6 | umac branchlink2
[    2.337369] iwlwifi 0000:05:00.0: 0x0109012A | umac interruptlink1
[    2.337371] iwlwifi 0000:05:00.0: 0x00000000 | umac interruptlink2
[    2.337373] iwlwifi 0000:05:00.0: 0x00000005 | umac data1
[    2.337375] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data2
[    2.337377] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data3
[    2.337379] iwlwifi 0000:05:00.0: 0x00000042 | umac major
[    2.337381] iwlwifi 0000:05:00.0: 0x55C64978 | umac minor
[    2.337383] iwlwifi 0000:05:00.0: 0x00026756 | frame pointer
[    2.337385] iwlwifi 0000:05:00.0: 0xC0885E88 | stack pointer
[    2.337387] iwlwifi 0000:05:00.0: 0x00010C00 | last host cmd
[    2.337389] iwlwifi 0000:05:00.0: 0x00000000 | isr status reg
[    2.337407] iwlwifi 0000:05:00.0: IML/ROM dump:
[    2.337409] iwlwifi 0000:05:00.0: 0x00000B03 | IML/ROM error/state
[    2.337426] iwlwifi 0000:05:00.0: 0x00007EA9 | IML/ROM data1
[    2.337441] iwlwifi 0000:05:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[    2.337452] iwlwifi 0000:05:00.0: Fseq Registers:
[    2.337463] iwlwifi 0000:05:00.0: 0x60000000 | FSEQ_ERROR_CODE
[    2.337474] iwlwifi 0000:05:00.0: 0x80440003 | FSEQ_TOP_INIT_VERSION
[    2.337485] iwlwifi 0000:05:00.0: 0x00080009 | FSEQ_CNVIO_INIT_VERSION
[    2.337496] iwlwifi 0000:05:00.0: 0x0000A652 | FSEQ_OTP_VERSION
[    2.337508] iwlwifi 0000:05:00.0: 0x00000002 | FSEQ_TOP_CONTENT_VERSION
[    2.337519] iwlwifi 0000:05:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN
[    2.337530] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVI_ID
[    2.337541] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVR_ID
[    2.337552] iwlwifi 0000:05:00.0: 0x00400410 | CNVI_AUX_MISC_CHIP
[    2.337566] iwlwifi 0000:05:00.0: 0x00400410 | CNVR_AUX_MISC_CHIP
[    2.337579] iwlwifi 0000:05:00.0: 0x00009061 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    2.337592] iwlwifi 0000:05:00.0: 0x00000061 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    2.337633] iwlwifi 0000:05:00.0: WRT: Collecting data: ini trigger 13 fired (delay=0ms).
[    3.148589] iwlwifi 0000:05:00.0: Failed to run INIT ucode: -5
[    3.161009] iwlwifi 0000:05:00.0: retry init count 0
[    3.162578] iwlwifi 0000:05:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420
[    3.168886] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 1, ret=-1
[    3.168888] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 2, ret=-1
[    3.168889] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 3, ret=-1
[    3.332845] iwlwifi 0000:05:00.0: Microcode SW error detected. Restarting 0x0.
[    3.333034] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    3.333065] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 6
[    3.333101] iwlwifi 0000:05:00.0: Loaded firmware version: 66.55c64978.0 ty-a0-gf-a0-66.ucode
[    3.333145] iwlwifi 0000:05:00.0: 0x00000071 | NMI_INTERRUPT_UMAC_FATAL    
[    3.333182] iwlwifi 0000:05:00.0: 0x002002F0 | trm_hw_status0
[    3.333212] iwlwifi 0000:05:00.0: 0x00000000 | trm_hw_status1
[    3.333243] iwlwifi 0000:05:00.0: 0x004DA1A2 | branchlink2
[    3.333272] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink1
[    3.333302] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink2
[    3.333332] iwlwifi 0000:05:00.0: 0x004D8F5A | data1
[    3.333359] iwlwifi 0000:05:00.0: 0x00000010 | data2
[    3.333386] iwlwifi 0000:05:00.0: 0x00000000 | data3
[    3.333412] iwlwifi 0000:05:00.0: 0x00000000 | beacon time
[    3.333442] iwlwifi 0000:05:00.0: 0x000136F3 | tsf low
[    3.333469] iwlwifi 0000:05:00.0: 0x00000000 | tsf hi
[    3.333496] iwlwifi 0000:05:00.0: 0x00000000 | time gp1
[    3.333523] iwlwifi 0000:05:00.0: 0x00027565 | time gp2
[    3.333551] iwlwifi 0000:05:00.0: 0x00000001 | uCode revision type
[    3.333583] iwlwifi 0000:05:00.0: 0x00000042 | uCode version major
[    3.333616] iwlwifi 0000:05:00.0: 0x55C64978 | uCode version minor
[    3.333648] iwlwifi 0000:05:00.0: 0x00000420 | hw version
[    3.333677] iwlwifi 0000:05:00.0: 0x18C89002 | board version
[    3.334611] iwlwifi 0000:05:00.0: 0x8008FF05 | hcmd
[    3.335648] iwlwifi 0000:05:00.0: 0x00020000 | isr0
[    3.336633] iwlwifi 0000:05:00.0: 0x60000000 | isr1
[    3.337549] iwlwifi 0000:05:00.0: 0x48F00002 | isr2
[    3.338147] iwlwifi 0000:05:00.0: 0x00C0000C | isr3
[    3.338684] iwlwifi 0000:05:00.0: 0x00000000 | isr4
[    3.339270] iwlwifi 0000:05:00.0: 0x00000000 | last cmd Id
[    3.339838] iwlwifi 0000:05:00.0: 0x004D8F5A | wait_event
[    3.340368] iwlwifi 0000:05:00.0: 0x00000000 | l2p_control
[    3.340898] iwlwifi 0000:05:00.0: 0x00000000 | l2p_duration
[    3.341423] iwlwifi 0000:05:00.0: 0x00000000 | l2p_mhvalid
[    3.341950] iwlwifi 0000:05:00.0: 0x00000000 | l2p_addr_match
[    3.342476] iwlwifi 0000:05:00.0: 0x00000009 | lmpm_pmg_sel
[    3.343030] iwlwifi 0000:05:00.0: 0x00000000 | timestamp
[    3.343573] iwlwifi 0000:05:00.0: 0x00000024 | flow_handler
[    3.344125] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    3.344626] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 7
[    3.345122] iwlwifi 0000:05:00.0: PNVM data is missing, please install iwlwifi-ty-a0-gf-a0.pnvm
[    3.345620] iwlwifi 0000:05:00.0: 0x2010070D | PNVM_MISSING
[    3.346107] iwlwifi 0000:05:00.0: 0x00000000 | umac branchlink1
[    3.346588] iwlwifi 0000:05:00.0: 0x8045DFC6 | umac branchlink2
[    3.347090] iwlwifi 0000:05:00.0: 0x0109012A | umac interruptlink1
[    3.347587] iwlwifi 0000:05:00.0: 0x00000000 | umac interruptlink2
[    3.348050] iwlwifi 0000:05:00.0: 0x00000005 | umac data1
[    3.348763] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data2
[    3.349497] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data3
[    3.350217] iwlwifi 0000:05:00.0: 0x00000042 | umac major
[    3.350940] iwlwifi 0000:05:00.0: 0x55C64978 | umac minor
[    3.351660] iwlwifi 0000:05:00.0: 0x0002755D | frame pointer
[    3.352336] iwlwifi 0000:05:00.0: 0xC0885E88 | stack pointer
[    3.352992] iwlwifi 0000:05:00.0: 0x00010C00 | last host cmd
[    3.353634] iwlwifi 0000:05:00.0: 0x00000000 | isr status reg
[    3.354268] iwlwifi 0000:05:00.0: IML/ROM dump:
[    3.354644] iwlwifi 0000:05:00.0: 0x00000B03 | IML/ROM error/state
[    3.355055] iwlwifi 0000:05:00.0: 0x00007EA9 | IML/ROM data1
[    3.355749] iwlwifi 0000:05:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[    3.356120] iwlwifi 0000:05:00.0: Fseq Registers:
[    3.356478] iwlwifi 0000:05:00.0: 0x60000000 | FSEQ_ERROR_CODE
[    3.356838] iwlwifi 0000:05:00.0: 0x80440003 | FSEQ_TOP_INIT_VERSION
[    3.357204] iwlwifi 0000:05:00.0: 0x00080009 | FSEQ_CNVIO_INIT_VERSION
[    3.357572] iwlwifi 0000:05:00.0: 0x0000A652 | FSEQ_OTP_VERSION
[    3.357940] iwlwifi 0000:05:00.0: 0x00000002 | FSEQ_TOP_CONTENT_VERSION
[    3.358313] iwlwifi 0000:05:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN
[    3.358688] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVI_ID
[    3.359085] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVR_ID
[    3.359481] iwlwifi 0000:05:00.0: 0x00400410 | CNVI_AUX_MISC_CHIP
[    3.359862] iwlwifi 0000:05:00.0: 0x00400410 | CNVR_AUX_MISC_CHIP
[    3.360242] iwlwifi 0000:05:00.0: 0x00009061 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    3.360632] iwlwifi 0000:05:00.0: 0x00000061 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    3.361052] iwlwifi 0000:05:00.0: WRT: Collecting data: ini trigger 13 fired (delay=0ms).
[    4.170893] iwlwifi 0000:05:00.0: Failed to run INIT ucode: -5
[    4.182863] iwlwifi 0000:05:00.0: retry init count 1
[    4.184212] iwlwifi 0000:05:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420
[    4.190545] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 1, ret=-1
[    4.190547] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 2, ret=-1
[    4.190549] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 3, ret=-1
[    4.350965] iwlwifi 0000:05:00.0: Microcode SW error detected. Restarting 0x0.
[    4.351055] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    4.351056] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 6
[    4.351058] iwlwifi 0000:05:00.0: Loaded firmware version: 66.55c64978.0 ty-a0-gf-a0-66.ucode
[    4.351060] iwlwifi 0000:05:00.0: 0x00000071 | NMI_INTERRUPT_UMAC_FATAL    
[    4.351062] iwlwifi 0000:05:00.0: 0x002002F0 | trm_hw_status0
[    4.351064] iwlwifi 0000:05:00.0: 0x00000000 | trm_hw_status1
[    4.351065] iwlwifi 0000:05:00.0: 0x004DA1A2 | branchlink2
[    4.351066] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink1
[    4.351068] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink2
[    4.351069] iwlwifi 0000:05:00.0: 0x004D8F5A | data1
[    4.351070] iwlwifi 0000:05:00.0: 0x00000010 | data2
[    4.351071] iwlwifi 0000:05:00.0: 0x00000000 | data3
[    4.351073] iwlwifi 0000:05:00.0: 0x00000000 | beacon time
[    4.351074] iwlwifi 0000:05:00.0: 0x000128CD | tsf low
[    4.351075] iwlwifi 0000:05:00.0: 0x00000000 | tsf hi
[    4.351077] iwlwifi 0000:05:00.0: 0x00000000 | time gp1
[    4.351078] iwlwifi 0000:05:00.0: 0x0002673C | time gp2
[    4.351079] iwlwifi 0000:05:00.0: 0x00000001 | uCode revision type
[    4.351080] iwlwifi 0000:05:00.0: 0x00000042 | uCode version major
[    4.351082] iwlwifi 0000:05:00.0: 0x55C64978 | uCode version minor
[    4.351083] iwlwifi 0000:05:00.0: 0x00000420 | hw version
[    4.351084] iwlwifi 0000:05:00.0: 0x18C89002 | board version
[    4.351098] iwlwifi 0000:05:00.0: 0x8008FF05 | hcmd
[    4.351099] iwlwifi 0000:05:00.0: 0x00020000 | isr0
[    4.351100] iwlwifi 0000:05:00.0: 0x60000000 | isr1
[    4.351102] iwlwifi 0000:05:00.0: 0x48F00002 | isr2
[    4.351103] iwlwifi 0000:05:00.0: 0x00C0000C | isr3
[    4.351104] iwlwifi 0000:05:00.0: 0x00000000 | isr4
[    4.351105] iwlwifi 0000:05:00.0: 0x00000000 | last cmd Id
[    4.351106] iwlwifi 0000:05:00.0: 0x004D8F5A | wait_event
[    4.351108] iwlwifi 0000:05:00.0: 0x00000000 | l2p_control
[    4.351109] iwlwifi 0000:05:00.0: 0x00000000 | l2p_duration
[    4.351110] iwlwifi 0000:05:00.0: 0x00000000 | l2p_mhvalid
[    4.351111] iwlwifi 0000:05:00.0: 0x00000000 | l2p_addr_match
[    4.351113] iwlwifi 0000:05:00.0: 0x00000009 | lmpm_pmg_sel
[    4.351114] iwlwifi 0000:05:00.0: 0x00000000 | timestamp
[    4.351126] iwlwifi 0000:05:00.0: 0x00000024 | flow_handler
[    4.351182] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    4.351183] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 7
[    4.351185] iwlwifi 0000:05:00.0: PNVM data is missing, please install iwlwifi-ty-a0-gf-a0.pnvm
[    4.351186] iwlwifi 0000:05:00.0: 0x2010070D | PNVM_MISSING
[    4.351187] iwlwifi 0000:05:00.0: 0x00000000 | umac branchlink1
[    4.351189] iwlwifi 0000:05:00.0: 0x8045DFC6 | umac branchlink2
[    4.351190] iwlwifi 0000:05:00.0: 0x0109012A | umac interruptlink1
[    4.351191] iwlwifi 0000:05:00.0: 0x00000000 | umac interruptlink2
[    4.351192] iwlwifi 0000:05:00.0: 0x00000005 | umac data1
[    4.351193] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data2
[    4.351194] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data3
[    4.351195] iwlwifi 0000:05:00.0: 0x00000042 | umac major
[    4.351197] iwlwifi 0000:05:00.0: 0x55C64978 | umac minor
[    4.351198] iwlwifi 0000:05:00.0: 0x00026734 | frame pointer
[    4.351199] iwlwifi 0000:05:00.0: 0xC0885E88 | stack pointer
[    4.351200] iwlwifi 0000:05:00.0: 0x00010C00 | last host cmd
[    4.351201] iwlwifi 0000:05:00.0: 0x00000000 | isr status reg
[    4.351218] iwlwifi 0000:05:00.0: IML/ROM dump:
[    4.351219] iwlwifi 0000:05:00.0: 0x00000B03 | IML/ROM error/state
[    4.351233] iwlwifi 0000:05:00.0: 0x00007EA9 | IML/ROM data1
[    4.351243] iwlwifi 0000:05:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[    4.351249] iwlwifi 0000:05:00.0: Fseq Registers:
[    4.351255] iwlwifi 0000:05:00.0: 0x60000000 | FSEQ_ERROR_CODE
[    4.351262] iwlwifi 0000:05:00.0: 0x80440003 | FSEQ_TOP_INIT_VERSION
[    4.351268] iwlwifi 0000:05:00.0: 0x00080009 | FSEQ_CNVIO_INIT_VERSION
[    4.351274] iwlwifi 0000:05:00.0: 0x0000A652 | FSEQ_OTP_VERSION
[    4.351281] iwlwifi 0000:05:00.0: 0x00000002 | FSEQ_TOP_CONTENT_VERSION
[    4.351287] iwlwifi 0000:05:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN
[    4.351293] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVI_ID
[    4.351300] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVR_ID
[    4.351306] iwlwifi 0000:05:00.0: 0x00400410 | CNVI_AUX_MISC_CHIP
[    4.351313] iwlwifi 0000:05:00.0: 0x00400410 | CNVR_AUX_MISC_CHIP
[    4.351319] iwlwifi 0000:05:00.0: 0x00009061 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    4.351325] iwlwifi 0000:05:00.0: 0x00000061 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    4.351345] iwlwifi 0000:05:00.0: WRT: Collecting data: ini trigger 13 fired (delay=0ms).
[    5.167967] iwlwifi 0000:05:00.0: Failed to run INIT ucode: -5
[    5.180292] iwlwifi 0000:05:00.0: retry init count 2
junior@ubuntuDesktop:~$ 

```

---

### Post by chili555 on 2022-02-24
Is this a dual-boot with Windows? Please see: [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled)

---

### Post by ocmjunior on 2022-03-08
yes, it is dual boot. but now i disabled the Fast Boot on windows.

and i still have the same problem:

```

junior@Ubuntu:~$ sudo dmesg | grep iwl 
[sudo] senha para junior:  
[    2.399411] iwlwifi 0000:05:00.0: uCode file size 9866284 does not match expected size 
[    2.401869] iwlwifi 0000:05:00.0: api flags index 2 larger than supported by driver 
[    2.401883] iwlwifi 0000:05:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 0.63.2.1 
[    2.402089] iwlwifi 0000:05:00.0: loaded firmware version 66.55c64978.0 ty-a0-gf-a0-66.ucode op_mode iwlmvm 
[    2.505134] iwlwifi 0000:05:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420 
[    2.511446] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 1, ret=-1 
[    2.511448] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 2, ret=-1 
[    2.511450] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 3, ret=-1 
[    2.670764] iwlwifi 0000:05:00.0: Detected RF GF, rfid=0x10d000 
[    2.671721] iwlwifi 0000:05:00.0: Microcode SW error detected. Restarting 0x0. 
[    2.671813] iwlwifi 0000:05:00.0: Start IWL Error Log Dump: 
[    2.671816] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 6 
[    2.671819] iwlwifi 0000:05:00.0: Loaded firmware version: 66.55c64978.0 ty-a0-gf-a0-66.ucode 
[    2.671822] iwlwifi 0000:05:00.0: 0x00000071 | NMI_INTERRUPT_UMAC_FATAL     
[    2.671825] iwlwifi 0000:05:00.0: 0x002002F0 | trm_hw_status0 
[    2.671828] iwlwifi 0000:05:00.0: 0x00000000 | trm_hw_status1 
[    2.671830] iwlwifi 0000:05:00.0: 0x004DA1A2 | branchlink2 
[    2.671832] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink1 
[    2.671834] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink2 
[    2.671836] iwlwifi 0000:05:00.0: 0x004D8F5A | data1 
[    2.671838] iwlwifi 0000:05:00.0: 0x00000010 | data2 
[    2.671840] iwlwifi 0000:05:00.0: 0x00000000 | data3 
[    2.671842] iwlwifi 0000:05:00.0: 0x00000000 | beacon time 
[    2.671844] iwlwifi 0000:05:00.0: 0x00012947 | tsf low 
[    2.671846] iwlwifi 0000:05:00.0: 0x00000000 | tsf hi 
[    2.671849] iwlwifi 0000:05:00.0: 0x00000000 | time gp1 
[    2.671851] iwlwifi 0000:05:00.0: 0x000267AF | time gp2 
[    2.671853] iwlwifi 0000:05:00.0: 0x00000001 | uCode revision type 
[    2.671855] iwlwifi 0000:05:00.0: 0x00000042 | uCode version major 
[    2.671858] iwlwifi 0000:05:00.0: 0x55C64978 | uCode version minor 
[    2.671860] iwlwifi 0000:05:00.0: 0x00000420 | hw version 
[    2.671862] iwlwifi 0000:05:00.0: 0x18C89002 | board version 
[    2.671864] iwlwifi 0000:05:00.0: 0x8008FF05 | hcmd 
[    2.671867] iwlwifi 0000:05:00.0: 0x00020000 | isr0 
[    2.671869] iwlwifi 0000:05:00.0: 0x20000000 | isr1 
[    2.671871] iwlwifi 0000:05:00.0: 0x48F00002 | isr2 
[    2.671873] iwlwifi 0000:05:00.0: 0x00C0000C | isr3 
[    2.671875] iwlwifi 0000:05:00.0: 0x00000000 | isr4 
[    2.671877] iwlwifi 0000:05:00.0: 0x00000000 | last cmd Id 
[    2.671879] iwlwifi 0000:05:00.0: 0x004D8F5A | wait_event 
[    2.671881] iwlwifi 0000:05:00.0: 0x00000000 | l2p_control 
[    2.671884] iwlwifi 0000:05:00.0: 0x00000000 | l2p_duration 
[    2.671886] iwlwifi 0000:05:00.0: 0x00000000 | l2p_mhvalid 
[    2.671888] iwlwifi 0000:05:00.0: 0x00000000 | l2p_addr_match 
[    2.671890] iwlwifi 0000:05:00.0: 0x00000009 | lmpm_pmg_sel 
[    2.671892] iwlwifi 0000:05:00.0: 0x00000000 | timestamp 
[    2.671894] iwlwifi 0000:05:00.0: 0x00000024 | flow_handler 
[    2.671935] iwlwifi 0000:05:00.0: Start IWL Error Log Dump: 
[    2.671937] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 7 
[    2.671940] iwlwifi 0000:05:00.0: 0x2010070D | ADVANCED_SYSASSERT 
[    2.671942] iwlwifi 0000:05:00.0: 0x00000000 | umac branchlink1 
[    2.671944] iwlwifi 0000:05:00.0: 0x8045DFC6 | umac branchlink2 
[    2.671947] iwlwifi 0000:05:00.0: 0x010900FE | umac interruptlink1 
[    2.671949] iwlwifi 0000:05:00.0: 0x00000000 | umac interruptlink2 
[    2.671951] iwlwifi 0000:05:00.0: 0x00000005 | umac data1 
[    2.671953] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data2 
[    2.671955] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data3 
[    2.671958] iwlwifi 0000:05:00.0: 0x00000042 | umac major 
[    2.671960] iwlwifi 0000:05:00.0: 0x55C64978 | umac minor 
[    2.671962] iwlwifi 0000:05:00.0: 0x000267A7 | frame pointer 
[    2.671964] iwlwifi 0000:05:00.0: 0xC0885E88 | stack pointer 
[    2.671966] iwlwifi 0000:05:00.0: 0x00010C00 | last host cmd 
[    2.671968] iwlwifi 0000:05:00.0: 0x00000000 | isr status reg 
[    2.671987] iwlwifi 0000:05:00.0: IML/ROM dump: 
[    2.671989] iwlwifi 0000:05:00.0: 0x00000B03 | IML/ROM error/state 
[    2.672006] iwlwifi 0000:05:00.0: 0x00007EA8 | IML/ROM data1 
[    2.672021] iwlwifi 0000:05:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0 
[    2.672032] iwlwifi 0000:05:00.0: Fseq Registers: 
[    2.672043] iwlwifi 0000:05:00.0: 0x60000000 | FSEQ_ERROR_CODE 
[    2.672054] iwlwifi 0000:05:00.0: 0x80440003 | FSEQ_TOP_INIT_VERSION 
[    2.672065] iwlwifi 0000:05:00.0: 0x00080009 | FSEQ_CNVIO_INIT_VERSION 
[    2.672077] iwlwifi 0000:05:00.0: 0x0000A652 | FSEQ_OTP_VERSION 
[    2.672088] iwlwifi 0000:05:00.0: 0x00000002 | FSEQ_TOP_CONTENT_VERSION 
[    2.672099] iwlwifi 0000:05:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN 
[    2.672110] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVI_ID 
[    2.672121] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVR_ID 
[    2.672133] iwlwifi 0000:05:00.0: 0x00400410 | CNVI_AUX_MISC_CHIP 
[    2.672146] iwlwifi 0000:05:00.0: 0x00400410 | CNVR_AUX_MISC_CHIP 
[    2.672159] iwlwifi 0000:05:00.0: 0x00009061 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM 
[    2.672173] iwlwifi 0000:05:00.0: 0x00000061 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR 
[    2.672190] iwlwifi 0000:05:00.0: WRT: Collecting data: ini trigger 13 fired (delay=0ms). 
[    3.483047] iwlwifi 0000:05:00.0: Failed to run INIT ucode: -5 
[    3.495357] iwlwifi 0000:05:00.0: retry init count 0 
[    3.495686] iwlwifi 0000:05:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420 
[    3.501276] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 1, ret=-1 
[    3.501278] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 2, ret=-1 
[    3.501279] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 3, ret=-1 
[    3.660445] iwlwifi 0000:05:00.0: Microcode SW error detected. Restarting 0x0. 
[    3.660648] iwlwifi 0000:05:00.0: Start IWL Error Log Dump: 
[    3.660693] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 6 
[    3.660696] iwlwifi 0000:05:00.0: Loaded firmware version: 66.55c64978.0 ty-a0-gf-a0-66.ucode 
[    3.660699] iwlwifi 0000:05:00.0: 0x00000071 | NMI_INTERRUPT_UMAC_FATAL     
[    3.660836] iwlwifi 0000:05:00.0: 0x002002F0 | trm_hw_status0 
[    3.660870] iwlwifi 0000:05:00.0: 0x00000000 | trm_hw_status1 
[    3.660912] iwlwifi 0000:05:00.0: 0x004DA1A2 | branchlink2 
[    3.660943] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink1 
[    3.660975] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink2 
[    3.661006] iwlwifi 0000:05:00.0: 0x004D8F5A | data1 
[    3.661034] iwlwifi 0000:05:00.0: 0x00000010 | data2 
[    3.661062] iwlwifi 0000:05:00.0: 0x00000000 | data3 
[    3.661090] iwlwifi 0000:05:00.0: 0x00000000 | beacon time 
[    3.661120] iwlwifi 0000:05:00.0: 0x000128EE | tsf low 
[    3.661149] iwlwifi 0000:05:00.0: 0x00000000 | tsf hi 
[    3.661179] iwlwifi 0000:05:00.0: 0x00000000 | time gp1 
[    3.661208] iwlwifi 0000:05:00.0: 0x00026757 | time gp2 
[    3.661237] iwlwifi 0000:05:00.0: 0x00000001 | uCode revision type 
[    3.661271] iwlwifi 0000:05:00.0: 0x00000042 | uCode version major 
[    3.661308] iwlwifi 0000:05:00.0: 0x55C64978 | uCode version minor 
[    3.661341] iwlwifi 0000:05:00.0: 0x00000420 | hw version 
[    3.661371] iwlwifi 0000:05:00.0: 0x18C89002 | board version 
[    3.661414] iwlwifi 0000:05:00.0: 0x8008FF05 | hcmd 
[    3.661440] iwlwifi 0000:05:00.0: 0x00020000 | isr0 
[    3.661467] iwlwifi 0000:05:00.0: 0x60000000 | isr1 
[    3.661493] iwlwifi 0000:05:00.0: 0x48F00002 | isr2 
[    3.661519] iwlwifi 0000:05:00.0: 0x00C0000C | isr3 
[    3.661557] iwlwifi 0000:05:00.0: 0x00000000 | isr4 
[    3.662519] iwlwifi 0000:05:00.0: 0x00000000 | last cmd Id 
[    3.663411] iwlwifi 0000:05:00.0: 0x004D8F5A | wait_event 
[    3.664223] iwlwifi 0000:05:00.0: 0x00000000 | l2p_control 
[    3.665087] iwlwifi 0000:05:00.0: 0x00000000 | l2p_duration 
[    3.665611] iwlwifi 0000:05:00.0: 0x00000000 | l2p_mhvalid 
[    3.666417] iwlwifi 0000:05:00.0: 0x00000000 | l2p_addr_match 
[    3.666939] iwlwifi 0000:05:00.0: 0x00000009 | lmpm_pmg_sel 
[    3.667483] iwlwifi 0000:05:00.0: 0x00000000 | timestamp 
[    3.668400] iwlwifi 0000:05:00.0: 0x00000024 | flow_handler 
[    3.669388] iwlwifi 0000:05:00.0: Start IWL Error Log Dump: 
[    3.670294] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 7 
[    3.671211] iwlwifi 0000:05:00.0: 0x2010070D | ADVANCED_SYSASSERT 
[    3.672097] iwlwifi 0000:05:00.0: 0x00000000 | umac branchlink1 
[    3.672982] iwlwifi 0000:05:00.0: 0x8045DFC6 | umac branchlink2 
[    3.672986] iwlwifi 0000:05:00.0: 0x0109012A | umac interruptlink1 
[    3.672988] iwlwifi 0000:05:00.0: 0x00000000 | umac interruptlink2 
[    3.672990] iwlwifi 0000:05:00.0: 0x00000005 | umac data1 
[    3.676781] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data2 
[    3.676784] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data3 
[    3.677738] iwlwifi 0000:05:00.0: 0x00000042 | umac major 
[    3.677740] iwlwifi 0000:05:00.0: 0x55C64978 | umac minor 
[    3.678604] iwlwifi 0000:05:00.0: 0x0002674F | frame pointer 
[    3.679008] iwlwifi 0000:05:00.0: 0xC0885E88 | stack pointer 
[    3.679408] iwlwifi 0000:05:00.0: 0x00010C00 | last host cmd 
[    3.679796] iwlwifi 0000:05:00.0: 0x00000000 | isr status reg 
[    3.680201] iwlwifi 0000:05:00.0: IML/ROM dump: 
[    3.680579] iwlwifi 0000:05:00.0: 0x00000B03 | IML/ROM error/state 
[    3.680980] iwlwifi 0000:05:00.0: 0x00007EAA | IML/ROM data1 
[    3.681370] iwlwifi 0000:05:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0 
[    3.681989] iwlwifi 0000:05:00.0: Fseq Registers: 
[    3.682621] iwlwifi 0000:05:00.0: 0x60000000 | FSEQ_ERROR_CODE 
[    3.683291] iwlwifi 0000:05:00.0: 0x80440003 | FSEQ_TOP_INIT_VERSION 
[    3.683958] iwlwifi 0000:05:00.0: 0x00080009 | FSEQ_CNVIO_INIT_VERSION 
[    3.684635] iwlwifi 0000:05:00.0: 0x0000A652 | FSEQ_OTP_VERSION 
[    3.685335] iwlwifi 0000:05:00.0: 0x00000002 | FSEQ_TOP_CONTENT_VERSION 
[    3.686033] iwlwifi 0000:05:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN 
[    3.686726] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVI_ID 
[    3.687422] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVR_ID 
[    3.688110] iwlwifi 0000:05:00.0: 0x00400410 | CNVI_AUX_MISC_CHIP 
[    3.688591] iwlwifi 0000:05:00.0: 0x00400410 | CNVR_AUX_MISC_CHIP 
[    3.689007] iwlwifi 0000:05:00.0: 0x00009061 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM 
[    3.689456] iwlwifi 0000:05:00.0: 0x00000061 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR 
[    3.689890] iwlwifi 0000:05:00.0: WRT: Collecting data: ini trigger 13 fired (delay=0ms). 
[    4.510661] iwlwifi 0000:05:00.0: Failed to run INIT ucode: -5 
[    4.522998] iwlwifi 0000:05:00.0: retry init count 1 
[    4.523410] iwlwifi 0000:05:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420 
[    4.774057] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 1, ret=-1 
[    4.774069] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 2, ret=-1 
[    4.774075] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 3, ret=-1 
[    4.935006] iwlwifi 0000:05:00.0: Microcode SW error detected. Restarting 0x0. 
[    4.935097] iwlwifi 0000:05:00.0: Start IWL Error Log Dump: 
[    4.935099] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 6 
[    4.935101] iwlwifi 0000:05:00.0: Loaded firmware version: 66.55c64978.0 ty-a0-gf-a0-66.ucode 
[    4.935103] iwlwifi 0000:05:00.0: 0x00000071 | NMI_INTERRUPT_UMAC_FATAL     
[    4.935105] iwlwifi 0000:05:00.0: 0x002002F0 | trm_hw_status0 
[    4.935107] iwlwifi 0000:05:00.0: 0x00000000 | trm_hw_status1 
[    4.935108] iwlwifi 0000:05:00.0: 0x004DA1A2 | branchlink2 
[    4.935110] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink1 
[    4.935111] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink2 
[    4.935113] iwlwifi 0000:05:00.0: 0x004D8F5A | data1 
[    4.935114] iwlwifi 0000:05:00.0: 0x00000010 | data2 
[    4.935116] iwlwifi 0000:05:00.0: 0x00000000 | data3 
[    4.935117] iwlwifi 0000:05:00.0: 0x00000000 | beacon time 
[    4.935119] iwlwifi 0000:05:00.0: 0x000128F5 | tsf low 
[    4.935120] iwlwifi 0000:05:00.0: 0x00000000 | tsf hi 
[    4.935122] iwlwifi 0000:05:00.0: 0x00000000 | time gp1 
[    4.935123] iwlwifi 0000:05:00.0: 0x00026761 | time gp2 
[    4.935125] iwlwifi 0000:05:00.0: 0x00000001 | uCode revision type 
[    4.935126] iwlwifi 0000:05:00.0: 0x00000042 | uCode version major 
[    4.935127] iwlwifi 0000:05:00.0: 0x55C64978 | uCode version minor 
[    4.935129] iwlwifi 0000:05:00.0: 0x00000420 | hw version 
[    4.935130] iwlwifi 0000:05:00.0: 0x18C89002 | board version 
[    4.935132] iwlwifi 0000:05:00.0: 0x8008FF05 | hcmd 
[    4.935133] iwlwifi 0000:05:00.0: 0x00020000 | isr0 
[    4.935135] iwlwifi 0000:05:00.0: 0x60000000 | isr1 
[    4.935136] iwlwifi 0000:05:00.0: 0x48F00002 | isr2 
[    4.935137] iwlwifi 0000:05:00.0: 0x00C0000C | isr3 
[    4.935139] iwlwifi 0000:05:00.0: 0x00000000 | isr4 
[    4.935140] iwlwifi 0000:05:00.0: 0x00000000 | last cmd Id 
[    4.935141] iwlwifi 0000:05:00.0: 0x004D8F5A | wait_event 
[    4.935143] iwlwifi 0000:05:00.0: 0x00000000 | l2p_control 
[    4.935144] iwlwifi 0000:05:00.0: 0x00000000 | l2p_duration 
[    4.935146] iwlwifi 0000:05:00.0: 0x00000000 | l2p_mhvalid 
[    4.935147] iwlwifi 0000:05:00.0: 0x00000000 | l2p_addr_match 
[    4.935149] iwlwifi 0000:05:00.0: 0x00000009 | lmpm_pmg_sel 
[    4.935150] iwlwifi 0000:05:00.0: 0x00000000 | timestamp 
[    4.935151] iwlwifi 0000:05:00.0: 0x00000024 | flow_handler 
[    4.935191] iwlwifi 0000:05:00.0: Start IWL Error Log Dump: 
[    4.935193] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 7 
[    4.935194] iwlwifi 0000:05:00.0: 0x2010070D | ADVANCED_SYSASSERT 
[    4.935196] iwlwifi 0000:05:00.0: 0x00000000 | umac branchlink1 
[    4.935197] iwlwifi 0000:05:00.0: 0x8045DFC6 | umac branchlink2 
[    4.935199] iwlwifi 0000:05:00.0: 0x0109012A | umac interruptlink1 
[    4.935200] iwlwifi 0000:05:00.0: 0x00000000 | umac interruptlink2 
[    4.935202] iwlwifi 0000:05:00.0: 0x00000005 | umac data1 
[    4.935203] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data2 
[    4.935204] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data3 
[    4.935206] iwlwifi 0000:05:00.0: 0x00000042 | umac major 
[    4.935207] iwlwifi 0000:05:00.0: 0x55C64978 | umac minor 
[    4.935209] iwlwifi 0000:05:00.0: 0x00026758 | frame pointer 
[    4.935210] iwlwifi 0000:05:00.0: 0xC0885E88 | stack pointer 
[    4.935211] iwlwifi 0000:05:00.0: 0x00010C00 | last host cmd 
[    4.935213] iwlwifi 0000:05:00.0: 0x00000000 | isr status reg 
[    4.935230] iwlwifi 0000:05:00.0: IML/ROM dump: 
[    4.935232] iwlwifi 0000:05:00.0: 0x00000B03 | IML/ROM error/state 
[    4.935249] iwlwifi 0000:05:00.0: 0x00007EAA | IML/ROM data1 
[    4.935259] iwlwifi 0000:05:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0 
[    4.935266] iwlwifi 0000:05:00.0: Fseq Registers: 
[    4.935272] iwlwifi 0000:05:00.0: 0x60000000 | FSEQ_ERROR_CODE 
[    4.935283] iwlwifi 0000:05:00.0: 0x80440003 | FSEQ_TOP_INIT_VERSION 
[    4.935295] iwlwifi 0000:05:00.0: 0x00080009 | FSEQ_CNVIO_INIT_VERSION 
[    4.935306] iwlwifi 0000:05:00.0: 0x0000A652 | FSEQ_OTP_VERSION 
[    4.935317] iwlwifi 0000:05:00.0: 0x00000002 | FSEQ_TOP_CONTENT_VERSION 
[    4.935328] iwlwifi 0000:05:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN 
[    4.935339] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVI_ID 
[    4.935351] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVR_ID 
[    4.935362] iwlwifi 0000:05:00.0: 0x00400410 | CNVI_AUX_MISC_CHIP 
[    4.935375] iwlwifi 0000:05:00.0: 0x00400410 | CNVR_AUX_MISC_CHIP 
[    4.935389] iwlwifi 0000:05:00.0: 0x00009061 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM 
[    4.935402] iwlwifi 0000:05:00.0: 0x00000061 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR 
[    4.935453] iwlwifi 0000:05:00.0: WRT: Collecting data: ini trigger 13 fired (delay=0ms). 
[    5.754982] iwlwifi 0000:05:00.0: Failed to run INIT ucode: -5 
[    5.767267] iwlwifi 0000:05:00.0: retry init count 2 



```

---

### Post by chili555 on 2022-03-08
```
uCode file size [COLOR="#FF0000"]9866284[/COLOR] does not match expected size 
```I sudpect that the firmware file is somehow corrupted. 

From my machine:

```
$ ls -al /usr/lib/firmware/iwlwifi-ty-a0-gf-a0-66.ucode
-rw-r--r-- 1 root root [COLOR="#FF0000"]1477864 [/COLOR]Jan 28 05:12 /usr/lib/firmware/iwlwifi-ty-a0-gf-a0-66.ucode
```


Please get a temporary working internet connection and do:

```
sudo apt update
sudo apt install --reinstall linux-firmware

```
Reboot. Is there any improvement?

---

### Post by ocmjunior on 2022-03-20
```


junior@Ubuntu:~$ uname -r
5.16.0-051600-generic
junior@Ubuntu:~$ sudo dmesg | grep iwl
[sudo] senha para junior: 
[    2.146936] iwlwifi 0000:05:00.0: uCode file size 9866284 does not match expected size
[    2.152871] iwlwifi 0000:05:00.0: api flags index 2 larger than supported by driver
[    2.152886] iwlwifi 0000:05:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 0.63.2.1
[    2.153183] iwlwifi 0000:05:00.0: loaded firmware version 66.55c64978.0 ty-a0-gf-a0-66.ucode op_mode iwlmvm
[    2.228489] iwlwifi 0000:05:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420
[    2.234857] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 1, ret=-1
[    2.234861] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 2, ret=-1
[    2.234862] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 3, ret=-1
[    2.394021] iwlwifi 0000:05:00.0: Detected RF GF, rfid=0x10d000
[    2.395048] iwlwifi 0000:05:00.0: Microcode SW error detected. Restarting 0x0.
[    2.395140] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    2.395142] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 6
[    2.395145] iwlwifi 0000:05:00.0: Loaded firmware version: 66.55c64978.0 ty-a0-gf-a0-66.ucode
[    2.395148] iwlwifi 0000:05:00.0: 0x00000071 | NMI_INTERRUPT_UMAC_FATAL    
[    2.395150] iwlwifi 0000:05:00.0: 0x002002F0 | trm_hw_status0
[    2.395153] iwlwifi 0000:05:00.0: 0x00000000 | trm_hw_status1
[    2.395155] iwlwifi 0000:05:00.0: 0x004DA1A2 | branchlink2
[    2.395157] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink1
[    2.395159] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink2
[    2.395160] iwlwifi 0000:05:00.0: 0x004D8F5A | data1
[    2.395162] iwlwifi 0000:05:00.0: 0x00000010 | data2
[    2.395164] iwlwifi 0000:05:00.0: 0x00000000 | data3
[    2.395166] iwlwifi 0000:05:00.0: 0x00000000 | beacon time
[    2.395168] iwlwifi 0000:05:00.0: 0x000128B6 | tsf low
[    2.395170] iwlwifi 0000:05:00.0: 0x00000000 | tsf hi
[    2.395172] iwlwifi 0000:05:00.0: 0x00000000 | time gp1
[    2.395174] iwlwifi 0000:05:00.0: 0x00026721 | time gp2
[    2.395176] iwlwifi 0000:05:00.0: 0x00000001 | uCode revision type
[    2.395178] iwlwifi 0000:05:00.0: 0x00000042 | uCode version major
[    2.395180] iwlwifi 0000:05:00.0: 0x55C64978 | uCode version minor
[    2.395182] iwlwifi 0000:05:00.0: 0x00000420 | hw version
[    2.395185] iwlwifi 0000:05:00.0: 0x00C89002 | board version
[    2.395187] iwlwifi 0000:05:00.0: 0x8008FF05 | hcmd
[    2.395189] iwlwifi 0000:05:00.0: 0x00020000 | isr0
[    2.395191] iwlwifi 0000:05:00.0: 0x60000000 | isr1
[    2.395193] iwlwifi 0000:05:00.0: 0x48F00002 | isr2
[    2.395195] iwlwifi 0000:05:00.0: 0x00C0000C | isr3
[    2.395196] iwlwifi 0000:05:00.0: 0x00000000 | isr4
[    2.395198] iwlwifi 0000:05:00.0: 0x00000000 | last cmd Id
[    2.395200] iwlwifi 0000:05:00.0: 0x004D8F5A | wait_event
[    2.395202] iwlwifi 0000:05:00.0: 0x00000000 | l2p_control
[    2.395204] iwlwifi 0000:05:00.0: 0x00000000 | l2p_duration
[    2.395207] iwlwifi 0000:05:00.0: 0x00000000 | l2p_mhvalid
[    2.395209] iwlwifi 0000:05:00.0: 0x00000000 | l2p_addr_match
[    2.395211] iwlwifi 0000:05:00.0: 0x00000009 | lmpm_pmg_sel
[    2.395212] iwlwifi 0000:05:00.0: 0x00000000 | timestamp
[    2.395214] iwlwifi 0000:05:00.0: 0x00000024 | flow_handler
[    2.395255] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    2.395257] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 7
[    2.395259] iwlwifi 0000:05:00.0: 0x2010070D | ADVANCED_SYSASSERT
[    2.395262] iwlwifi 0000:05:00.0: 0x00000000 | umac branchlink1
[    2.395264] iwlwifi 0000:05:00.0: 0x8045DFC6 | umac branchlink2
[    2.395266] iwlwifi 0000:05:00.0: 0x0109012A | umac interruptlink1
[    2.395268] iwlwifi 0000:05:00.0: 0x00000000 | umac interruptlink2
[    2.395270] iwlwifi 0000:05:00.0: 0x00000005 | umac data1
[    2.395272] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data2
[    2.395274] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data3
[    2.395276] iwlwifi 0000:05:00.0: 0x00000042 | umac major
[    2.395278] iwlwifi 0000:05:00.0: 0x55C64978 | umac minor
[    2.395279] iwlwifi 0000:05:00.0: 0x00026718 | frame pointer
[    2.395281] iwlwifi 0000:05:00.0: 0xC0885E88 | stack pointer
[    2.395283] iwlwifi 0000:05:00.0: 0x00010C00 | last host cmd
[    2.395285] iwlwifi 0000:05:00.0: 0x00000000 | isr status reg
[    2.395304] iwlwifi 0000:05:00.0: IML/ROM dump:
[    2.395306] iwlwifi 0000:05:00.0: 0x00000B03 | IML/ROM error/state
[    2.395323] iwlwifi 0000:05:00.0: 0x00007EAA | IML/ROM data1
[    2.395337] iwlwifi 0000:05:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[    2.395348] iwlwifi 0000:05:00.0: Fseq Registers:
[    2.395359] iwlwifi 0000:05:00.0: 0x60000000 | FSEQ_ERROR_CODE
[    2.395371] iwlwifi 0000:05:00.0: 0x80440003 | FSEQ_TOP_INIT_VERSION
[    2.395382] iwlwifi 0000:05:00.0: 0x00080009 | FSEQ_CNVIO_INIT_VERSION
[    2.395393] iwlwifi 0000:05:00.0: 0x0000A652 | FSEQ_OTP_VERSION
[    2.395404] iwlwifi 0000:05:00.0: 0x00000002 | FSEQ_TOP_CONTENT_VERSION
[    2.395415] iwlwifi 0000:05:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN
[    2.395426] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVI_ID
[    2.395438] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVR_ID
[    2.395449] iwlwifi 0000:05:00.0: 0x00400410 | CNVI_AUX_MISC_CHIP
[    2.395462] iwlwifi 0000:05:00.0: 0x00400410 | CNVR_AUX_MISC_CHIP
[    2.395475] iwlwifi 0000:05:00.0: 0x00009061 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    2.395489] iwlwifi 0000:05:00.0: 0x00000061 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    2.395529] iwlwifi 0000:05:00.0: WRT: Collecting data: ini trigger 13 fired (delay=0ms).
[    3.206562] iwlwifi 0000:05:00.0: Failed to run INIT ucode: -5
[    3.218806] iwlwifi 0000:05:00.0: retry init count 0
[    3.219089] iwlwifi 0000:05:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420
[    3.225225] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 1, ret=-1
[    3.225226] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 2, ret=-1
[    3.225228] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 3, ret=-1
[    3.384305] iwlwifi 0000:05:00.0: Microcode SW error detected. Restarting 0x0.
[    3.384488] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    3.384505] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 6
[    3.384525] iwlwifi 0000:05:00.0: Loaded firmware version: 66.55c64978.0 ty-a0-gf-a0-66.ucode
[    3.384550] iwlwifi 0000:05:00.0: 0x00000071 | NMI_INTERRUPT_UMAC_FATAL    
[    3.384570] iwlwifi 0000:05:00.0: 0x002002F0 | trm_hw_status0
[    3.384587] iwlwifi 0000:05:00.0: 0x00000000 | trm_hw_status1
[    3.384604] iwlwifi 0000:05:00.0: 0x004DA1A2 | branchlink2
[    3.384619] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink1
[    3.384636] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink2
[    3.384652] iwlwifi 0000:05:00.0: 0x004D8F5A | data1
[    3.384667] iwlwifi 0000:05:00.0: 0x00000010 | data2
[    3.384681] iwlwifi 0000:05:00.0: 0x00000000 | data3
[    3.384695] iwlwifi 0000:05:00.0: 0x00000000 | beacon time
[    3.384711] iwlwifi 0000:05:00.0: 0x000128C8 | tsf low
[    3.384726] iwlwifi 0000:05:00.0: 0x00000000 | tsf hi
[    3.384741] iwlwifi 0000:05:00.0: 0x00000000 | time gp1
[    3.384756] iwlwifi 0000:05:00.0: 0x00026737 | time gp2
[    3.384771] iwlwifi 0000:05:00.0: 0x00000001 | uCode revision type
[    3.384788] iwlwifi 0000:05:00.0: 0x00000042 | uCode version major
[    3.384806] iwlwifi 0000:05:00.0: 0x55C64978 | uCode version minor
[    3.384824] iwlwifi 0000:05:00.0: 0x00000420 | hw version
[    3.384840] iwlwifi 0000:05:00.0: 0x18C89002 | board version
[    3.384856] iwlwifi 0000:05:00.0: 0x8008FF05 | hcmd
[    3.384870] iwlwifi 0000:05:00.0: 0x00020000 | isr0
[    3.384885] iwlwifi 0000:05:00.0: 0x60000000 | isr1
[    3.384899] iwlwifi 0000:05:00.0: 0x48F00002 | isr2
[    3.384913] iwlwifi 0000:05:00.0: 0x00C0000C | isr3
[    3.384942] iwlwifi 0000:05:00.0: 0x00000000 | isr4
[    3.384956] iwlwifi 0000:05:00.0: 0x00000000 | last cmd Id
[    3.384972] iwlwifi 0000:05:00.0: 0x004D8F5A | wait_event
[    3.384988] iwlwifi 0000:05:00.0: 0x00000000 | l2p_control
[    3.385525] iwlwifi 0000:05:00.0: 0x00000000 | l2p_duration
[    3.386008] iwlwifi 0000:05:00.0: 0x00000000 | l2p_mhvalid
[    3.386758] iwlwifi 0000:05:00.0: 0x00000000 | l2p_addr_match
[    3.387527] iwlwifi 0000:05:00.0: 0x00000009 | lmpm_pmg_sel
[    3.388290] iwlwifi 0000:05:00.0: 0x00000000 | timestamp
[    3.389065] iwlwifi 0000:05:00.0: 0x00000024 | flow_handler
[    3.389858] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    3.390618] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 7
[    3.391393] iwlwifi 0000:05:00.0: 0x2010070D | ADVANCED_SYSASSERT
[    3.392178] iwlwifi 0000:05:00.0: 0x00000000 | umac branchlink1
[    3.392966] iwlwifi 0000:05:00.0: 0x8045DFC6 | umac branchlink2
[    3.393726] iwlwifi 0000:05:00.0: 0x0109012A | umac interruptlink1
[    3.394466] iwlwifi 0000:05:00.0: 0x00000000 | umac interruptlink2
[    3.395184] iwlwifi 0000:05:00.0: 0x00000005 | umac data1
[    3.395879] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data2
[    3.396550] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data3
[    3.397213] iwlwifi 0000:05:00.0: 0x00000042 | umac major
[    3.397864] iwlwifi 0000:05:00.0: 0x55C64978 | umac minor
[    3.398494] iwlwifi 0000:05:00.0: 0x0002672F | frame pointer
[    3.399121] iwlwifi 0000:05:00.0: 0xC0885E88 | stack pointer
[    3.399731] iwlwifi 0000:05:00.0: 0x00010C00 | last host cmd
[    3.400318] iwlwifi 0000:05:00.0: 0x00000000 | isr status reg
[    3.400917] iwlwifi 0000:05:00.0: IML/ROM dump:
[    3.401492] iwlwifi 0000:05:00.0: 0x00000B03 | IML/ROM error/state
[    3.402089] iwlwifi 0000:05:00.0: 0x00007EAC | IML/ROM data1
[    3.402659] iwlwifi 0000:05:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[    3.403809] iwlwifi 0000:05:00.0: Fseq Registers:
[    3.404952] iwlwifi 0000:05:00.0: 0x60000000 | FSEQ_ERROR_CODE
[    3.405948] iwlwifi 0000:05:00.0: 0x80440003 | FSEQ_TOP_INIT_VERSION
[    3.406348] iwlwifi 0000:05:00.0: 0x00080009 | FSEQ_CNVIO_INIT_VERSION
[    3.406818] iwlwifi 0000:05:00.0: 0x0000A652 | FSEQ_OTP_VERSION
[    3.407226] iwlwifi 0000:05:00.0: 0x00000002 | FSEQ_TOP_CONTENT_VERSION
[    3.407671] iwlwifi 0000:05:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN
[    3.408136] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVI_ID
[    3.408570] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVR_ID
[    3.408992] iwlwifi 0000:05:00.0: 0x00400410 | CNVI_AUX_MISC_CHIP
[    3.409431] iwlwifi 0000:05:00.0: 0x00400410 | CNVR_AUX_MISC_CHIP
[    3.409846] iwlwifi 0000:05:00.0: 0x00009061 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    3.410323] iwlwifi 0000:05:00.0: 0x00000061 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    3.410757] iwlwifi 0000:05:00.0: WRT: Collecting data: ini trigger 13 fired (delay=0ms).
[    4.225028] iwlwifi 0000:05:00.0: Failed to run INIT ucode: -5
[    4.236963] iwlwifi 0000:05:00.0: retry init count 1
[    4.237306] iwlwifi 0000:05:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420
[    4.243632] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 1, ret=-1
[    4.243634] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 2, ret=-1
[    4.243635] iwlwifi 0000:05:00.0: WRT: Failed to set DRAM buffer for alloc id 3, ret=-1
[    4.403287] iwlwifi 0000:05:00.0: Microcode SW error detected. Restarting 0x0.
[    4.403379] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    4.403381] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 6
[    4.403383] iwlwifi 0000:05:00.0: Loaded firmware version: 66.55c64978.0 ty-a0-gf-a0-66.ucode
[    4.403385] iwlwifi 0000:05:00.0: 0x00000071 | NMI_INTERRUPT_UMAC_FATAL    
[    4.403386] iwlwifi 0000:05:00.0: 0x002002F0 | trm_hw_status0
[    4.403388] iwlwifi 0000:05:00.0: 0x00000000 | trm_hw_status1
[    4.403389] iwlwifi 0000:05:00.0: 0x004DA1A2 | branchlink2
[    4.403390] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink1
[    4.403392] iwlwifi 0000:05:00.0: 0x004D0766 | interruptlink2
[    4.403393] iwlwifi 0000:05:00.0: 0x004D8F5A | data1
[    4.403394] iwlwifi 0000:05:00.0: 0x00000010 | data2
[    4.403395] iwlwifi 0000:05:00.0: 0x00000000 | data3
[    4.403396] iwlwifi 0000:05:00.0: 0x00000000 | beacon time
[    4.403398] iwlwifi 0000:05:00.0: 0x000128CB | tsf low
[    4.403399] iwlwifi 0000:05:00.0: 0x00000000 | tsf hi
[    4.403400] iwlwifi 0000:05:00.0: 0x00000000 | time gp1
[    4.403402] iwlwifi 0000:05:00.0: 0x00026733 | time gp2
[    4.403403] iwlwifi 0000:05:00.0: 0x00000001 | uCode revision type
[    4.403404] iwlwifi 0000:05:00.0: 0x00000042 | uCode version major
[    4.403405] iwlwifi 0000:05:00.0: 0x55C64978 | uCode version minor
[    4.403407] iwlwifi 0000:05:00.0: 0x00000420 | hw version
[    4.403408] iwlwifi 0000:05:00.0: 0x18C89002 | board version
[    4.403409] iwlwifi 0000:05:00.0: 0x8008FF05 | hcmd
[    4.403410] iwlwifi 0000:05:00.0: 0x00020000 | isr0
[    4.403412] iwlwifi 0000:05:00.0: 0x60000000 | isr1
[    4.403413] iwlwifi 0000:05:00.0: 0x48F00002 | isr2
[    4.403414] iwlwifi 0000:05:00.0: 0x00C0000C | isr3
[    4.403415] iwlwifi 0000:05:00.0: 0x00000000 | isr4
[    4.403416] iwlwifi 0000:05:00.0: 0x00000000 | last cmd Id
[    4.403417] iwlwifi 0000:05:00.0: 0x004D8F5A | wait_event
[    4.403418] iwlwifi 0000:05:00.0: 0x00000000 | l2p_control
[    4.403420] iwlwifi 0000:05:00.0: 0x00000000 | l2p_duration
[    4.403421] iwlwifi 0000:05:00.0: 0x00000000 | l2p_mhvalid
[    4.403422] iwlwifi 0000:05:00.0: 0x00000000 | l2p_addr_match
[    4.403423] iwlwifi 0000:05:00.0: 0x00000009 | lmpm_pmg_sel
[    4.403424] iwlwifi 0000:05:00.0: 0x00000000 | timestamp
[    4.403425] iwlwifi 0000:05:00.0: 0x00000024 | flow_handler
[    4.403465] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    4.403466] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 7
[    4.403468] iwlwifi 0000:05:00.0: 0x2010070D | ADVANCED_SYSASSERT
[    4.403469] iwlwifi 0000:05:00.0: 0x00000000 | umac branchlink1
[    4.403471] iwlwifi 0000:05:00.0: 0x8045DFC6 | umac branchlink2
[    4.403472] iwlwifi 0000:05:00.0: 0x0109012A | umac interruptlink1
[    4.403473] iwlwifi 0000:05:00.0: 0x00000000 | umac interruptlink2
[    4.403474] iwlwifi 0000:05:00.0: 0x00000005 | umac data1
[    4.403475] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data2
[    4.403477] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data3
[    4.403478] iwlwifi 0000:05:00.0: 0x00000042 | umac major
[    4.403479] iwlwifi 0000:05:00.0: 0x55C64978 | umac minor
[    4.403480] iwlwifi 0000:05:00.0: 0x0002672A | frame pointer
[    4.403481] iwlwifi 0000:05:00.0: 0xC0885E88 | stack pointer
[    4.403482] iwlwifi 0000:05:00.0: 0x00010C00 | last host cmd
[    4.403484] iwlwifi 0000:05:00.0: 0x00000000 | isr status reg
[    4.403501] iwlwifi 0000:05:00.0: IML/ROM dump:
[    4.403502] iwlwifi 0000:05:00.0: 0x00000B03 | IML/ROM error/state
[    4.403516] iwlwifi 0000:05:00.0: 0x00007EA8 | IML/ROM data1
[    4.403526] iwlwifi 0000:05:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[    4.403532] iwlwifi 0000:05:00.0: Fseq Registers:
[    4.403538] iwlwifi 0000:05:00.0: 0x60000000 | FSEQ_ERROR_CODE
[    4.403545] iwlwifi 0000:05:00.0: 0x80440003 | FSEQ_TOP_INIT_VERSION
[    4.403551] iwlwifi 0000:05:00.0: 0x00080009 | FSEQ_CNVIO_INIT_VERSION
[    4.403558] iwlwifi 0000:05:00.0: 0x0000A652 | FSEQ_OTP_VERSION
[    4.403564] iwlwifi 0000:05:00.0: 0x00000002 | FSEQ_TOP_CONTENT_VERSION
[    4.403571] iwlwifi 0000:05:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN
[    4.403577] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVI_ID
[    4.403583] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVR_ID
[    4.403590] iwlwifi 0000:05:00.0: 0x00400410 | CNVI_AUX_MISC_CHIP
[    4.403596] iwlwifi 0000:05:00.0: 0x00400410 | CNVR_AUX_MISC_CHIP
[    4.403602] iwlwifi 0000:05:00.0: 0x00009061 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    4.403616] iwlwifi 0000:05:00.0: 0x00000061 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    4.403628] iwlwifi 0000:05:00.0: WRT: Collecting data: ini trigger 13 fired (delay=0ms).
[    5.223051] iwlwifi 0000:05:00.0: Failed to run INIT ucode: -5
[    5.235429] iwlwifi 0000:05:00.0: retry init count 2


```

```

junior@Ubuntu:~$ ls -al /usr/lib/firmware/iwlwifi-ty-a0-gf-a0-66.ucode
-rw-r--r-- 1 root root 1477864 fev 18 11:22 /usr/lib/firmware/iwlwifi-ty-a0-gf-a0-66.ucode
junior@Ubuntu:~$ 

```

---

### Post by chili555 on 2022-03-21
Please try:

```
sudo mv /usr/lib/firmware/iwlwifi-ty-a0-gf-a0-66.ucode  /usr/lib/firmware/iwlwifi-ty-a0-gf-a0-66.bak

```
Reboot and tell us if there is any improvement. If not, do:

```
cd /usr/lib/firmware/
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/iwlwifi-ty-a0-gf-a0-66.ucode

```
I notice that this version has a different size and was changed 1-21-2022.

Again, reboot.

---

### Post by ocmjunior on 2022-03-24
This Card seems to be not ready to work with linux yet

```
root@Ubuntu:/home/junior# uname -r
5.16.0-051600-generic
root@Ubuntu:/home/junior# sudo dmesg | grep iwl
[    2.214061] iwlwifi 0000:05:00.0: uCode file size 9866284 does not match expected size
[    2.234803] iwlwifi 0000:05:00.0: uCode file size 9859197 does not match expected size
[    2.235418] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-ty-a0-gf-a0-65.ucode failed with error -2
[    2.235450] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-ty-a0-gf-a0-64.ucode failed with error -2
[    2.235564] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-ty-a0-gf-a0-63.ucode failed with error -2
[    2.254321] iwlwifi 0000:05:00.0: api flags index 2 larger than supported by driver
[    2.254350] iwlwifi 0000:05:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 0.59.2.22
[    2.254742] iwlwifi 0000:05:00.0: loaded firmware version 62.49eeb572.0 ty-a0-gf-a0-62.ucode op_mode iwlmvm
[    2.321131] iwlwifi 0000:05:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420
[    2.485347] iwlwifi 0000:05:00.0: Detected RF GF, rfid=0x10d000
[    2.486353] iwlwifi 0000:05:00.0: Microcode SW error detected. Restarting 0x0.
[    2.486447] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    2.486449] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 6
[    2.486452] iwlwifi 0000:05:00.0: Loaded firmware version: 62.49eeb572.0 ty-a0-gf-a0-62.ucode
[    2.486455] iwlwifi 0000:05:00.0: 0x00000071 | NMI_INTERRUPT_UMAC_FATAL    
[    2.486458] iwlwifi 0000:05:00.0: 0x002002F0 | trm_hw_status0
[    2.486461] iwlwifi 0000:05:00.0: 0x00000000 | trm_hw_status1
[    2.486463] iwlwifi 0000:05:00.0: 0x004DA02C | branchlink2
[    2.486465] iwlwifi 0000:05:00.0: 0x004D070E | interruptlink1
[    2.486467] iwlwifi 0000:05:00.0: 0x004D070E | interruptlink2
[    2.486469] iwlwifi 0000:05:00.0: 0x004D8E06 | data1
[    2.486471] iwlwifi 0000:05:00.0: 0x00000010 | data2
[    2.486473] iwlwifi 0000:05:00.0: 0x00000000 | data3
[    2.486475] iwlwifi 0000:05:00.0: 0x00000000 | beacon time
[    2.486477] iwlwifi 0000:05:00.0: 0x000122ED | tsf low
[    2.486479] iwlwifi 0000:05:00.0: 0x00000000 | tsf hi
[    2.486482] iwlwifi 0000:05:00.0: 0x00000000 | time gp1
[    2.486484] iwlwifi 0000:05:00.0: 0x00026351 | time gp2
[    2.486486] iwlwifi 0000:05:00.0: 0x00000001 | uCode revision type
[    2.486489] iwlwifi 0000:05:00.0: 0x0000003E | uCode version major
[    2.486491] iwlwifi 0000:05:00.0: 0x49EEB572 | uCode version minor
[    2.486493] iwlwifi 0000:05:00.0: 0x00000420 | hw version
[    2.486495] iwlwifi 0000:05:00.0: 0x18C89002 | board version
[    2.486498] iwlwifi 0000:05:00.0: 0x8008FF00 | hcmd
[    2.486500] iwlwifi 0000:05:00.0: 0x00020000 | isr0
[    2.486501] iwlwifi 0000:05:00.0: 0x60000000 | isr1
[    2.486502] iwlwifi 0000:05:00.0: 0x58F00002 | isr2
[    2.486507] iwlwifi 0000:05:00.0: 0x00C0001C | isr3
[    2.486510] iwlwifi 0000:05:00.0: 0x00000000 | isr4
[    2.486512] iwlwifi 0000:05:00.0: 0x00000000 | last cmd Id
[    2.486514] iwlwifi 0000:05:00.0: 0x004D8E06 | wait_event
[    2.486516] iwlwifi 0000:05:00.0: 0x00000000 | l2p_control
[    2.486518] iwlwifi 0000:05:00.0: 0x00000020 | l2p_duration
[    2.486520] iwlwifi 0000:05:00.0: 0x00000000 | l2p_mhvalid
[    2.486522] iwlwifi 0000:05:00.0: 0x00000000 | l2p_addr_match
[    2.486524] iwlwifi 0000:05:00.0: 0x00000009 | lmpm_pmg_sel
[    2.486527] iwlwifi 0000:05:00.0: 0x00000000 | timestamp
[    2.486529] iwlwifi 0000:05:00.0: 0x00000024 | flow_handler
[    2.486569] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    2.486572] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 7
[    2.486574] iwlwifi 0000:05:00.0: 0x2010070D | ADVANCED_SYSASSERT
[    2.486577] iwlwifi 0000:05:00.0: 0x00000000 | umac branchlink1
[    2.486579] iwlwifi 0000:05:00.0: 0x8045C7E4 | umac branchlink2
[    2.486581] iwlwifi 0000:05:00.0: 0x0108D0B2 | umac interruptlink1
[    2.486583] iwlwifi 0000:05:00.0: 0x00000000 | umac interruptlink2
[    2.486586] iwlwifi 0000:05:00.0: 0x00000005 | umac data1
[    2.486588] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data2
[    2.486590] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data3
[    2.486592] iwlwifi 0000:05:00.0: 0x0000003E | umac major
[    2.486594] iwlwifi 0000:05:00.0: 0x49EEB572 | umac minor
[    2.486596] iwlwifi 0000:05:00.0: 0x00026349 | frame pointer
[    2.486598] iwlwifi 0000:05:00.0: 0xC0885E90 | stack pointer
[    2.486601] iwlwifi 0000:05:00.0: 0x00010C00 | last host cmd
[    2.486603] iwlwifi 0000:05:00.0: 0x00000000 | isr status reg
[    2.486621] iwlwifi 0000:05:00.0: IML/ROM dump:
[    2.486623] iwlwifi 0000:05:00.0: 0x00000B03 | IML/ROM error/state
[    2.486640] iwlwifi 0000:05:00.0: 0x000080DC | IML/ROM data1
[    2.486655] iwlwifi 0000:05:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[    2.486666] iwlwifi 0000:05:00.0: Fseq Registers:
[    2.486677] iwlwifi 0000:05:00.0: 0x60000100 | FSEQ_ERROR_CODE
[    2.486692] iwlwifi 0000:05:00.0: 0x80440003 | FSEQ_TOP_INIT_VERSION
[    2.486703] iwlwifi 0000:05:00.0: 0x00070008 | FSEQ_CNVIO_INIT_VERSION
[    2.486715] iwlwifi 0000:05:00.0: 0x0000A652 | FSEQ_OTP_VERSION
[    2.486726] iwlwifi 0000:05:00.0: 0x00000002 | FSEQ_TOP_CONTENT_VERSION
[    2.486737] iwlwifi 0000:05:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN
[    2.486748] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVI_ID
[    2.486760] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVR_ID
[    2.486771] iwlwifi 0000:05:00.0: 0x00400410 | CNVI_AUX_MISC_CHIP
[    2.486784] iwlwifi 0000:05:00.0: 0x00400410 | CNVR_AUX_MISC_CHIP
[    2.486798] iwlwifi 0000:05:00.0: 0x00009061 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    2.486811] iwlwifi 0000:05:00.0: 0x00000061 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    2.486830] iwlwifi 0000:05:00.0: WRT: Collecting data: ini trigger 13 fired (delay=0ms).
[    3.263201] iwlwifi 0000:05:00.0: Failed to run INIT ucode: -5
[    3.275566] iwlwifi 0000:05:00.0: retry init count 0
[    3.275947] iwlwifi 0000:05:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420
[    3.439505] iwlwifi 0000:05:00.0: Microcode SW error detected. Restarting 0x0.
[    3.439701] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    3.439718] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 6
[    3.439738] iwlwifi 0000:05:00.0: Loaded firmware version: 62.49eeb572.0 ty-a0-gf-a0-62.ucode
[    3.439762] iwlwifi 0000:05:00.0: 0x00000071 | NMI_INTERRUPT_UMAC_FATAL    
[    3.439782] iwlwifi 0000:05:00.0: 0x002002F0 | trm_hw_status0
[    3.439798] iwlwifi 0000:05:00.0: 0x00000000 | trm_hw_status1
[    3.439814] iwlwifi 0000:05:00.0: 0x004DA02C | branchlink2
[    3.439830] iwlwifi 0000:05:00.0: 0x004D070E | interruptlink1
[    3.439846] iwlwifi 0000:05:00.0: 0x004D070E | interruptlink2
[    3.439862] iwlwifi 0000:05:00.0: 0x004D8E06 | data1
[    3.439877] iwlwifi 0000:05:00.0: 0x00000010 | data2
[    3.439891] iwlwifi 0000:05:00.0: 0x00000000 | data3
[    3.439905] iwlwifi 0000:05:00.0: 0x00000000 | beacon time
[    3.439921] iwlwifi 0000:05:00.0: 0x000122D7 | tsf low
[    3.439947] iwlwifi 0000:05:00.0: 0x00000000 | tsf hi
[    3.439973] iwlwifi 0000:05:00.0: 0x00000000 | time gp1
[    3.439988] iwlwifi 0000:05:00.0: 0x00026309 | time gp2
[    3.440015] iwlwifi 0000:05:00.0: 0x00000001 | uCode revision type
[    3.440033] iwlwifi 0000:05:00.0: 0x0000003E | uCode version major
[    3.440051] iwlwifi 0000:05:00.0: 0x49EEB572 | uCode version minor
[    3.440600] iwlwifi 0000:05:00.0: 0x00000420 | hw version
[    3.441154] iwlwifi 0000:05:00.0: 0x18C89002 | board version
[    3.442215] iwlwifi 0000:05:00.0: 0x8008FF00 | hcmd
[    3.443112] iwlwifi 0000:05:00.0: 0x00020000 | isr0
[    3.444160] iwlwifi 0000:05:00.0: 0x60000000 | isr1
[    3.445190] iwlwifi 0000:05:00.0: 0x58F00002 | isr2
[    3.446160] iwlwifi 0000:05:00.0: 0x00C0001C | isr3
[    3.446847] iwlwifi 0000:05:00.0: 0x00000000 | isr4
[    3.447410] iwlwifi 0000:05:00.0: 0x00000000 | last cmd Id
[    3.447411] iwlwifi 0000:05:00.0: 0x004D8E06 | wait_event
[    3.447412] iwlwifi 0000:05:00.0: 0x00000000 | l2p_control
[    3.447413] iwlwifi 0000:05:00.0: 0x00000020 | l2p_duration
[    3.447414] iwlwifi 0000:05:00.0: 0x00000000 | l2p_mhvalid
[    3.447414] iwlwifi 0000:05:00.0: 0x00000000 | l2p_addr_match
[    3.447415] iwlwifi 0000:05:00.0: 0x00000009 | lmpm_pmg_sel
[    3.447416] iwlwifi 0000:05:00.0: 0x00000000 | timestamp
[    3.447417] iwlwifi 0000:05:00.0: 0x00000024 | flow_handler
[    3.447468] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    3.453780] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 7
[    3.454634] iwlwifi 0000:05:00.0: 0x2010070D | ADVANCED_SYSASSERT
[    3.455142] iwlwifi 0000:05:00.0: 0x00000000 | umac branchlink1
[    3.455575] iwlwifi 0000:05:00.0: 0x8045C7E4 | umac branchlink2
[    3.456126] iwlwifi 0000:05:00.0: 0x0108D0B2 | umac interruptlink1
[    3.456573] iwlwifi 0000:05:00.0: 0x00000000 | umac interruptlink2
[    3.457016] iwlwifi 0000:05:00.0: 0x00000005 | umac data1
[    3.457519] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data2
[    3.457521] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data3
[    3.457523] iwlwifi 0000:05:00.0: 0x0000003E | umac major
[    3.457524] iwlwifi 0000:05:00.0: 0x49EEB572 | umac minor
[    3.457537] iwlwifi 0000:05:00.0: 0x00026301 | frame pointer
[    3.457539] iwlwifi 0000:05:00.0: 0xC0885E90 | stack pointer
[    3.457540] iwlwifi 0000:05:00.0: 0x00010C00 | last host cmd
[    3.457542] iwlwifi 0000:05:00.0: 0x00000000 | isr status reg
[    3.457578] iwlwifi 0000:05:00.0: IML/ROM dump:
[    3.462236] iwlwifi 0000:05:00.0: 0x00000B03 | IML/ROM error/state
[    3.462290] iwlwifi 0000:05:00.0: 0x000080AB | IML/ROM data1
[    3.462995] iwlwifi 0000:05:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[    3.463375] iwlwifi 0000:05:00.0: Fseq Registers:
[    3.463748] iwlwifi 0000:05:00.0: 0x60000100 | FSEQ_ERROR_CODE
[    3.464224] iwlwifi 0000:05:00.0: 0x80440003 | FSEQ_TOP_INIT_VERSION
[    3.464615] iwlwifi 0000:05:00.0: 0x00070008 | FSEQ_CNVIO_INIT_VERSION
[    3.464965] iwlwifi 0000:05:00.0: 0x0000A652 | FSEQ_OTP_VERSION
[    3.465327] iwlwifi 0000:05:00.0: 0x00000002 | FSEQ_TOP_CONTENT_VERSION
[    3.465974] iwlwifi 0000:05:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN
[    3.466607] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVI_ID
[    3.467172] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVR_ID
[    3.467738] iwlwifi 0000:05:00.0: 0x00400410 | CNVI_AUX_MISC_CHIP
[    3.468148] iwlwifi 0000:05:00.0: 0x00400410 | CNVR_AUX_MISC_CHIP
[    3.468484] iwlwifi 0000:05:00.0: 0x00009061 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    3.468837] iwlwifi 0000:05:00.0: 0x00000061 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    3.469221] iwlwifi 0000:05:00.0: WRT: Collecting data: ini trigger 13 fired (delay=0ms).
[    4.246216] iwlwifi 0000:05:00.0: Failed to run INIT ucode: -5
[    4.258498] iwlwifi 0000:05:00.0: retry init count 1
[    4.258753] iwlwifi 0000:05:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420
[    4.661488] iwlwifi 0000:05:00.0: Microcode SW error detected. Restarting 0x0.
[    4.661580] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    4.661581] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 6
[    4.661583] iwlwifi 0000:05:00.0: Loaded firmware version: 62.49eeb572.0 ty-a0-gf-a0-62.ucode
[    4.661585] iwlwifi 0000:05:00.0: 0x00000071 | NMI_INTERRUPT_UMAC_FATAL    
[    4.661587] iwlwifi 0000:05:00.0: 0x002002F0 | trm_hw_status0
[    4.661588] iwlwifi 0000:05:00.0: 0x00000000 | trm_hw_status1
[    4.661589] iwlwifi 0000:05:00.0: 0x004DA02C | branchlink2
[    4.661590] iwlwifi 0000:05:00.0: 0x004D070E | interruptlink1
[    4.661592] iwlwifi 0000:05:00.0: 0x004D070E | interruptlink2
[    4.661593] iwlwifi 0000:05:00.0: 0x004D8E06 | data1
[    4.661594] iwlwifi 0000:05:00.0: 0x00000010 | data2
[    4.661595] iwlwifi 0000:05:00.0: 0x00000000 | data3
[    4.661596] iwlwifi 0000:05:00.0: 0x00000000 | beacon time
[    4.661597] iwlwifi 0000:05:00.0: 0x0001231E | tsf low
[    4.661599] iwlwifi 0000:05:00.0: 0x00000000 | tsf hi
[    4.661600] iwlwifi 0000:05:00.0: 0x00000000 | time gp1
[    4.661601] iwlwifi 0000:05:00.0: 0x00026352 | time gp2
[    4.661602] iwlwifi 0000:05:00.0: 0x00000001 | uCode revision type
[    4.661603] iwlwifi 0000:05:00.0: 0x0000003E | uCode version major
[    4.661604] iwlwifi 0000:05:00.0: 0x49EEB572 | uCode version minor
[    4.661606] iwlwifi 0000:05:00.0: 0x00000420 | hw version
[    4.661607] iwlwifi 0000:05:00.0: 0x18C89002 | board version
[    4.661608] iwlwifi 0000:05:00.0: 0x8008FF00 | hcmd
[    4.661609] iwlwifi 0000:05:00.0: 0x00020000 | isr0
[    4.661610] iwlwifi 0000:05:00.0: 0x60000000 | isr1
[    4.661612] iwlwifi 0000:05:00.0: 0x58F00002 | isr2
[    4.661613] iwlwifi 0000:05:00.0: 0x00C0001C | isr3
[    4.661614] iwlwifi 0000:05:00.0: 0x00000000 | isr4
[    4.661615] iwlwifi 0000:05:00.0: 0x00000000 | last cmd Id
[    4.661616] iwlwifi 0000:05:00.0: 0x004D8E06 | wait_event
[    4.661617] iwlwifi 0000:05:00.0: 0x00000000 | l2p_control
[    4.661618] iwlwifi 0000:05:00.0: 0x00000020 | l2p_duration
[    4.661619] iwlwifi 0000:05:00.0: 0x00000000 | l2p_mhvalid
[    4.661620] iwlwifi 0000:05:00.0: 0x00000000 | l2p_addr_match
[    4.661622] iwlwifi 0000:05:00.0: 0x00000009 | lmpm_pmg_sel
[    4.661623] iwlwifi 0000:05:00.0: 0x00000000 | timestamp
[    4.661624] iwlwifi 0000:05:00.0: 0x00000024 | flow_handler
[    4.661663] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[    4.661664] iwlwifi 0000:05:00.0: Transport status: 0x0000004A, valid: 7
[    4.661666] iwlwifi 0000:05:00.0: 0x2010070D | ADVANCED_SYSASSERT
[    4.661667] iwlwifi 0000:05:00.0: 0x00000000 | umac branchlink1
[    4.661668] iwlwifi 0000:05:00.0: 0x8045C7E4 | umac branchlink2
[    4.661669] iwlwifi 0000:05:00.0: 0x0108D0B2 | umac interruptlink1
[    4.661671] iwlwifi 0000:05:00.0: 0x00000000 | umac interruptlink2
[    4.661672] iwlwifi 0000:05:00.0: 0x00000005 | umac data1
[    4.661673] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data2
[    4.661674] iwlwifi 0000:05:00.0: 0xDEADBEEF | umac data3
[    4.661675] iwlwifi 0000:05:00.0: 0x0000003E | umac major
[    4.661676] iwlwifi 0000:05:00.0: 0x49EEB572 | umac minor
[    4.661677] iwlwifi 0000:05:00.0: 0x0002634A | frame pointer
[    4.661678] iwlwifi 0000:05:00.0: 0xC0885E90 | stack pointer
[    4.661680] iwlwifi 0000:05:00.0: 0x00010C00 | last host cmd
[    4.661681] iwlwifi 0000:05:00.0: 0x00000000 | isr status reg
[    4.661698] iwlwifi 0000:05:00.0: IML/ROM dump:
[    4.661699] iwlwifi 0000:05:00.0: 0x00000B03 | IML/ROM error/state
[    4.661713] iwlwifi 0000:05:00.0: 0x000080AB | IML/ROM data1
[    4.661723] iwlwifi 0000:05:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[    4.661729] iwlwifi 0000:05:00.0: Fseq Registers:
[    4.661735] iwlwifi 0000:05:00.0: 0x60000100 | FSEQ_ERROR_CODE
[    4.661742] iwlwifi 0000:05:00.0: 0x80440003 | FSEQ_TOP_INIT_VERSION
[    4.661748] iwlwifi 0000:05:00.0: 0x00070008 | FSEQ_CNVIO_INIT_VERSION
[    4.661755] iwlwifi 0000:05:00.0: 0x0000A652 | FSEQ_OTP_VERSION
[    4.661761] iwlwifi 0000:05:00.0: 0x00000002 | FSEQ_TOP_CONTENT_VERSION
[    4.661767] iwlwifi 0000:05:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN
[    4.661774] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVI_ID
[    4.661780] iwlwifi 0000:05:00.0: 0x00400410 | FSEQ_CNVR_ID
[    4.661786] iwlwifi 0000:05:00.0: 0x00400410 | CNVI_AUX_MISC_CHIP
[    4.661793] iwlwifi 0000:05:00.0: 0x00400410 | CNVR_AUX_MISC_CHIP
[    4.661799] iwlwifi 0000:05:00.0: 0x00009061 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    4.661806] iwlwifi 0000:05:00.0: 0x00000061 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    4.661844] iwlwifi 0000:05:00.0: WRT: Collecting data: ini trigger 13 fired (delay=0ms).
[    5.423198] iwlwifi 0000:05:00.0: Failed to run INIT ucode: -5
[    5.435472] iwlwifi 0000:05:00.0: retry init count 2


```

```
root@Ubuntu:/home/junior# ls -al /usr/lib/firmware/iwlwifi-ty-a0-gf-a0-66.ucode
-rw-r--r-- 1 root root 9859197 mar 24 15:55 /usr/lib/firmware/iwlwifi-ty-a0-gf-a0-66.ucode


```

---

### Post by chili555 on 2022-03-24
Let's see:

```
ls -al /usr/lib/firmware/iwlwifi-ty-a0-gf-a0-*
```

For reference, here is the result from my machine:

```
-rw-r--r-- 1 root root 1413868 Feb 18 09:22 /usr/lib/firmware/iwlwifi-ty-a0-gf-a0-59.ucode
-rw-r--r-- 1 root root 1455104 Feb 18 09:22 /usr/lib/firmware/iwlwifi-ty-a0-gf-a0-62.ucode
-rw-r--r-- 1 root root 1460012 Feb 18 09:22 /usr/lib/firmware/iwlwifi-ty-a0-gf-a0-63.ucode
-rw-r--r-- 1 root root 1477864 Feb 18 09:22 /usr/lib/firmware/iwlwifi-ty-a0-gf-a0-66.ucode

```
Your -66.ucode inexplicably has size 9859197.

---

