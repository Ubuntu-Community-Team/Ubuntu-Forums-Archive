---
title: "Intel Centrino Ultimate N 6320 not working Ubuntu 15.04 thru 16.04"
date: 2016-07-08
forum: Networking &amp; Wireless
---

### Post by irinix on 2016-07-08
So, A couple of months ago, I installed 15.04, wifi didn't work out of  the box, so I downloaded the most recent intel firmware, This let the  wifi connect from my live usb, but not from the installed OS. So, I set  my /etc/modprobe.d/iwlwifi.conf as follows:

```

# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

options iwlwifi 11n_disable=8 led_mode=1 bt_coex_active=0 power_save=0

```

This allowed me to see the wireless networks in my area from the installed OS but not connect to any.  

Solving that required me to set my CRDA
```

# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=US

```

And this solved my problem, and got my wifi working.  

Ubuntu auto-updated to 15.10, and wifi worked great up till a couple of  days ago (Roughly 7/4).  At which point it started throwing errors on  boot.  Below is the Dmesg output of iwlwifi:

```

[   13.723237] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   14.367447] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-6000-6.ucode failed with error -2
[   14.369080] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-6000-5.ucode failed with error -2
[   14.862792] iwlwifi 0000:03:00.0: loaded firmware version 9.176.4.1 build 15835 op_mode iwldvm
[   16.207039] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   16.207042] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   16.207043] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   16.207046] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   16.207146] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   17.013177] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[   32.401171] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   32.407590] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   32.638122] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   32.644515] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   32.744606] iwlwifi 0000:03:00.0: Requested user TXPOWER 16 above upper limit 0.
[   39.645718] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   39.645801] iwlwifi 0000:03:00.0: CSR values:
[   39.645849] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   39.645937] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X0048c704
[   39.646017] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[   39.646095] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[   39.646179] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[   39.646260] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   39.646345] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
[   39.646429] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[   39.646507] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[   39.646587] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000074
[   39.646665] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X28360ffd
[   39.646745] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[   39.646829] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X00030001
[   39.646907] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080042
[   39.646991] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00001076
[   39.647073] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   39.647154] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   39.647253] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   39.647355] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000040
[   39.647455] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X880babb7
[   39.647560] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   39.647663] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   39.647761] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X43f7f757
[   39.647862] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   39.647965] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   39.648037] iwlwifi 0000:03:00.0: FH register values:
[   39.648148] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X0b9abd00
[   39.648286] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00b9abe0
[   39.648418] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000088
[   39.648577] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[   39.648790] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   39.648925] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   39.649055] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   39.649192] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   39.649322] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   39.649424] iwlwifi 0000:03:00.0: Loaded firmware version: 9.176.4.1 build 15835
[   39.649681] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[   39.649751] iwlwifi 0000:03:00.0: Status: 0x0000004C, count: 5
[   39.649823] iwlwifi 0000:03:00.0: 0x00000005 | SYSASSERT                   
[   39.649897] iwlwifi 0000:03:00.0: 0x00023D2C | uPc
[   39.649971] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink1
[   39.650047] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink2
[   39.650118] iwlwifi 0000:03:00.0: 0x00000996 | interruptlink1
[   39.650189] iwlwifi 0000:03:00.0: 0x00000000 | interruptlink2
[   39.650265] iwlwifi 0000:03:00.0: 0xFFFFFFC0 | data1
[   39.650334] iwlwifi 0000:03:00.0: 0x0000017C | data2
[   39.650407] iwlwifi 0000:03:00.0: 0x000001DD | line
[   39.650482] iwlwifi 0000:03:00.0: 0x00015382 | beacon time
[   39.650551] iwlwifi 0000:03:00.0: 0x00003C7D | tsf low
[   39.650622] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
[   39.650691] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[   39.650766] iwlwifi 0000:03:00.0: 0x006AB4DB | time gp2
[   39.650838] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[   39.650907] iwlwifi 0000:03:00.0: 0x000109B0 | uCode version
[   39.650982] iwlwifi 0000:03:00.0: 0x00000074 | hw version
[   39.651050] iwlwifi 0000:03:00.0: 0x0048C704 | board version
[   39.651127] iwlwifi 0000:03:00.0: 0x041A0010 | hcmd
[   39.651201] iwlwifi 0000:03:00.0: 0x26E22080 | isr0
[   39.651268] iwlwifi 0000:03:00.0: 0x0103E000 | isr1
[   39.651339] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[   39.651407] iwlwifi 0000:03:00.0: 0x1141FCC1 | isr3
[   39.651480] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[   39.651554] iwlwifi 0000:03:00.0: 0x11800112 | isr_pref
[   39.651623] iwlwifi 0000:03:00.0: 0x0001D5D6 | wait_event
[   39.651692] iwlwifi 0000:03:00.0: 0x00000080 | l2p_control
[   39.651764] iwlwifi 0000:03:00.0: 0x00000000 | l2p_duration
[   39.651839] iwlwifi 0000:03:00.0: 0x0000003F | l2p_mhvalid
[   39.651914] iwlwifi 0000:03:00.0: 0x00200200 | l2p_addr_match
[   39.651986] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
[   39.652060] iwlwifi 0000:03:00.0: 0x25090952 | timestamp
[   39.652129] iwlwifi 0000:03:00.0: 0x00000000 | flow_handler
[   39.652320] iwlwifi 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[   39.652465] iwlwifi 0000:03:00.0: EVT_LOGT:0006980479:0x00000001:1208
[   39.652583] iwlwifi 0000:03:00.0: EVT_LOGT:0006980489:0x00000011:1551
[   39.652690] iwlwifi 0000:03:00.0: EVT_LOGT:0006980490:0x00000000:1555
[   39.652801] iwlwifi 0000:03:00.0: EVT_LOGT:0006980491:0x00020000:1555
[   39.652907] iwlwifi 0000:03:00.0: EVT_LOGT:0006980492:0x00020000:1568
[   39.653011] iwlwifi 0000:03:00.0: EVT_LOGT:0006980507:0x000001a8:0103
[   39.653123] iwlwifi 0000:03:00.0: EVT_LOGT:0006980508:0x95000301:1333
[   39.653229] iwlwifi 0000:03:00.0: EVT_LOGT:0006980509:0x00000000:1334
[   39.653337] iwlwifi 0000:03:00.0: EVT_LOGT:0006980510:0x00010000:1334
[   39.653443] iwlwifi 0000:03:00.0: EVT_LOGT:0006980511:0x010007ac:1334
[   39.653546] iwlwifi 0000:03:00.0: EVT_LOGT:0006980513:0x8c200050:1334
[   39.653658] iwlwifi 0000:03:00.0: EVT_LOGT:0006980513:0x01010838:1334
[   39.653766] iwlwifi 0000:03:00.0: EVT_LOGT:0006980515:0x8c210054:1334
[   39.653877] iwlwifi 0000:03:00.0: EVT_LOGT:0006980516:0x020008c4:1334
[   39.653983] iwlwifi 0000:03:00.0: EVT_LOGT:0006980518:0x8c400061:1334
[   39.654089] iwlwifi 0000:03:00.0: EVT_LOGT:0006980519:0x02010950:1334
[   39.654199] iwlwifi 0000:03:00.0: EVT_LOGT:0006980521:0x8c410062:1334
[   39.654305] iwlwifi 0000:03:00.0: EVT_LOGT:0006988035:0x010007ac:1333
[   39.654415] iwlwifi 0000:03:00.0: EVT_LOGT:0006988036:0x07aed500:1333
[   39.654521] iwlwifi 0000:03:00.0: EVT_LOGT:0006993137:0x00000000:0125
[   39.654670] iwlwifi 0000:03:00.0: FW error in SYNC CMD REPLY_ADD_STA
[   39.654779]  [<ffffffffc033069d>] iwl_trans_pcie_send_hcmd+0x44d/0x5a0 [iwlwifi]
[   39.654990] iwlwifi 0000:03:00.0: Adding station ff:ff:ff:ff:ff:ff failed.
[   39.655092] iwlwifi 0000:03:00.0: Command REPLY_ADD_STA failed: FW Error
[   39.655167] iwlwifi 0000:03:00.0: Adding station c0:56:27:6f:1f:bf failed.
[   39.655246] iwlwifi 0000:03:00.0: Unable to add station c0:56:27:6f:1f:bf (-5)
[   39.655617] iwlwifi 0000:03:00.0: iwl_trans_wait_tx_queue_empty bad state = 0
[   39.655782] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   39.662195] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   39.882362] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   39.888775] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   39.952417] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   39.952560] iwlwifi 0000:03:00.0: CSR values:
[   39.952633] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   39.952762] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X0048c704
[   39.952867] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[   39.952972] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[   39.953077] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[   39.953181] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   39.953286] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
[   39.953391] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[   39.953496] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[   39.953600] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000074
[   39.953705] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X28360ffd
[   39.953810] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[   39.953914] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X00030001
[   39.954019] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080042
[   39.954124] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000005
[   39.954229] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   39.954333] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   39.954438] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   39.954541] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[   39.954646] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X880babb7
[   39.954750] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   39.954855] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   39.954960] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X43f7f757
[   39.955065] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   39.955167] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   39.955245] iwlwifi 0000:03:00.0: FH register values:
[   39.955355] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X0b9abd00
[   39.955491] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00b9abe0
[   39.955665] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000008
[   39.955803] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[   39.955939] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   39.956075] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   39.956212] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   39.956407] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   39.956550] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   39.956660] iwlwifi 0000:03:00.0: Loaded firmware version: 9.176.4.1 build 15835
[   39.956918] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[   39.956994] iwlwifi 0000:03:00.0: Status: 0x0000004C, count: 5
[   39.957070] iwlwifi 0000:03:00.0: 0x00000005 | SYSASSERT                   
[   39.957149] iwlwifi 0000:03:00.0: 0x00023D2C | uPc
[   39.957223] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink1
[   39.957299] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink2
[   39.957374] iwlwifi 0000:03:00.0: 0x00000996 | interruptlink1
[   39.957450] iwlwifi 0000:03:00.0: 0x00000000 | interruptlink2
[   39.957526] iwlwifi 0000:03:00.0: 0xFFFFFFC0 | data1
[   39.957600] iwlwifi 0000:03:00.0: 0x0000017C | data2
[   39.957674] iwlwifi 0000:03:00.0: 0x000001DD | line
[   39.957749] iwlwifi 0000:03:00.0: 0x00015350 | beacon time
[   39.957832] iwlwifi 0000:03:00.0: 0x00003CB0 | tsf low
[   39.957907] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
[   39.957981] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[   39.958056] iwlwifi 0000:03:00.0: 0x0000D08B | time gp2
[   39.958130] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[   39.958205] iwlwifi 0000:03:00.0: 0x000109B0 | uCode version
[   39.958280] iwlwifi 0000:03:00.0: 0x00000074 | hw version
[   39.958355] iwlwifi 0000:03:00.0: 0x0048C704 | board version
[   39.958430] iwlwifi 0000:03:00.0: 0x04080010 | hcmd
[   39.958503] iwlwifi 0000:03:00.0: 0x27F23080 | isr0
[   39.958577] iwlwifi 0000:03:00.0: 0x00000000 | isr1
[   39.958651] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[   39.958724] iwlwifi 0000:03:00.0: 0x1141FCC0 | isr3
[   39.958798] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[   39.958872] iwlwifi 0000:03:00.0: 0x01800112 | isr_pref
[   39.958947] iwlwifi 0000:03:00.0: 0x0001D0AC | wait_event
[   39.959022] iwlwifi 0000:03:00.0: 0x00000000 | l2p_control
[   39.959097] iwlwifi 0000:03:00.0: 0x00000000 | l2p_duration
[   39.959173] iwlwifi 0000:03:00.0: 0x00000000 | l2p_mhvalid
[   39.959248] iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
[   39.959324] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
[   39.959399] iwlwifi 0000:03:00.0: 0x25090952 | timestamp
[   39.959474] iwlwifi 0000:03:00.0: 0x00000000 | flow_handler
[   39.959633] iwlwifi 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[   39.963320] iwlwifi 0000:03:00.0: EVT_LOGT:0000040706:0x00000001:1208
[   39.963478] iwlwifi 0000:03:00.0: EVT_LOGT:0000040763:0x00000011:1551
[   39.963589] iwlwifi 0000:03:00.0: EVT_LOGT:0000040764:0x00000000:1555
[   39.963699] iwlwifi 0000:03:00.0: EVT_LOGT:0000040765:0x00020000:1555
[   39.963840] iwlwifi 0000:03:00.0: EVT_LOGT:0000040766:0x00020000:1568
[   39.963950] iwlwifi 0000:03:00.0: EVT_LOGT:0000040781:0x000001a8:0103
[   39.964060] iwlwifi 0000:03:00.0: EVT_LOGT:0000040782:0x95000301:1333
[   39.964169] iwlwifi 0000:03:00.0: EVT_LOGT:0000040783:0x00000000:1334
[   39.964279] iwlwifi 0000:03:00.0: EVT_LOGT:0000040784:0x00010000:1334
[   39.964429] iwlwifi 0000:03:00.0: EVT_LOGT:0000040785:0x010007ac:1334
[   39.964538] iwlwifi 0000:03:00.0: EVT_LOGT:0000040786:0x8c200050:1334
[   39.964648] iwlwifi 0000:03:00.0: EVT_LOGT:0000040787:0x01010838:1334
[   39.964758] iwlwifi 0000:03:00.0: EVT_LOGT:0000040789:0x8c210054:1334
[   39.964868] iwlwifi 0000:03:00.0: EVT_LOGT:0000040790:0x020008c4:1334
[   39.964977] iwlwifi 0000:03:00.0: EVT_LOGT:0000040792:0x8c400061:1334
[   39.965088] iwlwifi 0000:03:00.0: EVT_LOGT:0000040792:0x02010950:1334
[   39.965198] iwlwifi 0000:03:00.0: EVT_LOGT:0000040794:0x8c410062:1334
[   39.965309] iwlwifi 0000:03:00.0: EVT_LOGT:0000048311:0x010007ac:1333
[   39.965419] iwlwifi 0000:03:00.0: EVT_LOGT:0000048312:0x07aed500:1333
[   39.965529] iwlwifi 0000:03:00.0: EVT_LOGT:0000053409:0x00000000:0125
[   39.965673] iwlwifi 0000:03:00.0: FW error in SYNC CMD REPLY_ADD_STA
[   39.965805]  [<ffffffffc033069d>] iwl_trans_pcie_send_hcmd+0x44d/0x5a0 [iwlwifi]
[   39.965881] iwlwifi 0000:03:00.0: Adding station ff:ff:ff:ff:ff:ff failed.
[   39.965961] iwlwifi 0000:03:00.0: Command REPLY_CT_KILL_CONFIG_CMD failed: FW Error
[   39.966063] iwlwifi 0000:03:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[   39.966381] iwlwifi 0000:03:00.0: Unable to initialize device.
[   39.966483] Modules linked in: snd_hrtimer binfmt_misc arc4 iwldvm  mac80211 nvidia_uvm(POE) uvcvideo intel_rapl x86_pkg_temp_thermal  videobuf2_vmalloc nvidia_modeset(POE) videobuf2_memops intel_powerclamp  videobuf2_core v4l2_common videodev snd_hda_codec_hdmi coretemp media  kvm_intel snd_hda_codec_realtek nvidia(POE) snd_hda_codec_generic  snd_hda_intel snd_hda_codec kvm snd_hda_core snd_hwdep dell_wmi  crct10dif_pclmul snd_pcm iwlwifi crc32_pclmul sparse_keymap snd_seq_midi  drm snd_seq_midi_event snd_rawmidi mei_me aesni_intel cfg80211  aes_x86_64 lrw snd_seq mei gf128mul glue_helper dell_laptop  snd_seq_device snd_timer dcdbas ablk_helper cryptd snd input_leds joydev  serio_raw soundcore lpc_ich shpchp dell_smo8800 mac_hid wmi parport_pc  ppdev lp parport autofs4 ses enclosure hid_logitech_hidpp  hid_logitech_dj
[   39.966732] Modules linked in: snd_hrtimer binfmt_misc arc4 iwldvm  mac80211 nvidia_uvm(POE) uvcvideo intel_rapl x86_pkg_temp_thermal  videobuf2_vmalloc nvidia_modeset(POE) videobuf2_memops intel_powerclamp  videobuf2_core v4l2_common videodev snd_hda_codec_hdmi coretemp media  kvm_intel snd_hda_codec_realtek nvidia(POE) snd_hda_codec_generic  snd_hda_intel snd_hda_codec kvm snd_hda_core snd_hwdep dell_wmi  crct10dif_pclmul snd_pcm iwlwifi crc32_pclmul sparse_keymap snd_seq_midi  drm snd_seq_midi_event snd_rawmidi mei_me aesni_intel cfg80211  aes_x86_64 lrw snd_seq mei gf128mul glue_helper dell_laptop  snd_seq_device snd_timer dcdbas ablk_helper cryptd snd input_leds joydev  serio_raw soundcore lpc_ich shpchp dell_smo8800 mac_hid wmi parport_pc  ppdev lp parport autofs4 ses enclosure hid_logitech_hidpp  hid_logitech_dj
[   65.048019] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   65.054450] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   65.278336] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   65.284750] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   65.348543] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   65.348631] iwlwifi 0000:03:00.0: CSR values:
[   65.348683] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   65.348773] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X0048c704
[   65.348859] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[   65.348942] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[   65.349027] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[   65.349113] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   65.349197] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
[   65.349287] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[   65.349373] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[   65.349459] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000074
[   65.349545] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X28360ffd
[   65.349631] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[   65.349714] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X00030001
[   65.349800] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080042
[   65.349907] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000005
[   65.350014] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   65.350120] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   65.350225] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   65.350331] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[   65.350442] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X880babb7
[   65.350549] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   65.350654] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   65.350758] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X43f7ffd7
[   65.350863] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   65.350968] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   65.351048] iwlwifi 0000:03:00.0: FH register values:
[   65.351165] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X0b9abd00
[   65.351305] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00b9abe0
[   65.351445] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000008
[   65.351585] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[   65.351726] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   65.351871] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   65.352012] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   65.352152] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   65.352320] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   65.352435] iwlwifi 0000:03:00.0: Loaded firmware version: 9.176.4.1 build 15835
[   65.352708] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[   65.352789] iwlwifi 0000:03:00.0: Status: 0x0000004C, count: 5
[   65.352870] iwlwifi 0000:03:00.0: 0x00000005 | SYSASSERT                   
[   65.352953] iwlwifi 0000:03:00.0: 0x00023D2C | uPc
[   65.353031] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink1
[   65.353110] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink2
[   65.353190] iwlwifi 0000:03:00.0: 0x00000996 | interruptlink1
[   65.353271] iwlwifi 0000:03:00.0: 0x00000000 | interruptlink2
[   65.353352] iwlwifi 0000:03:00.0: 0xFFFFFFC0 | data1
[   65.353429] iwlwifi 0000:03:00.0: 0x0000017C | data2
[   65.353507] iwlwifi 0000:03:00.0: 0x000001DD | line
[   65.353585] iwlwifi 0000:03:00.0: 0x00015381 | beacon time
[   65.353664] iwlwifi 0000:03:00.0: 0x00003C7F | tsf low
[   65.353742] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
[   65.353820] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[   65.353899] iwlwifi 0000:03:00.0: 0x0000D0C2 | time gp2
[   65.353978] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[   65.354057] iwlwifi 0000:03:00.0: 0x000109B0 | uCode version
[   65.354137] iwlwifi 0000:03:00.0: 0x00000074 | hw version
[   65.354216] iwlwifi 0000:03:00.0: 0x0048C704 | board version
[   65.354296] iwlwifi 0000:03:00.0: 0x04080010 | hcmd
[   65.354374] iwlwifi 0000:03:00.0: 0x00122080 | isr0
[   65.354452] iwlwifi 0000:03:00.0: 0x00000000 | isr1
[   65.354530] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[   65.354607] iwlwifi 0000:03:00.0: 0x1141FCC0 | isr3
[   65.354684] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[   65.354765] iwlwifi 0000:03:00.0: 0x01800112 | isr_pref
[   65.354844] iwlwifi 0000:03:00.0: 0x0001D0AC | wait_event
[   65.354923] iwlwifi 0000:03:00.0: 0x00000000 | l2p_control
[   65.355002] iwlwifi 0000:03:00.0: 0x00000000 | l2p_duration
[   65.355082] iwlwifi 0000:03:00.0: 0x00000000 | l2p_mhvalid
[   65.355162] iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
[   65.355242] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
[   65.355321] iwlwifi 0000:03:00.0: 0x25090952 | timestampSo, A couple  of months ago, I installed 15.04, wifi didn't work out of  the box, so I downloaded the most recent intel firmware, This let the  wifi connect from my live usb, but not from the installed OS. So, I set  my /etc/modprobe.d/iwlwifi.conf as follows:

[CODE]
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

options iwlwifi 11n_disable=8 led_mode=1 bt_coex_active=0 power_save=0

```

This allowed me to see the wireless networks in my area from the installed OS but not connect to any.  

Solving that required me to set my CRDA
```

# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=US

```

And this solved my problem, and got my wifi working.  

Ubuntu auto-updated to 15.10, and wifi worked great up till a couple of  days ago (Roughly 7/4).  At which point it started throwing errors on  boot.  Below is the Dmesg output of iwlwifi:

```

[   13.723237] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   14.367447] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-6000-6.ucode failed with error -2
[   14.369080] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-6000-5.ucode failed with error -2
[   14.862792] iwlwifi 0000:03:00.0: loaded firmware version 9.176.4.1 build 15835 op_mode iwldvm
[   16.207039] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   16.207042] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   16.207043] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   16.207046] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   16.207146] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   17.013177] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[   32.401171] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   32.407590] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   32.638122] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   32.644515] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   32.744606] iwlwifi 0000:03:00.0: Requested user TXPOWER 16 above upper limit 0.
[   39.645718] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   39.645801] iwlwifi 0000:03:00.0: CSR values:
[   39.645849] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   39.645937] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X0048c704
[   39.646017] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[   39.646095] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[   39.646179] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[   39.646260] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   39.646345] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
[   39.646429] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[   39.646507] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[   39.646587] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000074
[   39.646665] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X28360ffd
[   39.646745] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[   39.646829] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X00030001
[   39.646907] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080042
[   39.646991] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00001076
[   39.647073] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   39.647154] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   39.647253] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   39.647355] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000040
[   39.647455] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X880babb7
[   39.647560] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   39.647663] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   39.647761] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X43f7f757
[   39.647862] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   39.647965] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   39.648037] iwlwifi 0000:03:00.0: FH register values:
[   39.648148] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X0b9abd00
[   39.648286] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00b9abe0
[   39.648418] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000088
[   39.648577] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[   39.648790] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   39.648925] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   39.649055] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   39.649192] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   39.649322] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   39.649424] iwlwifi 0000:03:00.0: Loaded firmware version: 9.176.4.1 build 15835
[   39.649681] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[   39.649751] iwlwifi 0000:03:00.0: Status: 0x0000004C, count: 5
[   39.649823] iwlwifi 0000:03:00.0: 0x00000005 | SYSASSERT                   
[   39.649897] iwlwifi 0000:03:00.0: 0x00023D2C | uPc
[   39.649971] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink1
[   39.650047] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink2
[   39.650118] iwlwifi 0000:03:00.0: 0x00000996 | interruptlink1
[   39.650189] iwlwifi 0000:03:00.0: 0x00000000 | interruptlink2
[   39.650265] iwlwifi 0000:03:00.0: 0xFFFFFFC0 | data1
[   39.650334] iwlwifi 0000:03:00.0: 0x0000017C | data2
[   39.650407] iwlwifi 0000:03:00.0: 0x000001DD | line
[   39.650482] iwlwifi 0000:03:00.0: 0x00015382 | beacon time
[   39.650551] iwlwifi 0000:03:00.0: 0x00003C7D | tsf low
[   39.650622] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
[   39.650691] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[   39.650766] iwlwifi 0000:03:00.0: 0x006AB4DB | time gp2
[   39.650838] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[   39.650907] iwlwifi 0000:03:00.0: 0x000109B0 | uCode version
[   39.650982] iwlwifi 0000:03:00.0: 0x00000074 | hw version
[   39.651050] iwlwifi 0000:03:00.0: 0x0048C704 | board version
[   39.651127] iwlwifi 0000:03:00.0: 0x041A0010 | hcmd
[   39.651201] iwlwifi 0000:03:00.0: 0x26E22080 | isr0
[   39.651268] iwlwifi 0000:03:00.0: 0x0103E000 | isr1
[   39.651339] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[   39.651407] iwlwifi 0000:03:00.0: 0x1141FCC1 | isr3
[   39.651480] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[   39.651554] iwlwifi 0000:03:00.0: 0x11800112 | isr_pref
[   39.651623] iwlwifi 0000:03:00.0: 0x0001D5D6 | wait_event
[   39.651692] iwlwifi 0000:03:00.0: 0x00000080 | l2p_control
[   39.651764] iwlwifi 0000:03:00.0: 0x00000000 | l2p_duration
[   39.651839] iwlwifi 0000:03:00.0: 0x0000003F | l2p_mhvalid
[   39.651914] iwlwifi 0000:03:00.0: 0x00200200 | l2p_addr_match
[   39.651986] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
[   39.652060] iwlwifi 0000:03:00.0: 0x25090952 | timestamp
[   39.652129] iwlwifi 0000:03:00.0: 0x00000000 | flow_handler
[   39.652320] iwlwifi 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[   39.652465] iwlwifi 0000:03:00.0: EVT_LOGT:0006980479:0x00000001:1208
[   39.652583] iwlwifi 0000:03:00.0: EVT_LOGT:0006980489:0x00000011:1551
[   39.652690] iwlwifi 0000:03:00.0: EVT_LOGT:0006980490:0x00000000:1555
[   39.652801] iwlwifi 0000:03:00.0: EVT_LOGT:0006980491:0x00020000:1555
[   39.652907] iwlwifi 0000:03:00.0: EVT_LOGT:0006980492:0x00020000:1568
[   39.653011] iwlwifi 0000:03:00.0: EVT_LOGT:0006980507:0x000001a8:0103
[   39.653123] iwlwifi 0000:03:00.0: EVT_LOGT:0006980508:0x95000301:1333
[   39.653229] iwlwifi 0000:03:00.0: EVT_LOGT:0006980509:0x00000000:1334
[   39.653337] iwlwifi 0000:03:00.0: EVT_LOGT:0006980510:0x00010000:1334
[   39.653443] iwlwifi 0000:03:00.0: EVT_LOGT:0006980511:0x010007ac:1334
[   39.653546] iwlwifi 0000:03:00.0: EVT_LOGT:0006980513:0x8c200050:1334
[   39.653658] iwlwifi 0000:03:00.0: EVT_LOGT:0006980513:0x01010838:1334
[   39.653766] iwlwifi 0000:03:00.0: EVT_LOGT:0006980515:0x8c210054:1334
[   39.653877] iwlwifi 0000:03:00.0: EVT_LOGT:0006980516:0x020008c4:1334
[   39.653983] iwlwifi 0000:03:00.0: EVT_LOGT:0006980518:0x8c400061:1334
[   39.654089] iwlwifi 0000:03:00.0: EVT_LOGT:0006980519:0x02010950:1334
[   39.654199] iwlwifi 0000:03:00.0: EVT_LOGT:0006980521:0x8c410062:1334
[   39.654305] iwlwifi 0000:03:00.0: EVT_LOGT:0006988035:0x010007ac:1333
[   39.654415] iwlwifi 0000:03:00.0: EVT_LOGT:0006988036:0x07aed500:1333
[   39.654521] iwlwifi 0000:03:00.0: EVT_LOGT:0006993137:0x00000000:0125
[   39.654670] iwlwifi 0000:03:00.0: FW error in SYNC CMD REPLY_ADD_STA
[   39.654779]  [<ffffffffc033069d>] iwl_trans_pcie_send_hcmd+0x44d/0x5a0 [iwlwifi]
[   39.654990] iwlwifi 0000:03:00.0: Adding station ff:ff:ff:ff:ff:ff failed.
[   39.655092] iwlwifi 0000:03:00.0: Command REPLY_ADD_STA failed: FW Error
[   39.655167] iwlwifi 0000:03:00.0: Adding station c0:56:27:6f:1f:bf failed.
[   39.655246] iwlwifi 0000:03:00.0: Unable to add station c0:56:27:6f:1f:bf (-5)
[   39.655617] iwlwifi 0000:03:00.0: iwl_trans_wait_tx_queue_empty bad state = 0
[   39.655782] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   39.662195] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   39.882362] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   39.888775] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   39.952417] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   39.952560] iwlwifi 0000:03:00.0: CSR values:
[   39.952633] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   39.952762] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X0048c704
[   39.952867] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[   39.952972] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[   39.953077] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[   39.953181] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   39.953286] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
[   39.953391] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[   39.953496] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[   39.953600] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000074
[   39.953705] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X28360ffd
[   39.953810] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[   39.953914] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X00030001
[   39.954019] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080042
[   39.954124] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000005
[   39.954229] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   39.954333] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   39.954438] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   39.954541] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[   39.954646] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X880babb7
[   39.954750] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   39.954855] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   39.954960] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X43f7f757
[   39.955065] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   39.955167] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   39.955245] iwlwifi 0000:03:00.0: FH register values:
[   39.955355] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X0b9abd00
[   39.955491] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00b9abe0
[   39.955665] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000008
[   39.955803] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[   39.955939] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   39.956075] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   39.956212] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   39.956407] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   39.956550] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   39.956660] iwlwifi 0000:03:00.0: Loaded firmware version: 9.176.4.1 build 15835
[   39.956918] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[   39.956994] iwlwifi 0000:03:00.0: Status: 0x0000004C, count: 5
[   39.957070] iwlwifi 0000:03:00.0: 0x00000005 | SYSASSERT                   
[   39.957149] iwlwifi 0000:03:00.0: 0x00023D2C | uPc
[   39.957223] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink1
[   39.957299] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink2
[   39.957374] iwlwifi 0000:03:00.0: 0x00000996 | interruptlink1
[   39.957450] iwlwifi 0000:03:00.0: 0x00000000 | interruptlink2
[   39.957526] iwlwifi 0000:03:00.0: 0xFFFFFFC0 | data1
[   39.957600] iwlwifi 0000:03:00.0: 0x0000017C | data2
[   39.957674] iwlwifi 0000:03:00.0: 0x000001DD | line
[   39.957749] iwlwifi 0000:03:00.0: 0x00015350 | beacon time
[   39.957832] iwlwifi 0000:03:00.0: 0x00003CB0 | tsf low
[   39.957907] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
[   39.957981] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[   39.958056] iwlwifi 0000:03:00.0: 0x0000D08B | time gp2
[   39.958130] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[   39.958205] iwlwifi 0000:03:00.0: 0x000109B0 | uCode version
[   39.958280] iwlwifi 0000:03:00.0: 0x00000074 | hw version
[   39.958355] iwlwifi 0000:03:00.0: 0x0048C704 | board version
[   39.958430] iwlwifi 0000:03:00.0: 0x04080010 | hcmd
[   39.958503] iwlwifi 0000:03:00.0: 0x27F23080 | isr0
[   39.958577] iwlwifi 0000:03:00.0: 0x00000000 | isr1
[   39.958651] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[   39.958724] iwlwifi 0000:03:00.0: 0x1141FCC0 | isr3
[   39.958798] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[   39.958872] iwlwifi 0000:03:00.0: 0x01800112 | isr_pref
[   39.958947] iwlwifi 0000:03:00.0: 0x0001D0AC | wait_event
[   39.959022] iwlwifi 0000:03:00.0: 0x00000000 | l2p_control
[   39.959097] iwlwifi 0000:03:00.0: 0x00000000 | l2p_duration
[   39.959173] iwlwifi 0000:03:00.0: 0x00000000 | l2p_mhvalid
[   39.959248] iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
[   39.959324] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
[   39.959399] iwlwifi 0000:03:00.0: 0x25090952 | timestamp
[   39.959474] iwlwifi 0000:03:00.0: 0x00000000 | flow_handler
[   39.959633] iwlwifi 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[   39.963320] iwlwifi 0000:03:00.0: EVT_LOGT:0000040706:0x00000001:1208
[   39.963478] iwlwifi 0000:03:00.0: EVT_LOGT:0000040763:0x00000011:1551
[   39.963589] iwlwifi 0000:03:00.0: EVT_LOGT:0000040764:0x00000000:1555
[   39.963699] iwlwifi 0000:03:00.0: EVT_LOGT:0000040765:0x00020000:1555
[   39.963840] iwlwifi 0000:03:00.0: EVT_LOGT:0000040766:0x00020000:1568
[   39.963950] iwlwifi 0000:03:00.0: EVT_LOGT:0000040781:0x000001a8:0103
[   39.964060] iwlwifi 0000:03:00.0: EVT_LOGT:0000040782:0x95000301:1333
[   39.964169] iwlwifi 0000:03:00.0: EVT_LOGT:0000040783:0x00000000:1334
[   39.964279] iwlwifi 0000:03:00.0: EVT_LOGT:0000040784:0x00010000:1334
[   39.964429] iwlwifi 0000:03:00.0: EVT_LOGT:0000040785:0x010007ac:1334
[   39.964538] iwlwifi 0000:03:00.0: EVT_LOGT:0000040786:0x8c200050:1334
[   39.964648] iwlwifi 0000:03:00.0: EVT_LOGT:0000040787:0x01010838:1334
[   39.964758] iwlwifi 0000:03:00.0: EVT_LOGT:0000040789:0x8c210054:1334
[   39.964868] iwlwifi 0000:03:00.0: EVT_LOGT:0000040790:0x020008c4:1334
[   39.964977] iwlwifi 0000:03:00.0: EVT_LOGT:0000040792:0x8c400061:1334
[   39.965088] iwlwifi 0000:03:00.0: EVT_LOGT:0000040792:0x02010950:1334
[   39.965198] iwlwifi 0000:03:00.0: EVT_LOGT:0000040794:0x8c410062:1334
[   39.965309] iwlwifi 0000:03:00.0: EVT_LOGT:0000048311:0x010007ac:1333
[   39.965419] iwlwifi 0000:03:00.0: EVT_LOGT:0000048312:0x07aed500:1333
[   39.965529] iwlwifi 0000:03:00.0: EVT_LOGT:0000053409:0x00000000:0125
[   39.965673] iwlwifi 0000:03:00.0: FW error in SYNC CMD REPLY_ADD_STA
[   39.965805]  [<ffffffffc033069d>] iwl_trans_pcie_send_hcmd+0x44d/0x5a0 [iwlwifi]
[   39.965881] iwlwifi 0000:03:00.0: Adding station ff:ff:ff:ff:ff:ff failed.
[   39.965961] iwlwifi 0000:03:00.0: Command REPLY_CT_KILL_CONFIG_CMD failed: FW Error
[   39.966063] iwlwifi 0000:03:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[   39.966381] iwlwifi 0000:03:00.0: Unable to initialize device.
[   39.966483] Modules linked in: snd_hrtimer binfmt_misc arc4 iwldvm  mac80211 nvidia_uvm(POE) uvcvideo intel_rapl x86_pkg_temp_thermal  videobuf2_vmalloc nvidia_modeset(POE) videobuf2_memops intel_powerclamp  videobuf2_core v4l2_common videodev snd_hda_codec_hdmi coretemp media  kvm_intel snd_hda_codec_realtek nvidia(POE) snd_hda_codec_generic  snd_hda_intel snd_hda_codec kvm snd_hda_core snd_hwdep dell_wmi  crct10dif_pclmul snd_pcm iwlwifi crc32_pclmul sparse_keymap snd_seq_midi  drm snd_seq_midi_event snd_rawmidi mei_me aesni_intel cfg80211  aes_x86_64 lrw snd_seq mei gf128mul glue_helper dell_laptop  snd_seq_device snd_timer dcdbas ablk_helper cryptd snd input_leds joydev  serio_raw soundcore lpc_ich shpchp dell_smo8800 mac_hid wmi parport_pc  ppdev lp parport autofs4 ses enclosure hid_logitech_hidpp  hid_logitech_dj
[   39.966732] Modules linked in: snd_hrtimer binfmt_misc arc4 iwldvm  mac80211 nvidia_uvm(POE) uvcvideo intel_rapl x86_pkg_temp_thermal  videobuf2_vmalloc nvidia_modeset(POE) videobuf2_memops intel_powerclamp  videobuf2_core v4l2_common videodev snd_hda_codec_hdmi coretemp media  kvm_intel snd_hda_codec_realtek nvidia(POE) snd_hda_codec_generic  snd_hda_intel snd_hda_codec kvm snd_hda_core snd_hwdep dell_wmi  crct10dif_pclmul snd_pcm iwlwifi crc32_pclmul sparse_keymap snd_seq_midi  drm snd_seq_midi_event snd_rawmidi mei_me aesni_intel cfg80211  aes_x86_64 lrw snd_seq mei gf128mul glue_helper dell_laptop  snd_seq_device snd_timer dcdbas ablk_helper cryptd snd input_leds joydev  serio_raw soundcore lpc_ich shpchp dell_smo8800 mac_hid wmi parport_pc  ppdev lp parport autofs4 ses enclosure hid_logitech_hidpp  hid_logitech_dj
[   65.048019] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   65.054450] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   65.278336] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   65.284750] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   65.348543] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   65.348631] iwlwifi 0000:03:00.0: CSR values:
[   65.348683] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   65.348773] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X0048c704
[   65.348859] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[   65.348942] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[   65.349027] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[   65.349113] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   65.349197] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
[   65.349287] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[   65.349373] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[   65.349459] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000074
[   65.349545] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X28360ffd
[   65.349631] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[   65.349714] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X00030001
[   65.349800] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080042
[   65.349907] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000005
[   65.350014] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   65.350120] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   65.350225] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   65.350331] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[   65.350442] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X880babb7
[   65.350549] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   65.350654] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   65.350758] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X43f7ffd7
[   65.350863] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   65.350968] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   65.351048] iwlwifi 0000:03:00.0: FH register values:
[   65.351165] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X0b9abd00
[   65.351305] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00b9abe0
[   65.351445] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000008
[   65.351585] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[   65.351726] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   65.351871] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   65.352012] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   65.352152] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   65.352320] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   65.352435] iwlwifi 0000:03:00.0: Loaded firmware version: 9.176.4.1 build 15835
[   65.352708] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[   65.352789] iwlwifi 0000:03:00.0: Status: 0x0000004C, count: 5
[   65.352870] iwlwifi 0000:03:00.0: 0x00000005 | SYSASSERT                   
[   65.352953] iwlwifi 0000:03:00.0: 0x00023D2C | uPc
[   65.353031] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink1
[   65.353110] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink2
[   65.353190] iwlwifi 0000:03:00.0: 0x00000996 | interruptlink1
[   65.353271] iwlwifi 0000:03:00.0: 0x00000000 | interruptlink2
[   65.353352] iwlwifi 0000:03:00.0: 0xFFFFFFC0 | data1
[   65.353429] iwlwifi 0000:03:00.0: 0x0000017C | data2
[   65.353507] iwlwifi 0000:03:00.0: 0x000001DD | line
[   65.353585] iwlwifi 0000:03:00.0: 0x00015381 | beacon time
[   65.353664] iwlwifi 0000:03:00.0: 0x00003C7F | tsf low
[   65.353742] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
[   65.353820] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[   65.353899] iwlwifi 0000:03:00.0: 0x0000D0C2 | time gp2
[   65.353978] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[   65.354057] iwlwifi 0000:03:00.0: 0x000109B0 | uCode version
[   65.354137] iwlwifi 0000:03:00.0: 0x00000074 | hw version
[   65.354216] iwlwifi 0000:03:00.0: 0x0048C704 | board version
[   65.354296] iwlwifi 0000:03:00.0: 0x04080010 | hcmd
[   65.354374] iwlwifi 0000:03:00.0: 0x00122080 | isr0
[   65.354452] iwlwifi 0000:03:00.0: 0x00000000 | isr1
[   65.354530] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[   65.354607] iwlwifi 0000:03:00.0: 0x1141FCC0 | isr3
[   65.354684] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[   65.354765] iwlwifi 0000:03:00.0: 0x01800112 | isr_pref
[   65.354844] iwlwifi 0000:03:00.0: 0x0001D0AC | wait_event
[   65.354923] iwlwifi 0000:03:00.0: 0x00000000 | l2p_control
[   65.355002] iwlwifi 0000:03:00.0: 0x00000000 | l2p_duration
[   65.355082] iwlwifi 0000:03:00.0: 0x00000000 | l2p_mhvalid
[   65.355162] iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
[   65.355242] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
[   65.355321] iwlwifi 0000:03:00.0: 0x25090952 | timestamp
[   65.355401] iwlwifi 0000:03:00.0: 0x00000000 | flow_handler
[   65.355566] iwlwifi 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[   65.355717] iwlwifi 0000:03:00.0: EVT_LOGT:0000040812:0x00000001:1208
[   65.355835] iwlwifi 0000:03:00.0: EVT_LOGT:0000040869:0x00000011:1551
[   65.355950] iwlwifi 0000:03:00.0: EVT_LOGT:0000040870:0x00000000:1555
[   65.356066] iwlwifi 0000:03:00.0: EVT_LOGT:0000040871:0x00020000:1555
[   65.356184] iwlwifi 0000:03:00.0: EVT_LOGT:0000040871:0x00020000:1568
[   65.356339] iwlwifi 0000:03:00.0: EVT_LOGT:0000040887:0x000001a8:0103
[   65.356457] iwlwifi 0000:03:00.0: EVT_LOGT:0000040888:0x95000301:1333
[   65.356573] iwlwifi 0000:03:00.0: EVT_LOGT:0000040889:0x00000000:1334
[   65.356689] iwlwifi 0000:03:00.0: EVT_LOGT:0000040889:0x00010000:1334
[   65.356805] iwlwifi 0000:03:00.0: EVT_LOGT:0000040890:0x010007ac:1334
[   65.356923] iwlwifi 0000:03:00.0: EVT_LOGT:0000040892:0x8c200050:1334
[   65.357041] iwlwifi 0000:03:00.0: EVT_LOGT:0000040893:0x01010838:1334
[   65.357158] iwlwifi 0000:03:00.0: EVT_LOGT:0000040895:0x8c210054:1334
[   65.357277] iwlwifi 0000:03:00.0: EVT_LOGT:0000040896:0x020008c4:1334
[   65.357392] iwlwifi 0000:03:00.0: EVT_LOGT:0000040898:0x8c400061:1334
[   65.357508] iwlwifi 0000:03:00.0: EVT_LOGT:0000040898:0x02010950:1334
[   65.357625] iwlwifi 0000:03:00.0: EVT_LOGT:0000040900:0x8c410062:1334
[   65.357743] iwlwifi 0000:03:00.0: EVT_LOGT:0000048381:0x010007ac:1333
[   65.357861] iwlwifi 0000:03:00.0: EVT_LOGT:0000048381:0x07aed500:1333
[   65.357980] iwlwifi 0000:03:00.0: EVT_LOGT:0000053464:0x00000000:0125
[   65.358136] iwlwifi 0000:03:00.0: FW error in SYNC CMD REPLY_ADD_STA
[   65.358264]  [<ffffffffc033069d>] iwl_trans_pcie_send_hcmd+0x44d/0x5a0 [iwlwifi]
[   65.358441] iwlwifi 0000:03:00.0: Adding station ff:ff:ff:ff:ff:ff failed.
[   65.358525] iwlwifi 0000:03:00.0: Command REPLY_CT_KILL_CONFIG_CMD failed: FW Error
[   65.358628] iwlwifi 0000:03:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[   65.358948] iwlwifi 0000:03:00.0: Unable to initialize device.
[   65.364815] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   65.371240] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   65.594140] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   65.600565] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   65.664374] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   65.664504] iwlwifi 0000:03:00.0: CSR values:
[   65.664576] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   65.664707] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X0048c704
[   65.664811] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[   65.664926] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[   65.665035] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[   65.665141] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   65.665248] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
[   65.665355] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[   65.665462] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[   65.665569] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000074
[   65.665675] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X28360ffd
[   65.665782] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[   65.665889] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X00030001
[   65.665995] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080042
[   65.666102] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000005
[   65.666208] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   65.666315] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   65.666423] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   65.666535] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[   65.666642] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X880babb7
[   65.666748] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   65.666855] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   65.666962] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X43f7ff57
[   65.667069] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   65.667173] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   65.667255] iwlwifi 0000:03:00.0: FH register values:
[   65.667367] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X0b9abd00
[   65.667509] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00b9abe0
[   65.667697] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000008
[   65.667838] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[   65.667981] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   65.668123] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   65.668282] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   65.668426] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   65.668570] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   65.668676] iwlwifi 0000:03:00.0: Loaded firmware version: 9.176.4.1 build 15835
[   65.669027] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[   65.669106] iwlwifi 0000:03:00.0: Status: 0x0000004C, count: 5
[   65.669184] iwlwifi 0000:03:00.0: 0x00000005 | SYSASSERT                   
[   65.669265] iwlwifi 0000:03:00.0: 0x00023D2C | uPc
[   65.669340] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink1
[   65.669416] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink2
[   65.669493] iwlwifi 0000:03:00.0: 0x00000996 | interruptlink1
[   65.669570] iwlwifi 0000:03:00.0: 0x00000000 | interruptlink2
[   65.669647] iwlwifi 0000:03:00.0: 0xFFFFFFC0 | data1
[   65.669723] iwlwifi 0000:03:00.0: 0x0000017C | data2
[   65.669798] iwlwifi 0000:03:00.0: 0x000001DD | line
[   65.669873] iwlwifi 0000:03:00.0: 0x00015371 | beacon time
[   65.669956] iwlwifi 0000:03:00.0: 0x00003C8F | tsf low
[   65.670040] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
[   65.670117] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[   65.670194] iwlwifi 0000:03:00.0: 0x0000D10D | time gp2
[   65.670270] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[   65.670347] iwlwifi 0000:03:00.0: 0x000109B0 | uCode version
[   65.670425] iwlwifi 0000:03:00.0: 0x00000074 | hw version
[   65.670503] iwlwifi 0000:03:00.0: 0x0048C704 | board version
[   65.670580] iwlwifi 0000:03:00.0: 0x04080010 | hcmd
[   65.670656] iwlwifi 0000:03:00.0: 0x00122080 | isr0
[   65.670732] iwlwifi 0000:03:00.0: 0x00000000 | isr1
[   65.670808] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[   65.670884] iwlwifi 0000:03:00.0: 0x1141FCC0 | isr3
[   65.670960] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[   65.671035] iwlwifi 0000:03:00.0: 0x01800112 | isr_pref
[   65.671113] iwlwifi 0000:03:00.0: 0x0001D0AC | wait_event
[   65.671194] iwlwifi 0000:03:00.0: 0x00000000 | l2p_control
[   65.671272] iwlwifi 0000:03:00.0: 0x00000000 | l2p_duration
[   65.671350] iwlwifi 0000:03:00.0: 0x00000000 | l2p_mhvalid
[   65.671427] iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
[   65.671505] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
[   65.671583] iwlwifi 0000:03:00.0: 0x25090952 | timestamp
[   65.675237] iwlwifi 0000:03:00.0: 0x00000000 | flow_handler
[   65.675418] iwlwifi 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[   65.675568] iwlwifi 0000:03:00.0: EVT_LOGT:0000040872:0x00000001:1208
[   65.675685] iwlwifi 0000:03:00.0: EVT_LOGT:0000040929:0x00000011:1551
[   65.675798] iwlwifi 0000:03:00.0: EVT_LOGT:0000040930:0x00000000:1555
[   65.675912] iwlwifi 0000:03:00.0: EVT_LOGT:0000040931:0x00020000:1555
[   65.676035] iwlwifi 0000:03:00.0: EVT_LOGT:0000040931:0x00020000:1568
[   65.676148] iwlwifi 0000:03:00.0: EVT_LOGT:0000040947:0x000001a8:0103
[   65.676262] iwlwifi 0000:03:00.0: EVT_LOGT:0000040948:0x95000301:1333
[   65.676375] iwlwifi 0000:03:00.0: EVT_LOGT:0000040949:0x00000000:1334
[   65.676487] iwlwifi 0000:03:00.0: EVT_LOGT:0000040949:0x00010000:1334
[   65.676600] iwlwifi 0000:03:00.0: EVT_LOGT:0000040950:0x010007ac:1334
[   65.676714] iwlwifi 0000:03:00.0: EVT_LOGT:0000040952:0x8c200050:1334
[   65.676828] iwlwifi 0000:03:00.0: EVT_LOGT:0000040953:0x01010838:1334
[   65.676942] iwlwifi 0000:03:00.0: EVT_LOGT:0000040955:0x8c210054:1334
[   65.677055] iwlwifi 0000:03:00.0: EVT_LOGT:0000040956:0x020008c4:1334
[   65.677169] iwlwifi 0000:03:00.0: EVT_LOGT:0000040958:0x8c400061:1334
[   65.677283] iwlwifi 0000:03:00.0: EVT_LOGT:0000040958:0x02010950:1334
[   65.677396] iwlwifi 0000:03:00.0: EVT_LOGT:0000040960:0x8c410062:1334
[   65.677510] iwlwifi 0000:03:00.0: EVT_LOGT:0000048439:0x010007ac:1333
[   65.677624] iwlwifi 0000:03:00.0: EVT_LOGT:0000048440:0x07aed500:1333
[   65.677738] iwlwifi 0000:03:00.0: EVT_LOGT:0000053539:0x00000000:0125
[   65.677861] iwlwifi 0000:03:00.0: FW error in SYNC CMD REPLY_ADD_STA
[   65.677982]  [<ffffffffc033069d>] iwl_trans_pcie_send_hcmd+0x44d/0x5a0 [iwlwifi]
[   65.678108] iwlwifi 0000:03:00.0: Adding station ff:ff:ff:ff:ff:ff failed.
[   65.678191] iwlwifi 0000:03:00.0: Command REPLY_CT_KILL_CONFIG_CMD failed: FW Error
[   65.678294] iwlwifi 0000:03:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[   65.678613] iwlwifi 0000:03:00.0: Unable to initialize device.
[   65.682500] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   65.688945] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   65.909788] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   65.916258] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   65.979788] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   65.979917] iwlwifi 0000:03:00.0: CSR values:
[   65.979991] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   65.980141] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X0048c704
[   65.980249] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[   65.980355] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[   65.980460] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[   65.980567] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   65.980673] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
[   65.980780] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[   65.980884] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[   65.980991] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000074
[   65.981098] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X28360ffd
[   65.981202] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[   65.981309] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X00030001
[   65.981415] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080042
[   65.981521] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000005
[   65.981629] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   65.981735] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   65.981842] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   65.981949] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[   65.982055] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X880babb7
[   65.982162] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   65.982268] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   65.982375] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X43f7ff57
[   65.982482] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   65.982589] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   65.982670] iwlwifi 0000:03:00.0: FH register values:
[   65.982785] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X0b9abd00
[   65.982926] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00b9abe0
[   65.983068] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000008
[   65.983210] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[   65.983352] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   65.983494] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   65.983636] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   65.983782] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   65.983922] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   65.984027] iwlwifi 0000:03:00.0: Loaded firmware version: 9.176.4.1 build 15835
[   65.984297] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[   65.984377] iwlwifi 0000:03:00.0: Status: 0x0000004C, count: 5
[   65.984456] iwlwifi 0000:03:00.0: 0x00000005 | SYSASSERT                   
[   65.984538] iwlwifi 0000:03:00.0: 0x00023D2C | uPc
[   65.984620] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink1
[   65.984697] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink2
[   65.984774] iwlwifi 0000:03:00.0: 0x00000996 | interruptlink1
[   65.984856] iwlwifi 0000:03:00.0: 0x00000000 | interruptlink2
[   65.984933] iwlwifi 0000:03:00.0: 0xFFFFFFC0 | data1
[   65.985008] iwlwifi 0000:03:00.0: 0x0000017C | data2
[   65.985083] iwlwifi 0000:03:00.0: 0x000001DD | line
[   65.985158] iwlwifi 0000:03:00.0: 0x00015372 | beacon time
[   65.985234] iwlwifi 0000:03:00.0: 0x00003C8E | tsf low
[   65.985309] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
[   65.985384] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[   65.985460] iwlwifi 0000:03:00.0: 0x0000CFCE | time gp2
[   65.985535] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[   65.985620] iwlwifi 0000:03:00.0: 0x000109B0 | uCode version
[   65.985698] iwlwifi 0000:03:00.0: 0x00000074 | hw version
[   65.985776] iwlwifi 0000:03:00.0: 0x0048C704 | board version
[   65.985853] iwlwifi 0000:03:00.0: 0x04080010 | hcmd
[   65.985929] iwlwifi 0000:03:00.0: 0x02322080 | isr0
[   65.986005] iwlwifi 0000:03:00.0: 0x00000000 | isr1
[   65.986086] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[   65.986162] iwlwifi 0000:03:00.0: 0x1141FCC0 | isr3
[   65.986238] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[   65.986314] iwlwifi 0000:03:00.0: 0x01800112 | isr_pref
[   65.986391] iwlwifi 0000:03:00.0: 0x0001D0AC | wait_event
[   65.986468] iwlwifi 0000:03:00.0: 0x00000000 | l2p_control
[   65.986544] iwlwifi 0000:03:00.0: 0x00000000 | l2p_duration
[   65.986622] iwlwifi 0000:03:00.0: 0x00000000 | l2p_mhvalid
[   65.986700] iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
[   65.986778] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
[   65.986856] iwlwifi 0000:03:00.0: 0x25090952 | timestamp
[   65.986932] iwlwifi 0000:03:00.0: 0x00000000 | flow_handler
[   65.987095] iwlwifi 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[   65.987248] iwlwifi 0000:03:00.0: EVT_LOGT:0000040554:0x00000001:1208
[   65.987363] iwlwifi 0000:03:00.0: EVT_LOGT:0000040611:0x00000011:1551
[   65.987477] iwlwifi 0000:03:00.0: EVT_LOGT:0000040612:0x00000000:1555
[   65.987590] iwlwifi 0000:03:00.0: EVT_LOGT:0000040613:0x00020000:1555
[   65.987702] iwlwifi 0000:03:00.0: EVT_LOGT:0000040614:0x00020000:1568
[   65.987816] iwlwifi 0000:03:00.0: EVT_LOGT:0000040629:0x000001a8:0103
[   65.987930] iwlwifi 0000:03:00.0: EVT_LOGT:0000040630:0x95000301:1333
[   65.988043] iwlwifi 0000:03:00.0: EVT_LOGT:0000040631:0x00000000:1334
[   65.988157] iwlwifi 0000:03:00.0: EVT_LOGT:0000040632:0x00010000:1334
[   65.988271] iwlwifi 0000:03:00.0: EVT_LOGT:0000040633:0x010007ac:1334
[   65.988387] iwlwifi 0000:03:00.0: EVT_LOGT:0000040634:0x8c200050:1334
[   65.988500] iwlwifi 0000:03:00.0: EVT_LOGT:0000040635:0x01010838:1334
[   65.988614] iwlwifi 0000:03:00.0: EVT_LOGT:0000040637:0x8c210054:1334
[   65.988728] iwlwifi 0000:03:00.0: EVT_LOGT:0000040638:0x020008c4:1334
[   65.988842] iwlwifi 0000:03:00.0: EVT_LOGT:0000040640:0x8c400061:1334
[   65.988953] iwlwifi 0000:03:00.0: EVT_LOGT:0000040640:0x02010950:1334
[   65.989067] iwlwifi 0000:03:00.0: EVT_LOGT:0000040642:0x8c410062:1334
[   65.989180] iwlwifi 0000:03:00.0: EVT_LOGT:0000048121:0x010007ac:1333
[   65.989294] iwlwifi 0000:03:00.0: EVT_LOGT:0000048121:0x07aed500:1333
[   65.989407] iwlwifi 0000:03:00.0: EVT_LOGT:0000053220:0x00000000:0125
[   65.989531] iwlwifi 0000:03:00.0: FW error in SYNC CMD REPLY_ADD_STA
[   65.989647]  [<ffffffffc033069d>] iwl_trans_pcie_send_hcmd+0x44d/0x5a0 [iwlwifi]
[   65.989786] iwlwifi 0000:03:00.0: Adding station ff:ff:ff:ff:ff:ff failed.
[   65.989876] iwlwifi 0000:03:00.0: Command REPLY_CT_KILL_CONFIG_CMD failed: FW Error
[   65.989980] iwlwifi 0000:03:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[   65.990331] iwlwifi 0000:03:00.0: Unable to initialize device.
[  171.673122] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  171.679541] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[  171.900518] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  171.906974] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[  171.971099] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[  171.971112] iwlwifi 0000:03:00.0: CSR values:
[  171.971117] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[  171.971149] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X0048c704
[  171.971181] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[  171.971210] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[  171.971241] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[  171.971269] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[  171.971297] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
[  171.971325] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[  171.971353] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[  171.971382] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000074
[  171.971411] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X28360ffd
[  171.971442] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[  171.971470] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X00030001
[  171.971498] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080042
[  171.971526] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000005
[  171.971553] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[  171.971581] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[  171.971608] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[  171.971636] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[  171.971664] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X880babb7
[  171.971692] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[  171.971720] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[  171.971747] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X43f7ff57
[  171.971775] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[  171.971803] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[  171.971808] iwlwifi 0000:03:00.0: FH register values:
[  171.971867] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X0b9abd00
[  171.971917] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00b9abe0
[  171.971961] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000008
[  171.972006] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[  171.972050] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[  171.972094] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[  171.972138] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[  171.972183] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[  171.972222] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[  171.972227] iwlwifi 0000:03:00.0: Loaded firmware version: 9.176.4.1 build 15835
[  171.972395] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[  171.972399] iwlwifi 0000:03:00.0: Status: 0x0000004C, count: 5
[  171.972404] iwlwifi 0000:03:00.0: 0x00000005 | SYSASSERT                   
[  171.972409] iwlwifi 0000:03:00.0: 0x00023D2C | uPc
[  171.972412] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink1
[  171.972416] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink2
[  171.972420] iwlwifi 0000:03:00.0: 0x00000996 | interruptlink1
[  171.972424] iwlwifi 0000:03:00.0: 0x00000000 | interruptlink2
[  171.972428] iwlwifi 0000:03:00.0: 0xFFFFFFC0 | data1
[  171.972431] iwlwifi 0000:03:00.0: 0x0000017C | data2
[  171.972435] iwlwifi 0000:03:00.0: 0x000001DD | line
[  171.972439] iwlwifi 0000:03:00.0: 0x0001537B | beacon time
[  171.972443] iwlwifi 0000:03:00.0: 0x00003C85 | tsf low
[  171.972446] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
[  171.972450] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[  171.972454] iwlwifi 0000:03:00.0: 0x0000D194 | time gp2
[  171.972457] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[  171.972461] iwlwifi 0000:03:00.0: 0x000109B0 | uCode version
[  171.972465] iwlwifi 0000:03:00.0: 0x00000074 | hw version
[  171.972469] iwlwifi 0000:03:00.0: 0x0048C704 | board version
[  171.972473] iwlwifi 0000:03:00.0: 0x04080010 | hcmd
[  171.972476] iwlwifi 0000:03:00.0: 0x00122080 | isr0
[  171.972480] iwlwifi 0000:03:00.0: 0x00000000 | isr1
[  171.972484] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[  171.972488] iwlwifi 0000:03:00.0: 0x1141FCC0 | isr3
[  171.972491] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[  171.972495] iwlwifi 0000:03:00.0: 0x01800112 | isr_pref
[  171.972499] iwlwifi 0000:03:00.0: 0x0001D0AC | wait_event
[  171.972502] iwlwifi 0000:03:00.0: 0x00000000 | l2p_control
[  171.972506] iwlwifi 0000:03:00.0: 0x00000000 | l2p_duration
[  171.972510] iwlwifi 0000:03:00.0: 0x00000000 | l2p_mhvalid
[  171.972514] iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
[  171.972518] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
[  171.972525] iwlwifi 0000:03:00.0: 0x25090952 | timestamp
[  171.972531] iwlwifi 0000:03:00.0: 0x00000000 | flow_handler
[  171.972723] iwlwifi 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[  171.972785] iwlwifi 0000:03:00.0: EVT_LOGT:0000041017:0x00000001:1208
[  171.972840] iwlwifi 0000:03:00.0: EVT_LOGT:0000041074:0x00000011:1551
[  171.972909] iwlwifi 0000:03:00.0: EVT_LOGT:0000041075:0x00000000:1555
[  171.972950] iwlwifi 0000:03:00.0: EVT_LOGT:0000041076:0x00020000:1555
[  171.972986] iwlwifi 0000:03:00.0: EVT_LOGT:0000041077:0x00020000:1568
[  171.973021] iwlwifi 0000:03:00.0: EVT_LOGT:0000041092:0x000001a8:0103
[  171.973060] iwlwifi 0000:03:00.0: EVT_LOGT:0000041093:0x95000301:1333
[  171.973096] iwlwifi 0000:03:00.0: EVT_LOGT:0000041094:0x00000000:1334
[  171.973132] iwlwifi 0000:03:00.0: EVT_LOGT:0000041095:0x00010000:1334
[  171.973167] iwlwifi 0000:03:00.0: EVT_LOGT:0000041096:0x010007ac:1334
[  171.973202] iwlwifi 0000:03:00.0: EVT_LOGT:0000041097:0x8c200050:1334
[  171.973243] iwlwifi 0000:03:00.0: EVT_LOGT:0000041098:0x01010838:1334
[  171.973279] iwlwifi 0000:03:00.0: EVT_LOGT:0000041100:0x8c210054:1334
[  171.973314] iwlwifi 0000:03:00.0: EVT_LOGT:0000041101:0x020008c4:1334
[  171.973353] iwlwifi 0000:03:00.0: EVT_LOGT:0000041103:0x8c400061:1334
[  171.973388] iwlwifi 0000:03:00.0: EVT_LOGT:0000041103:0x02010950:1334
[  171.973423] iwlwifi 0000:03:00.0: EVT_LOGT:0000041105:0x8c410062:1334
[  171.973458] iwlwifi 0000:03:00.0: EVT_LOGT:0000048590:0x010007ac:1333
[  171.973494] iwlwifi 0000:03:00.0: EVT_LOGT:0000048590:0x07aed500:1333
[  171.973536] iwlwifi 0000:03:00.0: EVT_LOGT:0000053674:0x00000000:0125
[  171.973651] iwlwifi 0000:03:00.0: FW error in SYNC CMD REPLY_ADD_STA
[  171.973755]  [<ffffffffc033069d>] iwl_trans_pcie_send_hcmd+0x44d/0x5a0 [iwlwifi]
[  171.974117] iwlwifi 0000:03:00.0: Adding station ff:ff:ff:ff:ff:ff failed.
[  171.974127] iwlwifi 0000:03:00.0: Command REPLY_CT_KILL_CONFIG_CMD failed: FW Error
[  171.974131] iwlwifi 0000:03:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[  171.974469] iwlwifi 0000:03:00.0: Unable to initialize device.

```

And I've been unable to connect since, except for a few brief moments last night.
So today I've tried several things.  I set our old, known good (for my  Ubuntu install) router up as a wireless bridge with our new router.  No  dice, I can see but not connect to any networks, So, I tried using a  wired network to update to 16.04 since that seems to be a common fix for  the intel cards.  Same result.  Checked my CRDA setting, and saw it had  been reset to "unset".  So I reset it to US.  Still can't connect.  So,  now, I'm here, asking for help.  I'm at my wits end.  Here is my  Wireless Script Info:
```


########## wireless info START ##########

Report from: 08 Jul 2016 16:39 CDT -0500

Booted last: 08 Jul 2016 00:00 CDT -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-28-generic #47-Ubuntu SMP Fri Jun 24 10:09:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

GNOME Flashback (Compiz)

##### lspci #############################

03:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:422b] (rev 09)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN [8086:1101]
    Kernel driver in use: iwlwifi

0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 06)
    Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:04b7]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0781:5571 SanDisk Corp. Cruzer Fit
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0408:2fb1 Quanta Computer, Inc. 
Bus 001 Device 003: ID 0955:7002 NVidia Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                233472  0
mac80211              737280  1 iwldvm
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
iwlwifi               200704  1 iwldvm
dell_laptop            20480  0
cfg80211              565248  3 iwlwifi,mac80211,iwldvm
dcdbas                 16384  1 dell_laptop
wmi                    20480  1 dell_wmi
video                  40960  2 dell_wmi,dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp10s0   Link encap:Ethernet  HWaddr <MAC 'enp10s0' [IF1]>  
          inet addr:192.168.1.122  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::642d:d5db:8931:d3d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1624827 (1.6 MB)  TX bytes:188713 (188.7 KB)

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp10s0   no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp10s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp10s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       877     1  0 16:31 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp10s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp10s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:0a:00.0/net/enp10s0
GENERAL.IP-IFACE:                       enp10s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       4b725651-8b2d-4f19-9b1c-a4ab8aaa309a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4b725651-8b2d-4f19-9b1c-a4ab8aaa309a | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.122/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        server_name = ecosystem.home.cisco.com
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[6]:                        ip_address = 192.168.1.122
DHCP4.OPTION[7]:                        requested_static_routes = 1
DHCP4.OPTION[8]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1468099885
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = Artemis
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::642d:d5db:8931:d3d3/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Ultimate-N 6300 (3x3 AGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-28-generic
GENERAL.FIRMWARE-VERSION:               9.221.4.1 build 25532
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/house]] (600 root)
[connection] id=house | type=wifi | permissions=user:krystal:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=house
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/dd-wrt-3]] (600 root)
[connection] id=dd-wrt-3 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=dd-wrt-3
[ipv4] method=manual
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp10s0   no frequency information.

lo        no frequency information.

wlp3s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

wlp3s0    Interface doesn't support scanning : Network is down

enp10s0   Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[iwldvm]
filename:       /lib/modules/4.4.0-28-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     6A40B68AAA6792A5BDEA010
depends:        mac80211,iwlwifi,cfg80211
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/4.4.0-28-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-28-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-13.ucode
firmware:       iwlwifi-7265-13.ucode
firmware:       iwlwifi-3160-13.ucode
firmware:       iwlwifi-7260-13.ucode
firmware:       iwlwifi-8000-13.ucode
srcversion:     651BF6CBF283F6F817B8F3A
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full,  2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.4.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwldvm]
force_cam: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 8
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: N
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 1
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=8 led_mode=1 bt_coex_active=0 power_save=0

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   92.641548] wlp3s0:  Failed check-sdata-in-driver check, flags: 0x0
[  114.685590] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready

########## wireless info END ############


```

Please!  HELP!



[   65.355401] iwlwifi 0000:03:00.0: 0x00000000 | flow_handler
[   65.355566] iwlwifi 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[   65.355717] iwlwifi 0000:03:00.0: EVT_LOGT:0000040812:0x00000001:1208
[   65.355835] iwlwifi 0000:03:00.0: EVT_LOGT:0000040869:0x00000011:1551
[   65.355950] iwlwifi 0000:03:00.0: EVT_LOGT:0000040870:0x00000000:1555
[   65.356066] iwlwifi 0000:03:00.0: EVT_LOGT:0000040871:0x00020000:1555
[   65.356184] iwlwifi 0000:03:00.0: EVT_LOGT:0000040871:0x00020000:1568
[   65.356339] iwlwifi 0000:03:00.0: EVT_LOGT:0000040887:0x000001a8:0103
[   65.356457] iwlwifi 0000:03:00.0: EVT_LOGT:0000040888:0x95000301:1333
[   65.356573] iwlwifi 0000:03:00.0: EVT_LOGT:0000040889:0x00000000:1334
[   65.356689] iwlwifi 0000:03:00.0: EVT_LOGT:0000040889:0x00010000:1334
[   65.356805] iwlwifi 0000:03:00.0: EVT_LOGT:0000040890:0x010007ac:1334
[   65.356923] iwlwifi 0000:03:00.0: EVT_LOGT:0000040892:0x8c200050:1334
[   65.357041] iwlwifi 0000:03:00.0: EVT_LOGT:0000040893:0x01010838:1334
[   65.357158] iwlwifi 0000:03:00.0: EVT_LOGT:0000040895:0x8c210054:1334
[   65.357277] iwlwifi 0000:03:00.0: EVT_LOGT:0000040896:0x020008c4:1334
[   65.357392] iwlwifi 0000:03:00.0: EVT_LOGT:0000040898:0x8c400061:1334
[   65.357508] iwlwifi 0000:03:00.0: EVT_LOGT:0000040898:0x02010950:1334
[   65.357625] iwlwifi 0000:03:00.0: EVT_LOGT:0000040900:0x8c410062:1334
[   65.357743] iwlwifi 0000:03:00.0: EVT_LOGT:0000048381:0x010007ac:1333
[   65.357861] iwlwifi 0000:03:00.0: EVT_LOGT:0000048381:0x07aed500:1333
[   65.357980] iwlwifi 0000:03:00.0: EVT_LOGT:0000053464:0x00000000:0125
[   65.358136] iwlwifi 0000:03:00.0: FW error in SYNC CMD REPLY_ADD_STA
[   65.358264]  [<ffffffffc033069d>] iwl_trans_pcie_send_hcmd+0x44d/0x5a0 [iwlwifi]
[   65.358441] iwlwifi 0000:03:00.0: Adding station ff:ff:ff:ff:ff:ff failed.
[   65.358525] iwlwifi 0000:03:00.0: Command REPLY_CT_KILL_CONFIG_CMD failed: FW Error
[   65.358628] iwlwifi 0000:03:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[   65.358948] iwlwifi 0000:03:00.0: Unable to initialize device.
[   65.364815] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   65.371240] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   65.594140] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   65.600565] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   65.664374] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   65.664504] iwlwifi 0000:03:00.0: CSR values:
[   65.664576] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   65.664707] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X0048c704
[   65.664811] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[   65.664926] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[   65.665035] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[   65.665141] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   65.665248] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
[   65.665355] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[   65.665462] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[   65.665569] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000074
[   65.665675] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X28360ffd
[   65.665782] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[   65.665889] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X00030001
[   65.665995] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080042
[   65.666102] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000005
[   65.666208] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   65.666315] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   65.666423] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   65.666535] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[   65.666642] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X880babb7
[   65.666748] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   65.666855] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   65.666962] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X43f7ff57
[   65.667069] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   65.667173] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   65.667255] iwlwifi 0000:03:00.0: FH register values:
[   65.667367] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X0b9abd00
[   65.667509] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00b9abe0
[   65.667697] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000008
[   65.667838] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[   65.667981] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   65.668123] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   65.668282] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   65.668426] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   65.668570] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   65.668676] iwlwifi 0000:03:00.0: Loaded firmware version: 9.176.4.1 build 15835
[   65.669027] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[   65.669106] iwlwifi 0000:03:00.0: Status: 0x0000004C, count: 5
[   65.669184] iwlwifi 0000:03:00.0: 0x00000005 | SYSASSERT                   
[   65.669265] iwlwifi 0000:03:00.0: 0x00023D2C | uPc
[   65.669340] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink1
[   65.669416] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink2
[   65.669493] iwlwifi 0000:03:00.0: 0x00000996 | interruptlink1
[   65.669570] iwlwifi 0000:03:00.0: 0x00000000 | interruptlink2
[   65.669647] iwlwifi 0000:03:00.0: 0xFFFFFFC0 | data1
[   65.669723] iwlwifi 0000:03:00.0: 0x0000017C | data2
[   65.669798] iwlwifi 0000:03:00.0: 0x000001DD | line
[   65.669873] iwlwifi 0000:03:00.0: 0x00015371 | beacon time
[   65.669956] iwlwifi 0000:03:00.0: 0x00003C8F | tsf low
[   65.670040] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
[   65.670117] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[   65.670194] iwlwifi 0000:03:00.0: 0x0000D10D | time gp2
[   65.670270] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[   65.670347] iwlwifi 0000:03:00.0: 0x000109B0 | uCode version
[   65.670425] iwlwifi 0000:03:00.0: 0x00000074 | hw version
[   65.670503] iwlwifi 0000:03:00.0: 0x0048C704 | board version
[   65.670580] iwlwifi 0000:03:00.0: 0x04080010 | hcmd
[   65.670656] iwlwifi 0000:03:00.0: 0x00122080 | isr0
[   65.670732] iwlwifi 0000:03:00.0: 0x00000000 | isr1
[   65.670808] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[   65.670884] iwlwifi 0000:03:00.0: 0x1141FCC0 | isr3
[   65.670960] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[   65.671035] iwlwifi 0000:03:00.0: 0x01800112 | isr_pref
[   65.671113] iwlwifi 0000:03:00.0: 0x0001D0AC | wait_event
[   65.671194] iwlwifi 0000:03:00.0: 0x00000000 | l2p_control
[   65.671272] iwlwifi 0000:03:00.0: 0x00000000 | l2p_duration
[   65.671350] iwlwifi 0000:03:00.0: 0x00000000 | l2p_mhvalid
[   65.671427] iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
[   65.671505] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
[   65.671583] iwlwifi 0000:03:00.0: 0x25090952 | timestamp
[   65.675237] iwlwifi 0000:03:00.0: 0x00000000 | flow_handler
[   65.675418] iwlwifi 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[   65.675568] iwlwifi 0000:03:00.0: EVT_LOGT:0000040872:0x00000001:1208
[   65.675685] iwlwifi 0000:03:00.0: EVT_LOGT:0000040929:0x00000011:1551
[   65.675798] iwlwifi 0000:03:00.0: EVT_LOGT:0000040930:0x00000000:1555
[   65.675912] iwlwifi 0000:03:00.0: EVT_LOGT:0000040931:0x00020000:1555
[   65.676035] iwlwifi 0000:03:00.0: EVT_LOGT:0000040931:0x00020000:1568
[   65.676148] iwlwifi 0000:03:00.0: EVT_LOGT:0000040947:0x000001a8:0103
[   65.676262] iwlwifi 0000:03:00.0: EVT_LOGT:0000040948:0x95000301:1333
[   65.676375] iwlwifi 0000:03:00.0: EVT_LOGT:0000040949:0x00000000:1334
[   65.676487] iwlwifi 0000:03:00.0: EVT_LOGT:0000040949:0x00010000:1334
[   65.676600] iwlwifi 0000:03:00.0: EVT_LOGT:0000040950:0x010007ac:1334
[   65.676714] iwlwifi 0000:03:00.0: EVT_LOGT:0000040952:0x8c200050:1334
[   65.676828] iwlwifi 0000:03:00.0: EVT_LOGT:0000040953:0x01010838:1334
[   65.676942] iwlwifi 0000:03:00.0: EVT_LOGT:0000040955:0x8c210054:1334
[   65.677055] iwlwifi 0000:03:00.0: EVT_LOGT:0000040956:0x020008c4:1334
[   65.677169] iwlwifi 0000:03:00.0: EVT_LOGT:0000040958:0x8c400061:1334
[   65.677283] iwlwifi 0000:03:00.0: EVT_LOGT:0000040958:0x02010950:1334
[   65.677396] iwlwifi 0000:03:00.0: EVT_LOGT:0000040960:0x8c410062:1334
[   65.677510] iwlwifi 0000:03:00.0: EVT_LOGT:0000048439:0x010007ac:1333
[   65.677624] iwlwifi 0000:03:00.0: EVT_LOGT:0000048440:0x07aed500:1333
[   65.677738] iwlwifi 0000:03:00.0: EVT_LOGT:0000053539:0x00000000:0125
[   65.677861] iwlwifi 0000:03:00.0: FW error in SYNC CMD REPLY_ADD_STA
[   65.677982]  [<ffffffffc033069d>] iwl_trans_pcie_send_hcmd+0x44d/0x5a0 [iwlwifi]
[   65.678108] iwlwifi 0000:03:00.0: Adding station ff:ff:ff:ff:ff:ff failed.
[   65.678191] iwlwifi 0000:03:00.0: Command REPLY_CT_KILL_CONFIG_CMD failed: FW Error
[   65.678294] iwlwifi 0000:03:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[   65.678613] iwlwifi 0000:03:00.0: Unable to initialize device.
[   65.682500] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   65.688945] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   65.909788] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   65.916258] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[   65.979788] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   65.979917] iwlwifi 0000:03:00.0: CSR values:
[   65.979991] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   65.980141] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X0048c704
[   65.980249] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[   65.980355] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[   65.980460] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[   65.980567] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   65.980673] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
[   65.980780] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[   65.980884] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[   65.980991] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000074
[   65.981098] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X28360ffd
[   65.981202] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[   65.981309] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X00030001
[   65.981415] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080042
[   65.981521] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000005
[   65.981629] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   65.981735] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   65.981842] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   65.981949] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[   65.982055] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X880babb7
[   65.982162] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   65.982268] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   65.982375] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X43f7ff57
[   65.982482] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   65.982589] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   65.982670] iwlwifi 0000:03:00.0: FH register values:
[   65.982785] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X0b9abd00
[   65.982926] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00b9abe0
[   65.983068] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000008
[   65.983210] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[   65.983352] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   65.983494] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   65.983636] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   65.983782] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   65.983922] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   65.984027] iwlwifi 0000:03:00.0: Loaded firmware version: 9.176.4.1 build 15835
[   65.984297] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[   65.984377] iwlwifi 0000:03:00.0: Status: 0x0000004C, count: 5
[   65.984456] iwlwifi 0000:03:00.0: 0x00000005 | SYSASSERT                   
[   65.984538] iwlwifi 0000:03:00.0: 0x00023D2C | uPc
[   65.984620] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink1
[   65.984697] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink2
[   65.984774] iwlwifi 0000:03:00.0: 0x00000996 | interruptlink1
[   65.984856] iwlwifi 0000:03:00.0: 0x00000000 | interruptlink2
[   65.984933] iwlwifi 0000:03:00.0: 0xFFFFFFC0 | data1
[   65.985008] iwlwifi 0000:03:00.0: 0x0000017C | data2
[   65.985083] iwlwifi 0000:03:00.0: 0x000001DD | line
[   65.985158] iwlwifi 0000:03:00.0: 0x00015372 | beacon time
[   65.985234] iwlwifi 0000:03:00.0: 0x00003C8E | tsf low
[   65.985309] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
[   65.985384] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[   65.985460] iwlwifi 0000:03:00.0: 0x0000CFCE | time gp2
[   65.985535] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[   65.985620] iwlwifi 0000:03:00.0: 0x000109B0 | uCode version
[   65.985698] iwlwifi 0000:03:00.0: 0x00000074 | hw version
[   65.985776] iwlwifi 0000:03:00.0: 0x0048C704 | board version
[   65.985853] iwlwifi 0000:03:00.0: 0x04080010 | hcmd
[   65.985929] iwlwifi 0000:03:00.0: 0x02322080 | isr0
[   65.986005] iwlwifi 0000:03:00.0: 0x00000000 | isr1
[   65.986086] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[   65.986162] iwlwifi 0000:03:00.0: 0x1141FCC0 | isr3
[   65.986238] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[   65.986314] iwlwifi 0000:03:00.0: 0x01800112 | isr_pref
[   65.986391] iwlwifi 0000:03:00.0: 0x0001D0AC | wait_event
[   65.986468] iwlwifi 0000:03:00.0: 0x00000000 | l2p_control
[   65.986544] iwlwifi 0000:03:00.0: 0x00000000 | l2p_duration
[   65.986622] iwlwifi 0000:03:00.0: 0x00000000 | l2p_mhvalid
[   65.986700] iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
[   65.986778] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
[   65.986856] iwlwifi 0000:03:00.0: 0x25090952 | timestamp
[   65.986932] iwlwifi 0000:03:00.0: 0x00000000 | flow_handler
[   65.987095] iwlwifi 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[   65.987248] iwlwifi 0000:03:00.0: EVT_LOGT:0000040554:0x00000001:1208
[   65.987363] iwlwifi 0000:03:00.0: EVT_LOGT:0000040611:0x00000011:1551
[   65.987477] iwlwifi 0000:03:00.0: EVT_LOGT:0000040612:0x00000000:1555
[   65.987590] iwlwifi 0000:03:00.0: EVT_LOGT:0000040613:0x00020000:1555
[   65.987702] iwlwifi 0000:03:00.0: EVT_LOGT:0000040614:0x00020000:1568
[   65.987816] iwlwifi 0000:03:00.0: EVT_LOGT:0000040629:0x000001a8:0103
[   65.987930] iwlwifi 0000:03:00.0: EVT_LOGT:0000040630:0x95000301:1333
[   65.988043] iwlwifi 0000:03:00.0: EVT_LOGT:0000040631:0x00000000:1334
[   65.988157] iwlwifi 0000:03:00.0: EVT_LOGT:0000040632:0x00010000:1334
[   65.988271] iwlwifi 0000:03:00.0: EVT_LOGT:0000040633:0x010007ac:1334
[   65.988387] iwlwifi 0000:03:00.0: EVT_LOGT:0000040634:0x8c200050:1334
[   65.988500] iwlwifi 0000:03:00.0: EVT_LOGT:0000040635:0x01010838:1334
[   65.988614] iwlwifi 0000:03:00.0: EVT_LOGT:0000040637:0x8c210054:1334
[   65.988728] iwlwifi 0000:03:00.0: EVT_LOGT:0000040638:0x020008c4:1334
[   65.988842] iwlwifi 0000:03:00.0: EVT_LOGT:0000040640:0x8c400061:1334
[   65.988953] iwlwifi 0000:03:00.0: EVT_LOGT:0000040640:0x02010950:1334
[   65.989067] iwlwifi 0000:03:00.0: EVT_LOGT:0000040642:0x8c410062:1334
[   65.989180] iwlwifi 0000:03:00.0: EVT_LOGT:0000048121:0x010007ac:1333
[   65.989294] iwlwifi 0000:03:00.0: EVT_LOGT:0000048121:0x07aed500:1333
[   65.989407] iwlwifi 0000:03:00.0: EVT_LOGT:0000053220:0x00000000:0125
[   65.989531] iwlwifi 0000:03:00.0: FW error in SYNC CMD REPLY_ADD_STA
[   65.989647]  [<ffffffffc033069d>] iwl_trans_pcie_send_hcmd+0x44d/0x5a0 [iwlwifi]
[   65.989786] iwlwifi 0000:03:00.0: Adding station ff:ff:ff:ff:ff:ff failed.
[   65.989876] iwlwifi 0000:03:00.0: Command REPLY_CT_KILL_CONFIG_CMD failed: FW Error
[   65.989980] iwlwifi 0000:03:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[   65.990331] iwlwifi 0000:03:00.0: Unable to initialize device.
[  171.673122] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  171.679541] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[  171.900518] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  171.906974] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x0
[  171.971099] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[  171.971112] iwlwifi 0000:03:00.0: CSR values:
[  171.971117] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[  171.971149] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X0048c704
[  171.971181] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[  171.971210] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[  171.971241] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[  171.971269] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[  171.971297] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
[  171.971325] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[  171.971353] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[  171.971382] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000074
[  171.971411] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X28360ffd
[  171.971442] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[  171.971470] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X00030001
[  171.971498] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080042
[  171.971526] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000005
[  171.971553] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[  171.971581] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[  171.971608] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[  171.971636] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[  171.971664] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X880babb7
[  171.971692] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[  171.971720] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[  171.971747] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X43f7ff57
[  171.971775] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[  171.971803] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[  171.971808] iwlwifi 0000:03:00.0: FH register values:
[  171.971867] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X0b9abd00
[  171.971917] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00b9abe0
[  171.971961] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000008
[  171.972006] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[  171.972050] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[  171.972094] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[  171.972138] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[  171.972183] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[  171.972222] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[  171.972227] iwlwifi 0000:03:00.0: Loaded firmware version: 9.176.4.1 build 15835
[  171.972395] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[  171.972399] iwlwifi 0000:03:00.0: Status: 0x0000004C, count: 5
[  171.972404] iwlwifi 0000:03:00.0: 0x00000005 | SYSASSERT                   
[  171.972409] iwlwifi 0000:03:00.0: 0x00023D2C | uPc
[  171.972412] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink1
[  171.972416] iwlwifi 0000:03:00.0: 0x00023E2A | branchlink2
[  171.972420] iwlwifi 0000:03:00.0: 0x00000996 | interruptlink1
[  171.972424] iwlwifi 0000:03:00.0: 0x00000000 | interruptlink2
[  171.972428] iwlwifi 0000:03:00.0: 0xFFFFFFC0 | data1
[  171.972431] iwlwifi 0000:03:00.0: 0x0000017C | data2
[  171.972435] iwlwifi 0000:03:00.0: 0x000001DD | line
[  171.972439] iwlwifi 0000:03:00.0: 0x0001537B | beacon time
[  171.972443] iwlwifi 0000:03:00.0: 0x00003C85 | tsf low
[  171.972446] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
[  171.972450] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[  171.972454] iwlwifi 0000:03:00.0: 0x0000D194 | time gp2
[  171.972457] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[  171.972461] iwlwifi 0000:03:00.0: 0x000109B0 | uCode version
[  171.972465] iwlwifi 0000:03:00.0: 0x00000074 | hw version
[  171.972469] iwlwifi 0000:03:00.0: 0x0048C704 | board version
[  171.972473] iwlwifi 0000:03:00.0: 0x04080010 | hcmd
[  171.972476] iwlwifi 0000:03:00.0: 0x00122080 | isr0
[  171.972480] iwlwifi 0000:03:00.0: 0x00000000 | isr1
[  171.972484] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[  171.972488] iwlwifi 0000:03:00.0: 0x1141FCC0 | isr3
[  171.972491] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[  171.972495] iwlwifi 0000:03:00.0: 0x01800112 | isr_pref
[  171.972499] iwlwifi 0000:03:00.0: 0x0001D0AC | wait_event
[  171.972502] iwlwifi 0000:03:00.0: 0x00000000 | l2p_control
[  171.972506] iwlwifi 0000:03:00.0: 0x00000000 | l2p_duration
[  171.972510] iwlwifi 0000:03:00.0: 0x00000000 | l2p_mhvalid
[  171.972514] iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
[  171.972518] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
[  171.972525] iwlwifi 0000:03:00.0: 0x25090952 | timestamp
[  171.972531] iwlwifi 0000:03:00.0: 0x00000000 | flow_handler
[  171.972723] iwlwifi 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[  171.972785] iwlwifi 0000:03:00.0: EVT_LOGT:0000041017:0x00000001:1208
[  171.972840] iwlwifi 0000:03:00.0: EVT_LOGT:0000041074:0x00000011:1551
[  171.972909] iwlwifi 0000:03:00.0: EVT_LOGT:0000041075:0x00000000:1555
[  171.972950] iwlwifi 0000:03:00.0: EVT_LOGT:0000041076:0x00020000:1555
[  171.972986] iwlwifi 0000:03:00.0: EVT_LOGT:0000041077:0x00020000:1568
[  171.973021] iwlwifi 0000:03:00.0: EVT_LOGT:0000041092:0x000001a8:0103
[  171.973060] iwlwifi 0000:03:00.0: EVT_LOGT:0000041093:0x95000301:1333
[  171.973096] iwlwifi 0000:03:00.0: EVT_LOGT:0000041094:0x00000000:1334
[  171.973132] iwlwifi 0000:03:00.0: EVT_LOGT:0000041095:0x00010000:1334
[  171.973167] iwlwifi 0000:03:00.0: EVT_LOGT:0000041096:0x010007ac:1334
[  171.973202] iwlwifi 0000:03:00.0: EVT_LOGT:0000041097:0x8c200050:1334
[  171.973243] iwlwifi 0000:03:00.0: EVT_LOGT:0000041098:0x01010838:1334
[  171.973279] iwlwifi 0000:03:00.0: EVT_LOGT:0000041100:0x8c210054:1334
[  171.973314] iwlwifi 0000:03:00.0: EVT_LOGT:0000041101:0x020008c4:1334
[  171.973353] iwlwifi 0000:03:00.0: EVT_LOGT:0000041103:0x8c400061:1334
[  171.973388] iwlwifi 0000:03:00.0: EVT_LOGT:0000041103:0x02010950:1334
[  171.973423] iwlwifi 0000:03:00.0: EVT_LOGT:0000041105:0x8c410062:1334
[  171.973458] iwlwifi 0000:03:00.0: EVT_LOGT:0000048590:0x010007ac:1333
[  171.973494] iwlwifi 0000:03:00.0: EVT_LOGT:0000048590:0x07aed500:1333
[  171.973536] iwlwifi 0000:03:00.0: EVT_LOGT:0000053674:0x00000000:0125
[  171.973651] iwlwifi 0000:03:00.0: FW error in SYNC CMD REPLY_ADD_STA
[  171.973755]  [<ffffffffc033069d>] iwl_trans_pcie_send_hcmd+0x44d/0x5a0 [iwlwifi]
[  171.974117] iwlwifi 0000:03:00.0: Adding station ff:ff:ff:ff:ff:ff failed.
[  171.974127] iwlwifi 0000:03:00.0: Command REPLY_CT_KILL_CONFIG_CMD failed: FW Error
[  171.974131] iwlwifi 0000:03:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[  171.974469] iwlwifi 0000:03:00.0: Unable to initialize device.
[/CODE]

And I've been unable to connect since, except for a few brief moments last night.
So today I've tried several things.  I set our old, known good (for my  Ubuntu install) router up as a wireless bridge with our new router.  No  dice, I can see but not connect to any networks, So, I tried using a  wired network to update to 16.04 since that seems to be a common fix for  the intel cards.  Same result.  Checked my CRDA setting, and saw it had  been reset to "unset".  So I reset it to US.  Still can't connect.  So,  now, I'm here, asking for help.  I'm at my wits end.  Here is my  Wireless Script Info:
```


########## wireless info START ##########

Report from: 08 Jul 2016 16:39 CDT -0500

Booted last: 08 Jul 2016 00:00 CDT -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-28-generic #47-Ubuntu SMP Fri Jun 24 10:09:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

GNOME Flashback (Compiz)

##### lspci #############################

03:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:422b] (rev 09)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN [8086:1101]
    Kernel driver in use: iwlwifi

0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 06)
    Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:04b7]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0781:5571 SanDisk Corp. Cruzer Fit
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0408:2fb1 Quanta Computer, Inc. 
Bus 001 Device 003: ID 0955:7002 NVidia Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                233472  0
mac80211              737280  1 iwldvm
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
iwlwifi               200704  1 iwldvm
dell_laptop            20480  0
cfg80211              565248  3 iwlwifi,mac80211,iwldvm
dcdbas                 16384  1 dell_laptop
wmi                    20480  1 dell_wmi
video                  40960  2 dell_wmi,dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp10s0   Link encap:Ethernet  HWaddr <MAC 'enp10s0' [IF1]>  
          inet addr:192.168.1.122  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::642d:d5db:8931:d3d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1624827 (1.6 MB)  TX bytes:188713 (188.7 KB)

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp10s0   no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp10s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp10s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       877     1  0 16:31 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp10s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp10s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:0a:00.0/net/enp10s0
GENERAL.IP-IFACE:                       enp10s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       4b725651-8b2d-4f19-9b1c-a4ab8aaa309a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4b725651-8b2d-4f19-9b1c-a4ab8aaa309a | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.122/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        server_name = ecosystem.home.cisco.com
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[6]:                        ip_address = 192.168.1.122
DHCP4.OPTION[7]:                        requested_static_routes = 1
DHCP4.OPTION[8]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1468099885
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = Artemis
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::642d:d5db:8931:d3d3/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Ultimate-N 6300 (3x3 AGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-28-generic
GENERAL.FIRMWARE-VERSION:               9.221.4.1 build 25532
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/house]] (600 root)
[connection] id=house | type=wifi | permissions=user:krystal:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=house
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/dd-wrt-3]] (600 root)
[connection] id=dd-wrt-3 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=dd-wrt-3
[ipv4] method=manual
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp10s0   no frequency information.

lo        no frequency information.

wlp3s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

wlp3s0    Interface doesn't support scanning : Network is down

enp10s0   Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[iwldvm]
filename:       /lib/modules/4.4.0-28-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     6A40B68AAA6792A5BDEA010
depends:        mac80211,iwlwifi,cfg80211
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/4.4.0-28-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-28-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-13.ucode
firmware:       iwlwifi-7265-13.ucode
firmware:       iwlwifi-3160-13.ucode
firmware:       iwlwifi-7260-13.ucode
firmware:       iwlwifi-8000-13.ucode
srcversion:     651BF6CBF283F6F817B8F3A
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full,  2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.4.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwldvm]
force_cam: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 8
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: N
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 1
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=8 led_mode=1 bt_coex_active=0 power_save=0

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   92.641548] wlp3s0:  Failed check-sdata-in-driver check, flags: 0x0
[  114.685590] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready

########## wireless info END ############


```

And Here is the output of lshw -C network

```

  *-network DISABLED
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 09
       serial: 00:15:00:55:01:24
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-28-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:36 memory:d7400000-d7401fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: enp10s0
       version: 06
       serial: 14:fe:b5:99:aa:ea
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:34 ioport:2000(size=256) memory:d6904000-d6904fff memory:d6900000-d6903fff


```


Please help me get my wifi back!?!

---

### Post by jeremy31 on 2016-07-09
I wonder if the firmware isn't corrupted try ```
sudo apt-get install --reinstall linux-firmware
```

Shut down the computer and do a cold boot

---

