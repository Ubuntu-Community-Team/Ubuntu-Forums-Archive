---
title: "Gigabyte P35K Network problems"
date: 2014-02-09
forum: Networking &amp; Wireless
---

### Post by Jeroen_Buyssens on 2014-02-09
Hello,


I have a P35K with a Intel® Dual Band Wireless-AC 7260.
When I install Ubuntu 13.10 I can't connect to any wireless network, he can see the wireless networs but can't connect to them.
And when I connect a network cxable directly to the laptop it shows connected to network but I don't have a internet connection.


Does anyone has the same problems, and does someone knows a solution for this?


thx

---

### Post by praseodym on 2014-02-09
Please show the terminal outputs of
```

lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
iwconfig
cat /etc/resolv.conf
dmesg | grep iwl
```

---

### Post by Jeroen_Buyssens on 2014-02-10
lspci -nnk | grep -iA2 net
```

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)    Subsystem: Gigabyte Technology Co., Ltd Device [1458:1552]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
    Kernel driver in use: iwlwifi

```


lsmod
```

Module                  Size  Used bydm_crypt               22728  1 
joydev                 17377  0 
arc4                   12608  2 
parport_pc             32701  0 
ppdev                  17671  0 
x86_pkg_temp_thermal    14162  0 
coretemp               13435  0 
kvm_intel             138538  0 
kvm                   431315  1 kvm_intel
rfcomm                 69070  12 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
bnep                   19564  2 
aesni_intel            55624  256 
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20329  130 ghash_clmulni_intel,aesni_intel,ablk_helper
sparse_keymap          13948  0 
snd_hda_codec_realtek    51465  1 
snd_hda_codec_hdmi     41276  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
snd_hda_intel          48171  5 
iwlmvm                161349  0 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
microcode              23518  0 
mac80211              596969  1 iwlmvm
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
psmouse                97626  0 
serio_raw              13413  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
btusb                  28267  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
bluetooth             371874  22 bnep,btusb,rfcomm
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
lpc_ich                21080  0 
iwlwifi               165398  1 iwlmvm
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
cfg80211              479757  3 iwlwifi,mac80211,iwlmvm
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei_me                 18421  0 
soundcore              12680  1 snd
mei                    77692  1 mei_me
mac_hid                13205  0 
nls_iso8859_1          12713  1 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
ext2                   72832  1 
i915                  655752  5 
i2c_algo_bit           13413  1 i915
drm_kms_helper         52651  1 i915
drm                   296739  4 i915,drm_kms_helper
r8169                  67341  0 
ahci                   25819  3 
libahci                31898  1 ahci
mii                    13934  1 r8169
wmi                    19070  0 
video                  19318  1 i915

```


ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 94:de:80:a1:73:06            
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11408 (11.4 KB)  TX bytes:11408 (11.4 KB)


wlan0     Link encap:Ethernet  HWaddr 0c:8b:fd:cc:3c:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113 (113.0 B)  TX bytes:0 (0.0 B)

```


iwconfig
```

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```


cat /etc/resolv.conf
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

```


dmesg | grep iwl
```

[    8.616509] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[    8.616681] iwlwifi 0000:02:00.0: irq 50 for MSI/MSI-X
[    8.620329] iwlwifi 0000:02:00.0: loaded firmware version 22.0.7.0 op_mode iwlmvm
[    8.640082] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    8.640148] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[    8.640293] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[    8.860223] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    9.024465] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[    9.024609] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   59.307280] iwlwifi 0000:02:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   59.307285] iwlwifi 0000:02:00.0: CSR values:
[   59.307287] iwlwifi 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   59.307292] iwlwifi 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00489204
[   59.307297] iwlwifi 0000:02:00.0:          CSR_INT_COALESCING: 0X00000040
[   59.307301] iwlwifi 0000:02:00.0:                     CSR_INT: 0X00000000
[   59.307306] iwlwifi 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[   59.307311] iwlwifi 0000:02:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   59.307315] iwlwifi 0000:02:00.0:                 CSR_GPIO_IN: 0X00000000
[   59.307320] iwlwifi 0000:02:00.0:                   CSR_RESET: 0X00000000
[   59.307324] iwlwifi 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
[   59.307329] iwlwifi 0000:02:00.0:                  CSR_HW_REV: 0X00000144
[   59.307333] iwlwifi 0000:02:00.0:              CSR_EEPROM_REG: 0X00000000
[   59.307337] iwlwifi 0000:02:00.0:               CSR_EEPROM_GP: 0X80000000
[   59.307342] iwlwifi 0000:02:00.0:              CSR_OTP_GP_REG: 0X803a0000
[   59.307347] iwlwifi 0000:02:00.0:                 CSR_GIO_REG: 0X00080044
[   59.307351] iwlwifi 0000:02:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   59.307356] iwlwifi 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   59.307360] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   59.307365] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   59.307369] iwlwifi 0000:02:00.0:                 CSR_LED_REG: 0X00000060
[   59.307374] iwlwifi 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X8821141f
[   59.307378] iwlwifi 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   59.307383] iwlwifi 0000:02:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[   59.307388] iwlwifi 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   59.307392] iwlwifi 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0010
[   59.307393] iwlwifi 0000:02:00.0: FH register values:
[   59.307408] iwlwifi 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X2117b900
[   59.307422] iwlwifi 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X02117ba0
[   59.307436] iwlwifi 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000060
[   59.307450] iwlwifi 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00801114
[   59.307464] iwlwifi 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   59.307478] iwlwifi 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X03030000
[   59.307493] iwlwifi 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   59.307507] iwlwifi 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   59.307521] iwlwifi 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   59.307645] iwlwifi 0000:02:00.0: Start IWL Error Log Dump:
[   59.307647] iwlwifi 0000:02:00.0: Status: 0x00000000, count: 6
[   59.307649] iwlwifi 0000:02:00.0: 0x0000003C | NMI_INTERRUPT_DATA_ACTION_PT
[   59.307650] iwlwifi 0000:02:00.0: 0x259002A0 | uPc
[   59.307652] iwlwifi 0000:02:00.0: 0x00000000 | branchlink1
[   59.307653] iwlwifi 0000:02:00.0: 0x00000C8A | branchlink2
[   59.307654] iwlwifi 0000:02:00.0: 0x00014078 | interruptlink1
[   59.307655] iwlwifi 0000:02:00.0: 0x00000676 | interruptlink2
[   59.307657] iwlwifi 0000:02:00.0: 0x00014D9A | data1
[   59.307658] iwlwifi 0000:02:00.0: 0x00000008 | data2
[   59.307659] iwlwifi 0000:02:00.0: 0x03030000 | data3
[   59.307660] iwlwifi 0000:02:00.0: 0x00000000 | beacon time
[   59.307662] iwlwifi 0000:02:00.0: 0x02FE8F4B | tsf low
[   59.307663] iwlwifi 0000:02:00.0: 0x00000000 | tsf hi
[   59.307664] iwlwifi 0000:02:00.0: 0x00000000 | time gp1
[   59.307665] iwlwifi 0000:02:00.0: 0x02FE8F4B | time gp2
[   59.307666] iwlwifi 0000:02:00.0: 0x00000000 | time gp3
[   59.307668] iwlwifi 0000:02:00.0: 0x00321600 | uCode version
[   59.307669] iwlwifi 0000:02:00.0: 0x00000144 | hw version
[   59.307670] iwlwifi 0000:02:00.0: 0x00489204 | board version
[   59.307671] iwlwifi 0000:02:00.0: 0x0001001C | hcmd
[   59.307673] iwlwifi 0000:02:00.0: 0x26F63800 | isr0
[   59.307674] iwlwifi 0000:02:00.0: 0x01018000 | isr1
[   59.307675] iwlwifi 0000:02:00.0: 0x00000002 | isr2
[   59.307676] iwlwifi 0000:02:00.0: 0x0041FC81 | isr3
[   59.307677] iwlwifi 0000:02:00.0: 0x00000001 | isr4
[   59.307679] iwlwifi 0000:02:00.0: 0x10000112 | isr_pref
[   59.307680] iwlwifi 0000:02:00.0: 0x00014D9A | wait_event
[   59.307681] iwlwifi 0000:02:00.0: 0x000000D0 | l2p_control
[   59.307682] iwlwifi 0000:02:00.0: 0x00018020 | l2p_duration
[   59.307683] iwlwifi 0000:02:00.0: 0x0000003F | l2p_mhvalid
[   59.307685] iwlwifi 0000:02:00.0: 0x000000CF | l2p_addr_match
[   59.307686] iwlwifi 0000:02:00.0: 0x00000005 | lmpm_pmg_sel
[   59.307687] iwlwifi 0000:02:00.0: 0x7626A382 | timestamp
[   59.307688] iwlwifi 0000:02:00.0: 0x00346070 | flow_handler
[   59.308065] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   59.308208] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   59.709298] iwlwifi 0000:02:00.0: No assocation and the time event is over already...
[   61.138438] iwlwifi 0000:02:00.0: No assocation and the time event is over already...
[   61.867877] iwlwifi 0000:02:00.0: Couldn't drain frames for staid 1
[   61.867901] Modules linked in: dm_crypt(F) joydev(F) arc4(F) parport_pc(F) ppdev(F) x86_pkg_temp_thermal coretemp kvm_intel(F) kvm(F) rfcomm crct10dif_pclmul(F) crc32_pclmul(F) ghash_clmulni_intel(F) bnep aesni_intel(F) aes_x86_64(F) lrw(F) gf128mul(F) glue_helper(F) ablk_helper(F) cryptd(F) sparse_keymap snd_hda_codec_realtek snd_hda_codec_hdmi uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev snd_hda_intel iwlmvm snd_hda_codec microcode(F) mac80211 snd_hwdep(F) snd_pcm(F) psmouse(F) serio_raw(F) snd_page_alloc(F) btusb snd_seq_midi(F) snd_seq_midi_event(F) bluetooth snd_rawmidi(F) snd_seq(F) lpc_ich iwlwifi snd_seq_device(F) snd_timer(F) cfg80211 snd(F) mei_me soundcore(F) mei mac_hid nls_iso8859_1(F) lp(F) parport(F) ext2(F) i915 i2c_algo_bit drm_kms_helper drm r8169 ahci(F) libahci(F) mii(F) wmi video(F)
[   65.670160] iwlwifi 0000:02:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   65.670163] iwlwifi 0000:02:00.0: CSR values:
[   65.670165] iwlwifi 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   65.670170] iwlwifi 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00489204
[   65.670175] iwlwifi 0000:02:00.0:          CSR_INT_COALESCING: 0X0000ff40
[   65.670180] iwlwifi 0000:02:00.0:                     CSR_INT: 0X00000000
[   65.670184] iwlwifi 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[   65.670189] iwlwifi 0000:02:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   65.670193] iwlwifi 0000:02:00.0:                 CSR_GPIO_IN: 0X00000000
[   65.670198] iwlwifi 0000:02:00.0:                   CSR_RESET: 0X00000000
[   65.670203] iwlwifi 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
[   65.670207] iwlwifi 0000:02:00.0:                  CSR_HW_REV: 0X00000144
[   65.670212] iwlwifi 0000:02:00.0:              CSR_EEPROM_REG: 0X00000000
[   65.670216] iwlwifi 0000:02:00.0:               CSR_EEPROM_GP: 0X80000000
[   65.670221] iwlwifi 0000:02:00.0:              CSR_OTP_GP_REG: 0X803a0000
[   65.670226] iwlwifi 0000:02:00.0:                 CSR_GIO_REG: 0X00080044
[   65.670230] iwlwifi 0000:02:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   65.670235] iwlwifi 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   65.670239] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   65.670244] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   65.670248] iwlwifi 0000:02:00.0:                 CSR_LED_REG: 0X00000060
[   65.670253] iwlwifi 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X8821141f
[   65.670257] iwlwifi 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   65.670262] iwlwifi 0000:02:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[   65.670266] iwlwifi 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   65.670271] iwlwifi 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0010
[   65.670272] iwlwifi 0000:02:00.0: FH register values:
[   65.670287] iwlwifi 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X2117b900
[   65.670301] iwlwifi 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X02117ba0
[   65.670315] iwlwifi 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000050
[   65.670328] iwlwifi 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[   65.670342] iwlwifi 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   65.670356] iwlwifi 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   65.670370] iwlwifi 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   65.670384] iwlwifi 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   65.670398] iwlwifi 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   65.670523] iwlwifi 0000:02:00.0: Start IWL Error Log Dump:
[   65.670525] iwlwifi 0000:02:00.0: Status: 0x00000000, count: 6
[   65.670526] iwlwifi 0000:02:00.0: 0x00002B00 | ADVANCED_SYSASSERT          
[   65.670528] iwlwifi 0000:02:00.0: 0x000002F0 | uPc
[   65.670529] iwlwifi 0000:02:00.0: 0x00000000 | branchlink1
[   65.670530] iwlwifi 0000:02:00.0: 0x00000C8A | branchlink2
[   65.670531] iwlwifi 0000:02:00.0: 0x00014078 | interruptlink1
[   65.670533] iwlwifi 0000:02:00.0: 0x00000676 | interruptlink2
[   65.670534] iwlwifi 0000:02:00.0: 0x00000001 | data1
[   65.670535] iwlwifi 0000:02:00.0: 0xDEADBEEF | data2
[   65.670536] iwlwifi 0000:02:00.0: 0xDEADBEEF | data3
[   65.670537] iwlwifi 0000:02:00.0: 0x00000000 | beacon time
[   65.670539] iwlwifi 0000:02:00.0: 0x00610051 | tsf low
[   65.670540] iwlwifi 0000:02:00.0: 0x00000000 | tsf hi
[   65.670541] iwlwifi 0000:02:00.0: 0x00000000 | time gp1
[   65.670542] iwlwifi 0000:02:00.0: 0x00610052 | time gp2
[   65.670543] iwlwifi 0000:02:00.0: 0x00000000 | time gp3
[   65.670545] iwlwifi 0000:02:00.0: 0x00321600 | uCode version
[   65.670546] iwlwifi 0000:02:00.0: 0x00000144 | hw version
[   65.670547] iwlwifi 0000:02:00.0: 0x00489204 | board version
[   65.670548] iwlwifi 0000:02:00.0: 0x09310019 | hcmd
[   65.670550] iwlwifi 0000:02:00.0: 0x00022081 | isr0
[   65.670551] iwlwifi 0000:02:00.0: 0x00000000 | isr1
[   65.670552] iwlwifi 0000:02:00.0: 0x00000002 | isr2
[   65.670553] iwlwifi 0000:02:00.0: 0x004000C0 | isr3
[   65.670561] iwlwifi 0000:02:00.0: 0x00000001 | isr4
[   65.670562] iwlwifi 0000:02:00.0: 0x01000112 | isr_pref
[   65.670564] iwlwifi 0000:02:00.0: 0x000255D8 | wait_event
[   65.670569] iwlwifi 0000:02:00.0: 0x0000C1DF | l2p_control
[   65.670574] iwlwifi 0000:02:00.0: 0x00000020 | l2p_duration
[   65.670580] iwlwifi 0000:02:00.0: 0x00000003 | l2p_mhvalid
[   65.670585] iwlwifi 0000:02:00.0: 0x00000010 | l2p_addr_match
[   65.670591] iwlwifi 0000:02:00.0: 0x00000005 | lmpm_pmg_sel
[   65.670597] iwlwifi 0000:02:00.0: 0x17061625 | timestamp
[   65.670602] iwlwifi 0000:02:00.0: 0x00005058 | flow_handler
[   65.670619] iwlwifi 0000:02:00.0: FW error in SYNC CMD REMOVE_STA
[   65.670639] Workqueue: events iwl_mvm_sta_drained_wk [iwlmvm]
[   65.670665]  [<ffffffffa02371ef>] iwl_trans_pcie_send_hcmd+0x53f/0x5d0 [iwlwifi]
[   65.670674]  [<ffffffffa04a7fe2>] iwl_mvm_send_cmd+0x32/0xb0 [iwlmvm]
[   65.670679]  [<ffffffffa04a80a1>] iwl_mvm_send_cmd_pdu+0x41/0x50 [iwlmvm]
[   65.670684]  [<ffffffffa04ab477>] iwl_mvm_rm_sta_common+0x47/0xa0 [iwlmvm]
[   65.670689]  [<ffffffffa04abdb2>] iwl_mvm_sta_drained_wk+0xb2/0x150 [iwlmvm]
[   65.670712] iwlwifi 0000:02:00.0: Failed to remove station. Id=1
[   65.670714] iwlwifi 0000:02:00.0: Couldn't remove sta 1 after it was drained
[   65.671550] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   65.671694] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   65.987636] iwlwifi 0000:02:00.0: No assocation and the time event is over already...
[   67.167176] iwlwifi 0000:02:00.0: No assocation and the time event is over already...
[   67.880598] iwlwifi 0000:02:00.0: Couldn't drain frames for staid 2
[   71.683104] iwlwifi 0000:02:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   71.683114] iwlwifi 0000:02:00.0: CSR values:
[   71.683118] iwlwifi 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   71.683127] iwlwifi 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00489204
[   71.683135] iwlwifi 0000:02:00.0:          CSR_INT_COALESCING: 0X0000ff40
[   71.683142] iwlwifi 0000:02:00.0:                     CSR_INT: 0X00000000
[   71.683149] iwlwifi 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[   71.683156] iwlwifi 0000:02:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   71.683164] iwlwifi 0000:02:00.0:                 CSR_GPIO_IN: 0X00000000
[   71.683171] iwlwifi 0000:02:00.0:                   CSR_RESET: 0X00000000
[   71.683179] iwlwifi 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
[   71.683186] iwlwifi 0000:02:00.0:                  CSR_HW_REV: 0X00000144
[   71.683193] iwlwifi 0000:02:00.0:              CSR_EEPROM_REG: 0X00000000
[   71.683201] iwlwifi 0000:02:00.0:               CSR_EEPROM_GP: 0X80000000
[   71.683208] iwlwifi 0000:02:00.0:              CSR_OTP_GP_REG: 0X803a0000
[   71.683216] iwlwifi 0000:02:00.0:                 CSR_GIO_REG: 0X00080044
[   71.683223] iwlwifi 0000:02:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   71.683230] iwlwifi 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   71.683237] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   71.683244] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   71.683251] iwlwifi 0000:02:00.0:                 CSR_LED_REG: 0X00000060
[   71.683259] iwlwifi 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X8821141f
[   71.683266] iwlwifi 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   71.683273] iwlwifi 0000:02:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[   71.683280] iwlwifi 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   71.683287] iwlwifi 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   71.683291] iwlwifi 0000:02:00.0: FH register values:
[   71.683309] iwlwifi 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X2117b900
[   71.683327] iwlwifi 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X02117ba0
[   71.683344] iwlwifi 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000048
[   71.683361] iwlwifi 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[   71.683378] iwlwifi 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   71.683396] iwlwifi 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   71.683434] iwlwifi 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   71.683453] iwlwifi 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   71.683480] iwlwifi 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   71.683628] iwlwifi 0000:02:00.0: Start IWL Error Log Dump:
[   71.683637] iwlwifi 0000:02:00.0: Status: 0x00000000, count: 6
[   71.683645] iwlwifi 0000:02:00.0: 0x00002B00 | ADVANCED_SYSASSERT          
[   71.683652] iwlwifi 0000:02:00.0: 0x000002B0 | uPc
[   71.683658] iwlwifi 0000:02:00.0: 0x00000000 | branchlink1
[   71.683665] iwlwifi 0000:02:00.0: 0x00000C8A | branchlink2
[   71.683672] iwlwifi 0000:02:00.0: 0x00014078 | interruptlink1
[   71.683679] iwlwifi 0000:02:00.0: 0x00000676 | interruptlink2
[   71.683685] iwlwifi 0000:02:00.0: 0x00000002 | data1
[   71.683692] iwlwifi 0000:02:00.0: 0xDEADBEEF | data2
[   71.683699] iwlwifi 0000:02:00.0: 0xDEADBEEF | data3
[   71.683705] iwlwifi 0000:02:00.0: 0x00000000 | beacon time
[   71.683712] iwlwifi 0000:02:00.0: 0x005B9843 | tsf low
[   71.683718] iwlwifi 0000:02:00.0: 0x00000000 | tsf hi
[   71.683725] iwlwifi 0000:02:00.0: 0x00000000 | time gp1
[   71.683737] iwlwifi 0000:02:00.0: 0x005B9843 | time gp2
[   71.683752] iwlwifi 0000:02:00.0: 0x00000000 | time gp3
[   71.683765] iwlwifi 0000:02:00.0: 0x00321600 | uCode version
[   71.683781] iwlwifi 0000:02:00.0: 0x00000144 | hw version
[   71.683792] iwlwifi 0000:02:00.0: 0x00489204 | board version
[   71.683799] iwlwifi 0000:02:00.0: 0x09310019 | hcmd
[   71.683806] iwlwifi 0000:02:00.0: 0x00022081 | isr0
[   71.683813] iwlwifi 0000:02:00.0: 0x00000000 | isr1
[   71.683819] iwlwifi 0000:02:00.0: 0x00000002 | isr2
[   71.683826] iwlwifi 0000:02:00.0: 0x0040A480 | isr3
[   71.683832] iwlwifi 0000:02:00.0: 0x00000001 | isr4
[   71.683839] iwlwifi 0000:02:00.0: 0x01002112 | isr_pref
[   71.683851] iwlwifi 0000:02:00.0: 0x000255D8 | wait_event
[   71.683865] iwlwifi 0000:02:00.0: 0x00000094 | l2p_control
[   71.683874] iwlwifi 0000:02:00.0: 0x00010020 | l2p_duration
[   71.683879] iwlwifi 0000:02:00.0: 0x0000000F | l2p_mhvalid
[   71.683885] iwlwifi 0000:02:00.0: 0x00000000 | l2p_addr_match
[   71.683891] iwlwifi 0000:02:00.0: 0x00000005 | lmpm_pmg_sel
[   71.683897] iwlwifi 0000:02:00.0: 0x17061625 | timestamp
[   71.683913] iwlwifi 0000:02:00.0: 0x00004858 | flow_handler
[   71.683950] iwlwifi 0000:02:00.0: FW error in SYNC CMD REMOVE_STA
[   71.683997] Workqueue: events iwl_mvm_sta_drained_wk [iwlmvm]
[   71.684093]  [<ffffffffa02371ef>] iwl_trans_pcie_send_hcmd+0x53f/0x5d0 [iwlwifi]
[   71.684127]  [<ffffffffa04a7fe2>] iwl_mvm_send_cmd+0x32/0xb0 [iwlmvm]
[   71.684145]  [<ffffffffa04a80a1>] iwl_mvm_send_cmd_pdu+0x41/0x50 [iwlmvm]
[   71.684164]  [<ffffffffa04ab477>] iwl_mvm_rm_sta_common+0x47/0xa0 [iwlmvm]
[   71.684183]  [<ffffffffa04abdb2>] iwl_mvm_sta_drained_wk+0xb2/0x150 [iwlmvm]
[   71.684274] iwlwifi 0000:02:00.0: Failed to remove station. Id=2
[   71.684282] iwlwifi 0000:02:00.0: Couldn't remove sta 2 after it was drained
[   71.684815] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   71.684982] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   72.001612] iwlwifi 0000:02:00.0: No assocation and the time event is over already...
[   72.872712] iwlwifi 0000:02:00.0: Couldn't drain frames for staid 1
[   76.677516] iwlwifi 0000:02:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   76.677526] iwlwifi 0000:02:00.0: CSR values:
[   76.677530] iwlwifi 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   76.677539] iwlwifi 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00489204
[   76.677547] iwlwifi 0000:02:00.0:          CSR_INT_COALESCING: 0X0000ff40
[   76.677555] iwlwifi 0000:02:00.0:                     CSR_INT: 0X00000000
[   76.677562] iwlwifi 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[   76.677570] iwlwifi 0000:02:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   76.677577] iwlwifi 0000:02:00.0:                 CSR_GPIO_IN: 0X00000000
[   76.677584] iwlwifi 0000:02:00.0:                   CSR_RESET: 0X00000000
[   76.677592] iwlwifi 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
[   76.677599] iwlwifi 0000:02:00.0:                  CSR_HW_REV: 0X00000144
[   76.677607] iwlwifi 0000:02:00.0:              CSR_EEPROM_REG: 0X00000000
[   76.677614] iwlwifi 0000:02:00.0:               CSR_EEPROM_GP: 0X80000000
[   76.677621] iwlwifi 0000:02:00.0:              CSR_OTP_GP_REG: 0X803a0000
[   76.677628] iwlwifi 0000:02:00.0:                 CSR_GIO_REG: 0X00080044
[   76.677636] iwlwifi 0000:02:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   76.677643] iwlwifi 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   76.677649] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   76.677657] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   76.677664] iwlwifi 0000:02:00.0:                 CSR_LED_REG: 0X00000060
[   76.677672] iwlwifi 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X8821141f
[   76.677678] iwlwifi 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   76.677685] iwlwifi 0000:02:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[   76.677693] iwlwifi 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   76.677700] iwlwifi 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   76.677704] iwlwifi 0000:02:00.0: FH register values:
[   76.677721] iwlwifi 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X2117b900
[   76.677738] iwlwifi 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X02117ba0
[   76.677755] iwlwifi 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000040
[   76.677773] iwlwifi 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[   76.677790] iwlwifi 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   76.677808] iwlwifi 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   76.677825] iwlwifi 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   76.677843] iwlwifi 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   76.677860] iwlwifi 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   76.677995] iwlwifi 0000:02:00.0: Start IWL Error Log Dump:
[   76.677999] iwlwifi 0000:02:00.0: Status: 0x00000000, count: 6
[   76.678004] iwlwifi 0000:02:00.0: 0x00002B00 | ADVANCED_SYSASSERT          
[   76.678008] iwlwifi 0000:02:00.0: 0x000002A0 | uPc
[   76.678013] iwlwifi 0000:02:00.0: 0x00000000 | branchlink1
[   76.678016] iwlwifi 0000:02:00.0: 0x00000C8A | branchlink2
[   76.678020] iwlwifi 0000:02:00.0: 0x00014078 | interruptlink1
[   76.678024] iwlwifi 0000:02:00.0: 0x00000676 | interruptlink2
[   76.678027] iwlwifi 0000:02:00.0: 0x00000001 | data1
[   76.678031] iwlwifi 0000:02:00.0: 0xDEADBEEF | data2
[   76.678034] iwlwifi 0000:02:00.0: 0xDEADBEEF | data3
[   76.678038] iwlwifi 0000:02:00.0: 0x00000000 | beacon time
[   76.678042] iwlwifi 0000:02:00.0: 0x004C0E67 | tsf low
[   76.678045] iwlwifi 0000:02:00.0: 0x00000000 | tsf hi
[   76.678049] iwlwifi 0000:02:00.0: 0x00000000 | time gp1
[   76.678052] iwlwifi 0000:02:00.0: 0x004C0E67 | time gp2
[   76.678056] iwlwifi 0000:02:00.0: 0x00000000 | time gp3
[   76.678060] iwlwifi 0000:02:00.0: 0x00321600 | uCode version
[   76.678063] iwlwifi 0000:02:00.0: 0x00000144 | hw version
[   76.678067] iwlwifi 0000:02:00.0: 0x00489204 | board version
[   76.678070] iwlwifi 0000:02:00.0: 0x09300019 | hcmd
[   76.678074] iwlwifi 0000:02:00.0: 0x00022081 | isr0
[   76.678077] iwlwifi 0000:02:00.0: 0x00000000 | isr1
[   76.678081] iwlwifi 0000:02:00.0: 0x00000002 | isr2
[   76.678084] iwlwifi 0000:02:00.0: 0x004050C0 | isr3
[   76.678088] iwlwifi 0000:02:00.0: 0x00000001 | isr4
[   76.678091] iwlwifi 0000:02:00.0: 0x01000112 | isr_pref
[   76.678095] iwlwifi 0000:02:00.0: 0x000255D8 | wait_event
[   76.678099] iwlwifi 0000:02:00.0: 0x00000050 | l2p_control
[   76.678102] iwlwifi 0000:02:00.0: 0x00018020 | l2p_duration
[   76.678106] iwlwifi 0000:02:00.0: 0x0000003F | l2p_mhvalid
[   76.678110] iwlwifi 0000:02:00.0: 0x00000081 | l2p_addr_match
[   76.678113] iwlwifi 0000:02:00.0: 0x00000005 | lmpm_pmg_sel
[   76.678117] iwlwifi 0000:02:00.0: 0x17061625 | timestamp
[   76.678121] iwlwifi 0000:02:00.0: 0x00004048 | flow_handler
[   76.678138] iwlwifi 0000:02:00.0: FW error in SYNC CMD REMOVE_STA
[   76.678174] Workqueue: events iwl_mvm_sta_drained_wk [iwlmvm]
[   76.678240]  [<ffffffffa02371ef>] iwl_trans_pcie_send_hcmd+0x53f/0x5d0 [iwlwifi]
[   76.678264]  [<ffffffffa04a7fe2>] iwl_mvm_send_cmd+0x32/0xb0 [iwlmvm]
[   76.678276]  [<ffffffffa04a80a1>] iwl_mvm_send_cmd_pdu+0x41/0x50 [iwlmvm]
[   76.678289]  [<ffffffffa04ab477>] iwl_mvm_rm_sta_common+0x47/0xa0 [iwlmvm]
[   76.678300]  [<ffffffffa04abdb2>] iwl_mvm_sta_drained_wk+0xb2/0x150 [iwlmvm]
[   76.678360] iwlwifi 0000:02:00.0: Failed to remove station. Id=1
[   76.678364] iwlwifi 0000:02:00.0: Couldn't remove sta 1 after it was drained
[   76.678868] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   76.679023] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   76.995604] iwlwifi 0000:02:00.0: No assocation and the time event is over already...
[   77.896763] iwlwifi 0000:02:00.0: Couldn't drain frames for staid 2
[  105.197383] iwlwifi 0000:02:00.0: Microcode SW error detected.  Restarting 0x2000000.
[  105.197395] iwlwifi 0000:02:00.0: CSR values:
[  105.197401] iwlwifi 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[  105.197410] iwlwifi 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00489204
[  105.197418] iwlwifi 0000:02:00.0:          CSR_INT_COALESCING: 0X0000ff40
[  105.197426] iwlwifi 0000:02:00.0:                     CSR_INT: 0X00000000
[  105.197433] iwlwifi 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[  105.197440] iwlwifi 0000:02:00.0:           CSR_FH_INT_STATUS: 0X00000000
[  105.197447] iwlwifi 0000:02:00.0:                 CSR_GPIO_IN: 0X00000000
[  105.197455] iwlwifi 0000:02:00.0:                   CSR_RESET: 0X00000000
[  105.197462] iwlwifi 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
[  105.197470] iwlwifi 0000:02:00.0:                  CSR_HW_REV: 0X00000144
[  105.197477] iwlwifi 0000:02:00.0:              CSR_EEPROM_REG: 0X00000000
[  105.197485] iwlwifi 0000:02:00.0:               CSR_EEPROM_GP: 0X80000000
[  105.197492] iwlwifi 0000:02:00.0:              CSR_OTP_GP_REG: 0X803a0000
[  105.197499] iwlwifi 0000:02:00.0:                 CSR_GIO_REG: 0X00080044
[  105.197507] iwlwifi 0000:02:00.0:            CSR_GP_UCODE_REG: 0X00000000
[  105.197514] iwlwifi 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[  105.197521] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[  105.197528] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[  105.197536] iwlwifi 0000:02:00.0:                 CSR_LED_REG: 0X00000060
[  105.197543] iwlwifi 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X8821141f
[  105.197550] iwlwifi 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[  105.197557] iwlwifi 0000:02:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[  105.197564] iwlwifi 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[  105.197571] iwlwifi 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[  105.197575] iwlwifi 0000:02:00.0: FH register values:
[  105.197593] iwlwifi 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X2117b900
[  105.197610] iwlwifi 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X02117ba0
[  105.197628] iwlwifi 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000050
[  105.197645] iwlwifi 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[  105.197662] iwlwifi 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[  105.197680] iwlwifi 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[  105.197697] iwlwifi 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[  105.197715] iwlwifi 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[  105.197732] iwlwifi 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[  105.197866] iwlwifi 0000:02:00.0: Start IWL Error Log Dump:
[  105.197871] iwlwifi 0000:02:00.0: Status: 0x00000000, count: 6
[  105.197876] iwlwifi 0000:02:00.0: 0x00002B00 | ADVANCED_SYSASSERT          
[  105.197879] iwlwifi 0000:02:00.0: 0x000002B0 | uPc
[  105.197883] iwlwifi 0000:02:00.0: 0x00000000 | branchlink1
[  105.197887] iwlwifi 0000:02:00.0: 0x00000C8A | branchlink2
[  105.197891] iwlwifi 0000:02:00.0: 0x00014078 | interruptlink1
[  105.197894] iwlwifi 0000:02:00.0: 0x00000676 | interruptlink2
[  105.197898] iwlwifi 0000:02:00.0: 0x00000002 | data1
[  105.197902] iwlwifi 0000:02:00.0: 0xDEADBEEF | data2
[  105.197905] iwlwifi 0000:02:00.0: 0xDEADBEEF | data3
[  105.197909] iwlwifi 0000:02:00.0: 0x00000000 | beacon time
[  105.197913] iwlwifi 0000:02:00.0: 0x01B2B9DC | tsf low
[  105.197916] iwlwifi 0000:02:00.0: 0x00000000 | tsf hi
[  105.197920] iwlwifi 0000:02:00.0: 0x00000000 | time gp1
[  105.197924] iwlwifi 0000:02:00.0: 0x01B2B9DC | time gp2
[  105.197927] iwlwifi 0000:02:00.0: 0x00000000 | time gp3
[  105.197931] iwlwifi 0000:02:00.0: 0x00321600 | uCode version
[  105.197935] iwlwifi 0000:02:00.0: 0x00000144 | hw version
[  105.197938] iwlwifi 0000:02:00.0: 0x00489204 | board version
[  105.197942] iwlwifi 0000:02:00.0: 0x09320019 | hcmd
[  105.197945] iwlwifi 0000:02:00.0: 0x00022081 | isr0
[  105.197949] iwlwifi 0000:02:00.0: 0x00000000 | isr1
[  105.197952] iwlwifi 0000:02:00.0: 0x00000002 | isr2
[  105.197956] iwlwifi 0000:02:00.0: 0x004140C0 | isr3
[  105.197959] iwlwifi 0000:02:00.0: 0x00000001 | isr4
[  105.197963] iwlwifi 0000:02:00.0: 0x01000112 | isr_pref
[  105.197967] iwlwifi 0000:02:00.0: 0x000255D8 | wait_event
[  105.197970] iwlwifi 0000:02:00.0: 0x00000094 | l2p_control
[  105.197974] iwlwifi 0000:02:00.0: 0x00010020 | l2p_duration
[  105.197978] iwlwifi 0000:02:00.0: 0x0000000F | l2p_mhvalid
[  105.197981] iwlwifi 0000:02:00.0: 0x00000000 | l2p_addr_match
[  105.197985] iwlwifi 0000:02:00.0: 0x00000005 | lmpm_pmg_sel
[  105.197989] iwlwifi 0000:02:00.0: 0x17061625 | timestamp
[  105.197992] iwlwifi 0000:02:00.0: 0x00005058 | flow_handler
[  105.198009] iwlwifi 0000:02:00.0: FW error in SYNC CMD REMOVE_STA
[  105.198043] Workqueue: events iwl_mvm_sta_drained_wk [iwlmvm]
[  105.198107]  [<ffffffffa02371ef>] iwl_trans_pcie_send_hcmd+0x53f/0x5d0 [iwlwifi]
[  105.198131]  [<ffffffffa04a7fe2>] iwl_mvm_send_cmd+0x32/0xb0 [iwlmvm]
[  105.198142]  [<ffffffffa04a80a1>] iwl_mvm_send_cmd_pdu+0x41/0x50 [iwlmvm]
[  105.198155]  [<ffffffffa04ab477>] iwl_mvm_rm_sta_common+0x47/0xa0 [iwlmvm]
[  105.198167]  [<ffffffffa04abdb2>] iwl_mvm_sta_drained_wk+0xb2/0x150 [iwlmvm]
[  105.198225] iwlwifi 0000:02:00.0: Failed to remove station. Id=2
[  105.198229] iwlwifi 0000:02:00.0: Couldn't remove sta 2 after it was drained
[  105.198661] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  105.198814] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  105.515454] iwlwifi 0000:02:00.0: No assocation and the time event is over already...
[  105.875307] iwlwifi 0000:02:00.0: Couldn't drain frames for staid 1
[  118.391888] iwlwifi 0000:02:00.0: Microcode SW error detected.  Restarting 0x2000000.
[  118.391897] iwlwifi 0000:02:00.0: CSR values:
[  118.391902] iwlwifi 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[  118.391911] iwlwifi 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00489204
[  118.391918] iwlwifi 0000:02:00.0:          CSR_INT_COALESCING: 0X0000ff40
[  118.391926] iwlwifi 0000:02:00.0:                     CSR_INT: 0X00000000
[  118.391933] iwlwifi 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[  118.391940] iwlwifi 0000:02:00.0:           CSR_FH_INT_STATUS: 0X00000000
[  118.391948] iwlwifi 0000:02:00.0:                 CSR_GPIO_IN: 0X00000000
[  118.391955] iwlwifi 0000:02:00.0:                   CSR_RESET: 0X00000000
[  118.391962] iwlwifi 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
[  118.391969] iwlwifi 0000:02:00.0:                  CSR_HW_REV: 0X00000144
[  118.391977] iwlwifi 0000:02:00.0:              CSR_EEPROM_REG: 0X00000000
[  118.391984] iwlwifi 0000:02:00.0:               CSR_EEPROM_GP: 0X80000000
[  118.391991] iwlwifi 0000:02:00.0:              CSR_OTP_GP_REG: 0X803a0000
[  118.391999] iwlwifi 0000:02:00.0:                 CSR_GIO_REG: 0X00080044
[  118.392006] iwlwifi 0000:02:00.0:            CSR_GP_UCODE_REG: 0X00000000
[  118.392013] iwlwifi 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[  118.392020] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[  118.392027] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[  118.392035] iwlwifi 0000:02:00.0:                 CSR_LED_REG: 0X00000060
[  118.392042] iwlwifi 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X8821141f
[  118.392049] iwlwifi 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[  118.392056] iwlwifi 0000:02:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[  118.392063] iwlwifi 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[  118.392070] iwlwifi 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[  118.392074] iwlwifi 0000:02:00.0: FH register values:
[  118.392091] iwlwifi 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X2117b900
[  118.392109] iwlwifi 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X02117ba0
[  118.392126] iwlwifi 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000048
[  118.392143] iwlwifi 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[  118.392160] iwlwifi 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[  118.392177] iwlwifi 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[  118.392194] iwlwifi 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[  118.392211] iwlwifi 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[  118.392229] iwlwifi 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[  118.392361] iwlwifi 0000:02:00.0: Start IWL Error Log Dump:
[  118.392365] iwlwifi 0000:02:00.0: Status: 0x00000000, count: 6
[  118.392370] iwlwifi 0000:02:00.0: 0x00002B00 | ADVANCED_SYSASSERT          
[  118.392374] iwlwifi 0000:02:00.0: 0x000002A0 | uPc
[  118.392378] iwlwifi 0000:02:00.0: 0x00000000 | branchlink1
[  118.392381] iwlwifi 0000:02:00.0: 0x00000C8A | branchlink2
[  118.392385] iwlwifi 0000:02:00.0: 0x00014078 | interruptlink1
[  118.392389] iwlwifi 0000:02:00.0: 0x00000676 | interruptlink2
[  118.392392] iwlwifi 0000:02:00.0: 0x00000001 | data1
[  118.392396] iwlwifi 0000:02:00.0: 0xDEADBEEF | data2
[  118.392400] iwlwifi 0000:02:00.0: 0xDEADBEEF | data3
[  118.392403] iwlwifi 0000:02:00.0: 0x00000000 | beacon time
[  118.392407] iwlwifi 0000:02:00.0: 0x00C914E1 | tsf low
[  118.392410] iwlwifi 0000:02:00.0: 0x00000000 | tsf hi
[  118.392414] iwlwifi 0000:02:00.0: 0x00000000 | time gp1
[  118.392418] iwlwifi 0000:02:00.0: 0x00C914E1 | time gp2
[  118.392421] iwlwifi 0000:02:00.0: 0x00000000 | time gp3
[  118.392425] iwlwifi 0000:02:00.0: 0x00321600 | uCode version
[  118.392428] iwlwifi 0000:02:00.0: 0x00000144 | hw version
[  118.392432] iwlwifi 0000:02:00.0: 0x00489204 | board version
[  118.392436] iwlwifi 0000:02:00.0: 0x09320019 | hcmd
[  118.392439] iwlwifi 0000:02:00.0: 0x00022081 | isr0
[  118.392443] iwlwifi 0000:02:00.0: 0x00000000 | isr1
[  118.392446] iwlwifi 0000:02:00.0: 0x00000002 | isr2
[  118.392450] iwlwifi 0000:02:00.0: 0x004104C0 | isr3
[  118.392453] iwlwifi 0000:02:00.0: 0x00000001 | isr4
[  118.392457] iwlwifi 0000:02:00.0: 0x01002112 | isr_pref
[  118.392460] iwlwifi 0000:02:00.0: 0x000255D8 | wait_event
[  118.392464] iwlwifi 0000:02:00.0: 0x00000094 | l2p_control
[  118.392468] iwlwifi 0000:02:00.0: 0x00018020 | l2p_duration
[  118.392472] iwlwifi 0000:02:00.0: 0x0000000F | l2p_mhvalid
[  118.392475] iwlwifi 0000:02:00.0: 0x00000000 | l2p_addr_match
[  118.392479] iwlwifi 0000:02:00.0: 0x00000005 | lmpm_pmg_sel
[  118.392483] iwlwifi 0000:02:00.0: 0x17061625 | timestamp
[  118.392486] iwlwifi 0000:02:00.0: 0x00004858 | flow_handler
[  118.392504] iwlwifi 0000:02:00.0: FW error in SYNC CMD REMOVE_STA
[  118.392542] Workqueue: events iwl_mvm_sta_drained_wk [iwlmvm]
[  118.392609]  [<ffffffffa02371ef>] iwl_trans_pcie_send_hcmd+0x53f/0x5d0 [iwlwifi]
[  118.392633]  [<ffffffffa04a7fe2>] iwl_mvm_send_cmd+0x32/0xb0 [iwlmvm]
[  118.392645]  [<ffffffffa04a80a1>] iwl_mvm_send_cmd_pdu+0x41/0x50 [iwlmvm]
[  118.392658]  [<ffffffffa04ab477>] iwl_mvm_rm_sta_common+0x47/0xa0 [iwlmvm]
[  118.392670]  [<ffffffffa04abdb2>] iwl_mvm_sta_drained_wk+0xb2/0x150 [iwlmvm]
[  118.392730] iwlwifi 0000:02:00.0: Failed to remove station. Id=1
[  118.392734] iwlwifi 0000:02:00.0: Couldn't remove sta 1 after it was drained
[  118.393230] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  118.393388] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  118.709992] iwlwifi 0000:02:00.0: No assocation and the time event is over already...
[  119.922606] iwlwifi 0000:02:00.0: Couldn't drain frames for staid 2
[  123.727500] iwlwifi 0000:02:00.0: Microcode SW error detected.  Restarting 0x2000000.
[  123.727512] iwlwifi 0000:02:00.0: CSR values:
[  123.727518] iwlwifi 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[  123.727529] iwlwifi 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00489204
[  123.727540] iwlwifi 0000:02:00.0:          CSR_INT_COALESCING: 0X0000ff40
[  123.727550] iwlwifi 0000:02:00.0:                     CSR_INT: 0X00000000
[  123.727559] iwlwifi 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[  123.727569] iwlwifi 0000:02:00.0:           CSR_FH_INT_STATUS: 0X00000000
[  123.727579] iwlwifi 0000:02:00.0:                 CSR_GPIO_IN: 0X00000000
[  123.727588] iwlwifi 0000:02:00.0:                   CSR_RESET: 0X00000000
[  123.727598] iwlwifi 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
[  123.727607] iwlwifi 0000:02:00.0:                  CSR_HW_REV: 0X00000144
[  123.727617] iwlwifi 0000:02:00.0:              CSR_EEPROM_REG: 0X00000000
[  123.727627] iwlwifi 0000:02:00.0:               CSR_EEPROM_GP: 0X80000000
[  123.727637] iwlwifi 0000:02:00.0:              CSR_OTP_GP_REG: 0X803a0000
[  123.727647] iwlwifi 0000:02:00.0:                 CSR_GIO_REG: 0X00080044
[  123.727657] iwlwifi 0000:02:00.0:            CSR_GP_UCODE_REG: 0X00000000
[  123.727667] iwlwifi 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[  123.727676] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[  123.727687] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[  123.727697] iwlwifi 0000:02:00.0:                 CSR_LED_REG: 0X00000060
[  123.727707] iwlwifi 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X8821141f
[  123.727717] iwlwifi 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[  123.727727] iwlwifi 0000:02:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[  123.727737] iwlwifi 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[  123.727747] iwlwifi 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[  123.727753] iwlwifi 0000:02:00.0: FH register values:
[  123.727773] iwlwifi 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X2117b900
[  123.727794] iwlwifi 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X02117ba0
[  123.727814] iwlwifi 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000040
[  123.727834] iwlwifi 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[  123.727854] iwlwifi 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[  123.727875] iwlwifi 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[  123.727896] iwlwifi 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[  123.727917] iwlwifi 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[  123.727937] iwlwifi 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[  123.728080] iwlwifi 0000:02:00.0: Start IWL Error Log Dump:
[  123.728087] iwlwifi 0000:02:00.0: Status: 0x00000000, count: 6
[  123.728095] iwlwifi 0000:02:00.0: 0x00002B00 | ADVANCED_SYSASSERT          
[  123.728100] iwlwifi 0000:02:00.0: 0x000002B0 | uPc
[  123.728106] iwlwifi 0000:02:00.0: 0x00000000 | branchlink1
[  123.728111] iwlwifi 0000:02:00.0: 0x00000C8A | branchlink2
[  123.728117] iwlwifi 0000:02:00.0: 0x00014078 | interruptlink1
[  123.728123] iwlwifi 0000:02:00.0: 0x00000676 | interruptlink2
[  123.728129] iwlwifi 0000:02:00.0: 0x00000002 | data1
[  123.728136] iwlwifi 0000:02:00.0: 0xDEADBEEF | data2
[  123.728141] iwlwifi 0000:02:00.0: 0xDEADBEEF | data3
[  123.728146] iwlwifi 0000:02:00.0: 0x00000000 | beacon time
[  123.728152] iwlwifi 0000:02:00.0: 0x0051430B | tsf low
[  123.728157] iwlwifi 0000:02:00.0: 0x00000000 | tsf hi
[  123.728163] iwlwifi 0000:02:00.0: 0x00000000 | time gp1
[  123.728168] iwlwifi 0000:02:00.0: 0x0051430B | time gp2
[  123.728173] iwlwifi 0000:02:00.0: 0x00000000 | time gp3
[  123.728179] iwlwifi 0000:02:00.0: 0x00321600 | uCode version
[  123.728186] iwlwifi 0000:02:00.0: 0x00000144 | hw version
[  123.728192] iwlwifi 0000:02:00.0: 0x00489204 | board version
[  123.728198] iwlwifi 0000:02:00.0: 0x09300019 | hcmd
[  123.728205] iwlwifi 0000:02:00.0: 0x00022081 | isr0
[  123.728211] iwlwifi 0000:02:00.0: 0x00000000 | isr1
[  123.728217] iwlwifi 0000:02:00.0: 0x00000002 | isr2
[  123.728223] iwlwifi 0000:02:00.0: 0x004160C0 | isr3
[  123.728229] iwlwifi 0000:02:00.0: 0x00000001 | isr4
[  123.728234] iwlwifi 0000:02:00.0: 0x01000112 | isr_pref
[  123.728240] iwlwifi 0000:02:00.0: 0x000255D8 | wait_event
[  123.728245] iwlwifi 0000:02:00.0: 0x00000094 | l2p_control
[  123.728250] iwlwifi 0000:02:00.0: 0x00010020 | l2p_duration
[  123.728256] iwlwifi 0000:02:00.0: 0x0000000F | l2p_mhvalid
[  123.728262] iwlwifi 0000:02:00.0: 0x00000000 | l2p_addr_match
[  123.728267] iwlwifi 0000:02:00.0: 0x00000005 | lmpm_pmg_sel
[  123.728273] iwlwifi 0000:02:00.0: 0x17061625 | timestamp
[  123.728278] iwlwifi 0000:02:00.0: 0x00004050 | flow_handler
[  123.728307] iwlwifi 0000:02:00.0: FW error in SYNC CMD REMOVE_STA
[  123.728351] Workqueue: events iwl_mvm_sta_drained_wk [iwlmvm]
[  123.728436]  [<ffffffffa02371ef>] iwl_trans_pcie_send_hcmd+0x53f/0x5d0 [iwlwifi]
[  123.728465]  [<ffffffffa04a7fe2>] iwl_mvm_send_cmd+0x32/0xb0 [iwlmvm]
[  123.728482]  [<ffffffffa04a80a1>] iwl_mvm_send_cmd_pdu+0x41/0x50 [iwlmvm]
[  123.728500]  [<ffffffffa04ab477>] iwl_mvm_rm_sta_common+0x47/0xa0 [iwlmvm]
[  123.728517]  [<ffffffffa04abdb2>] iwl_mvm_sta_drained_wk+0xb2/0x150 [iwlmvm]
[  123.728604] iwlwifi 0000:02:00.0: Failed to remove station. Id=2
[  123.728611] iwlwifi 0000:02:00.0: Couldn't remove sta 2 after it was drained
[  123.729097] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  123.729248] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  124.045975] iwlwifi 0000:02:00.0: No assocation and the time event is over already...
[  124.926690] iwlwifi 0000:02:00.0: Couldn't drain frames for staid 1

```

---

### Post by praseodym on 2014-02-10
> Tx-Power=0 dBm  
Your card is off. Any button, switch key or key combination? Also try
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by Jeroen_Buyssens on 2014-02-10
My card is actived with a key-combination. The weird thing is, the wireless networks are detected but I can't connect, he keeps asking for the password.

And when I try 
```
sudo modprobe -rfv iwlwifi
```
I get
```
FATAL: Module iwlwifi is in use.
```

---

### Post by praseodym on 2014-02-10
Doesnt matter. Reboot then and add the NSs as decribed

---

### Post by Jeroen_Buyssens on 2014-02-10
Awesome, I rebooted and it works now thanks alot :D

---

