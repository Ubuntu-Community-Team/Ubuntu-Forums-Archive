---
title: "Wifi not working on HP Pavillion g6 laptop, chipset Qualcom Atheros ar9485"
date: 2016-06-30
forum: Networking &amp; Wireless
---

### Post by ap-us on 2016-06-30
Hi, good afternoon,

Please, could you help me resolve this issue with my wireless connection? This week I successfully installed Ubuntu 16.04 LTS. At first the wireless icon showed. Entering the login and password of my network did not connect.  After implementing some suggestions I found on the web the icon disappeared. Placing the laptop close to the modem did not help either. Im now using an Ethernet connection.

Maybe I messed out something trying to find a solution. As  most of the replies posted in this forum request users to run some commands, I'm pleased to share the outputs of the ones I used. 

Thanks I advance for all of your help and please, let me know if additional information is needed.

Sincerely,

```
ap-us

--

Commands used:

lspci -nnk | grep -iA2 net lsusb
lsmod
iwconfig
rfkill list
iwlist chan
sudo iwlist scan

--


OUTPUTS
                        lspci -nnk | grep -iA2 net

02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    DeviceName: Atheros AR9485 802.11b/g/n WiFi Adapter
    Subsystem: Hewlett-Packard Company AR9485/HB125 802.11bgn 1×1 Wi-Fi Adapter [103c:1838]
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    DeviceName: Realtek PCIe FE Family Controller
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:1849]
    Kernel driver in use: r8169
    Kernel modules: r8169

lsusb

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b34f Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



lsmod

Module                  Size  Used by
appletalk              36864  0
ipx                    28672  0
p8023                  16384  1 ipx
p8022                  16384  1 ipx
psnap                  16384  2 ipx,appletalk
llc                    16384  2 p8022,psnap
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
kvm                   536576  0
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_hda_codec_idt      57344  1
snd_hda_codec_generic    77824  1 snd_hda_codec_idt
snd_hda_codec_hdmi     53248  1
aesni_intel           167936  0
snd_hda_intel          36864  5
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
uvcvideo               90112  0
snd_hda_codec         135168  4 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
snd_hda_core           73728  5 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
rtsx_pci_ms            20480  0
snd_hwdep              16384  1 snd_hda_codec
memstick               20480  1 rtsx_pci_ms
cryptd                 20480  2 aesni_intel,ablk_helper
joydev                 20480  0
input_leds             16384  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
serio_raw              16384  0
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
k10temp                16384  0
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
media                  24576  2 uvcvideo,videodev
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
shpchp                 36864  0
soundcore              16384  1 snd
i2c_piix4              24576  0
hp_accel               28672  0
lis3lv02d              20480  1 hp_accel
hp_wireless            16384  0
input_polldev          16384  1 lis3lv02d
mac_hid                16384  0
arc4                   16384  2
ath9k                 143360  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              737280  1 ath9k
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_logitech_hidpp     20480  0
hid_logitech_dj        20480  0
usbhid                 49152  0
hid                   118784  4 usbhid,hid_logitech_dj,hid_logitech_hidpp
rtsx_pci_sdmmc         24576  0
amdkfd                131072  1
amd_iommu_v2           20480  1 amdkfd
radeon               1515520  4
i2c_algo_bit           16384  1 radeon
ttm                    94208  1 radeon
drm_kms_helper        147456  1 radeon
psmouse               126976  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
r8169                  81920  0
fb_sys_fops            16384  1 drm_kms_helper
mii                    16384  1 r8169
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   36864  2
drm                   360448  7 ttm,drm_kms_helper,radeon
libahci                32768  1 ahci
wmi                    20480  1 hp_wmi
fjes                   28672  0
video                  40960  0


iwconfig

Module                  Size  Used by
appletalk              36864  0
ipx                    28672  0
p8023                  16384  1 ipx
p8022                  16384  1 ipx
psnap                  16384  2 ipx,appletalk
llc                    16384  2 p8022,psnap
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
kvm                   536576  0
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_hda_codec_idt      57344  1
snd_hda_codec_generic    77824  1 snd_hda_codec_idt
snd_hda_codec_hdmi     53248  1
aesni_intel           167936  0
snd_hda_intel          36864  5
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
uvcvideo               90112  0
snd_hda_codec         135168  4 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
snd_hda_core           73728  5 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
rtsx_pci_ms            20480  0
snd_hwdep              16384  1 snd_hda_codec
memstick               20480  1 rtsx_pci_ms
cryptd                 20480  2 aesni_intel,ablk_helper
joydev                 20480  0
input_leds             16384  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
serio_raw              16384  0
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
k10temp                16384  0
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
media                  24576  2 uvcvideo,videodev
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
shpchp                 36864  0
soundcore              16384  1 snd
i2c_piix4              24576  0
hp_accel               28672  0
lis3lv02d              20480  1 hp_accel
hp_wireless            16384  0
input_polldev          16384  1 lis3lv02d
mac_hid                16384  0
arc4                   16384  2
ath9k                 143360  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              737280  1 ath9k
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_logitech_hidpp     20480  0
hid_logitech_dj        20480  0
usbhid                 49152  0
hid                   118784  4 usbhid,hid_logitech_dj,hid_logitech_hidpp
rtsx_pci_sdmmc         24576  0
amdkfd                131072  1
amd_iommu_v2           20480  1 amdkfd
radeon               1515520  4
i2c_algo_bit           16384  1 radeon
ttm                    94208  1 radeon
drm_kms_helper        147456  1 radeon
psmouse               126976  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
r8169                  81920  0
fb_sys_fops            16384  1 drm_kms_helper
mii                    16384  1 r8169
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   36864  2
drm                   360448  7 ttm,drm_kms_helper,radeon
libahci                32768  1 ahci
wmi                    20480  1 hp_wmi
fjes                   28672  0
video                  40960  0

rfkill list

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

iwlist chan

lo        no frequency information.

wlo1      14 channels in total; available frequencies :
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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.437 GHz (Channel 6)

eno1      no frequency information.

sudo iwlist scan lo        Interface doesn't support scanning.
 
 
 wlo1      Scan completed :
           Cell 01 - Address: 50:6A:03:90:C5:83
                     Channel:1
                     Frequency:2.412 GHz (Channel 1)
                     Quality=69/70  Signal level=-41 dBm   
                     Encryption key: on
                     ESSID:"NETGEAR97"
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                               24 Mb/s; 36 Mb/s; 54 Mb/s
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                     Mode:Master
                     Extra:tsf=000003d525ef56c4
                     Extra: Last beacon: 4ms ago
                     IE: Unknown: 00094E4554474541523937
                     IE: Unknown: 010882848B962430486C
                     IE: Unknown: 030101
                     IE: Unknown: 2A0100
                     IE: Unknown: 2F0100
                     IE: IEEE 802.11i/WPA2 Version 1
                         Group Cipher : CCMP
                         Pairwise Ciphers (1) : CCMP
                         Authentication Suites (1) : PSK
                     IE: Unknown: 32040C121860
                     IE: Unknown: 0B050100330000
                     IE: Unknown: 2D1ABC191BFFFF000000000000000000000000000000000000000000
                     IE: Unknown: 3D1601080000000000000000000000000000000000000000
                     IE: Unknown: 4A0E14000A002C01C800140005001900
                     IE: Unknown: 7F080500080000000040
                     IE: Unknown: DD800050F204104A0001101044000102103B00010310470010794F8E8A062D407FB6E8324283F202FB102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F2040001101100094E6574676561724150100800022008103C0001011049000600372A000120
                     IE: Unknown: DD090010180201000C0000
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                     IE: Unknown: 46057208010000
           Cell 02 - Address: DC:FE:07:E8:67:38
                     Channel:1
                     Frequency:2.412 GHz (Channel 1)
                     Quality=70/70  Signal level=-33 dBm   
                     Encryption key: on
                     ESSID:"HOME-7837-2.4"
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                               9 Mb/s; 12 Mb/s; 18 Mb/s
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                     Mode:Master
                     Extra:tsf=000001f8de7d51b7
                     Extra: Last beacon: 4ms ago
                     IE: Unknown: 000D484F4D452D373833372D322E34
                     IE: Unknown: 010882848B968C129824
                     IE: Unknown: 030101
                     IE: Unknown: 0706555320010B1E
                     IE: Unknown: 2A0100
                     IE: Unknown: 3204B048606C
                     IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                     IE: Unknown: 3D1601080000000000000000000000000000000000000000
                     IE: Unknown: 4A0E14000A002C01C800140005001900
                     IE: Unknown: 7F080100000000000040
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                     IE: Unknown: DD0900037F01010000FF7F
                     IE: IEEE 802.11i/WPA2 Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: WPA Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: Unknown: DD8D0050F204104A0001101044000102103B00010310470010F98F963B896C5C38B05677CF1FA3881110210013436973636F2053797374656D732C20496E632E10230007445043333934311024000744504333393431104200093030303030303030311054000800060050F20400011011000744504333393431100800020000103C0001011049000600372A000120
           Cell 03 - Address: 10:05:B1:42:EE:C0
                     Channel:6
                     Frequency:2.437 GHz (Channel 6)
                     Quality=54/70  Signal level=-56 dBm   
                     Encryption key: on
                     ESSID:"ATT5q9W7k3"
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                               24 Mb/s; 36 Mb/s; 54 Mb/s
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                     Mode:Master
                     Extra:tsf=000000624a3e769c
                     Extra: Last beacon: 4ms ago
                     IE: Unknown: 000A41545435713957376B33
                     IE: Unknown: 010882848B962430486C
                     IE: Unknown: 030106
                     IE: Unknown: 2A0100
                     IE: Unknown: 2F0100
                     IE: IEEE 802.11i/WPA2 Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: Unknown: 32040C121860
                     IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                     IE: Unknown: 3D1606081500000000000000000000000000000000000000
                     IE: Unknown: DD090010180208F02C0000
                     IE: WPA Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
           Cell 04 - Address: F8:18:97:11:74:FA
                     Channel:5
                     Frequency:2.432 GHz (Channel 5)
                     Quality=31/70  Signal level=-79 dBm   
                     Encryption key: on
                     ESSID:"ATT2uwP8wZ"
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                               24 Mb/s; 36 Mb/s; 54 Mb/s
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                     Mode:Master
                     Extra:tsf=0000000024d230a1
                     Extra: Last beacon: 4ms ago
                     IE: Unknown: 000A4154543275775038775A
                     IE: Unknown: 010882848B962430486C
                     IE: Unknown: 030105
                     IE: Unknown: 0706555320010B1E
                     IE: Unknown: 2A0100
                     IE: Unknown: 2F0100
                     IE: IEEE 802.11i/WPA2 Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: Unknown: 32040C121860
                     IE: Unknown: 0B0500002E0000
                     IE: Unknown: 2D1A1C181FFFFF000000000000000000000000000000000000000000
                     IE: Unknown: 3D1605000000000000000000000000000000000000000000
                     IE: Unknown: 7F03000008
                     IE: Unknown: DD7F0050F204104A0001101044000102103B0001031047001000000000000000000000000000000000102100045061636510230004506163651024000631323334353610420004313233341054000800060050F204000110110011506163652041636365737320506F696E7410080002200C103C0001011049000600372A000120
                     IE: Unknown: DD090010180200000C0000
                     IE: WPA Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
           Cell 05 - Address: 3C:EA:4F:BA:C6:41
                     Channel:7
                     Frequency:2.442 GHz (Channel 7)
                     Quality=53/70  Signal level=-57 dBm   
                     Encryption key: on
                     ESSID:"Mardele"
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                               11 Mb/s; 12 Mb/s; 18 Mb/s
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                     Mode:Master
                     Extra:tsf=0000014fc3eb2e8b
                     Extra: Last beacon: 4ms ago
                     IE: Unknown: 00074D617264656C65
                     IE: Unknown: 010882848B0C12961824
                     IE: Unknown: 030107
                     IE: Unknown: 0706555320010B1B
                     IE: WPA Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (1) : TKIP
                         Authentication Suites (1) : PSK
                     IE: Unknown: 2A0100
                     IE: Unknown: 32043048606C
           Cell 06 - Address: 34:23:87:44:3C:34
                     Channel:6
                     Frequency:2.437 GHz (Channel 6)
                     Quality=33/70  Signal level=-77 dBm   
                     Encryption key:off
                     ESSID:"HP-Print-34-LaserJet 1102"
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                               36 Mb/s; 48 Mb/s; 54 Mb/s
                     Mode:Master
                     Extra:tsf=00000049a71f788b
                     Extra: Last beacon: 612ms ago
                     IE: Unknown: 001948502D5072696E742D33342D4C617365724A65742031313032
                     IE: Unknown: 01088C1218243048606C
                     IE: Unknown: 030106
                     IE: Unknown: 2A0100
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
           Cell 07 - Address: 74:9D:OC:E4:FE:39
                     Channel:9
                     Frequency:2.452 GHz (Channel 9)
                     Quality=61/70  Signal level=-49 dBm   
                     Encryption key:on
                     ESSID:"2WIRE303"
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                               11 Mb/s; 12 Mb/s; 18 Mb/s
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                     Mode:Master
                     Extra:tsf=0000018fb962e2ef
                     Extra: Last beacon: 4ms ago
                     IE: Unknown: 00083257495245333033
                     IE: Unknown: 010882848B0C12961824
                     IE: Unknown: 030109
                     IE: Unknown: 0706555320010B1B
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
           Cell 08 - Address: C0:3F:0E:19:88:0C
                     Channel:11
                     Frequency:2.462 GHz (Channel 11)
                     Quality=37/70  Signal level=-73 dBm   
                     Encryption key: on
                     ESSID:"leyva-network"
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                               24 Mb/s; 36 Mb/s; 54 Mb/s
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                     Mode:Master
                     Extra:tsf=000001b69158214e
                     Extra: Last beacon: 4ms ago
                     IE: Unknown: 000D6C657976612D6E6574776F726B
                     IE: Unknown: 010882840B162430486C
                     IE: Unknown: 03010B
                     IE: Unknown: 2A0106
                     IE: Unknown: 2F0106
                     IE: IEEE 802.11i/WPA2 Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: Unknown: 32040C121860
                     IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010BE5379A683286CCBC39CD11A7A2C85B71021000D4E4554474541522C20496E632E10230009574752363134763130102400095747523631347631301042000538333235381054000800060050F204000110110009574752363134763130100800020084
                     IE: Unknown: DD090010180202F0050000
                     IE: WPA Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
           Cell 09 - Address: CC:35:40:91:0D:EF
                     Channel:11
                     Frequency:2.462 GHz (Channel 11)
                     Quality=45/70  Signal level=-65 dBm   
                     Encryption key: on
                     ESSID:"Fart"
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                               24 Mb/s; 36 Mb/s; 54 Mb/s
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                     Mode:Master
                     Extra:tsf=000000aae58d7671
                     Extra: Last beacon: 4ms ago
                     IE: Unknown: 000446617274
                     IE: Unknown: 010882848B9624B0486C
                     IE: Unknown: 03010B
                     IE: Unknown: 2A0102
                     IE: Unknown: 2F0102
                     IE: IEEE 802.11i/WPA2 Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: Unknown: 32048C129860
                     IE: Unknown: 2D1ABD181BFFFFFF0000000000000000000000000000000000000000
                     IE: Unknown: 3D160B001700000000000000000000000000000000000000
                     IE: Unknown: DD8C0050F204104A0001101044000102103B000103104700105CBD5123FFD57353B35868AE86D6EA291021000B546563686E69636F6C6F721023000B546563686E69636F6C6F721024000631323334353610420007303030303030311054000800060050F20400011011000D546563686E69636F6C6F724150100800022008103C0001011049000600372A000120
                     IE: Unknown: DD090010180201001C0000
                     IE: WPA Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
           Cell 10 - Address: CE:35:40:91:0D:E0
                     Channel:11
                     Frequency:2.462 GHz (Channel 11)
                     Quality=43/70  Signal level=-67 dBm   
                     Encryption key: on
                     ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                               24 Mb/s; 36 Mb/s; 54 Mb/s
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                     Mode:Master
                     Extra:tsf=000000aae58dfa20
                     Extra: Last beacon: 324ms ago
                     IE: Unknown: 000C000000000000000000000000
                     IE: Unknown: 010882848B9624B0486C
                     IE: Unknown: 03010B
                     IE: Unknown: 050400010000
                     IE: Unknown: 2A0102
                     IE: Unknown: 2F0102
                     IE: IEEE 802.11i/WPA2 Version 1
                         Group Cipher : CCMP
                         Pairwise Ciphers (1) : CCMP
                         Authentication Suites (1) : PSK
                     IE: Unknown: 32048C129860
                     IE: Unknown: 2D1ABD181BFFFFFF0000000000000000000000000000000000000000
                     IE: Unknown: 3D160B001700000000000000000000000000000000000000
                     IE: Unknown: DD090010180200001C0000
                     IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
           Cell 11 - Address: CE:35:40:91:0D:E1
                     Channel:11
                     Frequency:2.462 GHz (Channel 11)
                     Quality=45/70  Signal level=-65 dBm   
                     Encryption key: off
                     ESSID:"xfinitywifi"
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                               24 Mb/s; 36 Mb/s; 54 Mb/s
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                     Mode:Master
                     Extra:tsf=000000aae58d6f0e
                     Extra: Last beacon: 4ms ago
                     IE: Unknown: 000B7866696E69747977696669
                     IE: Unknown: 010882848B9624B0486C
                     IE: Unknown: 03010B
                     IE: Unknown: 2A0102
                     IE: Unknown: 2F0102
                     IE: Unknown: 32048C129860
                     IE: Unknown: 2D1ABD181BFFFFFF0000000000000000000000000000000000000000
                     IE: Unknown: 3D160B001700000000000000000000000000000000000000
                     IE: Unknown: DD090010180201001C0000
                     IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
           Cell 12 - Address: FA:8F:CA:93:97:09
                     Channel:11
                     Frequency:2.462 GHz (Channel 11)
                     Quality=28/70  Signal level=-82 dBm   
                     Encryption key :off
                     ESSID:""
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                               9 Mb/s; 12 Mb/s; 18 Mb/s
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                     Mode:Master
                     Extra:tsf=000001b6914f4f0b
                     Extra: Last beacon: 260ms ago
                     IE: Unknown: 0000
                     IE: Unknown: 010882848B960C121824
                     IE: Unknown: 03010B
                     IE: Unknown: 05050102000000
                     IE: Unknown: 2A0102
                     IE: Unknown: 2D1A2C0103FF000000000000000000000000000000000008E0E10900
                     IE: Unknown: 32043048606C
                     IE: Unknown: 3D160B000100000000000000000000000000000000000000
                     IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
           Cell 13 - Address: 40:E2:30:7E:F3:6F
                     Channel:2
                     Frequency:2.417 GHz (Channel 2)
                     Quality=39/70  Signal level=-71 dBm   
                     Encryption key:off
                     ESSID:"WM7ef36f"
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                               9 Mb/s; 12 Mb/s; 18 Mb/s
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                     Mode:Master
                     Extra:tsf=000003d52b1b0917
                     Extra: Last beacon: 4ms ago
                     IE: Unknown: 0008574D376566333666
                     IE: Unknown: 010882848B960C121824
                     IE: Unknown: 030102
                     IE: Unknown: 2A0100
                     IE: Unknown: 32043048606C
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
           Cell 14 - Address: D8:97:BA:5A:37:48
                     Channel:1
                     Frequency:2.412 GHz (Channel 1)
                     Quality=70/70  Signal level=-37 dBm   
                     Encryption key: on
                     ESSID:"HOME-19DA-2.4"
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                               9 Mb/s; 12 Mb/s; 18 Mb/s
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                     Mode:Master
                     Extra:tsf=000000135eb69701
                     Extra: Last beacon: 4ms ago
                     IE: Unknown: 000D484F4D452D313944412D322E34
                     IE: Unknown: 010882848B968C129824
                     IE: Unknown: 030101
                     IE: Unknown: 0706555320010B1E
                     IE: Unknown: 2A0100
                     IE: Unknown: 3204B048606C
                     IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                     IE: Unknown: 3D1601080400000000000000000000000000000000000000
                     IE: Unknown: 4A0E14000A002C01C800140005001900
                     IE: Unknown: 7F080100000000000040
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                     IE: Unknown: DD0900037F01010000FF7F
                     IE: IEEE 802.11i/WPA2 Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: WPA Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: Unknown: DD8D0050F204104A0001101044000102103B00010310470010BC293F78D0B85F478C92EFE65168150010210013436973636F2053797374656D732C20496E632E10230007445043333933391024000744504333393339104200093030303030303030311054000800060050F2040001101100074450433339333910080002210C103C0001011049000600372A000120
           Cell 15 - Address: D8:97:BA:5A:37:4A
                     Channel:1
                     Frequency:2.412 GHz (Channel 1)
                     Quality=70/70  Signal level=-35 dBm   
                     Encryption key: off
                     ESSID:"xfinitywifi"
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                               9 Mb/s; 12 Mb/s; 18 Mb/s
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                     Mode:Master
                     Extra:tsf=000000135eb76ec7
                     Extra: Last beacon: 4ms ago
                     IE: Unknown: 000B7866696E69747977696669
                     IE: Unknown: 010882848B968C129824
                     IE: Unknown: 030101
                     IE: Unknown: 0706555320010B1E
                     IE: Unknown: 2A0100
                     IE: Unknown: 3204B048606C
                     IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                     IE: Unknown: 3D1601080400000000000000000000000000000000000000
                     IE: Unknown: 4A0E14000A002C01C800140005001900
                     IE: Unknown: 7F080100000000000040
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                     IE: Unknown: DD0900037F01010000FF7F
           Cell 16 - Address: 8C:7F:3B:43:A3:80
                     Channel:1
                     Frequency:2.412 GHz (Channel 1)
                     Quality=70/70  Signal level=-34 dBm   
                     Encryption key: on
                     ESSID:"Gallego"
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                               24 Mb/s; 36 Mb/s; 54 Mb/s
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                     Mode:Master
                     Extra:tsf=0000035b6b757172
                     Extra: Last beacon: 4ms ago
                     IE: Unknown: 000747616C6C65676F
                     IE: Unknown: 010882848B962430486C
                     IE: Unknown: 030101
                     IE: Unknown: 2A0104
                     IE: Unknown: 2F0104
                     IE: IEEE 802.11i/WPA2 Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: Unknown: 32040C121860
                     IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                     IE: Unknown: 3D1601080400000000000000000000000000000000000000
                     IE: Unknown: DD090010180204F02C0000
                     IE: WPA Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
           Cell 17 - Address: DC:FE:07:E8:67:39
                     Channel:1
                     Frequency:2.412 GHz (Channel 1)
                     Quality=70/70  Signal level=-31 dBm   
                     Encryption key: on
                     ESSID:""
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                               9 Mb/s; 12 Mb/s; 18 Mb/s
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                     Mode:Master
                     Extra:tsf=000001f8de7c0180
                     Extra: Last beacon: 896ms ago
                     IE: Unknown: 0000
                     IE: Unknown: 010882848B968C129824
                     IE: Unknown: 030101
                     IE: Unknown: 050400010000
                     IE: Unknown: 0706555320010B1E
                     IE: Unknown: 2A0100
                     IE: Unknown: 3204B048606C
                     IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                     IE: Unknown: 3D1601080000000000000000000000000000000000000000
                     IE: Unknown: 4A0E14000A002C01C800140005001900
                     IE: Unknown: 7F080100000000000040
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                     IE: Unknown: DD0900037F01010000FF7F
                     IE: IEEE 802.11i/WPA2 Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: WPA Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
           Cell 18 - Address: D8:97:BA:5A:37:49
                     Channel:1
                     Frequency:2.412 GHz (Channel 1)
                     Quality=22/70  Signal level=-88 dBm   
                     Encryption key: on
                     ESSID:""
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                               9 Mb/s; 12 Mb/s; 18 Mb/s
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                     Mode:Master
                     Extra:tsf=000000135eb74180
                     Extra: Last beacon: 880ms ago
                     IE: Unknown: 0000
                     IE: Unknown: 010882848B968C129824
                     IE: Unknown: 030101
                     IE: Unknown: 050400010000
                     IE: Unknown: 0706555320010B1E
                     IE: Unknown: 2A0100
                     IE: Unknown: 3204B048606C
                     IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                     IE: Unknown: 3D1601080400000000000000000000000000000000000000
                     IE: Unknown: 4A0E14000A002C01C800140005001900
                     IE: Unknown: 7F080100000000000040
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                     IE: Unknown: DD0900037F01010000FF7F
                     IE: IEEE 802.11i/WPA2 Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: WPA Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
           Cell 19 - Address: 60:C3:97:96:80:41
                     Channel:9
                     Frequency:2.452 GHz (Channel 9)
                     Quality=27/70  Signal level=-83 dBm   
                     Encryption key: on
                     ESSID:"2WIRE762"
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                               9 Mb/s; 12 Mb/s; 18 Mb/s
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                     Mode:Master
                     Extra:tsf=000003d526047181
                     Extra: Last beacon: 476ms ago
                     IE: Unknown: 00083257495245373632
                     IE: Unknown: 010882848B960C121824
                     IE: Unknown: 030109
                     IE: Unknown: 050400010000
                     IE: Unknown: 0706555320010B1B
                     IE: Unknown: 2A0102
                     IE: IEEE 802.11i/WPA2 Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: WPA Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: Unknown: 32043048606C
 
 
 eno1      Interface doesn't support scanning.
```

---

### Post by wildmanne39 on 2016-07-01
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by wildmanne39 on 2016-07-01
Please post the commands that made the icon disappear from the top panel and click on the wireless script in my signature and post the file created here using code tags.
Thanks

---

