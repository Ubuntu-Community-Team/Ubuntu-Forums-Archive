---
title: "Cannot connect to wi-fi (Toshiba Satellite p305) [SOLVED]"
date: 2015-10-02
forum: Networking &amp; Wireless
---

### Post by heroquestelf on 2015-10-02
I had a hard drive crash, and now that I have the new drive in, my wifi won't connect. 

For the record, my tablet and one of my other PC's ***ARE*** connecting, and I have gone into the internals of the router and tried multiple channels (it's currently on channel 11) and also verified the password. I use a WEP encryption.

I am running Ubuntu 14.04 LTS and the laptop is a Toshiba Satellite P-305 with an Atheros (I think) network card. Here is what I've done so far. Maybe you guys can see what I'm missing.

I started out with an *ifconfig  *and got this:

```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:62:a5:30  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:18855 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14893160 (14.8 MB)  TX bytes:2025350 (2.0 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:473888 (473.8 KB)  TX bytes:473888 (473.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:5c:88:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:33542 (33.5 KB)


```

I then ran [I]iwconfig

[/I]```

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Maftet"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.
```

(yes, my network is named for the Egyptian Goddess of Vengeance... long story.)

I then ran [I]sudo lsmod
[/I]
```
Module                  Size  Used by
nls_iso8859_1          12713  0 
uas                    27255  0 
usb_storage            66545  1 uas
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
hid_generic            12559  0 
snd_hda_codec_conexant    23109  1 
snd_hda_codec_generic    69011  1 snd_hda_codec_conexant
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
snd_hda_intel          30469  3 
snd_hda_controller     30228  1 snd_hda_intel
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
snd_hda_codec         139719  4 snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104112  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
usbhid                 52616  0 
hid                   110426  3 hid_generic,usbhid
arc4                   12608  2 
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
iwl3945                73279  0 
iwlegacy              100522  1 iwl3945
coretemp               13441  0 
rfcomm                 69509  0 
mac80211              652777  2 iwl3945,iwlegacy
bnep                   19624  2 
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
joydev                 17393  0 
bluetooth             446409  10 bnep,rfcomm
serio_raw              13483  0 
6lowpan_iphc           18702  1 bluetooth
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
i915                  906106  3 
snd_timer              29562  2 snd_pcm,snd_seq
drm_kms_helper         61574  1 i915
snd                    79468  16 snd_hwdep,snd_timer,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
cfg80211              498458  3 iwl3945,iwlegacy,mac80211
lpc_ich                21093  0 
drm                   311018  5 i915,drm_kms_helper
shpchp                 37047  0 
soundcore              15047  2 snd,snd_hda_codec
i2c_algo_bit           13413  1 i915
toshiba_acpi           28272  0 
sparse_keymap          13948  1 toshiba_acpi
wmi                    19193  1 toshiba_acpi
toshiba_bluetooth      12867  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
video                  20128  1 i915
parport                42348  3 lp,ppdev,parport_pc
mac_hid                13227  0 
psmouse               106767  0 
ahci                   34142  2 
libahci                32424  1 ahci
pata_acpi              13053  0 
sdhci_pci              23301  0 
sdhci                  43685  1 sdhci_pci
firewire_ohci          40551  0 
firewire_core          68769  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sky2                   58206  0 


```

I then tried [I]ifconfig -a

[/I]```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:62:a5:30  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:18855 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14893160 (14.8 MB)  TX bytes:2025350 (2.0 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4586 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:477656 (477.6 KB)  TX bytes:477656 (477.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:5c:88:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:33542 (33.5 KB)


```[I]

rfkill list all
[/I]
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

*lspci -knn | grep Net -A2*

```

02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation Device [8086:1040]
    Kernel driver in use: iwl3945
```

*sudo lspci -v*

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0a <?>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f0000000 (64-bit, non-prefetchable) [size=1M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 3
    Kernel driver in use: i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, fast devsel, latency 0
    Memory at f0100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [d0] Power Management version 3

00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at f0704800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f0300000-f03fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000c01fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Toshiba America Info Systems Device ff50
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0200000-f02fffff
    Prefetchable memory behind bridge: 00000000c0200000-00000000c03fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Toshiba America Info Systems Device ff50
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: c0400000-c05fffff
    Prefetchable memory behind bridge: 00000000c0600000-00000000c07fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Toshiba America Info Systems Device ff50
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 18a0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f0704c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci-pci

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
    Memory behind bridge: f0400000-f04fffff
    Capabilities: [50] Subsystem: Device 0000:0000

00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: lpc_ich

00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4
    I/O ports at 0170 [size=8]
    I/O ports at 0374
    I/O ports at 1810 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
    I/O ports at 1c00 [size=8]
    I/O ports at 18d4 [size=4]
    I/O ports at 18d8 [size=8]
    I/O ports at 18d0 [size=4]
    I/O ports at 18e0 [size=32]
    Memory at f0704000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/4 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: medium devsel, IRQ 10
    Memory at c0800000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 1c20 [size=32]

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Intel Corporation Device 1040
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f0300000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-1f-3c-ff-ff-5c-88-48
    Kernel driver in use: iwl3945

03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
    Subsystem: Toshiba America Info Systems Satellite P305D-S8995E
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at 2000 [size=256]
    Capabilities: [48] Power Management version 3
    Capabilities: [5c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [c0] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [130] Device Serial Number 30-a5-62-ff-ff-68-1e-00
    Kernel driver in use: sky2

0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10 [OHCI])
    Subsystem: Toshiba America Info Systems Satellite P305D-S8995E
    Flags: bus master, stepping, medium devsel, latency 32, IRQ 16
    Memory at f0400000 (32-bit, non-prefetchable) [size=4K]
    Memory at f0402000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [60] Power Management version 2
    Kernel driver in use: firewire_ohci

0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02) (prog-if 01)
    Subsystem: Toshiba America Info Systems Satellite P305D-S8995E
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at f0402800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: sdhci-pci

0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
    Subsystem: Toshiba America Info Systems Satellite P305D-S8995E
    Flags: slow devsel, IRQ 5
    Memory at f0401000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [a0] Power Management version 2

```


My /etc/network/interfaces file reads

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

I am totally lost here. Anybody got any idea what's going on?

I also checked the sticky for the topic, and I wanted to update the thread with my wireless info.txt file.

```


########## wireless info START ##########

Report from: 03 Oct 2015 09:29 EDT -0400

Booted last: 03 Oct 2015 09:25 EDT -0400

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-50-generic #66~14.04.1-Ubuntu SMP Thu Sep 10 17:05:00 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation Device [8086:1040]
    Kernel driver in use: iwl3945

03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller [11ab:4355] (rev 12)
    Subsystem: Toshiba America Info Systems Satellite P305D-S8995E [1179:ff50]
    Kernel driver in use: sky2

##### lsusb #############################

Bus 002 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwl3945                73279  0 
iwlegacy              100522  1 iwl3945
mac80211              652777  2 iwl3945,iwlegacy
cfg80211              498458  3 iwl3945,iwlegacy,mac80211
wmi                    19193  1 toshiba_acpi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.2.14  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:654 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:254575 (254.5 KB)  TX bytes:140718 (140.7 KB)
          Interrupt:17 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6647 (6.6 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search Belkin

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root       751     1  0 09:25 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Maftet:          Infra, <MAC 'Maftet' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WEP

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Maftet]] (600 root)
[connection] id=Maftet | type=802-11-wireless
[802-11-wireless] ssid=Maftet | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     24 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Maftet' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"Maftet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a70abcdba
                    Extra: Last beacon: 36ms ago

##### module infos ######################

[iwl3945]
filename:       /lib/modules/3.16.0-50-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     74607945F172262E502CED2
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.16.0-50-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:AD:CD:D9:FB:6A:09:6D:98:72:72:DD:1C:13:A3:C2:69:8F:51:CA
sig_hashalgo:   sha512
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/3.16.0-50-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     1FA10C0B834AAF4AE219899
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-50-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:AD:CD:D9:FB:6A:09:6D:98:72:72:DD:1C:13:A3:C2:69:8F:51:CA
sig_hashalgo:   sha512
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[mac80211]
filename:       /lib/modules/3.16.0-50-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F027B13105AEA0ECF6ABE3F
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-50-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:AD:CD:D9:FB:6A:09:6D:98:72:72:DD:1C:13:A3:C2:69:8F:51:CA
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-50-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     046346857FD53951C911443
depends:        
intree:         Y
vermagic:       3.16.0-50-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:AD:CD:D9:FB:6A:09:6D:98:72:72:DD:1C:13:A3:C2:69:8F:51:CA
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwl3945]
antenna: 0
disable_hw_scan: 1
fw_restart: 1
swcrypto: 1

[iwlegacy]
bt_coex_active: Y
led_mode: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x11ab:0x4355 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    4.327095] sky2 0000:03:00.0 eth0: enabling interface
[    4.331405] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.875024] iwl3945 0000:02:00.0: loaded firmware version 15.32.2.9
[    6.995189] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   45.849495] wlan0: authenticate with <MAC 'Maftet' [AC1]>
[   45.854028] wlan0: send auth to <MAC 'Maftet' [AC1]> (try 1/3)
[   45.855919] wlan0: authenticated
[   45.856411] iwl3945 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   45.860212] wlan0: associate with <MAC 'Maftet' [AC1]> (try 1/3)
[   45.862854] wlan0: RX AssocResp from <MAC 'Maftet' [AC1]> (capab=0x411 status=0 aid=3)
[   45.865165] wlan0: associated
[   45.865258] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   91.212099] wlan0: deauthenticating from <MAC 'Maftet' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[   97.284412] sky2 0000:03:00.0 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   97.284537] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

---

### Post by jeremy31 on 2015-10-03
I would switch to WPA2 only on the wireless router and shut off either wicd or network manager, using both can't help

---

### Post by heroquestelf on 2015-10-03
I don't want to be contrary, but switching over to WPA ***broke ***my network. Fully half of my devices could no longer connect. My server and my two Nooks both were unable to connect (and yes, before you ask, I did update the password on all of them). I had to switch back over to WEP to get everything connected again. If THAT is the problem, then I have a much bigger issue.

I did, however, go ahead and uninstall WiCD.

Anybody got any ideas on this one, or do I just need to buy an external wireless card?

---

### Post by jeremy31 on 2015-10-04
Are there any updates for the router?  Your wifi card is an older one, Intel 3945, but it should work with WPA2 as mine did

---

