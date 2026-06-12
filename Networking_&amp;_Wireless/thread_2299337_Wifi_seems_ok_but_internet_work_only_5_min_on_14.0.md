---
title: "Wifi seems ok but internet work only 5 min on 14.04 LTS DWA-131 rev b1"
date: 2015-10-17
forum: Networking &amp; Wireless
---

### Post by tuff on 2015-10-17
Hello,
I've got a problem on my PC, my wifi connection work but internet cancelled approximatively 5 min after connection is established. (i can't ping google.com in terminal and firefox take 3 years to say me server not found)
i have to restart wifi connection in network manager which don't show me a lost connection. and i can surf for 5 more min

I tried apt-get upgrade, options rtl8192cu swenc=1,change canal and encryption on my box, fixed ip, i change usb port, the same model of wifi card which is working properly on my other computer(windows), and finally ndiswrapper make me crash wifi and wired and i have reinstalled ubuntu.
Nothing work
here is rapport when connection is on with no internet
May you can, help me :).
```

root@hohoho:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"


root@hohoho:~# lsusb
Bus 002 Device 004: ID 2001:330d D-Link Corp. 
Bus 002 Device 002: ID 0d7d:1620 Phison Electronics Corp. USB Disk Pro
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 046d:c534 Logitech, Inc. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

root@hohoho:~# lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:06.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV770 [Radeon HD 4850]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV770 HDMI Audio [Radeon HD 4850/4870]
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV770 [Radeon HD 4850]
02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV770 HDMI Audio [Radeon HD 4850/4870]
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
04:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II / PATA Controller (rev b1)
06:00.0 Multimedia audio controller: Creative Labs SB X-Fi
06:02.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
06:03.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 70)
root@hohoho:~# lspci -k
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
    Kernel driver in use: pcieport
00:06.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
    Kernel driver in use: pcieport
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard
    Kernel driver in use: uhci_hcd
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard
    Kernel driver in use: ehci-pci
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
    Kernel driver in use: pcieport
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
    Kernel driver in use: pcieport
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
    Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard
    Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV770 [Radeon HD 4850]
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 1530
    Kernel driver in use: radeon
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV770 HDMI Audio [Radeon HD 4850/4870]
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device aa30
    Kernel driver in use: snd_hda_intel
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV770 [Radeon HD 4850]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] MSI Radeon HD 4850 512MB GDDR3
    Kernel driver in use: radeon
02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV770 HDMI Audio [Radeon HD 4850/4870]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RV770 HDMI Audio [Radeon HD 4850/4870]
    Kernel driver in use: snd_hda_intel
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
    Subsystem: ASUSTeK Computer Inc. Motherboard
    Kernel driver in use: sky2
04:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II / PATA Controller (rev b1)
    Subsystem: ASUSTeK Computer Inc. Device 8212
    Kernel driver in use: pata_marvell
06:00.0 Multimedia audio controller: Creative Labs SB X-Fi
    Subsystem: Creative Labs Device 0022
    Kernel driver in use: snd_ctxfi
06:02.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
    Subsystem: ASUSTeK Computer Inc. Marvell 88E8001 Gigabit Ethernet Controller (Asus)
    Kernel driver in use: skge
06:03.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 70)
    Subsystem: ASUSTeK Computer Inc. LSI FW322/323 IEEE 1394a FireWire Controller
    Kernel driver in use: firewire_ohci
root@hohoho:~# sudo lshw -C network
  *-network               
       description: Ethernet interface
       produit: 88E8056 PCI-E Gigabit Ethernet Controller
       fabriquant: Marvell Technology Group Ltd.
       identifiant matériel: 0
       information bus: pci@0000:03:00.0
       nom logique: eth0
       version: 12
       numéro de série: 00:23:54:1a:aa:14
       capacité: 1Gbit/s
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       ressources: irq:22 mémoire:f7efc000-f7efffff portE/S:c800(taille=256) mémoire:f7ec0000-f7edffff
  *-network
       description: Ethernet interface
       produit: 88E8001 Gigabit Ethernet Controller
       fabriquant: Marvell Technology Group Ltd.
       identifiant matériel: 2
       information bus: pci@0000:06:02.0
       nom logique: eth1
       version: 14
       numéro de série: 00:23:54:09:59:0b
       capacité: 1Gbit/s
       bits: 32 bits
       horloge: 66MHz
       fonctionnalités: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.14 latency=64 link=no maxlatency=31 mingnt=23 multicast=yes port=twisted pair
       ressources: irq:15 mémoire:fe9fc000-fe9fffff portE/S:e800(taille=256) mémoire:fe9c0000-fe9dffff
  *-network
       description: Interface réseau sans fil
       identifiant matériel: 1
       information bus: usb@2:6
       nom logique: wlan1
       numéro de série: 48:ee:0c:73:98:4b
       fonctionnalités: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.19.0-25-generic firmware=N/A ip=192.168.1.22 link=yes multicast=yes wireless=IEEE 802.11bgn
root@hohoho:~# lsmod
Module                  Size  Used by
nls_iso8859_1          16384  2 
ctr                    16384  1 
ccm                    20480  1 
bnep                   20480  2 
rfcomm                 69632  0 
bluetooth             491520  10 bnep,rfcomm
snd_hda_codec_hdmi     53248  2 
coretemp               16384  0 
kvm_intel             151552  0 
kvm                   479232  1 kvm_intel
serio_raw              16384  0 
snd_hda_codec_analog    16384  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_analog
arc4                   16384  2 
dm_multipath           24576  0 
scsi_dh                16384  1 dm_multipath
rtl8192cu              69632  0 
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                73728  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              708608  3 rtl_usb,rtlwifi,rtl8192cu
joydev                 20480  0 
cfg80211              524288  2 mac80211,rtlwifi
lpc_ich                24576  0 
snd_hda_intel          32768  7 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  5 snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller,snd_hda_codec_analog
snd_ctxfi             106496  2 
snd_hwdep              20480  1 snd_hda_codec
amdkfd                 81920  1 
amd_iommu_v2           20480  1 amdkfd
radeon               1552384  4 
snd_pcm               106496  5 snd_ctxfi,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
ttm                    94208  1 radeon
drm_kms_helper        126976  1 radeon
snd                    86016  30 snd_ctxfi,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog
8250_fintek            16384  0 
tpm_infineon           20480  0 
asus_atk0110           20480  0 
drm                   344064  7 ttm,drm_kms_helper,radeon
mac_hid                16384  0 
i2c_algo_bit           16384  1 radeon
soundcore              16384  2 snd,snd_hda_codec
shpchp                 40960  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
pata_acpi              16384  0 
pata_marvell           16384  0 
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  2 hid_generic,usbhid
uas                    24576  0 
usb_storage            69632  3 uas
psmouse               114688  0 
firewire_ohci          40960  0 
firewire_core          69632  1 firewire_ohci
crc_itu_t              16384  1 firewire_core
skge                   53248  0 
sky2                   61440  0 
dm_mirror              24576  0 
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
ahci                   36864  2 
libahci                32768  1 ahci
floppy                 77824  0 

root@hohoho:~# iwconfig
eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"Freebox tuff"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: F4:CA:E5:D3:23:40   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0

root@hohoho:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:1a:aa:14  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:11 

eth1      Link encap:Ethernet  HWaddr 00:23:54:09:59:0b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:15 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          Packets reçus:7037 erreurs:0 :0 overruns:0 frame:0
          TX packets:7037 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:663959 (663.9 KB) Octets transmis:663959 (663.9 KB)

wlan1     Link encap:Ethernet  HWaddr 48:ee:0c:73:98:4b  
          inet adr:192.168.1.22  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: 2a01:e35:8bec:4d30:48b9:b47e:e942:f9b3/64 Scope:Global
          adr inet6: fe80::4aee:cff:fe73:984b/64 Scope:Lien
          adr inet6: 2a01:e35:8bec:4d30:4aee:cff:fe73:984b/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:12672 erreurs:0 :0 overruns:0 frame:0
          TX packets:9913 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:8910905 (8.9 MB) Octets transmis:1437548 (1.4 MB)

root@hohoho:~# sudo iwlist scan
eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: F4:CA:E5:D3:23:40
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Freebox tuff"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a8c6b3da7e
                    Extra: Last beacon: 176ms ago
                    IE: Unknown: 000C46726565626F782074756666
                    IE: Unknown: 010882848B962C0C1218
                    IE: Unknown: 030103
                    IE: Unknown: 2A0104
                    IE: Unknown: 3205243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AEE0803FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D1603050600000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 02 - Address: 42:AC:0A:46:C9:7C
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"orange"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000077f1fc849
                    Extra: Last beacon: 228ms ago
                    IE: Unknown: 00066F72616E6765
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201018D0003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A0C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1604080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706465220010D14
          Cell 03 - Address: F4:CA:E5:D3:23:42
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a8c6b2ea26
                    Extra: Last beacon: 108ms ago
                    IE: Unknown: 000F46726565576966695F736563757265
                    IE: Unknown: 010882848B962C0C1218
                    IE: Unknown: 030103
                    IE: Unknown: 2A0104
                    IE: Unknown: 3205243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1AEE0803FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D1603050600000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 04 - Address: 4C:AC:0A:46:C9:7C
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Livebox-C97C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000077f1ea0c9
                    Extra: Last beacon: 892ms ago
                    IE: Unknown: 000C4C697665626F782D43393743
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201018D0003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A0C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1604080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD8A0050F204104A0001101044000102103B00010310470010000000000000100000004CAC0A46C97C102100035A54451023000F4C697665626F782046545448207632102400085A542E312E302E321042000F4C4D5A3131303931343031313131391054000800060050F20400011011000F4C697665626F782046545448207632100800020086103C000101
          Cell 05 - Address: F4:CA:E5:D3:23:41
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a8c6b362ca
                    Extra: Last beacon: 140ms ago
                    IE: Unknown: 00084672656557696669
                    IE: Unknown: 010882848B962C0C1218
                    IE: Unknown: 030103
                    IE: Unknown: 2A0104
                    IE: Unknown: 3205243048606C
                    IE: Unknown: 2D1AEE0803FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D1603050600000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 06 - Address: 14:0C:76:FA:FE:34
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"freebox_ANNABA23"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009fb5e0168
                    Extra: Last beacon: 23016ms ago
                    IE: Unknown: 001066726565626F785F414E4E4142413233
                    IE: Unknown: 010882848B962C0C1218
                    IE: Unknown: 03010B
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0104
                    IE: Unknown: 3205243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A6C0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 07 - Address: F4:CA:E5:94:D7:D1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000033c92908bd1
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 00084672656557696669
                    IE: Unknown: 010882848B962C0C1218
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 3205243048606C
                    IE: Unknown: 2D1A6C0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 08 - Address: F4:CA:E5:94:D7:D2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000033c929012f7
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000F46726565576966695F736563757265
                    IE: Unknown: 010882848B962C0C1218
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 3205243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A6C0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 09 - Address: 14:0C:76:FA:FE:36
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009fcbb8160
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000F46726565576966695F736563757265
                    IE: Unknown: 010882848B962C0C1218
                    IE: Unknown: 03010B
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0104
                    IE: Unknown: 3205243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A6C0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 10 - Address: F4:CA:E5:94:D7:D0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"freebox_Assabi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000033c9290fbad
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000E66726565626F785F417373616269
                    IE: Unknown: 010882848B962C0C1218
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 3205243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A6C0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

root@hohoho:~# uname -r -m
3.19.0-25-generic x86_64
root@hohoho:~# cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
root@hohoho:~# nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            skge
  State:             unavailable
  Default:           no
  HW Address:        00:23:54:09:59:0B

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan1  [Freebox tuff 1] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        48:EE:0C:73:98:4B

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    FreeWifi_secure: Infra, F4:CA:E5:D3:23:42, Freq 2422 MHz, Rate 54 Mb/s, Strength 84 WPA2 Enterprise
    Livebox-C97C:    Infra, 4C:AC:0A:46:C9:7C, Freq 2427 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    FreeWifi:        Infra, F4:CA:E5:D3:23:41, Freq 2422 MHz, Rate 54 Mb/s, Strength 74
    orange:          Infra, 42:AC:0A:46:C9:7C, Freq 2427 MHz, Rate 54 Mb/s, Strength 54
    *Freebox tuff:   Infra, F4:CA:E5:D3:23:40, Freq 2422 MHz, Rate 54 Mb/s, Strength 63 WPA2
    FreeWifi:        Infra, F4:CA:E5:E7:6E:01, Freq 2417 MHz, Rate 54 Mb/s, Strength 4
    freebox_ANNABA23:Infra, 14:0C:76:FA:FE:34, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA
    FreeWifi_secure: Infra, F4:CA:E5:94:D7:D2, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA2 Enterprise
    FreeWifi:        Infra, F4:CA:E5:94:D7:D1, Freq 2462 MHz, Rate 54 Mb/s, Strength 4
    FreeWifi_secure: Infra, 14:0C:76:FA:FE:36, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA2 Enterprise
    freebox_Assabi:  Infra, F4:CA:E5:94:D7:D0, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA

  IPv4 Settings:
    Address:         192.168.1.22
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

  IPv6 Settings:
    Address:         2a01:e35:8bec:4d30:48b9:b47e:e942:f9b3
    Prefix:          64
    Gateway:         fe80::f6ca:e5ff:fe4f:12b

    Address:         2a01:e35:8bec:4d30:4aee:cff:fe73:984b
    Prefix:          64
    Gateway:         fe80::f6ca:e5ff:fe4f:12b

    Address:         fe80::4aee:cff:fe73:984b
    Prefix:          64
    Gateway:         fe80::f6ca:e5ff:fe4f:12b

    DNS:             2a01:e00::2
    DNS:             2a01:e00::1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:23:54:1A:AA:14

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


root@hohoho:~# sudo rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by praseodym on 2015-10-17
Change the driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.10
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   

```
Reboot.

---

### Post by tuff on 2015-10-30
You saved my life
Thank you very much !
i seems to work

---

