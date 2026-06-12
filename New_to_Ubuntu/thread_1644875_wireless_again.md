---
title: "wireless again"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by jackwilson on 2010-12-13
I want to activate the wlan driver on my acer travelmate 2300. I have installed ndiswrapper and went to the acer website and down loaded these three drivers that are supposed to be for my PC
 

 

 Wireless LAN Ambit Wireless LAN Driver 2.10.03.2004 784.4 KB 2008/12/02
 Wireless LAN Atheros Wireless LAN Driver 4.0.0.14001 5.8 MB 2008/12/02
 Wireless LAN Intel Wireless LAN Driver 9.0.0.60 1.6 MB 2008/12/02
 

 I installed the inf. file and all three say invalid driver.
 

 I had Ubuntu 10.04 wlan working on this PC when it was dual boot.
 I now have Ubuntu 10.10 standing alone as my only OS.  
 I do not have any way of copying the inf file other than what I have tried.
 

 I got a copy of a driver inf file online to get my wlan working b-4, however I am not able to find where I got it the last time.
 

 Someone who helped me before directed me to a site that had a link to a place that I could down load the driver that worked. I think I found the link and downloaded those drivers too, and they say invalid also.


Help again thanks,


jackwilson

---

### Post by cariboo on 2010-12-14
Unless your system is bleeding edge new, there probably already is a driver for your wireless device included in the kernel. Could you paste the output of:

```
sudo lshw -C network
```

in your next post.

---

### Post by bkratz on 2010-12-14
If it helps you,found your original post and it was probably following post 15 that got you working--good luck.

[http://www.uluga.ubuntuforums.org/showthread.php?t=1565643](http://www.uluga.ubuntuforums.org/showthread.php?t=1565643)

---

### Post by jackwilson on 2010-12-14
bunnyg@bunnyg-TravelMate-2300:~$ sudo lshw -C network
[sudo] password for bunnyg: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:66:31:09
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.105 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:6 memory:e0200000-e0201fff memory:24000000-24003fff
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: IPN 2220 802.11g
       vendor: InProComm Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=32 mingnt=32
       resources: ioport:3800(size=32) memory:e0203800-e020381f memory:e0203000-e02037ff
bunnyg@bunnyg-TravelMate-2300:~$

---

### Post by Hippytaff on 2010-12-14
> **anewguy said:**
> Since you are trying ndiswrapper via the gui'd front-end ndisgtk, we first need to verify some things:
 
- you installed ndiswrapper-common first
- you installed ndiswrapper-utilities second
- you installed ndisgtk third
 
- you have both the .inf and .sys files for your Windows driver. Make sure both are in the same folder - I normally tell people just put them on the desktop.
 
- you have removed all previous attempts at getting this working via ndiswrapper/ndisgtk:

[LIST]
[*]open a terminal window (Applications/Accessories/Terminal)
[*]type: sudo ndiswrapper -l <press enter> That's a lower case "L" for "list".
[*]For every driver/device returned in the list:
[LIST]
[*]sudo ndiswrapper -e xxxxxx <press enter> where xxxxxx is one of the drivers/devices returned in the "list" command
[*]repeat this until sudo ndiswrapper -l returns nothing.
[/LIST]
[/LIST]
Now add the driver/device via ndisgtk:
 
- via ndisgtk (System/Administration/Windows Wireless Drivers), do the add (or new) and point it to your .inf file - remember the .sys file(s) must be in the same folder. Be sure that when you have finished the add that the device shows as ready.
 
Now be sure wireless is enabled in network manager:
 
- right-click on the network manager icon and be sure "Enable Wireless" is checked - if not, check it.
- exit from network manager and wait a few seconds
 
Now check for wireless networks in network manager:
 
- left-click on the network manager icon and see if any wireless networks show.
 
Other things to be aware of:
 
- if your router uses MAC filtering, be sure the MAC of your PC is in the allowed list on the router
 
- if your router uses some sort of protection/encryption, be sure you match it and the password/passphrase when trying to connect 
 
- if your router does not broadcast the SSID (the name of your network) you must specifically set up the connection via network manager
 
 
Dave ;)
 for conveinience

---

### Post by jackwilson on 2010-12-14
[COLOR=Red]when I get to this point on (15)[/COLOR]

Now add the driver/device via ndisgtk:
 
 - via ndisgtk (System/Administration/Windows Wireless Drivers)

[COLOR=Red]and add the driver inf file that's when it tells me invalid driver. I have tried at least 6 different inf files and they all say invalid driver.
[/COLOR]

---

### Post by jackwilson on 2010-12-14
this is my output for dmesg

[    0.184840] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.184847] pci 0000:00:1d.7: PME# disabled
[    0.184931] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH4 ACPI/GPIO/TCO
[    0.184936] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH4 GPIO
[    0.184959] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.184966] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.184974] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.184981] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.184989] pci 0000:00:1f.1: reg 20: [io  0x1810-0x181f]
[    0.184997] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.185045] pci 0000:00:1f.3: reg 20: [io  0x1880-0x189f]
[    0.185085] pci 0000:00:1f.5: reg 10: [io  0x1c00-0x1cff]
[    0.185092] pci 0000:00:1f.5: reg 14: [io  0x18c0-0x18ff]
[    0.185099] pci 0000:00:1f.5: reg 18: [mem 0xe0100c00-0xe0100dff]
[    0.185107] pci 0000:00:1f.5: reg 1c: [mem 0xe0100800-0xe01008ff]
[    0.185135] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.185140] pci 0000:00:1f.5: PME# disabled
[    0.185165] pci 0000:00:1f.6: reg 10: [io  0x2400-0x24ff]
[    0.185172] pci 0000:00:1f.6: reg 14: [io  0x2000-0x207f]
[    0.185208] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.185213] pci 0000:00:1f.6: PME# disabled
[    0.185253] pci 0000:02:02.0: reg 10: [mem 0xe0200000-0xe0201fff]
[    0.185278] pci 0000:02:02.0: reg 30: [mem 0x00000000-0x00003fff pref]
[    0.185295] pci 0000:02:02.0: supports D1 D2
[    0.185298] pci 0000:02:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.185303] pci 0000:02:02.0: PME# disabled
[    0.185330] pci 0000:02:04.0: reg 10: [io  0x3800-0x381f]
[    0.185338] pci 0000:02:04.0: reg 14: [mem 0xe0203800-0xe020381f]
[    0.185345] pci 0000:02:04.0: reg 18: [mem 0xe0203000-0xe02037ff]
[    0.185377] pci 0000:02:04.0: supports D2
[    0.185406] pci 0000:02:06.0: reg 10: [mem 0xe0202000-0xe0202fff]
[    0.185424] pci 0000:02:06.0: supports D1 D2
[    0.185427] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.185432] pci 0000:02:06.0: PME# disabled
[    0.185473] pci 0000:00:1e.0: PCI bridge to [bus 02-02] (subtractive decode)
[    0.185479] pci 0000:00:1e.0:   bridge window [io  0x3000-0x3fff]
[    0.185485] pci 0000:00:1e.0:   bridge window [mem 0xe0200000-0xe05fffff]
[    0.185491] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.185495] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.185499] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.185535] pci_bus 0000:03: [bus 03-06] partially hidden behind transparent bridge 0000:02 [bus 02-02]
[    0.185545] pci_bus 0000:00: on NUMA node 0
[    0.185551] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.185772] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.189413] ACPI: PCI Interrupt Link [LNKA] (IRQs *6)
[    0.189541] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    0.189666] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[    0.189790] ACPI: PCI Interrupt Link [LNKD] (IRQs *6)
[    0.189921] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[    0.190045] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[    0.190169] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *0, disabled.
[    0.190296] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[    0.190347] HEST: Table is not found!
[    0.190466] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.190479] vgaarb: loaded
[    0.190722] SCSI subsystem initialized
[    0.190814] libata version 3.00 loaded.
[    0.190906] usbcore: registered new interface driver usbfs
[    0.190925] usbcore: registered new interface driver hub
[    0.190959] usbcore: registered new device driver usb
[    0.191147] ACPI: WMI: Mapper loaded
[    0.191151] PCI: Using ACPI for IRQ routing
[    0.191184] PCI: pci_cache_line_size set to 64 bytes
[    0.191258] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.191262] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.191266] reserve RAM buffer: 000000001eee0000 - 000000001fffffff 
[    0.191412] NetLabel: Initializing
[    0.191415] NetLabel:  domain hash size = 128
[    0.191418] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.191436] NetLabel:  unlabeled traffic allowed by default
[    0.191501] Switching to clocksource tsc
[    0.203999] AppArmor: AppArmor Filesystem Enabled
[    0.204034] pnp: PnP ACPI init
[    0.204077] ACPI: bus type pnp registered
[    0.205162] ERROR: Unable to locate IOAPIC for GSI 8
[    0.205225] ERROR: Unable to locate IOAPIC for GSI 13
[    0.206020] ERROR: Unable to locate IOAPIC for GSI 1
[    0.206177] ERROR: Unable to locate IOAPIC for GSI 12
[    0.206516] pnp: PnP ACPI: found 8 devices
[    0.206520] ACPI: ACPI bus type pnp unregistered
[    0.206525] PnPBIOS: Disabled by ACPI PNP
[    0.206546] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.206553] system 00:04: [io  0x0600-0x060f] has been reserved
[    0.206557] system 00:04: [io  0x0700-0x070f] has been reserved
[    0.206561] system 00:04: [io  0x0800-0x080f] has been reserved
[    0.206565] system 00:04: [io  0x1000-0x107f] has been reserved
[    0.206569] system 00:04: [io  0x1180-0x11bf] has been reserved
[    0.206573] system 00:04: [io  0x01c0-0x01cf] has been reserved
[    0.206578] system 00:04: [io  0xfe00] has been reserved
[    0.206582] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.206586] system 00:04: [io  0x0610-0x061f] has been reserved
[    0.206593] system 00:04: [mem 0xfec10000-0xfec1ffff] has been reserved
[    0.206597] system 00:04: [mem 0xff800000-0xffbfffff] has been reserved
[    0.206602] system 00:04: [mem 0xfff00000-0xffffffff] could not be reserved
[    0.206607] system 00:04: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.206611] system 00:04: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.206616] system 00:04: [mem 0x000df800-0x000dffff] could not be reserved
[    0.243420] pci 0000:00:1e.0: BAR 15: assigned [mem 0x20000000-0x25ffffff pref]
[    0.243426] pci 0000:00:1f.1: BAR 5: assigned [mem 0x26000000-0x260003ff]
[    0.243434] pci 0000:00:1f.1: BAR 5: set to [mem 0x26000000-0x260003ff] (PCI address [0x26000000-0x260003ff]
[    0.243440] pci 0000:02:06.0: BAR 15: assigned [mem 0x20000000-0x23ffffff pref]
[    0.243445] pci 0000:02:06.0: BAR 16: assigned [mem 0x28000000-0x2bffffff]
[    0.243450] pci 0000:02:02.0: BAR 6: assigned [mem 0x24000000-0x24003fff pref]
[    0.243454] pci 0000:02:06.0: BAR 13: assigned [io  0x3000-0x30ff]
[    0.243458] pci 0000:02:06.0: BAR 14: assigned [io  0x3400-0x34ff]
[    0.243462] pci 0000:02:06.0: CardBus bridge to [bus 03-06]
[    0.243466] pci 0000:02:06.0:   bridge window [io  0x3000-0x30ff]
[    0.243471] pci 0000:02:06.0:   bridge window [io  0x3400-0x34ff]
[    0.243477] pci 0000:02:06.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[    0.243482] pci 0000:02:06.0:   bridge window [mem 0x28000000-0x2bffffff]
[    0.243488] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
[    0.243493] pci 0000:00:1e.0:   bridge window [io  0x3000-0x3fff]
[    0.243500] pci 0000:00:1e.0:   bridge window [mem 0xe0200000-0xe05fffff]
[    0.243506] pci 0000:00:1e.0:   bridge window [mem 0x20000000-0x25ffffff pref]
[    0.243524] pci 0000:00:1e.0: setting latency timer to 64
[    0.243535] pci 0000:02:06.0: enabling device (0104 -> 0107)
[    0.243786] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[    0.243791] PCI: setting IRQ 10 as level-triggered
[    0.243797] pci 0000:02:06.0: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[    0.243805] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.243809] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.243813] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.243817] pci_bus 0000:02: resource 1 [mem 0xe0200000-0xe05fffff]
[    0.243821] pci_bus 0000:02: resource 2 [mem 0x20000000-0x25ffffff pref]
[    0.243824] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.243828] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.243832] pci_bus 0000:03: resource 0 [io  0x3000-0x30ff]
[    0.243835] pci_bus 0000:03: resource 1 [io  0x3400-0x34ff]
[    0.243839] pci_bus 0000:03: resource 2 [mem 0x20000000-0x23ffffff pref]
[    0.243843] pci_bus 0000:03: resource 3 [mem 0x28000000-0x2bffffff]
[    0.243902] NET: Registered protocol family 2
[    0.243999] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.244300] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.244430] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.244588] TCP: Hash tables configured (established 16384 bind 16384)
[    0.244592] TCP reno registered
[    0.244597] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.244609] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.244732] NET: Registered protocol family 1
[    0.244763] pci 0000:00:02.0: Boot video device
[    0.244858] PCI: CLS 32 bytes, default 64
[    0.244974] Simple Boot Flag at 0x37 set to 0x1
[    0.245121] cpufreq-nforce2: No nForce2 chipset.
[    0.245157] Scanning for low memory corruption every 60 seconds
[    0.245396] audit: initializing netlink socket (disabled)
[    0.245419] type=2000 audit(1292306315.244:1): initialized
[    0.261247] Trying to unpack rootfs image as initramfs...
[    0.280989] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.289113] VFS: Disk quotas dquot_6.5.2
[    0.289261] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.290369] fuse init (API version 7.14)
[    0.290524] msgmni has been set to 937
[    0.297006] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.297012] io scheduler noop registered
[    0.297015] io scheduler deadline registered
[    0.297044] io scheduler cfq registered (default)
[    0.297241] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.297272] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.297552] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.316664] ACPI: Lid Switch [LID]
[    0.316787] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.316797] ACPI: Sleep Button [SLPB]
[    0.316879] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.316884] ACPI: Power Button [PWRF]
[    0.317121] ACPI: Fan [FAN0] (off)
[    0.317264] ACPI: Fan [FAN1] (off)
[    0.317407] ACPI: acpi_idle registered with cpuidle
[    0.317456] Marking TSC unstable due to TSC halts in idle
[    0.324586] Switching to clocksource acpi_pm
[    0.352732] thermal LNXTHERM:01: registered as thermal_zone0
[    0.352750] ACPI: Thermal Zone [THRM] (25 C)
[    0.352850] ACPI: SBS HC: EC = 0xde85bba0, offset = 0x18, query_bit = 0x20
[    0.480477] ACPI: Smart Battery System [SBS0]: AC Adapter [AC0] (on-line)
[    0.703840] Freeing initrd memory: 10508k freed
[    3.832210] ACPI: Smart Battery System [SBS0]: Battery Slot [BAT0] (battery present)
[    3.832245] ERST: Table is not found!
[    3.832548] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    3.833284] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    3.833292] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    3.833301] serial 0000:00:1f.6: PCI INT B disabled
[    3.834965] brd: module loaded
[    3.835756] loop: module loaded
[    3.836098] isapnp: Scanning for PnP cards...
[    3.841691] ata_piix 0000:00:1f.1: version 2.13
[    3.841724] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    3.841733] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    3.841741] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    3.841979] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 6
[    3.841983] PCI: setting IRQ 6 as level-triggered
[    3.841989] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 6 (level, low) -> IRQ 6
[    3.842042] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.842159] scsi0 : ata_piix
[    3.885828] scsi1 : ata_piix
[    3.887230] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    3.887236] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    3.887785] Fixed MDIO Bus: probed
[    3.887838] PPP generic driver version 2.4.2
[    3.887944] tun: Universal TUN/TAP device driver, 1.6
[    3.887947] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.888103] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.888351] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    3.888357] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[    3.888379] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.888384] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.888447] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.888484] ehci_hcd 0000:00:1d.7: debug port 1
[    3.892355] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.892532] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xe0100000
[    3.940046] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.940252] hub 1-0:1.0: USB hub found
[    3.940260] hub 1-0:1.0: 6 ports detected
[    3.940363] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.940384] uhci_hcd: USB Universal Host Controller Interface driver
[    3.940672] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 6
[    3.940678] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 6 (level, low) -> IRQ 6
[    3.940688] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.940693] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.940756] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.940785] uhci_hcd 0000:00:1d.0: irq 6, io base 0x00001820
[    3.940974] hub 2-0:1.0: USB hub found
[    3.940981] hub 2-0:1.0: 2 ports detected
[    3.941269] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
[    3.941275] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 6 (level, low) -> IRQ 6
[    3.941284] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.941289] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.941352] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.941377] uhci_hcd 0000:00:1d.1: irq 6, io base 0x00001840
[    3.941557] hub 3-0:1.0: USB hub found
[    3.941563] hub 3-0:1.0: 2 ports detected
[    3.941634] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 6 (level, low) -> IRQ 6
[    3.941643] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.941647] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.941695] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.941721] uhci_hcd 0000:00:1d.2: irq 6, io base 0x00001860
[    3.941901] hub 4-0:1.0: USB hub found
[    3.941907] hub 4-0:1.0: 2 ports detected
[    3.942060] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOU2] at 0x60,0x64 irq 1,12
[    3.944664] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.945633] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.945645] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.945686] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.945717] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.945753] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.945912] mice: PS/2 mouse device common for all mice
[    3.946171] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    3.946191] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    3.946391] device-mapper: uevent: version 1.0.3
[    3.946585] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    3.946662] device-mapper: multipath: version 1.1.1 loaded
[    3.946666] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.946855] EISA: Probing bus 0 at eisa.0
[    3.946865] Cannot allocate resource for EISA slot 1
[    3.946869] Cannot allocate resource for EISA slot 2
[    3.946872] Cannot allocate resource for EISA slot 3
[    3.946895] EISA: Detected 0 cards.
[    3.947005] cpuidle: using governor ladder
[    3.947084] cpuidle: using governor menu
[    3.947536] TCP cubic registered
[    3.947769] NET: Registered protocol family 10
[    3.948345] lo: Disabled Privacy Extensions
[    3.948691] NET: Registered protocol family 17
[    3.948775] ACPI Exception: AE_NOT_FOUND, Evaluating _PSS (20100428/processor_perflib-322)
[    3.948789] Using IPI No-Shortcut mode
[    3.948950] PM: Resume from disk failed.
[    3.948967] registered taskstats version 1
[    3.949213]   Magic number: 6:60:972
[    3.949338] rtc_cmos 00:01: setting system clock to 2010-12-14 05:58:39 UTC (1292306319)
[    3.949343] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.949346] EDD information not available.
[    4.124075] hub 2-0:1.0: over-current change on port 1
[    4.124436] ata2.01: NODEV after polling detection
[    4.168026] ata1.00: ATA-6: HTS424040M9AT00, MA2OA71A, max UDMA/100
[    4.168031] ata1.00: 78140160 sectors, multi 16: LBA48 
[    4.168567] ata2.00: ATAPI: UJDA760 DVD/CDRW, 1.00, max UDMA/33
[    4.212536] isapnp: No Plug & Play device found
[    4.212647] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.213573] ata2.00: configured for UDMA/33
[    4.213754] ata1.00: configured for UDMA/100
[    4.213958] scsi 0:0:0:0: Direct-Access     ATA      HTS424040M9AT00  MA2O PQ: 0 ANSI: 5
[    4.214179] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.214402] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    4.214472] sd 0:0:0:0: [sda] Write Protect is off
[    4.214476] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.214507] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.214709]  sda:
[    4.215733] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA760 DVD/CDRW 1.00 PQ: 0 ANSI: 5
[    4.218807] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.218812] Uniform CD-ROM driver Revision: 3.20
[    4.218962] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.219050] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.228053] hub 2-0:1.0: over-current change on port 2
[    4.229519]  sda1 sda2 < sda5 >
[    4.251728] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.251748] Freeing unused kernel memory: 684k freed
[    4.252424] Write protecting the kernel text: 4932k
[    4.252484] Write protecting the kernel read-only data: 1976k
[    4.279977] udev[68]: starting version 163
[    4.632782] b44 0000:02:02.0: PCI INT A -> Link[LNKD] -> GSI 6 (level, low) -> IRQ 6
[    4.652068] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
[    4.652075] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[    4.652082] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
[    4.684043] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    4.692232] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    4.692527] b44: b44.c:v2.0
[    4.713155] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:c0:9f:66:31:09
[    4.848809] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    4.848818] EXT4-fs (sda1): write access will be enabled during recovery
[    4.892158] usbcore: registered new interface driver hiddev
[    4.907679] input: HID 0566:3002 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input4
[    4.908524] generic-usb 0003:0566:3002.0001: input,hidraw0: USB HID v1.10 Keyboard [HID 0566:3002] on usb-0000:00:1d.1-2/input0
[    4.947725] input: HID 0566:3002 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input5
[    4.948378] generic-usb 0003:0566:3002.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [HID 0566:3002] on usb-0000:00:1d.1-2/input1
[    4.948621] usbcore: registered new interface driver usbhid
[    4.948625] usbhid: USB HID core driver
[    5.084072] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    5.277935] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input6
[    5.278748] generic-usb 0003:046D:C018.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[    5.278835] hub 1-0:1.0: over-current change on port 1
[    5.380056] hub 1-0:1.0: over-current change on port 2
[    5.665772] EXT4-fs (sda1): recovery complete
[    5.666390] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   24.638908] Adding 1533948k swap on /dev/sda5.  Priority:-1 extents:1 across:1533948k 
[   24.697406] udev[309]: starting version 163
[   25.016190] intel_rng: FWH not detected
[   25.083317] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.098943] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   25.099227] acpi device:04: registered as cooling_device3
[   25.099378] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input7
[   25.099469] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   25.361931] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   25.408442] Linux agpgart interface v0.103
[   25.487528] lp: driver loaded but no devices found
[   25.608225] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   25.608473] agpgart-intel 0000:00:00.0: detected 16252K stolen memory
[   25.637827] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[   25.643548] yenta_cardbus 0000:02:06.0: CardBus bridge found [1025:0064]
[   25.643566] yenta_cardbus 0000:02:06.0: Enabling burst memory read transactions
[   25.643571] yenta_cardbus 0000:02:06.0: Using CSCINT to route CSC interrupts to PCI
[   25.643574] yenta_cardbus 0000:02:06.0: Routing CardBus interrupts to PCI
[   25.643580] yenta_cardbus 0000:02:06.0: TI: mfunc 0x01a21b22, devctl 0x64
[   25.817362] type=1400 audit(1292327941.366:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=579 comm="apparmor_parser"
[   25.818253] type=1400 audit(1292327941.366:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=579 comm="apparmor_parser"
[   25.818754] type=1400 audit(1292327941.366:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=579 comm="apparmor_parser"
[   25.909371] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x08b8, PCI irq 10
[   25.909377] yenta_cardbus 0000:02:06.0: Socket status: 30000006
[   25.909383] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   25.909399] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge window: [io  0x3000-0x3fff]
[   25.909404] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x381f
[   25.922173] ip_tables: (C) 2000-2006 Netfilter Core Team
[   25.923446] 
[   25.923453] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge window: [mem 0xe0200000-0xe05fffff]
[   25.923461] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe0200000-0xe05fffff: excluding 0xe0200000-0xe023ffff
[   25.923480] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge window: [mem 0x20000000-0x25ffffff pref]
[   25.923485] pcmcia_socket pcmcia_socket0: cs: memory probe 0x20000000-0x25ffffff: excluding 0x20000000-0x25ffffff
[   26.109021] [drm] Initialized drm 1.1.0 20060810
[   26.142412] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1c0-0x1cf 0x1f0-0x1f7 0x370-0x377
[   26.144107] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   26.144830] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   26.145432] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   26.146090] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xdc000-0xfffff
[   26.146169] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   26.146246] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   26.146328] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   26.198107] nf_conntrack version 0.5.0 (7675 buckets, 30700 max)
[   26.200791] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   26.200798] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   26.200801] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   26.304070] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000/0x0
[   26.384784] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   26.422041] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.570466] i915 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 6 (level, low) -> IRQ 6
[   26.570476] i915 0000:00:02.0: setting latency timer to 64
[   26.598314] [drm] set up 15M of stolen space
[   26.720755] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   26.844561] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   26.845054] [drm] initialized overlay support
[   27.303122] type=1400 audit(1292327942.850:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=888 comm="apparmor_parser"
[   27.307355] type=1400 audit(1292327942.854:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=889 comm="apparmor_parser"
[   27.308553] type=1400 audit(1292327942.858:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=889 comm="apparmor_parser"
[   27.309055] type=1400 audit(1292327942.858:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=889 comm="apparmor_parser"
[   27.323884] type=1400 audit(1292327942.870:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=890 comm="apparmor_parser"
[   27.335954] type=1400 audit(1292327942.882:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=890 comm="apparmor_parser"
[   27.343598] type=1400 audit(1292327942.890:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=890 comm="apparmor_parser"
[   27.380258] Skipping EDID probe due to cached edid
[   27.663579] Console: switching to colour frame buffer device 160x50
[   27.670078] fb0: inteldrmfb frame buffer device
[   27.670080] drm: registered panic notifier
[   27.670096] Slow work thread pool: Starting up
[   27.670168] Slow work thread pool: Ready
[   27.670183] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   27.670470] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   27.670507] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   27.910488] Skipping EDID probe due to cached edid
[   27.988065] intel8x0_measure_ac97_clock: measured 53168 usecs (2562 samples)
[   27.988071] intel8x0: clocking to 48000
[   28.184285] ppdev: user-space parallel port driver
[   29.816188] b44 ssb0:0: eth0: Link is up at 100 Mbps, full duplex
[   29.816194] b44 ssb0:0: eth0: Flow control is off for TX and off for RX
[   29.816295] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   30.784144] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   32.493526] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   39.872020] eth0: no IPv6 routers present
[  180.040100] hub 2-0:1.0: over-current change on port 2
[  190.690233] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[  192.148041] hub 2-0:1.0: over-current change on port 2
[  192.601943] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  199.065784] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[  199.572034] hub 2-0:1.0: over-current change on port 2
[  201.131141] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  214.025726] [UFW BLOCK] IN=eth0 OUT= MAC=00:c0:9f:66:31:09:00:24:01:dd:78:15:08:00 SRC=67.195.141.201 DST=192.168.0.105 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=65376 DF PROTO=TCP SPT=80 DPT=48037 WINDOW=40 RES=0x00 ACK FIN URGP=0 
[  214.760264] [UFW BLOCK] IN=eth0 OUT= MAC=00:c0:9f:66:31:09:00:24:01:dd:78:15:08:00 SRC=216.115.107.206 DST=192.168.0.105 LEN=52 TOS=0x00 PREC=0x00 TTL=49 ID=35569 DF PROTO=TCP SPT=80 DPT=43376 WINDOW=40 RES=0x00 ACK FIN URGP=0 
[  223.392591] [UFW BLOCK] IN=eth0 OUT= MAC=00:c0:9f:66:31:09:00:24:01:dd:78:15:08:00 SRC=67.195.141.201 DST=192.168.0.105 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=65377 DF PROTO=TCP SPT=80 DPT=48037 WINDOW=40 RES=0x00 ACK FIN URGP=0 
[  348.276115] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[  350.140054] hub 2-0:1.0: over-current change on port 2
[  350.653141] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
bunnyg@bunnyg-TravelMate-2300:~$

---

### Post by Hippytaff on 2010-12-14
code tags :-)
```

this is my output for dmesg

[    0.184840] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.184847] pci 0000:00:1d.7: PME# disabled
[    0.184931] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH4 ACPI/GPIO/TCO
[    0.184936] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH4 GPIO
[    0.184959] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.184966] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.184974] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.184981] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.184989] pci 0000:00:1f.1: reg 20: [io  0x1810-0x181f]
[    0.184997] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.185045] pci 0000:00:1f.3: reg 20: [io  0x1880-0x189f]
[    0.185085] pci 0000:00:1f.5: reg 10: [io  0x1c00-0x1cff]
[    0.185092] pci 0000:00:1f.5: reg 14: [io  0x18c0-0x18ff]
[    0.185099] pci 0000:00:1f.5: reg 18: [mem 0xe0100c00-0xe0100dff]
[    0.185107] pci 0000:00:1f.5: reg 1c: [mem 0xe0100800-0xe01008ff]
[    0.185135] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.185140] pci 0000:00:1f.5: PME# disabled
[    0.185165] pci 0000:00:1f.6: reg 10: [io  0x2400-0x24ff]
[    0.185172] pci 0000:00:1f.6: reg 14: [io  0x2000-0x207f]
[    0.185208] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.185213] pci 0000:00:1f.6: PME# disabled
[    0.185253] pci 0000:02:02.0: reg 10: [mem 0xe0200000-0xe0201fff]
[    0.185278] pci 0000:02:02.0: reg 30: [mem 0x00000000-0x00003fff pref]
[    0.185295] pci 0000:02:02.0: supports D1 D2
[    0.185298] pci 0000:02:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.185303] pci 0000:02:02.0: PME# disabled
[    0.185330] pci 0000:02:04.0: reg 10: [io  0x3800-0x381f]
[    0.185338] pci 0000:02:04.0: reg 14: [mem 0xe0203800-0xe020381f]
[    0.185345] pci 0000:02:04.0: reg 18: [mem 0xe0203000-0xe02037ff]
[    0.185377] pci 0000:02:04.0: supports D2
[    0.185406] pci 0000:02:06.0: reg 10: [mem 0xe0202000-0xe0202fff]
[    0.185424] pci 0000:02:06.0: supports D1 D2
[    0.185427] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.185432] pci 0000:02:06.0: PME# disabled
[    0.185473] pci 0000:00:1e.0: PCI bridge to [bus 02-02] (subtractive decode)
[    0.185479] pci 0000:00:1e.0:   bridge window [io  0x3000-0x3fff]
[    0.185485] pci 0000:00:1e.0:   bridge window [mem 0xe0200000-0xe05fffff]
[    0.185491] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.185495] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.185499] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.185535] pci_bus 0000:03: [bus 03-06] partially hidden behind transparent bridge 0000:02 [bus 02-02]
[    0.185545] pci_bus 0000:00: on NUMA node 0
[    0.185551] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.185772] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.189413] ACPI: PCI Interrupt Link [LNKA] (IRQs *6)
[    0.189541] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    0.189666] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[    0.189790] ACPI: PCI Interrupt Link [LNKD] (IRQs *6)
[    0.189921] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[    0.190045] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[    0.190169] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *0, disabled.
[    0.190296] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[    0.190347] HEST: Table is not found!
[    0.190466] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=  none
[    0.190479] vgaarb: loaded
[    0.190722] SCSI subsystem initialized
[    0.190814] libata version 3.00 loaded.
[    0.190906] usbcore: registered new interface driver usbfs
[    0.190925] usbcore: registered new interface driver hub
[    0.190959] usbcore: registered new device driver usb
[    0.191147] ACPI: WMI: Mapper loaded
[    0.191151] PCI: Using ACPI for IRQ routing
[    0.191184] PCI: pci_cache_line_size set to 64 bytes
[    0.191258] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.191262] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.191266] reserve RAM buffer: 000000001eee0000 - 000000001fffffff 
[    0.191412] NetLabel: Initializing
[    0.191415] NetLabel:  domain hash size = 128
[    0.191418] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.191436] NetLabel:  unlabeled traffic allowed by default
[    0.191501] Switching to clocksource tsc
[    0.203999] AppArmor: AppArmor Filesystem Enabled
[    0.204034] pnp: PnP ACPI init
[    0.204077] ACPI: bus type pnp registered
[    0.205162] ERROR: Unable to locate IOAPIC for GSI 8
[    0.205225] ERROR: Unable to locate IOAPIC for GSI 13
[    0.206020] ERROR: Unable to locate IOAPIC for GSI 1
[    0.206177] ERROR: Unable to locate IOAPIC for GSI 12
[    0.206516] pnp: PnP ACPI: found 8 devices
[    0.206520] ACPI: ACPI bus type pnp unregistered
[    0.206525] PnPBIOS: Disabled by ACPI PNP
[    0.206546] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.206553] system 00:04: [io  0x0600-0x060f] has been reserved
[    0.206557] system 00:04: [io  0x0700-0x070f] has been reserved
[    0.206561] system 00:04: [io  0x0800-0x080f] has been reserved
[    0.206565] system 00:04: [io  0x1000-0x107f] has been reserved
[    0.206569] system 00:04: [io  0x1180-0x11bf] has been reserved
[    0.206573] system 00:04: [io  0x01c0-0x01cf] has been reserved
[    0.206578] system 00:04: [io  0xfe00] has been reserved
[    0.206582] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.206586] system 00:04: [io  0x0610-0x061f] has been reserved
[    0.206593] system 00:04: [mem 0xfec10000-0xfec1ffff] has been reserved
[    0.206597] system 00:04: [mem 0xff800000-0xffbfffff] has been reserved
[    0.206602] system 00:04: [mem 0xfff00000-0xffffffff] could not be reserved
[    0.206607] system 00:04: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.206611] system 00:04: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.206616] system 00:04: [mem 0x000df800-0x000dffff] could not be reserved
[    0.243420] pci 0000:00:1e.0: BAR 15: assigned [mem 0x20000000-0x25ffffff pref]
[    0.243426] pci 0000:00:1f.1: BAR 5: assigned [mem 0x26000000-0x260003ff]
[    0.243434] pci 0000:00:1f.1: BAR 5: set to [mem 0x26000000-0x260003ff] (PCI address [0x26000000-0x260003ff]
[    0.243440] pci 0000:02:06.0: BAR 15: assigned [mem 0x20000000-0x23ffffff pref]
[    0.243445] pci 0000:02:06.0: BAR 16: assigned [mem 0x28000000-0x2bffffff]
[    0.243450] pci 0000:02:02.0: BAR 6: assigned [mem 0x24000000-0x24003fff pref]
[    0.243454] pci 0000:02:06.0: BAR 13: assigned [io  0x3000-0x30ff]
[    0.243458] pci 0000:02:06.0: BAR 14: assigned [io  0x3400-0x34ff]
[    0.243462] pci 0000:02:06.0: CardBus bridge to [bus 03-06]
[    0.243466] pci 0000:02:06.0:   bridge window [io  0x3000-0x30ff]
[    0.243471] pci 0000:02:06.0:   bridge window [io  0x3400-0x34ff]
[    0.243477] pci 0000:02:06.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[    0.243482] pci 0000:02:06.0:   bridge window [mem 0x28000000-0x2bffffff]
[    0.243488] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
[    0.243493] pci 0000:00:1e.0:   bridge window [io  0x3000-0x3fff]
[    0.243500] pci 0000:00:1e.0:   bridge window [mem 0xe0200000-0xe05fffff]
[    0.243506] pci 0000:00:1e.0:   bridge window [mem 0x20000000-0x25ffffff pref]
[    0.243524] pci 0000:00:1e.0: setting latency timer to 64
[    0.243535] pci 0000:02:06.0: enabling device (0104 -> 0107)
[    0.243786] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[    0.243791] PCI: setting IRQ 10 as level-triggered
[    0.243797] pci 0000:02:06.0: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[    0.243805] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.243809] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.243813] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.243817] pci_bus 0000:02: resource 1 [mem 0xe0200000-0xe05fffff]
[    0.243821] pci_bus 0000:02: resource 2 [mem 0x20000000-0x25ffffff pref]
[    0.243824] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.243828] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.243832] pci_bus 0000:03: resource 0 [io  0x3000-0x30ff]
[    0.243835] pci_bus 0000:03: resource 1 [io  0x3400-0x34ff]
[    0.243839] pci_bus 0000:03: resource 2 [mem 0x20000000-0x23ffffff pref]
[    0.243843] pci_bus 0000:03: resource 3 [mem 0x28000000-0x2bffffff]
[    0.243902] NET: Registered protocol family 2
[    0.243999] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.244300] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.244430] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.244588] TCP: Hash tables configured (established 16384 bind 16384)
[    0.244592] TCP reno registered
[    0.244597] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.244609] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.244732] NET: Registered protocol family 1
[    0.244763] pci 0000:00:02.0: Boot video device
[    0.244858] PCI: CLS 32 bytes, default 64
[    0.244974] Simple Boot Flag at 0x37 set to 0x1
[    0.245121] cpufreq-nforce2: No nForce2 chipset.
[    0.245157] Scanning for low memory corruption every 60 seconds
[    0.245396] audit: initializing netlink socket (disabled)
[    0.245419] type=2000 audit(1292306315.244:1): initialized
[    0.261247] Trying to unpack rootfs image as initramfs...
[    0.280989] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.289113] VFS: Disk quotas dquot_6.5.2
[    0.289261] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.290369] fuse init (API version 7.14)
[    0.290524] msgmni has been set to 937
[    0.297006] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.297012] io scheduler noop registered
[    0.297015] io scheduler deadline registered
[    0.297044] io scheduler cfq registered (default)
[    0.297241] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.297272] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.297552] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.316664] ACPI: Lid Switch [LID]
[    0.316787] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.316797] ACPI: Sleep Button [SLPB]
[    0.316879] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.316884] ACPI: Power Button [PWRF]
[    0.317121] ACPI: Fan [FAN0] (off)
[    0.317264] ACPI: Fan [FAN1] (off)
[    0.317407] ACPI: acpi_idle registered with cpuidle
[    0.317456] Marking TSC unstable due to TSC halts in idle
[    0.324586] Switching to clocksource acpi_pm
[    0.352732] thermal LNXTHERM:01: registered as thermal_zone0
[    0.352750] ACPI: Thermal Zone [THRM] (25 C)
[    0.352850] ACPI: SBS HC: EC = 0xde85bba0, offset = 0x18, query_bit = 0x20
[    0.480477] ACPI: Smart Battery System [SBS0]: AC Adapter [AC0] (on-line)
[    0.703840] Freeing initrd memory: 10508k freed
[    3.832210] ACPI: Smart Battery System [SBS0]: Battery Slot [BAT0] (battery present)
[    3.832245] ERST: Table is not found!
[    3.832548] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    3.833284] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    3.833292] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    3.833301] serial 0000:00:1f.6: PCI INT B disabled
[    3.834965] brd: module loaded
[    3.835756] loop: module loaded
[    3.836098] isapnp: Scanning for PnP cards...
[    3.841691] ata_piix 0000:00:1f.1: version 2.13
[    3.841724] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    3.841733] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    3.841741] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    3.841979] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 6
[    3.841983] PCI: setting IRQ 6 as level-triggered
[    3.841989] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 6 (level, low) -> IRQ 6
[    3.842042] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.842159] scsi0 : ata_piix
[    3.885828] scsi1 : ata_piix
[    3.887230] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    3.887236] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    3.887785] Fixed MDIO Bus: probed
[    3.887838] PPP generic driver version 2.4.2
[    3.887944] tun: Universal TUN/TAP device driver, 1.6
[    3.887947] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.888103] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.888351] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    3.888357] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[    3.888379] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.888384] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.888447] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.888484] ehci_hcd 0000:00:1d.7: debug port 1
[    3.892355] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.892532] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xe0100000
[    3.940046] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.940252] hub 1-0:1.0: USB hub found
[    3.940260] hub 1-0:1.0: 6 ports detected
[    3.940363] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.940384] uhci_hcd: USB Universal Host Controller Interface driver
[    3.940672] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 6
[    3.940678] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 6 (level, low) -> IRQ 6
[    3.940688] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.940693] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.940756] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.940785] uhci_hcd 0000:00:1d.0: irq 6, io base 0x00001820
[    3.940974] hub 2-0:1.0: USB hub found
[    3.940981] hub 2-0:1.0: 2 ports detected
[    3.941269] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
[    3.941275] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 6 (level, low) -> IRQ 6
[    3.941284] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.941289] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.941352] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.941377] uhci_hcd 0000:00:1d.1: irq 6, io base 0x00001840
[    3.941557] hub 3-0:1.0: USB hub found
[    3.941563] hub 3-0:1.0: 2 ports detected
[    3.941634] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 6 (level, low) -> IRQ 6
[    3.941643] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.941647] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.941695] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.941721] uhci_hcd 0000:00:1d.2: irq 6, io base 0x00001860
[    3.941901] hub 4-0:1.0: USB hub found
[    3.941907] hub 4-0:1.0: 2 ports detected
[    3.942060] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOU2] at 0x60,0x64 irq 1,12
[    3.944664] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.945633] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.945645] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.945686] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.945717] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.945753] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.945912] mice: PS/2 mouse device common for all mice
[    3.946171] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    3.946191] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    3.946391] device-mapper: uevent: version 1.0.3
[    3.946585] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    3.946662] device-mapper: multipath: version 1.1.1 loaded
[    3.946666] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.946855] EISA: Probing bus 0 at eisa.0
[    3.946865] Cannot allocate resource for EISA slot 1
[    3.946869] Cannot allocate resource for EISA slot 2
[    3.946872] Cannot allocate resource for EISA slot 3
[    3.946895] EISA: Detected 0 cards.
[    3.947005] cpuidle: using governor ladder
[    3.947084] cpuidle: using governor menu
[    3.947536] TCP cubic registered
[    3.947769] NET: Registered protocol family 10
[    3.948345] lo: Disabled Privacy Extensions
[    3.948691] NET: Registered protocol family 17
[    3.948775] ACPI Exception: AE_NOT_FOUND, Evaluating _PSS (20100428/processor_perflib-322)
[    3.948789] Using IPI No-Shortcut mode
[    3.948950] PM: Resume from disk failed.
[    3.948967] registered taskstats version 1
[    3.949213]   Magic number: 6:60:972
[    3.949338] rtc_cmos 00:01: setting system clock to 2010-12-14 05:58:39 UTC (1292306319)
[    3.949343] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.949346] EDD information not available.
[    4.124075] hub 2-0:1.0: over-current change on port 1
[    4.124436] ata2.01: NODEV after polling detection
[    4.168026] ata1.00: ATA-6: HTS424040M9AT00, MA2OA71A, max UDMA/100
[    4.168031] ata1.00: 78140160 sectors, multi 16: LBA48 
[    4.168567] ata2.00: ATAPI: UJDA760 DVD/CDRW, 1.00, max UDMA/33
[    4.212536] isapnp: No Plug & Play device found
[    4.212647] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.213573] ata2.00: configured for UDMA/33
[    4.213754] ata1.00: configured for UDMA/100
[    4.213958] scsi 0:0:0:0: Direct-Access     ATA      HTS424040M9AT00  MA2O PQ: 0 ANSI: 5
[    4.214179] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.214402] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    4.214472] sd 0:0:0:0: [sda] Write Protect is off
[    4.214476] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.214507] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.214709]  sda:
[    4.215733] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA760 DVD/CDRW 1.00 PQ: 0 ANSI: 5
[    4.218807] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.218812] Uniform CD-ROM driver Revision: 3.20
[    4.218962] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.219050] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.228053] hub 2-0:1.0: over-current change on port 2
[    4.229519]  sda1 sda2 < sda5 >
[    4.251728] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.251748] Freeing unused kernel memory: 684k freed
[    4.252424] Write protecting the kernel text: 4932k
[    4.252484] Write protecting the kernel read-only data: 1976k
[    4.279977] udev[68]: starting version 163
[    4.632782] b44 0000:02:02.0: PCI INT A -> Link[LNKD] -> GSI 6 (level, low) -> IRQ 6
[    4.652068] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
[    4.652075] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[    4.652082] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
[    4.684043] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    4.692232] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    4.692527] b44: b44.c:v2.0
[    4.713155] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:c0:9f:66:31:09
[    4.848809] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    4.848818] EXT4-fs (sda1): write access will be enabled during recovery
[    4.892158] usbcore: registered new interface driver hiddev
[    4.907679] input: HID 0566:3002 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input4
[    4.908524] generic-usb 0003:0566:3002.0001: input,hidraw0: USB HID  v1.10 Keyboard [HID 0566:3002] on usb-0000:00:1d.1-2/input0
[    4.947725] input: HID 0566:3002 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input5
[    4.948378] generic-usb 0003:0566:3002.0002: input,hiddev96,hidraw1:  USB HID v1.10 Device [HID 0566:3002] on usb-0000:00:1d.1-2/input1
[    4.948621] usbcore: registered new interface driver usbhid
[    4.948625] usbhid: USB HID core driver
[    5.084072] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    5.277935] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input6
[    5.278748] generic-usb 0003:046D:C018.0003: input,hidraw2: USB HID  v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[    5.278835] hub 1-0:1.0: over-current change on port 1
[    5.380056] hub 1-0:1.0: over-current change on port 2
[    5.665772] EXT4-fs (sda1): recovery complete
[    5.666390] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   24.638908] Adding 1533948k swap on /dev/sda5.  Priority:-1 extents:1 across:1533948k 
[   24.697406] udev[309]: starting version 163
[   25.016190] intel_rng: FWH not detected
[   25.083317] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.098943] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   25.099227] acpi device:04: registered as cooling_device3
[   25.099378] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input7
[   25.099469] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   25.361931] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   25.408442] Linux agpgart interface v0.103
[   25.487528] lp: driver loaded but no devices found
[   25.608225] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   25.608473] agpgart-intel 0000:00:00.0: detected 16252K stolen memory
[   25.637827] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[   25.643548] yenta_cardbus 0000:02:06.0: CardBus bridge found [1025:0064]
[   25.643566] yenta_cardbus 0000:02:06.0: Enabling burst memory read transactions
[   25.643571] yenta_cardbus 0000:02:06.0: Using CSCINT to route CSC interrupts to PCI
[   25.643574] yenta_cardbus 0000:02:06.0: Routing CardBus interrupts to PCI
[   25.643580] yenta_cardbus 0000:02:06.0: TI: mfunc 0x01a21b22, devctl 0x64
[   25.817362] type=1400 audit(1292327941.366:2): apparmor="STATUS"  operation="profile_load" name="/sbin/dhclient3" pid=579  comm="apparmor_parser"
[   25.818253] type=1400 audit(1292327941.366:3): apparmor="STATUS"  operation="profile_load"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=579  comm="apparmor_parser"
[   25.818754] type=1400 audit(1292327941.366:4): apparmor="STATUS"  operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script"  pid=579 comm="apparmor_parser"
[   25.909371] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x08b8, PCI irq 10
[   25.909377] yenta_cardbus 0000:02:06.0: Socket status: 30000006
[   25.909383] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   25.909399] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge window: [io  0x3000-0x3fff]
[   25.909404] pcmcia_socket pcmcia_socket0: cs: IO port probe  0x3000-0x3fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x381f
[   25.922173] ip_tables: (C) 2000-2006 Netfilter Core Team
[   25.923446] 
[   25.923453] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge window: [mem 0xe0200000-0xe05fffff]
[   25.923461] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe0200000-0xe05fffff: excluding 0xe0200000-0xe023ffff
[   25.923480] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge window: [mem 0x20000000-0x25ffffff pref]
[   25.923485] pcmcia_socket pcmcia_socket0: cs: memory probe 0x20000000-0x25ffffff: excluding 0x20000000-0x25ffffff
[   26.109021] [drm] Initialized drm 1.1.0 20060810
[   26.142412] pcmcia_socket pcmcia_socket0: cs: IO port probe  0x100-0x3af: excluding 0x170-0x177 0x1c0-0x1cf 0x1f0-0x1f7 0x370-0x377
[   26.144107] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   26.144830] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   26.145432] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   26.146090] pcmcia_socket pcmcia_socket0: cs: memory probe  0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff  0xdc000-0xfffff
[   26.146169] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   26.146246] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   26.146328] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   26.198107] nf_conntrack version 0.5.0 (7675 buckets, 30700 max)
[   26.200791] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   26.200798] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   26.200801] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   26.304070] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000/0x0
[   26.384784] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   26.422041] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.570466] i915 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 6 (level, low) -> IRQ 6
[   26.570476] i915 0000:00:02.0: setting latency timer to 64
[   26.598314] [drm] set up 15M of stolen space
[   26.720755] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   26.844561] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:  owns=io+mem
[   26.845054] [drm] initialized overlay support
[   27.303122] type=1400 audit(1292327942.850:5): apparmor="STATUS"  operation="profile_load" name="/usr/share/gdm/guest-session/Xsession"  pid=888 comm="apparmor_parser"
[   27.307355] type=1400 audit(1292327942.854:6): apparmor="STATUS"  operation="profile_replace" name="/sbin/dhclient3" pid=889  comm="apparmor_parser"
[   27.308553] type=1400 audit(1292327942.858:7): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=889  comm="apparmor_parser"
[   27.309055] type=1400 audit(1292327942.858::cool:: apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=889 comm="apparmor_parser"
[   27.323884] type=1400 audit(1292327942.870:9): apparmor="STATUS"  operation="profile_load" name="/usr/bin/evince" pid=890  comm="apparmor_parser"
[   27.335954] type=1400 audit(1292327942.882:10): apparmor="STATUS"  operation="profile_load" name="/usr/bin/evince-previewer" pid=890  comm="apparmor_parser"
[   27.343598] type=1400 audit(1292327942.890:11): apparmor="STATUS"  operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=890  comm="apparmor_parser"
[   27.380258] Skipping EDID probe due to cached edid
[   27.663579] Console: switching to colour frame buffer device 160x50
[   27.670078] fb0: inteldrmfb frame buffer device
[   27.670080] drm: registered panic notifier
[   27.670096] Slow work thread pool: Starting up
[   27.670168] Slow work thread pool: Ready
[   27.670183] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   27.670470] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   27.670507] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   27.910488] Skipping EDID probe due to cached edid
[   27.988065] intel8x0_measure_ac97_clock: measured 53168 usecs (2562 samples)
[   27.988071] intel8x0: clocking to 48000
[   28.184285] ppdev: user-space parallel port driver
[   29.816188] b44 ssb0:0: eth0: Link is up at 100 Mbps, full duplex
[   29.816194] b44 ssb0:0: eth0: Flow control is off for TX and off for RX
[   29.816295] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   30.784144] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   32.493526] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   39.872020] eth0: no IPv6 routers present
[  180.040100] hub 2-0:1.0: over-current change on port 2
[  190.690233] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[  192.148041] hub 2-0:1.0: over-current change on port 2
[  192.601943] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  199.065784] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[  199.572034] hub 2-0:1.0: over-current change on port 2
[  201.131141] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  214.025726] [UFW BLOCK] IN=eth0 OUT=  MAC=00:c0:9f:66:31:09:00:24:01:dd:78:15:08:00 SRC=67.195.141.201  DST=192.168.0.105 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=65376 DF PROTO=TCP  SPT=80 DPT=48037 WINDOW=40 RES=0x00 ACK FIN URGP=0 
[  214.760264] [UFW BLOCK] IN=eth0 OUT=  MAC=00:c0:9f:66:31:09:00:24:01:dd:78:15:08:00 SRC=216.115.107.206  DST=192.168.0.105 LEN=52 TOS=0x00 PREC=0x00 TTL=49 ID=35569 DF PROTO=TCP  SPT=80 DPT=43376 WINDOW=40 RES=0x00 ACK FIN URGP=0 
[  223.392591] [UFW BLOCK] IN=eth0 OUT=  MAC=00:c0:9f:66:31:09:00:24:01:dd:78:15:08:00 SRC=67.195.141.201  DST=192.168.0.105 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=65377 DF PROTO=TCP  SPT=80 DPT=48037 WINDOW=40 RES=0x00 ACK FIN URGP=0 
[  348.276115] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[  350.140054] hub 2-0:1.0: over-current change on port 2
[  350.653141] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
bunnyg@bunnyg-TravelMate-2300:~$
```

do [code]text[/code ] to do that :-) easier to read

---

### Post by wep940 on 2010-12-14
See:  [http://ubuntuforums.org/showthread.php?t=1640997](http://ubuntuforums.org/showthread.php?t=1640997)  - they have the same adapter - IPN2220.
 
Remember:  ndiswrapper/ndisgtk -> must be Windows XP drivers only; must match type -> 32 bit or 64 bit to OS type

---

### Post by jackwilson on 2010-12-16
[COLOR=Red]Entered this[/COLOR]

sudo lshw -C network
[COLOR=Red]Got this[/COLOR]

bunnyg@bunnyg-TravelMate-2300:~$ sudo lshw -C network
[sudo] password for bunnyg: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:66:31:09
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.105 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:6 memory:e0200000-e0201fff memory:24000000-24003fff
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: IPN 2220 802.11g
       vendor: InProComm Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=32 mingnt=32
       resources: ioport:3800(size=32) memory:e0203800-e020381f memory:e0203000-e02037ff
bunnyg@bunnyg-TravelMate-2300:~$ 

[COLOR=Red]Have tried at least 15 drivers that are supposed to be the one for my card. Invalid driver is the response every time[/COLOR].
Until I have the correct driver nothing seems to work.
Someone said that the kernel might be included in ndiswrapper, I do not now how to install that kernel as my driver.

---

### Post by Hippytaff on 2010-12-16
Ignore what was originally here if you read it.

---

### Post by wep940 on 2010-12-16
As I noted in my previous response, your wireless is the IPN2220, *NOT* Broadcom. The Broadcom entry is for the normal cabled ethernet controller, the wireless is, from your own list:
 
*-network:1 UNCLAIMED
description: Ethernet controller
product: IPN 2220 802.11g
vendor: InProComm Inc.
 
So, for ANYTHING you've done in regards to Broadcom you need to reverse all of it to get back to a clean starting point.
 
From there, look at the link I pointed you to, do a search on the forum for IPN2220, or a web search for "linux and ipn220 and driver" to see more help.
 
In the thread pointed to earlier by another poster, you can see where anewguy got you going with this.  Be sure you are using IPN drivers for Windows XP, that match your OS type (32 or 64 bit) and follow his instructions for reversing anything you may have done before trying again.  Remember:  ndiswrapper AND ndisgtk.  And no, don't worry about the kernel.

---

### Post by jackwilson on 2010-12-17
Rather than undue everything I re-installed Ubuntu10.10 OS, and I installed ndiswrapper from synaptic package manager.
The one thing that anewguy said to do that I do not have is the correct IPN2220 inf file to install. I did have the correct one the last time I had my wireless working, but I do not know where I downloaded the driver that worked from. That's the part of this that I need help finding.

---

### Post by Hippytaff on 2010-12-17
You should be able to get the driver from the manufacturer's website, or do a google search for  IPN2220

---

### Post by walt.smith1960 on 2010-12-18
A complication I see here is that InProComm is not listed as a vendor for that model on Acer's Americas site.  Acer's  lists Ambit, Atheros and Intel for the TravelMate2300.  No InProComm.  I'd never heard of this manufacturer and googled. It seems they're out of business and if Acer's site doesn't mention them it may be a challenge to find the proper driver.  I found it easier to not "fight city hall" and just bought a mini-USB WiFi adapter that works with minimal fussing.

---

### Post by wep940 on 2010-12-18
If you installed ndiswrapper, be *SURE* to install ndisgtk as well.  It takes away all of the command line typing, file editing, modprobing, etc., that you would have to do if you just used ndiswrapper - in other words, it's far simpler, works great, and takes away the possibilities for typos and typos are your worse enemy when using ndiswrapper as you won't get errors, it just won't work.
 
If you can't find the driver, just contact the OP on the thread I pointed you to.  They obviously have the correct one as it is working.
 
As for the IPN stuff being available, a basic search on the net turns up all kinds of solutions for Linux.

---

### Post by jackwilson on 2010-12-20
When, and if I find the correct driver is there anything else I need to do besides System>Administration>Windows Wireless Driver- install new driver?
Every driver I've tried to install at this point says Invalid Driver

---

### Post by wep940 on 2010-12-20
You always need to back out anything that failed - so go to the command line and type:
 
ndiswrapper -l (lower case "L")
 
If it returns anything:
 
sudo ndiswrapper -e <device name>
 
Repeat until no devices are returned.
 
You also need to back out any changes you may have made to such things as the blacklist file, the modules file, etc..

---

### Post by wep940 on 2010-12-20
I did a net search using:
 
windows xp ipn2220 driver
 
and it returned a lot of results.  Here are just a few.  Have you tried these??
 
downloads.com has the windows xp 64-bit drivers and several acer ipn2220 drivers as well.
 
 
[http://forums.laptopvideo2go.com/topic/7172-inprocomm-latest-driver/](http://forums.laptopvideo2go.com/topic/7172-inprocomm-latest-driver/)
 
[http://members.driverguide.com/driver/detail.php?driverid=881505](http://members.driverguide.com/driver/detail.php?driverid=881505)
 
[http://yournewdriver.com/acer_IPN2220_Wireless_LAN_Card_4670.htm](http://yournewdriver.com/acer_IPN2220_Wireless_LAN_Card_4670.htm)
 
[http://support.acer-euro.com/drivers/notebook/tm_4000.html](http://support.acer-euro.com/drivers/notebook/tm_4000.html)
 
[http://www.wireless-driver.com/tag/inprocomm/](http://www.wireless-driver.com/tag/inprocomm/)
 
The list goes on.  Remember that you don't necessarily need the driver associated with the maker of your PC - as long as it works with the chipset you should try it.  As always, if one fails, back it out.
 
Also:
 
- remember to check in network manager to be "Enable Wireless" is checked and enabled
 
- any encryption and keys must be used
 
- if MAC filtering is used, the PC's MAC must be in the routers' table

---

### Post by wep940 on 2010-12-21
I don't know what Acer site you were looking at, but all I did was a net search for:
 
acer travelmate 2300
 
And the following was the 2nd on the list and HAS the driver (IPN2220) for your adapter:
 
[http://support.acer-euro.com/drivers/notebook/tm_2300.html](http://support.acer-euro.com/drivers/notebook/tm_2300.html)

---

### Post by jackwilson on 2010-12-27
p { margin-bottom: 0.08in; }  Here is sudo lshw -C network  in my next post as requested. I also did sudo ndiswrapper -l ,  dmesg, and iwconfig, if you continue to read down this post.
 

 

 bunny@localhost:~$ sudo lshw -C network 
 [sudo] password for bunny:  
   *-network:0              
        description: Ethernet interface 
        product: BCM4401 100Base-T 
        vendor: Broadcom Corporation 
        physical id: 2 
        bus info: pci@0000:02:02.0 
        logical name: eth0 
        version: 01 
        serial: 00:c0:9f:66:31:09 
        size: 100MB/s 
        capacity: 100MB/s 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.105 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s 
        resources: irq:6 memory:e0200000-e0201fff memory:24000000-24003fff 
   *-network:1 UNCLAIMED 
        description: Ethernet controller 
        product: IPN 2220 802.11g 
        vendor: InProComm Inc. 
        physical id: 4 
        bus info: pci@0000:02:04.0 
        version: 00 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm bus_master cap_list 
        configuration: latency=64 maxlatency=32 mingnt=32 
        resources: ioport:3800(size=32) memory:e0203800-e020381f memory:e0203000-e02037ff 
 bunny@localhost:~$  
 

        I think I found a driver that will work. At least it doesn't say invalid driver. When I open wireless driver it says neti2220 present yes.
 

 _**In**_ terminal sudo ndiswrapper -l  says:
 

 

 bunny@localhost:~$ sudo ndiswrapper -l 
 [sudo] password for bunny:  
 neti2220 : driver installed 
     device (17FE:2220) present
 

 _**In**_ the dmesg list it says _**Windows driver is not 32-bit;**_
 

 [   30.501533] ADDRCONF(NETDEV_UP): eth0: link is not ready 
 [   30.565440] ndiswrapper (check_nt_hdr:147): kernel is 32-bit, but _**Windows driver is not 32-bit;**_bad magic: 020B 
 [   30.565449] ndiswrapper (load_sys_files:206): couldn't prepare driver 'neti2220' 
 [   30.566069] ndiswrapper (load_wrap_driver:108): couldn't load driver neti2220; check system log for messages from 'loadndisdriver' 
 

 

 _**In**_  iwconfig it says:
 

 bunny@localhost:~$ iwconfig 
 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 sit0      no wireless extensions.
 

 _**Network**_ Manager says:  
 

 No wireless networks found.
 

 My question is will I be able to get my wireless working and how do I do that?

[B]Since I posted this I removed the 64 bit driver and installed a different one. This one said that it was correct and the light for my wireless started flashing, but it still says that there are no wireless networks found. My working D-Link hub is two feet from my PC and I know it is working. My xnetcardconfig system tool says my wireless is configured, so I am at a loss as to what else I need to do for my PC and My D-Link to see each other
[/B]

---

### Post by jackwilson on 2010-12-29
> **cariboo907 said:**
> Unless your system is bleeding edge new, there probably already is a driver for your wireless device included in the kernel. Could you paste the output of:

```
sudo lshw -C network
```in your next post.

[COLOR=Blue][B]Something still must not be installed, or configured correctly.  Is there something else I need to do to have my PC and D-link router see each other?
When I installed this last driver the light that flashes when the wireless system is locating and connecting to the router came on, so I disconnected the wired connection and the network manager said no wireless networks found. Then the light quit flashing, so I removed the driver and reinstalled it to see if the light would flash again but it did not.

[/B][/COLOR][COLOR=Blue][B]Could the items below in [COLOR=Red]red text [COLOR=Blue]be what's preventing the connection to be seen?
What do I need to do to correct these and/ or finish installation of additional software?
Like enabling the disabled, and turn on TX and RX what ever those are? So that etho: link is ready.

Thanks again,
jackwilson
[/COLOR][/COLOR][COLOR=Black]
[/COLOR][/B][/COLOR][COLOR=Blue]**This driver **[/COLOR][COLOR=Blue]**I found**[/COLOR][COLOR=Blue]** says present yes, but terminal says:**[/COLOR]
[COLOR=Blue][B][COLOR=Black] [   31.315565] IPv6 over IPv4 tunneling driver
[COLOR=Red][   31.317114] sit0: Disabled Privacy Extensions[/COLOR]
[   32.816204] b44 ssb0:0: eth0: Link is up at 100 Mbps, full duplex
[COLOR=Red][   32.816211] b44 ssb0:0: eth0: Flow control is off for TX and off for RX[/COLOR]
[   32.816323] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   36.136591] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  233.130963] b44 ssb0:0: eth0: powering down PHY
[COLOR=Red][  233.142349] ADDRCONF(NETDEV_UP): eth0: link is not ready[/COLOR]
[  235.337454] b44 ssb0:0: eth0: powering down PHY
[  235.347144] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  235.378534] b44 ssb0:0: eth0: powering down PHY
[/COLOR][COLOR=Black][  235.406226] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  238.816199] b44 ssb0:0: eth0: Link is up at 100 Mbps, full duplex
[  238.816206] b44 ssb0:0: eth0: Flow control is off for TX and off for RX
[  238.816319] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  241.866447] b44 ssb0:0: eth0: powering down PHY
[  241.874227] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  244.816195] b44 ssb0:0: eth0: Link is up at 100 Mbps, full duplex
[  244.816202] b44 ssb0:0: eth0: Flow control is off for TX and off for RX
[  244.816317] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[COLOR=Red][  403.176098] lo: Disabled Privacy Extensions
[  403.178049] sit0: Disabled Privacy Extensions[/COLOR]
bunny@localhost:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[COLOR=Red]sit0      no wireless extensions.[/COLOR]

bunny@localhost:~$ sudo lshw -C network
[sudo] password for bunny: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:66:31:09
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.105 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:6 memory:e0200000-e0201fff memory:24000000-24003fff
 [COLOR=Red] *-network:1 DISABLED[/COLOR]
       description: Wireless interface
       product: IPN 2220 802.11g
       vendor: InProComm Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlan0
       version: 00
       serial: 00:0e:9b:5f:09:16
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+neti2220 driverversion=1.56+LanExpress,03/29/2004,2.10. latency=64 link=no maxlatency=32 mingnt=32 multicast=yes wireless=IEEE 802.11g
       resources: irq:10 ioport:3800(size=32) memory:e0203800-e020381f memory:e0203000-e02037ff[/COLOR]

[/B][/COLOR]

---

