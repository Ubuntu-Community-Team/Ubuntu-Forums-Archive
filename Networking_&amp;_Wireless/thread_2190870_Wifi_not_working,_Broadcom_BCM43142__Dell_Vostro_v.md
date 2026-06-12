---
title: "Wifi not working, Broadcom BCM43142 / Dell Vostro v130"
date: 2013-11-29
forum: Networking &amp; Wireless
---

### Post by raphaelstbntlr on 2013-11-29
Hey guys, complete newbie here. I am recent convert to ubuntu as i had a mac before. But my school gave us a dell vostro v130 on which i installed ubuntu 13.10. So my problem is that it installed perfectly but the wifi always says it's offline and i have no idea how to turn it on. 
Thanks in advance for your help.

---

### Post by mörgæs on 2013-11-29
Hi, welcome to the fora.

Please run the commands shown [here]("http://ubuntuforums.org/showthread.php?p=6183681") and post the results.

---

### Post by raphaelstbntlr on 2013-11-30
1) Machine brand and model: Dell vosto v130
2) Wireless Brand, Model and Wireless Chipset:
```
$ lscpi
00:00.0 Host bridge: Intel Corporation3rd Gen Core processor DRAM Controller (rev 09) 
00:02.0 VGA compatible controller:Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: IntelCorporation 7 Series/C210 Series Chipset Family USB xHCI HostController (rev 04) 
00:16.0 Communication controller: IntelCorporation 7 Series/C210 Series Chipset Family MEI Controller #1(rev 04) 
00:1a.0 USB controller: IntelCorporation 7 Series/C210 Series Chipset Family USB Enhanced HostController #2 (rev 04) 
00:1b.0 Audio device: Intel Corporation7 Series/C210 Series Chipset Family High Definition Audio Controller(rev 04) 
00:1c.0 PCI bridge: Intel Corporation 7Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) 
00:1c.4 PCI bridge: Intel Corporation 7Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4) 
00:1d.0 USB controller: IntelCorporation 7 Series/C210 Series Chipset Family USB Enhanced HostController #1 (rev 04) 
00:1f.0 ISA bridge: Intel CorporationHM77 Express Chipset LPC Controller (rev 04) 
00:1f.2 SATA controller: IntelCorporation 7 Series Chipset Family 6-port SATA Controller [AHCImode] (rev 04) 
00:1f.3 SMBus: Intel Corporation 7Series/C210 Series Chipset Family SMBus Controller (rev 04) 
01:00.0 Network controller: BroadcomCorporation BCM43142 802.11b/g/n (rev 01) 
02:00.0 Ethernet controller: QualcommAtheros AR8161 Gigabit Ethernet (rev 10)
```
```
$ lsusb
Bus 002 Device 002: ID 8087:0024 IntelCorp. Integrated Rate Matching Hub 
Bus 002 Device 001: ID 1d6b:0002 LinuxFoundation 2.0 root hub 
Bus 001 Device 005: ID 0c45:648bMicrodia Integrated Webcam 
Bus 001 Device 004: ID 0bda:0129Realtek Semiconductor Corp. RTS5129 Card Reader Controller 
Bus 001 Device 003: ID 138a:0011Validity Sensors, Inc. VFS5011 Fingerprint Reader 
Bus 001 Device 002: ID 8087:0024 IntelCorp. Integrated Rate Matching Hub 
Bus 001 Device 001: ID 1d6b:0002 LinuxFoundation 2.0 root hub 
Bus 004 Device 001: ID 1d6b:0003 LinuxFoundation 3.0 root hub 
Bus 003 Device 001: ID 1d6b:0002 LinuxFoundation 2.0 root hub
```
3) Check Interface:
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr5c:f9:dd:60:7e:90
          UP BROADCAST MULTICAST MTU:1500  Metric:1 
          RX packets:0 errors:0dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TXbytes:0 (0.0 B) 
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1 Mask:255.0.0.0 
          inet6 addr: ::1/128Scope:Host 
          UP LOOPBACK RUNNING MTU:65536  Metric:1 
          RX packets:16 errors:0dropped:0 overruns:0 frame:0 
          TX packets:16 errors:0dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
RX bytes:1184 (1.1 KB)  TXbytes:1184 (1.1 KB)
```

```
$ iwconfig
eth0      no wireless extensions. 


lo        no wireless extensions.
```
4)Check for modules:
```
$ lsmod
Module                  Size  Used by 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  0 
bnep                   19564  2 
bluetooth             371874  10bnep,rfcomm 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138538  0 
kvm                   431315  1kvm_intel 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
cryptd                 20329  1ghash_clmulni_intel 
snd_hda_codec_hdmi     41276  1 
snd_hda_codec_cirrus    14537  1 
dell_wmi               12761  0 
sparse_keymap          13948  1dell_wmi 
dell_laptop            17369  0 
dcdbas                 14847  1dell_laptop 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1uvcvideo 
videobuf2_memops       13362  1videobuf2_vmalloc 
videobuf2_core         40469  1uvcvideo 
videodev              133390  2uvcvideo,videobuf2_core 
rts5139               331166  0 
snd_hda_intel          48171  3 
snd_hda_codec         188738  3snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_cirrus 
snd_hwdep              13602  1snd_hda_codec 
snd_pcm               102033  3snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel 
snd_page_alloc         18710  2snd_pcm,snd_hda_intel 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1snd_seq_midi 
snd_rawmidi            30095  1snd_seq_midi 
snd_seq                61560  2snd_seq_midi_event,snd_seq_midi 
microcode              23518  0 
psmouse                97626  0 
serio_raw              13413  0 
snd_seq_device         14497  3snd_seq,snd_rawmidi,snd_seq_midi 
snd_timer              29433  2snd_pcm,snd_seq 
snd                    69141  17snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_cirrus,snd_seq_midi
lpc_ich                21080  0 
i915                  655752  3 
bcma                   46670  0 
drm_kms_helper         52651  1 i915 
soundcore              12680  1 snd 
mei_me                 18421  0 
drm                   296739  4i915,drm_kms_helper 
mei                    77692  1 mei_me 
i2c_algo_bit           13413  1 i915 
wmi                    19070  1dell_wmi 
video                  19318  1 i915 
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3lp,ppdev,parport_pc 
ahci                   25819  2 
libahci                31898  1 ahci 
alx                    32255  0 
mdio                   13807  1 alx  
```
5) Kernel Boot Messages:
```
$ dmesg
[    0.135159] pci 0000:00:1f.2: reg0x20: [io  0x3060-0x307f] 
[    0.135170] pci 0000:00:1f.2: reg0x24: [mem 0x90618000-0x906187ff] 
[    0.135232] pci 0000:00:1f.2: PME#supported from D3hot 
[    0.135308] pci 0000:00:1f.3:[8086:1e22] type 00 class 0x0c0500 
[    0.135332] pci 0000:00:1f.3: reg0x10: [mem 0x90614000-0x906140ff 64bit] 
[    0.135367] pci 0000:00:1f.3: reg0x20: [io  0xefa0-0xefbf] 
[    0.135605] pci 0000:01:00.0:[14e4:4365] type 00 class 0x028000 
[    0.135642] pci 0000:01:00.0: reg0x10: [mem 0x90500000-0x90507fff 64bit] 
[    0.135821] pci 0000:01:00.0:supports D1 D2 
[    0.135823] pci 0000:01:00.0: PME#supported from D0 D3hot D3cold 
[    0.135868] pci 0000:01:00.0: Systemwakeup disabled by ACPI 
[    0.140219] pci 0000:00:1c.0: PCIbridge to [bus 01] 
[    0.140227] pci 0000:00:1c.0:  bridge window [mem 0x90500000-0x905fffff] 
[    0.140342] pci 0000:02:00.0:[1969:1091] type 00 class 0x020000 
[    0.140377] pci 0000:02:00.0: reg0x10: [mem 0x90400000-0x9043ffff 64bit] 
[    0.140395] pci 0000:02:00.0: reg0x18: [io  0x2000-0x207f] 
[    0.140552] pci 0000:02:00.0: PME#supported from D0 D1 D2 D3hot D3cold 
[    0.140593] pci 0000:02:00.0: Systemwakeup disabled by ACPI 
[    0.148200] pci 0000:00:1c.4: PCIbridge to [bus 02] 
[    0.148206] pci 0000:00:1c.4:  bridge window [io  0x2000-0x2fff] 
[    0.148211] pci 0000:00:1c.4:  bridge window [mem 0x90400000-0x904fffff] 
[    0.148831] ACPI: PCI Interrupt Link[LNKA] (IRQs 1 3 4 5 6 10 *11 12 14 15) 
[    0.148904] ACPI: PCI Interrupt Link[LNKB] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled. 
[    0.148973] ACPI: PCI Interrupt Link[LNKC] (IRQs 1 3 4 5 6 *10 11 12 14 15) 
[    0.149041] ACPI: PCI Interrupt Link[LNKD] (IRQs 1 3 4 5 6 10 *11 12 14 15) 
[    0.149108] ACPI: PCI Interrupt Link[LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled. 
[    0.149175] ACPI: PCI Interrupt Link[LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled. 
[    0.149243] ACPI: PCI Interrupt Link[LNKG] (IRQs 1 3 4 5 6 10 11 12 14 15) *7 
[    0.149311] ACPI: PCI Interrupt Link[LNKH] (IRQs 1 3 4 5 6 *10 11 12 14 15) 
[    0.149628] ACPI: Enabled 5 GPEs inblock 00 to 3F 
[    0.149639] ACPI: \_SB_.PCI0: notifyhandler is installed 
[    0.149705] Found 1 acpi rootdevices 
[    0.149784] ACPI: EC: GPE = 0x17,I/O: command/status = 0x66, data = 0x62 
[    0.149906] vgaarb: device added:PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none 
[    0.149910] vgaarb: loaded 
[    0.149911] vgaarb: bridge controlpossible 0000:00:02.0 
[    0.150116] SCSI subsysteminitialized 
[    0.150119] ACPI: bus type ATAregistered 
[    0.150179] libata version 3.00loaded. 
[    0.150200] ACPI: bus type USBregistered 
[    0.150219] usbcore: registered newinterface driver usbfs 
[    0.150230] usbcore: registered newinterface driver hub 
[    0.150261] usbcore: registered newdevice driver usb 
[    0.150374] PCI: Using ACPI for IRQrouting 
[    0.152306] PCI: pci_cache_line_sizeset to 64 bytes 
[    0.152387] e820: reserve RAM buffer[mem 0x0009d800-0x0009ffff] 
[    0.152389] e820: reserve RAM buffer[mem 0x40004000-0x43ffffff] 
[    0.152391] e820: reserve RAM buffer[mem 0x681fc000-0x6bffffff] 
[    0.152393] e820: reserve RAM buffer[mem 0x772a5000-0x77ffffff] 
[    0.152395] e820: reserve RAM buffer[mem 0x7a000000-0x7bffffff] 
[    0.152397] e820: reserve RAM buffer[mem 0x100600000-0x103ffffff] 
[    0.152495] NetLabel: Initializing 
[    0.152497] NetLabel:  domain hashsize = 128 
[    0.152498] NetLabel:  protocols =UNLABELED CIPSOv4 
[    0.152510] NetLabel:  unlabeledtraffic allowed by default 
[    0.152580] hpet0: at MMIO0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0 
[    0.152587] hpet0: 8 comparators,64-bit 14.318180 MHz counter 
[    0.154608] Switched to clocksourcehpet 
[    0.160413] AppArmor: AppArmorFilesystem Enabled 
[    0.160441] pnp: PnP ACPI init 
[    0.160457] ACPI: bus type PNPregistered 
[    0.160500] pnp 00:00: [dma 4] 
[    0.160524] pnp 00:00: Plug and PlayACPI device, IDs PNP0200 (active) 
[    0.160650] pnp 00:01: Plug and PlayACPI device, IDs PNP0103 (active) 
[    0.160690] pnp 00:02: Plug and PlayACPI device, IDs PNP0c04 (active) 
[    0.160743] system 00:03: [io 0x0680-0x069f] has been reserved 
[    0.160746] system 00:03: [io 0x1000-0x1003] has been reserved 
[    0.160749] system 00:03: [io 0x1004-0x1013] has been reserved 
[    0.160751] system 00:03: [io 0xffff] has been reserved 
[    0.160756] system 00:03: [io 0x0400-0x0453] could not be reserved 
[    0.160759] system 00:03: [io 0x0458-0x047f] has been reserved 
[    0.160761] system 00:03: [io 0x0500-0x057f] has been reserved 
[    0.160764] system 00:03: [io 0x164e-0x164f] has been reserved 
[    0.160767] system 00:03: Plug andPlay ACPI device, IDs PNP0c02 (active) 
[    0.160794] pnp 00:04: Plug and PlayACPI device, IDs PNP0b00 (active) 
[    0.160850] system 00:05: [io 0x0454-0x0457] has been reserved 
[    0.160854] system 00:05: Plug andPlay ACPI device, IDs INT3f0d PNP0c02 (active) 
[    0.160909] pnp 00:06: Plug and PlayACPI device, IDs PNP0303 (active) 
[    0.160945] pnp 00:07: Plug and PlayACPI device, IDs DLL055c PNP0f13 (active) 
[    0.161103] system 00:08: [mem0xfed1c000-0xfed1ffff] has been reserved 
[    0.161106] system 00:08: [mem0xfed10000-0xfed17fff] has been reserved 
[    0.161109] system 00:08: [mem0xfed18000-0xfed18fff] has been reserved 
[    0.161111] system 00:08: [mem0xfed19000-0xfed19fff] has been reserved 
[    0.161114] system 00:08: [mem0xf8000000-0xfbffffff] has been reserved 
[    0.161117] system 00:08: [mem0xfed20000-0xfed3ffff] has been reserved 
[    0.161119] system 00:08: [mem0xfed90000-0xfed93fff] has been reserved 
[    0.161122] system 00:08: [mem0xfed45000-0xfed8ffff] has been reserved 
[    0.161124] system 00:08: [mem0xff000000-0xffffffff] could not be reserved 
[    0.161127] system 00:08: [mem0xfee00000-0xfeefffff] could not be reserved 
[    0.161130] system 00:08: [mem0xfffff000-0xffffffff] has been reserved 
[    0.161133] system 00:08: Plug andPlay ACPI device, IDs PNP0c02 (active) 
[    0.161349] pnp 00:09: Plug and PlayACPI device, IDs SMO8810 (active) 
[    0.161527] pnp: PnP ACPI: found 10devices 
[    0.161529] ACPI: bus type PNPunregistered 
[    0.168193] pci 0000:00:1c.0: PCIbridge to [bus 01] 
[    0.168202] pci 0000:00:1c.0:  bridge window [mem 0x90500000-0x905fffff] 
[    0.168216] pci 0000:00:1c.4: PCIbridge to [bus 02] 
[    0.168220] pci 0000:00:1c.4:  bridge window [io  0x2000-0x2fff] 
[    0.168228] pci 0000:00:1c.4:  bridge window [mem 0x90400000-0x904fffff] 
[    0.168404] pci_bus 0000:00:resource 4 [io  0x0000-0x0cf7] 
[    0.168407] pci_bus 0000:00:resource 5 [io  0x0d00-0xffff] 
[    0.168409] pci_bus 0000:00:resource 6 [mem 0x000a0000-0x000bffff] 
[    0.168411] pci_bus 0000:00:resource 7 [mem 0x7ea00000-0xfeafffff] 
[    0.168414] pci_bus 0000:01:resource 1 [mem 0x90500000-0x905fffff] 
[    0.168417] pci_bus 0000:02:resource 0 [io  0x2000-0x2fff] 
[    0.168419] pci_bus 0000:02:resource 1 [mem 0x90400000-0x904fffff] 
[    0.168456] NET: Registered protocolfamily 2 
[    0.168639] TCP established hashtable entries: 16384 (order: 6, 262144 bytes) 
[    0.168710] TCP bind hash tableentries: 16384 (order: 6, 262144 bytes) 
[    0.168757] TCP: Hash tablesconfigured (established 16384 bind 16384) 
[    0.168778] TCP: reno registered 
[    0.168785] UDP hash table entries:1024 (order: 3, 32768 bytes) 
[    0.168796] UDP-Lite hash tableentries: 1024 (order: 3, 32768 bytes) 
[    0.168864] NET: Registered protocolfamily 1 
[    0.168877] pci 0000:00:02.0: Bootvideo device 
[    0.169438] pci 0000:02:00.0: setMSI_INTX_DISABLE_BUG flag 
[    0.169444] PCI: CLS 64 bytes,default 64 
[    0.169491] Trying to unpack rootfsimage as initramfs... 
[    0.557812] Freeing initrd memory:16900K (ffff880035eee000 - ffff880036f6f000) 
[    0.557818] PCI-DMA: Using softwarebounce buffering for IO (SWIOTLB) 
[    0.557821] software IO TLB [mem0x70c00000-0x74c00000] (64MB) mapped at[ffff880070c00000-ffff880074bfffff] 
[    0.557864] Simple Boot Flag at 0x66set to 0x1 
[    0.558014] Scanning for low memorycorruption every 60 seconds 
[    0.558363] Initialise moduleverification 
[    0.558413] audit: initializingnetlink socket (disabled) 
[    0.558424] type=2000audit(1385810564.552:1): initialized 
[    0.596638] bounce pool size: 64pages 
[    0.596650] HugeTLB registered 2 MBpage size, pre-allocated 0 pages 
[    0.597891] zbud: loaded 
[    0.598061] VFS: Disk quotasdquot_6.5.2 
[    0.598111] Dquot-cache hash tableentries: 512 (order 0, 4096 bytes) 
[    0.598651] fuse init (API version7.22) 
[    0.598741] msgmni has been set to3585 
[    0.599223] Key type asymmetricregistered 
[    0.599226] Asymmetric key parser'x509' registered 
[    0.599261] Block layer SCSI generic(bsg) driver version 0.4 loaded (major 252) 
[    0.599297] io scheduler noopregistered 
[    0.599300] io scheduler deadlineregistered (default) 
[    0.599327] io scheduler cfqregistered 
[    0.599542] pci_hotplug: PCI HotPlug PCI Core version: 0.5 
[    0.599557] pciehp: PCI Express HotPlug Controller Driver version: 0.4 
[    0.599622] intel_idle: MWAITsubstates: 0x21120 
[    0.599624] intel_idle: v0.4 model0x3A 
[    0.599626] intel_idle:lapic_timer_reliable_states 0xffffffff 
[    0.798186] ACPI: AC Adapter [ADP0](on-line) 
[    0.798290] input: Power Button as/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0 
[    0.798295] ACPI: Power Button[PWRB] 
[    0.798330] input: Sleep Button as/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1 
[    0.798334] ACPI: Sleep Button[SLPB] 
[    0.798372] input: Lid Switch as/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2 
[    0.798771] ACPI: Lid Switch [LID0] 
[    0.798825] input: Power Button as/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3 
[    0.798829] ACPI: Power Button[PWRF] 
[    0.798911] ACPI: Requestingacpi_cpufreq 
[    0.810402] thermal LNXTHERM:00:registered as thermal_zone0 
[    0.810406] ACPI: Thermal Zone[TZ00] (35 C) 
[    0.810696] thermal LNXTHERM:01:registered as thermal_zone1 
[    0.810698] ACPI: Thermal Zone[TZ01] (35 C) 
[    0.810738] GHES: HEST is notenabled! 
[    0.810813] Serial: 8250/16550driver, 32 ports, IRQ sharing enabled 
[    0.813877] Linux agpgart interfacev0.103 
[    0.815433] brd: module loaded 
[    0.816250] ACPI: Battery Slot[BAT0] (battery present) 
[    0.816300] loop: module loaded 
[    0.816656] libphy: Fixed MDIO Bus:probed 
[    0.816742] tun: Universal TUN/TAPdevice driver, 1.6 
[    0.816744] tun: (C) 1999-2004 MaxKrasnyansky <maxk@qualcomm.com> 
[    0.816786] PPP generic driverversion 2.4.2 
[    0.816830] ehci_hcd: USB 2.0'Enhanced' Host Controller (EHCI) Driver 
[    0.816832] ehci-pci: EHCI PCIplatform driver 
[    0.816952] ehci-pci 0000:00:1a.0:setting latency timer to 64 
[    0.816961] ehci-pci 0000:00:1a.0:EHCI Host Controller 
[    0.816967] ehci-pci 0000:00:1a.0:new USB bus registered, assigned bus number 1 
[    0.816986] ehci-pci 0000:00:1a.0:debug port 2 
[    0.820897] ehci-pci 0000:00:1a.0:cache line size of 64 is not supported 
[    0.820916] ehci-pci 0000:00:1a.0:irq 16, io mem 0x9061a000 
[    0.830142] ehci-pci 0000:00:1a.0:USB 2.0 started, EHCI 1.00 
[    0.830163] usb usb1: New USB devicefound, idVendor=1d6b, idProduct=0002 
[    0.830166] usb usb1: New USB devicestrings: Mfr=3, Product=2, SerialNumber=1 
[    0.830168] usb usb1: Product: EHCIHost Controller 
[    0.830171] usb usb1: Manufacturer:Linux 3.11.0-12-generic ehci_hcd 
[    0.830173] usb usb1: SerialNumber:0000:00:1a.0 
[    0.830281] hub 1-0:1.0: USB hubfound 
[    0.830287] hub 1-0:1.0: 2 portsdetected 
[    0.830492] ehci-pci 0000:00:1d.0:setting latency timer to 64 
[    0.830500] ehci-pci 0000:00:1d.0:EHCI Host Controller 
[    0.830505] ehci-pci 0000:00:1d.0:new USB bus registered, assigned bus number 2 
[    0.830521] ehci-pci 0000:00:1d.0:debug port 2 
[    0.834405] ehci-pci 0000:00:1d.0:cache line size of 64 is not supported 
[    0.834421] ehci-pci 0000:00:1d.0:irq 23, io mem 0x90619000 
[    0.846135] ehci-pci 0000:00:1d.0:USB 2.0 started, EHCI 1.00 
[    0.846149] usb usb2: New USB devicefound, idVendor=1d6b, idProduct=0002 
[    0.846152] usb usb2: New USB devicestrings: Mfr=3, Product=2, SerialNumber=1 
[    0.846154] usb usb2: Product: EHCIHost Controller 
[    0.846156] usb usb2: Manufacturer:Linux 3.11.0-12-generic ehci_hcd 
[    0.846158] usb usb2: SerialNumber:0000:00:1d.0 
[    0.846260] hub 2-0:1.0: USB hubfound 
[    0.846264] hub 2-0:1.0: 2 portsdetected 
[    0.846371] ehci-platform: EHCIgeneric platform driver 
[    0.846379] ohci_hcd: USB 1.1 'Open'Host Controller (OHCI) Driver 
[    0.846380] ohci-platform: OHCIgeneric platform driver 
[    0.846386] uhci_hcd: USB UniversalHost Controller Interface driver 
[    0.846504] xhci_hcd 0000:00:14.0:setting latency timer to 64 
[    0.846508] xhci_hcd 0000:00:14.0:xHCI Host Controller 
[    0.846515] xhci_hcd 0000:00:14.0:new USB bus registered, assigned bus number 3 
[    0.846618] xhci_hcd 0000:00:14.0:cache line size of 64 is not supported 
[    0.846650] xhci_hcd 0000:00:14.0:irq 40 for MSI/MSI-X 
[    0.846708] usb usb3: New USB devicefound, idVendor=1d6b, idProduct=0002 
[    0.846711] usb usb3: New USB devicestrings: Mfr=3, Product=2, SerialNumber=1 
[    0.846713] usb usb3: Product: xHCIHost Controller 
[    0.846715] usb usb3: Manufacturer:Linux 3.11.0-12-generic xhci_hcd 
[    0.846717] usb usb3: SerialNumber:0000:00:14.0 
[    0.846789] xHCI xhci_add_endpointcalled for root hub 
[    0.846791] xHCIxhci_check_bandwidth called for root hub 
[    0.846815] hub 3-0:1.0: USB hubfound 
[    0.846823] hub 3-0:1.0: 4 portsdetected 
[    0.847191] xhci_hcd 0000:00:14.0:xHCI Host Controller 
[    0.847195] xhci_hcd 0000:00:14.0:new USB bus registered, assigned bus number 4 
[    0.847218] usb usb4: New USB devicefound, idVendor=1d6b, idProduct=0003 
[    0.847221] usb usb4: New USB devicestrings: Mfr=3, Product=2, SerialNumber=1 
[    0.847223] usb usb4: Product: xHCIHost Controller 
[    0.847225] usb usb4: Manufacturer:Linux 3.11.0-12-generic xhci_hcd 
[    0.847227] usb usb4: SerialNumber:0000:00:14.0 
[    0.847300] xHCI xhci_add_endpointcalled for root hub 
[    0.847302] xHCIxhci_check_bandwidth called for root hub 
[    0.847323] hub 4-0:1.0: USB hubfound 
[    0.847331] hub 4-0:1.0: 4 portsdetected 
[    0.854186] i8042: PNP: PS/2Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[    0.857188] serio: i8042 KBD port at0x60,0x64 irq 1 
[    0.857194] serio: i8042 AUX port at0x60,0x64 irq 12 
[    0.857317] mousedev: PS/2 mousedevice common for all mice 
[    0.857501] rtc_cmos 00:04: RTC canwake from S4 
[    0.857642] rtc_cmos 00:04: rtccore: registered rtc_cmos as rtc0 
[    0.857685] rtc_cmos 00:04: alarmsup to one month, y3k, 242 bytes nvram, hpet irqs 
[    0.857760] device-mapper: uevent:version 1.0.3 
[    0.857823] device-mapper: ioctl:4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com 
[    0.857884] cpuidle: using governorladder 
[    0.857957] cpuidle: using governormenu 
[    0.857969] ledtrig-cpu: registeredto indicate activity on CPUs 
[    0.858062] TCP: cubic registered 
[    0.858171] NET: Registered protocolfamily 10 
[    0.858385] NET: Registered protocolfamily 17 
[    0.858396] Key type dns_resolverregistered 
[    0.858619] PM: Hibernation imagenot present or could not be loaded. 
[    0.858624] Loading moduleverification certificates 
[    0.859846] MODSIGN: Loaded cert'Magrathea: Glacier signing key:fddf6943d8ac4f5b6eb0919a7a3ee3d9088b1bfa' 
[    0.859859] registered taskstatsversion 1 
[    0.862469] Key type trustedregistered 
[    0.863449] input: AT Translated Set2 keyboard as /devices/platform/i8042/serio0/input/input4 
[    0.865115] Key type encryptedregistered 
[    0.867357] AppArmor: AppArmor sha1policy hashing enabled 
[    0.868168]   Magic number:5:275:379 
[    0.868261] rtc_cmos 00:04: settingsystem clock to 2013-11-30 11:22:45 UTC (1385810565) 
[    0.868649] BIOS EDD facility v0.162004-Jun-25, 0 devices found 
[    0.868651] EDD information notavailable. 
[    0.869891] Freeing unused kernelmemory: 1364K (ffffffff81d10000 - ffffffff81e65000) 
[    0.869894] Write protecting thekernel read-only data: 12288k 
[    0.873234] Freeing unused kernelmemory: 1040K (ffff8800016fc000 - ffff880001800000) 
[    0.875663] Freeing unused kernelmemory: 836K (ffff880001b2f000 - ffff880001c00000) 
[    0.890862] systemd-udevd[113]:starting version 204 
[    1.117605] libahci: moduleverification failed: signature and/or required key missing - taintingkernel 
[    1.118274] ahci 0000:00:1f.2:version 3.0 
[    1.118428] ahci 0000:00:1f.2: irq41 for MSI/MSI-X 
[    1.118496] ahci 0000:00:1f.2: AHCI0001.0300 32 slots 6 ports 6 Gbps 0x1 impl SATA mode 
[    1.118500] ahci 0000:00:1f.2:flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.118508] ahci 0000:00:1f.2:setting latency timer to 64 
[    1.119168] alx 0000:02:00.0 eth0:Qualcomm Atheros AR816x/AR817x Ethernet [5c:f9:dd:60:7e:90] 
[    1.120599] scsi0 : ahci 
[    1.122061] scsi1 : ahci 
[    1.123418] scsi2 : ahci 
[    1.124805] scsi3 : ahci 
[    1.126136] scsi4 : ahci 
[    1.128341] scsi5 : ahci 
[    1.128464] ata1: SATA max UDMA/133abar m2048@0x90618000 port 0x90618100 irq 41 
[    1.128467] ata2: DUMMY 
[    1.128468] ata3: DUMMY 
[    1.128470] ata4: DUMMY 
[    1.128471] ata5: DUMMY 
[    1.128472] ata6: DUMMY 
[    1.141941] usb 1-1: new high-speedUSB device number 2 using ehci-pci 
[    1.274332] usb 1-1: New USB devicefound, idVendor=8087, idProduct=0024 
[    1.274337] usb 1-1: New USB devicestrings: Mfr=0, Product=0, SerialNumber=0 
[    1.274746] hub 1-1:1.0: USB hubfound 
[    1.274941] hub 1-1:1.0: 6 portsdetected 
[    1.385783] usb 2-1: new high-speedUSB device number 2 using ehci-pci 
[    1.445767] ata1: SATA link up 3.0Gbps (SStatus 123 SControl 300) 
[    1.448976] ata1.00: ACPI cmd00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04) 
[    1.471986] ata1.00: ATA-8:ST320LT007-9ZV142, 0007DEM1, max UDMA/133 
[    1.471991] ata1.00: 625142448sectors, multi 16: LBA48 NCQ (depth 31/32) 
[    1.475588] ata1.00: ACPI cmd00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04) 
[    1.476083] ata1.00: configured forUDMA/133 
[    1.476349] scsi 0:0:0:0:Direct-Access     ATA      ST320LT007-9ZV14 0007 PQ: 0 ANSI: 5 
[    1.476588] sd 0:0:0:0: [sda]625142448 512-byte logical blocks: (320 GB/298 GiB) 
[    1.476591] sd 0:0:0:0: [sda]4096-byte physical blocks 
[    1.476625] sd 0:0:0:0: Attachedscsi generic sg0 type 0 
[    1.476725] sd 0:0:0:0: [sda] WriteProtect is off 
[    1.476731] sd 0:0:0:0: [sda] ModeSense: 00 3a 00 00 
[    1.476761] sd 0:0:0:0: [sda] Writecache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    1.518145] usb 2-1: New USB devicefound, idVendor=8087, idProduct=0024 
[    1.518150] usb 2-1: New USB devicestrings: Mfr=0, Product=0, SerialNumber=0 
[    1.518544] hub 2-1:1.0: USB hubfound 
[    1.518586] hub 2-1:1.0: 8 portsdetected 
[    1.553680] tsc: Refined TSCclocksource calibration: 1596.373 MHz 
[    1.562165]  sda: sda1 sda2 sda3sda4 < sda5 sda6 sda7 > 
[    1.563356] sd 0:0:0:0: [sda]Attached SCSI disk 
[    1.589852] usb 1-1.1: newfull-speed USB device number 3 using ehci-pci 
[    1.686741] usb 1-1.1: New USBdevice found, idVendor=138a, idProduct=0011 
[    1.686746] usb 1-1.1: New USBdevice strings: Mfr=0, Product=0, SerialNumber=1 
[    1.686749] usb 1-1.1: SerialNumber:7fba324d1255 
[    1.757733] usb 1-1.3: newhigh-speed USB device number 4 using ehci-pci 
[    1.850374] usb 1-1.3: New USBdevice found, idVendor=0bda, idProduct=0129 
[    1.850378] usb 1-1.3: New USBdevice strings: Mfr=1, Product=2, SerialNumber=3 
[    1.850381] usb 1-1.3: Product:USB2.0-CRW 
[    1.850383] usb 1-1.3: Manufacturer:Generic 
[    1.850385] usb 1-1.3: SerialNumber:20100201396000000 
[    1.921487] usb 1-1.5: newhigh-speed USB device number 5 using ehci-pci 
[    2.084999] usb 1-1.5: New USBdevice found, idVendor=0c45, idProduct=648b 
[    2.085004] usb 1-1.5: New USBdevice strings: Mfr=2, Product=1, SerialNumber=0 
[    2.085006] usb 1-1.5: Product:Laptop_Integrated_Webcam_E4HD 
[    2.085009] usb 1-1.5: Manufacturer:CNFB183J191090000S82 
[    2.553092] Switched to clocksourcetsc 
[    2.964796] EXT4-fs (sda6): mountedfilesystem with ordered data mode. Opts: (null) 
[   10.774321] Adding 1952764k swap on/dev/sda7.  Priority:-1 extents:1 across:1952764k FS 
[   10.826629] IPv6:ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   10.897001] systemd-udevd[287]:starting version 204 
[   10.963680] lp: driver loaded but nodevices found 
[   11.159292] wmi: Mapper loaded 
[   11.170190] [drm] Initialized drm1.1.0 20060810 
[   11.173057] mei_me 0000:00:16.0:setting latency timer to 64 
[   11.173114] mei_me 0000:00:16.0: irq42 for MSI/MSI-X 
[   11.183423] bcma: bus0: Found chipwith id 0xA886, rev 0x01 and package 0x08 
[   11.183458] bcma: bus0: Core 0found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x28, class 0x0) 
[   11.183485] bcma: bus0: Core 1found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x21, class 0x0) 
[   11.183539] bcma: bus0: Core 2found: PCIe (manuf 0x4BF, id 0x820, rev 0x16, class 0x0) 
[   11.183605] bcma: bus0: Core 3found: UNKNOWN (manuf 0x43B, id 0x368, rev 0x00, class 0x0) 
[   11.200281] [drm] Memory usable bygraphics device = 2048M 
[   11.200364] i915 0000:00:02.0:setting latency timer to 64 
[   11.243993] i915 0000:00:02.0: irq43 for MSI/MSI-X 
[   11.244005] [drm] Supports vblanktimestamp caching Rev 1 (10.10.2010). 
[   11.244007] [drm] Driver supportsprecise vblank timestamp query. 
[   11.244077] vgaarb: device changeddecodes:PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem 
[   11.257805] bcma: bus0: Busregistered 
[   11.294346] microcode: CPU0sig=0x306a9, pf=0x10, revision=0x17 
[   11.297230] fbcon: inteldrmfb (fb0)is primary device 
[   11.404004] type=1400audit(1385806976.038:2): apparmor="STATUS"operation="profile_load" parent=325 profile="unconfined"name="/sbin/dhclient" pid=335 comm="apparmor_parser"
[   11.404010] type=1400audit(1385806976.038:3): apparmor="STATUS"operation="profile_load" parent=325 profile="unconfined"name="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=335 comm="apparmor_parser" 
[   11.404014] type=1400audit(1385806976.038:4): apparmor="STATUS"operation="profile_load" parent=325 profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=335comm="apparmor_parser" 
[   11.404755] type=1400audit(1385806976.038:5): apparmor="STATUS"operation="profile_replace" parent=325 profile="unconfined"name="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=335 comm="apparmor_parser" 
[   11.404760] type=1400audit(1385806976.038:6): apparmor="STATUS"operation="profile_replace" parent=325 profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=335comm="apparmor_parser" 
[   11.405165] type=1400audit(1385806976.038:7): apparmor="STATUS"operation="profile_replace" parent=325 profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=335comm="apparmor_parser" 
[   11.522040] rts5139: module is fromthe staging directory, the quality is unknown, you have been warned. 
[   11.525714] Linux video captureinterface: v2.00 
[   11.530745] scsi6 : SCSI emulationfor RTS5139 USB card reader 
[   11.530946] scsi 6:0:0:0:Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS 
[   11.531349] sd 6:0:0:0: Attachedscsi generic sg1 type 0 
[   11.534601] usbcore: registered newinterface driver rts5139 
[   11.539014] uvcvideo: Found UVC 1.00device Laptop_Integrated_Webcam_E4HD (0c45:648b) 
[   11.564930] input:Laptop_Integrated_Webcam_E4HD as/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input5
[   11.566316] usbcore: registered newinterface driver uvcvideo 
[   11.566317] USB Video Class driver(1.1.1) 
[   11.631642] sd 6:0:0:0: [sdb]Attached SCSI removable disk 
[   11.654858] dcdbas dcdbas: DellSystems Management Base Driver (version 5.6.0-3.2) 
[   11.667202] psmouse serio1: alps:Unknown ALPS touchpad: E7=73 03 50, EC=73 02 02 
[   12.098289] Console: switching tocolour frame buffer device 170x48 
[   12.101946] i915 0000:00:02.0: fb0:inteldrmfb frame buffer device 
[   12.101947] i915 0000:00:02.0:registered panic notifier 
[   12.110226] EXT4-fs (sda6):re-mounted. Opts: errors=remount-ro 
[   12.153874] acpi device:36:registered as cooling_device2 
[   12.154083] ACPI: Video Device[GFX0] (multi-head: yes  rom: no  post: no) 
[   12.154998] input: Video Bus as/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6 
[   12.155346] [drm] Initialized i9151.6.0 20080730 for 0000:00:02.0 on minor 0 
[   12.156081] ACPI Warning:0x0000000000000428-0x000000000000042f SystemIO conflicts with Region\PMIO 1 (20130517/utaddress-251) 
[   12.156090] ACPI: If an ACPI driveris available for this device, you should use it instead of the nativedriver 
[   12.156094] ACPI Warning:0x0000000000000530-0x000000000000053f SystemIO conflicts with Region\GPIO 1 (20130517/utaddress-251) 
[   12.156098] ACPI: If an ACPI driveris available for this device, you should use it instead of the nativedriver 
[   12.156099] ACPI Warning:0x0000000000000500-0x000000000000052f SystemIO conflicts with Region\GPIO 1 (20130517/utaddress-251) 
[   12.156103] ACPI: If an ACPI driveris available for this device, you should use it instead of the nativedriver 
[   12.156104] lpc_ich: Resourceconflict(s) found affecting gpio_ich 
[   12.156321] snd_hda_intel0000:00:1b.0: irq 44 for MSI/MSI-X 
[   12.164808] input: Dell WMI hotkeysas /devices/virtual/input/input7 
[   12.205174] autoconfig: line_outs=1(0x5/0x0/0x0/0x0/0x0) type:speaker 
[   12.205178]    speaker_outs=0(0x0/0x0/0x0/0x0/0x0) 
[   12.205180]    hp_outs=1(0x4/0x0/0x0/0x0/0x0) 
[   12.205181]    mono: mono_out=0x0 
[   12.205182]    inputs: 
[   12.205184]      Internal Mic=0x8 
[   12.205186]      Mic=0x6 
[   12.217459] input: HDA Intel PCHHDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8 
[   12.225753] input: HDA Intel PCHHeadphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9 
[   12.225816] microcode: CPU1sig=0x306a9, pf=0x10, revision=0x17 
[   12.226321] input: HDA Intel PCH Micas /devices/pci0000:00/0000:00:1b.0/sound/card0/input10 
[   12.378090] microcode: MicrocodeUpdate Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   12.440578] input: PS/2 GenericMouse as /devices/platform/i8042/serio1/input/input11 
[   12.663702] init: failsafe mainprocess (565) killed by TERM signal 
[   12.817988] [drm] Enabling RC6states: RC6 on, RC6p on, RC6pp off 
[   13.068483] Bluetooth: Core ver 2.16
[   13.069344] NET: Registered protocolfamily 31 
[   13.069349] Bluetooth: HCI deviceand connection manager initialized 
[   13.069840] Bluetooth: HCI socketlayer initialized 
[   13.069844] Bluetooth: L2CAP socketlayer initialized 
[   13.069851] Bluetooth: SCO socketlayer initialized 
[   13.098245] Bluetooth: BNEP(Ethernet Emulation) ver 1.3 
[   13.098250] Bluetooth: BNEP filters:protocol multicast 
[   13.098260] Bluetooth: BNEP socketlayer initialized 
[   13.106589] Bluetooth: RFCOMM TTYlayer initialized 
[   13.106604] Bluetooth: RFCOMM socketlayer initialized 
[   13.106607] Bluetooth: RFCOMM ver1.11 
[   13.432330] init: avahi-cups-reloadmain process (660) terminated with status 1 
[   13.573847] ppdev: user-spaceparallel port driver 
[   13.589481] type=1400audit(1385806978.226:8): apparmor="STATUS"operation="profile_load" parent=672 profile="unconfined"name="/usr/lib/cups/backend/cups-pdf" pid=676comm="apparmor_parser" 
[   13.589491] type=1400audit(1385806978.226:9): apparmor="STATUS"operation="profile_load" parent=672 profile="unconfined"name="/usr/sbin/cupsd" pid=676 comm="apparmor_parser"
[   13.590337] type=1400audit(1385806978.226:10): apparmor="STATUS"operation="profile_replace" parent=672 profile="unconfined"name="/usr/sbin/cupsd" pid=676 comm="apparmor_parser"
[   14.426037] alx 0000:02:00.0: irq 45for MSI/MSI-X 
[   14.426493] IPv6:ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   14.427780] IPv6:ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   15.175901] type=1400audit(1385806979.810:11): apparmor="STATUS"operation="profile_load" parent=728 profile="unconfined"name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper"pid=733 comm="apparmor_parser" 
[  903.533324] systemd-hostnamed[2296]:Warning: nss-myhostname is not installed. Changing the local hostnamemight make it unresolveable. Please install nss-myhostname! 
```
6)Network configuration :
```
$ sudo lshw -C network
 *-network               
       description: Network controller 
       product: BCM43142 802.11b/g/n 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpressbus_master cap_list 
       configuration:driver=bcma-pci-bridge latency=0 
       resources: irq:16memory:90500000-90507fff 
  *-network 
       description: Ethernet interface 
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 10 
       serial: 5c:f9:dd:60:7e:90 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm pciexpress msimsix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt100bt-fd 1000bt-fd autonegotiation 
       configuration:autonegotiation=on broadcast=yes driver=alx latency=0 link=nomulticast=yes port=twisted pair 
resources: irq:45memory:90400000-9043ffff ioport:2000(size=128)  
```
7) Scan for networks:
```
$ iwlist scan
eth0      Interface doesn't supportscanning. 


lo        Interface doesn't supportscanning.  
```
8)Ubuntu Version:
```
$ lsb_release -d
Description:	Ubuntu 13.10  
```
9) Kernel/Architecture:
```
$ uname -mr
3.11.0-12-generic x86_64  
```

So that's all I think and again if my problem is stupid i'm sorry but I really can't find how to make it work.

---

### Post by praseodym on 2013-11-30
Does LAN work? If yes, activate the Broadcom-STA driver in "Update-manager"->"additional drivers"

---

### Post by raphaelstbntlr on 2013-11-30
No LAN does not work and my whenever i go on ubuntu it says network offline and i really don't know how to put it "online"

---

### Post by raphaelstbntlr on 2013-11-30
And when i go in additional drivers it says no additional drivers available.

---

### Post by praseodym on 2013-11-30
Download this package and save it in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu1_amd64.deb)

Installation via
```

sudo dpkg -i ~/Downloads/*.deb
```
Then activate the driver.

---

### Post by raphaelstbntlr on 2013-11-30
ok i'll see what happens

---

### Post by raphaelstbntlr on 2013-11-30
Ok so when i put in the command this is what happens ```
Selecting previously unselected packagebcmwl-kernel-source.(Reading database ... 162750 files anddirectories currently installed.) 
Unpacking bcmwl-kernel-source (from.../bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu1_amd64.deb) ... 
dpkg: dependency problems preventconfiguration of bcmwl-kernel-source: 
 bcmwl-kernel-source depends on dkms;however: 
  Package dkms is not installed. 


dpkg: error processingbcmwl-kernel-source (--install): 
 dependency problems - leavingunconfigured 
Errors were encountered whileprocessing: 
bcmwl-kernel-source  
```

---

### Post by praseodym on 2013-11-30
[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu4_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu4_all.deb)

Here it is, save it there, too, and try it again

---

### Post by raphaelstbntlr on 2013-11-30
WOW it works! Thanks so much i couldn't have done it without your help (i know i'm uber noob).
ps: is there a way i can help by putting this thread as solved?

---

### Post by mörgæs on 2013-11-30
Yes, see 'thread tools'.

---

