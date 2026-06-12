---
title: "WiFi card firmware crash - Intel 7265 on ASUS"
date: 2017-01-23
forum: Networking &amp; Wireless
---

### Post by argentum2f@gmail.com on 2017-01-23
My wifi occasionally crashes - occasionally bringing down the whole system with it. 
 My usual fall backs don't work. I've tried each of the following:
```
 
sudo systemctl restart networking 
sudo service networking restart
sudo ifconfig wlp2s0 down; sudo ifconfig wlp2s0 up

sudo modprobe -r iwlmvm cfg80211 mac80211 iwlwifi 
sudo modprobe  iwlmvm cfg80211 mac80211 iwlwifi 

```
(note - I don't really know what I'm doing with modprobe - just trying anything I could think of.)

I'd like to know how to bring it back up without restarting.
Because the problem freezes the whole system, I'd also like to stop it from happening completely, if possible.

Here's some more information about the problem.
My computer:
ASUS UX303U (Very happy with it, by the way, portability AND specs/price ratio was good - and I need both for work)

I've tried using kernels:
```

linux-image-4.4.0-57-generic              
linux-image-4.4.0-59-generic                              
linux-image-4.8.0-32-generic 

```
```

~$ uname -a
Linux Belgarion 4.8.0-32-generic #34~16.04.1-Ubuntu SMP Tue Dec 13 17:03:41 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:        16.04
Codename:       xenial

```
I've also installed kubuntu-desktop and usually use KDE.

```

$ lspci | grep -i wireless                                             
02:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)

```


```

~$ dmesg | tail -n 83
...
[ 2700.158102] wlp2s0: RX AssocResp from ~:~:28:38:3b:61 (capab=0x1531 status=0 aid=5)
[ 2700.159980] wlp2s0: associated
[ 2700.160020] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[ 2700.225112] wlp2s0: Limiting TX power to 17 (20 - 3) dBm as advertised by 50:60:28:38:3b:61
[ 3430.920416] wlp2s0: deauthenticating from ~:~:28:38:3b:61 by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3434.432136] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3434.535817] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3434.666897] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3438.293111] wlp2s0: authenticate with f4:f5:e8:14:8f:7b
[ 3438.298572] wlp2s0: send auth to ~:f5:e8:14:8f:7b (try 1/3)
[ 3438.306846] wlp2s0: authenticated
[ 3438.308863] wlp2s0: associate with ~:f5:e8:14:8f:7b (try 1/3)
[ 3438.321476] wlp2s0: RX AssocResp from ~:f5:e8:14:8f:7b (capab=0x1411 status=0 aid=3)
[ 3438.326693] wlp2s0: associated
[ 3438.326726] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[ 3438.384447] wlp2s0: Limiting TX power to 30 (30 - 0) dBm as advertised by f4:f5:e8:14:8f:7b
[ 4624.946070] p2p-dev-wlp2s0:  Failed check-sdata-in-driver check, flags: 0x0
[ 4624.946983] wlp2s0: deauthenticating from ~:~:e8:14:8f:7b by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4624.947034] wlp2s0:  Failed check-sdata-in-driver check, flags: 0x4
^ line above repeated a bunch
...
[ 4624.962024] wlp2s0: HW problem - can not stop rx aggregation for f4:f5:e8:14:8f:7b tid 0
[ 4624.962278] wlp2s0:  Failed check-sdata-in-driver check, flags: 0x4
[ 4624.966159] wlp2s0:  Failed check-sdata-in-driver check, flags: 0x4
[ 4624.968119] wlp2s0: failed to remove key (0, f4:f5:e8:14:8f:7b) from hardware (-5)
[ 4624.969033] wlp2s0:  Failed check-sdata-in-driver check, flags: 0x4
^ line above repeated a bunch
...
[ 4624.991097] wlp2s0: failed to remove key (1, ff:ff:ff:ff:ff:ff) from hardware (-5)
[ 4624.991200] wlp2s0:  Failed check-sdata-in-driver check, flags: 0x4
[ 4624.992037] wlp2s0: failed to remove key (2, ff:ff:ff:ff:ff:ff) from hardware (-5)
[ 4624.992575] wlp2s0:  Failed check-sdata-in-driver check, flags: 0x4


```

**EDIT:** 
I believe this only happens after the laptop has been suspended or hibernated, then awakened, though I'm not completely sure on that.
I also tried turning bluetooth off (saw something about that somewhere with this chip), but that didn't seem to help.

---

### Post by argentum2f@gmail.com on 2017-01-29
Should I ask about this elsewhere?
Should I submit it as a bug? If so, how?

---

### Post by praseodym on 2017-01-29
Please check:
```

dmesg | egrep 'iwl|firm'
```

---

### Post by argentum2f@gmail.com on 2017-01-31
```

~$ dmesg | egrep 'iwl|firm'
[    0.976542] [drm] GuC firmware load skipped
[    3.593845] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-24.ucode failed with error -2
[    3.598486] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-23.ucode failed with error -2
[    3.607354] iwlwifi 0000:02:00.0: loaded firmware version 22.361476.0 op_mode iwlmvm
[    3.662697] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[    3.664676] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.665135] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.754336] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.765728] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[    4.596165] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.596973] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.663252] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.663708] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled


```

Note, at this time WiFi is functioning. I can run the command again next time it crashes.

---

### Post by argentum2f@gmail.com on 2017-02-01
Here is the same result after the wifi crash:
```

~$ dmesg | egrep 'iwl|firm'
[    0.976542] [drm] GuC firmware load skipped
[    3.593845] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-24.ucode failed with error -2
[    3.598486] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-23.ucode failed with error -2
[    3.607354] iwlwifi 0000:02:00.0: loaded firmware version 22.361476.0 op_mode iwlmvm
[    3.662697] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[    3.664676] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.665135] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.754336] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.765728] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[    4.596165] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.596973] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.663252] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.663708] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 5919.641269] [drm] GuC firmware load skipped
[ 5920.574217] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[ 5920.690726] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 5920.691325] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 5920.765107] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 5920.765671] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 5920.896234] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[ 7157.259343] [drm] GuC firmware load skipped
[ 7158.289461]  ccm iptable_filter ip_tables x_tables rfcomm bnep binfmt_misc nls_iso8859_1 arc4 snd_soc_skl snd_soc_skl_ipc snd_soc_sst_ipc snd_soc_sst_dsp snd_hda_ext_core snd_soc_sst_match asus_nb_wmi snd_hda_codec_hdmi asus_wmi intel_rapl snd_hda_codec_conexant sparse_keymap snd_soc_core snd_hda_codec_generic mxm_wmi x86_pkg_temp_thermal snd_compress ac97_bus snd_pcm_dmaengine uvcvideo coretemp iwlmvm snd_hda_intel snd_hda_codec videobuf2_vmalloc kvm_intel mac80211 kvm videobuf2_memops videobuf2_v4l2 snd_hda_core snd_hwdep videobuf2_core irqbypass snd_pcm videodev snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul iwlwifi media snd_rawmidi ghash_clmulni_intel aesni_intel aes_x86_64 lrw glue_helper ablk_helper snd_seq cryptd cfg80211 snd_seq_device snd_timer intel_cstate snd intel_rapl_perf
[ 7158.345338] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[ 7158.620411] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 7158.620971] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 7158.692008] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 7158.692576] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 7158.748503] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[ 9740.349629] [drm] GuC firmware load skipped
[ 9741.569634] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[ 9741.698635] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 9741.699383] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 9741.767833] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 9741.768393] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 9741.893782] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[10617.998061] [drm] GuC firmware load skipped
[10618.986607] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[10619.305743] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[10619.381259] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[10619.382135] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[10619.457247] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[10619.458008] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[15114.939941] [drm] GuC firmware load skipped
[15115.738222] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[15116.143261] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[15116.382976] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[15116.383819] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[15116.610828] iwlwifi 0000:02:00.0: Microcode SW error detected.  Restarting 0x2000000.
[15116.610842] iwlwifi 0000:02:00.0: CSR values:
[15116.610849] iwlwifi 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[15116.610938] iwlwifi 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00489200
[15116.611089] iwlwifi 0000:02:00.0:          CSR_INT_COALESCING: 0X00000040
[15116.611147] iwlwifi 0000:02:00.0:                     CSR_INT: 0X00000000
[15116.611203] iwlwifi 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[15116.611260] iwlwifi 0000:02:00.0:           CSR_FH_INT_STATUS: 0X00000000
[15116.611316] iwlwifi 0000:02:00.0:                 CSR_GPIO_IN: 0X00000000
[15116.611373] iwlwifi 0000:02:00.0:                   CSR_RESET: 0X00000000
[15116.611429] iwlwifi 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
[15116.611487] iwlwifi 0000:02:00.0:                  CSR_HW_REV: 0X00000210
[15116.611736] iwlwifi 0000:02:00.0:              CSR_EEPROM_REG: 0Xd55555d5
[15116.611915] iwlwifi 0000:02:00.0:               CSR_EEPROM_GP: 0X00000000
[15116.612070] iwlwifi 0000:02:00.0:              CSR_OTP_GP_REG: 0Xd55555d5
[15116.612225] iwlwifi 0000:02:00.0:                 CSR_GIO_REG: 0X00080042
[15116.612380] iwlwifi 0000:02:00.0:            CSR_GP_UCODE_REG: 0X00000000
[15116.612536] iwlwifi 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[15116.612723] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[15116.612884] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[15116.613062] iwlwifi 0000:02:00.0:                 CSR_LED_REG: 0X00000018
[15116.613228] iwlwifi 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X88373feb
[15116.613423] iwlwifi 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[15116.613589] iwlwifi 0000:02:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[15116.613756] iwlwifi 0000:02:00.0:      CSR_MONITOR_STATUS_REG: 0Xc3b7f757
[15116.613916] iwlwifi 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[15116.614076] iwlwifi 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[15116.614086] iwlwifi 0000:02:00.0: FH register values:
[15116.614354] iwlwifi 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X371de800
[15116.614615] iwlwifi 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X036facf0
[15116.614876] iwlwifi 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000000
[15116.615093] iwlwifi 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00801114
[15116.615355] iwlwifi 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[15116.615647] iwlwifi 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X03030000
[15116.615874] iwlwifi 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[15116.616066] iwlwifi 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[15116.616233] iwlwifi 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[15116.616556] iwlwifi 0000:02:00.0: Start IWL Error Log Dump:
[15116.616567] iwlwifi 0000:02:00.0: Status: 0x00000000, count: 6
[15116.616578] iwlwifi 0000:02:00.0: Loaded firmware version: 22.361476.0
[15116.616590] iwlwifi 0000:02:00.0: 0x00000034 | NMI_INTERRUPT_WDG           
[15116.616600] iwlwifi 0000:02:00.0: 0x000002F0 | trm_hw_status0
[15116.616611] iwlwifi 0000:02:00.0: 0x00000000 | trm_hw_status1
[15116.616620] iwlwifi 0000:02:00.0: 0x0004162E | branchlink2
[15116.616631] iwlwifi 0000:02:00.0: 0x000445D0 | interruptlink1
[15116.616641] iwlwifi 0000:02:00.0: 0x0000B4D8 | interruptlink2
[15116.616650] iwlwifi 0000:02:00.0: 0x00000000 | data1
[15116.616659] iwlwifi 0000:02:00.0: 0x00000002 | data2
[15116.616667] iwlwifi 0000:02:00.0: 0x07030000 | data3
[15116.616675] iwlwifi 0000:02:00.0: 0x003CA7B2 | beacon time
[15116.616684] iwlwifi 0000:02:00.0: 0x0003584C | tsf low
[15116.616692] iwlwifi 0000:02:00.0: 0x00000000 | tsf hi
[15116.616701] iwlwifi 0000:02:00.0: 0x00000000 | time gp1
[15116.616709] iwlwifi 0000:02:00.0: 0x0003584D | time gp2
[15116.616718] iwlwifi 0000:02:00.0: 0x00000000 | uCode revision type
[15116.616727] iwlwifi 0000:02:00.0: 0x00000016 | uCode version major
[15116.616737] iwlwifi 0000:02:00.0: 0x00058404 | uCode version minor
[15116.616743] iwlwifi 0000:02:00.0: 0x00000210 | hw version
[15116.616749] iwlwifi 0000:02:00.0: 0x00489200 | board version
[15116.616766] iwlwifi 0000:02:00.0: 0x0902006A | hcmd
[15116.616774] iwlwifi 0000:02:00.0: 0x02023080 | isr0
[15116.616782] iwlwifi 0000:02:00.0: 0x00000000 | isr1
[15116.616791] iwlwifi 0000:02:00.0: 0x00000002 | isr2
[15116.616801] iwlwifi 0000:02:00.0: 0x404000C0 | isr3
[15116.616810] iwlwifi 0000:02:00.0: 0x00000080 | isr4
[15116.616819] iwlwifi 0000:02:00.0: 0x01800112 | last cmd Id
[15116.616831] iwlwifi 0000:02:00.0: 0x00000000 | wait_event
[15116.616840] iwlwifi 0000:02:00.0: 0x0000172F | l2p_control
[15116.616850] iwlwifi 0000:02:00.0: 0x00000000 | l2p_duration
[15116.616859] iwlwifi 0000:02:00.0: 0x00000000 | l2p_mhvalid
[15116.616870] iwlwifi 0000:02:00.0: 0x00000000 | l2p_addr_match
[15116.616879] iwlwifi 0000:02:00.0: 0x00000007 | lmpm_pmg_sel
[15116.616887] iwlwifi 0000:02:00.0: 0x03071928 | timestamp
[15116.616896] iwlwifi 0000:02:00.0: 0x00340010 | flow_handler
[15116.616976] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -5
[15116.654936] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[15116.655639] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[15116.880470] iwlwifi 0000:02:00.0: Microcode SW error detected.  Restarting 0x2000000.
[15116.880487] iwlwifi 0000:02:00.0: CSR values:
[15116.880494] iwlwifi 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[15116.880579] iwlwifi 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00489200
[15116.880734] iwlwifi 0000:02:00.0:          CSR_INT_COALESCING: 0X00000040
[15116.880888] iwlwifi 0000:02:00.0:                     CSR_INT: 0X00000000
[15116.880944] iwlwifi 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[15116.881001] iwlwifi 0000:02:00.0:           CSR_FH_INT_STATUS: 0X00000000
[15116.881057] iwlwifi 0000:02:00.0:                 CSR_GPIO_IN: 0X00000000
[15116.881114] iwlwifi 0000:02:00.0:                   CSR_RESET: 0X00000000
[15116.881170] iwlwifi 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
[15116.881227] iwlwifi 0000:02:00.0:                  CSR_HW_REV: 0X00000210
[15116.881283] iwlwifi 0000:02:00.0:              CSR_EEPROM_REG: 0Xd55555d5
[15116.881340] iwlwifi 0000:02:00.0:               CSR_EEPROM_GP: 0X00000000
[15116.881396] iwlwifi 0000:02:00.0:              CSR_OTP_GP_REG: 0Xd55555d5
[15116.881453] iwlwifi 0000:02:00.0:                 CSR_GIO_REG: 0X00080042
[15116.881509] iwlwifi 0000:02:00.0:            CSR_GP_UCODE_REG: 0X00000000
[15116.881565] iwlwifi 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[15116.881621] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[15116.881676] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[15116.881732] iwlwifi 0000:02:00.0:                 CSR_LED_REG: 0X00000018
[15116.881788] iwlwifi 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X88373feb
[15116.881845] iwlwifi 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[15116.882002] iwlwifi 0000:02:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[15116.882156] iwlwifi 0000:02:00.0:      CSR_MONITOR_STATUS_REG: 0Xc3b7ff77
[15116.882311] iwlwifi 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[15116.882465] iwlwifi 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[15116.882472] iwlwifi 0000:02:00.0: FH register values:
[15116.882638] iwlwifi 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X371de800
[15116.882805] iwlwifi 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X036facf0
[15116.883021] iwlwifi 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000000
[15116.883188] iwlwifi 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00801114
[15116.883398] iwlwifi 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[15116.883626] iwlwifi 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X03030000
[15116.883847] iwlwifi 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[15116.884058] iwlwifi 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[15116.884273] iwlwifi 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[15116.884878] iwlwifi 0000:02:00.0: Start IWL Error Log Dump:
[15116.884894] iwlwifi 0000:02:00.0: Status: 0x00000000, count: 6
[15116.884901] iwlwifi 0000:02:00.0: Loaded firmware version: 22.361476.0
[15116.884911] iwlwifi 0000:02:00.0: 0x00000034 | NMI_INTERRUPT_WDG           
[15116.884921] iwlwifi 0000:02:00.0: 0x000002F0 | trm_hw_status0
[15116.884931] iwlwifi 0000:02:00.0: 0x00000000 | trm_hw_status1
[15116.884941] iwlwifi 0000:02:00.0: 0x0004162E | branchlink2
[15116.884952] iwlwifi 0000:02:00.0: 0x000445D0 | interruptlink1
[15116.884960] iwlwifi 0000:02:00.0: 0x00005DCA | interruptlink2
[15116.884979] iwlwifi 0000:02:00.0: 0x00000000 | data1
[15116.884987] iwlwifi 0000:02:00.0: 0x00000002 | data2
[15116.884998] iwlwifi 0000:02:00.0: 0x07030000 | data3
[15116.885009] iwlwifi 0000:02:00.0: 0x003CB02C | beacon time
[15116.885017] iwlwifi 0000:02:00.0: 0x00034FD2 | tsf low
[15116.885025] iwlwifi 0000:02:00.0: 0x00000000 | tsf hi
[15116.885033] iwlwifi 0000:02:00.0: 0x00000000 | time gp1
[15116.885041] iwlwifi 0000:02:00.0: 0x00034FD3 | time gp2
[15116.885054] iwlwifi 0000:02:00.0: 0x00000000 | uCode revision type
[15116.885064] iwlwifi 0000:02:00.0: 0x00000016 | uCode version major
[15116.885073] iwlwifi 0000:02:00.0: 0x00058404 | uCode version minor
[15116.885080] iwlwifi 0000:02:00.0: 0x00000210 | hw version
[15116.885089] iwlwifi 0000:02:00.0: 0x00489200 | board version
[15116.885097] iwlwifi 0000:02:00.0: 0x0902006A | hcmd
[15116.885104] iwlwifi 0000:02:00.0: 0x02023080 | isr0
[15116.885110] iwlwifi 0000:02:00.0: 0x00000000 | isr1
[15116.885116] iwlwifi 0000:02:00.0: 0x00000002 | isr2
[15116.885123] iwlwifi 0000:02:00.0: 0x404000C0 | isr3
[15116.885130] iwlwifi 0000:02:00.0: 0x00000080 | isr4
[15116.885139] iwlwifi 0000:02:00.0: 0x01800112 | last cmd Id
[15116.885149] iwlwifi 0000:02:00.0: 0x00000000 | wait_event
[15116.885160] iwlwifi 0000:02:00.0: 0x0000172F | l2p_control
[15116.885167] iwlwifi 0000:02:00.0: 0x00000000 | l2p_duration
[15116.885176] iwlwifi 0000:02:00.0: 0x00000000 | l2p_mhvalid
[15116.885185] iwlwifi 0000:02:00.0: 0x00000000 | l2p_addr_match
[15116.885194] iwlwifi 0000:02:00.0: 0x00000007 | lmpm_pmg_sel
[15116.885203] iwlwifi 0000:02:00.0: 0x03071928 | timestamp
[15116.885210] iwlwifi 0000:02:00.0: 0x00340010 | flow_handler
[15116.885265] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -5

```
It continues repeating  like that. I couldn't post it all.

---

### Post by argentum2f@gmail.com on 2017-02-22
I tried some of the suggestions in the first answer [here]("http://askubuntu.com/questions/616119/unstable-wireless-with-intel-7260-iwlwifi-after-upgrade-to-15-04"), such as disabling 802.11n and dual wifi/bluetooth, and power saving mode. It is talking about a slightly different card, but most of the options seem applicable to this one as well. [s] Something seems to have helped. Or a recent update fixed it? Either way, I haven't had the problem for a week or two. [/s]


[s] If I figure out which one resolved the problem, I'll post back here. [/s]

**EDIT: **Nevermind, still having the same problem. I just had a lucky streak where it didn't happen for a while.

---

