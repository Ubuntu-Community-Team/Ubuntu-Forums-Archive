---
title: "Wireless button stays orange AMD/Ubuntu14.04/HP Envy dv7"
date: 2018-07-09
forum: Networking &amp; Wireless
---

### Post by insert.memories.here on 2018-07-09
Hello all :) It's my first time posting in this forum community, so I would like to say firstly that I'm happy to be here.
I'm also a novice to everything involved with linux.
So with that being said, here's my problem..
[URL="https://ubuntuforums.org/showthread.php?p=6183681"]
I've written this post based on this procedure[/URL]

1) Machine Brand and Model
```
HP Envy dv7 Laptop
```
2) Wireless Brand, Model and Chipset

LSPCI:

I'm not sure if the wireless brand is either: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)

```
$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7660G]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0)
00:15.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 2)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)

```

or AMD

```
$ lspci -nn | grep AMD
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex [1022:1410]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7660G] [1002:9900]
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller [1002:9902]
00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port [1022:1414]
00:10.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7812] (rev 03)
00:10.1 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7812] (rev 03)
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7804]
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:780b] (rev 14)
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 01)
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:780e] (rev 11)
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge [1022:780f] (rev 40)
00:15.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0) [1022:43a0]
00:15.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 2) [1022:43a2]
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0 [1022:1400]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1 [1022:1401]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2 [1022:1402]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3 [1022:1403]
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4 [1022:1404]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5 [1022:1405]

```

LSUSB:

```
$ lsusb
Bus 001 Device 003: ID 04f2:b2f8 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 138a:0018 Validity Sensors, Inc. Fingerprint scanner
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

3) interface
IFCONFIG:

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:2e:5f:79:8d:67  
          inet addr:192.168.1.72  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2600:1700:2770:6fc0::7bd/128 Scope:Global
          inet6 addr: 2600:1700:2770:6fc0:a2e:5fff:fe79:8d67/64 Scope:Global
          inet6 addr: 2600:1700:2770:6fc0:a4ca:b447:3587:2e53/64 Scope:Global
          inet6 addr: fe80::a2e:5fff:fe79:8d67/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1143267 errors:0 dropped:1 overruns:0 frame:0
          TX packets:318817 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1286769830 (1.2 GB)  TX bytes:39675738 (39.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:18539 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:2108363 (2.1 MB)  TX bytes:2108363 (2.1 MB)


```

IWCONFIG WLAN0:

```
$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

4) Wireless Modules

LSMOD:
```
$ lsmod
Module                  Size  Used by
rfcomm                 69632  0 
bnep                   20480  2 
bluetooth             516096  10 bnep,rfcomm
uvcvideo               90112  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              180224  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
arc4                   16384  2 
snd_hda_codec_idt      57344  1 
snd_hda_codec_generic    73728  1 snd_hda_codec_idt
snd_hda_codec_hdmi     53248  1 
snd_hda_intel          40960  7 
ath9k                 143360  0 
snd_hda_codec         135168  4 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
ath9k_common           36864  1 ath9k
ath9k_hw              471040  2 ath9k_common,ath9k
snd_pcm               106496  5 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0 
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
mac80211              733184  1 ath9k
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
cfg80211              561152  4 ath,ath9k_common,ath9k,mac80211
hp_wmi                 16384  0 
snd_timer              32768  2 snd_pcm,snd_seq
sparse_keymap          16384  1 hp_wmi
kvm                   536576  0 
rtsx_pci_ms            20480  0 
snd                    81920  24 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
memstick               20480  1 rtsx_pci_ms
k10temp                16384  0 
irqbypass              16384  1 kvm
soundcore              16384  1 snd
joydev                 20480  0 
input_leds             16384  0 
hp_wireless            16384  0 
serio_raw              16384  0 
hp_accel               28672  0 
i2c_piix4              24576  0 
shpchp                 36864  0 
lis3lv02d              20480  1 hp_accel
input_polldev          16384  1 lis3lv02d
parport_pc             36864  0 
ppdev                  20480  0 
mac_hid                16384  0 
lp                     20480  0 
parport                49152  3 lp,ppdev,parport_pc
drbg                   28672  1 
ansi_cprng             16384  0 
dm_crypt               28672  1 
rtsx_pci_sdmmc         24576  0 
amdkfd                131072  1 
amd_iommu_v2           20480  1 amdkfd
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
ghash_clmulni_intel    16384  0 
radeon               1503232  4 
aesni_intel           167936  6099 
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3052 ghash_clmulni_intel,aesni_intel,ablk_helper
i2c_algo_bit           16384  1 radeon
ttm                    94208  1 radeon
psmouse               131072  0 
ahci                   36864  2 
drm_kms_helper        151552  1 radeon
libahci                32768  1 ahci
r8169                  81920  0 
syscopyarea            16384  1 drm_kms_helper
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
sysfillrect            16384  1 drm_kms_helper
mii                    16384  1 r8169
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   360448  7 ttm,drm_kms_helper,radeon
wmi                    20480  1 hp_wmi
fjes                   28672  0 
video                  40960  0 

```

Pretty sure hp_wireless is a wireless module:

```
$ lsmod | grep hp_wireless
hp_wireless            16384  0 

```

or hp_wmi:

```
$ lsmod | grep hp_wmi
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
wmi                    20480  1 hp_wmi

```

5) Kernel Boot Messages

DMESG:

Now I'm certain it's hp_wmi:

```
$ dmesg | grep hp_wmi
[  141.598859] hp_wmi: Unknown event_id - 0 - 0x0
[  141.599230] hp_wmi: Unknown event_id - 0 - 0x0
[  141.599349] hp_wmi: Unknown event_id - 0 - 0x0

```

...but if not, here's the rest:

```
[    1.217782] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.219574] ACPI: Battery Slot [BAT0] (battery present)
[    1.224785] Linux agpgart interface v0.103
[    1.232122] loop: module loaded
[    1.233029] libphy: Fixed MDIO Bus: probed
[    1.233039] tun: Universal TUN/TAP device driver, 1.6
[    1.233043] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.233300] PPP generic driver version 2.4.2
[    1.233514] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.233526] ehci-pci: EHCI PCI platform driver
[    1.233871] QUIRK: Enable AMD PLL fix
[    1.233936] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.233957] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.233969] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.233999] ehci-pci 0000:00:12.2: debug port 1
[    1.234073] ehci-pci 0000:00:12.2: irq 17, io mem 0xf034c000
[    1.244889] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.245062] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.245070] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.245076] usb usb1: Product: EHCI Host Controller
[    1.245082] usb usb1: Manufacturer: Linux 4.4.0-93-generic ehci_hcd
[    1.245087] usb usb1: SerialNumber: 0000:00:12.2
[    1.245651] hub 1-0:1.0: USB hub found
[    1.245671] hub 1-0:1.0: 5 ports detected
[    1.246519] ehci-platform: EHCI generic platform driver
[    1.246571] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.246582] ohci-pci: OHCI PCI platform driver
[    1.246947] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.246964] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 2
[    1.247024] ohci-pci 0000:00:12.0: irq 18, io mem 0xf034d000
[    1.304981] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.304993] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.305000] usb usb2: Product: OHCI PCI host controller
[    1.305006] usb usb2: Manufacturer: Linux 4.4.0-93-generic ohci_hcd
[    1.305011] usb usb2: SerialNumber: 0000:00:12.0
[    1.305585] hub 2-0:1.0: USB hub found
[    1.305651] hub 2-0:1.0: 5 ports detected
[    1.306436] ohci-platform: OHCI generic platform driver
[    1.306483] uhci_hcd: USB Universal Host Controller Interface driver
[    1.306898] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.306919] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 3
[    1.307153] xhci_hcd 0000:00:10.0: hcc params 0x014042c3 hci version 0x96 quirks 0x00000608
[    1.307509] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.307516] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.307521] usb usb3: Product: xHCI Host Controller
[    1.307527] usb usb3: Manufacturer: Linux 4.4.0-93-generic xhci-hcd
[    1.307532] usb usb3: SerialNumber: 0000:00:10.0
[    1.308003] hub 3-0:1.0: USB hub found
[    1.308036] hub 3-0:1.0: 2 ports detected
[    1.308341] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.308352] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 4
[    1.310553] usb usb4: We don't know the algorithms for LPM for this host, disabling LPM.
[    1.310610] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.310616] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.310622] usb usb4: Product: xHCI Host Controller
[    1.310627] usb usb4: Manufacturer: Linux 4.4.0-93-generic xhci-hcd
[    1.310632] usb usb4: SerialNumber: 0000:00:10.0
[    1.311109] hub 4-0:1.0: USB hub found
[    1.311145] hub 4-0:1.0: 2 ports detected
[    1.311709] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.311724] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 5
[    1.311938] xhci_hcd 0000:00:10.1: hcc params 0x014042c3 hci version 0x96 quirks 0x00000608
[    1.312262] usb usb5: New USB device found, idVendor=1d6b, idProduct=0002
[    1.312269] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.312274] usb usb5: Product: xHCI Host Controller
[    1.312279] usb usb5: Manufacturer: Linux 4.4.0-93-generic xhci-hcd
[    1.312284] usb usb5: SerialNumber: 0000:00:10.1
[    1.312788] hub 5-0:1.0: USB hub found
[    1.312808] hub 5-0:1.0: 2 ports detected
[    1.313100] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.313111] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 6
[    1.315353] usb usb6: We don't know the algorithms for LPM for this host, disabling LPM.
[    1.315410] usb usb6: New USB device found, idVendor=1d6b, idProduct=0003
[    1.315416] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.315421] usb usb6: Product: xHCI Host Controller
[    1.315427] usb usb6: Manufacturer: Linux 4.4.0-93-generic xhci-hcd
[    1.315431] usb usb6: SerialNumber: 0000:00:10.1
[    1.315930] hub 6-0:1.0: USB hub found
[    1.315963] hub 6-0:1.0: 2 ports detected
[    1.316382] i8042: PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.340582] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.340594] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.341137] mousedev: PS/2 mouse device common for all mice
[    1.342392] rtc_cmos 00:01: RTC can wake from S4
[    1.342648] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.342685] rtc_cmos 00:01: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.342713] i2c /dev entries driver
[    1.342901] device-mapper: uevent: version 1.0.3
[    1.343261] device-mapper: ioctl: 4.34.0-ioctl (2015-10-28) initialised: dm-devel@redhat.com
[    1.343315] ledtrig-cpu: registered to indicate activity on CPUs
[    1.344542] NET: Registered protocol family 10
[    1.345324] NET: Registered protocol family 17
[    1.345370] Key type dns_resolver registered
[    1.346121] microcode: CPU0: patch_level=0x06001116
[    1.346191] microcode: CPU1: patch_level=0x06001116
[    1.346298] microcode: CPU2: patch_level=0x06001116
[    1.346324] microcode: CPU3: patch_level=0x06001116
[    1.346459] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.347016] registered taskstats version 1
[    1.347058] Loading compiled-in X.509 certificates
[    1.350366] Loaded X.509 cert 'Build time autogenerated kernel key: edb476a8777da943159b94e658ffa41a270913b7'
[    1.350429] zswap: loaded using pool lzo/zbud
[    1.356765] Key type trusted registered
[    1.368580] Key type encrypted registered
[    1.368611] AppArmor: AppArmor sha1 policy hashing enabled
[    1.368624] ima: No TPM chip found, activating TPM-bypass!
[    1.368742] evm: HMAC attrs: 0x1
[    1.369696]   Magic number: 10:187:883
[    1.369892] rtc_cmos 00:01: setting system clock to 2018-07-09 11:52:22 UTC (1531137142)
[    1.370359] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.370931] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.370935] EDD information not available.
[    1.371195] PM: Hibernation image not present or could not be loaded.
[    1.374598] Freeing unused kernel memory: 1496K (ffffffff81f48000 - ffffffff820be000)
[    1.374604] Write protecting the kernel read-only data: 14336k
[    1.376859] Freeing unused kernel memory: 1960K (ffff880001816000 - ffff880001a00000)
[    1.377719] Freeing unused kernel memory: 92K (ffff880001de9000 - ffff880001e00000)
[    1.377957] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.408484] systemd-udevd[119]: starting version 204
[    1.421918] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    1.421928] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.421961] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    1.422376] acpi device:00: registered as cooling_device4
[    1.422474] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    1.434747] wmi: Mapper loaded
[    1.441278] [drm] Initialized drm 1.1.0 20060810
[    1.447097] rtsx_pci 0000:05:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 35
[    1.448069] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.448919] r8169 0000:04:00.0 eth0: RTL8168evl/8111evl at 0xffffc9000001c000, 08:2e:5f:79:8d:67, XID 0c900800 IRQ 36
[    1.448924] r8169 0000:04:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.451992] ahci 0000:00:11.0: version 3.0
[    1.452240] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    1.452245] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.452966] scsi host0: ahci
[    1.453159] scsi host1: ahci
[    1.453264] ata1: SATA max UDMA/133 abar m2048@0xf034e000 port 0xf034e100 irq 37
[    1.453268] ata2: SATA max UDMA/133 abar m2048@0xf034e000 port 0xf034e180 irq 37
[    1.474123] AVX version of gcm_enc/dec engaged.
[    1.474127] AES CTR mode by8 optimization enabled
[    1.487981] [drm] radeon kernel modesetting enabled.
[    1.490781] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[    1.490785] AMD IOMMUv2 functionality not available on this system
[    1.494845] CRAT table not found
[    1.494849] Finished initializing topology ret=0
[    1.494906] kfd kfd: Initialized module
[    1.495199] checking generic (e0000000 580000) vs hw (e0000000 10000000)
[    1.495202] fb: switching to radeondrmfb from VESA VGA
[    1.495245] Console: switching to colour dummy device 80x25
[    1.495904] [drm] initializing kernel modesetting (ARUBA 0x1002:0x9900 0x103C:0x1833).
[    1.495919] [drm] register mmio base: 0xF0300000
[    1.495920] [drm] register mmio size: 262144
[    1.496891] ATOM BIOS: HP
[    1.496957] radeon 0000:00:01.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    1.496960] radeon 0000:00:01.0: GTT: 1024M 0x0000000020000000 - 0x000000005FFFFFFF
[    1.496962] [drm] Detected VRAM RAM=512M, BAR=256M
[    1.496964] [drm] RAM width 64bits DDR
[    1.497058] [TTM] Zone  kernel: Available graphics memory: 3813568 kiB
[    1.497064] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    1.497066] [TTM] Initializing pool allocator
[    1.497089] [TTM] Initializing DMA pool allocator
[    1.497120] [drm] radeon: 512M of VRAM memory ready
[    1.497122] [drm] radeon: 1024M of GTT memory ready.
[    1.497144] [drm] Loading ARUBA Microcode
[    1.497213] [drm] Internal thermal controller without fan control
[    1.497404] [drm] radeon: dpm initialized
[    1.498892] [drm] Found VCE firmware/feedback version 50.0.1 / 17!
[    1.498904] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    1.543270] [drm] PCIE GART of 1024M enabled (table at 0x00000000002E8000).
[    1.543411] radeon 0000:00:01.0: WB enabled
[    1.543416] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff88021087bc00
[    1.544147] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90001035a18
[    1.564192] radeon 0000:00:01.0: fence driver on ring 6 use gpu addr 0x0000000020000c18 and cpu addr 0xffff88021087bc18
[    1.564195] radeon 0000:00:01.0: fence driver on ring 7 use gpu addr 0x0000000020000c1c and cpu addr 0xffff88021087bc1c
[    1.564197] radeon 0000:00:01.0: fence driver on ring 1 use gpu addr 0x0000000020000c04 and cpu addr 0xffff88021087bc04
[    1.564200] radeon 0000:00:01.0: fence driver on ring 2 use gpu addr 0x0000000020000c08 and cpu addr 0xffff88021087bc08
[    1.564202] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff88021087bc0c
[    1.564204] radeon 0000:00:01.0: fence driver on ring 4 use gpu addr 0x0000000020000c10 and cpu addr 0xffff88021087bc10
[    1.564207] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.564208] [drm] Driver supports precise vblank timestamp query.
[    1.564210] radeon 0000:00:01.0: radeon: MSI limited to 32-bit
[    1.564248] radeon 0000:00:01.0: radeon: using MSI.
[    1.564277] [drm] radeon: irq initialized.
[    1.582952] [drm] ring test on 0 succeeded in 2 usecs
[    1.582960] [drm] ring test on 3 succeeded in 3 usecs
[    1.582966] [drm] ring test on 4 succeeded in 3 usecs
[    1.628732] [drm] ring test on 5 succeeded in 1 usecs
[    1.648723] [drm] UVD initialized successfully.
[    1.758794] [drm] ring test on 6 succeeded in 16 usecs
[    1.758807] [drm] ring test on 7 succeeded in 4 usecs
[    1.758808] [drm] VCE initialized successfully.
[    1.759307] [drm] ib test on ring 0 succeeded in 0 usecs
[    1.759345] [drm] ib test on ring 3 succeeded in 0 usecs
[    1.759381] [drm] ib test on ring 4 succeeded in 0 usecs
[    1.832888] usb 2-3: new full-speed USB device number 2 using ohci-pci
[    1.944894] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.944926] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.951438] ata1.00: ATA-9: ST750LM022 HN-M750MBB, 2AR10002, max UDMA/133
[    1.951443] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.957875] ata1.00: configured for UDMA/133
[    1.958247] scsi 0:0:0:0: Direct-Access     ATA      ST750LM022 HN-M7 0002 PQ: 0 ANSI: 5
[    1.958560] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/699 GiB)
[    1.958563] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.958636] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.958700] sd 0:0:0:0: [sda] Write Protect is off
[    1.958704] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.958760] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.962253] ata2.00: ATAPI: hp      DVD-RAM UJ8B1, H.03, max UDMA/100
[    1.987981] ata2.00: configured for UDMA/100
[    1.998076] usb 2-3: New USB device found, idVendor=138a, idProduct=0018
[    1.998082] usb 2-3: New USB device strings: Mfr=0, Product=0, SerialNumber=1
[    1.998085] usb 2-3: SerialNumber: 2b15bdecdfd6
[    1.999812] scsi 1:0:0:0: CD-ROM            hp       DVD-RAM UJ8B1    H.03 PQ: 0 ANSI: 5
[    2.001375]  sda: sda1 sda2 < sda5 >
[    2.002039] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.039931] sr 1:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.039937] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.040225] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.040358] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.172763] tsc: Refined TSC clocksource calibration: 2295.710 MHz
[    2.172769] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x21176069fe1, max_idle_ns: 440795205789 ns
[    2.276904] [drm] ib test on ring 5 succeeded
[    2.480835] usb 1-4: new high-speed USB device number 3 using ehci-pci
[    2.486605] psmouse serio1: synaptics: queried max coordinates: x [..5666], y [..4772]
[    2.538820] psmouse serio1: synaptics: queried min coordinates: x [1274..], y [1080..]
[    2.635709] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x26c00/0x0, board id: 2055, fw id: 1107424
[    2.697199] usb 1-4: New USB device found, idVendor=04f2, idProduct=b2f8
[    2.697205] usb 1-4: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    2.697208] usb 1-4: Product: HP Truevision HD
[    2.697211] usb 1-4: Manufacturer: Chicony Electronics Co.,Ltd.
[    2.697213] usb 1-4: SerialNumber: 0x0001
[    2.697323] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    2.796861] [drm] ib test on ring 6 succeeded
[    3.173168] clocksource: Switched to clocksource tsc
[    3.296902] [drm] ib test on ring 7 succeeded
[    3.300726] [drm] radeon atom DIG backlight initialized
[    3.300731] [drm] Radeon Display Connectors
[    3.300733] [drm] Connector 0:
[    3.300734] [drm]   LVDS-1
[    3.300736] [drm]   HPD1
[    3.300738] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[    3.300739] [drm]   Encoders:
[    3.300741] [drm]     LCD1: INTERNAL_UNIPHY2
[    3.300742] [drm]     LCD1: TRAVIS
[    3.300743] [drm] Connector 1:
[    3.300744] [drm]   VGA-1
[    3.300745] [drm]   HPD2
[    3.300747] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[    3.300748] [drm]   Encoders:
[    3.300749] [drm]     CRT1: INTERNAL_UNIPHY2
[    3.300750] [drm]     CRT1: NUTMEG
[    3.300751] [drm] Connector 2:
[    3.300752] [drm]   HDMI-A-1
[    3.300753] [drm]   HPD4
[    3.300755] [drm]   DDC: 0x6560 0x6560 0x6564 0x6564 0x6568 0x6568 0x656c 0x656c
[    3.300756] [drm]   Encoders:
[    3.300757] [drm]     DFP1: INTERNAL_UNIPHY
[    3.502127] [drm] fb mappable at 0xE04EC000
[    3.502131] [drm] vram apper at 0xE0000000
[    3.502133] [drm] size 5787648
[    3.502134] [drm] fb depth is 24
[    3.502136] [drm]    pitch is 6400
[    3.502301] fbcon: radeondrmfb (fb0) is primary device
[    3.502402] Console: switching to colour frame buffer device 200x56
[    3.502438] radeon 0000:00:01.0: fb0: radeondrmfb frame buffer device
[    3.513516] [drm] Initialized radeon 2.43.0 20080528 for 0000:00:01.0 on minor 0
[   11.052151] random: nonblocking pool is initialized
[   21.469964] EXT4-fs (dm-1): INFO: recovery required on readonly filesystem
[   21.469969] EXT4-fs (dm-1): write access will be enabled during recovery
[   24.140340] EXT4-fs (dm-1): orphan cleanup on readonly fs
[   24.140417] EXT4-fs (dm-1): 1 orphan inode deleted
[   24.140419] EXT4-fs (dm-1): recovery complete
[   24.246399] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[   38.439958] systemd-udevd[455]: starting version 204
[   39.806634] lp: driver loaded but no devices found
[   39.843898] ppdev: user-space parallel port driver
[   40.196479] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   40.200642] ACPI Warning: SystemIO range 0x0000000000000B00-0x0000000000000B08 conflicts with OpRegion 0x0000000000000B00-0x0000000000000B0F (\_SB_.PCI0.SMBS.SMB0) (20150930/utaddress-254)
[   40.200651] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   40.318042] hp_accel: laptop model unknown, using default axes configuration
[   40.352941] lis3lv02d: 8 bits 3DC sensor found
[   40.388451] Initializing HPQ6001 module
[   40.388586] input: HP Wireless hotkeys as /devices/virtual/input/input7
[   40.426093] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input8
[   40.752069] kvm: disabled by bios
[   40.778890] kvm: disabled by bios
[   40.814687] kvm: disabled by bios
[   40.846927] kvm: disabled by bios
[   41.666420] audit: type=1400 audit(1531151582.797:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=565 comm="apparmor_parser"
[   41.666430] audit: type=1400 audit(1531151582.797:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=565 comm="apparmor_parser"
[   41.666435] audit: type=1400 audit(1531151582.797:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=565 comm="apparmor_parser"
[   41.666468] audit: type=1400 audit(1531151582.797:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=564 comm="apparmor_parser"
[   41.666480] audit: type=1400 audit(1531151582.797:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=564 comm="apparmor_parser"
[   41.666486] audit: type=1400 audit(1531151582.797:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=564 comm="apparmor_parser"
[   41.687027] input: HP WMI hotkeys as /devices/virtual/input/input9
[   42.336570] ath: phy0: Enable LNA combining
[   42.337651] ath: phy0: ASPM enabled: 0x42
[   42.337655] ath: EEPROM regdomain: 0x60
[   42.337657] ath: EEPROM indicates we should expect a direct regpair map
[   42.337660] ath: Country alpha2 being used: 00
[   42.337662] ath: Regpair used: 0x60
[   42.368750] snd_hda_intel 0000:00:01.1: Force to non-snoop mode
[   42.382806] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input10
[   42.390558] cfg80211: World regulatory domain updated:
[   42.390564] cfg80211:  DFS Master region: unset
[   42.390566] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   42.390569] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   42.390572] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   42.390574] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   42.390576] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   42.390579] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   42.566193] snd_hda_codec_idt hdaudioC1D0: autoconfig for 92HD91BXX: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[   42.566199] snd_hda_codec_idt hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   42.566202] snd_hda_codec_idt hdaudioC1D0:    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
[   42.566205] snd_hda_codec_idt hdaudioC1D0:    mono: mono_out=0x0
[   42.566207] snd_hda_codec_idt hdaudioC1D0:    inputs:
[   42.566210] snd_hda_codec_idt hdaudioC1D0:      Internal Mic=0x11
[   42.566212] snd_hda_codec_idt hdaudioC1D0:      Mic=0xa
[   42.604608] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input11
[   42.605801] input: HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input12
[   42.612656] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   42.613264] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xffffc90001c00000, irq=16
[   43.528300] media: Linux media interface: v0.10
[   43.904939] Linux video capture interface: v2.00
[   44.490450] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
[   44.776017] uvcvideo: Found UVC 1.00 device HP Truevision HD (04f2:b2f8)
[   44.788010] input: HP Truevision HD as /devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4:1.0/input/input13
[   44.788121] usbcore: registered new interface driver uvcvideo
[   44.788124] USB Video Class driver (1.1.1)
[   44.991661] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   45.358260] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   46.298893] init: failsafe main process (774) killed by TERM signal
[   47.666041] audit: type=1400 audit(1531151588.797:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1003 comm="apparmor_parser"
[   47.666055] audit: type=1400 audit(1531151588.797:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1003 comm="apparmor_parser"
[   47.666063] audit: type=1400 audit(1531151588.797:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1003 comm="apparmor_parser"
[   47.669045] audit: type=1400 audit(1531151588.797:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1007 comm="apparmor_parser"
[   47.670774] audit: type=1400 audit(1531151588.801:12): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1002 comm="apparmor_parser"
[   47.670784] audit: type=1400 audit(1531151588.801:13): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//chromium" pid=1002 comm="apparmor_parser"
[   47.674827] audit: type=1400 audit(1531151588.805:14): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1008 comm="apparmor_parser"
[   47.674839] audit: type=1400 audit(1531151588.805:15): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=1008 comm="apparmor_parser"
[   47.676234] audit: type=1400 audit(1531151588.805:16): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=1010 comm="apparmor_parser"
[   47.738154] audit: type=1400 audit(1531151588.869:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=1006 comm="apparmor_parser"
[   48.757855] Bluetooth: Core ver 2.21
[   48.757884] NET: Registered protocol family 31
[   48.757887] Bluetooth: HCI device and connection manager initialized
[   48.757893] Bluetooth: HCI socket layer initialized
[   48.757897] Bluetooth: L2CAP socket layer initialized
[   48.757906] Bluetooth: SCO socket layer initialized
[   49.189050] init: cups main process (1044) killed by HUP signal
[   49.189069] init: cups main process ended, respawning
[   49.212372] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   49.212377] Bluetooth: BNEP filters: protocol multicast
[   49.212383] Bluetooth: BNEP socket layer initialized
[   49.386248] Bluetooth: RFCOMM TTY layer initialized
[   49.386258] Bluetooth: RFCOMM socket layer initialized
[   49.386265] Bluetooth: RFCOMM ver 1.11
[   54.534243] init: samba-ad-dc main process (1346) terminated with status 1
[   55.451142] r8169 0000:04:00.0 eth0: link down
[   55.451216] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   58.237572] init: plymouth-upstart-bridge main process ended, respawning
[   58.248189] init: plymouth-upstart-bridge main process (1486) terminated with status 1
[   58.248204] init: plymouth-upstart-bridge main process ended, respawning
[   62.635069] init: anacron main process (1184) killed by TERM signal
[   78.245428] audit_printk_skb: 54 callbacks suppressed
[   78.245432] audit: type=1400 audit(1531151619.377:36): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1855 comm="apparmor_parser"
[   78.245442] audit: type=1400 audit(1531151619.377:37): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1855 comm="apparmor_parser"
[  120.611208] audit: type=1400 audit(1531151661.745:38): apparmor="DENIED" operation="exec" profile="/usr/share/hplip/systray.py" name="/usr/bin/curl" pid=2453 comm="hp-upgrade" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
[  120.792393] audit: type=1400 audit(1531151661.929:39): apparmor="DENIED" operation="exec" profile="/usr/share/hplip/systray.py" name="/bin/ping" pid=2454 comm="hp-upgrade" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
[  141.598859] hp_wmi: Unknown event_id - 0 - 0x0
[  141.599230] hp_wmi: Unknown event_id - 0 - 0x0
[  141.599349] hp_wmi: Unknown event_id - 0 - 0x0
[  150.650411] r8169 0000:04:00.0 eth0: link up
[  150.650429] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  173.116418] r8169 0000:04:00.0 eth0: link down
[  383.265066] r8169 0000:04:00.0 eth0: link up
[  522.699130] r8169 0000:04:00.0 eth0: link down
[  630.498021] audit: type=1400 audit(1531152170.700:40): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=4466 comm="apparmor_parser"
[  630.498037] audit: type=1400 audit(1531152170.700:41): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=4466 comm="apparmor_parser"
[ 1473.680906] systemd-hostnamed[5291]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 1612.722927] r8169 0000:04:00.0 eth0: link up
[ 1881.476897] systemd-hostnamed[5537]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!

```



6) Network configuration

```
~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:e5:43:a4:29:a9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.4.0-93-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f0200000-f027ffff memory:f0280000-f028ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 07
       serial: 08:2e:5f:79:8d:67
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 latency=0 multicast=yes
       resources: irq:36 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

```

7) Networks Scanned

```
$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

eth0      Interface doesn't support scanning.

```

8) Ubuntu Version

```
$ lsb_release -d
Description:    Ubuntu 14.04.5 LTS

```

9) Kernel/architecture

```
$ uname -mr
4.4.0-93-generic x86_64

```

10) Restarting network

```
$ sudo service networking restart
stop: Job failed while stopping
start: Job is already running: networking

```

[B]..........

[/B]That's about it...
Please tell me there's a drive for this if it comes down to it :(

Additional info:

[LIST]
[*]My laptop doesn't have a wireless switch (or any additional hidden buttons, at least I don't think it does) 
[*]The computer came with Windows 8 before I switched it over completely, the wireless button had issues then as well.
[LIST]
[*]I had to press fn and f12 keys repeatedly during boot up 
[/LIST]
      
[/LIST]

---

### Post by insert.memories.here on 2018-07-14
Really? Nobody?


Well, at least this gets archived for others with this same problem to look up, so when I find a solution, I'll post it right here.

---

### Post by jeremy31 on 2018-07-14
Moved to Networking and Wireless

---

### Post by chili555 on 2018-07-14
When Jeremy doesn't propose an answer, you know it's a very tough problem!

This, of course, is the real problem:> [  141.598859] hp_wmi: Unknown event_id - 0 - 0x0
[  141.599230] hp_wmi: Unknown event_id - 0 - 0x0
[  141.599349] hp_wmi: Unknown event_id - 0 - 0x0The usual helper module, hp-wmi, doesn't know to translate the key press into action, namely, turn on the wireless radio.

The issue of HP wireless being inoperable because of a hard block and therefore the usual wireless key not toggling wireless on and off is long-standing. There are only a few things you can try.

First, try removing the helper module hp_wmi and then try to switch the wireless on with the key combination. 

You could also try:
```
sudo modprobe -r hp_wmi
sudo rfkill unblock all
rfkill list all

```
Second, check the user guide for your HP laptop and be certain that the wireless key combination you are using is correct. Be certain that you are not using Fn+F12, for example, if the user guide says it is simply F12. On the other hand, if you are certain you are using the correct sequence, try the wrong sequence as an experiment; i.e., use Fn+F12 (or whatever your sequence is) if the user guide says it’s F12 and vice versa.

Next, you can remove the card, tape off pin 20 and re-insert it: [https://ubuntuforums.org/showthread.php?t=2150597](https://ubuntuforums.org/showthread.php?t=2150597)

You can, if all these steps fail, file a bug report against the module hp_wmi: [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

Finally, in many, but not every case, a USB wireless will also be hard blocked for the same reasons. If you want to try one, be certain to try it within a return period.

I regret that there isn’t a better answer for HP laptops.

---

