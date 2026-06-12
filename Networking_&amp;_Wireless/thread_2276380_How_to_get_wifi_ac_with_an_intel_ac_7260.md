---
title: "How to get wifi ac with an intel ac 7260 ?"
date: 2015-05-02
forum: Networking &amp; Wireless
---

### Post by amauryat on 2015-05-02
Hi, my hp envyM6 1164sf had a poor wifi with its rt3290 (n was only on 20MhZ)
Thus I replaced it with an intel AC 7260.
Performs very well on wifi n, but i can't figure out how to use the wifi ac of my provider...

```


>>    cat /etc/lsb-release 

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.04
DISTRIB_CODENAME=vivid
DISTRIB_DESCRIPTION="Ubuntu 15.04"

>>    lsusb 

Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 8087:07dc Intel Corp. 
Bus 003 Device 003: ID 064e:c33c Suyin Corp. 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc. Fingerprint scanner
Bus 001 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

>>    lspci -k -nn | grep -A 3 -i net 

07:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: Hewlett-Packard Company Device [103c:18a5]
    Kernel driver in use: r8169
08:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 4b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
    Kernel driver in use: iwlwifi

>>    sudo lshw -C network 

  *-network
       description: Ethernet interface
       produit: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabriquant: Realtek Semiconductor Co., Ltd.
       identifiant matériel: 0.2
       information bus: pci@0000:07:00.2
       nom logique: eth0
       version: 0a
       numéro de série: 84:34:97:14:24:7b
       taille: 10Mbit/s
       capacité: 1Gbit/s
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-1_0.0.3 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       ressources: irq:27 portE/S:2000(taille=256) mémoire:61404000-61404fff mémoire:61400000-61403fff
  *-network
       description: Interface réseau sans fil
       produit: Wireless 7260
       fabriquant: Intel Corporation
       identifiant matériel: 0
       information bus: pci@0000:08:00.0
       nom logique: wlan2
       version: 4b
       numéro de série: 00:15:00:ba:6c:97
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.19.0-15-generic firmware=25.15.12.0 ip=192.168.0.33 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       ressources: irq:31 mémoire:61500000-61501fff

>>    lsmod 

Module                  Size  Used by
uas                    24576  0 
usb_storage            69632  1 uas
nvram                  16384  0 
msr                    16384  0 
ctr                    16384  3 
ccm                    20480  3 
binfmt_misc            20480  1 
nls_iso8859_1          16384  1 
arc4                   16384  2 
iwlmvm                278528  0 
intel_rapl             20480  0 
snd_hda_codec_hdmi     53248  1 
iosf_mbi               16384  1 intel_rapl
snd_hda_codec_idt      65536  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_idt
snd_hda_intel          32768  3 
snd_hda_controller     32768  1 snd_hda_intel
mac80211              720896  1 iwlmvm
snd_hda_codec         143360  5 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
x86_pkg_temp_thermal    16384  0 
snd_hwdep              20480  1 snd_hda_codec
uvcvideo               90112  0 
intel_powerclamp       20480  0 
videobuf2_vmalloc      16384  1 uvcvideo
amdkfd                 81920  1 
coretemp               16384  0 
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         49152  1 uvcvideo
kvm_intel             151552  0 
v4l2_common            16384  1 videobuf2_core
kvm                   483328  1 kvm_intel
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
hp_wmi                 16384  0 
amd_iommu_v2           20480  1 amdkfd
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           16384  0 
media                  24576  2 uvcvideo,videodev
sparse_keymap          16384  1 hp_wmi
iwlwifi               196608  1 iwlmvm
snd_seq_midi_event     16384  1 snd_seq_midi
radeon               1556480  0 
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
snd_rawmidi            32768  1 snd_seq_midi
ghash_clmulni_intel    16384  0 
cryptd                 20480  1 ghash_clmulni_intel
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
i915                 1052672  3 
ttm                    98304  1 radeon
drm_kms_helper        122880  2 i915,radeon
rtsx_pci_ms            20480  0 
btusb                  32768  0 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
drm                   344064  7 ttm,i915,drm_kms_helper,radeon
cfg80211              540672  3 iwlwifi,mac80211,iwlmvm
bluetooth             491520  2 btusb
snd_timer              32768  2 snd_pcm,snd_seq
wmi                    20480  1 hp_wmi
memstick               20480  1 rtsx_pci_ms
joydev                 20480  0 
serio_raw              16384  0 
snd                    90112  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  2 snd,snd_hda_codec
hp_accel               28672  0 
mac_hid                16384  0 
i2c_algo_bit           16384  2 i915,radeon
lis3lv02d              20480  1 hp_accel
mei_me                 20480  0 
mei                    90112  1 mei_me
lpc_ich                24576  0 
video                  20480  1 i915
intel_smartconnect     16384  0 
hp_wireless            16384  0 
shpchp                 40960  0 
input_polldev          16384  1 lis3lv02d
ip6t_REJECT            16384  1 
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5 
xt_hl                  16384  6 
ip6t_rt                16384  3 
nf_conntrack_ipv6      20480  8 
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1 
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5 
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
xt_LOG                 16384  10 
xt_limit               16384  13 
xt_tcpudp              16384  18 
xt_addrtype            16384  4 
nf_conntrack_ipv4      16384  8 
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16 
ip6table_filter        16384  1 
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0 
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0 
nf_nat                 28672  1 nf_nat_ftp
nf_conntrack_ftp       20480  1 nf_nat_ftp
parport_pc             32768  0 
nf_conntrack          106496  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
ppdev                  20480  0 
lp                     20480  0 
iptable_filter         16384  1 
ip_tables              28672  1 iptable_filter
parport                45056  3 lp,ppdev,parport_pc
x_tables               36864  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
autofs4                40960  2 
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  2 hid_generic,usbhid
rtsx_pci_sdmmc         24576  0 
psmouse               118784  0 
ahci                   36864  4 
libahci                32768  1 ahci
r8169                  81920  0 
rtsx_pci               49152  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    16384  1 r8169

```
```


>>    iwconfig 

wlan2     IEEE 802.11abgn  ESSID:"LENii"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:24:D4:70:96:88   
          Bit Rate=270 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:326   Missed beacon:0


>>    ifconfig -a 

eth0      Link encap:Ethernet  HWaddr 84:34:97:14:24:7b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          Packets reçus:29590 erreurs:0 :0 overruns:0 frame:0
          TX packets:29590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:2670549 (2.6 MB) Octets transmis:2670549 (2.6 MB)

wlan2     Link encap:Ethernet  HWaddr 00:15:00:ba:6c:97  
          inet adr:192.168.0.33  Bcast:192.168.0.255  Masque:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:4849250 erreurs:0 :0 overruns:0 frame:0
          TX packets:9393581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:938321524 (938.3 MB) Octets transmis:12223587778 (12.2 GB)


>>    sudo iwlist scan 

wlan2     Scan completed :
          Cell 01 - Address: 00:24:D4:70:96:88
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"LENii"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c6b8943a1
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 00054C454E6969
                    IE: Unknown: 010882848B962C0C1218
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 3205243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AFE0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D1606051600000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 02 - Address: F4:CA:E5:F4:C8:ED
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d7ed4c8160
                    Extra: Last beacon: 5288ms ago
                    IE: Unknown: 00084672656557696669
                    IE: Unknown: 010882848B962C0C1218
                    IE: Unknown: 030103
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0104
                    IE: Unknown: 3205243048606C
                    IE: Unknown: 2D1A6C0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D1603001100000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:19:70:AC:16:DA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Bbox-CA82DC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003843bbecd1
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 000B42626F782D434138324443
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
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
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 04 - Address: 00:24:D4:70:96:89
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c6b89eec9
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 00084672656557696669
                    IE: Unknown: 010882848B962C0C1218
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 3205243048606C
                    IE: Unknown: 2D1AFE0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D1606051600000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 05 - Address: 00:19:70:4B:8F:45
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Livebox-f997"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003047bbbf8
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 000C4C697665626F782D66393937
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
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
                    IE: Unknown: DD180050F20201018E0003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A0C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD8B0050F204104A0001101044000102103B00010310470010000000000000100000000019704B8F4510210005536167656D1023000F4C697665626F78204654544820763210240007422E312E312E311042000F414E313232313632353735373535371054000800060050F20400011011000F4C697665626F782046545448207632100800020086103C000101
          Cell 06 - Address: 06:19:70:4B:8F:45
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"orange"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003047cacbc
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 00066F72616E6765
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201018E0003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A0C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706465220010D14
          Cell 07 - Address: 00:9C:02:0C:8E:BF
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-BF-Officejet 6700"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c6ad02cab
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 001A48502D5072696E742D42462D4F66666963656A65742036373030
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101810027A4000003A4000042435E0062322F00
          Cell 08 - Address: 00:24:D4:70:96:8A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c6b895329
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 000F46726565576966695F736563757265
                    IE: Unknown: 010882848B962C0C1218
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 3205243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1AFE0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D1606051600000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 09 - Address: 00:24:D4:D5:FE:7C
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"wifimaisonvalmarpp"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000124e87d8160
                    Extra: Last beacon: 5156ms ago
                    IE: Unknown: 0012776966696D6169736F6E76616C6D61727070
                    IE: Unknown: 010882848B962C0C1218
                    IE: Unknown: 030107
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0104
                    IE: Unknown: 3205243048606C
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 10 - Address: 88:25:2C:70:45:84
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"AFONE_WPA_2EC3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000024a7aa93ea
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 000E41464F4E455F5750415F32454333
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
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
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DDA00050F204104A000110104400010210570001001041000100103B00010310470010500B1FDA8B6E4C26B88469DF2F6CC7D910210005426577616E102300174152563435314150572D412D4C462D4C332041666F6E651024000A307830304135304132311042000F3938303030303037353438363131321054000800060050F20400011011000F496E66696E656F6E2044616E756265100800020080103C000101
          Cell 11 - Address: BA:B3:62:45:D9:BE
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:off
                    ESSID:"orange"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004634b2f180
                    Extra: Last beacon: 5012ms ago
                    IE: Unknown: 00066F72616E6765
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A0C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706465220010D14
          Cell 12 - Address: 4E:08:D3:C4:21:24
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"freebox_auteuil"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007af6ab1154
                    Extra: Last beacon: 4984ms ago
                    IE: Unknown: 000F66726565626F785F6175746575696C
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B000100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000043127A
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 13 - Address: 4E:08:D3:C4:21:26
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007af6ab244f
                    Extra: Last beacon: 4976ms ago
                    IE: Unknown: 00084672656557696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B000100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000043127A
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 14 - Address: 4E:08:D3:C4:21:27
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007af6ab2d19
                    Extra: Last beacon: 4976ms ago
                    IE: Unknown: 000F46726565576966695F736563757265
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B000100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000043127A
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 15 - Address: A0:21:B7:D6:02:E8
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"NUMERICABLE-58E0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000553b1c63a8d
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 00104E554D4552494341424C452D35384530
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160D080000000000000000000000000000000000000000
                    IE: Unknown: DD800050F204104A0001101044000102103B00010310470010D46A8590ECB6D9E16B2C4B35EF3A5E48102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F2040001101100094E6574676561724150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 16 - Address: 3C:81:D8:D8:5B:56
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Livebox-5B56"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000fcf1099a1
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 000C4C697665626F782D35423536
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010D
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 331AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 3D160D080000000000000000000000000000000000000000
                    IE: Unknown: 34160D080000000000000000000000000000000000000000
                    IE: Unknown: DD180050F20201018E0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8F0050F204104A0001101044000102103B000103104700103A4A3F384B3FFB3FFC493C3D074A3F3810210008536167656D636F6D10230016536167656D636F6D46617374333936355F4C42322E381024000C53475F4C42335F312E322E30104200094E51313232393146461054000800060050F204000110110000100800020006103C0001011049000600372A000120
          Cell 17 - Address: 1E:81:D8:D8:5B:56
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"orange"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=4b00000fcf10a967
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 00066F72616E6765
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010D
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 331AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 3D160D080000000000000000000000000000000000000000
                    IE: Unknown: 34160D080000000000000000000000000000000000000000
                    IE: Unknown: DD180050F20201018E0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 18 - Address: 14:0C:76:BB:04:10
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"LENii"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c6bad8efd
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 00054C454E6969
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030124
                    IE: Unknown: 070A465220240814640B1B00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AEF101BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D1624050000000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: BF0CB2010030EAFF0000EAFF0000
                    IE: Unknown: C005012A00FCFF
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 19 - Address: DC:71:44:E9:A3:00
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Bbox-A7A59974-5GHz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000016d723ae2f4
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 001242626F782D41374135393937342D3547487A
                    IE: Unknown: 01080C1218243048606C
                    IE: Unknown: 03012C
                    IE: Unknown: 3E0401162C00
                    IE: Unknown: 2D1AEE0103FFFF000001000000000000000000000000001846471100
                    IE: Unknown: 3D162C050100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000000127A
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: DD06001C51AA0100
                    IE: Unknown: 200103
                    IE: Unknown: 0706465220241210
          Cell 20 - Address: 18:62:2C:95:77:67
                    Channel:112
                    Frequency:5.56 GHz (Channel 112)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Livebox-7766"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000253b229b03b
                    Extra: Last beacon: 2496ms ago
                    IE: Unknown: 000C4C697665626F782D37373636
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030170
                    IE: Unknown: 050400030008
                    IE: Unknown: 07344652202401172801172C01173001173401173801173C01174001176401176801176C01177001177401178401178801178C011700
                    IE: Unknown: 200100
                    IE: Unknown: 2D1AEF011BFFFFFF00000000000000000000000000000406E4470D00
                    IE: Unknown: 3D16700F0000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD1D0050F204104A0001101044000102103C0001021049000600372A000120
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


>>    uname -r -m 

3.19.0-15-generic x86_64

>>    cat /etc/network/interfaces 

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

>>    nm-tool 


>>    sudo rfkill list 

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

