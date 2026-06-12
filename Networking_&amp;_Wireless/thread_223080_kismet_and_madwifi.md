---
title: "kismet and madwifi"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by Th3_j3st3r on 2006-07-25
I have no idea why but my kismet was working thanks to the guide:
[http://forums.remote-exploit.org/showthread.php?t=624](http://forums.remote-exploit.org/showthread.php?t=624)

It broke after uninstalling in order to enable inject mode from a guide located at: 
[http://forums.remote-exploit.org/showthread.php?t=624](http://forums.remote-exploit.org/showthread.php?t=624)
](*,) 

My wireless card is a Netgear WG511T with the Atheros chipset.

here is my (ifconfig -a) & (iwconfig)
```
      
ifconfig -a
ath0 Link encap:UNSPEC  HWaddr 00-14-6C-A0-9E-F7-20-B3-00-00-00-00-00-00-00-00
          inet6 addr: fe80::214:6cff:fea0:9ef7/64 Scope:Link
          UP BROADCAST PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:39 errors:29838 dropped:0 overruns:0 frame:29838
          TX packets:10 errors:9 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:12918 (12.6 KiB)  TX bytes:2352 (2.2 KiB)
          Interrupt:185 Memory:d8a60000-d8a70000

eth0      Link encap:Ethernet  HWaddr 00:16:36:29:D4:06
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe29:d406/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:895 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:655568 (640.2 KiB)  TX bytes:151509 (147.9 KiB)
          Interrupt:217 Base address:0x8000

eth1      Link encap:Ethernet  HWaddr 00:14:A5:71:06:43
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

```

iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:""
          Mode:Monitor  Frequency:2.457 GHz  Access Point: Not-Associated
          Bit Rate=5.5 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:9  Invalid misc:9   Missed beacon:0

sit0      no wireless extensions.

```


Now after running kismet and kismet_server I get:

```

Gathering packets...
FATAL: Failed to set channel 52 22:Invalid argument
Terminating.
Didn't detect any Cisco Discovery Packets, unlinking cisco dump
Didn't see any weak encryption packets, unlinking weak file
Sending termination request to channel control child 5428...
Waiting for channel control child 5428 to exit...
Kismet exiting.

```

finally maybe this could help some my lsmod output
```

lsmod
Module                  Size  Used by
binfmt_misc            12296  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
radeon                116000  0
drm                    73236  1 radeon
powernow_k8            12680  0
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 powernow_k8,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
dm_mod                 58936  1
ipv6                  265728  6
md_mod                 72532  0
af_packet              22920  6
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
ath_pci                79516  0
ath_rate_sample        16392  1 ath_pci
wlan                  144284  3 ath_pci,ath_rate_sample
ath_hal               148560  3 ath_pci,ath_rate_sample
pcmcia                 40508  0
joydev                 10048  0
yenta_socket           28428  2
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
8139cp                 22528  0
8139too                26880  0
bcm43xx               124044  0
mii                     5888  2 8139cp,8139too
ieee80211softmac       29696  1 bcm43xx
ieee80211              37064  2 bcm43xx,ieee80211softmac
ieee80211_crypt         6272  1 ieee80211
tsdev                   8000  0
snd_atiixp             19724  1
snd_atiixp_modem       16136  0
snd_ac97_codec         93088  2 snd_atiixp,snd_atiixp_modem
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
pcspkr                  2180  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
rtc                    13492  0
snd_pcm                89864  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  9 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
psmouse                36100  0
ati_agp                 9100  0
agpgart                34888  2 drm,ati_agp
snd_page_alloc         10632  3 snd_atiixp,snd_atiixp_modem,snd_pcm
serio_raw               7300  0
usbhid                 39904  0
evdev                   9856  2
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
ohci_hcd               21892  0
usbcore               130692  4 usbhid,ehci_hcd,ohci_hcd
ide_disk               17664  3
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
generic                 5124  0
atiixp                  6800  1
thermal                13576  0
processor              23360  2 powernow_k8,thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```

Please help!!! I really need it.

---

### Post by Th3_j3st3r on 2006-07-26
oh ps
my dmesg is (seems like there is some MAD errors here):
```

dmesg
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000017ef0000 (usable)
[17179569.184000]  BIOS-e820: 0000000017ef0000 - 0000000017eff000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000017eff000 - 0000000017f00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 0000000017f00000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 382MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f8130
[17179569.184000] On node 0 totalpages: 98032
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 93936 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI present.
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: RSDP (v000 HP                                    ) @ 0x000f8080
[17179569.184000] ACPI: RSDT (v001 HP     3097     0x20040206  LTP 0x00000000) @ 0x17ef8bc4
[17179569.184000] ACPI: FADT (v001 HP     3097     0x20040206 PTL  0x0000005f) @ 0x17efee2a
[17179569.184000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x20040206  LTP 0x00000001) @ 0x17efee9e
[17179569.184000] ACPI: MADT (v001 PTLTD         3097   0x20040206  LTP 0x00000000) @ 0x17efef74
[17179569.184000] ACPI: MCFG (v001 PTLTD    MCFG   0x20040206  LTP 0x00000000) @ 0x17efefc4
[17179569.184000] ACPI: DSDT (v001 HP     3091     0x20040206 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:12 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 1795.229 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.304000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.304000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)[17179570.312000] Memory: 378164k/392128k available (1976k kernel code, 13388k reserved, 606k data, 288k init, 0k highmem)
[17179570.312000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.392000] Calibrating delay using timer specific routine.. 3595.66 BogoMIPS (lpj=7191327)
[17179570.392000] Security Framework v1.0.0 initialized
[17179570.392000] SELinux:  Disabled at boot.
[17179570.392000] Mount-cache hash table entries: 512
[17179570.392000] CPU: After generic identify, caps: 078bfbff c3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179570.392000] CPU: After vendor identify, caps: 078bfbff c3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179570.392000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179570.392000] CPU: L2 Cache: 128K (64 bytes/line)
[17179570.392000] CPU: After all inits, caps: 078bfbff c3d3fbff 00000000 00000410 00000001 00000000 00000001
[17179570.392000] mtrr: v2.0 (20020519)
[17179570.392000] CPU: AMD Mobile AMD Sempron(tm) Processor 3000+ stepping 02
[17179570.392000] Enabling fast FPU save and restore... done.
[17179570.392000] Enabling unmasked SIMD FPU exception support... done.
[17179570.392000] Checking 'hlt' instruction... OK.
[17179570.408000] checking if image is initramfs... it is
[17179570.952000] Freeing initrd memory: 6616k freed
[17179570.960000] ACPI: Looking for DSDT ... not found!
[17179570.964000] ENABLING IO-APIC IRQs
[17179570.964000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179571.108000] NET: Registered protocol family 16
[17179571.108000] EISA bus registered
[17179571.108000] ACPI: bus type pci registered
[17179571.108000] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=5
[17179571.108000] PCI: Using MMCONFIG
[17179571.108000] ACPI: Subsystem revision 20051216
[17179571.108000] ACPI: Interpreter enabled
[17179571.108000] ACPI: Using IOAPIC for interrupt routing
[17179571.108000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.108000] PCI: Probing PCI hardware (bus 00)
[17179571.112000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[17179571.112000] Boot video device is 0000:01:05.0
[17179571.112000] PCI: Transparent bridge - 0000:00:14.4
[17179571.112000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.116000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[17179571.116000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[17179571.116000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[17179571.116000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[17179571.116000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[17179571.116000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[17179571.116000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[17179571.116000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[17179571.116000] ACPI: Embedded Controller [EC0] (gpe 24) interrupt mode.
[17179571.120000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[17179571.120000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179571.120000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.120000] pnp: PnP ACPI init
[17179571.120000] pnp: PnP ACPI: found 10 devices
[17179571.120000] PnPBIOS: Disabled by ACPI PNP
[17179571.120000] PCI: Using ACPI for IRQ routing
[17179571.120000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.136000] pnp: 00:07: ioport range 0x1080-0x1080 has been reserved
[17179571.136000] pnp: 00:07: ioport range 0x220-0x22f has been reserved
[17179571.136000] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
[17179571.136000] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[17179571.136000] PCI: Bridge: 0000:00:01.0
[17179571.136000]   IO window: 9000-9fff
[17179571.136000]   MEM window: c0100000-c01fffff
[17179571.136000]   PREFETCH window: c8000000-cfffffff
[17179571.136000] PCI: Bus 6, cardbus bridge: 0000:05:09.0
[17179571.136000]   IO window: 0000a400-0000a4ff
[17179571.136000]   IO window: 0000a800-0000a8ff
[17179571.136000]   PREFETCH window: 30000000-31ffffff
[17179571.136000]   MEM window: 32000000-33ffffff
[17179571.136000] PCI: Bridge: 0000:00:14.4
[17179571.136000]   IO window: a000-afff
[17179571.136000]   MEM window: c0200000-c02fffff
[17179571.136000]   PREFETCH window: 30000000-31ffffff
[17179571.136000] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179571.136000] PCI: Setting latency timer of device 0000:05:09.0 to 64
[17179571.136000] audit: initializing netlink socket (disabled)
[17179571.136000] audit(1153890015.136:1): initialized
[17179571.136000] VFS: Disk quotas dquot_6.5.1
[17179571.136000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.136000] Initializing Cryptographic API
[17179571.136000] io scheduler noop registered
[17179571.136000] io scheduler anticipatory registered
[17179571.136000] io scheduler deadline registered
[17179571.136000] io scheduler cfq registered
[17179571.136000] isapnp: Scanning for PnP cards...
[17179571.492000] isapnp: No Plug & Play device found
[17179571.504000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179571.516000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.516000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.516000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179571.520000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 185
[17179571.520000] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[17179571.520000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.520000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.520000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.520000] mice: PS/2 mouse device common for all mice
[17179571.520000] EISA: Probing bus 0 at eisa.0
[17179571.520000] Cannot allocate resource for EISA slot 1
[17179571.520000] Cannot allocate resource for EISA slot 8
[17179571.520000] EISA: Detected 0 cards.
[17179571.520000] NET: Registered protocol family 2
[17179571.556000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179571.556000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179571.556000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179571.556000] TCP: Hash tables configured (established 16384 bind 16384)
[17179571.556000] TCP reno registered
[17179571.556000] TCP bic registered
[17179571.556000] NET: Registered protocol family 1
[17179571.556000] NET: Registered protocol family 8
[17179571.556000] NET: Registered protocol family 20
[17179571.556000] Using IPI Shortcut mode
[17179571.556000] ACPI wakeup devices:
[17179571.556000] KBC0 MSE0  P2P AUDO
[17179571.556000] ACPI: (supports S0 S3 S4 S5)
[17179571.556000] Freeing unused kernel memory: 288k freed
[17179571.556000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.600000] vga16fb: initializing
[17179571.600000] vga16fb: mapped to 0xc00a0000
[17179571.692000] Console: switching to colour frame buffer device 80x25
[17179571.692000] fb0: VGA16 VGA frame buffer device
[17179572.796000] Capability LSM initialized
[17179572.832000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179572.832000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179572.836000] ACPI: Thermal Zone [THRM] (27 C)
[17179573.416000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[17179573.416000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 193
[17179573.416000] ATIIXP: chipset revision 0
[17179573.416000] ATIIXP: not 100% native mode: will probe irqs later
[17179573.416000]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[17179573.416000]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[17179573.416000] Probing IDE interface ide0...
[17179573.708000] hda: ST9402113A, ATA DISK drive
[17179574.380000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.380000] Probing IDE interface ide1...
[17179575.120000] hdc: UJDA770 DVD/CDRW, ATAPI CD/DVD-ROM drive
[17179575.456000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.468000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[17179575.468000] Uniform CD-ROM driver Revision: 3.20
[17179575.472000] hda: max request size: 1024KiB
[17179575.472000] hda: 78140160 sectors (40007 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179575.472000] hda: cache flushes supported
[17179575.472000]  hda: hda1 hda2 < hda5 >
[17179575.784000] usbcore: registered new driver usbfs
[17179575.784000] usbcore: registered new driver hub
[17179575.784000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179575.788000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 201
[17179575.788000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[17179576.124000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[17179576.124000] ohci_hcd 0000:00:13.0: irq 201, io mem 0xc0000000
[17179576.184000] hub 1-0:1.0: USB hub found
[17179576.184000] hub 1-0:1.0: 4 ports detected
[17179576.288000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 201
[17179576.288000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[17179576.620000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[17179576.620000] ohci_hcd 0000:00:13.1: irq 201, io mem 0xc0001000
[17179576.680000] hub 2-0:1.0: USB hub found
[17179576.680000] hub 2-0:1.0: 4 ports detected
[17179576.784000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 201
[17179576.784000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[17179576.784000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[17179576.784000] ehci_hcd 0000:00:13.2: irq 201, io mem 0xc0002000
[17179576.784000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.784000] hub 3-0:1.0: USB hub found
[17179576.784000] hub 3-0:1.0: 8 ports detected
[17179576.988000] Attempting manual resume
[17179577.044000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.060000] kjournald starting.  Commit interval 5 seconds
[17179577.664000] usb 1-1: new low speed USB device using ohci_hcd and address 3[17179587.100000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.404000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 185
[17179587.512000] MC'97 0 converters and GPIO not ready (0x1)
[17179587.516000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 185
[17179587.548000] Real Time Clock Driver v1.12
[17179587.560000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179587.564000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179587.572000] usbcore: registered new driver hiddev
[17179587.576000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input1
[17179587.576000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:13.0-1
[17179587.576000] usbcore: registered new driver usbhid
[17179587.576000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179587.584000] input: PC Speaker as /class/input/input2
[17179588.136000] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[17179588.168000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[17179588.252000] ts: Compaq touchscreen protocol output
[17179588.284000] ieee80211_crypt: registered algorithm 'NULL'
[17179588.292000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17179588.292000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179588.364000] 8139too Fast Ethernet driver 0.9.27
[17179588.364000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 209
[17179588.364000] eth0: RealTek RTL8139 at 0xd88ca000, 00:16:36:29:d4:06, IRQ 209
[17179588.364000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179588.452000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179588.616000] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179588.616000] Yenta: CardBus bridge found at 0000:05:09.0 [103c:3091]
[17179588.616000] Yenta: Enabling burst memory read transactions
[17179588.616000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179588.616000] Yenta: Routing CardBus interrupts to PCI
[17179588.616000] Yenta TI: socket 0000:05:09.0, mfunc 0x01a01b22, devctl 0x66
[17179588.644000] bcm43xx driver
[17179588.644000] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 20 (level, low) -> IRQ 217
[17179588.848000] Yenta: ISA IRQ mask 0x0ee8, PCI irq 185
[17179588.848000] Socket status: 30000820
[17179588.848000] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[17179588.848000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[17179588.848000] cs: IO port probe 0xa000-0xafff: clean.
[17179588.848000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[17179588.848000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x31ffffff
[17179589.232000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[17179589.384000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179589.392000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179589.516000] pccard: CardBus card inserted into slot 0
[17179589.760000] cs: IO port probe 0x100-0x3af: clean.
[17179589.764000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179589.764000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[17179589.764000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[17179589.768000] cs: IO port probe 0xa00-0xaff: clean.
[17179589.848000] ath_hal: module license 'Proprietary' taints kernel.
[17179589.848000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[17179589.876000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17179590.080000] ath_rate_sample: 1.2
[17179590.100000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17179590.100000] PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
[17179590.100000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179590.684000] Build date: Jul 19 2006
[17179590.684000] Debugging version (IEEE80211)
[17179590.684000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179590.684000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179590.684000] ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179590.684000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[17179590.684000] ath0: mac 7.9 phy 4.5 radio 5.6
[17179590.684000] ath0: Use hw queue 1 for WME_AC_BE traffic
[17179590.684000] ath0: Use hw queue 0 for WME_AC_BK traffic
[17179590.684000] ath0: Use hw queue 2 for WME_AC_VI traffic
[17179590.684000] ath0: Use hw queue 3 for WME_AC_VO traffic
[17179590.684000] ath0: Use hw queue 8 for CAB traffic
[17179590.684000] ath0: Use hw queue 9 for beacons
[17179590.684000] Debugging version (ATH)
[17179590.684000] ath0: Atheros 5212: mem=0x32000000, irq=185
[17179590.756000] NET: Registered protocol family 17
[17179591.328000] lp: driver loaded but no devices found
[17179591.424000] Adding 1132540k swap on /dev/hda5.  Priority:-1 extents:1 across:1132540k
[17179592.096000] EXT3 FS on hda1, internal journal
[17179592.284000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179592.284000] md: bitmap version 4.39
[17179592.936000] NET: Registered protocol family 10
[17179592.936000] lo: Disabled Privacy Extensions
[17179592.936000] IPv6 over IPv4 tunneling driver
[17179592.988000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179593.132000] rix 192 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 192 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 192 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<6>cdrom: open failed.
[17179598.796000] ACPI: AC Adapter [ACAD] (on-line)
[17179598.876000] ACPI: Battery Slot [BAT1] (battery present)
[17179598.964000] ACPI: Power Button (FF) [PWRF]
[17179598.964000] ACPI: Power Button (CM) [PWRB]
[17179598.964000] ACPI: Sleep Button (CM) [SLPB]
[17179598.964000] ACPI: Lid Switch [LID]
[17179599.052000] ibm_acpi: ec object not found
[17179599.084000] pcc_acpi: loading...
[17179599.120000] wmi_add device=d7e37800
[17179599.120000] calling WQBA
[17179599.172000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179599.684000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
[17179599.684000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa (1300 mV)
[17179599.684000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc (1250 mV)
[17179599.684000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x13 (1075 mV)
[17179599.684000] cpu_init done, current fid 0xa, vid 0xa
[17179603.100000] ath0: no IPv6 routers present
[17179603.384000] eth0: no IPv6 routers present
[17179603.920000] [drm] Initialized drm 1.0.1 20051102
[17179604.860000] ppdev: user-space parallel port driver
[17179605.424000] apm: BIOS not found.
[17179609.124000] Bluetooth: Core ver 2.8
[17179609.124000] NET: Registered protocol family 31
[17179609.124000] Bluetooth: HCI device and connection manager initialized
[17179609.124000] Bluetooth: HCI socket layer initialized
[17179609.252000] Bluetooth: L2CAP ver 2.8
[17179609.252000] Bluetooth: L2CAP socket layer initialized
[17179609.320000] Bluetooth: RFCOMM socket layer initialized
[17179609.320000] Bluetooth: RFCOMM TTY layer initialized
[17179609.320000] Bluetooth: RFCOMM ver 1.7
[17179925.900000] rix 192 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 192 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 192 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 192 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 192 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 192 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240<4>rix 255 (0) bad ratekbps 0 mode 3635158240

```

---

