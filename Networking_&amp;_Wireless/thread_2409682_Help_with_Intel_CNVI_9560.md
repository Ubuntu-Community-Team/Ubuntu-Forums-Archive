---
title: "Help with Intel CNVI 9560"
date: 2019-01-05
forum: Networking &amp; Wireless
---

### Post by Fong_Wee_Kim on 2019-01-05
Hi,

I just installed  Ubuntu 18.04. It doesn't detect my WiFi adapter (Intel CNVI 9560). 

This problem doesn't happen in Win10. Any ideas?

I ran dmesg | grep iwl
```

[    6.130762] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[    6.141173] iwlwifi 0000:00:14.3: loaded firmware version 34.0.0 op_mode iwlmvm
[    6.183949] iwlwifi 0000:00:14.3: Detected Intel(R) Dual Band Wireless AC 9560, REV=0x318
[    6.190560] kernel BUG at /build/linux-vxxS7y/linux-4.15.0/drivers/net/wireless/intel/iwlwifi/pcie/rx.c:425!
[    6.190565] Modules linked in: kvm(+) snd_hda_core snd_hwdep iwlmvm(+) irqbypass snd_pcm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel mac80211 pcbc snd_seq_midi snd_seq_midi_event aesni_intel snd_rawmidi btusb aes_x86_64 crypto_simd iwlwifi glue_helper cryptd input_leds btrtl snd_seq btbcm intel_cstate btintel joydev snd_seq_device intel_rapl_perf bluetooth snd_timer snd ecdh_generic wmi_bmof intel_wmi_thunderbolt soundcore cfg80211 mei_me mei shpchp intel_pch_thermal acpi_pad mac_hid sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid i915 mxm_wmi drm_kms_helper igb syscopyarea sysfillrect sysimgblt dca fb_sys_fops e1000e i2c_algo_bit nvme drm ptp ahci i2c_i801 nvme_core pps_core libahci wmi video
[    6.190590] RIP: 0010:iwl_pcie_rxq_alloc_rbs+0x1d0/0x1f0 [iwlwifi]
[    6.190604]  _iwl_pcie_rx_init+0x252/0x710 [iwlwifi]
[    6.190607]  iwl_pcie_rx_init+0x2d/0x3c0 [iwlwifi]
[    6.190613]  ? iwl_mvm_nic_config+0xeb/0x120 [iwlmvm]
[    6.190617]  iwl_trans_pcie_start_fw+0x2a1/0x6c0 [iwlwifi]
[    6.190621]  iwl_mvm_load_ucode_wait_alive+0xec/0x2b0 [iwlmvm]
[    6.190626]  iwl_run_init_mvm_ucode+0x8e/0x330 [iwlmvm]
[    6.190629]  ? iwl_run_init_mvm_ucode+0x8e/0x330 [iwlmvm]
[    6.190632]  ? iwl_wait_init_complete+0x20/0x20 [iwlmvm]
[    6.190636]  iwl_op_mode_mvm_start+0x649/0x920 [iwlmvm]
[    6.190639]  ? iwl_op_mode_mvm_start+0x649/0x920 [iwlmvm]
[    6.190642]  _iwl_op_mode_start.isra.10+0x4c/0xa0 [iwlwifi]
[    6.190644]  iwl_opmode_register+0x75/0xe0 [iwlwifi]
[    6.190648]  iwl_mvm_init+0x38/0x1000 [iwlmvm]
[    6.190692] RIP: iwl_pcie_rxq_alloc_rbs+0x1d0/0x1f0 [iwlwifi] RSP: ffffb01b4400f8a8

```

---

### Post by chili555 on 2019-01-05
Please see: [https://askubuntu.com/questions/1107172/help-with-wifi-adapter-for-ubuntu-18-04/1107242#1107242](https://askubuntu.com/questions/1107172/help-with-wifi-adapter-for-ubuntu-18-04/1107242#1107242)

---

