---
title: "Wireless PC Card on a Mac Powerbook G3"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by clarklinux on 2007-04-19
Hello-

I've been trying for about a month to get my Sonnet Aria Extreme wireless network PCMCIA card to work with my Powerbook G3 (PPC) laptop running Xubuntu (Edgy.)

I've tried following a guide I found on the wiki for the exact model card, and all the configuration went fine, but whenever I plug in my card, I can't do anything that requires root login. su comes back with a "Sorry- Authentication failure" type message, and if I used sudo, it just hangs up. Without going into superuser mode or using sudo I can't get into the Networking application from the xfce menu. I also can't run any hardware checks, iwconfig, etc. I think this is a problem with the PCMCIA software and not with wireless networking. dmesg does actually return the model name and everything, saying that it's a broadcom wireless card. I've alreday used the fwcutter thing to install the appropriate broadcom driver (which I know is the correct one because I extracted it from the .exe setup program that comes with my card.)


Can anyone help me figure out how to correct this problem?

Thanks in advance,

-Clark

---

### Post by clarklinux on 2007-04-20
by the way, here´s what dmesg gives me

> clark@xubuntulaptop:/usr/sbin$ dmesg
[    0.000000] Using PowerMac machine description
[    0.000000] Total memory = 128MB; using 256kB for hash table (at c7fc0000)
[    0.000000] Linux version 2.6.17-11-powerpc (root@royal) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Thu Feb 1 17:56:02 UTC 2007 (Ubuntu 2.6.17-11.35-powerpc)
[    0.000000] Found initrd at 0xc1900000:0xc1ed1000
[    0.000000] Found a Paddington mac-io controller, rev: 0, mapped at 0xfdf80000
[    0.000000] PowerMac motherboard: PowerBook 101 (Lombard)
[    0.000000] PMU driver v2 initialized for 1999 PowerBook G3, firmware: 0b
[    0.000000] Found Grackle (MPC106) PCI host bridge at 0x80000000. Firmware bus number: 0->0
[    0.000000] nvram: OF partition at 0x140
[    0.000000] nvram: XP partition at 0xffffffff
[    0.000000] nvram: NR partition at 0xffffffff
[    0.000000] Top of RAM: 0x8000000, Total RAM: 0x8000000
[    0.000000] Memory hole size: 0MB
[    0.000000] On node 0 totalpages: 32768
[    0.000000]   DMA zone: 32768 pages, LIFO batch:7
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/hda3 ro quiet splash 
[    0.000000] irq: Found primary Apple PIC /pci@80000000/mac-io@10 for 64 irqs
[    0.000000] irq: System has 64 possible interrupts
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] GMT Delta read from XPRAM: 0 minutes, DST: on
[    0.000000] time_init: decrementer frequency = 16.703750 MHz
[    0.000000] time_init: processor frequency   = 333.333330 MHz
[   21.499314] Console: colour dummy device 80x25
[   21.499943] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[   21.500514] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[   21.519329] High memory: 0k
[   21.519351] Memory: 119720k/131072k available (2748k kernel code, 11188k reserved, 432k data, 300k bss, 172k init)
[   21.519728] Calibrating delay loop... 33.28 BogoMIPS (lpj=66560)
[   21.603100] Security Framework v1.0.0 initialized
[   21.603138] SELinux:  Disabled at boot.
[   21.603200] Mount-cache hash table entries: 512
[   21.603868] device-tree: Duplicate name in /cpus/PowerPC,750@0, renamed to "l2-cache#1"
[   21.606384] checking if image is initramfs... it is
[   23.920446] Freeing initrd memory: 5956k freed
[   23.923710] NET: Registered protocol family 16
[   23.924329] PMU i2c /pci@80000000/mac-io@10/via-pmu@16000
[   23.924349]  channel 1 bus <multibus>
[   23.924360]  channel 2 bus <multibus>
[   23.924637] PCI: Probing PCI hardware
[   23.926452] Registering pmac pic with sysfs...
[   23.929484] NET: Registered protocol family 2
[   23.959220] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[   23.959712] TCP established hash table entries: 4096 (order: 2, 16384 bytes)
[   23.959871] TCP bind hash table entries: 2048 (order: 1, 8192 bytes)
[   23.959959] TCP: Hash tables configured (established 4096 bind 2048)
[   23.959974] TCP reno registered
[   23.960076] Thermal assist unit using timers, shrink_timer: 500 jiffies
[   23.963369] audit: initializing netlink socket (disabled)
[   23.963427] audit(1177029517.464:1): initialized
[   23.963996] VFS: Disk quotas dquot_6.5.1
[   23.964104] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.964356] Initializing Cryptographic API
[   23.964381] io scheduler noop registered
[   23.964407] io scheduler anticipatory registered
[   23.964430] io scheduler deadline registered
[   23.964477] io scheduler cfq registered (default)
[   23.965125] PCI: Enabling device 0000:00:11.0 (0086 -> 0087)
[   23.965166] atyfb: using auxiliary register aperture
[   23.965894] atyfb: 3D RAGE LT PRO (Mach64 LI, PCI) [0x4c49 rev 0xdc]
[   23.965945] atyfb: 8M SDRAM (1:1), 29.498928 MHz XTAL, 230 MHz PLL, 100 Mhz MCLK, 100 MHz XCLK
[   23.966507] atyfb: monitor sense=62b, mode 6
[   24.046564] Console: switching to colour frame buffer device 128x48
[   24.046592] atyfb: fb0: ATY Mach64 frame buffer device on PCI
[   24.206751] Generic RTC Driver v1.07
[   24.206959] Macintosh non-volatile memory driver v1.1
[   24.207464] mice: PS/2 mouse device common for all mice
[   24.210448] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.211321] MacIO PCI driver attached to Paddington chipset
[   24.212486] Can't request resource 0 for MacIO device 0.00000000:power-mg
[   24.215538] mediabay0: Registered Heathrow media-bay
[   24.215563] mediabay0: powering down
[   24.450969] mediabay0: switching to 3
[   24.450980] mediabay0: powering up
[   24.674969] mediabay0: enabling (kind:3)
[   24.738968] mediabay0: waiting reset (kind:3)
[   24.866967] mediabay0: waiting IDE reset (kind:3)
[   26.018967] mediabay0: waiting IDE ready (kind:3)
[   26.050966] mediabay0: up before IDE init
[   26.051390] input: Macintosh mouse button emulation as /class/input/input0
[   26.051909] Registered "pmu" backlight controller,level: 15/15
[   26.052285] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   26.052309] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   26.052607] adb: starting probe task...
[   27.070980] ide0: Found Apple Heathrow ATA controller, bus ID 0, irq 13
[   27.071040] Probing IDE interface ide0...
[   27.471167] hda: TOSHIBA MK4309MAT, ATA DISK drive
[   28.142998] hda: Enabling MultiWord DMA 2
[   28.144114] ide0 at 0xc9014000-0xc9014007,0xc9014160 on irq 13
[   28.144485] Registered ide1 for media bay 0
[   28.144509] ide1: Found Apple Heathrow ATA controller, bus ID 1 (mediabay), irq 14
[   28.144542] Probing IDE interface ide1...
[   28.186555] adb devices: [2]: 2 c3 [3]: 3 1 [7]: 7 1f
[   28.212096] ADB keyboard at 2, handler 1
[   28.212132] Detected ADB keyboard, type ANSI.
[   28.212442] input: ADB keyboard as /class/input/input1
[   28.212743] input: ADB Powerbook buttons as /class/input/input2
[   28.223036] ADB mouse at 3, handler set to 4 (trackpad)
[   28.282358] input: ADB mouse as /class/input/input3
[   28.282516] adb: finished probe task...
[   28.543154] hdc: MATSHITA CR-175, ATAPI CD/DVD-ROM drive
[   28.878978] hdc: Enabling MultiWord DMA 2
[   28.880036] ide1 at 0xc9016000-0xc9016007,0xc9016160 on irq 14
[   28.880715] PowerMac i2c bus pmu 2 registered
[   28.880927] PowerMac i2c bus pmu 1 registered
[   28.881349] TCP bic registered
[   28.881378] NET: Registered protocol family 1
[   28.881410] NET: Registered protocol family 8
[   28.881421] NET: Registered protocol family 20
[   28.881640] Freeing unused kernel memory: 172k init
[   30.394144] Capability LSM initialized
[   33.213783] hda: max request size: 128KiB
[   33.402247] hda: 8452080 sectors (4327 MB), CHS=8944/15/63, (U)DMA
[   33.402282] hda: cache flushes not supported
[   33.402482]  hda: [mac] hda1 hda2 hda3 hda4
[   33.574691] hdc: ATAPI 24X CD-ROM drive, 128kB Cache, DMA
[   33.574735] Uniform CD-ROM driver Revision: 3.20
[   33.714599] usbcore: registered new driver usbfs
[   33.718454] usbcore: registered new driver hub
[   33.731498] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   33.735394] ohci_hcd 0000:00:0e.0: OHCI Host Controller
[   33.736682] ohci_hcd 0000:00:0e.0: new USB bus registered, assigned bus number 1
[   33.736774] ohci_hcd 0000:00:0e.0: irq 28, io mem 0x80882000
[   33.821112] usb usb1: configuration #1 chosen from 1 choice
[   33.821835] hub 1-0:1.0: USB hub found
[   33.821915] hub 1-0:1.0: 2 ports detected
[   34.682394] Attempting manual resume
[   34.887340] kjournald starting.  Commit interval 5 seconds
[   34.887404] EXT3-fs: mounted filesystem with ordered data mode.
[   63.375305] eth0: BMAC+ at 00:50:e4:25:16:49
[   63.496118] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[   63.496267] pmac_zilog: serial modem detected
[   63.496365] ttyS0 at MMIO 0x80813020 (irq = 15) is a Z85c30 ESCC - Internal modem
[   63.504464] ttyS1 at MMIO 0x80813000 (irq = 16) is a Z85c30 ESCC - Infrared port
[   63.667019] PCI: Enabling device 0000:00:13.0 (0000 -> 0002)
[   63.667070] Yenta: CardBus bridge found at 0000:00:13.0 [0000:0000]
[   63.667118] PCI: Bus 1, cardbus bridge: 0000:00:13.0
[   63.667131]   IO window: 00001000-000011ff
[   63.667143]   IO window: 00001400-000015ff
[   63.667157]   PREFETCH window: 80000000-803fffff
[   63.667171]   MEM window: 80400000-807fffff
[   63.667184] Yenta: Enabling burst memory read transactions
[   63.667197] Yenta: Using CSCINT to route CSC interrupts to PCI
[   63.667208] Yenta: Routing CardBus interrupts to PCI
[   63.667223] Yenta TI: socket 0000:00:13.0, mfunc 0x00000002, devctl 0x60
[   63.792698] Yenta: ISA IRQ mask 0x0000, PCI irq 22
[   63.792723] Socket status: 30000006
[   63.792743] pcmcia: parent PCI bridge I/O window: 0x0 - 0x7fffff
[   63.792761] pcmcia: parent PCI bridge Memory window: 0x80000000 - 0xfcffffff
[   63.792778] pcmcia: parent PCI bridge Memory window: 0xfd000000 - 0xfdffffff
[   63.834692] SCSI subsystem initialized
[   63.957761] ts: Compaq touchscreen protocol output
[   64.388047] mesh: configured for synchronous 5 MB/s
[   64.595096] mesh: performing initial bus reset...
[   68.599028] scsi0 : MESH
[   72.531481] apm_emu: APM Emulation 0.5 initialized.
[   74.459289] input: PowerMac Beep as /class/input/input4
[   76.082155] Adding 211348k swap on /dev/disk/by-uuid/662a54dc-3437-43bb-8404-ff0f071f962a.  Priority:-1 extents:1 across:211348k
[   76.400785] EXT3 FS on hda3, internal journal
[   93.180861] lp: driver loaded but no devices found
[   93.631956] ppdev: user-space parallel port driver
[  116.136975] phy registers:
[  116.137004]  0800 7849 2000 5c10 01e1 45e1 0007 2801
[  116.147266]  0000 0000 0000 0000 0000 0000 0000 0000
[  116.157518]  2002 0000 0000 0000 0001 0000 0020 0000
[  116.167771]  0000 0000 0180 0100 0006 0f00 0000 0000
[  140.563950] NET: Registered protocol family 10
[  140.564451] lo: Disabled Privacy Extensions
[  140.565093] IPv6 over IPv4 tunneling driver
[  149.034279] NET: Registered protocol family 17
[  165.054977] eth0: no IPv6 routers present
[  702.855023] pccard: CardBus card inserted into slot 0
[  703.941003] ieee80211_crypt: registered algorithm 'NULL'
[  704.147558] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  704.147593] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  704.502675] bcm43xx driver
[  704.505759] PCI: Enabling device 0000:01:00.0 (0000 -> 0002)
[  705.555798] Machine check in kernel mode.
[  705.555829] Caused by (from SRR1=49030): Transfer error ack signal
[  705.555855] Oops: Machine check, sig: 7 [#1]
[  705.555870] 
[  705.555877] Modules linked in: bcm43xx ieee80211softmac ieee80211 ieee80211_crypt af_packet ipv6 ppdev lp parport cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand cpufreq_conservative snd_powermac snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc apm_emu pcmcia mesh tsdev evdev scsi_mod yenta_socket rsrc_nonstatic pcmcia_core pmac_zilog serial_core bmac ext3 jbd ohci_hcd usbcore ide_cd cdrom ide_disk capability commoncap
[  705.556003] NIP: C9A33C44 LR: C9A33F44 CTR: C000D980
[  705.556021] REGS: c3e658e0 TRAP: 0200   Not tainted  (2.6.17-11-powerpc)
[  705.556033] MSR: 00049030 <EE,ME,IR,DR>  CR: 48004424  XER: 00000000
[  705.556065] TASK = c7430c10[3571] 'NetworkManager' THREAD: c3e64000
[  705.556077] GPR00: C99FC3FC C3E65990 C7430C10 0000FFFF 00000060 0000FFFF 0000FFFF C3E65A38 
[  705.556111] GPR08: C99FC000 C99FC000 00000025 C99FC000 28002482 1005FBE0 016AB5C8 00241B00 
[  705.556146] GPR16: 00241AB8 1001819D 10058BC0 10058BD0 10058BC4 FFFFFC18 C3B5CEEC FFFFFFFF 
[  705.556181] GPR24: FFFFFFFF C3B5CEB8 00000000 C3B5CEB8 C3B5CD58 00000002 00000000 C3B5CD58 
[  705.556216] NIP [C9A33C44] bcm43xx_phy_read+0x1c/0x2c [bcm43xx]
[  705.556310] LR [C9A33F44] bcm43xx_phy_set_baseband_attenuation+0xa8/0xd0 [bcm43xx]
[  705.556345] Call Trace:
[  705.556355] [C3E65990] [FFFFFC18] 0xfffffc18 (unreliable)
[  705.556383] [C3E659A0] [C9A32E30] bcm43xx_radio_set_txpower_bg+0xd4/0x154 [bcm43xx]
[  705.556420] [C3E659C0] [C9A3588C] bcm43xx_phy_initb5+0x310/0x4ec [bcm43xx]
[  705.556457] [C3E659E0] [C9A37A08] bcm43xx_phy_initg+0x3bc/0xd3c [bcm43xx]
[  705.556494] [C3E65A50] [C9A39428] bcm43xx_phy_calibrate+0x80/0x94 [bcm43xx]
[  705.556530] [C3E65A60] [C9A2A928] wireless_core_up+0x8c/0xf78 [bcm43xx]
[  705.556565] [C3E65AC0] [C9A2BA78] bcm43xx_select_wireless_core+0x264/0x430 [bcm43xx]
[  705.556601] [C3E65B10] [C9A2BD84] bcm43xx_init_board+0xa4/0xe0 [bcm43xx]
[  705.556635] [C3E65B30] [C01BD8E8] dev_open+0x78/0xcc
[  705.556672] [C3E65B50] [C01BBA7C] dev_change_flags+0x13c/0x168
[  705.556696] [C3E65B70] [C01C7558] do_setlink+0x200/0x3fc
[  705.556717] [C3E65BA0] [C01C6CA8] rtnetlink_rcv_msg+0x190/0x26c
[  705.556750] [C3E65BD0] [C01D5AA0] netlink_run_queue+0xcc/0x1bc
[  705.556777] [C3E65C10] [C01C6A7C] rtnetlink_rcv+0x44/0x70
[  705.556800] [C3E65C40] [C01D6150] netlink_data_ready+0x28/0x84
[  705.556822] [C3E65C50] [C01D48AC] netlink_sendskb+0x34/0x70
[  705.556843] [C3E65C70] [C01D6050] netlink_sendmsg+0x1c8/0x2a0
[  705.556864] [C3E65CC0] [C01AF8A0] sock_sendmsg+0xf4/0x124
[  705.556897] [C3E65DB0] [C01B057C] sys_sendmsg+0x154/0x27c
[  705.556920] [C3E65F00] [C01B1994] sys_socketcall+0x120/0x1d8
[  705.556944] [C3E65F40] [C0011A80] ret_from_syscall+0x0/0x38
[  705.556977] --- Exception: c01 at 0xff077f4
[  705.556997]     LR = 0xff077e0
[  705.557006] Instruction dump:
[  705.557017] 813f0014 380903ec 7e00072c 7c0006ac 4bfffd50 81630014 380b03fc 7c80072c 
[  705.557051] 7c0006ac 81230014 386903fe 7c601e2c <0c030000> 4c00012c 5463043e 4e800020 
[  705.557086]  



...and lspci
> clark@xubuntulaptop:/usr/sbin$ lspci
00:00.0 Host bridge: Motorola MPC106 [Grackle] (rev 40)
00:0e.0 USB Controller: Agere Systems USB (rev 12)
00:10.0 Class ff00: Apple Computer Inc. Paddington Mac I/O
00:11.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro (rev dc)
00:13.0 CardBus bridge: Texas Instruments PCI1211
01:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)


---

