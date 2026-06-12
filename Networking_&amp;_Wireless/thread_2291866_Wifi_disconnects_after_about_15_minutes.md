---
title: "Wifi disconnects after about 15 minutes"
date: 2015-08-23
forum: Networking &amp; Wireless
---

### Post by barad2 on 2015-08-23
Hi all, first of all i am completely new to Linux based OS , i bought a new laptop Lenovo Ideapad G50-70 59439302 
and installed Ubuntu 14.04.3 LTS on it.
everything works fine except the WiFi 
it connects to my WiFi at first but after about 15-20 minutes it disconnects , if i reboot then its connected again for 15 minutes
and of course i cant reboot my laptop every 15 mins just to have WiFi again.

is this problem known?
is there a solution?

Notes: 

internet works with Ethernet cable plugged in
Additional drivers show "no additional drivers available" - with or without Ethernet cable plugged
Kernel version is 3.19 

thanks in advance,
barad

---

### Post by praseodym on 2015-08-23
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lspci -nnk
lsusb
lsmod
ifconfig -a
iwconfig
iwlist chan
sudo iwlist scan
```Does LAN work?

---

### Post by barad2 on 2015-08-23
the WIFI works on my phone if thats what you mean by LAN works

```
here are the outputs:
:~$ uname -a
Linux barad-Lenovo 3.19.0-26-generic #28~14.04.1-Ubuntu SMP Wed Aug 12 14:09:17 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 0b)
    Subsystem: Lenovo Device [17aa:3978]
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b)
    Subsystem: Lenovo Device [17aa:380c]
    Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 0b)
    Subsystem: Lenovo Device [17aa:3978]
    Kernel driver in use: snd_hda_intel
00:14.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB xHCI HC [8086:9c31] (rev 04)
    Subsystem: Lenovo Device [17aa:3978]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation Lynx Point-LP HECI #0 [8086:9c3a] (rev 04)
    Subsystem: Lenovo Device [17aa:3978]
    Kernel driver in use: mei_me
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
    Subsystem: Lenovo Device [17aa:3978]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 3 [8086:9c14] (rev e4)
    Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 4 [8086:9c16] (rev e4)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB EHCI #1 [8086:9c26] (rev 04)
    Subsystem: Lenovo Device [17aa:3978]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation Lynx Point-LP LPC Controller [8086:9c43] (rev 04)
    Subsystem: Lenovo Device [17aa:3978]
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
    Subsystem: Lenovo Device [17aa:3978]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Lynx Point-LP SMBus Controller [8086:9c22] (rev 04)
    Subsystem: Lenovo Device [17aa:3978]
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380a]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be

~$ lsusb
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 5986:0652 Acer, Inc 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub





~$ lsmod
Module                  Size  Used by
ctr                    16384  1 
ccm                    20480  1 
bnep                   20480  2 
rfcomm                 69632  8 
rtsx_usb_ms            20480  0 
memstick               20480  1 rtsx_usb_ms
arc4                   16384  2 
uvcvideo               90112  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         53248  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
snd_hda_codec_hdmi     53248  1 
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
coretemp               16384  0 
rtl8723be              90112  0 
btcoexist              53248  1 rtl8723be
kvm                   479232  0 
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                73728  2 rtl_pci,rtl8723be
mac80211              708608  3 rtl_pci,rtlwifi,rtl8723be
snd_soc_rt5640         94208  0 
joydev                 20480  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
serio_raw              16384  0 
cfg80211              524288  2 mac80211,rtlwifi
btusb                  40960  0 
snd_soc_core          196608  1 snd_soc_rt5640
bluetooth             491520  22 bnep,btusb,rfcomm
snd_compress           20480  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
lpc_ich                24576  0 
shpchp                 40960  0 
mei_me                 20480  0 
snd_hda_codec_conexant    24576  1 
mei                    90112  1 mei_me
snd_hda_codec_generic    69632  1 snd_hda_codec_conexant
ideapad_laptop         20480  0 
sparse_keymap          16384  1 ideapad_laptop
snd_hda_intel          32768  5 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
8250_fintek            16384  0 
snd_hwdep              20480  1 snd_hda_codec
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_soc_sst_acpi       16384  0 
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
dw_dmac                16384  0 
i2c_hid                20480  0 
dw_dmac_core           24576  1 dw_dmac
8250_dw                16384  0 
snd_timer              32768  2 snd_pcm,snd_seq
i2c_designware_platform    16384  0 
i2c_designware_core    16384  1 i2c_designware_platform
snd                    86016  23 snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
spi_pxa2xx_platform    24576  0 
soundcore              16384  2 snd,snd_hda_codec
mac_hid                16384  0 
soc_button_array       16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
dm_crypt               24576  1 
rtsx_usb_sdmmc         28672  0 
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  3 i2c_hid,hid_generic,usbhid
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
ghash_clmulni_intel    16384  0 
i915                 1048576  5 
aesni_intel           172032  5 
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  4 ghash_clmulni_intel,aesni_intel,ablk_helper
psmouse               114688  0 
i2c_algo_bit           16384  1 i915
drm_kms_helper        126976  1 i915
ahci                   36864  2 
libahci                32768  1 ahci
r8169                  81920  0 
drm                   344064  6 i915,drm_kms_helper
mii                    16384  1 r8169
video                  20480  1 i915
sdhci_acpi             16384  0 
sdhci                  45056  1 sdhci_acpi

~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 68:f7:28:4c:a4:ed  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34661 (34.6 KB)  TX bytes:34661 (34.6 KB)


wlan0     Link encap:Ethernet  HWaddr 2c:33:7a:0d:25:19  
          inet addr:192.168.1.19  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e33:7aff:fe0d:2519/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2721 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2473 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1911537 (1.9 MB)  TX bytes:597832 (597.8 KB)


~$ iwconfig
eth0      no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"izy pizy"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C0:AC:54:F7:A9:1B   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr off
          Power Management off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0


lo        no wireless extensions.



~$ iwlist chan
eth0      no frequency information.


wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)


lo        no frequency information.



~$ sudo iwlist scan
[sudo] password for : 
eth0      Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: C0:AC:54:F7:A9:1B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key :on
                    ESSID:"izy pizy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000093699462c9
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 0008697A792070697A79
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180205F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: C0:AC:54:F6:F4:E5
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"ELENA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002eb3c6219b
                    Extra: Last beacon: 588ms ago
                    IE: Unknown: 0005454C454E41
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180204F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: C4:04:15:52:31:9D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key : on
                    ESSID:"tomer"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009369bfd1cb
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 0005746F6D6572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B050200150000
                    IE: Unknown: 2D1ABC1817FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001500000000000000000000000000000000000000
                    IE: Unknown: 7F03000008
                    IE: Unknown: DD850050F204104A0001101044000102103B0001031047001010ADE44DFD946E555D75EA3FB18727491021000D4E4554474541522C20496E632E102300085645474E32363130102400085645474E3236313010420004333730301054000800060050F2040001101100085645474E3236313010080002200C103C0001031049000600372A000120
                    IE: Unknown: DD090010180202000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: F4:EC:38:B0:4D:3E
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key : on
                    ESSID:"tali"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001177ed80
                    Extra: Last beacon: 2520ms ago
                    IE: Unknown: 000474616C69
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34040D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16040D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 05 - Address: 00:27:19: o2:02:3A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key: on
                    ESSID:"kobiap"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002b94ef181
                    Extra: Last beacon: 2548ms ago
                    IE: Unknown: 00066B6F62696170
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000002719D2023A022719D2023A64002C010808
          Cell 06 - Address: D0: o4:12:65:74:02
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key: on
                    ESSID:"Frida"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000093671a5708
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 00054672696461
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 0706455520010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B0501002F0000
                    IE: Unknown: 2D1A3C1817FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 7F03000008
                    IE: Unknown: DD090010180201000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
          Cell 07 - Address: E0:CE:C3:EF:DD:3F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key: on
                    ESSID:"HOTFiber-16B8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005e085e9198
                    Extra: Last beacon: 2116ms ago
                    IE: Unknown: 000D484F5446696265722D31364238
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B050200100000
                    IE: Unknown: 2D1ABC191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 7F080400080000000040
                    IE: Unknown: DD090010180202000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46057208010000
          Cell 08 - Address: 00:78:9E:FA:63:6B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key: on
                    ESSID:"Eden1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001793cc1191
                    Extra: Last beacon: 1588ms ago
                    IE: Unknown: 00054564656E31
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180205F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: 20:0C:C8:1D:01:80
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key: on
                    ESSID:"YosiSalme_2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009369b2108a
                    Extra: Last beacon: 1408ms ago
                    IE: Unknown: 000D596F736953616C6D655F322E34
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B050200720000
                    IE: Unknown: 2D1ABC1817FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001500000000000000000000000000000000000000
                    IE: Unknown: 7F03000008
                    IE: Unknown: DD090010180202000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 10 - Address: A0:21:B7:82:74:7E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key: on
                    ESSID:"sigiattali"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000936b2310c1
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 000A73696769617474616C69
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD920050F204104A00011010440001011041000100103B0001031047001011728AF768C2D13C14D83AF6E1335E5B1021000D4E4554474541522C20496E632E1023000E44474E32323030763242455A45511024000E44474E32323030763242455A455110420004323230301054000800060050F20400011011000E44474E32323030763242455A4551100800020084103C000101
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


lo        Interface doesn't support scanning.
```

---

### Post by praseodym on 2015-08-23
Please run

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot

---

### Post by barad2 on 2015-08-23
ok , just ran that, it showed:

options rtl8723be swenc=1 fwlps=0 ips=0

reboot now and gona wait and see if connection lasts :)

---

### Post by barad2 on 2015-08-23
over 40 minutes and working...hope it stays that way

thanks a lot  :D

---

