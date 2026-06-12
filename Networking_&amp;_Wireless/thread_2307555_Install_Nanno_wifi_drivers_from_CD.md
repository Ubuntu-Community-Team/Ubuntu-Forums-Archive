---
title: "Install Nanno wifi drivers from CD"
date: 2015-12-26
forum: Networking &amp; Wireless
---

### Post by tom219 on 2015-12-26
Hello I have recently decided to join Ubuntu for my main operating system (although I am dual booting windows 7 for some games). Yesterday I downloaded and installed the latest Ubuntu o/s and eveything went as expected. 

It seems I'm in a bit of a pickle alredy though. I currently have no internet access until my wifi drivers are installed. Ethernet is not an option because the distance from the router. So firstly I found the linux driver for the wifi adapter on the CD and found I needed to unrar it. This was not possible as I didn't have the rar installed and no internet to get it. So I ended up rebooting windows extracting the driver and booting back into Ubuntu. 

This is basically where I am now and don't really know what to do with the driver files to install them, there is no .exe or setup but just the driver files. There are no additional drivers available to install either. 

How on earth can I install my wifi drivers? 

I realise I have probably not given you enough info so please ask what else is needed. I do apologise as I am a total noob when it comes to Ubuntu. 

Any help would be really appreciated. 

Thank you

Tom

---

### Post by Bucky Ball on 2015-12-26
*Thread moved to **Networking and Wireless**.*

Welcome. People will take into account the fact you are new and you'll get better help here. 

Please open a terminal and run this for starters:

```
sudo lshw -C network
```

Paste it in and hit return. You will be asked for your password. When you type that in it will be invisible. This is normal. 

Please post the output between code tags (see last link in my signature).

---

### Post by tom219 on 2015-12-26
Thank you very much for the welcome and reply. Here is the outputted code:

```

tom@tom-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Ethernet Connection (2) I218-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 00
       serial: d0:50:99:3e:28:39
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.1-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:39 memory:f7300000-f731ffff memory:f7338000-f7338fff ioport:f040(size=32)
tom@tom-desktop:~$ 

```

---

### Post by Bucky Ball on 2015-12-26
Is this a USB wireless adapter? If so, please plug it in and run the command again. If you had it plugged in, perhaps show us the result of:

```
lsusb
```

If it is an internal wireless card, oddly, it is not showing up in your output. :-k

---

### Post by tom219 on 2015-12-26
Yes it's usb. 

```


tom@tom-desktop:~$ lsusb
Bus 006 Device 002: ID 8087:8001 Intel Corp. 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 8087:8009 Intel Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 148f:7601 Ralink Technology, Corp. 
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 1e4e:0102 Cubeternet GL-UPC822 UVC WebCam
Bus 001 Device 002: ID 0e8f:00a5 GreenAsia Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Thank you

---

### Post by chili555 on 2015-12-26
> Hello I have recently decided to join Ubuntu for my main operating system Did you install Ubuntu 15.10? If so, the driver is already included (!!!) but you probably need the firmware, which is probably on the CD (!!!!!!!!!). If you installed 15.10, please open a terminal with Ctrl+Alt+t and run:```
sudo modprobe mt7601u
```Now check the message log to see if there is a complaint about needed firmware:```
dmesg | grep mt76
```Now check the CD; is there a firmware folder? Does it contain a MT76xxx.bin file or some such?

Depending on your reply, I will propose a solution.

---

### Post by tom219 on 2015-12-26
Thanks for the reply. 

I''m using Ubuntu 14.04.3 LTS. I went for that option because it has longer support. I can always reinstall with 15.10 version if you think it is a good idea?

sudo modprobe mt7601u outputs the following:

```
FATAL: Module mt7601u not found.
```

If I try  then nothing happens at all
dmesg | grep mt76

If I try dmesg I get the following:

```
[    0.231566] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.231581] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.231602] system 00:03: [io  0x1854-0x1857] has been reserved
[    0.231604] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.231649] system 00:04: [io  0x0290-0x029f] has been reserved
[    0.231651] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.231680] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.231681] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.231771] pnp 00:06: [dma 0 disabled]
[    0.231792] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.232056] system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.232058] system 00:07: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.232059] system 00:07: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.232060] system 00:07: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.232061] system 00:07: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.232062] system 00:07: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.232063] system 00:07: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.232063] system 00:07: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.232064] system 00:07: [mem 0xff000000-0xffffffff] has been reserved
[    0.232066] system 00:07: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.232067] system 00:07: [mem 0xf7fe0000-0xf7feffff] has been reserved
[    0.232068] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.232160] pnp: PnP ACPI: found 8 devices
[    0.237775] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.237777] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.237779] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
[    0.237781] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.237783] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.237791] pci 0000:00:1c.3: PCI bridge to [bus 03]
[    0.237793] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.237796] pci 0000:00:1c.3:   bridge window [mem 0xf7200000-0xf72fffff]
[    0.237801] pci 0000:00:1c.6: PCI bridge to [bus 04]
[    0.237804] pci 0000:00:1c.6:   bridge window [mem 0xf7100000-0xf71fffff]
[    0.237810] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.237811] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.237812] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.237813] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.237814] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.237815] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.237816] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.237816] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.237817] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.237818] pci_bus 0000:00: resource 13 [mem 0xe0000000-0xfeafffff]
[    0.237819] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.237820] pci_bus 0000:01: resource 1 [mem 0xf6000000-0xf70fffff]
[    0.237821] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.237822] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.237823] pci_bus 0000:03: resource 1 [mem 0xf7200000-0xf72fffff]
[    0.237823] pci_bus 0000:04: resource 1 [mem 0xf7100000-0xf71fffff]
[    0.237841] NET: Registered protocol family 2
[    0.237965] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.238104] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.238206] TCP: Hash tables configured (established 131072 bind 65536)
[    0.238217] TCP: reno registered
[    0.238228] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.238264] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.238314] NET: Registered protocol family 1
[    0.276126] pci 0000:01:00.0: Video device with shadowed ROM
[    0.276222] PCI: CLS 64 bytes, default 64
[    0.276251] Trying to unpack rootfs image as initramfs...
[    0.461145] Freeing initrd memory: 19328K (ffff880035a30000 - ffff880036d10000)
[    0.461158] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.461160] software IO TLB [mem 0xda157000-0xde157000] (64MB) mapped at [ffff8800da157000-ffff8800de156fff]
[    0.461345] RAPL PMU detected, hw unit 2^-14 Joules, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
[    0.461412] microcode: CPU0 sig=0x306c3, pf=0x2, revision=0x19
[    0.461416] microcode: CPU1 sig=0x306c3, pf=0x2, revision=0x19
[    0.461422] microcode: CPU2 sig=0x306c3, pf=0x2, revision=0x19
[    0.461426] microcode: CPU3 sig=0x306c3, pf=0x2, revision=0x19
[    0.461431] microcode: CPU4 sig=0x306c3, pf=0x2, revision=0x19
[    0.461436] microcode: CPU5 sig=0x306c3, pf=0x2, revision=0x19
[    0.461440] microcode: CPU6 sig=0x306c3, pf=0x2, revision=0x19
[    0.461444] microcode: CPU7 sig=0x306c3, pf=0x2, revision=0x19
[    0.461480] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.461496] Scanning for low memory corruption every 60 seconds
[    0.461707] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.461726] Initialise system trusted keyring
[    0.461739] audit: initializing netlink subsys (disabled)
[    0.461748] audit: type=2000 audit(1451147027.452:1): initialized
[    0.461950] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.462790] zpool: loaded
[    0.462791] zbud: loaded
[    0.462896] VFS: Disk quotas dquot_6.5.2
[    0.462916] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.463177] fuse init (API version 7.23)
[    0.463260] Key type big_key registered
[    0.463527] Key type asymmetric registered
[    0.463529] Asymmetric key parser 'x509' registered
[    0.463550] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.463588] io scheduler noop registered
[    0.463591] io scheduler deadline registered (default)
[    0.463608] io scheduler cfq registered
[    0.463989] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    0.463991] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.463992] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    0.463993] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    0.464004] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.464007] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.464017] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    0.464018] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.464020] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    0.464030] pcieport 0000:00:1c.6: Signaling PME through PCIe PME interrupt
[    0.464031] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    0.464034] pcie_pme 0000:00:1c.6:pcie01: service driver pcie_pme loaded
[    0.464037] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.464046] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.464064] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[    0.464065] vesafb: scrolling: redraw
[    0.464066] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.468786] vesafb: framebuffer at 0xf1000000, mapped to 0xffffc90005c00000, using 5120k, total 5120k
[    0.468861] Console: switching to colour frame buffer device 160x64
[    0.468871] fb0: VESA VGA frame buffer device
[    0.468888] intel_idle: MWAIT substates: 0x42120
[    0.468889] intel_idle: v0.4 model 0x3C
[    0.468889] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.469114] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.469116] ACPI: Power Button [PWRB]
[    0.469138] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.469139] ACPI: Sleep Button [SLPB]
[    0.469157] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.469158] ACPI: Power Button [PWRF]
[    0.469338] GHES: HEST is not enabled!
[    0.469408] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.489800] 00:06: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.490706] Linux agpgart interface v0.103
[    0.491430] brd: module loaded
[    0.491766] loop: module loaded
[    0.491896] libphy: Fixed MDIO Bus: probed
[    0.491899] tun: Universal TUN/TAP device driver, 1.6
[    0.491899] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.491925] PPP generic driver version 2.4.2
[    0.492030] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.492034] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.492106] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.492161] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.492162] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.492163] usb usb1: Product: xHCI Host Controller
[    0.492164] usb usb1: Manufacturer: Linux 3.19.0-25-generic xhci-hcd
[    0.492165] usb usb1: SerialNumber: 0000:00:14.0
[    0.492227] hub 1-0:1.0: USB hub found
[    0.492242] hub 1-0:1.0: 14 ports detected
[    0.494377] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.494379] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.494400] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.494401] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.494402] usb usb2: Product: xHCI Host Controller
[    0.494403] usb usb2: Manufacturer: Linux 3.19.0-25-generic xhci-hcd
[    0.494403] usb usb2: SerialNumber: 0000:00:14.0
[    0.494459] hub 2-0:1.0: USB hub found
[    0.494469] hub 2-0:1.0: 6 ports detected
[    0.495572] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    0.495574] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
[    0.556300] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.556302] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.556302] usb usb3: Product: xHCI Host Controller
[    0.556303] usb usb3: Manufacturer: Linux 3.19.0-25-generic xhci-hcd
[    0.556304] usb usb3: SerialNumber: 0000:04:00.0
[    0.556373] hub 3-0:1.0: USB hub found
[    0.556378] hub 3-0:1.0: 2 ports detected
[    0.556422] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    0.556423] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
[    0.556474] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.556475] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.556476] usb usb4: Product: xHCI Host Controller
[    0.556476] usb usb4: Manufacturer: Linux 3.19.0-25-generic xhci-hcd
[    0.556477] usb usb4: SerialNumber: 0000:04:00.0
[    0.556546] hub 4-0:1.0: USB hub found
[    0.556551] hub 4-0:1.0: 2 ports detected
[    0.556598] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.556602] ehci-pci: EHCI PCI platform driver
[    0.556656] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.556658] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 5
[    0.556667] ehci-pci 0000:00:1a.0: debug port 2
[    0.560564] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.560573] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7337000
[    0.572558] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.572578] usb usb5: New USB device found, idVendor=1d6b, idProduct=0002
[    0.572578] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.572579] usb usb5: Product: EHCI Host Controller
[    0.572580] usb usb5: Manufacturer: Linux 3.19.0-25-generic ehci_hcd
[    0.572581] usb usb5: SerialNumber: 0000:00:1a.0
[    0.572652] hub 5-0:1.0: USB hub found
[    0.572654] hub 5-0:1.0: 2 ports detected
[    0.572766] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.572768] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.572777] ehci-pci 0000:00:1d.0: debug port 2
[    0.576673] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.576681] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7336000
[    0.588582] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.588602] usb usb6: New USB device found, idVendor=1d6b, idProduct=0002
[    0.588603] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.588604] usb usb6: Product: EHCI Host Controller
[    0.588605] usb usb6: Manufacturer: Linux 3.19.0-25-generic ehci_hcd
[    0.588606] usb usb6: SerialNumber: 0000:00:1d.0
[    0.588680] hub 6-0:1.0: USB hub found
[    0.588683] hub 6-0:1.0: 2 ports detected
[    0.588746] ehci-platform: EHCI generic platform driver
[    0.588752] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.588755] ohci-pci: OHCI PCI platform driver
[    0.588762] ohci-platform: OHCI generic platform driver
[    0.588767] uhci_hcd: USB Universal Host Controller Interface driver
[    0.588797] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.591079] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.591082] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.591187] mousedev: PS/2 mouse device common for all mice
[    0.591360] rtc_cmos 00:02: RTC can wake from S4
[    0.591467] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.591489] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.591499] i2c /dev entries driver
[    0.591535] device-mapper: uevent: version 1.0.3
[    0.591582] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    0.591590] Intel P-state driver initializing.
[    0.591754] Consider also installing thermald for improved thermal control.
[    0.591757] ledtrig-cpu: registered to indicate activity on CPUs
[    0.591930] PCCT header not found.
[    0.591930] ACPI PCC probe failed.
[    0.591985] TCP: cubic registered
[    0.592036] NET: Registered protocol family 10
[    0.592240] NET: Registered protocol family 17
[    0.592246] Key type dns_resolver registered
[    0.592454] Loading compiled-in X.509 certificates
[    0.593011] Loaded X.509 cert 'Magrathea: Glacier signing key: 6aaa11d18c2d3a40b1b4dbe5bf8ad656ddf51838'
[    0.593021] registered taskstats version 1
[    0.593970] Key type trusted registered
[    0.595831] Key type encrypted registered
[    0.595835] AppArmor: AppArmor sha1 policy hashing enabled
[    0.595838] ima: No TPM chip found, activating TPM-bypass!
[    0.595859] evm: HMAC attrs: 0x1
[    0.596282]   Magic number: 11:511:389
[    0.596298] thermal cooling_device4: hash matches
[    0.596392] rtc_cmos 00:02: setting system clock to 2015-12-26 16:23:48 UTC (1451147028)
[    0.596465] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.596465] EDD information not available.
[    0.596529] PM: Hibernation image not present or could not be loaded.
[    0.596748] Freeing unused kernel memory: 1408K (ffffffff81d27000 - ffffffff81e87000)
[    0.596748] Write protecting the kernel read-only data: 12288k
[    0.596932] Freeing unused kernel memory: 260K (ffff8800017bf000 - ffff880001800000)
[    0.597007] Freeing unused kernel memory: 344K (ffff880001baa000 - ffff880001c00000)
[    0.602242] systemd-udevd[148]: starting version 204
[    0.610380] sdhci: Secure Digital Host Controller Interface driver
[    0.610382] sdhci: Copyright(c) Pierre Ossman
[    0.617183] pps_core: LinuxPPS API ver. 1 registered
[    0.617184] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.617895] PTP clock support registered
[    0.618221] ahci 0000:00:1f.2: version 3.0
[    0.618342] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x24 impl SATA mode
[    0.618344] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
[    0.620042] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    0.620044] e1000e: Copyright(c) 1999 - 2014 Intel Corporation.
[    0.625088] scsi host0: ahci
[    0.625179] scsi host1: ahci
[    0.625252] scsi host2: ahci
[    0.625328] scsi host3: ahci
[    0.625413] scsi host4: ahci
[    0.625493] scsi host5: ahci
[    0.625522] ata1: DUMMY
[    0.625523] ata2: DUMMY
[    0.625524] ata3: SATA max UDMA/133 abar m2048@0xf7335000 port 0xf7335200 irq 37
[    0.625525] ata4: DUMMY
[    0.625526] ata5: DUMMY
[    0.625527] ata6: SATA max UDMA/133 abar m2048@0xf7335000 port 0xf7335380 irq 37
[    0.625645] ahci 0000:03:00.0: SSS flag set, parallel bus scan disabled
[    0.625694] ahci 0000:03:00.0: AHCI 0001.0200 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    0.625696] ahci 0000:03:00.0: flags: 64bit ncq sntf stag led clo pmp pio slum part ccc sxs 
[    0.625718] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.626074] scsi host6: ahci
[    0.626162] scsi host7: ahci
[    0.626204] ata7: SATA max UDMA/133 abar m512@0xf7200000 port 0xf7200100 irq 38
[    0.626206] ata8: SATA max UDMA/133 abar m512@0xf7200000 port 0xf7200180 irq 38
[    0.804974] usb 1-2: new low-speed USB device number 2 using xhci_hcd
[    0.885116] usb 5-1: new high-speed USB device number 2 using ehci-pci
[    0.891971] e1000e 0000:00:19.0 eth0: registered PHC clock
[    0.891973] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) d0:50:99:3e:28:39
[    0.891974] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    0.891999] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    0.901156] usb 6-1: new high-speed USB device number 2 using ehci-pci
[    0.921193] usb 3-2: new low-speed USB device number 2 using xhci_hcd
[    0.945235] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.945242] ata7: SATA link down (SStatus 0 SControl 300)
[    0.945258] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    0.946203] ata3.00: ATA-9: ST1000DM003-1ER162, CC45, max UDMA/133
[    0.946205] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.947213] ata3.00: configured for UDMA/133
[    0.947369] scsi 2:0:0:0: Direct-Access     ATA      ST1000DM003-1ER1 CC45 PQ: 0 ANSI: 5
[    0.947517] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.947519] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.947520] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.947666] sd 2:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    0.947669] sd 2:0:0:0: [sda] 4096-byte physical blocks
[    0.947674] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    0.947860] sd 2:0:0:0: [sda] Write Protect is off
[    0.947871] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.947928] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.948032] ata6.00: ATAPI: TSSTcorp CDDVDW SH-224DB, SB01, max UDMA/100
[    0.949147] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.949149] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.949150] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.949694] ata6.00: configured for UDMA/100
[    0.955905] scsi 5:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-224DB  SB01 PQ: 0 ANSI: 5
[    0.964277] sr 5:0:0:0: [sr0] scsi3-mmc drive: 16x/16x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.964278] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.964412] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    0.964494] sr 5:0:0:0: Attached scsi generic sg1 type 5
[    0.977778]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    0.978513] sd 2:0:0:0: [sda] Attached SCSI disk
[    0.994869] usb 1-2: New USB device found, idVendor=0e8f, idProduct=00a5
[    0.994881] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    0.994882] usb 1-2: Product: 2.4G RX
[    0.994883] usb 1-2: Manufacturer: DaKai
[    0.995020] usb 1-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    0.995024] usb 1-2: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    0.997192] hidraw: raw HID events driver (C) Jiri Kosina
[    1.006037] usbcore: registered new interface driver usbhid
[    1.006038] usbhid: USB HID core driver
[    1.006850] input: DaKai 2.4G RX as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/0003:0E8F:00A5.0001/input/input6
[    1.025648] usb 5-1: New USB device found, idVendor=8087, idProduct=8009
[    1.025649] usb 5-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.025800] hub 5-1:1.0: USB hub found
[    1.025893] hub 5-1:1.0: 6 ports detected
[    1.033684] usb 6-1: New USB device found, idVendor=8087, idProduct=8001
[    1.033695] usb 6-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.033974] hub 6-1:1.0: USB hub found
[    1.034063] hub 6-1:1.0: 8 ports detected
[    1.061444] hid-generic 0003:0E8F:00A5.0001: input,hidraw0: USB HID v1.10 Keyboard [DaKai 2.4G RX] on usb-0000:00:14.0-2/input0
[    1.061591] input: DaKai 2.4G RX as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.1/0003:0E8F:00A5.0002/input/input7
[    1.117733] hid-generic 0003:0E8F:00A5.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [DaKai 2.4G RX] on usb-0000:00:14.0-2/input1
[    1.136746] usb 3-2: New USB device found, idVendor=0458, idProduct=003a
[    1.136748] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.136749] usb 3-2: Product: USB Optical Mouse
[    1.136750] usb 3-2: Manufacturer: Genius
[    1.136864] usb 3-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.139859] input: Genius USB Optical Mouse as /devices/pci0000:00/0000:00:1c.6/0000:04:00.0/usb3/3-2/3-2:1.0/0003:0458:003A.0003/input/input8
[    1.140161] hid-generic 0003:0458:003A.0003: input,hidraw2: USB HID v1.11 Mouse [Genius USB Optical Mouse] on usb-0000:04:00.0-2/input0
[    1.161573] usb 1-3: new high-speed USB device number 3 using xhci_hcd
[    1.281788] ata8: SATA link down (SStatus 0 SControl 300)
[    1.310757] usb 1-3: New USB device found, idVendor=1e4e, idProduct=0102
[    1.310768] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.310769] usb 1-3: Product: USB 2.0 VGA Camera 
[    1.310770] usb 1-3: Manufacturer: YM Camera
[    1.426004] usb 1-7: new full-speed USB device number 4 using xhci_hcd
[    1.462046] tsc: Refined TSC clocksource calibration: 3598.955 MHz
[    1.557470] usb 1-7: New USB device found, idVendor=046d, idProduct=c52b
[    1.557482] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.557483] usb 1-7: Product: USB Receiver
[    1.557484] usb 1-7: Manufacturer: Logitech
[    1.568507] logitech-djreceiver 0003:046D:C52B.0006: hiddev0,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-7/input2
[    1.730509] usb 1-8: new high-speed USB device number 5 using xhci_hcd
[    1.781398] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    1.869050] usb 1-8: New USB device found, idVendor=148f, idProduct=7601
[    1.869052] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.869053] usb 1-8: Product: 802.11 n WLAN
[    1.869054] usb 1-8: Manufacturer: MediaTek
[    1.869055] usb 1-8: SerialNumber: 1.0
[    2.186241] random: init urandom read with 101 bits of entropy available
[    2.440326] init: plymouth-upstart-bridge main process (239) terminated with status 1
[    2.440332] init: plymouth-upstart-bridge main process ended, respawning
[    2.441215] init: plymouth-upstart-bridge main process (252) terminated with status 1
[    2.441220] init: plymouth-upstart-bridge main process ended, respawning
[    2.441956] init: plymouth-upstart-bridge main process (254) terminated with status 1
[    2.441961] init: plymouth-upstart-bridge main process ended, respawning
[    2.442846] init: plymouth-upstart-bridge main process (255) terminated with status 1
[    2.442852] init: plymouth-upstart-bridge main process ended, respawning
[    2.443606] init: plymouth-upstart-bridge main process (257) terminated with status 1
[    2.443611] init: plymouth-upstart-bridge main process ended, respawning
[    2.444520] init: plymouth-upstart-bridge main process (258) terminated with status 1
[    2.444525] init: plymouth-upstart-bridge main process ended, respawning
[    2.445272] init: plymouth-upstart-bridge main process (260) terminated with status 1
[    2.445278] init: plymouth-upstart-bridge main process ended, respawning
[    2.446156] init: plymouth-upstart-bridge main process (261) terminated with status 1
[    2.446161] init: plymouth-upstart-bridge main process ended, respawning
[    2.446850] init: plymouth-upstart-bridge main process (263) terminated with status 1
[    2.446855] init: plymouth-upstart-bridge main process ended, respawning
[    2.447764] init: plymouth-upstart-bridge main process (264) terminated with status 1
[    2.447768] init: plymouth-upstart-bridge main process ended, respawning
[    2.448476] init: plymouth-upstart-bridge main process (266) terminated with status 1
[    2.448480] init: plymouth-upstart-bridge respawning too fast, stopped
[    2.463873] Switched to clocksource tsc
[    2.702351] random: nonblocking pool is initialized
[    6.256961] Adding 16722940k swap on /dev/sda6.  Priority:-1 extents:1 across:16722940k FS
[    6.330430] systemd-udevd[369]: starting version 204
[    6.366418] lp: driver loaded but no devices found
[    6.368922] ppdev: user-space parallel port driver
[    6.421239] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    6.461705] wmi: Mapper loaded
[    6.474373] [drm] Initialized drm 1.1.0 20060810
[    6.493171] AVX2 version of gcm_enc/dec engaged.
[    6.493173] AES CTR mode by8 optimization enabled
[    6.500330] MXM: GUID detected in BIOS
[    6.500353] checking generic (f1000000 500000) vs hw (e0000000 10000000)
[    6.500354] checking generic (f1000000 500000) vs hw (f0000000 2000000)
[    6.500355] fb: switching to nouveaufb from VESA VGA
[    6.500373] Console: switching to colour dummy device 80x25
[    6.501359] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x124020a1
[    6.501361] nouveau  [  DEVICE][0000:01:00.0] Chipset: GM204 (NV124)
[    6.501362] nouveau  [  DEVICE][0000:01:00.0] Family : NV110
[    6.514084] intel_rapl: Found RAPL domain package
[    6.514087] intel_rapl: Found RAPL domain core
[    6.514089] intel_rapl: Found RAPL domain dram
[    6.531538] audit: type=1400 audit(1451147034.421:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=485 comm="apparmor_parser"
[    6.531543] audit: type=1400 audit(1451147034.421:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=485 comm="apparmor_parser"
[    6.531547] audit: type=1400 audit(1451147034.421:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=485 comm="apparmor_parser"
[    6.531863] audit: type=1400 audit(1451147034.421:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=485 comm="apparmor_parser"
[    6.531868] audit: type=1400 audit(1451147034.421:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=485 comm="apparmor_parser"
[    6.532042] audit: type=1400 audit(1451147034.421:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=485 comm="apparmor_parser"
[    6.544092] sound hdaudioC0D0: ALC1150: SKU not ready 0x00000000
[    6.544626] sound hdaudioC0D0: autoconfig: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
[    6.544628] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    6.544630] sound hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    6.544631] sound hdaudioC0D0:    mono: mono_out=0x0
[    6.544633] sound hdaudioC0D0:    dig-out=0x1e/0x0
[    6.544634] sound hdaudioC0D0:    inputs:
[    6.544636] sound hdaudioC0D0:      Front Mic=0x19
[    6.544638] sound hdaudioC0D0:      Rear Mic=0x18
[    6.544639] sound hdaudioC0D0:      Line=0x1a
[    6.556015] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    6.556074] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    6.556148] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    6.556240] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    6.556279] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    6.582053] nouveau  [   VBIOS][0000:01:00.0] using image from PROM
[    6.582192] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[    6.582194] nouveau  [   VBIOS][0000:01:00.0] version 84.04.31.00.30
[    6.582785] nouveau  [     PMC][0000:01:00.0] MSI interrupts enabled
[    6.582810] nouveau  [     PFB][0000:01:00.0] RAM type: GDDR5
[    6.582811] nouveau  [     PFB][0000:01:00.0] RAM size: 4096 MiB
[    6.582811] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 0 tags
[    6.584387] [TTM] Zone  kernel: Available graphics memory: 8190154 kiB
[    6.584388] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    6.584389] [TTM] Initializing pool allocator
[    6.584391] [TTM] Initializing DMA pool allocator
[    6.584397] nouveau  [     DRM] VRAM: 4096 MiB
[    6.584398] nouveau  [     DRM] GART: 1048576 MiB
[    6.584400] nouveau  [     DRM] TMDS table version 2.0
[    6.584401] nouveau  [     DRM] DCB version 4.1
[    6.584402] nouveau  [     DRM] DCB outp 00: 01000f02 00020030
[    6.584403] nouveau  [     DRM] DCB outp 01: 02000f00 00000000
[    6.584404] nouveau  [     DRM] DCB outp 02: 02811f76 04420020
[    6.584404] nouveau  [     DRM] DCB outp 03: 02011f72 00020020
[    6.584405] nouveau  [     DRM] DCB outp 05: 04022f82 00020030
[    6.584406] nouveau  [     DRM] DCB outp 08: 02044f62 00020010
[    6.584407] nouveau  [     DRM] DCB outp 15: 01df5ff8 00000000
[    6.584407] nouveau  [     DRM] DCB conn 00: 00001030
[    6.584409] nouveau  [     DRM] DCB conn 01: 00020146
[    6.584409] nouveau  [     DRM] DCB conn 02: 01000231
[    6.584410] nouveau  [     DRM] DCB conn 04: 00010461
[    6.584411] nouveau  [     DRM] DCB conn 05: 00000570
[    6.584412] nouveau W[     DRM] Pointer to flat panel table invalid
[    6.588391] nouveau W[     DRM] unknown connector type 70
[    6.588411] nouveau W[     DRM] failed to create encoder 1/8/0: -19
[    6.588412] nouveau W[     DRM] Unknown-1 has no encoders, removing
[    6.588431] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    6.588432] [drm] Driver supports precise vblank timestamp query.
[    6.588437] nouveau E[     DRM] failed to initialise sync subsystem, -38
[    6.676133] media: Linux media interface: v0.10
[    6.678746] Linux video capture interface: v2.00
[    6.682664] logitech-hidpp-device 0003:046D:4101.0007: hidraw4: USB HID v1.11 Keyboard [Logitech T650] on usb-0000:00:14.0-7:1
[    6.683848] uvcvideo: Found UVC 1.00 device USB 2.0 VGA Camera  (1e4e:0102)
[    6.686719] input: Logitech K400 as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.2/0003:046D:C52B.0006/0003:046D:4024.0008/input/input14
[    6.686751] input: USB 2.0 VGA Camera  as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/input/input15
[    6.686783] logitech-hidpp-device 0003:046D:4024.0008: input,hidraw5: USB HID v1.11 Keyboard [Logitech K400] on usb-0000:00:14.0-7:2
[    6.686821] usbcore: registered new interface driver uvcvideo
[    6.686822] USB Video Class driver (1.1.1)
[    6.764024] nouveau  [     DRM] allocated 1920x1080 fb: 0x60000, bo ffff8800d9008000
[    6.764084] fbcon: nouveaufb (fb0) is primary device
[    6.764137] Console: switching to colour frame buffer device 210x65
[    6.764149] nouveau 0000:01:00.0: fb0: nouveaufb frame buffer device
[    6.764150] nouveau 0000:01:00.0: registered panic notifier
[    6.786884] [drm] Initialized nouveau 1.2.1 20120801 for 0000:01:00.0 on minor 0
[    6.787006] snd_hda_intel 0000:01:00.1: Disabling MSI
[    6.787022] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    7.251951] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[    7.252012] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input17
[    7.252044] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input18
[    7.252083] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input19
[    7.632038] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    7.763054] init: failsafe main process (674) killed by TERM signal
[    8.035555] Bluetooth: Core ver 2.20
[    8.035565] NET: Registered protocol family 31
[    8.035566] Bluetooth: HCI device and connection manager initialized
[    8.035569] Bluetooth: HCI socket layer initialized
[    8.035570] Bluetooth: L2CAP socket layer initialized
[    8.035574] Bluetooth: SCO socket layer initialized
[    8.037001] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    8.037002] Bluetooth: BNEP filters: protocol multicast
[    8.037004] Bluetooth: BNEP socket layer initialized
[    8.037397] Bluetooth: RFCOMM TTY layer initialized
[    8.037400] Bluetooth: RFCOMM socket layer initialized
[    8.037403] Bluetooth: RFCOMM ver 1.11
[    8.056936] audit: type=1400 audit(1451147035.941:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=750 comm="apparmor_parser"
[    8.056940] audit: type=1400 audit(1451147035.941:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=750 comm="apparmor_parser"
[    8.057168] audit: type=1400 audit(1451147035.945:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=750 comm="apparmor_parser"
[    8.159488] init: cups main process (751) killed by HUP signal
[    8.159493] init: cups main process ended, respawning
[    8.553454] audit: type=1400 audit(1451147036.437:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=831 comm="apparmor_parser"
[    8.750232] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.433205] ISO 9660 Extensions: Microsoft Joliet Level 3
[   18.434958] ISOFS: changing to secondary root
[   26.044057] systemd-hostnamed[1952]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[   38.197431] audit_printk_skb: 150 callbacks suppressed
[   38.197433] audit: type=1400 audit(1451147066.033:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2060 comm="apparmor_parser"
[   38.197437] audit: type=1400 audit(1451147066.033:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2060 comm="apparmor_parser"
[   38.197631] audit: type=1400 audit(1451147066.033:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2060 comm="apparmor_parser"
tom@tom-desktop:~$ 

```

I'm not sure if this is helpful too but I ran lsmod:

```
Module                  Size  Used by
nls_utf8               16384  1 
isofs                  40960  1 
bnep                   20480  2 
rfcomm                 69632  0 
bluetooth             491520  10 bnep,rfcomm
uvcvideo               90112  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         53248  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
hid_logitech_hidpp     20480  0 
joydev                 20480  0 
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
snd_hda_codec_hdmi     53248  1 
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
coretemp               16384  0 
kvm_intel             151552  0 
kvm                   479232  1 kvm_intel
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
ghash_clmulni_intel    16384  0 
aesni_intel           172032  0 
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
snd_soc_core          196608  1 snd_soc_rt5640
gf128mul               16384  1 lrw
snd_compress           20480  1 snd_soc_core
glue_helper            16384  1 aesni_intel
snd_pcm_dmaengine      16384  1 snd_soc_core
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_midi           16384  0 
snd_hda_codec_realtek    81920  1 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
nouveau              1368064  2 
serio_raw              16384  0 
snd_rawmidi            32768  1 snd_seq_midi
snd_hda_intel          32768  5 
snd_hda_controller     32768  1 snd_hda_intel
mxm_wmi                16384  1 nouveau
lpc_ich                24576  0 
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
ttm                    94208  1 nouveau
snd_hwdep              20480  1 snd_hda_codec
drm_kms_helper        126976  1 nouveau
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
mei_me                 20480  0 
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
drm                   344064  5 ttm,drm_kms_helper,nouveau
mei                    90112  1 mei_me
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
8250_fintek            16384  0 
i2c_algo_bit           16384  1 nouveau
snd_timer              32768  2 snd_pcm,snd_seq
snd                    86016  23 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
i2c_hid                20480  0 
soundcore              16384  2 snd,snd_hda_codec
wmi                    20480  2 mxm_wmi,nouveau
video                  20480  1 nouveau
dw_dmac                16384  0 
snd_soc_sst_acpi       16384  0 
i2c_designware_platform    16384  0 
dw_dmac_core           24576  1 dw_dmac
8250_dw                16384  0 
i2c_designware_core    16384  1 i2c_designware_platform
spi_pxa2xx_platform    24576  0 
intel_smartconnect     16384  0 
acpi_pad               20480  0 
mac_hid                16384  0 
shpchp                 40960  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
hid_logitech_dj        20480  0 
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  5 i2c_hid,hid_generic,usbhid,hid_logitech_dj,hid_logitech_hidpp
e1000e                237568  0 
psmouse               114688  0 
ahci                   36864  4 
ptp                    20480  1 e1000e
libahci                32768  1 ahci
pps_core               20480  1 ptp
sdhci_acpi             16384  0 
sdhci                  45056  1 sdhci_acpi
```

---

### Post by praseodym on 2015-12-26
Please check
```

uname -a
dpkg -l linux-image-* | grep ii
```

---

### Post by tom219 on 2015-12-26
uname -a
```
Linux tom-desktop 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```


dpkg -l linux-image-* | grep ii
```
ii  linux-image-3.19.0-25-generic                         3.19.0-25.26~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-25-generic                   3.19.0-25.26~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-vivid                         3.19.0.25.12                                        amd64        Generic Linux kernel image
tom@tom-desktop:~$ 

```

---

### Post by praseodym on 2015-12-26
Try the mainline kernel 4.3:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-headers-4.3.0-040300-generic_4.3.0-040300.201511020949_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-headers-4.3.0-040300-generic_4.3.0-040300.201511020949_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-image-4.3.0-040300-generic_4.3.0-040300.201511020949_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-image-4.3.0-040300-generic_4.3.0-040300.201511020949_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-headers-4.3.0-040300_4.3.0-040300.201511020949_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-headers-4.3.0-040300_4.3.0-040300.201511020949_all.deb)

Save these files in "Downloads" and install them:
```

sudo dpkg -i ~/Downloads/*.deb
```
Did work without problems? Then reboot. Please note that proprietary VGA drivers may not work properly. If it doesn't work boot back into an earlier kernel.

---

### Post by tom219 on 2015-12-26
Thank you, I have done this and the following has outputed:

```
tom@tom-desktop:~$ sudo dpkg -i ~/Downloads/*.deb
[sudo] password for tom: 
Selecting previously unselected package linux-headers-4.3.0-040300.
(Reading database ... 164677 files and directories currently installed.)
Preparing to unpack .../linux-headers-4.3.0-040300_4.3.0-040300.201511020949_all.deb ...
Unpacking linux-headers-4.3.0-040300 (4.3.0-040300.201511020949) ...
Selecting previously unselected package linux-headers-4.3.0-040300-generic.
Preparing to unpack .../linux-headers-4.3.0-040300-generic_4.3.0-040300.201511020949_amd64.deb ...
Unpacking linux-headers-4.3.0-040300-generic (4.3.0-040300.201511020949) ...
Selecting previously unselected package linux-image-4.3.0-040300-generic.
Preparing to unpack .../linux-image-4.3.0-040300-generic_4.3.0-040300.201511020949_amd64.deb ...
Done.
Unpacking linux-image-4.3.0-040300-generic (4.3.0-040300.201511020949) ...
Setting up linux-headers-4.3.0-040300 (4.3.0-040300.201511020949) ...
Setting up linux-headers-4.3.0-040300-generic (4.3.0-040300.201511020949) ...
Setting up linux-image-4.3.0-040300-generic (4.3.0-040300.201511020949) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.3.0-040300-generic /boot/vmlinuz-4.3.0-040300-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.3.0-040300-generic /boot/vmlinuz-4.3.0-040300-generic
update-initramfs: Generating /boot/initrd.img-4.3.0-040300-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.3.0-040300-generic /boot/vmlinuz-4.3.0-040300-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.3.0-040300-generic /boot/vmlinuz-4.3.0-040300-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.3.0-040300-generic /boot/vmlinuz-4.3.0-040300-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.3.0-040300-generic
Found initrd image: /boot/initrd.img-4.3.0-040300-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
tom@tom-desktop:~$ 

```

---

### Post by tom219 on 2015-12-26
Thank you very much for your help. It's working now. :D

---

### Post by tom219 on 2015-12-26
Hello 

While the wifi adapter is now working on Linux it has just stopped on windows 7. Is this a coincidence? I didn't think it was possible for one o/s to effect the other, after all they on their own partitions? Has anybody else experienced this before? Or know how to fix it?

Thank you

---

### Post by chili555 on 2015-12-26
Is the behavior the same whether you reboot into Windows or do a full shutdown and, after a few moments, cold boot to Windows?

---

### Post by tom219 on 2015-12-26
Yes, It only works if cold booted so the power cable is disconnected. A simple restart does not fix the issue. So it seems that it will work fine until Ubuntu is booted and thereafter will only work if a cold boot is made and windows is booted next. While this is a workable solution, it is slightly annoying. 

Thank you. :)

---

### Post by chili555 on 2015-12-26
I suspect it is because the firmware is still resident in the device in a restart and is flushed completely at a full shutdown. I know of no easy solution. Perhaps one of our colleagues will have a further suggestion.

---

### Post by tom219 on 2015-12-27
Thank you again for your help. 

I really love the spirit of Ubuntu but it does seem to come with its own head aches. For instance I have just fired up ubuntu only to find that again the wifi adapter is not working! Even if a cold boot is made the wifi adapter still wont find any wireless networks.  It's as though the drivers have been uninstalled? Any ideas on why this is happening and how I can fix this once and for all? This is so annoying and I'm getting to the point where I may begrudgingly give up with ubuntu as I seem to have hit a very high and unclimbable brick wall from the start. 

Thank you

---

### Post by praseodym on 2015-12-27
Which kernel is in use?

```
uname -a
lsmod
```

---

### Post by tom219 on 2015-12-27
It seems to be working now after 3 more reboots (none cold). This is quite strange indeed. 

I'm going to stay with Ubuntu and hopefully things will become easier as I become more familiar with it.

Thank you very much for your help.

---

### Post by praseodym on 2015-12-27
Please check if there is (still) a difference between

```
sudo reboot
```

and
```

sudo shutdown -r now
```

---

