---
title: "USB Telbox using kB2Kskype switches On/Off"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by Sky Pixie on 2009-05-23
I am attempting to turn a Shuttle KPC45 into a dedicated Skype box to serve a digital telephone.

I ordered the B2K adapter from Amazon.com:  [http://www.amazon.com/Eforcity-Adapter-Interface-connects-network/dp/B000JCU88S/ref=sr_1_1/181-0565061-9681939?ie=UTF8&s=electronics&qid=1243115823&sr=8-1](http://www.amazon.com/Eforcity-Adapter-Interface-connects-network/dp/B000JCU88S/ref=sr_1_1/181-0565061-9681939?ie=UTF8&s=electronics&qid=1243115823&sr=8-1)

I installed Ubuntu Server 8.04 64-bit Mini because of the minimal install, 5 year support offered, and familiar KDE3 graphical interface.  The kernel version is 2.6.24-16-server.

I updated the package list, installed updates to the base system, then installed xorg, kde-core, kdm, build-essential, guarddog, and kde-systemsettings.

I preceded to install Skype 2.0.0.72 i386 for Ubuntu 7.04-8.04 using dpkg and the force-architecture option.  Dependencies, if any, were installed.

I downloaded usbb2k-api-mod_2.8-1_amd64.kubuntu8042.deb and kb2kskype_0.3.8-1_amd64_kubuntu8042.deb from sourceforge.  As per the kB2Kskype instructions, I installed the following:
libusb
alsa
kdelibs-4

I suspect the 2.6.24-16-server kernel is compiled with snd-usb-audio because lsmod lists such a module.  See below.

I installed usbb2k-api-mod2.8 and kb2kskype-0.3.8 using dpkg.

I started the usbb2k_api daemon.

I started Skype from a command line, logged in, and configured privacy and sound settings.

I started kb2kskype from the command line.  I received the following output:
```

amixer: Unable to find simple control 'Mic',1

amixer: Unable to find simple control 'PCM',1

amixer: Unable to find simple control 'Mic',1

amixer: Unable to find simple control 'PCM',1

```

lsmod output:
```

Module                  Size  Used by
nls_iso8859_1          13824  1
nls_cp437              15488  1
vfat                   23424  1
fat                    67632  1 vfat
usb_storage            89664  1
libusual               30688  1 usb_storage
i915                   45312  1
drm                   113320  2 i915
ipv6                  325768  21
ac                     15496  0
coretemp               17024  0
it87                   34064  0
hwmon_vid              12288  1 it87
lp                     22084  0
loop                   28676  0
af_packet              34440  2
snd_usb_audio         107552  0
snd_usb_lib            28288  1 snd_usb_audio
iTCO_wdt               22480  0
iTCO_vendor_support    12932  1 iTCO_wdt
snd_rawmidi            37024  1 snd_usb_lib
snd_seq_device         17812  1 snd_rawmidi
evdev                  22144  3
yealink                22272  0
serio_raw              16260  0
snd_hda_intel         447576  0
parport_pc             48296  1
parport                51340  2 lp,parport_pc
pcspkr                 12160  0
psmouse                53404  0
sky2                   61060  0
snd_pcm                99336  2 snd_usb_audio,snd_hda_intel
snd_timer              35080  1 snd_pcm
snd_page_alloc         20368  2 snd_hda_intel,snd_pcm
snd_hwdep              19720  2 snd_usb_audio,snd_hda_intel
snd                    78024  8 snd_usb_audio,snd_usb_lib,snd_rawmidi,snd_seq_device,snd_hda_intel,snd_pcm,snd_timer,snd_hwdep
button                 18080  0
intel_agp              37792  1
shpchp                 45340  0
pci_hotplug            41776  1 shpchp
soundcore              17568  1 snd
xt_tcpudp              12160  28
nf_conntrack_ipv4      29072  30
xt_state               11264  30
nf_conntrack           86384  2 nf_conntrack_ipv4,xt_state
ipt_REJECT             13696  4
xt_limit               11776  6
ipt_LOG                15360  6
iptable_filter         11776  1
ip_tables              31720  1 iptable_filter
x_tables               30728  6 xt_tcpudp,xt_state,ipt_REJECT,xt_limit,ipt_LOG,ip_tables
ext3                  156176  4
jbd                    64168  1 ext3
mbcache                18560  1 ext3
sha256_generic         17536  0
aes_x86_64             34088  2
cbc                    13568  1
blkcipher              16644  1 cbc
usbhid                 42336  0
hid                    52160  1 usbhid
sg                     48920  0
sd_mod                 40448  5
pata_acpi              17024  0
ata_piix               31364  2
ata_generic            17156  0
libata                183472  3 pata_acpi,ata_piix,ata_generic
scsi_mod              185528  4 usb_storage,sg,sd_mod,libata
ehci_hcd               49164  0
uhci_hcd               37024  0
usbcore               176816  10 usb_storage,libusual,snd_usb_audio,snd_usb_lib,yealink,usbhid,ehci_hcd,uhci_hcd
dm_crypt               23944  1
dm_mirror              33408  0
dm_snapshot            27848  0
dm_mod                 78200  14 dm_crypt,dm_mirror,dm_snapshot
thermal                26912  0
processor              49608  1 thermal
fan                    13960  0
fbcon                  53504  0
tileblit               11264  1 fbcon
font                   17280  1 fbcon
bitblit                14592  1 fbcon
softcursor             10880  1 bitblit
fuse                   63280  1

```

cat /proc/modules output:
```

nls_iso8859_1 13824 1 - Live 0xffffffff88479000
nls_cp437 15488 1 - Live 0xffffffff88474000
vfat 23424 1 - Live 0xffffffff8846d000
fat 67632 1 vfat, Live 0xffffffff8845b000
usb_storage 89664 1 - Live 0xffffffff88444000
libusual 30688 1 usb_storage, Live 0xffffffff8843b000
i915 45312 1 - Live 0xffffffff8842e000
drm 113320 2 i915, Live 0xffffffff88411000
ipv6 325768 21 - Live 0xffffffff883c0000
ac 15496 0 - Live 0xffffffff883bb000
coretemp 17024 0 - Live 0xffffffff883b5000
it87 34064 0 - Live 0xffffffff883ab000
hwmon_vid 12288 1 it87, Live 0xffffffff883a7000
lp 22084 0 - Live 0xffffffff883a0000
loop 28676 0 - Live 0xffffffff88397000
af_packet 34440 2 - Live 0xffffffff8838d000
snd_usb_audio 107552 0 - Live 0xffffffff88371000
snd_usb_lib 28288 1 snd_usb_audio, Live 0xffffffff88369000
iTCO_wdt 22480 0 - Live 0xffffffff88362000
iTCO_vendor_support 12932 1 iTCO_wdt, Live 0xffffffff8835d000
snd_rawmidi 37024 1 snd_usb_lib, Live 0xffffffff88352000
snd_seq_device 17812 1 snd_rawmidi, Live 0xffffffff88338000
evdev 22144 3 - Live 0xffffffff8834b000
yealink 22272 0 - Live 0xffffffff88344000
serio_raw 16260 0 - Live 0xffffffff8833f000
snd_hda_intel 447576 0 - Live 0xffffffff882c7000
parport_pc 48296 1 - Live 0xffffffff882b8000
parport 51340 2 lp,parport_pc, Live 0xffffffff882aa000
pcspkr 12160 0 - Live 0xffffffff882a6000
psmouse 53404 0 - Live 0xffffffff88297000
sky2 61060 0 - Live 0xffffffff88287000
snd_pcm 99336 2 snd_usb_audio,snd_hda_intel, Live 0xffffffff8826d000
snd_timer 35080 1 snd_pcm, Live 0xffffffff88263000
snd_page_alloc 20368 2 snd_hda_intel,snd_pcm, Live 0xffffffff8825d000
snd_hwdep 19720 2 snd_usb_audio,snd_hda_intel, Live 0xffffffff88257000
snd 78024 8 snd_usb_audio,snd_usb_lib,snd_rawmidi,snd_seq_device,snd_hda_intel,snd_pcm,snd_timer,snd_hwdep, Live 0xffffffff88242000
button 18080 0 - Live 0xffffffff8823c000
intel_agp 37792 1 - Live 0xffffffff88231000
shpchp 45340 0 - Live 0xffffffff88224000
pci_hotplug 41776 1 shpchp, Live 0xffffffff88218000
soundcore 17568 1 snd, Live 0xffffffff88212000
xt_tcpudp 12160 28 - Live 0xffffffff8820e000
nf_conntrack_ipv4 29072 30 - Live 0xffffffff88205000
xt_state 11264 30 - Live 0xffffffff88201000
nf_conntrack 86384 2 nf_conntrack_ipv4,xt_state, Live 0xffffffff881ea000
ipt_REJECT 13696 4 - Live 0xffffffff881e5000
xt_limit 11776 6 - Live 0xffffffff881e1000
ipt_LOG 15360 6 - Live 0xffffffff881dc000
iptable_filter 11776 1 - Live 0xffffffff881d8000
ip_tables 31720 1 iptable_filter, Live 0xffffffff881cf000
x_tables 30728 6 xt_tcpudp,xt_state,ipt_REJECT,xt_limit,ipt_LOG,ip_tables, Live 0xffffffff881c6000
ext3 156176 4 - Live 0xffffffff8819e000
jbd 64168 1 ext3, Live 0xffffffff8818d000
mbcache 18560 1 ext3, Live 0xffffffff88187000
sha256_generic 17536 0 - Live 0xffffffff88181000
aes_x86_64 34088 2 - Live 0xffffffff88177000
cbc 13568 1 - Live 0xffffffff88172000
blkcipher 16644 1 cbc, Live 0xffffffff8816c000
usbhid 42336 0 - Live 0xffffffff88160000
hid 52160 1 usbhid, Live 0xffffffff88152000
sg 48920 0 - Live 0xffffffff88145000
sd_mod 40448 5 - Live 0xffffffff8813a000
pata_acpi 17024 0 - Live 0xffffffff88134000
ata_piix 31364 2 - Live 0xffffffff8812b000
ata_generic 17156 0 - Live 0xffffffff88125000
libata 183472 3 pata_acpi,ata_piix,ata_generic, Live 0xffffffff880f7000
scsi_mod 185528 4 usb_storage,sg,sd_mod,libata, Live 0xffffffff880c8000
ehci_hcd 49164 0 - Live 0xffffffff880b8000
uhci_hcd 37024 0 - Live 0xffffffff880ab000
usbcore 176816 10 usb_storage,libusual,snd_usb_audio,snd_usb_lib,yealink,usbhid,ehci_hcd,uhci_hcd, Live 0xffffffff8807e000
dm_crypt 23944 1 - Live 0xffffffff88077000
dm_mirror 33408 0 - Live 0xffffffff8806d000
dm_snapshot 27848 0 - Live 0xffffffff88065000
dm_mod 78200 14 dm_crypt,dm_mirror,dm_snapshot, Live 0xffffffff88050000
thermal 26912 0 - Live 0xffffffff88048000
processor 49608 1 thermal, Live 0xffffffff8803a000
fan 13960 0 - Live 0xffffffff88035000
fbcon 53504 0 - Live 0xffffffff88026000
tileblit 11264 1 fbcon, Live 0xffffffff88022000
font 17280 1 fbcon, Live 0xffffffff8801c000
bitblit 14592 1 fbcon, Live 0xffffffff88017000
softcursor 10880 1 bitblit, Live 0xffffffff88013000
fuse 63280 1 - Live 0xffffffff88002000

```

lspci -v output run as normal user:
```

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 3140
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 3140
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fdf00000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ff00 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at fdf80000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 3140
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fdb00000-fdbfffff
        Prefetchable memory behind bridge: 00000000fde00000-00000000fdefffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 3140
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at fe00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 3140
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at fd00 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 3140
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at fc00 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 3140
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at fb00 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 3140
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at fdfff000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fda00000-fdafffff
        Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 3140
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 3140
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at fa00 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 3140
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at f900 [size=8]
        I/O ports at f800 [size=4]
        I/O ports at f700 [size=8]
        I/O ports at f600 [size=4]
        I/O ports at f500 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 3140
        Flags: medium devsel, IRQ 15
        I/O ports at 0500 [size=32]

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 3140
        Flags: bus master, fast devsel, latency 0, IRQ 2301
        Memory at fddfc000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at ee00 [size=256]
        [virtual] Expansion ROM at fdc00000 [disabled] [size=128K]
        Capabilities: <access denied>

```

There is a dial tone when I pick up the phone and press the SEND button.  I can make and receive Skype calls using the phone.

**The #1 problem is the USB Telbox will make an audible click and I will no longer hear a dial tone nor be able to make and receive calls.**  Seconds, minutes, and hours may pass before the phone fails to work.

I started kb2kskype --debugmessages.  I picked up the phone, pressed the SEND button and heard a dial tone.  I pressed the CANCEL button and hung up the phone.  Less than two minutes later, I picked up the phone, pressed the SEND button and did not receive a dial tone.
```

Skype instance found, window id 29360414
NAME B2K_CONNECTOR (sent to skype) 
PROTOCOL 7 (sent to skype) 
OK (message from skype) 
PROTOCOL 7 (message from skype) 
CONNSTATUS ONLINE (message from skype) 
CURRENTUSERHANDLE ******** (message from skype) 
SEARCH FRIENDS (sent to skype) 
USERSTATUS INVISIBLE (message from skype) 
USERS echo123, +******** (message from skype) 
USB Device Found (from telbox) 
SWITCH USB (from telbox) 
HANDSET OFF (from telbox) 
MINIMIZE (sent to skype) 
OK (message from skype) 
USBB2K 2.08 Bus 003/003 DeviceVersion: B2Kv2 [0x57d] Serial: 20 05 04 11 00 00 00 00 00 01 f8 (from telbox) 
HANDSET ON (from telbox) 
FOCUS (from telbox) 
FOCUS (sent to skype) 
OK (message from skype) 
HANDSET OFF (from telbox) 
MINIMIZE (sent to skype) 
OK (message from skype) 

```

Below is debugging output from when I picked up and hung up twice having received a dial tone both times.
```

Skype instance found, window id 29360414
NAME B2K_CONNECTOR (sent to skype) 
PROTOCOL 7 (sent to skype) 
OK (message from skype) 
PROTOCOL 7 (message from skype) 
CONNSTATUS ONLINE (message from skype) 
CURRENTUSERHANDLE ******** (message from skype) 
SEARCH FRIENDS (sent to skype) 
USERSTATUS INVISIBLE (message from skype) 
USERS echo123, +********* (message from skype) 
USB Device Found (from telbox) 
SWITCH USB (from telbox) 
HANDSET OFF (from telbox) 
MINIMIZE (sent to skype) 
OK (message from skype) 
USBB2K 2.08 Bus 003/003 DeviceVersion: B2Kv2 [0x57d] Serial: 20 05 04 11 00 00 00 00 00 01 f8 (from telbox) 
HANDSET ON (from telbox) 
FOCUS (from telbox) 
FOCUS (sent to skype) 
OK (message from skype) 
HANDSET OFF (from telbox) 
MINIMIZE (sent to skype) 
OK (message from skype) 
HANDSET ON (from telbox) 
FOCUS (from telbox) 
FOCUS (sent to skype) 
OK (message from skype) 
HANDSET OFF (from telbox) 
MINIMIZE (sent to skype) 
OK (message from skype) 

```

The quick fix is to exit kb2kskype and restart kb2kskype.  I don't know if the USB Telbox is defective, if there is a kb2kskype bug, or if the Telbox and kb2kskype don't like each other.

Members of ubuntuforums, I ask for your help.

---

### Post by Sky Pixie on 2009-07-04
Update

I have been unable to configure the cordless Panasonic KX-TG1033S to my satisfaction.

I suspect the phone base and the telbox are speaking to each other, perhaps using kb2kskype.  If the phone base does not respond, the telbox terminates the connection, hence, no dial tone.

I purchased a corded at&t Digital Answering System Speakerphone 1856 to test this theory.  This phone does not randomly disconnect as often as the cordless Panasonic because the phone is tethered to the base.  However, kb2kskype does need to be reset when phone features such as ringtone, number of rings, etc. are changed.

---

