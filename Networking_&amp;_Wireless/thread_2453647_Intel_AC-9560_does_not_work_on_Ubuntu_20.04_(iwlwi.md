---
title: "Intel AC-9560 does not work on Ubuntu 20.04 (iwlwifi)"
date: 2020-11-14
forum: Networking &amp; Wireless
---

### Post by gacoka on 2020-11-14
I cold booted my recently added Ubuntu distribution and my wifi stopped working. Additionally, my dmesg shows a 'failed to run INIT code -5' which signifies a problem with my firmware. However, I tried reinstalling the firmware and downloading the official drivers from both Intel and Dell to no avail. My WiFi radio is off (rfkill list) but my laptop is not on airplane mode. I know its not an issue with recognizing the wireless card as it is shown in the lspci output. Can you please help me?

The specifications for my computer are detailed below.[B]

Operating System and Kernel:[/B]
Description: Ubuntu 20.04.1 LTS focal
Linux Firmware: 1.189
Linux Headers: 5.4.0-42-generic

**dmesg**
[    7.308388] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[    7.321602] iwlwifi 0000:00:14.3: Found debug destination: EXTERNAL_DRAM
[    7.321606] iwlwifi 0000:00:14.3: Found debug configuration: 0
[    7.322475] iwlwifi 0000:00:14.3: loaded firmware version 46.8902351f.0 op_mode iwlmvm
[    7.358023] iwlwifi 0000:00:14.3: Detected Intel(R) Dual Band Wireless AC 9460, REV=0x318
[    7.365714] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[    7.366888] iwlwifi 0000:00:14.3: Allocated 0x00400000 bytes for firmware monitor.
[    7.371425] iwlwifi 0000:00:14.3: Microcode SW error detected. Restarting 0x0.
[    7.371432] iwlwifi 0000:00:14.3: Not valid error log pointer 0x00000000 for Init uCode
[    7.371442] iwlwifi 0000:00:14.3: Fseq Registers:
[    7.371445] iwlwifi 0000:00:14.3: 0x8000E404 | FSEQ_ERROR_CODE
[    7.371455] iwlwifi 0000:00:14.3: 0x1440C788 | FSEQ_TOP_INIT_VERSION
[    7.371458] iwlwifi 0000:00:14.3: 0x45163477 | FSEQ_CNVIO_INIT_VERSION
[    7.371461] iwlwifi 0000:00:14.3: 0x055260E5 | FSEQ_OTP_VERSION
[    7.371464] iwlwifi 0000:00:14.3: 0x39B2FADF | FSEQ_TOP_CONTENT_VERSION
[    7.371466] iwlwifi 0000:00:14.3: 0xC3BBD7F0 | FSEQ_ALIVE_TOKEN
[    7.371469] iwlwifi 0000:00:14.3: 0x00489810 | FSEQ_CNVI_ID
[    7.371472] iwlwifi 0000:00:14.3: 0xF7EA67FF | FSEQ_CNVR_ID
[    7.371475] iwlwifi 0000:00:14.3: 0x01000100 | CNVI_AUX_MISC_CHIP
[    7.371511] iwlwifi 0000:00:14.3: 0xA5A5A5A2 | CNVR_AUX_MISC_CHIP
[    7.371586] iwlwifi 0000:00:14.3: 0xA5A5A5A2 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    7.371662] iwlwifi 0000:00:14.3: 0xA5A5A5A2 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    7.371866] iwlwifi 0000:00:14.3: SecBoot CPU1 Status: 0xa5a5a5a2, CPU2 Status: 0xa5a5a5a2
[    7.371877] iwlwifi 0000:00:14.3: Failed to start INIT ucode: -5
[    7.371880] iwlwifi 0000:00:14.3: Collecting data: trigger 16 fired.
[    7.618273] iwlwifi 0000:00:14.3: Firmware not running - cannot dump error
[    7.630421] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -5

**lspci**
00:14.3 Network controller: Intel Corporation Cannon Point-LP CNVi [Wireless-AC] (rev 30)

**rfkill list**
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


**sudo lshw -C network**
  *-network                 
       description: Network controller
       product: Cannon Point-LP CNVi [Wireless-AC]
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       version: 30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: driver=iwlwifi latency=0
       resources: irq:16 memory:a121c000-a121ffff

---

