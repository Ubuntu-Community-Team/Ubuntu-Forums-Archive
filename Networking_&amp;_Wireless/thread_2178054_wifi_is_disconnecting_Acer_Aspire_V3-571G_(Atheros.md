---
title: "wifi is disconnecting Acer Aspire V3-571G (Atheros AR9462) on Ubuntu 13.04"
date: 2013-10-01
forum: Networking &amp; Wireless
---

### Post by Maksim_Lekhman on 2013-10-01
Hello guys. my wifi connection is disappears too often after updating ubuntu 13.04

**Machine Brand and Model (PC/Laptop)**:
```
Acer Aspire V3-571G-53238G1TMaii (NX.M7EEU.001)
```
                                                                     
                                                                     lspci 
```
03:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)
```

lsusb
```
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1bcf:2c18 Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 0489:e04e Foxconn / Hon Hai 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 18a5:0243 Verbatim, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

ifconfig
```
wlan0     Link encap:Ethernet  HWaddr 9c:2a:70:4f:38:b9  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9e2a:70ff:fe4f:38b9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:18644 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24703999 (24.7 MB)  TX bytes:984123 (984.1 KB)
```

iwconfig
```
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

lsmod
```
Module                  Size  Used by
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  16 
bnep                   19564  2 
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138538  0 
kvm                   431315  1 kvm_intel
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  2 
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17377  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
snd_hda_codec_hdmi     41284  1 
snd_hda_codec_realtek    51465  1 
snd_hda_intel          48171  3 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
arc4                   12608  2 
microcode              23518  0 
ath9k                 151173  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
ath9k_common           13859  1 ath9k
ath9k_hw              444645  2 ath9k_common,ath9k
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
psmouse                97626  0 
serio_raw              13413  0 
mac80211              596969  1 ath9k
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
cfg80211              479757  3 ath,ath9k,mac80211
ath3k                  13318  0 
btusb                  28267  0 
lpc_ich                21080  0 
bluetooth             371874  23 bnep,ath3k,btusb,rfcomm
soundcore              12680  1 snd
mei_me                 18421  0 
mei                    77692  1 mei_me
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101225  3 hid_generic,usbhid
usb_storage            62062  0 
nouveau               943295  1 
i915                  655709  3 
mxm_wmi                13021  1 nouveau
ttm                    83995  1 nouveau
i2c_algo_bit           13413  2 i915,nouveau
sdhci_pci              18985  0 
drm_kms_helper         52651  2 i915,nouveau
sdhci                  42630  1 sdhci_pci
drm                   292643  7 ttm,i915,drm_kms_helper,nouveau
tg3                   162230  0 
ahci                   25819  3 
libahci                31898  1 ahci
ptp                    18580  1 tg3
pps_core               19027  1 ptp
wmi                    19070  3 acer_wmi,mxm_wmi,nouveau
video                  19318  3 i915,acer_wmi,nouveau
```

dmesg | grep wlan0
```
[ 2652.349952] wlan0: authenticate with 54:e6:fc:ae:c6:fc
[ 2652.362772] wlan0: send auth to 54:e6:fc:ae:c6:fc (try 1/3)
[ 2652.364658] wlan0: authenticated
[ 2652.368569] wlan0: associate with 54:e6:fc:ae:c6:fc (try 1/3)
[ 2652.371984] wlan0: RX AssocResp from 54:e6:fc:ae:c6:fc (capab=0x431 status=0 aid=1)
[ 2652.372238] wlan0: associated
```

sudo lshw -C network
 ```
 *-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: b8:88:e3:b2:2b:2c
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.132 firmware=sb latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:b3430000-b343ffff memory:b3440000-b344ffff memory:b3450000-b34507ff
  *-network
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 9c:2a:70:4f:38:b9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.11.0-8-generic firmware=N/A ip=192.168.1.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:b3500000-b357ffff memory:9fc00000-9fc0ffff
```

iwlist wlan0 scan
```
wlan0     Scan completed :
          Cell 01 - Address: 00:21:91:2D:FD:41
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"yakanet2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000012573467ca1
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000879616B616E657432
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030102
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
                    IE: Unknown: DD0900037F01010060FF7F
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B000103104700102550E0A7776126283B710021912DFD4110210006442D4C696E6B102300074449522D333030102400074449522D3330301042000830303030303030301054000800060050F2040001101100074449522D33303010080002008E
          Cell 02 - Address: C8:60:00:AC:33:DC
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"kris"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000023390d5f612
                    Extra: Last beacon: 2684ms ago
                    IE: Unknown: 00046B726973
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0600E04C020160
          Cell 03 - Address: C8:D3:A3:4B:59:DE
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"my"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006aeda11816
                    Extra: Last beacon: 3324ms ago
                    IE: Unknown: 00026D79
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000028127A
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706554120010E10
          Cell 04 - Address: 00:1F:1F:82:1E:3C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"G-HOME-2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000047c45c9c173
                    Extra: Last beacon: 2704ms ago
                    IE: Unknown: 0008472D484F4D452D32
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010007127A
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B000700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 05 - Address: 20:C9:D0:A3:C3:A6
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a801c595be
                    Extra: Last beacon: 2756ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400030000
                    IE: Unknown: 0706525520010D1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAD511BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301730320
                    IE: Unknown: DD0E0017F2070001010620C9D0A3C3A6
          Cell 06 - Address: 20:C9:D0:A3:C3:A7
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a7e936103b
                    Extra: Last beacon: 2616ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030124
                    IE: Unknown: 050401030000
                    IE: Unknown: 070652552024081E
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AEF111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16240D0400000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301730320
                    IE: Unknown: DD0E0017F2070001010620C9D0A3C3A6
          Cell 07 - Address: 00:19:CB:8D:A3:AB
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"volia_36"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000adc3b7419b
                    Extra: Last beacon: 2668ms ago
                    IE: Unknown: 0008766F6C69615F3336
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010D
                    IE: Unknown: 050400010014
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0700E04C01020300
          Cell 08 - Address: 84:C9:B2:4A:ED:B9
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Tpatata"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000022f6315d
                    Extra: Last beacon: 10052ms ago
                    IE: Unknown: 000754706174617461
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
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
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1605001B00000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
          Cell 09 - Address: 54:E6:FC:AE:C6:FC
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:"posontre"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000021f37ecbd
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 0008706F736F6E747265
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000
                    IE: Unknown: DD810050F204104A0001101044000102103B000103104700100000000000001000000054E6FCAEC6FC1021000754502D4C494E4B10230009544C2D57523934314E10240003322E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523934314E100800020086103C000101
          Cell 10 - Address: 94:0C:6D:F7:2E:94
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_F72E94"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000001c37504
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000E54502D4C494E4B5F463732453934
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409071900000000000000000000000000000000000000
                    IE: Unknown: 3D1609071900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD830050F204104A0001101044000101103B0001031047001000000000000010000000940C6DF72E941021000754502D4C494E4B10230009544C2D57523834314E10240003352E3010420003312E301054000800060050F20400011011001B576972656C657373204E20526F7574657220544C2D57523834314E100800020086103C000101
          Cell 11 - Address: A0:F3:C1:44:C4:DA
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"ToLiVolia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ba9ab2c93
                    Extra: Last beacon: 3396ms ago
                    IE: Unknown: 0009546F4C69566F6C6961
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706554120010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 331A6E1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601051700000000000000000000000000000000000000
                    IE: Unknown: 341601051700000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD990050F204104A0001101044000102103B0001031047001000000000000010000000A0F3C144C4101021000754502D4C494E4B10230009544C2D57523734304E10240003342E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523734304E100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 12 - Address: 2C:AB:25:65:15:80
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"DIR-300"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000684220760b
                    Extra: Last beacon: 3400ms ago
                    IE: Unknown: 00074449522D333030
                    IE: Unknown: 010882848B968C9298A4
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B0C8E0EC
                    IE: Unknown: 2D1A6E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601051100000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401051100000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 13 - Address: 90:94:E4:EF:5A:DE
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Jazz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000012edff16d
                    Extra: Last beacon: 3060ms ago
                    IE: Unknown: 00044A617A7A
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706554120010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010004
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070100000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101834003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050000D6127A
                    IE: Unknown: DD07000C4307000000
          Cell 14 - Address: D4:CA:6D:25:F0:59
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"MikroTik"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e033edd180
                    Extra: Last beacon: 8412ms ago
                    IE: Unknown: 00084D696B726F54696B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4E1003FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: DD2A000C42000000011E0010000000660B050000443443413644323546303539000000000000000005026C09
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E1003FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
          Cell 15 - Address: 54:04:A6:8D:E3:44
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"ASUS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003609fa701ea
                    Extra: Last beacon: 3116ms ago
                    IE: Unknown: 000441535553
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010002
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEC0117FF000000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000085127A
                    IE: Unknown: DD1E00904C33EC0117FF000000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
          Cell 16 - Address: 10:BF:48:C6:C9:00
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"IT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002f70434176
                    Extra: Last beacon: 2656ms ago
                    IE: Unknown: 00024954
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010D
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160D000000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340D000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD0E0050F204104A0001101044000102
```

uname -mr
```
3.11.0-8-generic x86_64
```

Please help me and thanks in advance!

---

### Post by varunendra on 2013-10-03
Welcome to the forums Maksim_Lekhman !

Is "yakanet2" your access-point? -
> **Maksim_Lekhman said:**
> ```

iwlist wlan0 scan
[CODE]wlan0     Scan completed :
          Cell 01 - Address: 00:21:91:2D:FD:41
                    [COLOR="#FF0000"]Channel:2[/COLOR]
                    .....
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
```
If yes, try changing the channel to 1 or 11, and the encryption algorithm to AES instead of TKIP in the router. Save the changes and reboot the router. Then in Ubuntu, please try -
```
sudo modprobe -rv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```
Do not reboot after this as it is a temporary change that will be lost at next boot. If it helps, we can make it permanent. If it does not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by Maksim_Lekhman on 2013-10-03
hello!
my access point is

```
Cell 09 - Address: 54:E6:FC:AE:C6:FC
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:"posontre"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000021f37ecbd
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 0008706F736F6E747265
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000
                    IE: Unknown: DD810050F204104A0001101044000102103B000103104700100000000000001000000054E6FCAEC6FC1021000754502D4C494E4B10230009544C2D57523934314E10240003322E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523934314E100800020086103C000101
         
```

here is result of script in attachement[ATTACH]246712[/ATTACH]

thank you

---

### Post by varunendra on 2013-10-04
In your original post, you mentioned the kernel version to be 3.[COLOR="#FF0000"]11[/COLOR].0-8-generic x86_64, while the script report states it to be 3.[COLOR="#000080"]8[/COLOR].0-19-generic. Have you re-installed the system? Or removed the newer kernel somehow?

Have you tried the "nohwcrypt=1" option I suggested? Any other suggestions from somewhere else? Please post the details if you have, preferably links if you followed some guide or another blog/thread-post.

---

### Post by Maksim_Lekhman on 2013-10-04
> **varunendra said:**
> In your original post, you mentioned the kernel version to be 3.[COLOR=#FF0000]11[/COLOR].0-8-generic x86_64, while the script report states it to be 3.[COLOR=#000080]8[/COLOR].0-19-generic. Have you re-installed the system? Or removed the newer kernel somehow?

Have you tried the "nohwcrypt=1" option I suggested? Any other suggestions from somewhere else? Please post the details if you have, preferably links if you followed some guide or another blog/thread-post.

yes, i've reinstalled my system from ubuntu 13.10 to 13.04 because the second one is currently supported and i think it is more stable. 

i've tried some solutions from this forum and from askubuntu.com:
[http://ubuntuforums.org/showthread.php?t=2133296](http://ubuntuforums.org/showthread.php?t=2133296)
[http://ubuntuforums.org/showthread.php?t=2081714](http://ubuntuforums.org/showthread.php?t=2081714)
[http://ubuntuforums.org/showthread.php?t=2121598](http://ubuntuforums.org/showthread.php?t=2121598)
[http://ubuntuforums.org/showthread.php?t=2157102](http://ubuntuforums.org/showthread.php?t=2157102)
[http://askubuntu.com/questions/301442/atheros-ar9462-wifi-very-unstable-package-loss](http://askubuntu.com/questions/301442/atheros-ar9462-wifi-very-unstable-package-loss)
[http://askubuntu.com/questions/217539/acer-aspire-one-wifi-atheros-communications-inc-ar9462-problem-with-12-10](http://askubuntu.com/questions/217539/acer-aspire-one-wifi-atheros-communications-inc-ar9462-problem-with-12-10)

i should try them today again on a new installed 13.04 system

also i've tried "nohwcrypt=1" option, but it did not help.

---

### Post by varunendra on 2013-10-05
So did you also try the [compat]("http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.8-1.tar.bz2") wireless 3.6 package with corrections suggested by matt_symes [post=12620869]here[/post]? (from page #5 of the first link you listed).

Actually that package builds an older driver than you already have (you have kernel 3.8, that compat driver is from kernel 3.6), but who cares if it works. I would have suggested to try the latest [backported]("http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/") one from kernel 3.11, but you already tried kernel 3.11 (and it failed too?).

Let me know the result if you tried that again. If not, please do the changes as suggested by matt_symes in that post, and see if it builds successfully (it should). Moreover, if it works any better, like it did on the older kernel.

If not, please post back the details of how you tried along with the "wireless_script" result with the compat driver installed. We may then try a few tweaks if applicable, or try the latest backported one anyway, as it does seem to work for some users.

---

### Post by Maksim_Lekhman on 2013-10-06
hello!

i have tried this solution one more time, and they've helped me
```
sudo nano /etc/modprobe.d/ath9k.conf

#fix wifi disconnecting
# [http://askubuntu.com/questions/301442/atheros-ar9462-wifi-very-unstable-package-loss](http://askubuntu.com/questions/301442/atheros-ar9462-wifi-very-unstable-package-loss)
# [http://askubuntu.com/questions/217539/acer-aspire-one-wifi-atheros-communications-inc-ar9462-problem-with-12-10](http://askubuntu.com/questions/217539/acer-aspire-one-wifi-atheros-communications-inc-ar9462-problem-with-12-10)
options ath9k nohwcrypt=1 blink=1 btcoex_enable=1 enable_diversity=1
```
at first they solved my issue on ubuntu 13.04, and then i have upgraded my system to 13.10 beta, and now my connection is ok!

Thank you guys!

---

