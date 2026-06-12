---
title: "Problem with drivers for PCMCIA wireless card...please help :("
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by clarklinux on 2007-04-20
When I plug in my Sonnet Aria Extreme Wifi Card, dmesg gives me this:

> [ 63.667019] PCI: Enabling device 0000:00:13.0 (0000 -> 0002)
[ 63.667070] Yenta: CardBus bridge found at 0000:00:13.0 [0000:0000]
[ 63.667118] PCI: Bus 1, cardbus bridge: 0000:00:13.0
[ 63.667131] IO window: 00001000-000011ff
[ 63.667143] IO window: 00001400-000015ff
[ 63.667157] PREFETCH window: 80000000-803fffff
[ 63.667171] MEM window: 80400000-807fffff
[ 63.667184] Yenta: Enabling burst memory read transactions
[ 63.667197] Yenta: Using CSCINT to route CSC interrupts to PCI
[ 63.667208] Yenta: Routing CardBus interrupts to PCI
[ 63.667223] Yenta TI: socket 0000:00:13.0, mfunc 0x00000002, devctl 0x60
[ 63.792698] Yenta: ISA IRQ mask 0x0000, PCI irq 22
[ 63.792723] Socket status: 30000006
[ 63.792743] pcmcia: parent PCI bridge I/O window: 0x0 - 0x7fffff
[ 63.792761] pcmcia: parent PCI bridge Memory window: 0x80000000 - 0xfcffffff
[ 63.792778] pcmcia: parent PCI bridge Memory window: 0xfd000000 - 0xfdffffff
[ 63.834692] SCSI subsystem initialized
[ 63.957761] ts: Compaq touchscreen protocol output
[ 64.388047] mesh: configured for synchronous 5 MB/s
[ 64.595096] mesh: performing initial bus reset...
[ 68.599028] scsi0 : MESH
[ 72.531481] apm_emu: APM Emulation 0.5 initialized.
[ 74.459289] input: PowerMac Beep as /class/input/input4
[ 76.082155] Adding 211348k swap on /dev/disk/by-uuid/662a54dc-3437-43bb-8404-ff0f071f962a. Priority:-1 extents:1 across:211348k
[ 76.400785] EXT3 FS on hda3, internal journal
[ 93.180861] lp: driver loaded but no devices found
[ 93.631956] ppdev: user-space parallel port driver
[ 116.136975] phy registers:
[ 116.137004] 0800 7849 2000 5c10 01e1 45e1 0007 2801
[ 116.147266] 0000 0000 0000 0000 0000 0000 0000 0000
[ 116.157518] 2002 0000 0000 0000 0001 0000 0020 0000
[ 116.167771] 0000 0000 0180 0100 0006 0f00 0000 0000
[ 140.563950] NET: Registered protocol family 10
[ 140.564451] lo: Disabled Privacy Extensions
[ 140.565093] IPv6 over IPv4 tunneling driver
[ 149.034279] NET: Registered protocol family 17
[ 165.054977] eth0: no IPv6 routers present
[ 702.855023] pccard: CardBus card inserted into slot 0
[ 703.941003] ieee80211_crypt: registered algorithm 'NULL'
[ 704.147558] ieee80211: 802.11 data/management/control stack, git-1.1.13
[ 704.147593] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[ 704.502675] bcm43xx driver
[ 704.505759] PCI: Enabling device 0000:01:00.0 (0000 -> 0002)
[ 705.555798] Machine check in kernel mode.
[ 705.555829] Caused by (from SRR1=49030): Transfer error ack signal
[ 705.555855] Oops: Machine check, sig: 7 [#1]
[ 705.555870]
[ 705.555877] Modules linked in: bcm43xx ieee80211softmac ieee80211 ieee80211_crypt af_packet ipv6 ppdev lp parport cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand cpufreq_conservative snd_powermac snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc apm_emu pcmcia mesh tsdev evdev scsi_mod yenta_socket rsrc_nonstatic pcmcia_core pmac_zilog serial_core bmac ext3 jbd ohci_hcd usbcore ide_cd cdrom ide_disk capability commoncap
[ 705.556003] NIP: C9A33C44 LR: C9A33F44 CTR: C000D980
[ 705.556021] REGS: c3e658e0 TRAP: 0200 Not tainted (2.6.17-11-powerpc)
[ 705.556033] MSR: 00049030 <EE,ME,IR,DR> CR: 48004424 XER: 00000000
[ 705.556065] TASK = c7430c10[3571] 'NetworkManager' THREAD: c3e64000
[ 705.556077] GPR00: C99FC3FC C3E65990 C7430C10 0000FFFF 00000060 0000FFFF 0000FFFF C3E65A38
[ 705.556111] GPR08: C99FC000 C99FC000 00000025 C99FC000 28002482 1005FBE0 016AB5C8 00241B00
[ 705.556146] GPR16: 00241AB8 1001819D 10058BC0 10058BD0 10058BC4 FFFFFC18 C3B5CEEC FFFFFFFF
[ 705.556181] GPR24: FFFFFFFF C3B5CEB8 00000000 C3B5CEB8 C3B5CD58 00000002 00000000 C3B5CD58
[ 705.556216] NIP [C9A33C44] bcm43xx_phy_read+0x1c/0x2c [bcm43xx]
[ 705.556310] LR [C9A33F44] bcm43xx_phy_set_baseband_attenuation+0xa8/0xd0 [bcm43xx]
[ 705.556345] Call Trace:
[ 705.556355] [C3E65990] [FFFFFC18] 0xfffffc18 (unreliable)
[ 705.556383] [C3E659A0] [C9A32E30] bcm43xx_radio_set_txpower_bg+0xd4/0x154 [bcm43xx]
[ 705.556420] [C3E659C0] [C9A3588C] bcm43xx_phy_initb5+0x310/0x4ec [bcm43xx]
[ 705.556457] [C3E659E0] [C9A37A08] bcm43xx_phy_initg+0x3bc/0xd3c [bcm43xx]
[ 705.556494] [C3E65A50] [C9A39428] bcm43xx_phy_calibrate+0x80/0x94 [bcm43xx]
[ 705.556530] [C3E65A60] [C9A2A928] wireless_core_up+0x8c/0xf78 [bcm43xx]
[ 705.556565] [C3E65AC0] [C9A2BA78] bcm43xx_select_wireless_core+0x264/0x430 [bcm43xx]
[ 705.556601] [C3E65B10] [C9A2BD84] bcm43xx_init_board+0xa4/0xe0 [bcm43xx]
[ 705.556635] [C3E65B30] [C01BD8E8] dev_open+0x78/0xcc
[ 705.556672] [C3E65B50] [C01BBA7C] dev_change_flags+0x13c/0x168
[ 705.556696] [C3E65B70] [C01C7558] do_setlink+0x200/0x3fc
[ 705.556717] [C3E65BA0] [C01C6CA8] rtnetlink_rcv_msg+0x190/0x26c
[ 705.556750] [C3E65BD0] [C01D5AA0] netlink_run_queue+0xcc/0x1bc
[ 705.556777] [C3E65C10] [C01C6A7C] rtnetlink_rcv+0x44/0x70
[ 705.556800] [C3E65C40] [C01D6150] netlink_data_ready+0x28/0x84
[ 705.556822] [C3E65C50] [C01D48AC] netlink_sendskb+0x34/0x70
[ 705.556843] [C3E65C70] [C01D6050] netlink_sendmsg+0x1c8/0x2a0
[ 705.556864] [C3E65CC0] [C01AF8A0] sock_sendmsg+0xf4/0x124
[ 705.556897] [C3E65DB0] [C01B057C] sys_sendmsg+0x154/0x27c
[ 705.556920] [C3E65F00] [C01B1994] sys_socketcall+0x120/0x1d8
[ 705.556944] [C3E65F40] [C0011A80] ret_from_syscall+0x0/0x38
[ 705.556977] --- Exception: c01 at 0xff077f4
[ 705.556997] LR = 0xff077e0
[ 705.557006] Instruction dump:
[ 705.557017] 813f0014 380903ec 7e00072c 7c0006ac 4bfffd50 81630014 380b03fc 7c80072c
[ 705.557051] 7c0006ac 81230014 386903fe 7c601e2c <0c030000> 4c00012c 5463043e 4e800020
[ 705.557086]


What´s going on? Can someone please help?

---

