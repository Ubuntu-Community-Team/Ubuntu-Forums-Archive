---
title: "Qualcomm Atheros and Netgear Wifi Failures"
date: 2014-11-22
forum: Networking &amp; Wireless
---

### Post by vrcdng on 2014-11-22
Hi, 

A few basics: I have am HP Pavilion Touchsmart laptop which runs windows 8 and ubuntu 14.04 LTS

I installed Ubuntu 14.04 LTS from a burned iso onto a 16GB USB stick and then proceeded to install some software onto the stick. Everything seemed to work fine. The wifi was working fine on Ubuntu and also on my Windows 8. I installed a few video editing programs like Kedenlive, Blender, Openshot, I also installed Cairo Dock and finally some Compiz stuff. I can't quite remember how my wifi stopped working, but I seem to remember a dialog that asked if I wanted to make deep changes to my system. I think it was during using compiz, but I was rushing around and not checking to carefully unfortunately. Anyway, I soon noticed that my wifi started to pop up the " disconnected you are offline now" message. And I was never able to get a wifi connection again no matter what I tried.

This was using Qualcomm Atheros AR9485/HB125 internal to my laptop wifi adapter. When I logged into Windows 8 later, it too would no longer connect to the wifi. I am able to see the routers around me but when I try to connect to them with the correct password it never can do so. I tried an external USB Netgear WNA3100M wifi adapter and Ubuntu was able to recognize it and let me connect back to the internet, but the Qualcomm one remains useless. Also in Windows 8 neither of the adapters will work. The Qualcomm will only see the routers around it, but I cannot even fully install the Netgear one. I tried hard to get the netgear to work in Windows 8 and I got to the point where it said in Device Manager that the driver had installed correctly, but in reality it had not. The blue light on the netgear never lit up like it did using Ubuntu, and the netgear could not see the routers around it. 

I have tried installing, uninstalling the latest drivers in windows that I could find for both the qualcomm and netgear. I tried installing in Safe mode etc. Still no progress.  I have not tried uninstalling and reinstalling the Qualcomm internal wifi from within Ubuntu because I do not know how to do that or if it will even help. I am a semi-intermediate user of Linux so I can do a little terminal stuff if anyone can suggest anything. I also took out the qualcomm board off the main motherboard to see if I could get the netgear to run in Windows 8, but this did not help, so I put it back.

I am pretty stumped as to what the problem is. So just to recap, the qualcomm sees routers in ubuntu and windows 8, but cannot connect to the internet on both OS's. The netgear is blind to the routers in windows 8 and cannot connect at all, but works fine in ubuntu. I am wondering if somehow my motherboard has been damaged in someway, or if the ROM inside the wifi chips has become corrupted. Would appreciate any tips on things to try, starting from the easiest to more arduous. Would like to find what the cause of the problem is if possible.

Thanks

Al

---

### Post by praseodym on 2014-11-23
Hi,

please show the terminal outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
```

---

### Post by vrcdng on 2014-11-23
Hi praseodym,

Thanks for replying.

I have included all the info you requested I think below:





```



lspci -nnk | grep -iA2 net



01:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Hewlett-Packard Company AR9485/HB125 802.11bgn 1×1 Wi-Fi Adapter [103c:1838]
    Kernel driver in use: ath9k
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:18fc]
    Kernel driver in use: r8169


-------------------------------------




lsusb


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0eef:a107 D-WAV Scientific Co., Ltd 
Bus 001 Device 003: ID 0846:9021 NetGear, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0781:5581 SanDisk Corp. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04f2:b35f Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---------------------


lsmod



Module                  Size  Used by
ctr                    13049  1 
ccm                    17773  1 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391196  10 bnep,rfcomm
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_idt      54645  1 
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
arc4                   12608  4 
uvcvideo               80885  0 
rtl8192cu              67723  0 
ath9k                 164164  0 
snd_hda_intel          52355  3 
rtl_usb                18448  1 rtl8192cu
ath9k_common           13551  1 ath9k
videobuf2_vmalloc      13216  1 uvcvideo
hid_multitouch         17407  0 
rtlwifi                63475  2 rtl_usb,rtl8192cu
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
videobuf2_memops       13362  1 videobuf2_vmalloc
ath9k_hw              453856  2 ath9k_common,ath9k
intel_rapl             18773  0 
videobuf2_core         40664  1 uvcvideo
rtl8192c_common        53172  1 rtl8192cu
snd_hwdep              13602  1 snd_hda_codec
videodev              134688  2 uvcvideo,videobuf2_core
x86_pkg_temp_thermal    14205  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
intel_powerclamp       14705  0 
mac80211              630653  4 ath9k,rtl_usb,rtlwifi,rtl8192cu
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
coretemp               13435  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
i915                  783805  3 
snd_rawmidi            30144  1 snd_seq_midi
kvm                   451511  0 
cfg80211              484040  4 ath,ath9k,mac80211,rtlwifi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
crct10dif_pclmul       14289  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
snd_timer              29482  2 snd_pcm,snd_seq
drm_kms_helper         53081  1 i915
drm                   303102  4 i915,drm_kms_helper
snd                    69238  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
cryptd                 20359  1 ghash_clmulni_intel
soundcore              12680  1 snd
joydev                 17381  0 
i2c_algo_bit           13413  1 i915
serio_raw              13462  0 
mei_me                 18627  0 
hp_accel               26012  0 
mei                    82276  1 mei_me
lis3lv02d              20156  1 hp_accel
input_polldev          13896  1 lis3lv02d
video                  19476  1 i915
wmi                    19177  1 hp_wmi
lpc_ich                21080  0 
hp_wireless            12637  0 
mac_hid                13205  0 
binfmt_misc            17468  1 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  3 hid_multitouch,hid_generic,usbhid
usb_storage            62209  2 
psmouse               106678  0 
ahci                   25819  0 
libahci                32560  1 ahci
r8169                  67581  0 
mii                    13934  1 r8169



------------------

iwconfig



wlan1     IEEE 802.11bgn  ESSID:"HouseWifi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 34:8A:AE:24:CA:24   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=12/70  Signal level=-98 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off




--------------------------

rfkill list




0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no




------------------------------



iwlist chan



wlan1     11 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

eth0      no frequency information.

lo        no frequency information.

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




--------------------------------------------



sudo iwlist scan





wlan1     Scan completed :
          Cell 01 - Address: 34:8A:AE:24:CA:24
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"HouseWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e0a0957ad6
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 001356696C6C612D6C65732D76696F6C6574746573
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 331AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 34160B080400000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD9E0050F204104A0001101044000102103B000103104700103334384141454234834132340034384110210008536167656D636F6D10230016536167656D636F6D46617374333936355F4C42322E381024000C53475F4C42335F312E322E311042000F4C4B313430383144503431313032361054000800060050F2040001101100094C697665626F782033100800020006103C0001011049000600372A000120
          Cell 02 - Address: 20:0C:C8:43:FA:C9
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR31"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001fcd344127
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 00094E4554474541523331
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD0103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AD0103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: DD1A00904C3401080400000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD900050F204104A0001101044000102103B00010310470010427974EECF6C52788C94000000000000102100046E6F6E65102300046E6F6E65102400046E6F6E651042001253657269616C204E756D62657220486572651054000800060050F204000110110016574E5232303030763428576972656C65737320415029100800022008103C0001011049000600372A000120
          Cell 03 - Address: 14:0C:76:A6:1F:21
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ab01fb015f
                    Extra: Last beacon: 1764ms ago
                    IE: Unknown: 000F46726565576966695F736563757265
                    IE: Unknown: 010882848B962C0C1218
                    IE: Unknown: 030102
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0104
                    IE: Unknown: 3205243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1AEC0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D1602000400000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 04 - Address: 2C:39:96:23:7A:3E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Livebox1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000faf79848a4
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 000C4C697665626F782D37413345
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 331AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 34160B080400000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD9E0050F204104A0001101044000102103B000103104700103243333939364233B74133450043333910210008536167656D636F6D10230016536167656D636F6D46617374333936355F4C42322E381024000C53475F4C42335F312E322E311042000F4E51313331303030343434393832361054000800060050F2040001101100094C697665626F782033100800020006103C0001011049000600372A000120

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 20:0C:C8:43:FA:C9
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR31"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001fcd4f88d5
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 00094E4554474541523331
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD0103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AD0103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: DD1A00904C3401080400000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD900050F204104A0001101044000102103B00010310470010427974EECF6C52788C94000000000000102100046E6F6E65102300046E6F6E65102400046E6F6E651042001253657269616C204E756D62657220486572651054000800060050F204000110110016574E5232303030763428576972656C65737320415029100800022008103C0001011049000600372A000120
          Cell 02 - Address: 2C:39:96:23:7A:3E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Livebox1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000faf7a70d54
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000C4C697665626F782D37413345
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 331AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 34160B080400000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD9E0050F204104A0001101044000102103B000103104700103243333939364233B74133450043333910210008536167656D636F6D10230016536167656D636F6D46617374333936355F4C42322E381024000C53475F4C42335F312E322E311042000F4E51313331303030343434393832361054000800060050F2040001101100094C697665626F782033100800020006103C0001011049000600372A000120
          Cell 03 - Address: 00:00:00:00:00:00
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"HouseWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e0a09feff2
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 001356696C6C612D6C65732D76696F6C6574746573
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 331AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 34160B080400000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD9E0050F204104A0001101044000102103B000103104700103334384141454234834132340034384110210008536167656D636F6D10230016536167656D636F6D46617374333936355F4C42322E381024000C53475F4C42335F312E322E311042000F4C4B313430383144503431313032361054000800060050F2040001101100094C697665626F782033100800020006103C0001011049000600372A000120
          Cell 04 - Address: 34:8A:AE:24:CA:24
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"HouseWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e0a0a06180
                    Extra: Last beacon: 224ms ago
                    IE: Unknown: 001356696C6C612D6C65732D76696F6C6574746573
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050401030040
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD1D0050F204104A0001101044000102103C0001011049000600372A000120
          Cell 05 - Address: 00:1F:9F:BE:24:73
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Thomson11"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c72386cc90
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000D54686F6D736F6E323431423639
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020000040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 06 - Address: DC:9F:DB:0E:B8:70
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Mesh1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000036f912bd180
                    Extra: Last beacon: 372ms ago
                    IE: Unknown: 00074D657368504441
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 050400010001
                    IE: Unknown: 2A0100
                    IE: Unknown: DD26000C42000000011E000000001F660902FF0F5041350000000000000000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409080C00000000000000000000000000000000000000
                    IE: Unknown: 3D1609080C00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD0E00156D000000010212E002021200











```

---

### Post by praseodym on 2014-11-23
For the internal card: Deactivate the hardware encryption:

```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
For the stick: Change the driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by vrcdng on 2014-11-23
Hi again praseodym

I put each line in one by one and it installed a bunch of packages, but my internal atheros wifi adapter is still only listing the connections available. When I try to connect to one it tries to but after 30 seconds it says disconnected you are now offline.


Just to be clear I also have an external netgear USB wifi adapter which is working fine.

And I have an internal ethernet from Realtek.

If you have any other ideas to try please let me know, I will keep trying a few things at my end.

Thanks

Al

---

### Post by praseodym on 2014-11-24
Try setting up an UDEV-rule:

```
gksudo gedit /etc/udev/rules.d/10-wlan-stick.rules 
```
Add these lines:

```
# UDEV-rule for external USB adapters
# unloads/loads the internal driver when the stick is plugged in

ACTION=="add", GOTO="device_check"
ACTION=="remove", GOTO="onboard_load"

LABEL="device_check"
### WLAN-Stick erkannt, Onboard-Karte deaktivieren
SUBSYSTEM=="net", KERNEL=="wlan1", RUN+="/sbin/modprobe -rf ath9k"

GOTO="rules_end"

LABEL="onboard_load"
### WLAN-Stick entfernt, Onboard-Karte aktivieren
SUBSYSTEM=="net", KERNEL=="wlan*", RUN+="/sbin/modprobe ath9k"

LABEL="rules_end"
```
Save, close the editor and restart UDEV
```
sudo service udev reload
sudo service udev restart
```

---

### Post by vrcdng on 2014-11-24
Thanks again, 

I tried that too, but I still am unable to get the internal atheros to do anymore than simply see the SSIDs out there.

I also have gone into Windows 8 and installed the Netgear external wifi adapter, the problem is it would not install. The light on the device never lit up and so I got hold of another external wifi adapter by D-Link (N 150 DWA-121) and tried to install it in Win8, but it too had the same problem. Maybe it is no longer possible to install any external wifi adapter into my Windows 8 PC, but then why is Ubuntu able to get them to work? I just can't understand.

In Windows 8 the: 

Atheros internal can see the SSIDs, but never can connect, it says its drivers are installed properly
Netgear external cannot see the SSIDs, it says drivers are installed properly
D-Link external cannot see the SSIDs, it says drivers are installed properly

In Ubuntu 14.04:


Atheros internal can see the SSIDs, but never can connect
Netgear external works properly
D-Link external works properly

This is a weird problem. I figure if I can get the Atheros fixed, then the other adapters may start to work too. As I mentioed before I removed the atheros temporarily off the motherboard, but the externals still would not work, which might mean that something could be set incorrectly on the motherboard itself somewhere. Some part of the motherboard that handles some of the network communication. I don't want to go in that direction though until I have looked at any other easier things I can try first to solve this.

Al

---

### Post by jeremy31 on 2014-11-24
Can you change the security(encryption) on your wifi router to WPA2-AES only as it shows a mixed mode now that includes TKIP

---

### Post by vrcdng on 2014-11-25
Good news.

Thanks to both of you I am on my way to checking that all is working.

I tried your tip Jeremy to go into the router and change the setting from mixed mode to WPA2-AES only. I disabled networking in ubuntu and shutdown and restarted and re-enabled it, and it let me use the atheros internal to connect. Also I went back into Windows 8 and re-enabled the atheros with device manager, checking it was turned on in the Wireless section of windows tiles.  Checked flight mode was off and the atheros is now working in win 8. Many thanks indeed to both of you for your help. You are top men!!

I am going to spend the next 24 hours checking that the other wifi external adapters are all working too as well as a few other things. Then I will let you know if all is fixed. The only worry I have is that the wifi router I am using is a public one for about 10 other people in this apartment building. I am not sure if my changing the router setting will mess up other people's connections and devices. It says in the router that the mixed mode is the recommended setting. So do you think that I am able to change the setting back to mixed mode and still keep my wifi working? Am I able to specify to my PC that it will have to tackle mixed mode and still get an internet connection?

If not I will have to discuss with my neighbors a way we can all use the router without stepping on each others toes.

Many thanks

Al

---

### Post by vrcdng on 2014-11-27
I have been able to get all my wifi adapters working in Ubuntu and Windows, but yesterday the wifi router seems to have reset itself for some unknown reason. It is now broadcasting its original netgear name as the SSID and will only accept the network key on the box label, not the custom one set in the admin page. In the admin page it says it is broadcasting the custom SSID but it is actually ignoring this and broadcasting netgear SSID. Is it safe to just turn the router power off and try to reboot it to get it to restore itself. This may cut off other apartement wifi users for a few seconds, but should not permanently mess things up should it?

---

### Post by jeremy31 on 2014-11-27
> **vrcdng said:**
> I have been able to get all my wifi adapters working in Ubuntu and Windows, but yesterday the wifi router seems to have reset itself for some unknown reason. It is now broadcasting its original netgear name as the SSID and will only accept the network key on the box label, not the custom one set in the admin page. In the admin page it says it is broadcasting the custom SSID but it is actually ignoring this and broadcasting netgear SSID. Is it safe to just turn the router power off and try to reboot it to get it to restore itself. This may cut off other apartement wifi users for a few seconds, but should not permanently mess things up should it?

The other users are likely without access now if the SSID and password has changed.  A full reset might help and then set the SSID and password up as it was before

---

### Post by vrcdng on 2014-11-27
Yes I think the other people are having problems. I will try and reset it, I do not want to hard reset it though because I do not want to alter all the custom stuff (SSIDs, passwords, and a bunch of other stuff etc) set in it by the serviceman who installed it months ago.

Another weird thing is the download speed of the router is a lot slower after this happened. I am wondering if maybe there are other routers chained together in the apartment block that repeat the signal around, but are now confused because they are not seeing the original SSID.

Someone is talking to the landlord who runs the place and I think they will hopefully fix it, but it seems a waste of money to get a serviceman in if all that is required is a reset.

Thanks again for all your help.


Al

---

### Post by vrcdng on 2014-11-28
Ok this problem is completely solved.

Internals work and both externals in Ubuntu and Win8

I restarted the router from the admin page and the device began to broadcast the correct custom SSID again.

Just for win8 users the problem of installing the external wifi devices was due to the Zonealarm firewall. I uninstalled it, then installed both wifi devices and reinstalled ZA.

Well done guys.

Bye

Al

---

