---
title: "Problem loading network driver for older Intel server board (Ubunutu 14.04)"
date: 2018-03-29
forum: Networking &amp; Wireless
---

### Post by arcimedez on 2018-03-29
[COLOR=#111111][FONT=Ubuntu]Created an account specifically looking for help with this problem. I've used linux before but am basically completely new to it (at least dealing with issues). So I recently got an older intel server board (s5520hc) and am having a heck of a time getting a driver loaded for the NICs. After initial problems I found the most recent version of the driver(igb) and discovered that it only supports up to 3.X kernels. I thought my problems would be solved when I downloaded an ISO of 14.04 with a 3.X kernel (defaults to 4.4 now apparently) but it still doesn't seem to be working. 


When I run `make install` in the src folder it seems to go fine but `ifconfig` only shows lo.


When I run `lshw -C network` I there are two things labeled network0 and network1, but they show up as unclaimed.


Running `dmesg | grep -e igb -eth` these are the errors I get.


    ```
[    0.684796] ACPI Error: Method parse/execution failed [\_SB_._OSC] (Node ffff88183f0082f8), AE_AML_BUFFER_LIMIT (20141107/psparse-536) 
[  141.944706] igb: module verification failed: signature and/or  required key missing - tainting kernel
```


This is pretty much where I'm stuck and googling has run out for me. I actually encountered this same error when I was running Ubunutu 16.04 with the 4.4 kernel so I'm a bit confused. I thought switching to a 3.X kernel would solve my problem, but it has not. 


Any help here would be much appreciated. I started this build off of this board I got super cheap on ebay, but this networking issue is starting to be a bit much. I had hoped to run 16.04, but now I just want to get something working.


Let me know if I can provide more info. 

[/FONT][/COLOR]

---

### Post by praseodym on 2018-03-30
Is it an UEFI? If yes, deactivate SecureBoot

---

### Post by arcimedez on 2018-03-30
I think just BIOS, not completely sure on the difference, but I dont see anything about secure boot in the BIOS section of the boards manual. 

Late last night I checked what lspci showed me and im a bit concerned. For the NICs it showed something like "ehternet controller Intel corporation device 10aa (Rev2)"

A quick google makes me think that something is wrong with the EEPROM. Is that an accurate analysis? Can it be fixed or does it mean the board is busted?

Thanks

---

### Post by praseodym on 2018-03-30
BIOS update available?

---

### Post by chili555 on 2018-03-30
>  For the NICs it showed something like "ehternet controller Intel corporation device 10aa (Rev2)"

A quick google makes me think that something is wrong with the EEPROM. Is that an accurate analysis? Can it be fixed or does it mean the board is busted?
We need more details:```
lspci -nnk | grep 0200 -A3
```What makes you suspect the EEPROM?

---

### Post by arcimedez on 2018-03-30
The BIOS should be intels most recent for that board.

The results of ```
[COLOR=#000000][FONT=&amp]lspci -nnk | grep 0200 -A3[/FONT][/COLOR]
```
are
```
01:00.0 Ethernet controller [0200]: Intel Corporation Device [8086:10aa] (rev 02)    Subsystem: Intel Corporation Device [8086:0000]
01:00.1 Ethernet controller [0200]: Intel Corporation Device [8086:10aa] (rev 02)
    Subsystem: Intel Corporation Device [8086:0000]
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280] [1002:679a]
    Subsystem: PC Partner Limited / Sapphire Technology Device [174b:3000]

```
....dont mind the graphiscs card...it was in an older system

Was going off these two threads that lead me to EEPROM, but I don't fully understand all thats concerned with this 
[https://sourceforge.net/p/e1000/mailman/message/27622531/](https://sourceforge.net/p/e1000/mailman/message/27622531/)
[https://sourceforge.net/p/e1000/mailman/message/27627531/](https://sourceforge.net/p/e1000/mailman/message/27627531/)


Thanks so much for the help btw :)

---

### Post by chili555 on 2018-03-30
May we also see:```
dmesg | grep -e igb -e 00.1
sudo modprobe igb
```Thanks.

---

### Post by arcimedez on 2018-04-01
Sorry was away for the weekend.

The grep grabbed a lot but here's the result. Also sudo modprobe igb returns nothing. igb does show up when I run lsmod though. Thanks.

```
 0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000008c49ffff] usable[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000186fffffff] usable
[    0.000000] ACPI: XSDT 0x000000008F7FD120 000094 (v01 INTEL  S5520HC  00000000      01000013)
[    0.000000] ACPI: APIC 0x000000008F7F3000 0001A8 (v02 INTEL  S5520HC  00000000 MSFT 0100000D)
[    0.000000] ACPI: MCFG 0x000000008F7F2000 00003C (v01 INTEL  S5520HC  00000001 MSFT 0100000D)
[    0.000000] ACPI: HPET 0x000000008F7F1000 000038 (v01 INTEL  S5520HC  00000001 MSFT 0100000D)
[    0.000000] ACPI: SLIT 0x000000008F7F0000 000030 (v01 INTEL  S5520HC  00000001 MSFT 0100000D)
[    0.000000] ACPI: SRAT 0x000000008F7EF000 000430 (v02 INTEL  S5520HC  00000001 MSFT 0100000D)
[    0.000000] ACPI: SSDT 0x000000008F7D2000 01AFC4 (v02 INTEL  SSDT  PM 00004000 INTL 20061109)
[    0.000000] ACPI: SSDT 0x000000008F7D1000 0001D8 (v02 INTEL  IPMI     00004000 INTL 20061109)
[    0.000000] ACPI: HEST 0x000000008F7D0000 0000A8 (v01 INTEL  S5520HC  00000001 INTL 00000001)
[    0.000000] ACPI: BERT 0x000000008F7CF000 000030 (v01 INTEL  S5520HC  00000001 INTL 00000001)
[    0.000000] ACPI: ERST 0x000000008F6F0000 000230 (v01 INTEL  S5520HC  00000001 INTL 00000001)
[    0.000000] ACPI: EINJ 0x000000008F6EF000 000130 (v01 INTEL  S5520HC  00000001 INTL 00000001)
[    0.000000]  [ffffea0000000000-ffffea0031bfffff] PMD -> [ffff880c3fe00000-ffff880c6fdfffff] on node 0
[    0.000000]  [ffffea0031c00000-ffffea0061bfffff] PMD -> [ffff88183f600000-ffff88186f5fffff] on node 1
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   node   0: [mem 0x00001000-0x00098fff]
[    0.000000] Initmem setup node 0 [mem 0x00001000-0xc6fffffff]
[    0.000031] pid_max: default: 32768 minimum: 301
[    0.060011] Mount-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.700711] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
[    0.700919] pci 0000:00:03.0: [8086:340a] type 01 class 0x060400
[    0.701444] pci 0000:00:10.0: [8086:3425] type 00 class 0x080000
[    0.701541] pci 0000:00:10.1: [8086:3426] type 00 class 0x080000
[    0.701631] pci 0000:00:11.0: [8086:3427] type 00 class 0x080000
[    0.701727] pci 0000:00:11.1: [8086:3428] type 00 class 0x080000
[    0.701818] pci 0000:00:13.0: [8086:342d] type 00 class 0x080020
[    0.701827] pci 0000:00:13.0: reg 0x10: [mem 0xc1c24000-0xc1c24fff]
[    0.701868] pci 0000:00:13.0: PME# supported from D0 D3hot D3cold
[    0.701937] pci 0000:00:14.0: [8086:342e] type 00 class 0x080000
[    0.702037] pci 0000:00:14.1: [8086:3422] type 00 class 0x080000
[    0.702139] pci 0000:00:14.2: [8086:3423] type 00 class 0x080000
[    0.702236] pci 0000:00:14.3: [8086:3438] type 00 class 0x080000
[    0.702322] pci 0000:00:15.0: [8086:342f] type 00 class 0x080020
[    0.702413] pci 0000:00:16.0: [8086:3430] type 00 class 0x088000
[    0.702425] pci 0000:00:16.0: reg 0x10: [mem 0xc1c00000-0xc1c03fff 64bit]
[    0.702540] pci 0000:00:16.1: [8086:3431] type 00 class 0x088000
[    0.702551] pci 0000:00:16.1: reg 0x10: [mem 0xc1c04000-0xc1c07fff 64bit]
[    0.702660] pci 0000:00:16.2: [8086:3432] type 00 class 0x088000
[    0.702672] pci 0000:00:16.2: reg 0x10: [mem 0xc1c08000-0xc1c0bfff 64bit]
[    0.702782] pci 0000:00:16.3: [8086:3433] type 00 class 0x088000
[    0.702793] pci 0000:00:16.3: reg 0x10: [mem 0xc1c0c000-0xc1c0ffff 64bit]
[    0.702902] pci 0000:00:16.4: [8086:3429] type 00 class 0x088000
[    0.702913] pci 0000:00:16.4: reg 0x10: [mem 0xc1c10000-0xc1c13fff 64bit]
[    0.703022] pci 0000:00:16.5: [8086:342a] type 00 class 0x088000
[    0.703033] pci 0000:00:16.5: reg 0x10: [mem 0xc1c14000-0xc1c17fff 64bit]
[    0.703142] pci 0000:00:16.6: [8086:342b] type 00 class 0x088000
[    0.703153] pci 0000:00:16.6: reg 0x10: [mem 0xc1c18000-0xc1c1bfff 64bit]
[    0.703264] pci 0000:00:16.7: [8086:342c] type 00 class 0x088000
[    0.703275] pci 0000:00:16.7: reg 0x10: [mem 0xc1c1c000-0xc1c1ffff 64bit]
[    0.703387] pci 0000:00:1a.0: [8086:3a37] type 00 class 0x0c0300
[    0.703424] pci 0000:00:1a.0: reg 0x20: [io  0x40e0-0x40ff]
[    0.703510] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.703545] pci 0000:00:1a.1: [8086:3a38] type 00 class 0x0c0300
[    0.703582] pci 0000:00:1a.1: reg 0x20: [io  0x40c0-0x40df]
[    0.703665] pci 0000:00:1a.1: System wakeup disabled by ACPI
[    0.703700] pci 0000:00:1a.2: [8086:3a39] type 00 class 0x0c0300
[    0.703737] pci 0000:00:1a.2: reg 0x20: [io  0x40a0-0x40bf]
[    0.703819] pci 0000:00:1a.2: System wakeup disabled by ACPI
[    0.703864] pci 0000:00:1a.7: [8086:3a3c] type 00 class 0x0c0320
[    0.703883] pci 0000:00:1a.7: reg 0x10: [mem 0xc1c22000-0xc1c223ff]
[    0.703965] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.704022] pci 0000:00:1a.7: System wakeup disabled by ACPI
[    0.704058] pci 0000:00:1c.0: [8086:3a40] type 01 class 0x060400
[    0.704127] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.704172] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.704208] pci 0000:00:1c.4: [8086:3a48] type 01 class 0x060400
[    0.704276] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.704321] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.704360] pci 0000:00:1d.0: [8086:3a34] type 00 class 0x0c0300
[    0.704397] pci 0000:00:1d.0: reg 0x20: [io  0x4080-0x409f]
[    0.704481] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.704516] pci 0000:00:1d.1: [8086:3a35] type 00 class 0x0c0300
[    0.704553] pci 0000:00:1d.1: reg 0x20: [io  0x4060-0x407f]
[    0.704637] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.704671] pci 0000:00:1d.2: [8086:3a36] type 00 class 0x0c0300
[    0.704708] pci 0000:00:1d.2: reg 0x20: [io  0x4040-0x405f]
[    0.704794] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.704837] pci 0000:00:1d.7: [8086:3a3a] type 00 class 0x0c0320
[    0.704856] pci 0000:00:1d.7: reg 0x10: [mem 0xc1c21000-0xc1c213ff]
[    0.704938] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.704996] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.705030] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.705110] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.705147] pci 0000:00:1f.0: [8086:3a16] type 00 class 0x060100
[    0.705218] pci 0000:00:1f.0: can't claim BAR 13 [io  0x0400-0x047f]: address conflict with ACPI PM1a_EVT_BLK [io  0x0400-0x0403]
[    0.705223] pci 0000:00:1f.0: quirk: [io  0x0500-0x053f] claimed by ICH6 GPIO
[    0.705226] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 000f)
[    0.705228] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0ca0 (mask 000f)
[    0.705231] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0600 (mask 001f)
[    0.705326] pci 0000:00:1f.2: [8086:3a22] type 00 class 0x010601
[    0.705343] pci 0000:00:1f.2: reg 0x10: [io  0x4108-0x410f]
[    0.705350] pci 0000:00:1f.2: reg 0x14: [io  0x4114-0x4117]
[    0.705357] pci 0000:00:1f.2: reg 0x18: [io  0x4100-0x4107]
[    0.705363] pci 0000:00:1f.2: reg 0x1c: [io  0x4110-0x4113]
[    0.705370] pci 0000:00:1f.2: reg 0x20: [io  0x4020-0x403f]
[    0.705376] pci 0000:00:1f.2: reg 0x24: [mem 0xc1c20000-0xc1c207ff]
[    0.705418] pci 0000:00:1f.2: PME# supported from D3hot
[    0.705491] pci 0000:00:1f.3: [8086:3a30] type 00 class 0x0c0500
[    0.705505] pci 0000:00:1f.3: reg 0x10: [mem 0xc1c23000-0xc1c230ff 64bit]
[    0.705522] pci 0000:00:1f.3: reg 0x20: [io  0x4000-0x401f]
[    0.705821] pci 0000:01:00.1: [8086:10aa] type 00 class 0x020000
[    0.705834] pci 0000:01:00.1: reg 0x10: [mem 0xc1b00000-0xc1b1ffff]
[    0.705848] pci 0000:01:00.1: reg 0x18: [io  0x3000-0x301f]
[    0.705856] pci 0000:01:00.1: reg 0x1c: [mem 0xc1b40000-0xc1b43fff]
[    0.705920] pci 0000:01:00.1: PME# supported from D0 D3hot D3cold
[    0.705943] pci 0000:01:00.1: System wakeup disabled by ACPI
[    0.712016] pci 0000:02:00.1: [1002:aaa0] type 00 class 0x040300
[    0.712028] pci 0000:02:00.1: reg 0x10: [mem 0xc1a40000-0xc1a43fff 64bit]
[    0.712088] pci 0000:02:00.1: supports D1 D2
[    0.722447] pci 0000:00:1c.0: PCI bridge to [bus 06]
[    0.722452] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.722457] pci 0000:00:1c.0:   bridge window [mem 0xc1900000-0xc19fffff]
[    0.722525] pci 0000:00:1c.4: PCI bridge to [bus 07]
[    0.722530] pci 0000:00:1c.4:   bridge window [mem 0xc1000000-0xc18fffff]
[    0.722534] pci 0000:00:1c.4:   bridge window [mem 0xc0000000-0xc0ffffff 64bit pref]
[    0.722644] pci 0000:00:1e.0: PCI bridge to [bus 08] (subtractive decode)
[    0.722652] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.722653] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.722655] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.722656] pci 0000:00:1e.0:   bridge window [mem 0x000c4000-0x000cbfff] (subtractive decode)
[    0.722658] pci 0000:00:1e.0:   bridge window [mem 0xfed40000-0xfedfffff] (subtractive decode)
[    0.722659] pci 0000:00:1e.0:   bridge window [mem 0xb0000000-0xfdffffff] (subtractive decode)
[    0.729415] pci 0000:fe:00.1: [8086:2d81] type 00 class 0x060000
[    0.730349] pci 0000:ff:00.1: [8086:2d81] type 00 class 0x060000
[    0.739553] system 00:01: [mem 0xfe900000-0xfe90001f] has been reserved
[    0.739554] system 00:01: [mem 0xfea00000-0xfea0001f] has been reserved
[    0.739872] pnp 00:04: Plug and Play ACPI device, IDs IPI0001 (active)
[    0.746875] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 06] add_size 200000
[    0.746881] pci 0000:00:1c.4: bridge window [io  0x1000-0x0fff] to [bus 07] add_size 1000
[    0.746896] pci 0000:00:1f.0: BAR 13: [io  0x0400-0x047f] has bogus alignment
[    0.746898] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.746900] pci 0000:00:1c.4: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.746906] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc1d00000-0xc1efffff 64bit pref]
[    0.746908] pci 0000:00:1c.4: BAR 13: assigned [io  0x5000-0x5fff]
[    0.746958] pci 0000:00:1c.0: PCI bridge to [bus 06]
[    0.746960] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.746964] pci 0000:00:1c.0:   bridge window [mem 0xc1900000-0xc19fffff]
[    0.746967] pci 0000:00:1c.0:   bridge window [mem 0xc1d00000-0xc1efffff 64bit pref]
[    0.746971] pci 0000:00:1c.4: PCI bridge to [bus 07]
[    0.746973] pci 0000:00:1c.4:   bridge window [io  0x5000-0x5fff]
[    0.746977] pci 0000:00:1c.4:   bridge window [mem 0xc1000000-0xc18fffff]
[    0.746980] pci 0000:00:1c.4:   bridge window [mem 0xc0000000-0xc0ffffff 64bit pref]
[    0.746984] pci 0000:00:1e.0: PCI bridge to [bus 08]
[    1.033129] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    1.033142] pci 0000:02:00.1: Signaling PME through PCIe PME interrupt
[    1.033191] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    1.033196] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    1.033209] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
[    1.033212] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
[    1.033254] pciehp 0000:00:1c.0:pcie04: Slot #1 AttnBtn- AttnInd- PwrInd- PwrCtrl- MRL- Interlock- NoCompl- LLActRep+
[    1.033312] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
[    1.033320] pciehp 0000:00:1c.4:pcie04: Slot #5 AttnBtn- AttnInd- PwrInd- PwrCtrl- MRL- Interlock- NoCompl- LLActRep+
[    1.033371] pciehp 0000:00:1c.4:pcie04: service driver pciehp loaded
[    1.107333] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    1.107340] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.107352] ehci-pci 0000:00:1a.7: debug port 1
[    1.111255] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    1.111269] ehci-pci 0000:00:1a.7: irq 19, io mem 0xc1c22000
[    1.121428] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.121470] usb usb1: SerialNumber: 0000:00:1a.7
[    1.121803] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.121808] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.121819] ehci-pci 0000:00:1d.7: debug port 1
[    1.125715] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    1.125726] ehci-pci 0000:00:1d.7: irq 16, io mem 0xc1c21000
[    1.137423] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.137458] usb usb2: SerialNumber: 0000:00:1d.7
[    1.137809] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.137813] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.137819] uhci_hcd 0000:00:1a.0: detected 2 ports
[    1.137838] uhci_hcd 0000:00:1a.0: irq 19, io base 0x000040e0
[    1.137876] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.137881] usb usb3: SerialNumber: 0000:00:1a.0
[    1.138194] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.138199] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.138204] uhci_hcd 0000:00:1a.1: detected 2 ports
[    1.138221] uhci_hcd 0000:00:1a.1: irq 19, io base 0x000040c0
[    1.138257] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.138263] usb usb4: SerialNumber: 0000:00:1a.1
[    1.138569] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.138574] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.138579] uhci_hcd 0000:00:1a.2: detected 2 ports
[    1.138596] uhci_hcd 0000:00:1a.2: irq 19, io base 0x000040a0
[    1.138632] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.138638] usb usb5: SerialNumber: 0000:00:1a.2
[    1.138945] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.138950] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.138955] uhci_hcd 0000:00:1d.0: detected 2 ports
[    1.138972] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00004080
[    1.139007] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.139013] usb usb6: SerialNumber: 0000:00:1d.0
[    1.139323] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.139329] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.139334] uhci_hcd 0000:00:1d.1: detected 2 ports
[    1.139351] uhci_hcd 0000:00:1d.1: irq 16, io base 0x00004060
[    1.139386] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.139392] usb usb7: SerialNumber: 0000:00:1d.1
[    1.139696] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.139701] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.139708] uhci_hcd 0000:00:1d.2: detected 2 ports
[    1.139724] uhci_hcd 0000:00:1d.2: irq 16, io base 0x00004040
[    1.139759] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    1.139765] usb usb8: SerialNumber: 0000:00:1d.2
[    2.193226] Freeing unused kernel memory: 260K (ffff8800017bf000 - ffff880001800000)
[    2.195770] Freeing unused kernel memory: 344K (ffff880001baa000 - ffff880001c00000)
[    2.280396] ahci 0000:00:1f.2: version 3.0
[    2.280647] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    2.280651] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    2.301693] input: American Megatrends Inc. Virtual Keyboard and Mouse as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/0003:046B:FF10.0001/input/input2
[    2.357379] hid-generic 0003:046B:FF10.0001: input,hidraw0: USB HID v1.10 Keyboard [American Megatrends Inc. Virtual Keyboard and Mouse] on usb-0000:00:1a.2-1/input0
[    2.357518] input: American Megatrends Inc. Virtual Keyboard and Mouse as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.1/0003:046B:FF10.0002/input/input3
[    2.357877] hid-generic 0003:046B:FF10.0002: input,hidraw1: USB HID v1.10 Mouse [American Megatrends Inc. Virtual Keyboard and Mouse] on usb-0000:00:1a.2-1/input1
[    2.460594] logitech-djreceiver 0003:046D:C52B.0005: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.2-1/input2
[    3.598336] snd_hda_intel 0000:02:00.1: Handle VGA-switcheroo audio client
[    3.598342] snd_hda_intel 0000:02:00.1: Force to non-snoop mode
[    3.598762] checking generic (b0000000 7f0000) vs hw (b0000000 10000000)
[    3.604892] input: Logitech Wireless Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.2/0003:046D:C52B.0005/0003:046D:4055.0006/input/input6
[    3.605019] logitech-hidpp-device 0003:046D:4055.0006: input,hidraw3: USB HID v1.11 Mouse [Logitech Wireless Mouse] on usb-0000:00:1d.2-1:1
[    3.605304] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/0000:02:00.1/sound/card0/input4
[    3.605380] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/0000:02:00.1/sound/card0/input5
[    3.605538] input: HDA ATI HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/0000:02:00.1/sound/card0/input7
[    3.605765] input: HDA ATI HDMI HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:03.0/0000:02:00.1/sound/card0/input8
[    3.606022] input: HDA ATI HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:03.0/0000:02:00.1/sound/card0/input9
[    3.606244] input: HDA ATI HDMI HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:03.0/0000:02:00.1/sound/card0/input10
[    3.610973] input: Logitech K520 as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.2/0003:046D:C52B.0005/0003:046D:2011.0007/input/input11
[    3.611052] logitech-hidpp-device 0003:046D:2011.0007: input,hidraw4: USB HID v1.11 Keyboard [Logitech K520] on usb-0000:00:1d.2-1:2
[    3.670061] radeon 0000:02:00.0: fence driver on ring 1 use gpu addr 0x00000000c0000c04 and cpu addr 0xffff88182e2bac04
[    3.670067] radeon 0000:02:00.0: fence driver on ring 4 use gpu addr 0x00000000c0000c10 and cpu addr 0xffff88182e2bac10
[    3.712794] ipmi_si 00:04: Found new BMC (man_id: 0x000157, prod_id: 0x003e, dev_id: 0x21)
[    4.008171] [drm] ring test on 5 succeeded in 1 usecs
[    4.008178] [drm] UVD initialized successfully.
```

---

### Post by chili555 on 2018-04-02
There is not much useful there. Let's try something else:```
modinfo igb | grep 10AA
sudo modprobe igb && dmesg | grep igb
```

---

### Post by arcimedez on 2018-04-02
The grep of modifno didn't grab anything so I'm including the whole thing in case that is helpful
```
filename:       /lib/modules/3.19.0-25-generic/updates/drivers/net/ethernet/intel/igb/igb.koversion:        5.3.5.15
license:        GPL
description:    Intel(R) Gigabit Ethernet Linux Driver
author:         Intel Corporation, <e1000-devel@lists.sourceforge.net>
srcversion:     CEE05A9F418B18AF30EF443
alias:          pci:v00008086d000010D6sv*sd*bc*sc*i*
alias:          pci:v00008086d000010A9sv*sd*bc*sc*i*
alias:          pci:v00008086d000010A7sv*sd*bc*sc*i*
alias:          pci:v00008086d000010E8sv*sd*bc*sc*i*
alias:          pci:v00008086d00001526sv*sd*bc*sc*i*
alias:          pci:v00008086d0000150Dsv*sd*bc*sc*i*
alias:          pci:v00008086d000010E7sv*sd*bc*sc*i*
alias:          pci:v00008086d000010E6sv*sd*bc*sc*i*
alias:          pci:v00008086d00001518sv*sd*bc*sc*i*
alias:          pci:v00008086d0000150Asv*sd*bc*sc*i*
alias:          pci:v00008086d000010C9sv*sd*bc*sc*i*
alias:          pci:v00008086d00000440sv*sd*bc*sc*i*
alias:          pci:v00008086d0000043Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000043Asv*sd*bc*sc*i*
alias:          pci:v00008086d00000438sv*sd*bc*sc*i*
alias:          pci:v00008086d00001516sv*sd*bc*sc*i*
alias:          pci:v00008086d00001511sv*sd*bc*sc*i*
alias:          pci:v00008086d00001510sv*sd*bc*sc*i*
alias:          pci:v00008086d00001527sv*sd*bc*sc*i*
alias:          pci:v00008086d0000150Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000150Esv*sd*bc*sc*i*
alias:          pci:v00008086d00001524sv*sd*bc*sc*i*
alias:          pci:v00008086d00001523sv*sd*bc*sc*i*
alias:          pci:v00008086d00001522sv*sd*bc*sc*i*
alias:          pci:v00008086d00001521sv*sd*bc*sc*i*
alias:          pci:v00008086d00001539sv*sd*bc*sc*i*
alias:          pci:v00008086d0000157Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000157Bsv*sd*bc*sc*i*
alias:          pci:v00008086d00001538sv*sd*bc*sc*i*
alias:          pci:v00008086d00001537sv*sd*bc*sc*i*
alias:          pci:v00008086d00001536sv*sd*bc*sc*i*
alias:          pci:v00008086d00001533sv*sd*bc*sc*i*
alias:          pci:v00008086d00001F45sv*sd*bc*sc*i*
alias:          pci:v00008086d00001F41sv*sd*bc*sc*i*
alias:          pci:v00008086d00001F40sv*sd*bc*sc*i*
depends:        ptp,dca
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
parm:           InterruptThrottleRate:Maximum interrupts per second, per vector, (max 100000), default 3=adaptive (array of int)
parm:           IntMode:Change Interrupt Mode (0=Legacy, 1=MSI, 2=MSI-X), default 2 (array of int)
parm:           Node:set the starting node to allocate memory on, default -1 (array of int)
parm:           LLIPort:Low Latency Interrupt TCP Port (0-65535), default 0=off (array of int)
parm:           LLIPush:Low Latency Interrupt on TCP Push flag (0,1), default 0=off (array of int)
parm:           LLISize:Low Latency Interrupt on Packet Size (0-1500), default 0=off (array of int)
parm:           RSS:Number of Receive-Side Scaling Descriptor Queues (0-8), default 1, 0=number of cpus (array of int)
parm:           VMDQ:Number of Virtual Machine Device Queues: 0-1 = disable, 2-8 enable, default 0 (array of int)
parm:           max_vfs:Number of Virtual Functions: 0 = disable, 1-7 enable, default 0 (array of int)
parm:           MDD:Malicious Driver Detection (0/1), default 1 = enabled. Only available when max_vfs is greater than 0 (array of int)
parm:           QueuePairs:Enable Tx/Rx queue pairs for interrupt handling (0,1), default 1=on (array of int)
parm:           EEE:Enable/disable on parts that support the feature (array of int)
parm:           DMAC:Disable or set latency for DMA Coalescing ((0=off, 1000-10000(msec), 250, 500 (usec)) (array of int)
parm:           LRO:Large Receive Offload (0,1), default 0=off (array of int)
parm:           debug:Debug level (0=none, ..., 16=all) (int)
```

dmesg grep shows the same thing as before 

```
[    3.353032] igb: module verification failed: signature and/or  required key missing - tainting kernel
```

---

### Post by chili555 on 2018-04-02
> 01:00.0 Ethernet controller [0200]: Intel Corporation Device [8086:[COLOR="#FF0000"]10aa[/COLOR]] (rev 02)    Subsystem: Intel Corporation Device [8086:0000]Next, we run:```
modinfo igb | grep [COLOR="#FF0000"]10AA[/COLOR]
```And the result is:> The grep of modifno didn't grab anything We therefore conclude that the version of igb that you compiled doesn't cover your device.

We could try a newer kernel version and a later version of the driver; we could try, experimentally to force the pci.id 8086:10aa into the driver code and recompile or you could invest a very few dollars into a known working device.

What is your preference?

---

### Post by praseodym on 2018-04-02
SecureBoot is disabled?

---

