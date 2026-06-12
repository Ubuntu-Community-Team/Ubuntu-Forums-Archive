---
title: "Intel ax200 no wifi"
date: 2021-09-28
forum: Networking &amp; Wireless
---

### Post by dennnic on 2021-09-28
Hello, I need some help enabling wifi.

Just added Gigabye network adapter with intel ax200, current status:

Network:
  Device-1: Intel Wi-Fi 6 AX200 driver: iwlwifi v: kernel port: f040 
  bus ID: 01:00.0 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Micro-Star MSI driver: r8169 v: kernel port: e000 bus ID: 03:00.0 
  IF: enp3s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 


For some reason, there is no WiFi settings or any hint that its in there. Bluetooth works fine tho.

So far I tried:

-Upgraded to Ubuntu 21.04
-Upgraded to kernel 5.11
-Backports update
-Checked for firmware in libs (its there)
-Disabling fast boot
-Hitting it (gently, its still new)

According to the info I found, kernel 5.11 should support Ax200. Any clue what to do?

Thanks!

---

### Post by dennnic on 2021-09-28
one additional info if it matters:

[   10.310589] iwlwifi 0000:01:00.0: Failed to run INIT ucode: -110

---

### Post by T6&amp;sfpER35% on 2021-09-28
maybe [this](https://community.intel.com/t5/Wireless/AX200-unable-to-detect-WiFi-Network/m-p/1225944) will help ?

---

### Post by dennnic on 2021-09-29
No luck.

This is what lshw shows:

  *-network                 
       description: Network controller
       product: Wi-Fi 6 AX200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 1a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: driver=iwlwifi latency=0
       resources: irq:16 memory:f7e00000-f7e03fff

as if everything is installed already

---

### Post by T6&amp;sfpER35% on 2021-09-29
are you on a laptop?
this is a long shot ...
recently i sold a laptop of mine , afterwards the woman phones me complaining she can't get the wifi to work.
turns out she didn't enable the wifi with the physical switch/key. 
most laptops have a actual switch or key combo to enable/disable wifi. 
as i'm saying ,just reaching here lol

---

### Post by dennnic on 2021-09-29
No, its a desktop pc. 
I've reinstalled ubuntu 20.04, tried backports again, enabled secureboot, than disable it and still no wifi to be found.
Kernel 5.11

---

### Post by T6&amp;sfpER35% on 2021-09-29
try ```
sudo apt upgrade
```
and then ```
sudo apt-get update -y
```

---

### Post by dennnic on 2021-09-29
No change

---

### Post by T6&amp;sfpER35% on 2021-09-29
output of ?```
inxi -Fxzd
```

---

### Post by dennnic on 2021-09-29
Network:
  Device-1: Intel Wi-Fi 6 AX200 driver: iwlwifi v: kernel port: f040 
  bus ID: 01:00.0 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Micro-Star MSI driver: r8169 v: kernel port: e000 bus ID: 03:00.0 
  IF: enp3s0 state: up speed: 1000 Mbps duplex: full mac: <filter>

---

### Post by T6&amp;sfpER35% on 2021-09-29
do you have Ethernet cable connected?

---

### Post by dennnic on 2021-09-29
Yes, but it makes little difference whether it is plugged in, or not

---

### Post by T6&amp;sfpER35% on 2021-09-30
apart from pulling out the ethernet cable and then rebooting to see if the wifi picks up , i'm out of ideas .
from what I've read ,cabled connection and wifi together doesn't gel together so nice. system will always choose cable over wifi.

---

### Post by chili555 on 2021-09-30
We need to see *all* of:

```
sudo dmesg | grep iwl
```

---

### Post by dennnic on 2021-10-03
Here it comes:

[    3.165655] iwlwifi 0000:01:00.0: enabling device (0000 -> 0002)
[    3.186397] iwlwifi 0000:01:00.0: api flags index 2 larger than supported by driver
[    3.186407] iwlwifi 0000:01:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 89.3.35.22
[    3.186607] iwlwifi 0000:01:00.0: loaded firmware version 59.601f3a66.0 cc-a0-59.ucode op_mode iwlmvm
[    3.239469] iwlwifi 0000:01:00.0: Detected Intel(R) Wi-Fi 6 AX200 160MHz, REV=0x340
[    4.279697] iwlwifi 0000:01:00.0: SecBoot CPU1 Status: 0x5596, CPU2 Status: 0x3
[    4.279716] iwlwifi 0000:01:00.0: UMAC PC: 0x804766c0
[    4.279728] iwlwifi 0000:01:00.0: LMAC PC: 0xd0
[    4.279733] iwlwifi 0000:01:00.0: WRT: Collecting data: ini trigger 13 fired.
[    4.279811] iwlwifi 0000:01:00.0: Start IWL Error Log Dump:
[    4.279814] iwlwifi 0000:01:00.0: Status: 0x00000000, count: 6
[    4.279819] iwlwifi 0000:01:00.0: Loaded firmware version: 59.601f3a66.0 cc-a0-59.ucode
[    4.279823] iwlwifi 0000:01:00.0: 0x00000071 | NMI_INTERRUPT_UMAC_FATAL    
[    4.279828] iwlwifi 0000:01:00.0: 0x002022F0 | trm_hw_status0
[    4.279831] iwlwifi 0000:01:00.0: 0x00000000 | trm_hw_status1
[    4.279835] iwlwifi 0000:01:00.0: 0x004FAA36 | branchlink2
[    4.279838] iwlwifi 0000:01:00.0: 0x004F0E12 | interruptlink1
[    4.279841] iwlwifi 0000:01:00.0: 0x004F0E12 | interruptlink2
[    4.279844] iwlwifi 0000:01:00.0: 0x004F3D2A | data1
[    4.279848] iwlwifi 0000:01:00.0: 0x00001000 | data2
[    4.279851] iwlwifi 0000:01:00.0: 0x00000000 | data3
[    4.279854] iwlwifi 0000:01:00.0: 0x00000000 | beacon time
[    4.279858] iwlwifi 0000:01:00.0: 0x0000E538 | tsf low
[    4.279861] iwlwifi 0000:01:00.0: 0x00000000 | tsf hi
[    4.279864] iwlwifi 0000:01:00.0: 0x00000000 | time gp1
[    4.279868] iwlwifi 0000:01:00.0: 0x00013BC1 | time gp2
[    4.279871] iwlwifi 0000:01:00.0: 0x00000001 | uCode revision type
[    4.279874] iwlwifi 0000:01:00.0: 0x0000003B | uCode version major
[    4.279878] iwlwifi 0000:01:00.0: 0x601F3A66 | uCode version minor
[    4.279881] iwlwifi 0000:01:00.0: 0x00000340 | hw version
[    4.279885] iwlwifi 0000:01:00.0: 0x18C89000 | board version
[    4.279888] iwlwifi 0000:01:00.0: 0x8001FF03 | hcmd
[    4.279891] iwlwifi 0000:01:00.0: 0x00020000 | isr0
[    4.279895] iwlwifi 0000:01:00.0: 0x00000000 | isr1
[    4.279898] iwlwifi 0000:01:00.0: 0x08F00002 | isr2
[    4.279901] iwlwifi 0000:01:00.0: 0x00C0000C | isr3
[    4.279904] iwlwifi 0000:01:00.0: 0x00000000 | isr4
[    4.279907] iwlwifi 0000:01:00.0: 0x00000000 | last cmd Id
[    4.279911] iwlwifi 0000:01:00.0: 0x004F3D2A | wait_event
[    4.279914] iwlwifi 0000:01:00.0: 0x00000000 | l2p_control
[    4.279917] iwlwifi 0000:01:00.0: 0x00000020 | l2p_duration
[    4.279920] iwlwifi 0000:01:00.0: 0x00000000 | l2p_mhvalid
[    4.279923] iwlwifi 0000:01:00.0: 0x00000000 | l2p_addr_match
[    4.279927] iwlwifi 0000:01:00.0: 0x00000009 | lmpm_pmg_sel
[    4.279930] iwlwifi 0000:01:00.0: 0x00000000 | timestamp
[    4.279933] iwlwifi 0000:01:00.0: 0x0000F81C | flow_handler
[    4.279961] iwlwifi 0000:01:00.0: Start IWL Error Log Dump:
[    4.279964] iwlwifi 0000:01:00.0: Status: 0x00000000, count: 7
[    4.279968] iwlwifi 0000:01:00.0: 0x20100222 | ADVANCED_SYSASSERT
[    4.279972] iwlwifi 0000:01:00.0: 0x00000000 | umac branchlink1
[    4.279975] iwlwifi 0000:01:00.0: 0x804568FC | umac branchlink2
[    4.279979] iwlwifi 0000:01:00.0: 0xC0085328 | umac interruptlink1
[    4.279982] iwlwifi 0000:01:00.0: 0x00000000 | umac interruptlink2
[    4.279985] iwlwifi 0000:01:00.0: 0xDEADBEEF | umac data1
[    4.279988] iwlwifi 0000:01:00.0: 0xDEADBEEF | umac data2
[    4.279991] iwlwifi 0000:01:00.0: 0xDEADBEEF | umac data3
[    4.279995] iwlwifi 0000:01:00.0: 0x0000003B | umac major
[    4.279998] iwlwifi 0000:01:00.0: 0x601F3A66 | umac minor
[    4.280001] iwlwifi 0000:01:00.0: 0x00013BBB | frame pointer
[    4.280004] iwlwifi 0000:01:00.0: 0xC0886AD4 | stack pointer
[    4.280008] iwlwifi 0000:01:00.0: 0x00000000 | last host cmd
[    4.280011] iwlwifi 0000:01:00.0: 0x00000000 | isr status reg
[    4.280018] iwlwifi 0000:01:00.0: Fseq Registers:
[    4.280023] iwlwifi 0000:01:00.0: 0x60000000 | FSEQ_ERROR_CODE
[    4.280029] iwlwifi 0000:01:00.0: 0x80290021 | FSEQ_TOP_INIT_VERSION
[    4.280034] iwlwifi 0000:01:00.0: 0x00050008 | FSEQ_CNVIO_INIT_VERSION
[    4.280040] iwlwifi 0000:01:00.0: 0x0000A503 | FSEQ_OTP_VERSION
[    4.280045] iwlwifi 0000:01:00.0: 0x80000003 | FSEQ_TOP_CONTENT_VERSION
[    4.280050] iwlwifi 0000:01:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN
[    4.280056] iwlwifi 0000:01:00.0: 0x00100530 | FSEQ_CNVI_ID
[    4.280061] iwlwifi 0000:01:00.0: 0x00000532 | FSEQ_CNVR_ID
[    4.280066] iwlwifi 0000:01:00.0: 0x00100530 | CNVI_AUX_MISC_CHIP
[    4.280074] iwlwifi 0000:01:00.0: 0x00000532 | CNVR_AUX_MISC_CHIP
[    4.280081] iwlwifi 0000:01:00.0: 0x05B0905B | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    4.280089] iwlwifi 0000:01:00.0: 0x0000025B | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    4.280095] iwlwifi 0000:01:00.0: Failed to start RT ucode: -110
[    4.645333] iwlwifi 0000:01:00.0: Failed to run INIT ucode: -110

---

### Post by chili555 on 2021-10-03
> [ 4.280095] iwlwifi 0000:01:00.0: Failed to start RT ucode: -110
[ 4.645333] iwlwifi 0000:01:00.0: Failed to run INIT ucode: -110These are often signs of Fast Boot interfering with initialization of the wireless card. I know you said that you disabled Fast Boot, but please check again.

---

