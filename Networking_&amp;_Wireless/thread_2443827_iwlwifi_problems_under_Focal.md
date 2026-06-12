---
title: "iwlwifi problems under Focal"
date: 2020-05-20
forum: Networking &amp; Wireless
---

### Post by rgaddi on 2020-05-20
I recently upgraded to Focal, and having problems with my PCIe Wi-Fi adapter.  I had an Intel 7260, and when that was giving me problems I picked up an Asus card with an Intel 9260 chip.  Same behavior.

My connection to a 2.4GHz network is semi-stable, but seems to have a lot of weird lags.  I can't connect to my 5GHz network.  I believe (but can't be sure) that the 5GHz behavior was happening under Eoan, but the 2.4 is new and severe.  Loading this page, for instance, took minutes.  My SSH connection to my router has noticable keystroke lag.

When the 5GHz connection fails, I get the following in dmesg

```
[ 6526.413520] wlp7s0: authenticate with 60:e3:27:5d:fa:98
[ 6526.414599] iwlwifi 0000:07:00.0: Microcode SW error detected. Restarting 0x0.
[ 6526.414706] iwlwifi 0000:07:00.0: Start IWL Error Log Dump:
[ 6526.414708] iwlwifi 0000:07:00.0: Status: 0x00000040, count: 6
[ 6526.414710] iwlwifi 0000:07:00.0: Loaded firmware version: 46.6bf1df06.0 9260-th-b0-jf-b0-46.ucode
[ 6526.414713] iwlwifi 0000:07:00.0: 0x000014FD | ADVANCED_SYSASSERT          
[ 6526.414714] iwlwifi 0000:07:00.0: 0x000022F0 | trm_hw_status0
[ 6526.414716] iwlwifi 0000:07:00.0: 0x00000000 | trm_hw_status1
[ 6526.414718] iwlwifi 0000:07:00.0: 0x0048853E | branchlink2
[ 6526.414719] iwlwifi 0000:07:00.0: 0x00479392 | interruptlink1
[ 6526.414721] iwlwifi 0000:07:00.0: 0x00000000 | interruptlink2
[ 6526.414723] iwlwifi 0000:07:00.0: 0x00000076 | data1
[ 6526.414724] iwlwifi 0000:07:00.0: 0xDEADBEEF | data2
[ 6526.414726] iwlwifi 0000:07:00.0: 0xDEADBEEF | data3
[ 6526.414727] iwlwifi 0000:07:00.0: 0x003751C2 | beacon time
[ 6526.414729] iwlwifi 0000:07:00.0: 0x00968225 | tsf low
[ 6526.414730] iwlwifi 0000:07:00.0: 0x00000000 | tsf hi
[ 6526.414732] iwlwifi 0000:07:00.0: 0x00000000 | time gp1
[ 6526.414733] iwlwifi 0000:07:00.0: 0x00968226 | time gp2
[ 6526.414734] iwlwifi 0000:07:00.0: 0x00000001 | uCode revision type
[ 6526.414736] iwlwifi 0000:07:00.0: 0x0000002E | uCode version major
[ 6526.414737] iwlwifi 0000:07:00.0: 0x6BF1DF06 | uCode version minor
[ 6526.414739] iwlwifi 0000:07:00.0: 0x00000321 | hw version
[ 6526.414740] iwlwifi 0000:07:00.0: 0x00C89004 | board version
[ 6526.414742] iwlwifi 0000:07:00.0: 0x8031F405 | hcmd
[ 6526.414744] iwlwifi 0000:07:00.0: 0x00022080 | isr0
[ 6526.414745] iwlwifi 0000:07:00.0: 0x00000000 | isr1
[ 6526.414747] iwlwifi 0000:07:00.0: 0x08201802 | isr2
[ 6526.414749] iwlwifi 0000:07:00.0: 0x00400080 | isr3
[ 6526.414750] iwlwifi 0000:07:00.0: 0x00000000 | isr4
[ 6526.414752] iwlwifi 0000:07:00.0: 0x003301A9 | last cmd Id
[ 6526.414754] iwlwifi 0000:07:00.0: 0x0001A836 | wait_event
[ 6526.414756] iwlwifi 0000:07:00.0: 0x00000000 | l2p_control
[ 6526.414757] iwlwifi 0000:07:00.0: 0x00000000 | l2p_duration
[ 6526.414759] iwlwifi 0000:07:00.0: 0x00000000 | l2p_mhvalid
[ 6526.414761] iwlwifi 0000:07:00.0: 0x00000000 | l2p_addr_match
[ 6526.414763] iwlwifi 0000:07:00.0: 0x0000008F | lmpm_pmg_sel
[ 6526.414765] iwlwifi 0000:07:00.0: 0x08081424 | timestamp
[ 6526.414767] iwlwifi 0000:07:00.0: 0x00003058 | flow_handler
[ 6526.414810] iwlwifi 0000:07:00.0: Start IWL Error Log Dump:
[ 6526.414812] iwlwifi 0000:07:00.0: Status: 0x00000040, count: 7
[ 6526.414815] iwlwifi 0000:07:00.0: 0x20000070 | NMI_INTERRUPT_LMAC_FATAL
[ 6526.414817] iwlwifi 0000:07:00.0: 0x00000000 | umac branchlink1
[ 6526.414819] iwlwifi 0000:07:00.0: 0xC008888E | umac branchlink2
[ 6526.414821] iwlwifi 0000:07:00.0: 0xC0084414 | umac interruptlink1
[ 6526.414823] iwlwifi 0000:07:00.0: 0xC0084414 | umac interruptlink2
[ 6526.414825] iwlwifi 0000:07:00.0: 0x00000800 | umac data1
[ 6526.414827] iwlwifi 0000:07:00.0: 0xC0084414 | umac data2
[ 6526.414829] iwlwifi 0000:07:00.0: 0xDEADBEEF | umac data3
[ 6526.414831] iwlwifi 0000:07:00.0: 0x0000002E | umac major
[ 6526.414833] iwlwifi 0000:07:00.0: 0x6BF1DF06 | umac minor
[ 6526.414834] iwlwifi 0000:07:00.0: 0x00968238 | frame pointer
[ 6526.414836] iwlwifi 0000:07:00.0: 0xC088627C | stack pointer
[ 6526.414838] iwlwifi 0000:07:00.0: 0x00340108 | last host cmd
[ 6526.414840] iwlwifi 0000:07:00.0: 0x00000000 | isr status reg
[ 6526.414849] iwlwifi 0000:07:00.0: Fseq Registers:
[ 6526.414854] iwlwifi 0000:07:00.0: 0x8022F72A | FSEQ_ERROR_CODE
[ 6526.414860] iwlwifi 0000:07:00.0: 0x00000000 | FSEQ_TOP_INIT_VERSION
[ 6526.414864] iwlwifi 0000:07:00.0: 0x9A9A7FA2 | FSEQ_CNVIO_INIT_VERSION
[ 6526.414869] iwlwifi 0000:07:00.0: 0x0000A371 | FSEQ_OTP_VERSION
[ 6526.414874] iwlwifi 0000:07:00.0: 0xA5F305A6 | FSEQ_TOP_CONTENT_VERSION
[ 6526.414878] iwlwifi 0000:07:00.0: 0x67DA49DB | FSEQ_ALIVE_TOKEN
[ 6526.414882] iwlwifi 0000:07:00.0: 0xA44ED806 | FSEQ_CNVI_ID
[ 6526.414886] iwlwifi 0000:07:00.0: 0xC0A64A0B | FSEQ_CNVR_ID
[ 6526.414891] iwlwifi 0000:07:00.0: 0x01000200 | CNVI_AUX_MISC_CHIP
[ 6526.414897] iwlwifi 0000:07:00.0: 0x01300202 | CNVR_AUX_MISC_CHIP
[ 6526.414904] iwlwifi 0000:07:00.0: 0x0000485B | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[ 6526.414961] iwlwifi 0000:07:00.0: 0x0BADCAFE | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[ 6526.414967] iwlwifi 0000:07:00.0: WRT: Collecting data: ini trigger 4 fired.
[ 6526.414972] ieee80211 phy0: Hardware restart was requested
[ 6526.414983] iwlwifi 0000:07:00.0: FW error in SYNC CMD PHY_CONTEXT_CMD
[ 6526.414986] CPU: 9 PID: 1425 Comm: wpa_supplicant Tainted: P           OE     5.4.0-31-generic #35-Ubuntu
[ 6526.414988] Hardware name: System manufacturer System Product Name/PRIME B450M-A, BIOS 0219 06/08/2018
[ 6526.414989] Call Trace:
[ 6526.414996]  dump_stack+0x6d/0x9a
[ 6526.415011]  iwl_trans_pcie_send_hcmd+0x42d/0x440 [iwlwifi]
[ 6526.415015]  ? wait_woken+0x80/0x80
[ 6526.415025]  iwl_trans_send_cmd+0x55/0xc0 [iwlwifi]
[ 6526.415035]  iwl_mvm_send_cmd+0x1f/0x40 [iwlmvm]
[ 6526.415045]  iwl_mvm_send_cmd_pdu+0x51/0x70 [iwlmvm]
[ 6526.415054]  iwl_mvm_phy_ctxt_apply.constprop.0+0x193/0x290 [iwlmvm]
[ 6526.415063]  iwl_mvm_phy_ctxt_changed+0x58/0xb0 [iwlmvm]
[ 6526.415071]  iwl_mvm_change_chanctx+0x10a/0x140 [iwlmvm]
[ 6526.415092]  ieee80211_recalc_chanctx_min_def+0x1c6/0x320 [mac80211]
[ 6526.415112]  ieee80211_assign_vif_chanctx+0x21c/0x420 [mac80211]
[ 6526.415131]  ieee80211_vif_use_channel+0x171/0x280 [mac80211]
[ 6526.415150]  ieee80211_prep_connection+0x69f/0x9a0 [mac80211]
[ 6526.415170]  ieee80211_mgd_auth+0x19d/0x3d0 [mac80211]
[ 6526.415191]  ieee80211_auth+0x18/0x20 [mac80211]
[ 6526.415220]  cfg80211_mlme_auth+0x104/0x210 [cfg80211]
[ 6526.415245]  nl80211_authenticate+0x284/0x2e0 [cfg80211]
[ 6526.415254]  genl_family_rcv_msg+0x1b9/0x470
[ 6526.415259]  ? try_to_wake_up+0x224/0x6a0
[ 6526.415263]  genl_rcv_msg+0x4c/0xa0
[ 6526.415268]  ? _cond_resched+0x19/0x30
[ 6526.415274]  ? genl_family_rcv_msg+0x470/0x470
[ 6526.415282]  netlink_rcv_skb+0x50/0x120
[ 6526.415286]  genl_rcv+0x29/0x40
[ 6526.415290]  netlink_unicast+0x187/0x220
[ 6526.415294]  netlink_sendmsg+0x222/0x3e0
[ 6526.415300]  sock_sendmsg+0x65/0x70
[ 6526.415303]  ____sys_sendmsg+0x212/0x280
[ 6526.415309]  ___sys_sendmsg+0x88/0xd0
[ 6526.415312]  ? sock_do_ioctl+0x47/0x140
[ 6526.415317]  ? __check_object_size+0x4d/0x150
[ 6526.415323]  ? _copy_to_user+0x2c/0x30
[ 6526.415326]  ? sock_ioctl+0x24f/0x3c0
[ 6526.415329]  ? __sys_sendto+0x113/0x190
[ 6526.415336]  ? __cgroup_bpf_run_filter_setsockopt+0xae/0x2c0
[ 6526.415339]  ? _cond_resched+0x19/0x30
[ 6526.415344]  ? aa_sk_perm+0x43/0x170
[ 6526.415348]  __sys_sendmsg+0x5c/0xa0
[ 6526.415354]  __x64_sys_sendmsg+0x1f/0x30
[ 6526.415359]  do_syscall_64+0x57/0x190
[ 6526.415365]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
[ 6526.415370] RIP: 0033:0x7fc09f6675b7
[ 6526.415375] Code: 64 89 02 48 c7 c0 ff ff ff ff eb bb 0f 1f 80 00 00 00 00 f3 0f 1e fa 64 8b 04 25 18 00 00 00 85 c0 75 10 b8 2e 00 00 00 0f 05 <48> 3d 00 f0 ff ff 77 51 c3 48 83 ec 28 89 54 24 1c 48 89 74 24 10
[ 6526.415379] RSP: 002b:00007ffe5a350598 EFLAGS: 00000246 ORIG_RAX: 000000000000002e
[ 6526.415386] RAX: ffffffffffffffda RBX: 000055944eacd5b0 RCX: 00007fc09f6675b7
[ 6526.415389] RDX: 0000000000000000 RSI: 00007ffe5a3505d0 RDI: 0000000000000006
[ 6526.415393] RBP: 000055944eb56b00 R08: 0000000000000004 R09: 00007fc09f72fb80
[ 6526.415396] R10: 00007ffe5a3506a4 R11: 0000000000000246 R12: 000055944eacd4c0
[ 6526.415399] R13: 00007ffe5a3505d0 R14: 00007ffe5a3506a4 R15: 000055944eb0fbe0
[ 6526.415415] iwlwifi 0000:07:00.0: PHY ctxt cmd error. ret=-5
[ 6526.869031] iwlwifi 0000:07:00.0: Failed to send MAC context (action:2): -5
[ 6526.869036] iwlwifi 0000:07:00.0: failed to update MAC 0c:7a:15:ff:dd:b3
[ 6526.869041] iwlwifi 0000:07:00.0: Failed to send MAC context (action:2): -5
[ 6526.869043] iwlwifi 0000:07:00.0: failed to update MAC 0c:7a:15:ff:dd:b3
[ 6526.869127] wlp7s0: failed to insert STA entry for the AP (error -5)
[ 6526.869133] iwlwifi 0000:07:00.0: Failed to send MAC context (action:2): -5
[ 6526.869136] iwlwifi 0000:07:00.0: failed to update MAC 0c:7a:15:ff:dd:b3
[ 6526.869142] iwlwifi 0000:07:00.0: Failed to send binding (action:3): -5
[ 6526.869146] iwlwifi 0000:07:00.0: Failed to send MAC context (action:2): -5
[ 6526.869149] iwlwifi 0000:07:00.0: failed to update MAC 0c:7a:15:ff:dd:b3
[ 6526.869153] iwlwifi 0000:07:00.0: PHY ctxt cmd error. ret=-5

```


All that repeats 5 times before giving up.  Googling around, I see a lot of people talking about this problem on other distros, but they pretty consistently report it as fixed upstream in the kernel at earlier versions than I'm running.

```

$ uname -a
Linux rg 5.4.0-31-generic #35-Ubuntu SMP Thu May 7 20:20:34 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
$ modinfo iwlwifi
filename:       /lib/modules/5.4.0-31-generic/updates/dkms/iwlwifi.ko
version:        iwlwifi-stack-public:master:8324:9176b151
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-7265D-29.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-29.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-36.ucode
firmware:       iwlwifi-8000C-36.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0-46.ucode
firmware:       iwlwifi-9000-pu-b0-jf-b0-46.ucode
firmware:       iwlwifi-SoSnj-a0-gf-a0-55.ucode
firmware:       iwlwifi-SoSnj-a0-gf4-a0-55.ucode
firmware:       iwlwifi-ty-a0-gf-a0-55.ucode
firmware:       iwlwifi-so-a0-gf-a0-55.ucode
firmware:       iwlwifi-so-a0-hr-b0-55.ucode
firmware:       iwlwifi-so-a0-jf-b0-55.ucode
firmware:       iwlwifi-cc-a0-55.ucode
firmware:       iwlwifi-QuQnj-b0-jf-b0-55.ucode
firmware:       iwlwifi-QuZ-a0-jf-b0-55.ucode
firmware:       iwlwifi-QuZ-a0-hr-b0-55.ucode
firmware:       iwlwifi-Qu-b0-jf-b0-55.ucode
firmware:       iwlwifi-Qu-c0-hr-b0-55.ucode
firmware:       iwlwifi-QuQnj-b0-hr-b0-55.ucode
firmware:       iwlwifi-Qu-a0-jf-b0-55.ucode
firmware:       iwlwifi-Qu-a0-hr-a0-55.ucode
srcversion:     429405ECF8888645E7117B9
alias:                                               ...many lines of alias snipped here...
depends:        compat,cfg80211
retpoline:      Y
name:           iwlwifi
vermagic:       5.4.0-31-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         rg Secure Boot Module Signature key
sig_key:        88:66:AA:11:FB:F8:6B:78
sig_hashalgo:   sha512
signature:      69:1C:7E:05:22:0C:F3:93:C4:AC:99:A5:F1:DF:A0:66:59:E0:84:AC:
        22:EE:98:D9:0E:E7:F9:D8:57:D1:86:99:AC:8D:D7:14:7A:ED:E0:EC:
        EA:04:A6:1B:FD:7E:A6:81:9F:00:61:AC:EF:AF:DA:E0:19:AE:D5:8F:
        29:57:1B:C1:D6:75:1E:E5:D0:EB:7E:04:33:AB:EF:7E:B8:6B:16:5E:
        8E:03:80:09:A7:1E:FA:4C:94:DE:7B:8B:92:ED:7E:44:8F:68:EE:41:
        97:5C:8C:DF:CF:B4:1C:BC:E9:E2:B4:9B:79:D6:91:7C:5B:1C:D7:56:
        F5:17:3F:D9:40:F8:E1:35:FE:81:98:84:A5:EE:B0:BE:70:39:83:85:
        CF:30:E1:05:59:5A:E6:7A:2A:BC:0D:3D:D2:83:DD:FA:0C:19:B2:8E:
        08:37:33:B7:BB:4B:93:F8:E5:24:58:11:FF:D8:51:19:36:98:4D:36:
        BF:B0:BA:75:99:B4:8E:AE:E0:D7:F5:19:9F:49:85:D3:E3:59:15:05:
        08:09:1E:52:B5:FF:35:A7:90:80:40:82:9A:31:21:F9:8B:15:A2:E8:
        93:1E:7F:C6:BE:61:1D:62:B6:32:6A:F8:14:9B:99:46:A3:45:48:42:
        DE:A2:35:C5:96:08:20:5D:FF:B9:8B:6D:63:B7:06:B2
parm:           debug:debug output mask (uint)
parm:           xvt_default_mode:xVT is the default operation mode (default: false) (bool)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 2K for AX210 devices, 4K for other devices 1:4K 2:8K 3:12K 4: 2K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           enable_ini:Enable debug INI TLV FW debug infrastructure (default: true (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)
parm:           disable_11ax:Disable HE capabilities (default: false) (bool)
parm:           disable_msix:Disable MSI-X and use MSI instead (default: false) (bool)
parm:           remove_when_gone:Remove dev from PCIe bus if it is deemed inaccessible (default: false) (bool)

```

Anyone have any ideas?

---

### Post by wildmanne39 on 2020-05-20
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by rgaddi on 2020-05-20
Update: I tried updating to the latest stable kernel (5.6.14-050614-generic) from kernel.ubuntu.com and that seems to have fixed the problem.  I'm successfully connected to my 5GHz network.  No problems being reported in dmesg.

---

