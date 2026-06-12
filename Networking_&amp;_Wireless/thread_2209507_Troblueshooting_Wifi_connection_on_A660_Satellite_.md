---
title: "Troblueshooting Wifi connection on A660 Satellite Ubuntu 12.10"
date: 2014-03-06
forum: Networking &amp; Wireless
---

### Post by jaykob_hxc2 on 2014-03-06
Hi there,

I'm currently dual booting with Windows 7 64 bit and Ubuntu 12.10. Today has been the first time I've used Ubuntu in a while. I tried activating the Wifi on my laptop (A Toshiba Satellite A660) however It doesn't seem to work. 

On the toshiba it has a row of soft buttons on the top including a wireless button. When I press the button all it seems to do in Ubuntu is activate the Bluetooth and not the wirless connections. I have tried the shortcut FN + F8 with no help there. 

I have internet working fine on my Windows (I'm currently writing this on it now) however wireless isn't working at all for Ubuntu. The downside is that I don't have a wired connection to help install additional software to aid my problem.

Any help would be greatly appreciated and thank-you for helping in advance

Jake

---

### Post by papibe on 2014-03-06
Hi jaykob_hxc2. Welcome to the forum ):P

Could you open a terminal, run this command, and post back its results? (you can copy/paste the text):
```
rfkill list
```
Regards.

---

### Post by jaykob_hxc2 on 2014-03-06
I'll have that for you shortly. I just read this post as well [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) and i'l give you this information. As for the command "sudo service networking restart" it just seems to do analogous to ending expolorer.exe in Windows.[B]

lspci[/B]
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GT216 [GeForce GT 330M] (rev a2)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
07:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
16:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
16:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20)
16:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
16:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```

[B]lsusb
[/B]```

Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b1e4 Chicony Electronics Co., Ltd
Bus 001 Device 004: ID 1164:0871 YUAN High-Tech Development Co., Ltd
Bus 001 Device 005: ID 0930:0214 Toshiba Corp.
Bus 002 Device 003: ID 0951:1607 Kingston Technology DataTraveler 100

```

[B]ifconfig
[/B]```


eth0      Link encap:Ethernet  HWaddr 1c:75:08:7a:af:83 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:16544 (16.5 KB)  TX bytes:16544 (16.5 KB)

```

[B]iwconfig
[/B]```

eth0      no wireless extensions.
 
lo        no wireless extensions.

```

[B]lsmod
[/B]```

Module                  Size  Used by
nls_iso8859_1          12714  1
joydev                 17458  0
rfcomm                 46620  12
rc_dib0700_rc5         12509  0
tuner_xc2028           31201  1
btusb                  22475  0
bnep                   18141  2
bluetooth             209297  22 rfcomm,btusb,bnep
parport_pc             32689  0
coretemp               13401  0
ppdev                  17074  0
kvm_intel             132760  0
nouveau               896008  1
kvm                   414111  1 kvm_intel
dvb_usb_dib0700       148702  0
snd_hda_codec_hdmi     32049  1
snd_hda_codec_realtek    78147  1
i915                  520799  8
ttm                    83596  1 nouveau
dib0090                38609  1 dvb_usb_dib0700
dib7000p               38382  2 dvb_usb_dib0700
dib7000m               23034  1 dvb_usb_dib0700
dib0070                18233  1 dvb_usb_dib0700
uvcvideo               76750  0
videobuf2_core         32852  1 uvcvideo
snd_hda_intel          33492  3
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
drm_kms_helper         49113  2 nouveau,i915
drm                   288972  7 nouveau,i915,ttm,drm_kms_helper
dvb_usb                24261  1 dvb_usb_dib0700
videodev              120310  2 uvcvideo,videobuf2_core
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
dib8000                52679  1 dvb_usb_dib0700
psmouse               100424  0
dvb_core              110324  3 dib7000p,dvb_usb,dib8000
snd_seq_midi           13325  0
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15048  1 snd
dib3000mc              23240  1 dvb_usb_dib0700
dibx000_common         18753  5 dvb_usb_dib0700,dib7000p,dib7000m,dib8000,dib3000mc
videobuf2_vmalloc      12861  1 uvcvideo
microcode              22804  0
mxm_wmi                13022  1 nouveau
jmb38x_ms              17417  0
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
videobuf2_memops       13405  1 videobuf2_vmalloc
serio_raw              13216  0
memstick               16555  1 jmb38x_ms
i2c_algo_bit           13414  2 nouveau,i915
mei                    40691  0
lpc_ich                17062  0
intel_ips              18244  0
toshiba_acpi           18727  0
sparse_keymap          13891  1 toshiba_acpi
wmi                    19071  3 nouveau,mxm_wmi,toshiba_acpi
ir_lirc_codec          12860  0
lirc_dev               19167  1 ir_lirc_codec
ir_mce_kbd_decoder     12724  0
ir_sanyo_decoder       12514  0
ir_sony_decoder        12511  0
ir_jvc_decoder         12508  0
ir_rc6_decoder         12508  0
ir_rc5_decoder         12508  0
ir_nec_decoder         12508  0
rc_rc6_mce             12503  0
ene_ir                 18321  0
toshiba_bluetooth      12808  0
rc_core                22331  15 rc_dib0700_rc5,dvb_usb_dib0700,dvb_usb,ir_lirc_codec,ir_mce_kbd_decoder,ir_sanyo_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mce,ene_ir
mac_hid                13206  0
lp                     17760  0
video                  19391  2 nouveau,i915
parport                46346  3 parport_pc,ppdev,lp
usb_storage            48839  1
ahci                   25721  3
libahci                31192  1 ahci
sdhci_pci              18617  0
sdhci                  32646  1 sdhci_pci
r8169                  61671  0
 
```

**dmesg**
 ```

[    0.604388] pnp 00:09: [mem 0xfed90000-0xfed8ffff disabled]
[    0.604389] pnp 00:09: [mem 0xfed45000-0xfed8ffff]
[    0.604391] pnp 00:09: [mem 0xff000000-0xffffffff]
[    0.604392] pnp 00:09: [mem 0xfee00000-0xfeefffff]
[    0.604393] pnp 00:09: [mem 0x00000000-0x00000fff]
[    0.604448] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.604449] system 00:09: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.604451] system 00:09: [mem 0xfed16000-0xfed16fff] has been reserved
[    0.604452] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.604456] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.604458] system 00:09: [mem 0x00000000-0x00000fff] could not be reserved
[    0.604459] system 00:09: [mem 0xd6c00000-0xd6c00fff] has been reserved
[    0.604461] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.604462] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.604464] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    0.604465] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.604467] system 00:09: [mem 0x00000000-0x00000fff] could not be reserved
[    0.604469] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.604617] pnp 00:0a: [bus ff]
[    0.604658] pnp 00:0a: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.604665] pnp: PnP ACPI: found 11 devices
[    0.604666] ACPI: ACPI bus type pnp unregistered
[    0.610924] pci 0000:01:00.0: no compatible bridge window for [mem 0xfff80000-0xffffffff pref]
[    0.610980] pci 0000:01:00.0: BAR 6: assigned [mem 0xd1000000-0xd107ffff pref]
[    0.610982] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.610985] pci 0000:00:01.0:   bridge window [io  0x8000-0x8fff]
[    0.610987] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd10fffff]
[    0.610989] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xb1ffffff 64bit pref]
[    0.610993] pci 0000:00:1c.0: PCI bridge to [bus 02-06]
[    0.610995] pci 0000:00:1c.0:   bridge window [io  0x6000-0x7fff]
[    0.610999] pci 0000:00:1c.0:   bridge window [mem 0xd6300000-0xd6afffff]
[    0.611002] pci 0000:00:1c.0:   bridge window [mem 0xd1800000-0xd20fffff 64bit pref]
[    0.611007] pci 0000:00:1c.1: PCI bridge to [bus 07-0b]
[    0.611009] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    0.611013] pci 0000:00:1c.1:   bridge window [mem 0xd5a00000-0xd62fffff]
[    0.611016] pci 0000:00:1c.1:   bridge window [mem 0xd2100000-0xd28fffff 64bit pref]
[    0.611021] pci 0000:00:1c.2: PCI bridge to [bus 0c-10]
[    0.611023] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.611027] pci 0000:00:1c.2:   bridge window [mem 0xd5200000-0xd59fffff]
[    0.611031] pci 0000:00:1c.2:   bridge window [mem 0xd2900000-0xd30fffff 64bit pref]
[    0.611036] pci 0000:00:1c.3: PCI bridge to [bus 11-15]
[    0.611038] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.611042] pci 0000:00:1c.3:   bridge window [mem 0xd4a00000-0xd51fffff]
[    0.611045] pci 0000:00:1c.3:   bridge window [mem 0xd3100000-0xd38fffff 64bit pref]
[    0.611051] pci 0000:00:1c.4: PCI bridge to [bus 16-1a]
[    0.611053] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
[    0.611057] pci 0000:00:1c.4:   bridge window [mem 0xd4100000-0xd49fffff]
[    0.611061] pci 0000:00:1c.4:   bridge window [mem 0xd3900000-0xd40fffff 64bit pref]
[    0.611066] pci 0000:00:1e.0: PCI bridge to [bus 1b-1b]
[    0.611099] pci 0000:00:1c.2: enabling device (0000 -> 0003)
[    0.611108] pci 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.611123] pci 0000:00:1e.0: setting latency timer to 64
[    0.611127] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.611128] pci_bus 0000:00: resource 5 [io  0x0d00-0xfdff]
[    0.611129] pci_bus 0000:00: resource 6 [io  0xff28-0xff2b]
[    0.611131] pci_bus 0000:00: resource 7 [mem 0x000a0000-0x000bffff]
[    0.611132] pci_bus 0000:00: resource 8 [mem 0x9b800000-0xfeafffff]
[    0.611134] pci_bus 0000:01: resource 0 [io  0x8000-0x8fff]
[    0.611135] pci_bus 0000:01: resource 1 [mem 0xd0000000-0xd10fffff]
[    0.611136] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xb1ffffff 64bit pref]
[    0.611138] pci_bus 0000:02: resource 0 [io  0x6000-0x7fff]
[    0.611140] pci_bus 0000:02: resource 1 [mem 0xd6300000-0xd6afffff]
[    0.611141] pci_bus 0000:02: resource 2 [mem 0xd1800000-0xd20fffff 64bit pref]
[    0.611143] pci_bus 0000:07: resource 0 [io  0x5000-0x5fff]
[    0.611144] pci_bus 0000:07: resource 1 [mem 0xd5a00000-0xd62fffff]
[    0.611145] pci_bus 0000:07: resource 2 [mem 0xd2100000-0xd28fffff 64bit pref]
[    0.611147] pci_bus 0000:0c: resource 0 [io  0x4000-0x4fff]
[    0.611148] pci_bus 0000:0c: resource 1 [mem 0xd5200000-0xd59fffff]
[    0.611150] pci_bus 0000:0c: resource 2 [mem 0xd2900000-0xd30fffff 64bit pref]
[    0.611151] pci_bus 0000:11: resource 0 [io  0x3000-0x3fff]
[    0.611153] pci_bus 0000:11: resource 1 [mem 0xd4a00000-0xd51fffff]
[    0.611154] pci_bus 0000:11: resource 2 [mem 0xd3100000-0xd38fffff 64bit pref]
[    0.611156] pci_bus 0000:16: resource 0 [io  0x2000-0x2fff]
[    0.611157] pci_bus 0000:16: resource 1 [mem 0xd4100000-0xd49fffff]
[    0.611158] pci_bus 0000:16: resource 2 [mem 0xd3900000-0xd40fffff 64bit pref]
[    0.611160] pci_bus 0000:1b: resource 4 [io  0x0000-0x0cf7]
[    0.611161] pci_bus 0000:1b: resource 5 [io  0x0d00-0xfdff]
[    0.611162] pci_bus 0000:1b: resource 6 [io  0xff28-0xff2b]
[    0.611164] pci_bus 0000:1b: resource 7 [mem 0x000a0000-0x000bffff]
[    0.611165] pci_bus 0000:1b: resource 8 [mem 0x9b800000-0xfeafffff]
[    0.611197] NET: Registered protocol family 2
[    0.611344] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.612618] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.614788] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.615062] TCP: Hash tables configured (established 524288 bind 65536)
[    0.615063] TCP: reno registered
[    0.615075] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.615118] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.615223] NET: Registered protocol family 1
[    0.615240] pci 0000:00:02.0: Boot video device
[    0.644142] PCI: CLS 0 bytes, default 64
[    0.644144] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.644146] software IO TLB [mem 0x9730c000-0x9b30bfff] (64MB) mapped at [ffff88009730c000-ffff88009b30bfff]
[    0.644604] audit: initializing netlink socket (disabled)
[    0.644615] type=2000 audit(1394129163.640:1): initialized
[    0.662272] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.663989] VFS: Disk quotas dquot_6.5.2
[    0.664043] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.664411] fuse init (API version 7.19)
[    0.664471] msgmni has been set to 11523
[    0.664805] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.664831] io scheduler noop registered
[    0.664834] io scheduler deadline registered (default)
[    0.664854] io scheduler cfq registered
[    0.664959] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.665168] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.665179] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.665213] intel_idle: MWAIT substates: 0x1120
[    0.665214] intel_idle: v0.4 model 0x25
[    0.665215] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.720037] ACPI: AC Adapter [ACAD] (on-line)
[    0.720166] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.720190] ACPI: Lid Switch [LID0]
[    0.720216] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.720219] ACPI: Power Button [PWRB]
[    0.720245] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.720247] ACPI: Power Button [PWRF]
[    0.720300] ACPI: Requesting acpi_cpufreq
[    0.864681] ACPI: Battery Slot [BAT1] (battery present)
[    0.864703] GHES: HEST is not enabled!
[    0.864773] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.884157] Linux agpgart interface v0.103
[    0.884218] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    0.884283] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    0.884951] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    0.885111] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    0.886064] brd: module loaded
[    0.886549] loop: module loaded
[    0.886800] Fixed MDIO Bus: probed
[    0.886825] tun: Universal TUN/TAP device driver, 1.6
[    0.886826] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.886861] PPP generic driver version 2.4.2
[    0.886895] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.886938] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.886941] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.886946] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.886971] ehci_hcd 0000:00:1a.0: debug port 2
[    0.890871] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    0.890888] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xd6b08000
[    0.900028] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.900066] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.900070] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.900074] usb usb1: Product: EHCI Host Controller
[    0.900077] usb usb1: Manufacturer: Linux 3.5.0-39-generic ehci_hcd
[    0.900080] usb usb1: SerialNumber: 0000:00:1a.0
[    0.900193] hub 1-0:1.0: USB hub found
[    0.900197] hub 1-0:1.0: 2 ports detected
[    0.900258] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.900261] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.900266] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.900286] ehci_hcd 0000:00:1d.0: debug port 2
[    0.904168] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    0.904179] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xd6b07000
[    0.916024] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.916051] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.916055] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.916059] usb usb2: Product: EHCI Host Controller
[    0.916062] usb usb2: Manufacturer: Linux 3.5.0-39-generic ehci_hcd
[    0.916065] usb usb2: SerialNumber: 0000:00:1d.0
[    0.916172] hub 2-0:1.0: USB hub found
[    0.916175] hub 2-0:1.0: 2 ports detected
[    0.916215] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.916226] uhci_hcd: USB Universal Host Controller Interface driver
[    0.916259] usbcore: registered new interface driver libusual
[    0.916286] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.979700] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.979704] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.979795] mousedev: PS/2 mouse device common for all mice
[    0.980087] rtc_cmos 00:06: RTC can wake from S4
[    0.980209] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.980237] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.980308] device-mapper: uevent: version 1.0.3
[    0.980360] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.980429] cpuidle: using governor ladder
[    0.982264] cpuidle: using governor menu
[    0.982266] EFI Variables Facility v0.08 2004-May-17
[    0.982461] ashmem: initialized
[    0.982589] TCP: cubic registered
[    0.982659] NET: Registered protocol family 10
[    0.982820] NET: Registered protocol family 17
[    0.982830] Key type dns_resolver registered
[    0.982948] PM: Hibernation image not present or could not be loaded.
[    0.982959] registered taskstats version 1
[    0.986602] Key type trusted registered
[    0.989916] Key type encrypted registered
[    1.041991] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.045405]   Magic number: 6:405:139
[    1.045430] block ram4: hash matches
[    1.045513] acpi device:10: hash matches
[    1.047389] rtc_cmos 00:06: setting system clock to 2014-03-06 18:06:04 UTC (1394129164)
[    1.048504] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.048506] EDD information not available.
[    1.212094] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.344505] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    1.344510] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.344946] hub 1-1:1.0: USB hub found
[    1.345129] hub 1-1:1.0: 6 ports detected
[    1.456083] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.520104] [Firmware Bug]: battery: (dis)charge rate invalid.
[    1.520140] ACPI: Battery Slot [BAT1] (battery present)
[    1.521410] Freeing unused kernel memory: 932k freed
[    1.521609] Write protecting the kernel read-only data: 12288k
[    1.524874] Freeing unused kernel memory: 1464k freed
[    1.527481] Freeing unused kernel memory: 1132k freed
[    1.544738] udevd[101]: starting version 175
[    1.588523] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    1.588531] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.588949] hub 2-1:1.0: USB hub found
[    1.589143] hub 2-1:1.0: 8 ports detected
[    1.629274] sdhci: Secure Digital Host Controller Interface driver
[    1.629279] sdhci: Copyright(c) Pierre Ossman
[    1.629327] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.629495] r8169 0000:02:00.0: irq 41 for MSI/MSI-X
[    1.629594] sdhci-pci 0000:16:00.0: SDHCI controller found [197b:2382] (rev 20)
[    1.629643] mmc0: no vmmc regulator found
[    1.629672] Registered led device: mmc0::
[    1.629699] r8169 0000:02:00.0: eth0: RTL8168e/8111e at 0xffffc90000c7e000, 1c:75:08:7a:af:83, XID 0c200000 IRQ 41
[    1.629703] r8169 0000:02:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.636679] ahci 0000:00:1f.2: version 3.0
[    1.636759] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.636814] ahci: SSS flag set, parallel bus scan disabled
[    1.636843] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x32 impl SATA mode
[    1.636847] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst
[    1.636851] ahci 0000:00:1f.2: setting latency timer to 64
[    1.652820] scsi0 : ahci
[    1.655038] scsi1 : ahci
[    1.655119] scsi2 : ahci
[    1.655241] scsi3 : ahci
[    1.655438] scsi4 : ahci
[    1.655571] scsi5 : ahci
[    1.655778] ata1: DUMMY
[    1.655782] ata2: SATA max UDMA/133 abar m2048@0xd6b08800 port 0xd6b08980 irq 42
[    1.655783] ata3: DUMMY
[    1.655784] ata4: DUMMY
[    1.655786] ata5: SATA max UDMA/133 abar m2048@0xd6b08800 port 0xd6b08b00 irq 42
[    1.655788] ata6: SATA max UDMA/133 abar m2048@0xd6b08800 port 0xd6b08b80 irq 42
[    1.660040] mmc0: SDHCI controller on PCI [0000:16:00.0] using DMA
[    1.660076] sdhci-pci 0000:16:00.2: SDHCI controller found [197b:2381] (rev 20)
[    1.660102] sdhci-pci 0000:16:00.2: Refusing to bind to secondary interface.
[    1.660191] usb 1-1.4: new high-speed USB device number 3 using ehci_hcd
[    1.972100] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.973221] ata2.00: ATA-8: ST9750420AS, 0001SDM5, max UDMA/133
[    1.973226] ata2.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.974485] ata2.00: configured for UDMA/133
[    1.974818] scsi 1:0:0:0: Direct-Access     ATA      ST9750420AS      0001 PQ: 0 ANSI: 5
[    1.975074] sd 1:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    1.975076] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.975083] sd 1:0:0:0: [sda] 4096-byte physical blocks
[    1.975174] sd 1:0:0:0: [sda] Write Protect is off
[    1.975179] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.975203] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.982739] usb 1-1.4: New USB device found, idVendor=04f2, idProduct=b1e4
[    1.982745] usb 1-1.4: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    1.982750] usb 1-1.4: Product: USB 2.0 Camera
[    1.982753] usb 1-1.4: Manufacturer: Chicony Electronics Co., Ltd.
[    1.982756] usb 1-1.4: SerialNumber: SN0001
[    2.038805]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.040195] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.056288] usb 1-1.5: new high-speed USB device number 4 using ehci_hcd
[    2.150641] usb 1-1.5: New USB device found, idVendor=1164, idProduct=0871
[    2.150647] usb 1-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.150650] usb 1-1.5: Product: STK7700D
[    2.150653] usb 1-1.5: Manufacturer: YUANRD
[    2.150655] usb 1-1.5: SerialNumber: 0000000001
[    2.220319] usb 2-1.3: new high-speed USB device number 3 using ehci_hcd
[    2.292103] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.307324] ata5.00: ATAPI: TSSTcorp CDDVDW TS-L633C, TF20, max UDMA/100
[    2.315397] usb 2-1.3: New USB device found, idVendor=0951, idProduct=1607
[    2.315402] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.315406] usb 2-1.3: Product: DataTraveler 2.0
[    2.315408] usb 2-1.3: Manufacturer: Kingston
[    2.315411] usb 2-1.3: SerialNumber: 001CC0EC34ADA9C0A6A106EF
[    2.317183] Initializing USB Mass Storage driver...
[    2.317281] scsi6 : usb-storage 2-1.3:1.0
[    2.317363] usbcore: registered new interface driver usb-storage
[    2.317364] USB Mass Storage support registered.
[    2.323429] ata5.00: configured for UDMA/100
[    2.325050] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633C  TF20 PQ: 0 ANSI: 5
[    2.328299] sr0: scsi3-mmc drive: 20x/20x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.328305] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.328519] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.328596] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    2.648065] ata6: SATA link down (SStatus 0 SControl 300)
[    3.317039] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 8.20 PQ: 0 ANSI: 2
[    3.318870] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    3.319573] sd 6:0:0:0: [sdb] 7825408 512-byte logical blocks: (4.00 GB/3.73 GiB)
[    3.320337] sd 6:0:0:0: [sdb] Write Protect is off
[    3.320344] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    3.321058] sd 6:0:0:0: [sdb] No Caching mode page present
[    3.321062] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.324757] sd 6:0:0:0: [sdb] No Caching mode page present
[    3.324764] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.325658]  sdb: sdb1
[    3.328496] sd 6:0:0:0: [sdb] No Caching mode page present
[    3.328503] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.328508] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    3.527043] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   14.412216] Adding 6080508k swap on /dev/sda6.  Priority:-1 extents:1 across:6080508k
[   14.416478] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.458778] udevd[359]: starting version 175
[   14.651914] lp: driver loaded but no devices found
[   14.724366] ene_ir: chip is 0x3926 - kbver = 0x00, rev = 0xd2
[   14.724370] ene_ir: PLL freq = 1000
[   14.724371] ene_ir: KB3926D or higher detected
[   14.724386] ene_ir: Firmware regs: 64 00
[   14.724387] ene_ir: Hardware features:
[   14.724388] ene_ir: * Uses GPIO 40 for IR demodulated input
[   14.724389] ene_ir: * Uses new style input buffer
[   14.724430] ene_ir: Hardware uses 2 extended buffers:
[   14.724431] ene_ir:   0xfa48 - len : 15
[   14.724433] ene_ir:   0xfb24 - len : 17
[   14.724434] ene_ir: Total buffer len = 40
[   14.752091] Registered IR keymap rc-rc6-mce
[   14.752269] input: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0/input4
[   14.752363] rc0: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0
[   14.752407] ene_ir: driver has been successfully loaded
[   14.756839] IR NEC protocol handler initialized
[   14.758190] IR RC5(x) protocol handler initialized
[   14.770522] IR RC6 protocol handler initialized
[   14.771959] IR JVC protocol handler initialized
[   14.772088] toshiba_bluetooth: Detected Toshiba ACPI Bluetooth device - installing RFKill handler
[   14.788109] IR Sony protocol handler initialized
[   14.805102] IR SANYO protocol handler initialized
[   14.822404] input: MCE IR Keyboard/Mouse (ene_ir) as /devices/virtual/input/input5
[   14.822490] IR MCE Keyboard/mouse protocol handler initialized
[   14.836843] lirc_dev: IR Remote Control driver registered, major 251
[   14.840321] rc rc0: lirc_dev: driver ir-lirc-codec (ene_ir) registered at minor = 0
[   14.840324] IR LIRC bridge handler initialized
[   14.860081] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
[   14.864469] wmi: Mapper loaded
[   14.904956] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19
[   14.905084] input: Toshiba input device as /devices/virtual/input/input6
[   14.908538] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   14.908596] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled until i915 loads
[   14.909638] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   14.913903] ACPI Warning: 0x0000000000000460-0x000000000000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   14.913913] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.913915] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[   14.913918] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   14.913922] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.913925] ACPI Warning: 0x0000000000000500-0x000000000000057f SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251)
[   14.913929] ACPI Warning: 0x0000000000000500-0x000000000000057f SystemIO conflicts with Region \_SB_.PCI0.P0P2.VGA_.GPIO 2 (20120320/utaddress-251)
[   14.913932] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.913934] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   14.924394] mei 0000:00:16.0: setting latency timer to 64
[   14.924480] mei 0000:00:16.0: irq 43 for MSI/MSI-X
[   14.928455] mei 0000:00:16.0: wd: failed to find the client
[   14.961874] type=1400 audit(1394091378.410:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=562 comm="apparmor_parser"
[   14.962278] type=1400 audit(1394091378.410:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=562 comm="apparmor_parser"
[   14.962522] type=1400 audit(1394091378.410:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=562 comm="apparmor_parser"
[   14.964996] type=1400 audit(1394091378.414:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=669 comm="apparmor_parser"
[   14.965044] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   14.965373] type=1400 audit(1394091378.414:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=669 comm="apparmor_parser"
[   14.965593] type=1400 audit(1394091378.414:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=669 comm="apparmor_parser"
[   14.983347] microcode: CPU0 sig=0x20655, pf=0x10, revision=0x2
[   15.021158] Registered led device: toshiba::illumination
[   15.041408] microcode: CPU1 sig=0x20655, pf=0x10, revision=0x2
[   15.043175] microcode: CPU2 sig=0x20655, pf=0x10, revision=0x2
[   15.045064] microcode: CPU3 sig=0x20655, pf=0x10, revision=0x2
[   15.047446] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   15.154700] Linux video capture interface: v2.00
[   15.175092] usb 1-1.6: new full-speed USB device number 5 using ehci_hcd
[   15.187824] [drm] Initialized drm 1.1.0 20060810
[   15.252403] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   15.269620] usb 1-1.6: New USB device found, idVendor=0930, idProduct=0214
[   15.269629] usb 1-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   15.269635] usb 1-1.6: Product: Askey Bluetooth Module
[   15.269641] usb 1-1.6: Manufacturer: Broadcom Corp
[   15.269646] usb 1-1.6: SerialNumber: 4CEDDE6FD15C
[   15.286799] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b1e4)
[   15.299861] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input7
[   15.299987] usbcore: registered new interface driver uvcvideo
[   15.299990] USB Video Class driver (1.1.1)
[   15.339203] init: failsafe main process (806) killed by TERM signal
[   15.370726] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   15.370827] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   15.370911] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   15.371731] i915 0000:00:02.0: setting latency timer to 64
[   15.376333] dvb-usb: found a 'YUAN High-Tech MC770' in warm state.
[   15.376387] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.376527] DVB: registering new adapter (YUAN High-Tech MC770)
[   15.400897] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[   15.400907] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.400908] [drm] Driver supports precise vblank timestamp query.
[   15.401223] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   15.401225] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[   15.458981] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   15.462860] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.P0P2.VGA_ handle
[   15.462903] nouveau 0000:01:00.0: power state changed by ACPI to D0
[   15.462908] nouveau 0000:01:00.0: power state changed by ACPI to D0
[   15.462912] nouveau 0000:01:00.0: enabling device (0000 -> 0003)
[   15.470155] type=1400 audit(1394091378.918:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=898 comm="apparmor_parser"
[   15.470549] type=1400 audit(1394091378.918:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=898 comm="apparmor_parser"
[   15.470727] type=1400 audit(1394091378.918:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=898 comm="apparmor_parser"
[   15.470992] type=1400 audit(1394091378.918:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=895 comm="apparmor_parser"
[   15.544253] ppdev: user-space parallel port driver
[   15.640600] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   15.783734] Bluetooth: Core ver 2.16
[   15.783765] NET: Registered protocol family 31
[   15.783766] Bluetooth: HCI device and connection manager initialized
[   15.783768] Bluetooth: HCI socket layer initialized
[   15.783770] Bluetooth: L2CAP socket layer initialized
[   15.783775] Bluetooth: SCO socket layer initialized
[   15.809112] r8169 0000:02:00.0: eth0: link down
[   15.809881] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.810181] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.814007] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.814010] Bluetooth: BNEP filters: protocol multicast
[   15.818648] usbcore: registered new interface driver btusb
[   15.823011] xc2028 7-0061: creating new instance
[   15.823014] xc2028 7-0061: type set to XCeive xc2028/xc3028 tuner
[   15.835109] Bluetooth: RFCOMM TTY layer initialized
[   15.835116] Bluetooth: RFCOMM socket layer initialized
[   15.835117] Bluetooth: RFCOMM ver 1.11
[   15.852034] Registered IR keymap rc-dib0700-rc5
[   15.852160] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/rc/rc1/input11
[   15.852232] rc1: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/rc/rc1
[   15.852584] dvb-usb: schedule remote query interval to 50 msecs.
[   15.852587] dvb-usb: YUAN High-Tech MC770 successfully initialized and connected.
[   15.853008] dib0700: rc submit urb failed
[   15.853008]
[   15.853055] usbcore: registered new interface driver dvb_usb_dib0700
[   15.885745] fbcon: inteldrmfb (fb0) is primary device
[   15.885858] Console: switching to colour frame buffer device 170x48
[   15.885896] fb0: inteldrmfb frame buffer device
[   15.885898] drm: registered panic notifier
[   15.996142] acpi device:02: registered as cooling_device4
[   15.996224] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   15.996276] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input12
[   16.112198] acpi device:0d: registered as cooling_device5
[   16.112359] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   16.112406] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:02/input/input13
[   16.112561] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.113600] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x0a5480a2)
[   16.118557] vga_switcheroo: enabled
[   16.118570] [drm] nouveau 0000:01:00.0: Checking PRAMIN for VBIOS
[   16.118576] [drm] nouveau 0000:01:00.0: ... BIOS signature not found
[   16.118577] [drm] nouveau 0000:01:00.0: Checking PROM for VBIOS
[   16.118606] [drm] nouveau 0000:01:00.0: ... BIOS signature not found
[   16.118606] [drm] nouveau 0000:01:00.0: Checking ACPI for VBIOS
[   16.341363] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   16.341367] [drm] nouveau 0000:01:00.0: Using VBIOS from ACPI
[   16.341369] [drm] nouveau 0000:01:00.0: BIT BIOS found
[   16.341372] [drm] nouveau 0000:01:00.0: Bios version 70.16.60.00
[   16.341375] [drm] nouveau 0000:01:00.0: TMDS table version 2.0
[   16.341696] [drm] nouveau 0000:01:00.0: MXM: no VBIOS data, nothing to do
[   16.341699] [drm] nouveau 0000:01:00.0: DCB version 4.0
[   16.341702] [drm] nouveau 0000:01:00.0: DCB outp 00: 01000323 00010034
[   16.341704] [drm] nouveau 0000:01:00.0: DCB outp 01: 02011300 00000000
[   16.341706] [drm] nouveau 0000:01:00.0: DCB outp 02: 08022382 00020010
[   16.341707] [drm] nouveau 0000:01:00.0: DCB conn 00: 00000040
[   16.341710] [drm] nouveau 0000:01:00.0: DCB conn 01: 00000100
[   16.341711] [drm] nouveau 0000:01:00.0: DCB conn 02: 00002261
[   16.341721] [drm] nouveau 0000:01:00.0: Adaptor not initialised, running VBIOS init tables.
[   16.341723] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0x7056
[   16.381753] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0x74EE
[   16.409320] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0x83EE
[   16.409346] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0x8410
[   16.410392] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0x8572
[   16.410394] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0x85D7
[   16.433965] [TTM] Zone  kernel: Available graphics memory: 2951774 kiB
[   16.433968] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[   16.433969] [TTM] Initializing pool allocator
[   16.433975] [TTM] Initializing DMA pool allocator
[   16.433991] [drm] nouveau 0000:01:00.0: Detected 1024MiB VRAM (DDR3)
[   16.435387] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[   16.489938] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   16.489940] [drm] No driver support for vblank timestamp query.
[   16.489942] [drm] nouveau 0000:01:00.0: ACPI backlight interface available, not registering our own
[   16.494861] [drm] nouveau 0000:01:00.0: 3 available performance level(s)
[   16.494865] [drm] nouveau 0000:01:00.0: 0: core 135MHz shader 270MHz memory 135MHz voltage 800mV
[   16.494867] [drm] nouveau 0000:01:00.0: 1: core 405MHz shader 810MHz memory 324MHz voltage 850mV
[   16.494868] [drm] nouveau 0000:01:00.0: 3: core 500MHz shader 1210MHz memory 790MHz voltage 950mV
[   16.494870] [drm] nouveau 0000:01:00.0: c: core 405MHz shader 810MHz memory 324MHz voltage 850mV
[   16.527650] [drm] nouveau 0000:01:00.0: MM: using COPY for buffer copies
[   16.875850] No connectors reported connected with modes
[   16.875857] [drm] Cannot find any crtc or sizes - going 1024x768
[   16.889165] [drm] nouveau 0000:01:00.0: allocated 1024x768 fb: 0x2c0000, bo ffff8801bd09c400
[   16.889249] fb1: nouveaufb frame buffer device
[   16.889255] [drm] Initialized nouveau 1.0.0 20120316 for 0000:01:00.0 on minor 1
[   17.232803] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xa40000/0xa0400
[   17.232811] psmouse serio1: synaptics: Toshiba Satellite A660 detected, limiting rate to 40pps.
[   17.396145] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input14
[   20.108064] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
[  146.654282] show_signal_msg: 57 callbacks suppressed
[  146.654290] update-notifier[2357]: segfault at 88 ip 00007fe9decb1d21 sp 00007fff90eb92c0 error 4 in libgobject-2.0.so.0.3400.1[7fe9dec9d000+4d000]
 
```

**sudo lshw -C network **
  ```

*-network              
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: 1c:75:08:7a:af:83
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:6000(size=256) memory:d1804000-d1804fff memory:d1800000-d1803fff
  *-network UNCLAIMED
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d5a00000-d5a03fff
 
```

**sudo iwlist wlan0 scan**
```

wlan0     Interface doesn't support scanning.
 
```

**lsb_release -d**
```

Description:   Ubuntu 12.10
 
```

 **uname -mr**
```

3.5.0-39-generic x86_64

```

---

### Post by varunendra on 2014-03-06
Please edit your post above to wrap the outputs within 'Code' tags. Please follow the "Using Code Tags" link in my signature below to see how.

As for the problem, I couldn't find either "wl" or "brcmsmac" in your lsmod output above. These are the (mutually conflicting) correct drivers for your card. Please try -
```
sudo modprobe -v brcmsmac
```
Does wifi become active? If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by jaykob_hxc2 on 2014-03-06
SUCCESS!! It seems to have solved the problem by doing the command 'sudo modprobe -v brcmsmac'. As soon as I excuted that code the connections became avaible to me. May I ask what that peice of code does and how it fixed the problem? I'm a novice programmer so I'd be keen to learn :)

rfkill list
```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

sudo modprobe -v brcmsmac

```
 
insmod /lib/modules/3.5.0-39-generic/kernel/lib/cordic.ko 
insmod /lib/modules/3.5.0-39-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.5.0-39-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko 
insmod /lib/modules/3.5.0-39-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.5.0-39-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-39-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko 

```

---

### Post by varunendra on 2014-03-06
> **jaykob_hxc2 said:**
> May I ask what that peice of code does and how it fixed the problem? I'm a novice programmer so I'd be keen to learn :)
And I'd love to explain :)

The 'modprobe' command loads a specified module (driver) into the running kernel, and the "-v" option just makes it verbose so you can see what would have otherwise happened in the background. Loading a module requires root privilege, hence the 'sudo' before it.

So our command "**sudo modprobe -v *brcmsmac***" loaded the module "brcmsmac" which is the driver required to control the wireless card that you have.

This module is already present in the kernel and should be loaded automatically at startup. There are quite a few reasons when this may not happen, and the most common one is a failed installation (or improper removal after installation) of proprietary driver "wl". When the "wl" driver installs, it **blacklists** certain drivers to avoid conflict, and "brcmsmac" is one of those drivers. You may have installed it following some other suggestion somewhere else, or it might have been installed automatically during OS installation, if you opted the "Install Updates" option while installing Ubuntu.

Whatever be the cause, the fix is usually as easy as removing the driver from blacklist.

Accordingly, please check -
```
grep -R '^blacklist brcmsmac' /etc/modprobe.d
```
This command will recursively scan the /etc/modprobe.d directory, and will return all those lines that contain the search term "blacklist brcmsmac", with the names of files that contain those lines (the '^' is an expression to indicate 'beginning' of a line).

Post back the above output and we'll tell you whether you can remove just the blacklist line or the whole file so that you don't have to manually run the 'modprobe.." command everytime.

---

### Post by jaykob_hxc2 on 2014-03-06
Thank-you so much for that information. It's really interesting that it overrides it like that. After getting my wifi connection back I updated my Ubuntu and as soon as I restarted the computer I had no wifi again. Will this keep recurring everytime I update? 

I ran the code and got something like this:

grep -R '^blacklist brcmsmac' /etc/modprobe.d
```

/etc/modprobe.d/blacklist-bcm43.conf:blacklist brcmsmac

```

---

### Post by varunendra on 2014-03-06
> **jaykob_hxc2 said:**
> ```

**/etc/modprobe.d/blacklist-bcm43.conf**:blacklist brcmsmac

```

The above is the file that is preventing the driver from loading automatically. And as suspected, this is clearly the one that is created during the installation of the "wl" driver. Easy to fix ! :)

Please do -
```
sudo apt-get purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
One of the two commands will return error, just ignore it.

The first one will purge the offending driver package "bcmwl-kernel-source" if it is still installed, so that an update doesn't cause troubles. If the package is already removed, this command may return error, which is fine, no problem.
The second one will delete the file that contains the blacklist entries that are preventing the "brcmsmac" driver from loading. If the first command completes without errors, this file will also be removed during the purge operation. In that case, this second one will return error (file not found). Again, perfectly fine.

Reboot or manually load the "brcmsmac" driver again. It should load automatically since next booting. Let me know if it doesn't, we also know how to 'force' a driver if required. :)

---

### Post by jaykob_hxc2 on 2014-03-06
The first command executed however the second command returned an error just as you said. From now on Wifi is loading automatically when I start up Ubuntu which is amazing.

Thank-you so much Varun for all your help and taking the time out to help me. It's greatly appreciated. I can hope that if someone has the same problem they can read this post and go through the same procedure to get the same result :D

Thanks again!

---

### Post by varunendra on 2014-03-06
You're welcome!

Hope you'll enjoy Ubuntu as well as the forums here. :)

Cheers!!

---

