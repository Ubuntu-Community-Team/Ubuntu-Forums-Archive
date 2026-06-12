---
title: "Periodic Wifi Network hang"
date: 2023-04-01
forum: Networking &amp; Wireless
---

### Post by makitso on 2023-04-01
I have a 2019 Dell XPS 15 7590.  All the hardware drivers are up to date.
Intel Corporation Wi-Fi 6 AX200 (rev 1a)

About once a week the wifi network fails requiring a network restart.  A ping to yahoo.com also fails as does a ping to 192.168.4.1
Problem existed before encrypting home folder.

Here are the error messages:

Dmesg

[242807.470223] wlp58s0: associate with 9c:a5:70:11:bb:c5 (try 1/3)
[242807.487056] wlp58s0: RX AssocResp from 9c:a5:70:11:bb:c5 (capab=0x1431 status=0 aid=3)
[242807.501686] wlp58s0: associated
[242807.566309] wlp58s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 9c:a5:70:11:bb:c5
[242976.581360] CIFS: VFS: \\192.168.4.205 has not responded in 180 seconds. Reconnecting...
[242976.581513] CIFS: VFS: \\192.168.4.205\rob error -11 on ioctl to get interface list
[260929.061063] iwlwifi 0000:3a:00.0: Microcode SW error detected. Restarting 0x0.
[260929.063558] iwlwifi 0000:3a:00.0: Start IWL Error Log Dump:
[260929.063566] iwlwifi 0000:3a:00.0: Transport status: 0x0000004A, valid: 6
[260929.063574] iwlwifi 0000:3a:00.0: Loaded firmware version: 72.daa05125.0 cc-a0-72.ucode
[260929.063580] iwlwifi 0000:3a:00.0: 0x00000071 | NMI_INTERRUPT_UMAC_FATAL    
[260929.063587] iwlwifi 0000:3a:00.0: 0x000026F7 | trm_hw_status0
[260929.063592] iwlwifi 0000:3a:00.0: 0x00000000 | trm_hw_status1
[260929.063597] iwlwifi 0000:3a:00.0: 0x004FBE16 | branchlink2
[260929.063603] iwlwifi 0000:3a:00.0: 0x00007DF8 | interruptlink1
[260929.063607] iwlwifi 0000:3a:00.0: 0x00007DF8 | interruptlink2
[260929.063612] iwlwifi 0000:3a:00.0: 0x0000F1E0 | data1
[260929.063617] iwlwifi 0000:3a:00.0: 0x00001000 | data2
[260929.063622] iwlwifi 0000:3a:00.0: 0x00000000 | data3
[260929.063627] iwlwifi 0000:3a:00.0: 0xD2018D7D | beacon time
[260929.063632] iwlwifi 0000:3a:00.0: 0xBFC374BB | tsf low
[260929.063637] iwlwifi 0000:3a:00.0: 0x00000219 | tsf hi
[260929.063642] iwlwifi 0000:3a:00.0: 0x00000000 | time gp1
[260929.063647] iwlwifi 0000:3a:00.0: 0xD7D6BD35 | time gp2
[260929.063652] iwlwifi 0000:3a:00.0: 0x00000001 | uCode revision type
[260929.063657] iwlwifi 0000:3a:00.0: 0x00000048 | uCode version major
[260929.063662] iwlwifi 0000:3a:00.0: 0xDAA05125 | uCode version minor
[260929.063667] iwlwifi 0000:3a:00.0: 0x00000340 | hw version
[260929.063672] iwlwifi 0000:3a:00.0: 0x00C89000 | board version
[260929.063677] iwlwifi 0000:3a:00.0: 0x80A2FC18 | hcmd
[260929.063682] iwlwifi 0000:3a:00.0: 0xE6E20000 | isr0
[260929.063686] iwlwifi 0000:3a:00.0: 0x01404000 | isr1
[260929.063691] iwlwifi 0000:3a:00.0: 0x08F80002 | isr2
[260929.063696] iwlwifi 0000:3a:00.0: 0x00C32008 | isr3
[260929.063701] iwlwifi 0000:3a:00.0: 0x00000000 | isr4
[260929.063706] iwlwifi 0000:3a:00.0: 0x04BB001C | last cmd Id
[260929.063711] iwlwifi 0000:3a:00.0: 0x0000F1E0 | wait_event
[260929.063715] iwlwifi 0000:3a:00.0: 0x00000080 | l2p_control
[260929.063720] iwlwifi 0000:3a:00.0: 0x00003C22 | l2p_duration
[260929.063725] iwlwifi 0000:3a:00.0: 0x0000003F | l2p_mhvalid
[260929.063730] iwlwifi 0000:3a:00.0: 0x000000CE | l2p_addr_match
[260929.063735] iwlwifi 0000:3a:00.0: 0x0000000B | lmpm_pmg_sel
[260929.063740] iwlwifi 0000:3a:00.0: 0x00000000 | timestamp
[260929.063744] iwlwifi 0000:3a:00.0: 0x0000D8D0 | flow_handler
[260929.064739] iwlwifi 0000:3a:00.0: Start IWL Error Log Dump:
[260929.064743] iwlwifi 0000:3a:00.0: Transport status: 0x0000004A, valid: 7
[260929.064749] iwlwifi 0000:3a:00.0: 0x20003463 | ADVANCED_SYSASSERT
[260929.064755] iwlwifi 0000:3a:00.0: 0x00000000 | umac branchlink1
[260929.064760] iwlwifi 0000:3a:00.0: 0x80455E3C | umac branchlink2
[260929.064765] iwlwifi 0000:3a:00.0: 0xC0081200 | umac interruptlink1
[260929.064770] iwlwifi 0000:3a:00.0: 0x00000000 | umac interruptlink2
[260929.064775] iwlwifi 0000:3a:00.0: 0xBFC374AE | umac data1
[260929.064780] iwlwifi 0000:3a:00.0: 0xD7D6BD25 | umac data2
[260929.064784] iwlwifi 0000:3a:00.0: 0x42F92605 | umac data3
[260929.064789] iwlwifi 0000:3a:00.0: 0x00000048 | umac major
[260929.064794] iwlwifi 0000:3a:00.0: 0xDAA05125 | umac minor
[260929.064799] iwlwifi 0000:3a:00.0: 0xD7D6BD2E | frame pointer
[260929.064804] iwlwifi 0000:3a:00.0: 0xC0885E00 | stack pointer
[260929.064808] iwlwifi 0000:3a:00.0: 0x00BC010C | last host cmd
[260929.064813] iwlwifi 0000:3a:00.0: 0x00000000 | isr status reg
[260929.065092] iwlwifi 0000:3a:00.0: IML/ROM dump:
[260929.065096] iwlwifi 0000:3a:00.0: 0x00000003 | IML/ROM error/state
[260929.065296] iwlwifi 0000:3a:00.0: 0x00005D19 | IML/ROM data1
[260929.065497] iwlwifi 0000:3a:00.0: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[260929.065599] iwlwifi 0000:3a:00.0: Fseq Registers:
[260929.065724] iwlwifi 0000:3a:00.0: 0x60000000 | FSEQ_ERROR_CODE
[260929.065849] iwlwifi 0000:3a:00.0: 0x80290021 | FSEQ_TOP_INIT_VERSION
[260929.065973] iwlwifi 0000:3a:00.0: 0x00050008 | FSEQ_CNVIO_INIT_VERSION
[260929.066097] iwlwifi 0000:3a:00.0: 0x0000A503 | FSEQ_OTP_VERSION
[260929.066222] iwlwifi 0000:3a:00.0: 0x80000003 | FSEQ_TOP_CONTENT_VERSION
[260929.066359] iwlwifi 0000:3a:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN
[260929.066489] iwlwifi 0000:3a:00.0: 0x00100530 | FSEQ_CNVI_ID
[260929.066616] iwlwifi 0000:3a:00.0: 0x00000532 | FSEQ_CNVR_ID
[260929.066744] iwlwifi 0000:3a:00.0: 0x00100530 | CNVI_AUX_MISC_CHIP
[260929.066882] iwlwifi 0000:3a:00.0: 0x00000532 | CNVR_AUX_MISC_CHIP
[260929.067016] iwlwifi 0000:3a:00.0: 0x05B0905B | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[260929.067153] iwlwifi 0000:3a:00.0: 0x0000025B | CNVR_SCU_SD_REGS_SD_RE

---

