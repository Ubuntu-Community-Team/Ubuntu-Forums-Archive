---
title: "Wifi drops and won't reconnect"
date: 2014-01-23
forum: Networking &amp; Wireless
---

### Post by fipem on 2014-01-23
Hi guys, I'm having problems with my wifi connection, from time to time it drops and the only way to get it back is to disable and re-enable networking (sometimes i have to reboot since not always work)
I have an HP Pavilion SleekBook 15 which came with win8. I delete it and only have ubuntu 12.04

sudo lshw -c network

```
  *-network               
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 1c:3e:84:4e:8f:eb
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.8.0-35-generic firmware=0.37 ip=192.168.1.110 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f0210000-f021ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 05
       serial: d4:c9:ef:60:17:34
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:48 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
rulo@rulo-note:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  0 
mmc_block              27429  0 
vmnet                  55751  13 
parport_pc             28284  0 
vsock                  52918  0 
vmci                   87405  1 vsock
vmmon                  80278  0 
hid_dr                 12723  0 
ff_memless             13097  1 hid_dr
usbhid                 47346  1 hid_dr
hid                   105826  2 hid_dr,usbhid
snd_seq_dummy          12798  0 
usb_storage            61749  1 
vesafb                 13876  1 
bnep                   18399  2 
rfcomm                 47922  0 
bluetooth             247324  10 bnep,rfcomm
ppdev                  17113  0 
uvcvideo               82214  0 
videobuf2_core         40815  1 uvcvideo
videodev              130172  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
binfmt_misc            17540  1 
arc4                   12573  2 
kvm                   456261  0 
rt2800pci              18754  0 
ghash_clmulni_intel    13259  0 
rt2800lib              67510  1 rt2800pci
snd_hda_codec_idt      71153  1 
snd_hda_codec_hdmi     37463  1 
crc_ccitt              12707  1 rt2800lib
snd_hda_intel          44339  5 
aesni_intel            55495  0 
snd_hda_codec         141761  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
ablk_helper            13597  1 aesni_intel
snd_hwdep              13668  1 snd_hda_codec
cryptd                 20530  3 ghash_clmulni_intel,aesni_intel,ablk_helper
rt2x00pci              14621  1 rt2800pci
lrw                    13323  1 aesni_intel
rt2x00lib              55643  3 rt2800pci,rt2800lib,rt2x00pci
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
aes_x86_64             17255  1 aesni_intel
snd_seq_midi           13324  0 
fglrx                5294837  143 
snd_rawmidi            30417  1 snd_seq_midi
mac80211              631450  3 rt2800lib,rt2x00pci,rt2x00lib
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
xts                    12951  1 aesni_intel
gf128mul               14951  2 lrw,xts
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              526422  2 rt2x00lib,mac80211
psmouse                97902  0 
snd                    69533  20 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4              13459  0 
joydev                 17613  0 
hp_wmi                 18092  0 
microcode              23075  0 
rtsx_pci_ms            13180  0 
memstick               16605  1 rtsx_pci_ms
soundcore              12680  1 snd
k10temp                13173  0 
sparse_keymap          13890  1 hp_wmi
hp_accel               26012  0 
eeprom_93cx6           13344  1 rt2800pci
lis3lv02d              20200  1 hp_accel
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
serio_raw              13215  0 
amd_iommu_v2           19227  1 fglrx
input_polldev          13896  1 lis3lv02d
video                  19652  0 
mac_hid                13253  0 
wmi                    19256  1 hp_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
rtsx_pci_sdmmc         17800  0 
r8169                  68904  0 
rtsx_pci               34530  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25879  3 
libahci                31636  1 ahci


```

sudo lspci -v

```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
    Subsystem: Hewlett-Packard Company Device 193c
    Flags: bus master, 66MHz, medium devsel, latency 32

00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7600G] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 193c
    Flags: bus master, fast devsel, latency 0, IRQ 50
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=256]
    Memory at f0400000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_updates, radeon

00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
    Subsystem: Hewlett-Packard Company Device 193c
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at f0444000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f0300000-f03fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices, Inc. [AMD] Device 1234
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: f0200000-f02fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices, Inc. [AMD] Device 1234
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03) (prog-if 30 [XHCI])
    Subsystem: Hewlett-Packard Company Device 193c
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f0448000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [50] Power Management version 3
    Capabilities: [70] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [90] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [a0] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Latency Tolerance Reporting
    Kernel driver in use: xhci_hcd

00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
    Subsystem: Hewlett-Packard Company Device 193c
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 46
    I/O ports at 4118 [size=8]
    I/O ports at 4124 [size=4]
    I/O ports at 4110 [size=8]
    I/O ports at 4120 [size=4]
    I/O ports at 4100 [size=16]
    Memory at f044e000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [50] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Capabilities: [70] SATA HBA v1.0
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 193c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f044d000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 193c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at f044c000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci-pci

00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 193c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f044b000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 193c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at f044a000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci-pci

00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 14)
    Subsystem: Hewlett-Packard Company Device 193c
    Flags: 66MHz, medium devsel
    Kernel modules: i2c-piix4

00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 193c
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
    Subsystem: Hewlett-Packard Company Device 193c
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=64

00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Memory behind bridge: f0100000-f01fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices, Inc. [AMD] Device 0000
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0000000-f00fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices, Inc. [AMD] Device 0000
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0
    Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4
    Flags: fast devsel

00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5
    Flags: fast devsel

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8730M] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 193c
    Physical Slot: 0
    Flags: bus master, fast devsel, latency 0, IRQ 51
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0300000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 3000 [size=256]
    [virtual] Expansion ROM at f0340000 [disabled] [size=128K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Capabilities: [270] #19
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_updates

02:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
    Subsystem: Hewlett-Packard Company Device 18ec
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0210000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-00-eb-8f-4e-84-3e-1c
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci

02:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth
    Subsystem: Hewlett-Packard Company Device 18ec
    Flags: bus master, fast devsel, latency 0, IRQ 3
    Memory at f0200000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-00-ec-8f-4e-84-3e-1c

04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
    Subsystem: Hewlett-Packard Company Device 193c
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f0100000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-00-00-01-00-4c-e0-00
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller
    Flags: bus master, fast devsel, latency 0, IRQ 48
    I/O ports at 2000 [size=256]
    Memory at f0004000 (64-bit, prefetchable) [size=4K]
    Memory at f0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: r8169
    Kernel modules: r8169


```

Thanks a lot in advance!

---

### Post by praseodym on 2014-01-24
Check this driver:```


sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms 
wget http://media.cdn.ubuntu-de.org/forum/attachments/29/20/5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz
sudo tar xvf 5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz -C /usr/src/
sudo dkms add -m Ralink_3290sta -v 2.6.0.0
sudo dkms build -m Ralink_3290sta -v 2.6.0.0
sudo dkms install -m Ralink_3290sta -v 2.6.0.0 
sudo cp /usr/src/Ralink_3290sta/src/common/rt3290.bin /lib/firmware 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist-rt2800pci.conf  
```
Reboot.

---

### Post by fipem on 2014-01-24
Thanks a lot, I will try it and comment on it later

TY!

---

### Post by fipem on 2014-01-24
I got an error during the process, can I continue with the next steps? or shall I try something different?
Thanks you for your help
```
rulo@rulo-note:~$ sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms[sudo] password for rulo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
dkms set to manually installed.
linux-headers-3.8.0-35-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  gir1.2-rb-3.0 gir1.2-gstreamer-0.10 python-mako gir1.2-ubuntuoneui-3.0
  libdmapsharing-3.0-2 rhythmbox-data libdiscid0 libgpod-common
  librhythmbox-core5 libgpod4 gir1.2-gst-plugins-base-0.10
  libubuntuoneui-3.0-1 thunderbird-globalmenu media-player-info
  python-markupsafe libmusicbrainz3-6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.6 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libdpkg-perl libstdc++6-4.6-dev
  linux-headers-3.2.0-58 linux-headers-3.2.0-58-generic
Suggested packages:
  debian-keyring g++-multilib g++-4.6-multilib gcc-4.6-doc libstdc++6-4.6-dbg
  libstdc++6-4.6-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.6 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
  libstdc++6-4.6-dev linux-headers-3.2.0-58 linux-headers-3.2.0-58-generic
  linux-headers-generic
0 upgraded, 12 newly installed, 0 to remove and 10 not upgraded.
Need to get 22.0 MB of archives.
After this operation, 95.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libdpkg-perl dpkg-dev build-essential linux-headers-3.2.0-58
  linux-headers-3.2.0-58-generic linux-headers-generic
Install these packages without verification [y/N]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main libstdc++6-4.6-dev amd64 4.6.3-1ubuntu5 [1,660 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main g++-4.6 amd64 4.6.3-1ubuntu5 [6,954 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/main g++ amd64 4:4.6.3-1ubuntu5 [1,442 B]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdpkg-perl all 1.16.1.2ubuntu7.2 [180 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main dpkg-dev all 1.16.1.2ubuntu7.2 [469 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main build-essential amd64 11.5ubuntu2.1 [5,816 B]
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise/main libalgorithm-diff-perl all 1.19.02-2 [50.7 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ precise/main libalgorithm-diff-xs-perl amd64 0.04-2build2 [12.4 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-58 all 3.2.0-58.88 [11.7 MB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-58-generic amd64 3.2.0-58.88 [980 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-generic amd64 3.2.0.58.69 [2,356 B]
Fetched 22.0 MB in 6min 31s (56.2 kB/s)                                        
Selecting previously unselected package libstdc++6-4.6-dev.
(Reading database ... 185187 files and directories currently installed.)
Unpacking libstdc++6-4.6-dev (from .../libstdc++6-4.6-dev_4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package g++-4.6.
Unpacking g++-4.6 (from .../g++-4.6_4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package libdpkg-perl.
Unpacking libdpkg-perl (from .../libdpkg-perl_1.16.1.2ubuntu7.2_all.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.1.2ubuntu7.2_all.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from .../build-essential_11.5ubuntu2.1_amd64.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-2_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-2build2_amd64.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-58.
Unpacking linux-headers-3.2.0-58 (from .../linux-headers-3.2.0-58_3.2.0-58.88_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-58-generic.
Unpacking linux-headers-3.2.0-58-generic (from .../linux-headers-3.2.0-58-generic_3.2.0-58.88_amd64.deb) ...
Selecting previously unselected package linux-headers-generic.
Unpacking linux-headers-generic (from .../linux-headers-generic_3.2.0.58.69_amd64.deb) ...
Processing triggers for man-db ...
Setting up libdpkg-perl (1.16.1.2ubuntu7.2) ...
Setting up dpkg-dev (1.16.1.2ubuntu7.2) ...
Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build2) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up linux-headers-3.2.0-58 (3.2.0-58.88) ...
Setting up linux-headers-3.2.0-58-generic (3.2.0-58.88) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-58-generic /boot/vmlinuz-3.2.0-58-generic
Setting up linux-headers-generic (3.2.0.58.69) ...
Setting up libstdc++6-4.6-dev (4.6.3-1ubuntu5) ...
Setting up g++-4.6 (4.6.3-1ubuntu5) ...
Setting up g++ (4:4.6.3-1ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5ubuntu2.1) ...
rulo@rulo-note:~$ wget http://media.cdn.ubuntu-de.org/forum/attachments/29/20/5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz
--2014-01-24 22:24:04--  http://media.cdn.ubuntu-de.org/forum/attachments/29/20/5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz
Resolving media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)... 213.95.41.4, 2001:780:0:25:dead:beef:cafe:1
Connecting to media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)|213.95.41.4|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 925964 (904K) [application/octet-stream]
Saving to: `5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz'


61% [=======================>               ] 570,693     37.1K/s   in 15s     


2014-01-24 22:24:23 (37.1 KB/s) - Read error at byte 570693/925964 (Connection reset by peer). Retrying.


--2014-01-24 22:24:24--  (try: 2)  http://media.cdn.ubuntu-de.org/forum/attachments/29/20/5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz
Connecting to media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)|213.95.41.4|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 925964 (904K), 355271 (347K) remaining [application/octet-stream]
Saving to: `5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz'


100%[++++++++++++++++++++++++==============>] 925,964     73.6K/s   in 4.7s    


2014-01-24 22:24:31 (73.6 KB/s) - `5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz' saved [925964/925964]


rulo@rulo-note:~$ sudo tar xvf 5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz -C /usr/src/
Ralink_3290sta-2.6.0.0/src/include/chip/chip_id.h
Ralink_3290sta-2.6.0.0/src/include/chip/mac_pci.h
Ralink_3290sta-2.6.0.0/src/include/chip/rt28xx.h
Ralink_3290sta-2.6.0.0/src/include/chip/rt30xx.h
Ralink_3290sta-2.6.0.0/src/include/chip/rt3290.h
Ralink_3290sta-2.6.0.0/src/include/chip/rtmp_mac.h
Ralink_3290sta-2.6.0.0/src/include/chip/rtmp_phy.h
Ralink_3290sta-2.6.0.0/src/include/iface/iface_util.h
Ralink_3290sta-2.6.0.0/src/include/iface/rtmp_pci.h
Ralink_3290sta-2.6.0.0/src/include/os/rt_drv.h
Ralink_3290sta-2.6.0.0/src/include/os/rt_linux.h
Ralink_3290sta-2.6.0.0/src/include/os/rt_linux_cmm.h
Ralink_3290sta-2.6.0.0/src/include/os/rt_os.h
Ralink_3290sta-2.6.0.0/src/os/linux/Kconfig.ap.soc
Ralink_3290sta-2.6.0.0/src/os/linux/Kconfig.ap.usb
Ralink_3290sta-2.6.0.0/src/os/linux/Kconfig.sta.soc
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.4
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.4.netif
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.4.util
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.6
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.6.netif
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.6.netif~
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.6.util
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.ap.soc
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.ap.usb
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.clean
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.libautoprovision.6
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.sta.soc
Ralink_3290sta-2.6.0.0/src/os/linux/br_ftph.c
Ralink_3290sta-2.6.0.0/src/os/linux/cfg80211.c
Ralink_3290sta-2.6.0.0/src/os/linux/cfg80211drv.c
Ralink_3290sta-2.6.0.0/src/os/linux/config.mk
Ralink_3290sta-2.6.0.0/src/os/linux/inf_ppa.c
Ralink_3290sta-2.6.0.0/src/os/linux/pci_main_dev.c
Ralink_3290sta-2.6.0.0/src/os/linux/rt_linux.c
Ralink_3290sta-2.6.0.0/src/os/linux/rt_linux_symb.c
Ralink_3290sta-2.6.0.0/src/os/linux/rt_main_dev.c
Ralink_3290sta-2.6.0.0/src/os/linux/rt_pci_rbus.c
Ralink_3290sta-2.6.0.0/src/os/linux/rt_proc.c
Ralink_3290sta-2.6.0.0/src/os/linux/rt_profile.c
Ralink_3290sta-2.6.0.0/src/os/linux/rt_rbus_pci_drv.c
Ralink_3290sta-2.6.0.0/src/os/linux/rt_rbus_pci_util.c
Ralink_3290sta-2.6.0.0/src/os/linux/rt_symb.c
Ralink_3290sta-2.6.0.0/src/os/linux/sta_ioctl.c
Ralink_3290sta-2.6.0.0/src/os/linux/vr_bdlt.c
Ralink_3290sta-2.6.0.0/src/os/linux/vr_ikans.c
Ralink_3290sta-2.6.0.0/src/chips/rt28xx.c
Ralink_3290sta-2.6.0.0/src/chips/rt30xx.c
Ralink_3290sta-2.6.0.0/src/chips/rt3290.c
Ralink_3290sta-2.6.0.0/src/chips/rtmp_chip.c
Ralink_3290sta-2.6.0.0/src/common/action.c
Ralink_3290sta-2.6.0.0/src/common/ba_action.c
Ralink_3290sta-2.6.0.0/src/common/client_wds.c
Ralink_3290sta-2.6.0.0/src/common/cmm_aes.c
Ralink_3290sta-2.6.0.0/src/common/cmm_asic.c
Ralink_3290sta-2.6.0.0/src/common/cmm_cfg.c
Ralink_3290sta-2.6.0.0/src/common/cmm_cmd.c
Ralink_3290sta-2.6.0.0/src/common/cmm_cs.c
Ralink_3290sta-2.6.0.0/src/common/cmm_data.c
Ralink_3290sta-2.6.0.0/src/common/cmm_data_pci.c
Ralink_3290sta-2.6.0.0/src/common/cmm_info.c
Ralink_3290sta-2.6.0.0/src/common/cmm_mac_pci.c
Ralink_3290sta-2.6.0.0/src/common/cmm_profile.c
Ralink_3290sta-2.6.0.0/src/common/cmm_radar.c
Ralink_3290sta-2.6.0.0/src/common/cmm_sanity.c
Ralink_3290sta-2.6.0.0/src/common/cmm_sync.c
Ralink_3290sta-2.6.0.0/src/common/cmm_tkip.c
Ralink_3290sta-2.6.0.0/src/common/cmm_video.c
Ralink_3290sta-2.6.0.0/src/common/cmm_wep.c
Ralink_3290sta-2.6.0.0/src/common/cmm_wpa.c
Ralink_3290sta-2.6.0.0/src/common/crypt_aes.c
Ralink_3290sta-2.6.0.0/src/common/crypt_arc4.c
Ralink_3290sta-2.6.0.0/src/common/crypt_hmac.c
Ralink_3290sta-2.6.0.0/src/common/crypt_md5.c
Ralink_3290sta-2.6.0.0/src/common/crypt_sha2.c
Ralink_3290sta-2.6.0.0/src/common/ee_efuse.c
Ralink_3290sta-2.6.0.0/src/common/ee_prom.c
Ralink_3290sta-2.6.0.0/src/common/eeprom.c
Ralink_3290sta-2.6.0.0/src/common/frq_cal.c
Ralink_3290sta-2.6.0.0/src/common/frq_cal_ori.c
Ralink_3290sta-2.6.0.0/src/common/misc.c
Ralink_3290sta-2.6.0.0/src/common/mlme.c
Ralink_3290sta-2.6.0.0/src/common/netif_block.c
Ralink_3290sta-2.6.0.0/src/common/ps.c
Ralink_3290sta-2.6.0.0/src/common/rt2860.bin_ori
Ralink_3290sta-2.6.0.0/src/common/rt2860_ori.bin
Ralink_3290sta-2.6.0.0/src/common/rt3290.bin
Ralink_3290sta-2.6.0.0/src/common/rt_channel.c
Ralink_3290sta-2.6.0.0/src/common/rt_led.c
Ralink_3290sta-2.6.0.0/src/common/rt_os_util.c
Ralink_3290sta-2.6.0.0/src/common/rt_rf.c
Ralink_3290sta-2.6.0.0/src/common/rtmp_init.c
Ralink_3290sta-2.6.0.0/src/common/rtmp_init_inf.c
Ralink_3290sta-2.6.0.0/src/common/rtmp_mcu.c
Ralink_3290sta-2.6.0.0/src/common/rtmp_timer.c
Ralink_3290sta-2.6.0.0/src/common/spectrum.c
Ralink_3290sta-2.6.0.0/src/common/uapsd.c
Ralink_3290sta-2.6.0.0/src/include/action.h
Ralink_3290sta-2.6.0.0/src/include/ags.h
Ralink_3290sta-2.6.0.0/src/include/ap.h
Ralink_3290sta-2.6.0.0/src/include/ap_diversity.h
Ralink_3290sta-2.6.0.0/src/include/br_ftph.h
Ralink_3290sta-2.6.0.0/src/include/cfg80211.h
Ralink_3290sta-2.6.0.0/src/include/cfg80211extr.h
Ralink_3290sta-2.6.0.0/src/include/chlist.h
Ralink_3290sta-2.6.0.0/src/include/client_wds.h
Ralink_3290sta-2.6.0.0/src/include/client_wds_cmm.h
Ralink_3290sta-2.6.0.0/src/include/crypt_aes.h
Ralink_3290sta-2.6.0.0/src/include/crypt_arc4.h
Ralink_3290sta-2.6.0.0/src/include/crypt_hmac.h
Ralink_3290sta-2.6.0.0/src/include/crypt_md5.h
Ralink_3290sta-2.6.0.0/src/include/crypt_sha2.h
Ralink_3290sta-2.6.0.0/src/include/cs.h
Ralink_3290sta-2.6.0.0/src/include/dfs.h
Ralink_3290sta-2.6.0.0/src/include/dot11i_wpa.h
Ralink_3290sta-2.6.0.0/src/include/drs_extr.h
Ralink_3290sta-2.6.0.0/src/include/eeprom.h
Ralink_3290sta-2.6.0.0/src/include/firmware.h
Ralink_3290sta-2.6.0.0/src/include/frq_cal.h
Ralink_3290sta-2.6.0.0/src/include/link_list.h
Ralink_3290sta-2.6.0.0/src/include/misc.h
Ralink_3290sta-2.6.0.0/src/include/misc_cmm.h
Ralink_3290sta-2.6.0.0/src/include/mlme.h
Ralink_3290sta-2.6.0.0/src/include/netif_block.h
Ralink_3290sta-2.6.0.0/src/include/oid.h
Ralink_3290sta-2.6.0.0/src/include/radar.h
Ralink_3290sta-2.6.0.0/src/include/rt_config.h
Ralink_3290sta-2.6.0.0/src/include/rt_led.h
Ralink_3290sta-2.6.0.0/src/include/rt_os_net.h
Ralink_3290sta-2.6.0.0/src/include/rt_os_util.h
Ralink_3290sta-2.6.0.0/src/include/rt_txbf.h
Ralink_3290sta-2.6.0.0/src/include/rtmp.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_chip.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_cmd.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_comm.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_def.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_dot11.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_iface.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_mcu.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_os.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_osabl.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_timer.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_type.h
Ralink_3290sta-2.6.0.0/src/include/spectrum.h
Ralink_3290sta-2.6.0.0/src/include/spectrum_def.h
Ralink_3290sta-2.6.0.0/src/include/sta_cfg.h
Ralink_3290sta-2.6.0.0/src/include/uapsd.h
Ralink_3290sta-2.6.0.0/src/include/video.h
Ralink_3290sta-2.6.0.0/src/include/vr_ikans.h
Ralink_3290sta-2.6.0.0/src/include/vrut_ubm.h
Ralink_3290sta-2.6.0.0/src/include/wpa.h
Ralink_3290sta-2.6.0.0/src/include/wpa_cmm.h
Ralink_3290sta-2.6.0.0/src/include/wsc.h
Ralink_3290sta-2.6.0.0/src/rate_ctrl/alg_ags.c
Ralink_3290sta-2.6.0.0/src/rate_ctrl/alg_grp.c
Ralink_3290sta-2.6.0.0/src/rate_ctrl/alg_legacy.c
Ralink_3290sta-2.6.0.0/src/rate_ctrl/ra_ctrl.c
Ralink_3290sta-2.6.0.0/src/sta/assoc.c
Ralink_3290sta-2.6.0.0/src/sta/auth.c
Ralink_3290sta-2.6.0.0/src/sta/auth_rsp.c
Ralink_3290sta-2.6.0.0/src/sta/connect.c
Ralink_3290sta-2.6.0.0/src/sta/dls.c
Ralink_3290sta-2.6.0.0/src/sta/rtmp_ckipmic.c
Ralink_3290sta-2.6.0.0/src/sta/rtmp_data.c
Ralink_3290sta-2.6.0.0/src/sta/sanity.c
Ralink_3290sta-2.6.0.0/src/sta/sta_cfg.c
Ralink_3290sta-2.6.0.0/src/sta/sync.c
Ralink_3290sta-2.6.0.0/src/sta/wpa.c
Ralink_3290sta-2.6.0.0/src/tools/Makefile
Ralink_3290sta-2.6.0.0/src/tools/bin2h
Ralink_3290sta-2.6.0.0/src/tools/bin2h.c
Ralink_3290sta-2.6.0.0/src/README_STA_pci
Ralink_3290sta-2.6.0.0/src/RT2860STA.dat
Ralink_3290sta-2.6.0.0/src/RT2860STACard.dat
Ralink_3290sta-2.6.0.0/src/iwpriv_usage.txt
Ralink_3290sta-2.6.0.0/src/sta_ate_iwpriv_usage.txt
Ralink_3290sta-2.6.0.0/src/Makefile
Ralink_3290sta-2.6.0.0/dkms.conf
Ralink_3290sta-2.6.0.0/Makefile
Ralink_3290sta-2.6.0.0/src/include/chip/
Ralink_3290sta-2.6.0.0/src/include/iface/
Ralink_3290sta-2.6.0.0/src/include/os/
Ralink_3290sta-2.6.0.0/src/os/linux/
Ralink_3290sta-2.6.0.0/src/chips/
Ralink_3290sta-2.6.0.0/src/common/
Ralink_3290sta-2.6.0.0/src/include/
Ralink_3290sta-2.6.0.0/src/os/
Ralink_3290sta-2.6.0.0/src/rate_ctrl/
Ralink_3290sta-2.6.0.0/src/sta/
Ralink_3290sta-2.6.0.0/src/tools/
Ralink_3290sta-2.6.0.0/src/
Ralink_3290sta-2.6.0.0/
rulo@rulo-note:~$ sudo dkms add -m Ralink_3290sta -v 2.6.0.0


Creating symlink /var/lib/dkms/Ralink_3290sta/2.6.0.0/source ->
                 /usr/src/Ralink_3290sta-2.6.0.0


DKMS: add completed.
rulo@rulo-note:~$ sudo dkms build -m Ralink_3290sta -v 2.6.0.0


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....
'make' -C src/ all........................................(bad exit status: 2)
ERROR (dkms apport): binary package for Ralink_3290sta: 2.6.0.0 not found
Error! Bad return status for module build on kernel: 3.8.0-35-generic (x86_64)
Consult /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/make.log for more information.
rulo@rulo-note:~$ sudo dkms install -m Ralink_3290sta -v 2.6.0.0


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....
'make' -C src/ all......................................(bad exit status: 2)
ERROR (dkms apport): binary package for Ralink_3290sta: 2.6.0.0 not found
Error! Bad return status for module build on kernel: 3.8.0-35-generic (x86_64)
Consult /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/make.log for more information.
rulo@rulo-note:~$ 
```

---

### Post by praseodym on 2014-01-25
Please check
```

cat /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/make.log
dpkg -l linux-headers-$(uname -r) | grep ii
```

---

### Post by fipem on 2014-01-25
```
rulo@rulo-note:~$ cat /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/make.logDKMS make.log for Ralink_3290sta-2.6.0.0 for kernel 3.8.0-35-generic (x86_64)
Fri Jan 24 22:27:30 CLST 2014
make: Entering directory `/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src'
make -C tools
make[1]: Entering directory `/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/tools'
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/tools/bin2h
cp -f os/linux/Makefile.6 /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/Makefile
make -C /lib/modules/3.8.0-35-generic/build SUBDIRS=/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-35-generic'
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/crypt_md5.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/crypt_sha2.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/crypt_hmac.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/crypt_aes.o
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Wrap’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/crypt_aes.c:1466:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Unwrap’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/crypt_aes.c:1561:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat]
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/crypt_arc4.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/mlme.o
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/mlme.c:528:3: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/mlme.c:528:3: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_wep.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/action.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_data.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/rtmp_init.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/rtmp_init_inf.o
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/rtmp_init_inf.c: In function ‘rt28xx_init’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/rtmp_init_inf.c:162:3: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/rtmp_init_inf.c:178:10: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_tkip.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_aes.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_sync.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/eeprom.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_sanity.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_info.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_cfg.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_wpa.o
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_wpa.c: In function ‘PeerPairMsg3Action’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_wpa.c:1032:13: warning: unused variable ‘Cancelled’ [-Wunused-variable]
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_radar.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/spectrum.o
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/spectrum.c:1972:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat]
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/rtmp_timer.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/rt_channel.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_profile.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_asic.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_cmd.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/ps.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/uapsd.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_profile.o
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_profile.c: In function ‘STA_MonPktSend’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_profile.c:409:9: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat]
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rtmp_chip.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../sta/assoc.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../sta/auth.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../sta/auth_rsp.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../sta/sync.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../sta/sanity.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../sta/rtmp_data.o
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxDataFrame’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../sta/rtmp_data.c:283:17: warning: unused variable ‘pFmeCtrl’ [-Wunused-variable]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../sta/rtmp_data.c:282:8: warning: unused variable ‘OldPwrMgmt’ [-Wunused-variable]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxMgmtFrame’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../sta/rtmp_data.c:766:5: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../sta/connect.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../sta/wpa.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../sta/sta_cfg.o
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../sta/sta_cfg.c: In function ‘RTMPQueryInformation’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../sta/sta_cfg.c:3956:4: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../sta/sta_cfg.c: In function ‘RtmpIoctl_rt_private_get_statistics’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../sta/sta_cfg.c:7220:1: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘EEPROM_NIC_CONFIG3_STRUC’ [-Wformat]
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/rt_os_util.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_linux.o
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_linux.c:508:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
/usr/src/linux-headers-3.8.0-35-generic/arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_linux.c:510:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
/usr/src/linux-headers-3.8.0-35-generic/arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_linux.c:662:20: warning: assignment makes integer from pointer without a cast [enabled by default]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsPktInit’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_linux.c:681:2: warning: assignment makes integer from pointer without a cast [enabled by default]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_linux.c:708:15: warning: assignment makes integer from pointer without a cast [enabled by default]
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/ba_action.o
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/ba_action.c: In function ‘convert_reordering_packet_to_preAMSDU_or_802_3_packet’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/ba_action.c:1550:2: warning: assignment makes integer from pointer without a cast [enabled by default]
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/rt_led.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_mac_pci.o
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_mac_pci.c: In function ‘RT28xxPciMlmeRadioOn’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_mac_pci.c:2245:13: warning: unused variable ‘Cancelled’ [-Wunused-variable]
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_data_pci.o
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_data_pci.c: In function ‘RTMPFreeTXDUponTxDmaDone’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_data_pci.c:543:8: warning: unused variable ‘TXWISize’ [-Wunused-variable]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_data_pci.c: In function ‘RTMPHandleMgmtRingDmaDoneInterrupt’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_data_pci.c:738:8: warning: unused variable ‘TXWISize’ [-Wunused-variable]
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_rbus_pci_drv.o
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_rbus_pci_drv.c: In function ‘RTMPInitPCIeDevice’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_rbus_pci_drv.c:1349:22: warning: unused variable ‘Index’ [-Wunused-variable]
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/rtmp_mcu.o
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/rtmp_mcu.c: In function ‘RtmpAsicSendCommandToMcu’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/rtmp_mcu.c:464:8: warning: unused variable ‘offset’ [-Wunused-variable]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/rtmp_mcu.c:463:8: warning: unused variable ‘Configuration’ [-Wunused-variable]
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/ee_prom.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/ee_efuse.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../common/rt_rf.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt30xx.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.o
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c: In function ‘RT3290_AsicTxAlcGetAutoAgcOffset’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:1564:25: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c: In function ‘MlmeAntSelection’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2489:4: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2489:4: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2489:4: warning: format ‘%d’ expects argument of type ‘int’, but argument 4 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2507:5: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2522:5: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2522:5: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2523:5: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2523:5: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2526:5: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2526:5: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2527:5: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2527:5: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2528:5: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2528:5: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2545:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2545:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2545:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 4 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2559:9: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2565:9: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2574:8: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2581:8: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2583:7: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2583:7: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2595:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2595:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2596:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2596:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2597:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:2597:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c: In function ‘BtCoexSetting’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:3244:4: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘ULONG’ [-Wformat]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c: In function ‘Profile_TwoAnt’:
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../chips/rt3290.c:4097:2: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘CMB_CTRL_STRUC’ [-Wformat]
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_pci_rbus.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_rbus_pci_util.o
  CC [M]  /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/pci_main_dev.o
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/pci_main_dev.c:43:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rt2860_remove_one’
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/pci_main_dev.c:44:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rt2860_probe’
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/pci_main_dev.c:63:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__devinitdata’
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/pci_main_dev.c:85:17: error: ‘rt2860_pci_tbl’ undeclared here (not in a function)
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/pci_main_dev.c:86:17: error: ‘rt2860_probe’ undeclared here (not in a function)
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/pci_main_dev.c:88:5: error: implicit declaration of function ‘__devexit_p’ [-Werror=implicit-function-declaration]
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/pci_main_dev.c:88:29: error: ‘rt2860_remove_one’ undeclared here (not in a function)
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/pci_main_dev.c:292:24: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rt2860_probe’
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/pci_main_dev.c:463:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rt2860_remove_one’
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/pci_main_dev.c:71:1: error: ‘__mod_pci_device_table’ aliased to undefined symbol ‘rt2860_pci_tbl’
cc1: some warnings being treated as errors
make[2]: *** [/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/pci_main_dev.o] Error 1
make[1]: *** [_module_/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-35-generic'
make: *** [LINUX] Error 2
make: Leaving directory `/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src'
rulo@rulo-note:~$ dpkg -l linux-headers-$(uname -r) | grep ii
ii  linux-headers-3.8.0-35-generic              3.8.0-35.50~precise1                    Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
```

---

### Post by praseodym on 2014-01-25
Please remove the "tar.gz" files of the driver and the driver itself:
```

rm 5641297*.tar.gz
sudo dkms remove -m Ralink_3290sta -v 2.6.0.0 --all
sudo rm -r /usr/src/Ralink_3290sta-2.6.0.0
```
and try it again starting with "wget"

---

### Post by fipem on 2014-01-25
```
rulo@rulo-note:~$ rm 5641297*.tar.gzrulo@rulo-note:~$ sudo dkms remove -m Ralink_3290sta -v 2.6.0.0 --all
[sudo] password for rulo: 


------------------------------
Deleting module version: 2.6.0.0
completely from the DKMS tree.
------------------------------
Done.
rulo@rulo-note:~$ sudo rm -r /usr/src/Ralink_3290sta-2.6.0.0
rulo@rulo-note:~$ wget http://media.cdn.ubuntu-de.org/forum/attachments/29/20/5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz
--2014-01-25 10:06:07--  http://media.cdn.ubuntu-de.org/forum/attachments/29/20/5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz
Resolving media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)... 213.95.41.4, 2001:780:0:25:dead:beef:cafe:1
Connecting to media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)|213.95.41.4|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 925964 (904K) [application/octet-stream]
Saving to: `5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz'


100%[======================================>] 925,964     81.3K/s   in 10s     


2014-01-25 10:06:20 (89.0 KB/s) - `5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz' saved [925964/925964]


rulo@rulo-note:~$ sudo tar xvf 5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz -C /usr/src/
Ralink_3290sta-2.6.0.0/src/include/chip/chip_id.h
Ralink_3290sta-2.6.0.0/src/include/chip/mac_pci.h
Ralink_3290sta-2.6.0.0/src/include/chip/rt28xx.h
Ralink_3290sta-2.6.0.0/src/include/chip/rt30xx.h
Ralink_3290sta-2.6.0.0/src/include/chip/rt3290.h
Ralink_3290sta-2.6.0.0/src/include/chip/rtmp_mac.h
Ralink_3290sta-2.6.0.0/src/include/chip/rtmp_phy.h
Ralink_3290sta-2.6.0.0/src/include/iface/iface_util.h
Ralink_3290sta-2.6.0.0/src/include/iface/rtmp_pci.h
Ralink_3290sta-2.6.0.0/src/include/os/rt_drv.h
Ralink_3290sta-2.6.0.0/src/include/os/rt_linux.h
Ralink_3290sta-2.6.0.0/src/include/os/rt_linux_cmm.h
Ralink_3290sta-2.6.0.0/src/include/os/rt_os.h
Ralink_3290sta-2.6.0.0/src/os/linux/Kconfig.ap.soc
Ralink_3290sta-2.6.0.0/src/os/linux/Kconfig.ap.usb
Ralink_3290sta-2.6.0.0/src/os/linux/Kconfig.sta.soc
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.4
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.4.netif
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.4.util
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.6
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.6.netif
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.6.netif~
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.6.util
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.ap.soc
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.ap.usb
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.clean
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.libautoprovision.6
Ralink_3290sta-2.6.0.0/src/os/linux/Makefile.sta.soc
Ralink_3290sta-2.6.0.0/src/os/linux/br_ftph.c
Ralink_3290sta-2.6.0.0/src/os/linux/cfg80211.c
Ralink_3290sta-2.6.0.0/src/os/linux/cfg80211drv.c
Ralink_3290sta-2.6.0.0/src/os/linux/config.mk
Ralink_3290sta-2.6.0.0/src/os/linux/inf_ppa.c
Ralink_3290sta-2.6.0.0/src/os/linux/pci_main_dev.c
Ralink_3290sta-2.6.0.0/src/os/linux/rt_linux.c
Ralink_3290sta-2.6.0.0/src/os/linux/rt_linux_symb.c
Ralink_3290sta-2.6.0.0/src/os/linux/rt_main_dev.c
Ralink_3290sta-2.6.0.0/src/os/linux/rt_pci_rbus.c
Ralink_3290sta-2.6.0.0/src/os/linux/rt_proc.c
Ralink_3290sta-2.6.0.0/src/os/linux/rt_profile.c
Ralink_3290sta-2.6.0.0/src/os/linux/rt_rbus_pci_drv.c
Ralink_3290sta-2.6.0.0/src/os/linux/rt_rbus_pci_util.c
Ralink_3290sta-2.6.0.0/src/os/linux/rt_symb.c
Ralink_3290sta-2.6.0.0/src/os/linux/sta_ioctl.c
Ralink_3290sta-2.6.0.0/src/os/linux/vr_bdlt.c
Ralink_3290sta-2.6.0.0/src/os/linux/vr_ikans.c
Ralink_3290sta-2.6.0.0/src/chips/rt28xx.c
Ralink_3290sta-2.6.0.0/src/chips/rt30xx.c
Ralink_3290sta-2.6.0.0/src/chips/rt3290.c
Ralink_3290sta-2.6.0.0/src/chips/rtmp_chip.c
Ralink_3290sta-2.6.0.0/src/common/action.c
Ralink_3290sta-2.6.0.0/src/common/ba_action.c
Ralink_3290sta-2.6.0.0/src/common/client_wds.c
Ralink_3290sta-2.6.0.0/src/common/cmm_aes.c
Ralink_3290sta-2.6.0.0/src/common/cmm_asic.c
Ralink_3290sta-2.6.0.0/src/common/cmm_cfg.c
Ralink_3290sta-2.6.0.0/src/common/cmm_cmd.c
Ralink_3290sta-2.6.0.0/src/common/cmm_cs.c
Ralink_3290sta-2.6.0.0/src/common/cmm_data.c
Ralink_3290sta-2.6.0.0/src/common/cmm_data_pci.c
Ralink_3290sta-2.6.0.0/src/common/cmm_info.c
Ralink_3290sta-2.6.0.0/src/common/cmm_mac_pci.c
Ralink_3290sta-2.6.0.0/src/common/cmm_profile.c
Ralink_3290sta-2.6.0.0/src/common/cmm_radar.c
Ralink_3290sta-2.6.0.0/src/common/cmm_sanity.c
Ralink_3290sta-2.6.0.0/src/common/cmm_sync.c
Ralink_3290sta-2.6.0.0/src/common/cmm_tkip.c
Ralink_3290sta-2.6.0.0/src/common/cmm_video.c
Ralink_3290sta-2.6.0.0/src/common/cmm_wep.c
Ralink_3290sta-2.6.0.0/src/common/cmm_wpa.c
Ralink_3290sta-2.6.0.0/src/common/crypt_aes.c
Ralink_3290sta-2.6.0.0/src/common/crypt_arc4.c
Ralink_3290sta-2.6.0.0/src/common/crypt_hmac.c
Ralink_3290sta-2.6.0.0/src/common/crypt_md5.c
Ralink_3290sta-2.6.0.0/src/common/crypt_sha2.c
Ralink_3290sta-2.6.0.0/src/common/ee_efuse.c
Ralink_3290sta-2.6.0.0/src/common/ee_prom.c
Ralink_3290sta-2.6.0.0/src/common/eeprom.c
Ralink_3290sta-2.6.0.0/src/common/frq_cal.c
Ralink_3290sta-2.6.0.0/src/common/frq_cal_ori.c
Ralink_3290sta-2.6.0.0/src/common/misc.c
Ralink_3290sta-2.6.0.0/src/common/mlme.c
Ralink_3290sta-2.6.0.0/src/common/netif_block.c
Ralink_3290sta-2.6.0.0/src/common/ps.c
Ralink_3290sta-2.6.0.0/src/common/rt2860.bin_ori
Ralink_3290sta-2.6.0.0/src/common/rt2860_ori.bin
Ralink_3290sta-2.6.0.0/src/common/rt3290.bin
Ralink_3290sta-2.6.0.0/src/common/rt_channel.c
Ralink_3290sta-2.6.0.0/src/common/rt_led.c
Ralink_3290sta-2.6.0.0/src/common/rt_os_util.c
Ralink_3290sta-2.6.0.0/src/common/rt_rf.c
Ralink_3290sta-2.6.0.0/src/common/rtmp_init.c
Ralink_3290sta-2.6.0.0/src/common/rtmp_init_inf.c
Ralink_3290sta-2.6.0.0/src/common/rtmp_mcu.c
Ralink_3290sta-2.6.0.0/src/common/rtmp_timer.c
Ralink_3290sta-2.6.0.0/src/common/spectrum.c
Ralink_3290sta-2.6.0.0/src/common/uapsd.c
Ralink_3290sta-2.6.0.0/src/include/action.h
Ralink_3290sta-2.6.0.0/src/include/ags.h
Ralink_3290sta-2.6.0.0/src/include/ap.h
Ralink_3290sta-2.6.0.0/src/include/ap_diversity.h
Ralink_3290sta-2.6.0.0/src/include/br_ftph.h
Ralink_3290sta-2.6.0.0/src/include/cfg80211.h
Ralink_3290sta-2.6.0.0/src/include/cfg80211extr.h
Ralink_3290sta-2.6.0.0/src/include/chlist.h
Ralink_3290sta-2.6.0.0/src/include/client_wds.h
Ralink_3290sta-2.6.0.0/src/include/client_wds_cmm.h
Ralink_3290sta-2.6.0.0/src/include/crypt_aes.h
Ralink_3290sta-2.6.0.0/src/include/crypt_arc4.h
Ralink_3290sta-2.6.0.0/src/include/crypt_hmac.h
Ralink_3290sta-2.6.0.0/src/include/crypt_md5.h
Ralink_3290sta-2.6.0.0/src/include/crypt_sha2.h
Ralink_3290sta-2.6.0.0/src/include/cs.h
Ralink_3290sta-2.6.0.0/src/include/dfs.h
Ralink_3290sta-2.6.0.0/src/include/dot11i_wpa.h
Ralink_3290sta-2.6.0.0/src/include/drs_extr.h
Ralink_3290sta-2.6.0.0/src/include/eeprom.h
Ralink_3290sta-2.6.0.0/src/include/firmware.h
Ralink_3290sta-2.6.0.0/src/include/frq_cal.h
Ralink_3290sta-2.6.0.0/src/include/link_list.h
Ralink_3290sta-2.6.0.0/src/include/misc.h
Ralink_3290sta-2.6.0.0/src/include/misc_cmm.h
Ralink_3290sta-2.6.0.0/src/include/mlme.h
Ralink_3290sta-2.6.0.0/src/include/netif_block.h
Ralink_3290sta-2.6.0.0/src/include/oid.h
Ralink_3290sta-2.6.0.0/src/include/radar.h
Ralink_3290sta-2.6.0.0/src/include/rt_config.h
Ralink_3290sta-2.6.0.0/src/include/rt_led.h
Ralink_3290sta-2.6.0.0/src/include/rt_os_net.h
Ralink_3290sta-2.6.0.0/src/include/rt_os_util.h
Ralink_3290sta-2.6.0.0/src/include/rt_txbf.h
Ralink_3290sta-2.6.0.0/src/include/rtmp.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_chip.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_cmd.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_comm.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_def.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_dot11.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_iface.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_mcu.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_os.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_osabl.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_timer.h
Ralink_3290sta-2.6.0.0/src/include/rtmp_type.h
Ralink_3290sta-2.6.0.0/src/include/spectrum.h
Ralink_3290sta-2.6.0.0/src/include/spectrum_def.h
Ralink_3290sta-2.6.0.0/src/include/sta_cfg.h
Ralink_3290sta-2.6.0.0/src/include/uapsd.h
Ralink_3290sta-2.6.0.0/src/include/video.h
Ralink_3290sta-2.6.0.0/src/include/vr_ikans.h
Ralink_3290sta-2.6.0.0/src/include/vrut_ubm.h
Ralink_3290sta-2.6.0.0/src/include/wpa.h
Ralink_3290sta-2.6.0.0/src/include/wpa_cmm.h
Ralink_3290sta-2.6.0.0/src/include/wsc.h
Ralink_3290sta-2.6.0.0/src/rate_ctrl/alg_ags.c
Ralink_3290sta-2.6.0.0/src/rate_ctrl/alg_grp.c
Ralink_3290sta-2.6.0.0/src/rate_ctrl/alg_legacy.c
Ralink_3290sta-2.6.0.0/src/rate_ctrl/ra_ctrl.c
Ralink_3290sta-2.6.0.0/src/sta/assoc.c
Ralink_3290sta-2.6.0.0/src/sta/auth.c
Ralink_3290sta-2.6.0.0/src/sta/auth_rsp.c
Ralink_3290sta-2.6.0.0/src/sta/connect.c
Ralink_3290sta-2.6.0.0/src/sta/dls.c
Ralink_3290sta-2.6.0.0/src/sta/rtmp_ckipmic.c
Ralink_3290sta-2.6.0.0/src/sta/rtmp_data.c
Ralink_3290sta-2.6.0.0/src/sta/sanity.c
Ralink_3290sta-2.6.0.0/src/sta/sta_cfg.c
Ralink_3290sta-2.6.0.0/src/sta/sync.c
Ralink_3290sta-2.6.0.0/src/sta/wpa.c
Ralink_3290sta-2.6.0.0/src/tools/Makefile
Ralink_3290sta-2.6.0.0/src/tools/bin2h
Ralink_3290sta-2.6.0.0/src/tools/bin2h.c
Ralink_3290sta-2.6.0.0/src/README_STA_pci
Ralink_3290sta-2.6.0.0/src/RT2860STA.dat
Ralink_3290sta-2.6.0.0/src/RT2860STACard.dat
Ralink_3290sta-2.6.0.0/src/iwpriv_usage.txt
Ralink_3290sta-2.6.0.0/src/sta_ate_iwpriv_usage.txt
Ralink_3290sta-2.6.0.0/src/Makefile
Ralink_3290sta-2.6.0.0/dkms.conf
Ralink_3290sta-2.6.0.0/Makefile
Ralink_3290sta-2.6.0.0/src/include/chip/
Ralink_3290sta-2.6.0.0/src/include/iface/
Ralink_3290sta-2.6.0.0/src/include/os/
Ralink_3290sta-2.6.0.0/src/os/linux/
Ralink_3290sta-2.6.0.0/src/chips/
Ralink_3290sta-2.6.0.0/src/common/
Ralink_3290sta-2.6.0.0/src/include/
Ralink_3290sta-2.6.0.0/src/os/
Ralink_3290sta-2.6.0.0/src/rate_ctrl/
Ralink_3290sta-2.6.0.0/src/sta/
Ralink_3290sta-2.6.0.0/src/tools/
Ralink_3290sta-2.6.0.0/src/
Ralink_3290sta-2.6.0.0/
rulo@rulo-note:~$ sudo dkms add -m Ralink_3290sta -v 2.6.0.0


Creating symlink /var/lib/dkms/Ralink_3290sta/2.6.0.0/source ->
                 /usr/src/Ralink_3290sta-2.6.0.0


DKMS: add completed.
rulo@rulo-note:~$ sudo dkms build -m Ralink_3290sta -v 2.6.0.0


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....
'make' -C src/ all........................................(bad exit status: 2)
ERROR (dkms apport): binary package for Ralink_3290sta: 2.6.0.0 not found
Error! Bad return status for module build on kernel: 3.8.0-35-generic (x86_64)
Consult /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/make.log for more information.
rulo@rulo-note:~$ 
```

Should I continue?? Can I?

---

### Post by praseodym on 2014-01-25
Same error here with kernel 3.8.0-35 on 32bit.

So, boot in an earlier kernel: Reboot, press SHIFT during boot-up and choose "previous ubuntu versions" in the grub menu. Try to compile with the earlier kernel.

---

### Post by fipem on 2014-01-25
Did it work?

---

### Post by praseodym on 2014-01-25
I didnt try

---

### Post by praseodym on 2014-01-26
Please try to compile with the earlier kernel

---

### Post by fipem on 2014-01-26
Same error... is there another way to install those drivers? i really need a stable connection.

thanks

---

### Post by fipem on 2014-01-26
Well, sadly its enough for me, too many issues on this laptop. Switching back to windoze, thanks for all the help!

---

