---
title: "Network device not found in ubuntu 22.04"
date: 2023-07-08
forum: Networking &amp; Wireless
---

### Post by 0x-pranay on 2023-07-08
Hi all, 


My wifi got disconnected while I was using my laptop. I couldn't connect back cause it says No network device found. 

Here are some info I think will be helpful. 

```

$ uname -a 
Linux pranay-laptop 5.19.0-46-generic #47~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Jun 21 15:35:31 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

$ lspci -knn | grep Net -A400:14.3 Network controller [0280]: Intel Corporation Ice Lake-LP PCH CNVi WiFi [8086:34f0] (rev 30)
    DeviceName: WLAN
    Subsystem: Intel Corporation Wireless-AC 9461 [8086:0264]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

$ rfkill list 
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no





```

Here are the things I tried but none worked. 
 
1.  `sudo systemctl status NetworkManager.service` 
2. Reinstall linux-firmware 
`sudo apt-get install --reinstall linux-firmware` 
```

$ lsmod | grep iwlwifi
iwlwifi               503808  1 iwlmvm
cfg80211             1052672  3 iwlmvm,iwlwifi,mac80211


```



```

$ dmesg | grep iwlwifi[   10.208746] iwlwifi 0000:00:14.3: Detected Intel(R) Wireless-AC 9461, REV=0x332
[   11.233127] iwlwifi 0000:00:14.3: SecBoot CPU1 Status: 0x54af, CPU2 Status: 0x3
[   11.233153] iwlwifi 0000:00:14.3: WFPM_LMAC1_PD_NOTIFICATION: 0x200
[   11.233162] iwlwifi 0000:00:14.3: HPM_SECONDARY_DEVICE_STATE: 0x142
[   11.233171] iwlwifi 0000:00:14.3: WFPM_MAC_OTP_CFG7_ADDR: 0x0
[   11.233180] iwlwifi 0000:00:14.3: WFPM_MAC_OTP_CFG7_DATA: 0x0
[   11.233188] iwlwifi 0000:00:14.3: UMAC PC: 0xc008156c
[   11.233197] iwlwifi 0000:00:14.3: LMAC PC: 0x11a88
[   11.233199] iwlwifi 0000:00:14.3: WRT: Collecting data: ini trigger 13 fired (delay=0ms).
[   11.234292] iwlwifi 0000:00:14.3: Loaded firmware version: 72.daa05125.0 Qu-c0-jf-b0-72.ucode
[   11.234294] iwlwifi 0000:00:14.3: 0x00000000 | ADVANCED_SYSASSERT          
[   11.234295] iwlwifi 0000:00:14.3: 0x00000000 | trm_hw_status0
[   11.234296] iwlwifi 0000:00:14.3: 0x00000000 | trm_hw_status1
[   11.234297] iwlwifi 0000:00:14.3: 0x00000000 | branchlink2
[   11.234298] iwlwifi 0000:00:14.3: 0x00000000 | interruptlink1
[   11.234298] iwlwifi 0000:00:14.3: 0x00000000 | interruptlink2
[   11.234299] iwlwifi 0000:00:14.3: 0x00000000 | data1
[   11.234300] iwlwifi 0000:00:14.3: 0x00000000 | data2
[   11.234301] iwlwifi 0000:00:14.3: 0x00000000 | data3
[   11.234302] iwlwifi 0000:00:14.3: 0x00000000 | beacon time
[   11.234303] iwlwifi 0000:00:14.3: 0x00000000 | tsf low
[   11.234304] iwlwifi 0000:00:14.3: 0x00000000 | tsf hi
[   11.234304] iwlwifi 0000:00:14.3: 0x00000000 | time gp1
[   11.234305] iwlwifi 0000:00:14.3: 0x00000000 | time gp2
[   11.234306] iwlwifi 0000:00:14.3: 0x00000000 | uCode revision type
[   11.234307] iwlwifi 0000:00:14.3: 0x00000000 | uCode version major
[   11.234308] iwlwifi 0000:00:14.3: 0x00000000 | uCode version minor
[   11.234309] iwlwifi 0000:00:14.3: 0x00000000 | hw version
[   11.234310] iwlwifi 0000:00:14.3: 0x00000000 | board version
[   11.234311] iwlwifi 0000:00:14.3: 0x00000000 | hcmd
[   11.234311] iwlwifi 0000:00:14.3: 0x00000000 | isr0
[   11.234312] iwlwifi 0000:00:14.3: 0x00000000 | isr1
[   11.234313] iwlwifi 0000:00:14.3: 0x00000000 | isr2
[   11.234314] iwlwifi 0000:00:14.3: 0x00000000 | isr3
[   11.234315] iwlwifi 0000:00:14.3: 0x00000000 | isr4
[   11.234315] iwlwifi 0000:00:14.3: 0x00000000 | last cmd Id
[   11.234316] iwlwifi 0000:00:14.3: 0x00000000 | wait_event
[   11.234317] iwlwifi 0000:00:14.3: 0x00000000 | l2p_control
[   11.234318] iwlwifi 0000:00:14.3: 0x00000000 | l2p_duration
[   11.234319] iwlwifi 0000:00:14.3: 0x00000000 | l2p_mhvalid
[   11.234320] iwlwifi 0000:00:14.3: 0x00000000 | l2p_addr_match
[   11.234321] iwlwifi 0000:00:14.3: 0x00000000 | lmpm_pmg_sel
[   11.234322] iwlwifi 0000:00:14.3: 0x00000000 | timestamp
[   11.234322] iwlwifi 0000:00:14.3: 0x00000000 | flow_handler
[   11.234362] iwlwifi 0000:00:14.3: Start IWL Error Log Dump:
[   11.234363] iwlwifi 0000:00:14.3: Transport status: 0x00000042, valid: 7
[   11.234364] iwlwifi 0000:00:14.3: 0x20000066 | NMI_INTERRUPT_HOST
[   11.234365] iwlwifi 0000:00:14.3: 0x00000000 | umac branchlink1
[   11.234366] iwlwifi 0000:00:14.3: 0x80453BCC | umac branchlink2
[   11.234367] iwlwifi 0000:00:14.3: 0x8046FFDA | umac interruptlink1
[   11.234368] iwlwifi 0000:00:14.3: 0xC0081570 | umac interruptlink2
[   11.234369] iwlwifi 0000:00:14.3: 0x01000000 | umac data1
[   11.234370] iwlwifi 0000:00:14.3: 0xC0081570 | umac data2
[   11.234371] iwlwifi 0000:00:14.3: 0x00000000 | umac data3
[   11.234372] iwlwifi 0000:00:14.3: 0x00000048 | umac major
[   11.234373] iwlwifi 0000:00:14.3: 0xDAA05125 | umac minor
[   11.234374] iwlwifi 0000:00:14.3: 0x000F6E88 | frame pointer
[   11.234374] iwlwifi 0000:00:14.3: 0xC0887F00 | stack pointer
[   11.234375] iwlwifi 0000:00:14.3: 0x00000000 | last host cmd
[   11.234376] iwlwifi 0000:00:14.3: 0x00000004 | isr status reg
[   11.234398] iwlwifi 0000:00:14.3: IML/ROM dump:
[   11.234398] iwlwifi 0000:00:14.3: 0x00000003 | IML/ROM error/state
[   11.234407] iwlwifi 0000:00:14.3: 0x000054AF | IML/ROM data1
[   11.234416] iwlwifi 0000:00:14.3: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[   11.234422] iwlwifi 0000:00:14.3: Fseq Registers:
[   11.234424] iwlwifi 0000:00:14.3: 0x60000000 | FSEQ_ERROR_CODE
[   11.234427] iwlwifi 0000:00:14.3: 0x80260000 | FSEQ_TOP_INIT_VERSION
[   11.234430] iwlwifi 0000:00:14.3: 0x00020006 | FSEQ_CNVIO_INIT_VERSION
[   11.234433] iwlwifi 0000:00:14.3: 0x0000A384 | FSEQ_OTP_VERSION
[   11.234436] iwlwifi 0000:00:14.3: 0x424161DA | FSEQ_TOP_CONTENT_VERSION
[   11.234439] iwlwifi 0000:00:14.3: 0x4552414E | FSEQ_ALIVE_TOKEN
[   11.234442] iwlwifi 0000:00:14.3: 0x02000300 | FSEQ_CNVI_ID
[   11.234444] iwlwifi 0000:00:14.3: 0x00000201 | FSEQ_CNVR_ID
[   11.234447] iwlwifi 0000:00:14.3: 0x02000300 | CNVI_AUX_MISC_CHIP
[   11.234452] iwlwifi 0000:00:14.3: 0x00000201 | CNVR_AUX_MISC_CHIP
[   11.234457] iwlwifi 0000:00:14.3: 0x0000485B | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[   11.234491] iwlwifi 0000:00:14.3: 0xA5A5A5A2 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[   11.234494] iwlwifi 0000:00:14.3: Failed to start RT ucode: -110
[   11.234495] iwlwifi 0000:00:14.3: WRT: Collecting data: ini trigger 13 fired (delay=0ms).
[   12.275382] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -110
[   12.287756] iwlwifi 0000:00:14.3: retry init count 2


```

I tried restarting the machine after each try but none worked so far. 


I been trying to find a solution for this for a day and nothing helped. 

Best regards.

---

