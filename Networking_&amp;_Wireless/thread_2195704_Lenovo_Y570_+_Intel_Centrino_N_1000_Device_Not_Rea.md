---
title: "Lenovo Y570 + Intel Centrino N 1000 Device Not Ready"
date: 2013-12-25
forum: Networking &amp; Wireless
---

### Post by mprihoda13 on 2013-12-25
I recently installed 13.04 and haven't been able to get the wifi working. I have tried reinstalling the drivers/firmware and using windows wireless drivers but to no avail. I reinstalled the OS twice already to see if there was a problem with installation but that also has not helped. Currently I get the message that the "Device not Ready" in the drop down menu on the Network Manager. I haven't been able to find out much in terms of help for this particular wireless card.

---

### Post by chili555 on 2013-12-26
What does this tell us, from a terminal:```
rfkill list all
dmesg | grep iwl
```

---

### Post by mprihoda13 on 2013-12-26
From rfkill list all I get:

```
mikey@mikey-Lenovo-IdeaPad-Y570:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```


and dmesg | grep iwl:

```
[14904.580738] iwlwifi 0000:08:00.0: 0x00000000 | time gp3
[14904.580753] iwlwifi 0000:08:00.0: 0x0001271F | uCode version
[14904.580767] iwlwifi 0000:08:00.0: 0x0000006C | hw version
[14904.580779] iwlwifi 0000:08:00.0: 0x00C8330C | board version
[14904.580794] iwlwifi 0000:08:00.0: 0x00000000 | hcmd
[14904.580797] iwlwifi 0000:08:00.0: 0x00122000 | isr0
[14904.580799] iwlwifi 0000:08:00.0: 0x00000000 | isr1
[14904.580800] iwlwifi 0000:08:00.0: 0x00000002 | isr2
[14904.580802] iwlwifi 0000:08:00.0: 0x004000C0 | isr3
[14904.580803] iwlwifi 0000:08:00.0: 0x00000000 | isr4
[14904.580804] iwlwifi 0000:08:00.0: 0x00000000 | isr_pref
[14904.580805] iwlwifi 0000:08:00.0: 0x00002BFE | wait_event
[14904.580807] iwlwifi 0000:08:00.0: 0x00000000 | l2p_control
[14904.580808] iwlwifi 0000:08:00.0: 0x00000000 | l2p_duration
[14904.580809] iwlwifi 0000:08:00.0: 0x00000000 | l2p_mhvalid
[14904.580811] iwlwifi 0000:08:00.0: 0x00100040 | l2p_addr_match
[14904.580812] iwlwifi 0000:08:00.0: 0x00000007 | lmpm_pmg_sel
[14904.580813] iwlwifi 0000:08:00.0: 0x00000000 | timestamp
[14904.580814] iwlwifi 0000:08:00.0: 0x0000F808 | flow_handler
[14904.580877] iwlwifi 0000:08:00.0: Start IWL Event Log Dump: display last 5 entries
[14904.580897] iwlwifi 0000:08:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[14904.580910] iwlwifi 0000:08:00.0: EVT_LOGT:0000000021:0x00000000:1208
[14904.580923] iwlwifi 0000:08:00.0: EVT_LOGT:0000001004:0x00000001:0071
[14904.580938] iwlwifi 0000:08:00.0: EVT_LOGT:0000001080:0x00000002:0071
[14904.580954] iwlwifi 0000:08:00.0: EVT_LOGT:0000001086:0x00000000:0125
[14904.580962] iwlwifi 0000:08:00.0: BUG_ON, Stop restarting
[14904.581298] iwlwifi 0000:08:00.0: Failed to run INIT ucode: -5
[14904.581379] iwlwifi 0000:08:00.0: Unable to initialize device.
[14904.583524] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[14904.591103] iwlwifi 0000:08:00.0: Radio type=0x0-0x0-0x3
[14904.599675] iwlwifi 0000:08:00.0: Microcode SW error detected.  Restarting 0x82000000.
[14904.599695] iwlwifi 0000:08:00.0: CSR values:
[14904.599715] iwlwifi 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[14904.599723] iwlwifi 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c8330c
[14904.599730] iwlwifi 0000:08:00.0:          CSR_INT_COALESCING: 0X00000040
[14904.599737] iwlwifi 0000:08:00.0:                     CSR_INT: 0X80000000
[14904.599744] iwlwifi 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[14904.599752] iwlwifi 0000:08:00.0:           CSR_FH_INT_STATUS: 0X40010000
[14904.599759] iwlwifi 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[14904.599765] iwlwifi 0000:08:00.0:                   CSR_RESET: 0X00000000
[14904.599772] iwlwifi 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[14904.599778] iwlwifi 0000:08:00.0:                  CSR_HW_REV: 0X0000006c
[14904.599784] iwlwifi 0000:08:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[14904.599791] iwlwifi 0000:08:00.0:               CSR_EEPROM_GP: 0X90000001
[14904.599797] iwlwifi 0000:08:00.0:              CSR_OTP_GP_REG: 0X00210801
[14904.599802] iwlwifi 0000:08:00.0:                 CSR_GIO_REG: 0X00080046
[14904.599808] iwlwifi 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00000000
[14904.599815] iwlwifi 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[14904.599820] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[14904.599826] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[14904.599834] iwlwifi 0000:08:00.0:                 CSR_LED_REG: 0X00000018
[14904.599840] iwlwifi 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[14904.599845] iwlwifi 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[14904.599851] iwlwifi 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[14904.599857] iwlwifi 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[14904.599863] iwlwifi 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[14904.599866] iwlwifi 0000:08:00.0: FH register values:
[14904.599887] iwlwifi 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X136f3100
[14904.599906] iwlwifi 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0136ad40
[14904.599923] iwlwifi 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[14904.599944] iwlwifi 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[14904.599963] iwlwifi 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[14904.599981] iwlwifi 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[14904.599999] iwlwifi 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[14904.600016] iwlwifi 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[14904.600039] iwlwifi 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[14904.600048] iwlwifi 0000:08:00.0: Loaded firmware version: 39.31.5.1 build 35138
[14904.600213] iwlwifi 0000:08:00.0: Start IWL Error Log Dump:
[14904.600221] iwlwifi 0000:08:00.0: Status: 0x00000400, count: 5
[14904.600224] iwlwifi 0000:08:00.0: 0x00000005 | SYSASSERT                   
[14904.600226] iwlwifi 0000:08:00.0: 0x00016E00 | uPc
[14904.600228] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink1
[14904.600229] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink2
[14904.600231] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink1
[14904.600232] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink2
[14904.600234] iwlwifi 0000:08:00.0: 0x00000000 | data1
[14904.600235] iwlwifi 0000:08:00.0: 0x00000000 | data2
[14904.600237] iwlwifi 0000:08:00.0: 0x00000616 | line
[14904.600240] iwlwifi 0000:08:00.0: 0x00018BC9 | beacon time
[14904.600242] iwlwifi 0000:08:00.0: 0x00000437 | tsf low
[14904.600244] iwlwifi 0000:08:00.0: 0x00000000 | tsf hi
[14904.600246] iwlwifi 0000:08:00.0: 0x00000000 | time gp1
[14904.600248] iwlwifi 0000:08:00.0: 0x0000043B | time gp2
[14904.600249] iwlwifi 0000:08:00.0: 0x00000000 | time gp3
[14904.600251] iwlwifi 0000:08:00.0: 0x0001271F | uCode version
[14904.600253] iwlwifi 0000:08:00.0: 0x0000006C | hw version
[14904.600254] iwlwifi 0000:08:00.0: 0x00C8330C | board version
[14904.600256] iwlwifi 0000:08:00.0: 0x00000000 | hcmd
[14904.600258] iwlwifi 0000:08:00.0: 0x00122000 | isr0
[14904.600259] iwlwifi 0000:08:00.0: 0x00000000 | isr1
[14904.600261] iwlwifi 0000:08:00.0: 0x00000002 | isr2
[14904.600263] iwlwifi 0000:08:00.0: 0x004400C0 | isr3
[14904.600265] iwlwifi 0000:08:00.0: 0x00000000 | isr4
[14904.600266] iwlwifi 0000:08:00.0: 0x00000000 | isr_pref
[14904.600268] iwlwifi 0000:08:00.0: 0x00002BFE | wait_event
[14904.600270] iwlwifi 0000:08:00.0: 0x00000000 | l2p_control
[14904.600271] iwlwifi 0000:08:00.0: 0x00000000 | l2p_duration
[14904.600273] iwlwifi 0000:08:00.0: 0x00000000 | l2p_mhvalid
[14904.600274] iwlwifi 0000:08:00.0: 0x00100040 | l2p_addr_match
[14904.600276] iwlwifi 0000:08:00.0: 0x00000007 | lmpm_pmg_sel
[14904.600278] iwlwifi 0000:08:00.0: 0x00000000 | timestamp
[14904.600279] iwlwifi 0000:08:00.0: 0x0000F808 | flow_handler
[14904.600354] iwlwifi 0000:08:00.0: Start IWL Event Log Dump: display last 5 entries
[14904.600382] iwlwifi 0000:08:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[14904.600396] iwlwifi 0000:08:00.0: EVT_LOGT:0000000021:0x00000000:1208
[14904.600410] iwlwifi 0000:08:00.0: EVT_LOGT:0000001004:0x00000001:0071
[14904.600425] iwlwifi 0000:08:00.0: EVT_LOGT:0000001080:0x00000002:0071
[14904.600439] iwlwifi 0000:08:00.0: EVT_LOGT:0000001086:0x00000000:0125
[14904.600450] iwlwifi 0000:08:00.0: BUG_ON, Stop restarting
[14904.600898] iwlwifi 0000:08:00.0: Failed to run INIT ucode: -5
[14904.601058] iwlwifi 0000:08:00.0: Unable to initialize device.
[14904.601823] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[14904.609382] iwlwifi 0000:08:00.0: Radio type=0x0-0x0-0x3
[14904.618178] iwlwifi 0000:08:00.0: Microcode SW error detected.  Restarting 0x82000000.
[14904.618191] iwlwifi 0000:08:00.0: CSR values:
[14904.618197] iwlwifi 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[14904.618207] iwlwifi 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c8330c
[14904.618216] iwlwifi 0000:08:00.0:          CSR_INT_COALESCING: 0X00000040
[14904.618226] iwlwifi 0000:08:00.0:                     CSR_INT: 0X80000000
[14904.618235] iwlwifi 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[14904.618244] iwlwifi 0000:08:00.0:           CSR_FH_INT_STATUS: 0X40010000
[14904.618252] iwlwifi 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[14904.618261] iwlwifi 0000:08:00.0:                   CSR_RESET: 0X00000000
[14904.618270] iwlwifi 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[14904.618279] iwlwifi 0000:08:00.0:                  CSR_HW_REV: 0X0000006c
[14904.618287] iwlwifi 0000:08:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[14904.618296] iwlwifi 0000:08:00.0:               CSR_EEPROM_GP: 0X90000001
[14904.618305] iwlwifi 0000:08:00.0:              CSR_OTP_GP_REG: 0X00210801
[14904.618314] iwlwifi 0000:08:00.0:                 CSR_GIO_REG: 0X00080046
[14904.618323] iwlwifi 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00000000
[14904.618332] iwlwifi 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[14904.618340] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[14904.618349] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[14904.618358] iwlwifi 0000:08:00.0:                 CSR_LED_REG: 0X00000018
[14904.618367] iwlwifi 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[14904.618375] iwlwifi 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[14904.618384] iwlwifi 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[14904.618393] iwlwifi 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[14904.618402] iwlwifi 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[14904.618407] iwlwifi 0000:08:00.0: FH register values:
[14904.618429] iwlwifi 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X136f3100
[14904.618450] iwlwifi 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0136ad40
[14904.618471] iwlwifi 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[14904.618493] iwlwifi 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[14904.618514] iwlwifi 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[14904.618536] iwlwifi 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[14904.618557] iwlwifi 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[14904.618579] iwlwifi 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[14904.618600] iwlwifi 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[14904.618607] iwlwifi 0000:08:00.0: Loaded firmware version: 39.31.5.1 build 35138
[14904.618776] iwlwifi 0000:08:00.0: Start IWL Error Log Dump:
[14904.618782] iwlwifi 0000:08:00.0: Status: 0x00000400, count: 5
[14904.618788] iwlwifi 0000:08:00.0: 0x00000005 | SYSASSERT                   
[14904.618793] iwlwifi 0000:08:00.0: 0x00016E00 | uPc
[14904.618797] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink1
[14904.618802] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink2
[14904.618806] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink1
[14904.618811] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink2
[14904.618815] iwlwifi 0000:08:00.0: 0x00000000 | data1
[14904.618819] iwlwifi 0000:08:00.0: 0x00000000 | data2
[14904.618824] iwlwifi 0000:08:00.0: 0x00000616 | line
[14904.618829] iwlwifi 0000:08:00.0: 0x00018BCB | beacon time
[14904.618833] iwlwifi 0000:08:00.0: 0x00000435 | tsf low
[14904.618837] iwlwifi 0000:08:00.0: 0x00000000 | tsf hi
[14904.618842] iwlwifi 0000:08:00.0: 0x00000000 | time gp1
[14904.618846] iwlwifi 0000:08:00.0: 0x00000439 | time gp2
[14904.618851] iwlwifi 0000:08:00.0: 0x00000000 | time gp3
[14904.618855] iwlwifi 0000:08:00.0: 0x0001271F | uCode version
[14904.618860] iwlwifi 0000:08:00.0: 0x0000006C | hw version
[14904.618865] iwlwifi 0000:08:00.0: 0x00C8330C | board version
[14904.618869] iwlwifi 0000:08:00.0: 0x00000000 | hcmd
[14904.618874] iwlwifi 0000:08:00.0: 0x00122000 | isr0
[14904.618878] iwlwifi 0000:08:00.0: 0x00000000 | isr1
[14904.618883] iwlwifi 0000:08:00.0: 0x00000002 | isr2
[14904.618887] iwlwifi 0000:08:00.0: 0x004000C0 | isr3
[14904.618892] iwlwifi 0000:08:00.0: 0x00000000 | isr4
[14904.618896] iwlwifi 0000:08:00.0: 0x00000000 | isr_pref
[14904.618901] iwlwifi 0000:08:00.0: 0x00002BFE | wait_event
[14904.618905] iwlwifi 0000:08:00.0: 0x00000000 | l2p_control
[14904.618910] iwlwifi 0000:08:00.0: 0x00000000 | l2p_duration
[14904.618915] iwlwifi 0000:08:00.0: 0x00000000 | l2p_mhvalid
[14904.618919] iwlwifi 0000:08:00.0: 0x00100040 | l2p_addr_match
[14904.618924] iwlwifi 0000:08:00.0: 0x00000007 | lmpm_pmg_sel
[14904.618928] iwlwifi 0000:08:00.0: 0x00000000 | timestamp
[14904.618933] iwlwifi 0000:08:00.0: 0x0000F808 | flow_handler
[14904.619008] iwlwifi 0000:08:00.0: Start IWL Event Log Dump: display last 5 entries
[14904.619036] iwlwifi 0000:08:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[14904.619054] iwlwifi 0000:08:00.0: EVT_LOGT:0000000021:0x00000000:1208
[14904.619072] iwlwifi 0000:08:00.0: EVT_LOGT:0000001002:0x00000001:0071
[14904.619089] iwlwifi 0000:08:00.0: EVT_LOGT:0000001078:0x00000002:0071
[14904.619106] iwlwifi 0000:08:00.0: EVT_LOGT:0000001084:0x00000000:0125
[14904.619123] iwlwifi 0000:08:00.0: BUG_ON, Stop restarting
[14904.619553] iwlwifi 0000:08:00.0: Failed to run INIT ucode: -5
[14904.619667] iwlwifi 0000:08:00.0: Unable to initialize device.
[14904.622182] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[14904.629727] iwlwifi 0000:08:00.0: Radio type=0x0-0x0-0x3
[14904.638537] iwlwifi 0000:08:00.0: Microcode SW error detected.  Restarting 0x82000000.
[14904.638550] iwlwifi 0000:08:00.0: CSR values:
[14904.638555] iwlwifi 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[14904.638566] iwlwifi 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c8330c
[14904.638575] iwlwifi 0000:08:00.0:          CSR_INT_COALESCING: 0X00000040
[14904.638584] iwlwifi 0000:08:00.0:                     CSR_INT: 0X80000000
[14904.638594] iwlwifi 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[14904.638603] iwlwifi 0000:08:00.0:           CSR_FH_INT_STATUS: 0X40010000
[14904.638612] iwlwifi 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[14904.638620] iwlwifi 0000:08:00.0:                   CSR_RESET: 0X00000000
[14904.638629] iwlwifi 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[14904.638638] iwlwifi 0000:08:00.0:                  CSR_HW_REV: 0X0000006c
[14904.638647] iwlwifi 0000:08:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[14904.638656] iwlwifi 0000:08:00.0:               CSR_EEPROM_GP: 0X90000001
[14904.638665] iwlwifi 0000:08:00.0:              CSR_OTP_GP_REG: 0X00210801
[14904.638673] iwlwifi 0000:08:00.0:                 CSR_GIO_REG: 0X00080046
[14904.638682] iwlwifi 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00000000
[14904.638691] iwlwifi 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[14904.638700] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[14904.638708] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[14904.638717] iwlwifi 0000:08:00.0:                 CSR_LED_REG: 0X00000018
[14904.638726] iwlwifi 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[14904.638734] iwlwifi 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[14904.638743] iwlwifi 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[14904.638752] iwlwifi 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[14904.638760] iwlwifi 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[14904.638765] iwlwifi 0000:08:00.0: FH register values:
[14904.638787] iwlwifi 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X136f3100
[14904.638808] iwlwifi 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0136ad40
[14904.638830] iwlwifi 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[14904.638851] iwlwifi 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[14904.638872] iwlwifi 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[14904.638893] iwlwifi 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[14904.638915] iwlwifi 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[14904.638936] iwlwifi 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[14904.638958] iwlwifi 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[14904.638965] iwlwifi 0000:08:00.0: Loaded firmware version: 39.31.5.1 build 35138
[14904.639134] iwlwifi 0000:08:00.0: Start IWL Error Log Dump:
[14904.639139] iwlwifi 0000:08:00.0: Status: 0x00000400, count: 5
[14904.639145] iwlwifi 0000:08:00.0: 0x00000005 | SYSASSERT                   
[14904.639150] iwlwifi 0000:08:00.0: 0x00016E00 | uPc
[14904.639155] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink1
[14904.639159] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink2
[14904.639164] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink1
[14904.639168] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink2
[14904.639173] iwlwifi 0000:08:00.0: 0x00000000 | data1
[14904.639177] iwlwifi 0000:08:00.0: 0x00000000 | data2
[14904.639182] iwlwifi 0000:08:00.0: 0x00000616 | line
[14904.639186] iwlwifi 0000:08:00.0: 0x00018BC7 | beacon time
[14904.639191] iwlwifi 0000:08:00.0: 0x00000439 | tsf low
[14904.639195] iwlwifi 0000:08:00.0: 0x00000000 | tsf hi
[14904.639200] iwlwifi 0000:08:00.0: 0x00000000 | time gp1
[14904.639204] iwlwifi 0000:08:00.0: 0x0000043D | time gp2
[14904.639208] iwlwifi 0000:08:00.0: 0x00000000 | time gp3
[14904.639213] iwlwifi 0000:08:00.0: 0x0001271F | uCode version
[14904.639218] iwlwifi 0000:08:00.0: 0x0000006C | hw version
[14904.639222] iwlwifi 0000:08:00.0: 0x00C8330C | board version
[14904.639227] iwlwifi 0000:08:00.0: 0x00000000 | hcmd
[14904.639231] iwlwifi 0000:08:00.0: 0x00122000 | isr0
[14904.639236] iwlwifi 0000:08:00.0: 0x00000000 | isr1
[14904.639240] iwlwifi 0000:08:00.0: 0x00000002 | isr2
[14904.639245] iwlwifi 0000:08:00.0: 0x004000C0 | isr3
[14904.639249] iwlwifi 0000:08:00.0: 0x00000000 | isr4
[14904.639254] iwlwifi 0000:08:00.0: 0x00000000 | isr_pref
[14904.639258] iwlwifi 0000:08:00.0: 0x00002BFE | wait_event
[14904.639263] iwlwifi 0000:08:00.0: 0x00000000 | l2p_control
[14904.639268] iwlwifi 0000:08:00.0: 0x00000000 | l2p_duration
[14904.639272] iwlwifi 0000:08:00.0: 0x00000000 | l2p_mhvalid
[14904.639277] iwlwifi 0000:08:00.0: 0x00100040 | l2p_addr_match
[14904.639281] iwlwifi 0000:08:00.0: 0x00000007 | lmpm_pmg_sel
[14904.639286] iwlwifi 0000:08:00.0: 0x00000000 | timestamp
[14904.639290] iwlwifi 0000:08:00.0: 0x0000F808 | flow_handler
[14904.639367] iwlwifi 0000:08:00.0: Start IWL Event Log Dump: display last 5 entries
[14904.639395] iwlwifi 0000:08:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[14904.639412] iwlwifi 0000:08:00.0: EVT_LOGT:0000000021:0x00000000:1208
[14904.639430] iwlwifi 0000:08:00.0: EVT_LOGT:0000001006:0x00000001:0071
[14904.639447] iwlwifi 0000:08:00.0: EVT_LOGT:0000001082:0x00000002:0071
[14904.639464] iwlwifi 0000:08:00.0: EVT_LOGT:0000001088:0x00000000:0125
[14904.639482] iwlwifi 0000:08:00.0: BUG_ON, Stop restarting
[14904.639874] iwlwifi 0000:08:00.0: Failed to run INIT ucode: -5
[14904.639983] iwlwifi 0000:08:00.0: Unable to initialize device.
[14904.640552] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[14904.648221] iwlwifi 0000:08:00.0: Radio type=0x0-0x0-0x3
[14904.656880] iwlwifi 0000:08:00.0: Microcode SW error detected.  Restarting 0x82000000.
[14904.656894] iwlwifi 0000:08:00.0: CSR values:
[14904.656896] iwlwifi 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[14904.656902] iwlwifi 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c8330c
[14904.656908] iwlwifi 0000:08:00.0:          CSR_INT_COALESCING: 0X00000040
[14904.656914] iwlwifi 0000:08:00.0:                     CSR_INT: 0X80000000
[14904.656919] iwlwifi 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[14904.656925] iwlwifi 0000:08:00.0:           CSR_FH_INT_STATUS: 0X40010000
[14904.656930] iwlwifi 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[14904.656936] iwlwifi 0000:08:00.0:                   CSR_RESET: 0X00000000
[14904.656941] iwlwifi 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[14904.656946] iwlwifi 0000:08:00.0:                  CSR_HW_REV: 0X0000006c
[14904.656952] iwlwifi 0000:08:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[14904.656969] iwlwifi 0000:08:00.0:               CSR_EEPROM_GP: 0X90000001
[14904.656978] iwlwifi 0000:08:00.0:              CSR_OTP_GP_REG: 0X00210801
[14904.656986] iwlwifi 0000:08:00.0:                 CSR_GIO_REG: 0X00080046
[14904.656995] iwlwifi 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00000000
[14904.657004] iwlwifi 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[14904.657012] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[14904.657021] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[14904.657030] iwlwifi 0000:08:00.0:                 CSR_LED_REG: 0X00000018
[14904.657039] iwlwifi 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[14904.657047] iwlwifi 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[14904.657056] iwlwifi 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[14904.657065] iwlwifi 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[14904.657073] iwlwifi 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[14904.657078] iwlwifi 0000:08:00.0: FH register values:
[14904.657100] iwlwifi 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X136f3100
[14904.657122] iwlwifi 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0136ad40
[14904.657142] iwlwifi 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[14904.657164] iwlwifi 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[14904.657184] iwlwifi 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[14904.657206] iwlwifi 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[14904.657228] iwlwifi 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[14904.657249] iwlwifi 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[14904.657270] iwlwifi 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[14904.657278] iwlwifi 0000:08:00.0: Loaded firmware version: 39.31.5.1 build 35138
[14904.657445] iwlwifi 0000:08:00.0: Start IWL Error Log Dump:
[14904.657451] iwlwifi 0000:08:00.0: Status: 0x00000400, count: 5
[14904.657457] iwlwifi 0000:08:00.0: 0x00000005 | SYSASSERT                   
[14904.657462] iwlwifi 0000:08:00.0: 0x00016E00 | uPc
[14904.657466] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink1
[14904.657471] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink2
[14904.657475] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink1
[14904.657480] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink2
[14904.657484] iwlwifi 0000:08:00.0: 0x00000000 | data1
[14904.657488] iwlwifi 0000:08:00.0: 0x00000000 | data2
[14904.657493] iwlwifi 0000:08:00.0: 0x00000616 | line
[14904.657498] iwlwifi 0000:08:00.0: 0x00018BC9 | beacon time
[14904.657502] iwlwifi 0000:08:00.0: 0x00000437 | tsf low
[14904.657506] iwlwifi 0000:08:00.0: 0x00000000 | tsf hi
[14904.657511] iwlwifi 0000:08:00.0: 0x00000000 | time gp1
[14904.657515] iwlwifi 0000:08:00.0: 0x0000043B | time gp2
[14904.657520] iwlwifi 0000:08:00.0: 0x00000000 | time gp3
[14904.657524] iwlwifi 0000:08:00.0: 0x0001271F | uCode version
[14904.657529] iwlwifi 0000:08:00.0: 0x0000006C | hw version
[14904.657534] iwlwifi 0000:08:00.0: 0x00C8330C | board version
[14904.657538] iwlwifi 0000:08:00.0: 0x00000000 | hcmd
[14904.657543] iwlwifi 0000:08:00.0: 0x00122000 | isr0
[14904.657547] iwlwifi 0000:08:00.0: 0x00000000 | isr1
[14904.657551] iwlwifi 0000:08:00.0: 0x00000002 | isr2
[14904.657556] iwlwifi 0000:08:00.0: 0x004400C0 | isr3
[14904.657560] iwlwifi 0000:08:00.0: 0x00000000 | isr4
[14904.657565] iwlwifi 0000:08:00.0: 0x00000000 | isr_pref
[14904.657570] iwlwifi 0000:08:00.0: 0x00002BFE | wait_event
[14904.657575] iwlwifi 0000:08:00.0: 0x00000000 | l2p_control
[14904.657579] iwlwifi 0000:08:00.0: 0x00000000 | l2p_duration
[14904.657584] iwlwifi 0000:08:00.0: 0x00000000 | l2p_mhvalid
[14904.657588] iwlwifi 0000:08:00.0: 0x00100040 | l2p_addr_match
[14904.657593] iwlwifi 0000:08:00.0: 0x00000007 | lmpm_pmg_sel
[14904.657597] iwlwifi 0000:08:00.0: 0x00000000 | timestamp
[14904.657602] iwlwifi 0000:08:00.0: 0x0000F808 | flow_handler
[14904.657678] iwlwifi 0000:08:00.0: Start IWL Event Log Dump: display last 5 entries
[14904.657706] iwlwifi 0000:08:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[14904.657724] iwlwifi 0000:08:00.0: EVT_LOGT:0000000021:0x00000000:1208
[14904.657742] iwlwifi 0000:08:00.0: EVT_LOGT:0000001004:0x00000001:0071
[14904.657759] iwlwifi 0000:08:00.0: EVT_LOGT:0000001080:0x00000002:0071
[14904.657776] iwlwifi 0000:08:00.0: EVT_LOGT:0000001086:0x00000000:0125
[14904.657795] iwlwifi 0000:08:00.0: BUG_ON, Stop restarting
[14904.658186] iwlwifi 0000:08:00.0: Failed to run INIT ucode: -5
[14904.658296] iwlwifi 0000:08:00.0: Unable to initialize device.
[14904.661389] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[14904.668931] iwlwifi 0000:08:00.0: Radio type=0x0-0x0-0x3
[14904.677696] iwlwifi 0000:08:00.0: Microcode SW error detected.  Restarting 0x82000000.
[14904.677709] iwlwifi 0000:08:00.0: CSR values:
[14904.677714] iwlwifi 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[14904.677724] iwlwifi 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c8330c
[14904.677734] iwlwifi 0000:08:00.0:          CSR_INT_COALESCING: 0X00000040
[14904.677743] iwlwifi 0000:08:00.0:                     CSR_INT: 0X80000000
[14904.677752] iwlwifi 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[14904.677761] iwlwifi 0000:08:00.0:           CSR_FH_INT_STATUS: 0X40010000
[14904.677770] iwlwifi 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[14904.677779] iwlwifi 0000:08:00.0:                   CSR_RESET: 0X00000000
[14904.677788] iwlwifi 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[14904.677797] iwlwifi 0000:08:00.0:                  CSR_HW_REV: 0X0000006c
[14904.677806] iwlwifi 0000:08:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[14904.677815] iwlwifi 0000:08:00.0:               CSR_EEPROM_GP: 0X90000001
[14904.677823] iwlwifi 0000:08:00.0:              CSR_OTP_GP_REG: 0X00210801
[14904.677832] iwlwifi 0000:08:00.0:                 CSR_GIO_REG: 0X00080046
[14904.677841] iwlwifi 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00000000
[14904.677850] iwlwifi 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[14904.677859] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[14904.677868] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[14904.677876] iwlwifi 0000:08:00.0:                 CSR_LED_REG: 0X00000018
[14904.677885] iwlwifi 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[14904.677894] iwlwifi 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[14904.677903] iwlwifi 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[14904.677911] iwlwifi 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[14904.677920] iwlwifi 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[14904.677925] iwlwifi 0000:08:00.0: FH register values:
[14904.677948] iwlwifi 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X136f3100
[14904.677969] iwlwifi 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0136ad40
[14904.677990] iwlwifi 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[14904.678012] iwlwifi 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[14904.678034] iwlwifi 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[14904.678055] iwlwifi 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[14904.678077] iwlwifi 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[14904.678099] iwlwifi 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[14904.678120] iwlwifi 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[14904.678127] iwlwifi 0000:08:00.0: Loaded firmware version: 39.31.5.1 build 35138
[14904.678296] iwlwifi 0000:08:00.0: Start IWL Error Log Dump:
[14904.678302] iwlwifi 0000:08:00.0: Status: 0x00000400, count: 5
[14904.678308] iwlwifi 0000:08:00.0: 0x00000005 | SYSASSERT                   
[14904.678313] iwlwifi 0000:08:00.0: 0x00016E00 | uPc
[14904.678318] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink1
[14904.678323] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink2
[14904.678328] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink1
[14904.678332] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink2
[14904.678337] iwlwifi 0000:08:00.0: 0x00000000 | data1
[14904.678341] iwlwifi 0000:08:00.0: 0x00000000 | data2
[14904.678346] iwlwifi 0000:08:00.0: 0x00000616 | line
[14904.678350] iwlwifi 0000:08:00.0: 0x00018BCA | beacon time
[14904.678355] iwlwifi 0000:08:00.0: 0x00000436 | tsf low
[14904.678359] iwlwifi 0000:08:00.0: 0x00000000 | tsf hi
[14904.678364] iwlwifi 0000:08:00.0: 0x00000000 | time gp1
[14904.678368] iwlwifi 0000:08:00.0: 0x0000043B | time gp2
[14904.678373] iwlwifi 0000:08:00.0: 0x00000000 | time gp3
[14904.678377] iwlwifi 0000:08:00.0: 0x0001271F | uCode version
[14904.678382] iwlwifi 0000:08:00.0: 0x0000006C | hw version
[14904.678387] iwlwifi 0000:08:00.0: 0x00C8330C | board version
[14904.678392] iwlwifi 0000:08:00.0: 0x00000000 | hcmd
[14904.678397] iwlwifi 0000:08:00.0: 0x00122000 | isr0
[14904.678402] iwlwifi 0000:08:00.0: 0x00000000 | isr1
[14904.678406] iwlwifi 0000:08:00.0: 0x00000002 | isr2
[14904.678411] iwlwifi 0000:08:00.0: 0x004000C0 | isr3
[14904.678415] iwlwifi 0000:08:00.0: 0x00000000 | isr4
[14904.678420] iwlwifi 0000:08:00.0: 0x00000000 | isr_pref
[14904.678425] iwlwifi 0000:08:00.0: 0x00002BFE | wait_event
[14904.678430] iwlwifi 0000:08:00.0: 0x00000000 | l2p_control
[14904.678434] iwlwifi 0000:08:00.0: 0x00000000 | l2p_duration
[14904.678439] iwlwifi 0000:08:00.0: 0x00000000 | l2p_mhvalid
[14904.678444] iwlwifi 0000:08:00.0: 0x00100040 | l2p_addr_match
[14904.678448] iwlwifi 0000:08:00.0: 0x00000007 | lmpm_pmg_sel
[14904.678453] iwlwifi 0000:08:00.0: 0x00000000 | timestamp
[14904.678457] iwlwifi 0000:08:00.0: 0x0000F808 | flow_handler
[14904.678535] iwlwifi 0000:08:00.0: Start IWL Event Log Dump: display last 5 entries
[14904.678563] iwlwifi 0000:08:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[14904.678582] iwlwifi 0000:08:00.0: EVT_LOGT:0000000022:0x00000000:1208
[14904.678600] iwlwifi 0000:08:00.0: EVT_LOGT:0000001004:0x00000001:0071
[14904.678617] iwlwifi 0000:08:00.0: EVT_LOGT:0000001080:0x00000002:0071
[14904.678635] iwlwifi 0000:08:00.0: EVT_LOGT:0000001086:0x00000000:0125
[14904.678655] iwlwifi 0000:08:00.0: BUG_ON, Stop restarting
[14904.679053] iwlwifi 0000:08:00.0: Failed to run INIT ucode: -5
[14904.679149] iwlwifi 0000:08:00.0: Unable to initialize device.
[14904.679997] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[14904.687658] iwlwifi 0000:08:00.0: Radio type=0x0-0x0-0x3
```

---

### Post by chili555 on 2013-12-27
That is an unhappy card, for sure. Has the card worked properly in Windows? Other Linux distributions? Ever?

I suggest a few things. First, let's be sure the latest and greatest firmware is installed. You said you've done that but how? Did you get the latest from Intel's site or ... what? Let's check the integrity of your firmware file:```
md5sum /lib/firmware/iwlwifi-1000-5.ucode
```If you have other than -5, please post what you have. My file says:> 9f81a060ed274f76cd605295da77f7a6  /lib/firmware/iwlwifi-1000-5.ucodeSecond, I worked on a case a few weeks ago where the card was not connected to the antenna wires at all. If your laptop has a little door on the bottom where you can check, I suggest you take a peek. Finally, see if the card seems to be seated fully. Of course, please read and follow all the safety precautions in the manual before you proceed.

May I see:```
lspci -nn | grep 0280
```

---

### Post by mprihoda13 on 2013-12-27
When I had it installed in windows the card worked fined, but then I got a new hard drive. After I got it, I decided to install Ubuntu instead of reinstalling windows. The first time I installed it, I was able to get wifi working. Then later on I had tried to install Windows as well, but my disc wasn't the one I needed so I ended removing the Windows copy as to not break any licensing terms and reinstalling Ubuntu. After that I have been unable to get it. So I at least know that it is possible for it to work.

When I put in the first code:

```
mikey@mikey-Lenovo-IdeaPad-Y570:~$ md5sum /lib/firmware/iwlwifi-1000-5.ucode
9f81a060ed274f76cd605295da77f7a6  /lib/firmware/iwlwifi-1000-5.ucode
```

The second code gives me 

```
mikey@mikey-Lenovo-IdeaPad-Y570:~$ lspci -nn | grep 280
08:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0084]
```


Thanks for helping me too by the way, I really appreciate it.

---

### Post by mprihoda13 on 2013-12-30
Anything else I can try doing to fix this?

---

