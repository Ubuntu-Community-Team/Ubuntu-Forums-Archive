---
title: "via_velocity gigabit NIC - Can it work under 2.6.20-15 (7.04)? (VT6120/VT6121/VT6122)"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by RudeIota on 2007-04-23
Much like many other posts start out, I am relatively novice with Linux..

My questions are:
1.) Has anyone gotten this card or this chipset to work with 2.6.20-15 or simliar kernel?
2.) How did you do it?

The problem here is my ZyXEL GN670-T (Uses a ¨ZX1701¨ controller that is supposedly based on the Via Velocity chipset). It does not work out of the box under any recent versions of Linux I can find. 
[B]
Steps taken:[/B]

I downloaded the source and attempted to compile it. The compiler had numerous fatal errors, including one I fixed by replacing instances of linux/config.h in the source with linux/autoconfg.h, but there are still still plenty of issues left. (more details below)

I manually configured the controller using ethtool with speed 1000; autoneg off and assigned a static IP with appropriate subnet, gateway etc...

Tried to get it to work in a somewhat FC6 box with no luck.

I tried to insmod the compiled ,ko file included with the driver source, but inmod tells me it&#347; an invalid format. Probably because it is too old? 
**Information:**

```
**uname -r **
2.6.20-15-server
```
```
**lspci -v**
 00:09.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
        Subsystem: ZyXEL Communication Corporation Unknown device 3302
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
        I/O ports at ec00 [size=256]
        Memory at dfffff00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

``````
**lsmod**
via_velocity           34308  0 
crc_ccitt               3072  2 irda,via_velocity
```
```
[code] **ethtool eth1**
Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  Not reported
        Advertised auto-negotiation: No
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: puag
        Wake-on: g
        Current message level: 0x00000002 (2)
        Link detected: yes

```

Additionally, attempting to build the source (which is supposed to be suitable for the 2.6 kernel) gives me this junk... even after I have done my best to patch it up by eliminating different problems:
```
make
make -C /lib/modules/2.6.20-15-server/build SUBDIRS=/tmp/1.23 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-server'
  CC [M]  /tmp/1.23/velocity_main.o
/tmp/1.23/velocity_main.c:62: error: expected &#8216;)&#8217; before string constant
/tmp/1.23/velocity_main.c:67: error: expected &#8216;)&#8217; before string constant
/tmp/1.23/velocity_main.c:76: error: expected &#8216;)&#8217; before string constant
/tmp/1.23/velocity_main.c:87: error: expected &#8216;)&#8217; before string constant
/tmp/1.23/velocity_main.c:103: error: expected &#8216;)&#8217; before string constant
/tmp/1.23/velocity_main.c:110: error: expected &#8216;)&#8217; before string constant
/tmp/1.23/velocity_main.c:119: error: expected &#8216;)&#8217; before string constant
/tmp/1.23/velocity_main.c:128: error: expected &#8216;)&#8217; before string constant
/tmp/1.23/velocity_main.c:141: error: expected &#8216;)&#8217; before string constant
/tmp/1.23/velocity_main.c:157: error: expected &#8216;)&#8217; before string constant
/tmp/1.23/velocity_main.c:164: error: expected &#8216;)&#8217; before string constant
/tmp/1.23/velocity_main.c:176: error: expected &#8216;)&#8217; before string constant
/tmp/1.23/velocity_main.c:181: error: expected &#8216;)&#8217; before string constant
/tmp/1.23/velocity_main.c:187: error: expected &#8216;)&#8217; before string constant
/tmp/1.23/velocity_main.c: In function &#8216;velocity_open&#8217;:
/tmp/1.23/velocity_main.c:1224: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
/tmp/1.23/velocity_main.c: In function &#8216;velocity_xmit&#8217;:
/tmp/1.23/velocity_main.c:1355: error: too many arguments to function &#8216;skb_linearize&#8217;
/tmp/1.23/velocity_main.c:1450: error: &#8216;CHECKSUM_HW&#8217; undeclared (first use in this function)
/tmp/1.23/velocity_main.c:1450: error: (Each undeclared identifier is reported only once
/tmp/1.23/velocity_main.c:1450: error: for each function it appears in.)
/tmp/1.23/velocity_main.c: In function &#8216;velocity_notify_reboot&#8217;:
/tmp/1.23/velocity_main.c:1960: error: incompatible type for argument 2 of &#8216;velocity_suspend&#8217;
/tmp/1.23/velocity_main.c: In function &#8216;velocity_suspend&#8217;:
/tmp/1.23/velocity_main.c:2004: error: incompatible type for argument 2 of &#8216;pci_set_power_state&#8217;
make[2]: *** [/tmp/1.23/velocity_main.o] Error 1
make[1]: *** [_module_/tmp/1.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-server'
make: *** [default] Error 2

```

More, possibly less pertinent information:
```
**lsmod**
Module                  Size  Used by
nls_cp437               6784  1 
isofs                  36156  1 
udf                    84996  0 
ipv6                  273344  10 
via                    44160  2 
drm                    81044  3 via
dev_acpi               12164  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
dock                   10268  0 
ac                      6020  0 
button                  8720  0 
sbs                    15524  0 
i2c_ec                  5888  1 sbs
asus_acpi              17308  0 
backlight               6784  1 asus_acpi
battery                10756  0 
video                  16260  0 
container               5248  0 
lp                     12324  0 
snd_via82xx            29336  1 
snd_ac97_codec         97952  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44416  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11016  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9472  1 snd_via82xx
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
parport_pc             36644  1 
snd_seq                52464  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                  4224  0 
parport                36808  2 lp,parport_pc
via_ircc               27796  0 
analog                 12832  0 
irda                  201148  1 via_ircc
serio_raw               7940  0 
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
gameport               16520  2 snd_via82xx,analog
psmouse                38920  0 
i2c_viapro             10132  0 
i2c_core               22784  2 i2c_ec,i2c_viapro
via_agp                11264  1 
snd                    53892  13 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
shpchp                 34452  0 
pci_hotplug            32448  1 shpchp
agpgart                35528  2 drm,via_agp
af_packet              23688  2 
evdev                  11008  4 
tsdev                   8768  0 
ext3                  132872  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32544  1 
cdrom                  37536  1 ide_cd
ide_disk               17024  3 
ata_generic             9092  0 
libata                125848  1 ata_generic
scsi_mod              142220  1 libata
usbhid                 26720  0 
hid                    27392  1 usbhid
via82cxxx              10244  0 [permanent]
floppy                 59396  0 
generic                 5124  0 [permanent]
via_rhine              25864  0 
mii                     6656  1 via_rhine
ehci_hcd               34572  0 
uhci_hcd               25488  0 
usbcore               134408  4 usbhid,ehci_hcd,uhci_hcd
via_velocity           34308  0 
crc_ccitt               3072  2 irda,via_velocity
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```
```
**lspci -v**
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
        Subsystem: ASRock Incorporation Unknown device 3205
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at e0000000 (32-bit, prefetchable) [size=32M]
        Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: dde00000-dfefffff
        Prefetchable memory behind bridge: d5d00000-ddcfffff
        Capabilities: <access denied>

00:09.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
        Subsystem: ZyXEL Communication Corporation Unknown device 3302
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
        I/O ports at ec00 [size=256]
        Memory at dfffff00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation K7VT6
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at e000 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation K7VT6
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at e400 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation K7VT6
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at e800 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])
        Subsystem: ASRock Incorporation K7VT6 motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at dffffe00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
        Subsystem: ASRock Incorporation K7VT2 motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: ASRock Incorporation K7VT2/K7VT6 motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 255
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at fc00 [size=16]
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
        Subsystem: ASRock Incorporation Unknown device 1617
        Flags: medium devsel, IRQ 19
        I/O ports at dc00 [size=256]
        Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
        Subsystem: ASRock Incorporation K7VT6 motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at d800 [size=256]
        Memory at dffffd00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01) (prog-if 00 [VGA])
        Subsystem: ASRock Incorporation Unknown device 7205
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 20
        Memory at d8000000 (32-bit, prefetchable) [size=64M]
        Memory at de000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at dfef0000 [disabled] [size=64K]
        Capabilities: <access denied>

rick@server:~$ sudo lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
        Subsystem: ASRock Incorporation Unknown device 3205
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at e0000000 (32-bit, prefetchable) [size=32M]
        Capabilities: [80] AGP version 3.5
        Capabilities: [c0] Power Management version 2

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: dde00000-dfefffff
        Prefetchable memory behind bridge: d5d00000-ddcfffff
        Capabilities: [80] Power Management version 2

00:09.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
        Subsystem: ZyXEL Communication Corporation Unknown device 3302
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
        I/O ports at ec00 [size=256]
        Memory at dfffff00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation K7VT6
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at e000 [size=32]
        Capabilities: [80] Power Management version 2

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation K7VT6
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at e400 [size=32]
        Capabilities: [80] Power Management version 2

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation K7VT6
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at e800 [size=32]
        Capabilities: [80] Power Management version 2

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])
        Subsystem: ASRock Incorporation K7VT6 motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at dffffe00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
        Subsystem: ASRock Incorporation K7VT2 motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: [c0] Power Management version 2

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: ASRock Incorporation K7VT2/K7VT6 motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 255
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at fc00 [size=16]
        Capabilities: [c0] Power Management version 2

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
        Subsystem: ASRock Incorporation Unknown device 1617
        Flags: medium devsel, IRQ 19
        I/O ports at dc00 [size=256]
        Capabilities: [c0] Power Management version 2

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
        Subsystem: ASRock Incorporation K7VT6 motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at d800 [size=256]
        Memory at dffffd00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [40] Power Management version 2

01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01) (prog-if 00 [VGA])
        Subsystem: ASRock Incorporation Unknown device 7205
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 20
        Memory at d8000000 (32-bit, prefetchable) [size=64M]
        Memory at de000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at dfef0000 [disabled] [size=64K]
        Capabilities: [60] Power Management version 2
        Capabilities: [70] AGP version 2.0

```

Thank you for any help you can provide. I really want to get this up and running as soon as I can... and I really want to avoid buying another NIC... for both the linux experience and saving a little money.

---

### Post by RudeIota on 2007-04-24
I just tried using 6.06  (2.6.15-26-server) and I am having the same NIC issues. When I try to compile the source code, things go a lot smoother though. Here's what I get...
```
make
make -C /lib/modules/2.6.15-26-server/build SUBDIRS=/tmp/1.23 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-server'
  CC [M]  /tmp/1.23/velocity_main.o
/tmp/1.23/velocity_main.c: In function ‘velocity_notify_reboot’:
/tmp/1.23/velocity_main.c:1960: error: incompatible type for argument 2 of ‘velocity_suspend’
/tmp/1.23/velocity_main.c: In function ‘velocity_suspend’:
/tmp/1.23/velocity_main.c:2004: error: incompatible type for argument 2 of ‘pci_set_power_state’
make[2]: *** [/tmp/1.23/velocity_main.o] Error 1
make[1]: *** [_module_/tmp/1.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-server'
make: *** [default] Error 2

```

---

### Post by RudeIota on 2007-04-27
It would appear that I cannot get this to compile under 6.10 either....

```
make -C /lib/modules/2.6.17-11-server/build SUBDIRS=/tmp/1.23 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-server'
  CC [M]  /tmp/1.23/velocity_main.o
/tmp/1.23/velocity_main.c:62: error: expected ‘)’ before string constant
/tmp/1.23/velocity_main.c:67: error: expected ‘)’ before string constant
/tmp/1.23/velocity_main.c:76: error: expected ‘)’ before string constant
/tmp/1.23/velocity_main.c:87: error: expected ‘)’ before string constant
/tmp/1.23/velocity_main.c:103: error: expected ‘)’ before string constant
/tmp/1.23/velocity_main.c:110: error: expected ‘)’ before string constant
/tmp/1.23/velocity_main.c:119: error: expected ‘)’ before string constant
/tmp/1.23/velocity_main.c:128: error: expected ‘)’ before string constant
/tmp/1.23/velocity_main.c:141: error: expected ‘)’ before string constant
/tmp/1.23/velocity_main.c:157: error: expected ‘)’ before string constant
/tmp/1.23/velocity_main.c:164: error: expected ‘)’ before string constant
/tmp/1.23/velocity_main.c:176: error: expected ‘)’ before string constant
/tmp/1.23/velocity_main.c:181: error: expected ‘)’ before string constant
/tmp/1.23/velocity_main.c:187: error: expected ‘)’ before string constant
/tmp/1.23/velocity_main.c: In function ‘velocity_notify_reboot’:
/tmp/1.23/velocity_main.c:1960: error: incompatible type for argument 2 of ‘velocity_suspend’
/tmp/1.23/velocity_main.c: In function ‘velocity_suspend’:
/tmp/1.23/velocity_main.c:2004: error: incompatible type for argument 2 of ‘pci_set_power_state’
make[2]: *** [/tmp/1.23/velocity_main.o] Error 1
make[1]: *** [_module_/tmp/1.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-server'
make: *** [default] Error 2
 
```

---

