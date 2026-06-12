---
title: "Wifi 17.04 not working"
date: 2017-05-02
forum: Networking &amp; Wireless
---

### Post by sbdesign on 2017-05-02
My laptop came with buntu 16.10 - if i reinstall it as the laptop manufacturer supplied it the wifi card works.

The wifi card doesn't work once I upgrade to 17.04... there are also lots of error log messages:

```
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00000000 | isr status reg
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x095E019C | last host cmd
21:00:16 kernel: iwlwifi 0000:01:00.0: 0xC0886298 | stack pointer
21:00:16 kernel: iwlwifi 0000:01:00.0: 0xC0886298 | frame pointer
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00049ED0 | umac minor
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00000015 | umac major
21:00:16 kernel: iwlwifi 0000:01:00.0: 0xDEADBEEF | umac data3
21:00:16 kernel: iwlwifi 0000:01:00.0: 0xC0081000 | umac data2
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00000800 | umac data1
21:00:16 kernel: iwlwifi 0000:01:00.0: 0xC0081000 | umac interruptlink2
21:00:16 kernel: iwlwifi 0000:01:00.0: 0xC0081000 | umac interruptlink1
21:00:16 kernel: iwlwifi 0000:01:00.0: 0xC008113A | umac branchlink2
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00000000 | umac branchlink1
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00000070 | ADVANCED_SYSASSERT
21:00:16 kernel: iwlwifi 0000:01:00.0: Status: 0x00000000, count: 7
21:00:16 kernel: iwlwifi 0000:01:00.0: Start IWL Error Log Dump:
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00346070 | flow_handler
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x09031905 | timestamp
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x0000000D | lmpm_pmg_sel
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x000000EE | l2p_addr_match
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00000003 | l2p_mhvalid
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00002020 | l2p_duration
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00002E74 | l2p_control
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00000000 | wait_event
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00004110 | last cmd Id
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00000000 | isr4
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x0040A8C4 | isr3
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x0800180A | isr2
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x01800000 | isr1
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x80022002 | isr0
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x027B001C | hcmd
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00C89008 | board version
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00000201 | hw version
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00049ED0 | uCode version minor
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00000015 | uCode version major
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00000000 | uCode revision type
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x011A48E2 | time gp2
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00000000 | time gp1
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x0000001C | tsf hi
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x9F8FE3B9 | tsf low
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x1D005C47 | beacon time
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x07830000 | data3
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00000080 | data2
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00000000 | data1
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x0002A382 | interruptlink2
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00026AC4 | interruptlink1
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00000BD8 | branchlink2
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00000000 | trm_hw_status1
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x008006F4 | trm_hw_status0
21:00:16 kernel: iwlwifi 0000:01:00.0: 0x00000084 | NMI_INTERRUPT_UNKNOWN       
21:00:16 kernel: iwlwifi 0000:01:00.0: Loaded firmware version: 21.302800.0
21:00:16 kernel: iwlwifi 0000:01:00.0: Status: 0x00000000, count: 6
21:00:16 kernel: iwlwifi 0000:01:00.0: Start IWL Error Log Dump:
21:00:16 kernel: iwlwifi 0000:01:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
21:00:16 kernel: iwlwifi 0000:01:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
21:00:16 kernel: iwlwifi 0000:01:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
21:00:16 kernel: iwlwifi 0000:01:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X03030000
21:00:16 kernel: iwlwifi 0000:01:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
21:00:16 kernel: iwlwifi 0000:01:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00801054
21:00:16 kernel: iwlwifi 0000:01:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000060
21:00:16 kernel: iwlwifi 0000:01:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X045d29f0
21:00:16 kernel: iwlwifi 0000:01:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X45edf500
21:00:16 kernel: iwlwifi 0000:01:00.0: FH register values:
21:00:16 kernel: iwlwifi 0000:01:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
21:00:16 kernel: iwlwifi 0000:01:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
21:00:16 kernel: iwlwifi 0000:01:00.0:      CSR_MONITOR_STATUS_REG: 0Xc03803c0
21:00:16 kernel: iwlwifi 0000:01:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
21:00:16 kernel: iwlwifi 0000:01:00.0:        CSR_GIO_CHICKEN_BITS: 0X07800200
21:00:16 kernel: iwlwifi 0000:01:00.0:        CSR_DRAM_INT_TBL_REG: 0X8846011f
21:00:16 kernel: iwlwifi 0000:01:00.0:                 CSR_LED_REG: 0X00000060
21:00:16 kernel: iwlwifi 0000:01:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
21:00:16 kernel: iwlwifi 0000:01:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
21:00:16 kernel: iwlwifi 0000:01:00.0:           CSR_GP_DRIVER_REG: 0X00000000
21:00:16 kernel: iwlwifi 0000:01:00.0:            CSR_GP_UCODE_REG: 0X00000000
21:00:16 kernel: iwlwifi 0000:01:00.0:                 CSR_GIO_REG: 0X001f0044
21:00:16 kernel: iwlwifi 0000:01:00.0:              CSR_OTP_GP_REG: 0Xd55555d5
21:00:16 kernel: iwlwifi 0000:01:00.0:               CSR_EEPROM_GP: 0Xd55555d5
21:00:16 kernel: iwlwifi 0000:01:00.0:              CSR_EEPROM_REG: 0Xd55555d5
21:00:16 kernel: iwlwifi 0000:01:00.0:                  CSR_HW_REV: 0X00000201
21:00:16 kernel: iwlwifi 0000:01:00.0:                CSR_GP_CNTRL: 0X08040005
21:00:16 kernel: iwlwifi 0000:01:00.0:                   CSR_RESET: 0X00000000
21:00:16 kernel: iwlwifi 0000:01:00.0:                 CSR_GPIO_IN: 0X00000019
21:00:16 kernel: iwlwifi 0000:01:00.0:           CSR_FH_INT_STATUS: 0X00000000
21:00:16 kernel: iwlwifi 0000:01:00.0:                CSR_INT_MASK: 0X00000000
21:00:16 kernel: iwlwifi 0000:01:00.0:                     CSR_INT: 0X00000000
21:00:16 kernel: iwlwifi 0000:01:00.0:          CSR_INT_COALESCING: 0X00000040
21:00:16 kernel: iwlwifi 0000:01:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c89008
21:00:16 kernel: iwlwifi 0000:01:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
21:00:16 kernel: iwlwifi 0000:01:00.0: CSR values:
21:00:16 kernel: iwlwifi 0000:01:00.0: Microcode SW error detected.  Restarting 0x2000000.
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 30 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 29 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 28 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 27 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 26 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 25 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 24 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 23 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 22 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 21 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 20 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 15 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 10 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [95,95]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 8 is active and mapped to fifo 3 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 7 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 6 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 5 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 4 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [123,67]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
21:00:16 kernel: iwlwifi 0000:01:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [2,2]
21:00:16 kernel: iwlwifi 0000:01:00.0: FH TRBs(7) = 0x0070905e
21:00:16 kernel: iwlwifi 0000:01:00.0: FH TRBs(6) = 0x1ee23842
21:00:16 kernel: iwlwifi 0000:01:00.0: FH TRBs(5) = 0xc1952c60
21:00:16 kernel: iwlwifi 0000:01:00.0: FH TRBs(4) = 0xdff5cf7f
21:00:16 kernel: iwlwifi 0000:01:00.0: FH TRBs(3) = 0x80300001
21:00:16 kernel: iwlwifi 0000:01:00.0: FH TRBs(2) = 0x5f6072f3
21:00:16 kernel: iwlwifi 0000:01:00.0: FH TRBs(1) = 0x8010208a
21:00:16 kernel: iwlwifi 0000:01:00.0: FH TRBs(0) = 0x26fd9178
21:00:16 kernel: iwl data: 00000000: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
21:00:16 kernel: iwlwifi 0000:01:00.0: Current SW read_ptr 123 write_ptr 67
21:00:16 kernel: iwlwifi 0000:01:00.0: Queue 2 stuck for 10000 ms.
21:00:01 dhclient: receive_packet failed on enx000ec6fa246d: Network is down
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00000000 | isr status reg
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x096C019C | last host cmd
20:59:56 kernel: iwlwifi 0000:01:00.0: 0xC0886298 | stack pointer
20:59:56 kernel: iwlwifi 0000:01:00.0: 0xC0886298 | frame pointer
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00049ED0 | umac minor
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00000015 | umac major
20:59:56 kernel: iwlwifi 0000:01:00.0: 0xDEADBEEF | umac data3
20:59:56 kernel: iwlwifi 0000:01:00.0: 0xC0081000 | umac data2
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00000800 | umac data1
20:59:56 kernel: iwlwifi 0000:01:00.0: 0xC0081000 | umac interruptlink2
20:59:56 kernel: iwlwifi 0000:01:00.0: 0xC0081000 | umac interruptlink1
20:59:56 kernel: iwlwifi 0000:01:00.0: 0xC008113A | umac branchlink2
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00000000 | umac branchlink1
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00000070 | ADVANCED_SYSASSERT
20:59:56 kernel: iwlwifi 0000:01:00.0: Status: 0x00000000, count: 7
20:59:56 kernel: iwlwifi 0000:01:00.0: Start IWL Error Log Dump:
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00347880 | flow_handler
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x09031905 | timestamp
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x0000000D | lmpm_pmg_sel
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x000000CE | l2p_addr_match
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x0000003F | l2p_mhvalid
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00012120 | l2p_duration
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00000080 | l2p_control
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00000000 | wait_event
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00014110 | last cmd Id
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00000000 | isr4
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x004068C5 | isr3
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x08001802 | isr2
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00800000 | isr1
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x8002200A | isr0
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x0007001C | hcmd
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00C89008 | board version
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00000201 | hw version
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00049ED0 | uCode version minor
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00000015 | uCode version major
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00000000 | uCode revision type
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x0129C44D | time gp2
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00000000 | time gp1
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x0000001C | tsf hi
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x9E6AEA23 | tsf low
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x250125DD | beacon time
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x07830000 | data3
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00000080 | data2
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00000000 | data1
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00000120 | interruptlink2
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00026AC4 | interruptlink1
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00000BD8 | branchlink2
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00000000 | trm_hw_status1
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x008006B4 | trm_hw_status0
20:59:56 kernel: iwlwifi 0000:01:00.0: 0x00000084 | NMI_INTERRUPT_UNKNOWN       
20:59:56 kernel: iwlwifi 0000:01:00.0: Loaded firmware version: 21.302800.0
20:59:56 kernel: iwlwifi 0000:01:00.0: Status: 0x00000000, count: 6
20:59:56 kernel: iwlwifi 0000:01:00.0: Start IWL Error Log Dump:
20:59:56 kernel: iwlwifi 0000:01:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
20:59:56 kernel: iwlwifi 0000:01:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
20:59:56 kernel: iwlwifi 0000:01:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
20:59:56 kernel: iwlwifi 0000:01:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X03030000
20:59:56 kernel: iwlwifi 0000:01:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
20:59:56 kernel: iwlwifi 0000:01:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00801054
20:59:56 kernel: iwlwifi 0000:01:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000078
20:59:56 kernel: iwlwifi 0000:01:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X045d29f0
20:59:56 kernel: iwlwifi 0000:01:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X45edf500
20:59:56 kernel: iwlwifi 0000:01:00.0: FH register values:
20:59:56 kernel: iwlwifi 0000:01:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0010
20:59:56 kernel: iwlwifi 0000:01:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
20:59:56 kernel: iwlwifi 0000:01:00.0:      CSR_MONITOR_STATUS_REG: 0Xc03803c0
20:59:56 kernel: iwlwifi 0000:01:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
20:59:56 kernel: iwlwifi 0000:01:00.0:        CSR_GIO_CHICKEN_BITS: 0X07800200
20:59:56 kernel: iwlwifi 0000:01:00.0:        CSR_DRAM_INT_TBL_REG: 0X8846011f
20:59:56 kernel: iwlwifi 0000:01:00.0:                 CSR_LED_REG: 0X00000060
20:59:56 kernel: iwlwifi 0000:01:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
20:59:56 kernel: iwlwifi 0000:01:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
```

Does anyone know what the problem might be? Thanks for any help, if you need more info please let me know

---

### Post by sbdesign on 2017-05-02
Hre is my wifi info

---

### Post by jeremy31 on 2017-05-02
I would disable power managment on the wifi with
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf{/code]
[code]systemctl restart network-manager.service
```

If you can change the encryption on the wifi router to WPA2 only as it is showing TKIP being enabled and that could contribute to the issue

---

### Post by sbdesign on 2017-05-02
I ran the command... still nothing. It isn't possible to change from tkip, sorry

---

### Post by jeremy31 on 2017-05-02
I would try a reboot and post new wireless-script results if it isn't better

You may want to consider installing Ubuntu 16.04 or 16.04.1 as they are supported until 2021

---

### Post by ajgreeny on 2017-05-02
I suspect that you are using kernel 4.4.0-77 which has had some wifi problems for other users as well.

Try booting from the previous kernel, probably 4.4.0-75, from the grub menu and you may find as they have that wifi reappears.

Another user said earlier that he was about to file a bug for this problem on 4.4.0-77, and I think it is probably here.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687623](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687623)

EDIT:
Whoops!!!
I should have read more accurately as I thought I read 16.04, not 17.04, in your post.
Booting from an earlier kernel may help, however, if you have one on the machine.

---

### Post by sbdesign on 2017-05-02
4.10.0-20-generic is my current kernel

---

### Post by Dennis N on 2017-05-02
Can you connect to your router? If not, the solution at this link may be a solution (I used it on 17.04 and it restored my ability to connect).

[https://askubuntu.com/questions/904864/wifi-doesnt-work-on-17-04](https://askubuntu.com/questions/904864/wifi-doesnt-work-on-17-04)

See the first (and only) answer.

---

### Post by sbdesign on 2017-05-03
I can connect to my router and seem to be able to ping sites... I just can't use the internet even when connected through a browser

---

