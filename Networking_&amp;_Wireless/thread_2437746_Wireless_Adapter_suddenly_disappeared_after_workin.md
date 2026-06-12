---
title: "Wireless Adapter suddenly disappeared after working for months"
date: 2020-02-28
forum: Networking &amp; Wireless
---

### Post by animalbrain on 2020-02-28
Ubuntu 19.10 on Thinkpad X1 Carbon 7th Gen. Intel Wireless-AC 9560 adapter.

Wifi has worked fine on the laptop for the past couple months, and a few days ago it suddenly will not find the adapter. Everything works fine booting in Windows 10 on the laptop.

Here is the best I could do to find some clues - output from dmesg below.

Thanks for any suggestions or other things to look at!!

```
[FONT=Arial]$ dmesg | grep iwlwifi[/FONT]
[FONT=Arial][    2.677639] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)[/FONT]
[FONT=Arial][    2.702553] iwlwifi 0000:00:14.3: TLV_FW_FSEQ_VERSION: FSEQ Version: 43.2.23.17[/FONT]
[FONT=Arial][    2.703033] iwlwifi 0000:00:14.3: loaded firmware version 48.4fa0041f.0 op_mode iwlmvm[/FONT]
[FONT=Arial][    2.738738] iwlwifi 0000:00:14.3: Detected Intel(R) Wireless-AC 9560 160MHz, REV=0x354[/FONT]
[FONT=Arial][    3.763012] iwlwifi 0000:00:14.3: Collecting data: trigger 15 fired.[/FONT]
[FONT=Arial][    3.763162] iwlwifi 0000:00:14.3: Start IWL Error Log Dump:[/FONT]
[FONT=Arial][    3.763164] iwlwifi 0000:00:14.3: Status: 0x00000000, count: -1611023411[/FONT]
[FONT=Arial][    3.763165] iwlwifi 0000:00:14.3: Loaded firmware version: 48.4fa0041f.0[/FONT]
[FONT=Arial][    3.763166] iwlwifi 0000:00:14.3: 0x3BEFFCE4 | ADVANCED_SYSASSERT          [/FONT]
[FONT=Arial][    3.763167] iwlwifi 0000:00:14.3: 0xF94621E5 | trm_hw_status0[/FONT]
[FONT=Arial][    3.763167] iwlwifi 0000:00:14.3: 0x1E41F808 | trm_hw_status1[/FONT]
[FONT=Arial][    3.763168] iwlwifi 0000:00:14.3: 0x814FBA63 | branchlink2[/FONT]
[FONT=Arial][    3.763169] iwlwifi 0000:00:14.3: 0xF98A3F7B | interruptlink1[/FONT]
[FONT=Arial][    3.763169] iwlwifi 0000:00:14.3: 0x80A81622 | interruptlink2[/FONT]
[FONT=Arial][    3.763170] iwlwifi 0000:00:14.3: 0x688C915A | data1[/FONT]
[FONT=Arial][    3.763171] iwlwifi 0000:00:14.3: 0xF57D6C5F | data2[/FONT]
[FONT=Arial][    3.763171] iwlwifi 0000:00:14.3: 0xBE9F67BC | data3[/FONT]
[FONT=Arial][    3.763172] iwlwifi 0000:00:14.3: 0x769019B6 | beacon time[/FONT]
[FONT=Arial][    3.763173] iwlwifi 0000:00:14.3: 0x1077FFD7 | tsf low[/FONT]
[FONT=Arial][    3.763173] iwlwifi 0000:00:14.3: 0xF38D6BD7 | tsf hi[/FONT]
[FONT=Arial][    3.763174] iwlwifi 0000:00:14.3: 0x1E67D534 | time gp1[/FONT]
[FONT=Arial][    3.763174] iwlwifi 0000:00:14.3: 0x8063AFCA | time gp2[/FONT]
[FONT=Arial][    3.763175] iwlwifi 0000:00:14.3: 0x6AD4C512 | uCode revision type[/FONT]
[FONT=Arial][    3.763176] iwlwifi 0000:00:14.3: 0xF0EB826C | uCode version major[/FONT]
[FONT=Arial][    3.763176] iwlwifi 0000:00:14.3: 0x26A7BDCB | uCode version minor[/FONT]
[FONT=Arial][    3.763177] iwlwifi 0000:00:14.3: 0x92FE5A3A | hw version[/FONT]
[FONT=Arial][    3.763178] iwlwifi 0000:00:14.3: 0x19920644 | board version[/FONT]
[FONT=Arial][    3.763178] iwlwifi 0000:00:14.3: 0xBA9EE2DD | hcmd[/FONT]
[FONT=Arial][    3.763179] iwlwifi 0000:00:14.3: 0xD8D9B746 | isr0[/FONT]
[FONT=Arial][    3.763180] iwlwifi 0000:00:14.3: 0x8D47FC6B | isr1[/FONT]
[FONT=Arial][    3.763180] iwlwifi 0000:00:14.3: 0x665E5524 | isr2[/FONT]
[FONT=Arial][    3.763181] iwlwifi 0000:00:14.3: 0xB3291CDA | isr3[/FONT]
[FONT=Arial][    3.763181] iwlwifi 0000:00:14.3: 0x7EC15994 | isr4[/FONT]
[FONT=Arial][    3.763182] iwlwifi 0000:00:14.3: 0x96160EDD | last cmd Id[/FONT]
[FONT=Arial][    3.763183] iwlwifi 0000:00:14.3: 0xE423E41B | wait_event[/FONT]
[FONT=Arial][    3.763183] iwlwifi 0000:00:14.3: 0xCD71518A | l2p_control[/FONT]
[FONT=Arial][    3.763184] iwlwifi 0000:00:14.3: 0xD76798B9 | l2p_duration[/FONT]
[FONT=Arial][    3.763185] iwlwifi 0000:00:14.3: 0xAF9B6DAA | l2p_mhvalid[/FONT]
[FONT=Arial][    3.763185] iwlwifi 0000:00:14.3: 0xC8A55D30 | l2p_addr_match[/FONT]
[FONT=Arial][    3.763186] iwlwifi 0000:00:14.3: 0x7303686D | lmpm_pmg_sel[/FONT]
[FONT=Arial][    3.763187] iwlwifi 0000:00:14.3: 0x735E1437 | timestamp[/FONT]
[FONT=Arial][    3.763187] iwlwifi 0000:00:14.3: 0x593E9BCF | flow_handler[/FONT]
[FONT=Arial][    3.763220] iwlwifi 0000:00:14.3: Start IWL Error Log Dump:[/FONT]
[FONT=Arial][    3.763220] iwlwifi 0000:00:14.3: Status: 0x00000000, count: 7[/FONT]
[FONT=Arial][    3.763221] iwlwifi 0000:00:14.3: 0x201013F1 | ADVANCED_SYSASSERT[/FONT]
[FONT=Arial][    3.763222] iwlwifi 0000:00:14.3: 0x00000000 | umac branchlink1[/FONT]
[FONT=Arial][    3.763223] iwlwifi 0000:00:14.3: 0xC008CF5C | umac branchlink2[/FONT]
[FONT=Arial][    3.763223] iwlwifi 0000:00:14.3: 0x00000000 | umac interruptlink1[/FONT]
[FONT=Arial][    3.763224] iwlwifi 0000:00:14.3: 0x00000000 | umac interruptlink2[/FONT]
[FONT=Arial][    3.763224] iwlwifi 0000:00:14.3: 0x00000003 | umac data1[/FONT]
[FONT=Arial][    3.763225] iwlwifi 0000:00:14.3: 0x20000302 | umac data2[/FONT]
[FONT=Arial][    3.763226] iwlwifi 0000:00:14.3: 0x01300202 | umac data3[/FONT]
[FONT=Arial][    3.763226] iwlwifi 0000:00:14.3: 0x00000030 | umac major[/FONT]
[FONT=Arial][    3.763227] iwlwifi 0000:00:14.3: 0x4FA0041F | umac minor[/FONT]
[FONT=Arial][    3.763228] iwlwifi 0000:00:14.3: 0x00005D22 | frame pointer[/FONT]
[FONT=Arial][    3.763228] iwlwifi 0000:00:14.3: 0xC0887F58 | stack pointer[/FONT]
[FONT=Arial][    3.763229] iwlwifi 0000:00:14.3: 0x00000000 | last host cmd[/FONT]
[FONT=Arial][    3.763230] iwlwifi 0000:00:14.3: 0x00000000 | isr status reg[/FONT]
[FONT=Arial][    3.763246] iwlwifi 0000:00:14.3: Fseq Registers:[/FONT]
[FONT=Arial][    3.763248] iwlwifi 0000:00:14.3: 0x00000003 | FSEQ_ERROR_CODE[/FONT]
[FONT=Arial][    3.763250] iwlwifi 0000:00:14.3: 0x00000000 | FSEQ_TOP_INIT_VERSION[/FONT]
[FONT=Arial][    3.763252] iwlwifi 0000:00:14.3: 0x7A3213E9 | FSEQ_CNVIO_INIT_VERSION[/FONT]
[FONT=Arial][    3.763255] iwlwifi 0000:00:14.3: 0x0000A384 | FSEQ_OTP_VERSION[/FONT]
[FONT=Arial][    3.763257] iwlwifi 0000:00:14.3: 0xC28FC6D2 | FSEQ_TOP_CONTENT_VERSION[/FONT]
[FONT=Arial][    3.763259] iwlwifi 0000:00:14.3: 0x68A02BD3 | FSEQ_ALIVE_TOKEN[/FONT]
[FONT=Arial][    3.763261] iwlwifi 0000:00:14.3: 0x3FEFEACD | FSEQ_CNVI_ID[/FONT]
[FONT=Arial][    3.763264] iwlwifi 0000:00:14.3: 0x52AC25AC | FSEQ_CNVR_ID[/FONT]
[FONT=Arial][    3.763266] iwlwifi 0000:00:14.3: 0x20000302 | CNVI_AUX_MISC_CHIP[/FONT]
[FONT=Arial][    3.763270] iwlwifi 0000:00:14.3: 0x01300202 | CNVR_AUX_MISC_CHIP[/FONT]
[FONT=Arial][    3.763275] iwlwifi 0000:00:14.3: 0x0000485B | CNVR_SCU_SD_REGS_SD_REG_DIG_[/FONT][FONT=Arial]DCDC_VTRIM[/FONT]
[FONT=Arial][    3.763309] iwlwifi 0000:00:14.3: 0xA5A5A5A2 | CNVR_SCU_SD_REGS_SD_REG_[/FONT][FONT=Arial]ACTIVE_VDIG_MIRROR[/FONT]
[FONT=Arial][    3.763337] iwlwifi 0000:00:14.3: SecBoot CPU1 Status: 0x5c94, CPU2 Status: 0x3[/FONT]
[FONT=Arial][    3.763338] iwlwifi 0000:00:14.3: Failed to start RT ucode: -110[/FONT]
[FONT=Arial][    3.763340] iwlwifi 0000:00:14.3: Firmware not running - cannot dump error[/FONT]
[FONT=Arial][    3.775188] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -110[/FONT]
```

---

### Post by CelticWarrior on 2020-02-28
A similar situation: [https://askubuntu.com/a/1191307](https://askubuntu.com/a/1191307)
I suggest reading it until the end where you'll find an interesting note from the author. I would try the last edit before the modprobe.

---

### Post by chili555 on 2020-02-28
Please reboot. Interrupt the boot process and, at the GRUB menu, boot into an earlier kernel version, likely 5.3.0-28. Does the wireless work now?

Please see the last three comments here: [https://askubuntu.com/questions/1192531/wifi-adapter-not-found-for-dell-inspiron-5590-processor-is-i5-10th-gen-10210u/1193493?noredirect=1#comment2038709_1193493](https://askubuntu.com/questions/1192531/wifi-adapter-not-found-for-dell-inspiron-5590-processor-is-i5-10th-gen-10210u/1193493?noredirect=1#comment2038709_1193493)

---

### Post by animalbrain on 2020-02-28
chili555, thank you very much. I used advanced boot options to select kernel 5.3.0-29-generic (5.3.0-28 wasn't an option for me), and wireless is working again!

---

### Post by chili555 on 2020-02-28
> **animalbrain said:**
> chili555, thank you very much. I used advanced boot options to select kernel 5.3.0-29-generic (5.3.0-28 wasn't an option for me), and wireless is working again!Please add to the bug report I linked in my reply. 

Glad it's working.

---

