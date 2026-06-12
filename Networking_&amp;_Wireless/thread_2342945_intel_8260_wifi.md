---
title: "intel 8260 wifi"
date: 2016-11-11
forum: Networking &amp; Wireless
---

### Post by fixxar on 2016-11-11
Does anyone know how to help me get this to work? 

```
 *-network DISABLED
       description: Wireless interface
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:70:00.0
       logical name: wlp112s0
       version: 3a
       serial: e4:a7:a0:3f:2b:ae
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.8.0-27-generic firmware=22.361476.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:140 memory:dc100000-dc101fff

sudo rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


 60.042107] iwlwifi 0000:70:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   60.042115] iwlwifi 0000:70:00.0: CSR values:
[   60.042119] iwlwifi 0000:70:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   60.042126] iwlwifi 0000:70:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c89008
[   60.042132] iwlwifi 0000:70:00.0:          CSR_INT_COALESCING: 0X0000ff40
[   60.042137] iwlwifi 0000:70:00.0:                     CSR_INT: 0X00000000
[   60.042143] iwlwifi 0000:70:00.0:                CSR_INT_MASK: 0X00000000
[   60.042149] iwlwifi 0000:70:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   60.042154] iwlwifi 0000:70:00.0:                 CSR_GPIO_IN: 0X00000019
[   60.042159] iwlwifi 0000:70:00.0:                   CSR_RESET: 0X00000000
[   60.042165] iwlwifi 0000:70:00.0:                CSR_GP_CNTRL: 0X08040005
[   60.042171] iwlwifi 0000:70:00.0:                  CSR_HW_REV: 0X00000201
[   60.042176] iwlwifi 0000:70:00.0:              CSR_EEPROM_REG: 0Xd55555d5
[   60.042182] iwlwifi 0000:70:00.0:               CSR_EEPROM_GP: 0Xd55555d5
[   60.042187] iwlwifi 0000:70:00.0:              CSR_OTP_GP_REG: 0Xd55555d5
[   60.042193] iwlwifi 0000:70:00.0:                 CSR_GIO_REG: 0X001f0044
[   60.042198] iwlwifi 0000:70:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   60.042203] iwlwifi 0000:70:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   60.042209] iwlwifi 0000:70:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   60.042214] iwlwifi 0000:70:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   60.042219] iwlwifi 0000:70:00.0:                 CSR_LED_REG: 0X00000020
[   60.042225] iwlwifi 0000:70:00.0:        CSR_DRAM_INT_TBL_REG: 0X8802b1d2
[   60.042230] iwlwifi 0000:70:00.0:        CSR_GIO_CHICKEN_BITS: 0X07800200
[   60.042236] iwlwifi 0000:70:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[   60.042241] iwlwifi 0000:70:00.0:      CSR_MONITOR_STATUS_REG: 0Xc03803c0
[   60.042247] iwlwifi 0000:70:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   60.042252] iwlwifi 0000:70:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   60.042255] iwlwifi 0000:70:00.0: FH register values:
[   60.042270] iwlwifi 0000:70:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X02b1d380
[   60.042286] iwlwifi 0000:70:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X002b1d30
[   60.042301] iwlwifi 0000:70:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000000
[   60.042316] iwlwifi 0000:70:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00801054
[   60.042331] iwlwifi 0000:70:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   60.042346] iwlwifi 0000:70:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X03030000
[   60.042362] iwlwifi 0000:70:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   60.042377] iwlwifi 0000:70:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0003
[   60.042392] iwlwifi 0000:70:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   60.042508] iwlwifi 0000:70:00.0: Start IWL Error Log Dump:
[   60.042511] iwlwifi 0000:70:00.0: Status: 0x00000000, count: 6
[   60.042515] iwlwifi 0000:70:00.0: Loaded firmware version: 22.361476.0
[   60.042518] iwlwifi 0000:70:00.0: 0x00000071 | ADVANCED_SYSASSERT          
[   60.042522] iwlwifi 0000:70:00.0: 0x000002F0 | trm_hw_status0
[   60.042525] iwlwifi 0000:70:00.0: 0x00000000 | trm_hw_status1
[   60.042528] iwlwifi 0000:70:00.0: 0x0000E9C8 | branchlink2
[   60.042531] iwlwifi 0000:70:00.0: 0x0002843C | interruptlink1
[   60.042534] iwlwifi 0000:70:00.0: 0x0002843C | interruptlink2
[   60.042536] iwlwifi 0000:70:00.0: 0x00000000 | data1
[   60.042539] iwlwifi 0000:70:00.0: 0x00001000 | data2
[   60.042542] iwlwifi 0000:70:00.0: 0x07830000 | data3
[   60.042545] iwlwifi 0000:70:00.0: 0x003FE435 | beacon time
[   60.042548] iwlwifi 0000:70:00.0: 0x00001BC9 | tsf low
[   60.042551] iwlwifi 0000:70:00.0: 0x00000000 | tsf hi
[   60.042554] iwlwifi 0000:70:00.0: 0x00000000 | time gp1
[   60.042557] iwlwifi 0000:70:00.0: 0x00001BCA | time gp2
[   60.042560] iwlwifi 0000:70:00.0: 0x00000000 | uCode revision type
[   60.042563] iwlwifi 0000:70:00.0: 0x00000016 | uCode version major
[   60.042566] iwlwifi 0000:70:00.0: 0x00058404 | uCode version minor
[   60.042569] iwlwifi 0000:70:00.0: 0x00000201 | hw version
[   60.042572] iwlwifi 0000:70:00.0: 0x00C89008 | board version
[   60.042575] iwlwifi 0000:70:00.0: 0x00000000 | hcmd
[   60.042578] iwlwifi 0000:70:00.0: 0x00022000 | isr0
[   60.042581] iwlwifi 0000:70:00.0: 0x10800000 | isr1
[   60.042583] iwlwifi 0000:70:00.0: 0x18001802 | isr2
[   60.042586] iwlwifi 0000:70:00.0: 0x004000C0 | isr3
[   60.042589] iwlwifi 0000:70:00.0: 0x00000000 | isr4
[   60.042592] iwlwifi 0000:70:00.0: 0x00000110 | last cmd Id
[   60.042595] iwlwifi 0000:70:00.0: 0x00000000 | wait_event
[   60.042598] iwlwifi 0000:70:00.0: 0x0000BFF9 | l2p_control
[   60.042601] iwlwifi 0000:70:00.0: 0x00000000 | l2p_duration
[   60.042604] iwlwifi 0000:70:00.0: 0x00000000 | l2p_mhvalid
[   60.042606] iwlwifi 0000:70:00.0: 0x00000000 | l2p_addr_match
[   60.042609] iwlwifi 0000:70:00.0: 0x0000000F | lmpm_pmg_sel
[   60.042612] iwlwifi 0000:70:00.0: 0x03071928 | timestamp
[   60.042615] iwlwifi 0000:70:00.0: 0x00340008 | flow_handler
[   60.042670] iwlwifi 0000:70:00.0: Start IWL Error Log Dump:
[   60.042674] iwlwifi 0000:70:00.0: Status: 0x00000000, count: 7
[   60.042677] iwlwifi 0000:70:00.0: 0x00000309 | ADVANCED_SYSASSERT
[   60.042680] iwlwifi 0000:70:00.0: 0x00000000 | umac branchlink1
[   60.042683] iwlwifi 0000:70:00.0: 0xC008383C | umac branchlink2
[   60.042686] iwlwifi 0000:70:00.0: 0xC008166C | umac interruptlink1
[   60.042689] iwlwifi 0000:70:00.0: 0x00000000 | umac interruptlink2
[   60.042692] iwlwifi 0000:70:00.0: 0xDEADBEEF | umac data1
[   60.042694] iwlwifi 0000:70:00.0: 0xDEADBEEF | umac data2
[   60.042697] iwlwifi 0000:70:00.0: 0xDEADBEEF | umac data3
[   60.042700] iwlwifi 0000:70:00.0: 0x00000016 | umac major
[   60.042703] iwlwifi 0000:70:00.0: 0x00058404 | umac minor
[   60.042706] iwlwifi 0000:70:00.0: 0xC0887DEC | frame pointer
[   60.042709] iwlwifi 0000:70:00.0: 0xC0887DEC | stack pointer
[   60.042712] iwlwifi 0000:70:00.0: 0x0900014F | last host cmd
[   60.042715] iwlwifi 0000:70:00.0: 0x00080002 | isr status reg
[   60.042782] iwlwifi 0000:70:00.0: FW error in SYNC CMD FW_PAGING_BLOCK_CMD
[   60.042844]  [<ffffffffc128e831>] iwl_trans_pcie_send_hcmd+0x461/0x580 [iwlwifi]
[   60.042864]  [<ffffffffc12952ae>] iwl_trans_send_cmd+0x3e/0x90 [iwlwifi]
[   60.043131] iwlwifi 0000:70:00.0: failed to send the paging cmd
[   60.043163] iwlwifi 0000:70:00.0: Failed to start RT ucode: -5
[   60.049616] iwlwifi 0000:70:00.0: L1 Disabled - LTR Disabled
[   60.049865] iwlwifi 0000:70:00.0: L1 Disabled - LTR Disabled
[   60.177143] iwlwifi 0000:70:00.0: L1 Disabled - LTR Disabled
[   60.177404] iwlwifi 0000:70:00.0: L1 Disabled - LTR Disabled
[   60.241517] iwlwifi 0000:70:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   60.241526] iwlwifi 0000:70:00.0: CSR values:
[   60.241529] iwlwifi 0000:70:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   60.241536] iwlwifi 0000:70:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c89008
[   60.241542] iwlwifi 0000:70:00.0:          CSR_INT_COALESCING: 0X0000ff40
[   60.241548] iwlwifi 0000:70:00.0:                     CSR_INT: 0X00000000
[   60.241554] iwlwifi 0000:70:00.0:                CSR_INT_MASK: 0X00000000
[   60.241559] iwlwifi 0000:70:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   60.241565] iwlwifi 0000:70:00.0:                 CSR_GPIO_IN: 0X00000019
[   60.241570] iwlwifi 0000:70:00.0:                   CSR_RESET: 0X00000000
[   60.241576] iwlwifi 0000:70:00.0:                CSR_GP_CNTRL: 0X08040005
[   60.241581] iwlwifi 0000:70:00.0:                  CSR_HW_REV: 0X00000201
[   60.241587] iwlwifi 0000:70:00.0:              CSR_EEPROM_REG: 0Xd55555d5
[   60.241592] iwlwifi 0000:70:00.0:               CSR_EEPROM_GP: 0Xd55555d5
[   60.241598] iwlwifi 0000:70:00.0:              CSR_OTP_GP_REG: 0Xd55555d5
[   60.241603] iwlwifi 0000:70:00.0:                 CSR_GIO_REG: 0X001f0044
[   60.241609] iwlwifi 0000:70:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   60.241614] iwlwifi 0000:70:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   60.241620] iwlwifi 0000:70:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   60.241625] iwlwifi 0000:70:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   60.241630] iwlwifi 0000:70:00.0:                 CSR_LED_REG: 0X00000020
[   60.241636] iwlwifi 0000:70:00.0:        CSR_DRAM_INT_TBL_REG: 0X8802b1d2
[   60.241641] iwlwifi 0000:70:00.0:        CSR_GIO_CHICKEN_BITS: 0X07800200
[   60.241647] iwlwifi 0000:70:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[   60.241652] iwlwifi 0000:70:00.0:      CSR_MONITOR_STATUS_REG: 0Xc03803c0
[   60.241658] iwlwifi 0000:70:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   60.241663] iwlwifi 0000:70:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   60.241666] iwlwifi 0000:70:00.0: FH register values:
[   60.241682] iwlwifi 0000:70:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X02b1d380
[   60.241697] iwlwifi 0000:70:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X002b1d30
[   60.241712] iwlwifi 0000:70:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000000
[   60.241727] iwlwifi 0000:70:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00801054
[   60.241742] iwlwifi 0000:70:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   60.241757] iwlwifi 0000:70:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X03030000
[   60.241773] iwlwifi 0000:70:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   60.241788] iwlwifi 0000:70:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0003
[   60.241803] iwlwifi 0000:70:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   60.241915] iwlwifi 0000:70:00.0: Start IWL Error Log Dump:
[   60.241919] iwlwifi 0000:70:00.0: Status: 0x00000000, count: 6
[   60.241923] iwlwifi 0000:70:00.0: Loaded firmware version: 22.361476.0
[   60.241927] iwlwifi 0000:70:00.0: 0x00000071 | ADVANCED_SYSASSERT          
[   60.241930] iwlwifi 0000:70:00.0: 0x000002F0 | trm_hw_status0
[   60.241933] iwlwifi 0000:70:00.0: 0x00000000 | trm_hw_status1
[   60.241936] iwlwifi 0000:70:00.0: 0x0000E9C8 | branchlink2
[   60.241939] iwlwifi 0000:70:00.0: 0x0002843C | interruptlink1
[   60.241942] iwlwifi 0000:70:00.0: 0x0002843C | interruptlink2
[   60.241944] iwlwifi 0000:70:00.0: 0x00000000 | data1
[   60.241947] iwlwifi 0000:70:00.0: 0x00001000 | data2
[   60.241950] iwlwifi 0000:70:00.0: 0x07830000 | data3
[   60.241953] iwlwifi 0000:70:00.0: 0x003FE361 | beacon time
[   60.241956] iwlwifi 0000:70:00.0: 0x00001C9D | tsf low
[   60.241959] iwlwifi 0000:70:00.0: 0x00000000 | tsf hi
[   60.241962] iwlwifi 0000:70:00.0: 0x00000000 | time gp1
[   60.241965] iwlwifi 0000:70:00.0: 0x00001C9E | time gp2
[   60.241968] iwlwifi 0000:70:00.0: 0x00000000 | uCode revision type
[   60.241971] iwlwifi 0000:70:00.0: 0x00000016 | uCode version major
[   60.241974] iwlwifi 0000:70:00.0: 0x00058404 | uCode version minor
[   60.241978] iwlwifi 0000:70:00.0: 0x00000201 | hw version
[   60.241981] iwlwifi 0000:70:00.0: 0x00C89008 | board version
[   60.241983] iwlwifi 0000:70:00.0: 0x00000000 | hcmd
[   60.241986] iwlwifi 0000:70:00.0: 0x00022000 | isr0
[   60.241989] iwlwifi 0000:70:00.0: 0x10800000 | isr1
[   60.241992] iwlwifi 0000:70:00.0: 0x18001802 | isr2
[   60.241995] iwlwifi 0000:70:00.0: 0x004000C0 | isr3
[   60.241998] iwlwifi 0000:70:00.0: 0x00000000 | isr4
[   60.242001] iwlwifi 0000:70:00.0: 0x00000110 | last cmd Id
[   60.242004] iwlwifi 0000:70:00.0: 0x00000000 | wait_event
[   60.242007] iwlwifi 0000:70:00.0: 0x0000BFF9 | l2p_control
[   60.242010] iwlwifi 0000:70:00.0: 0x00000000 | l2p_duration
[   60.242013] iwlwifi 0000:70:00.0: 0x00000000 | l2p_mhvalid
[   60.242016] iwlwifi 0000:70:00.0: 0x00000000 | l2p_addr_match
[   60.242019] iwlwifi 0000:70:00.0: 0x0000000F | lmpm_pmg_sel
[   60.242022] iwlwifi 0000:70:00.0: 0x03071928 | timestamp
[   60.242025] iwlwifi 0000:70:00.0: 0x00340008 | flow_handler
[   60.242077] iwlwifi 0000:70:00.0: Start IWL Error Log Dump:
[   60.242081] iwlwifi 0000:70:00.0: Status: 0x00000000, count: 7
[   60.242084] iwlwifi 0000:70:00.0: 0x00000309 | ADVANCED_SYSASSERT
[   60.242087] iwlwifi 0000:70:00.0: 0x00000000 | umac branchlink1
[   60.242090] iwlwifi 0000:70:00.0: 0xC008383C | umac branchlink2
[   60.242093] iwlwifi 0000:70:00.0: 0xC008166C | umac interruptlink1
[   60.242096] iwlwifi 0000:70:00.0: 0x00000000 | umac interruptlink2
[   60.242099] iwlwifi 0000:70:00.0: 0xDEADBEEF | umac data1
[   60.242102] iwlwifi 0000:70:00.0: 0xDEADBEEF | umac data2
[   60.242105] iwlwifi 0000:70:00.0: 0xDEADBEEF | umac data3
[   60.242108] iwlwifi 0000:70:00.0: 0x00000016 | umac major
[   60.242111] iwlwifi 0000:70:00.0: 0x00058404 | umac minor
[   60.242114] iwlwifi 0000:70:00.0: 0xC0887DEC | frame pointer
[   60.242117] iwlwifi 0000:70:00.0: 0xC0887DEC | stack pointer
[   60.242120] iwlwifi 0000:70:00.0: 0x0900014F | last host cmd
[   60.242123] iwlwifi 0000:70:00.0: 0x00080002 | isr status reg
[   60.242202] iwlwifi 0000:70:00.0: FW error in SYNC CMD FW_PAGING_BLOCK_CMD
[   60.242265]  [<ffffffffc128e831>] iwl_trans_pcie_send_hcmd+0x461/0x580 [iwlwifi]
[   60.242285]  [<ffffffffc12952ae>] iwl_trans_send_cmd+0x3e/0x90 [iwlwifi]
[   60.242557] iwlwifi 0000:70:00.0: failed to send the paging cmd
[   60.242598] iwlwifi 0000:70:00.0: Failed to start RT ucode: -5
```

---

### Post by jeremy31 on 2016-11-12
*Thread moved to **Networking & Wireless**.*

Might want to try renaming the firmware to see if an older version works
```
cd /lib/firmware
sudo mv iwlwifi-8000C-22.ucode iwlwifi-8000C-22.bak
```

Reboot

---

### Post by fixxar on 2016-11-12
thanks for the help that made it work.

---

