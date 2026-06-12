---
title: "hp pavilion dv5000 wifi problem[SOLVED]"
date: 2014-04-28
forum: Networking &amp; Wireless
---

### Post by bryantarrington on 2014-04-28
Ubuntu 14.04 can connect with Netgear WNA1100 but not with internal wifi.  Here is some info:

[CODE06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02) 
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:1355] 
    Kernel driver in use: b43-pci-bridge 
06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10) 
    Subsystem: Hewlett-Packard Company Device [103c:30a4] 
    Kernel driver in use: 8139too 

laptop@laptop-Pavilion-dv5000-EP411UA-ABA:~$ lsusb 
Bus 001 Device 006: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271] 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 

laptop@laptop-Pavilion-dv5000-EP411UA-ABA:~$ iwconfig 
wlan0     IEEE 802.11bgn  ESSID:"WIRE278"   
          Mode:Managed  Frequency:2.462 GHz  Access Point: 2C:B0:5D:46:A6:8A    
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=70/70  Signal level=-16 dBm   
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:1  Invalid misc:191   Missed beacon:0 
   

 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 


][/CODE]

```
                         laptop@laptop-Pavilion-dv5000-EP411UA-ABA:~$ rfkill list all 
 2: phy3: Wireless LAN 
     Soft blocked: no 
     Hard blocked: no 
 

  
```

[CODE                         laptop@laptop-Pavilion-dv5000-EP411UA-ABA:~$ lsmod 
 Module                  Size  Used by 
 usb_storage            48417  0  
 ctr                    12905  2  
 ccm                    17496  2  
 arc4                   12536  2  
 ath9k_htc              90038  0  
 ath9k_common           13359  1 ath9k_htc 
 ath9k_hw              438205  2 ath9k_common,ath9k_htc 
 ath                    23922  3 ath9k_common,ath9k_htc,ath9k_hw 
 bnep                   18895  2  
 rfcomm                 53664  0  
 bluetooth             342263  10 bnep,rfcomm 
 b43                   356470  0  
 joydev                 17101  0  
 hp_wmi                 13702  0  
 radeon               1416373  3  
 sparse_keymap          13708  1 hp_wmi 
 snd_atiixp             19305  2  
 bcma                   42043  1 b43 
 snd_atiixp_modem       18670  0  
 snd_ac97_codec        105709  2 snd_atiixp_modem,snd_atiixp 
 mac80211              545990  2 b43,ath9k_htc 
 ac97_bus               12642  1 snd_ac97_codec 
 snd_pcm                85501  3 snd_ac97_codec,snd_atiixp_modem,snd_atiixp 
 snd_page_alloc         14230  3 snd_pcm,snd_atiixp_modem,snd_atiixp 
 snd_seq_midi           13132  0  
 cfg80211              409394  4 b43,ath,mac80211,ath9k_htc 
 ttm                    72698  1 radeon 
 snd_seq_midi_event     14475  1 snd_seq_midi 
 drm_kms_helper         46907  1 radeon 
 snd_rawmidi            25135  1 snd_seq_midi 
 drm                   243792  5 ttm,drm_kms_helper,radeon 
 snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi 
 psmouse                91033  0  
 snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi 
 snd_timer              28584  2 snd_pcm,snd_seq 
 serio_raw              13230  0  
 i2c_algo_bit           13197  1 radeon 
 snd                    60871  13 snd_ac97_codec,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_atiixp_modem,snd_atiixp,snd_seq_midi 
 k8temp                 12842  0  
 soundcore              12600  1 snd 
 wmi                    18673  1 hp_wmi 
 shpchp                 32128  0  
 i2c_piix4              17723  0  
 ati_agp                13177  0  
 video                  18903  0  
 mac_hid                13037  0  
 parport_pc             31981  0  
 ppdev                  17391  0  
 lp                     13299  0  
 parport                40836  3 lp,ppdev,parport_pc 
 pata_acpi              12886  0  
 8139too                32571  0  
 8139cp                 27171  0  
 mii                    13654  2 8139cp,8139too 
 ssb                    51854  1 b43 
 pata_atiixp            13058  2  
 

  ][/CODE]


```
                         laptop@laptop-Pavilion-dv5000-EP411UA-ABA:~$ sudo iwlist scan 
 wlan0     Scan completed : 
           Cell 01 - Address: 2C:B0:5D:46:A6:8A 
                     Channel:11 
                     Frequency:2.462 GHz (Channel 11) 
                     Quality=70/70  Signal level=-15 dBm   
                     Encryption key:on 
                     ESSID:"WIRE278" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                               24 Mb/s; 36 Mb/s; 54 Mb/s 
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                     Mode:Master 
                     Extra:tsf=00000000c058d4cb 
                     Extra: Last beacon: 268ms ago 
                     IE: Unknown: 000757495245323738 
                     IE: Unknown: 010882848B962430486C 
                     IE: Unknown: 03010B 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 2F0100 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : CCMP 
                         Pairwise Ciphers (1) : CCMP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: 32040C121860 
                     IE: Unknown: 2D1AFD191BFFFFFF0000000000000000000000000000000000000000 
                     IE: Unknown: 3D160B080400000000000000000000000000000000000000 
                     IE: Unknown: 4A0E14000A002C01C800140005001900 
                     IE: Unknown: 7F0101 
                     IE: Unknown: DD7B0050F204104A0001101044000102103B00010310470010D94FA1DB4FB0A7F0E509CBE128CE5FF11021000D4E4554474541522C20496E632E10230008574E44523435303010240008574E44523435303010420004343533361054000800060050F204000110110008574E445234353030100800020004103C000103 
                     IE: Unknown: DD090010180204F03C0000 
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
           Cell 02 - Address: 52:57:1A:04:1B:A0 
                     Channel:1 
                     Frequency:2.412 GHz (Channel 1) 
                     Quality=16/70  Signal level=-94 dBm   
                     Encryption key:on 
                     ESSID:"" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s 
                               18 Mb/s; 36 Mb/s; 54 Mb/s 
                     Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s 
                     Mode:Master 
                     Extra:tsf=00000024002fcb2f 
                     Extra: Last beacon: 28776ms ago 
                     IE: Unknown: 0000 
                     IE: Unknown: 010882848B961224486C 
                     IE: Unknown: 030101 
                     IE: Unknown: 32048C98B060 
                     IE: Unknown: 0706555320010B14 
                     IE: Unknown: 050400010000 
                     IE: Unknown: 2A0104 
                     IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000 
                     IE: Unknown: 3D1601000700000000000000000000000000000000000000 
                     IE: Unknown: 7F0101 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : CCMP 
                         Pairwise Ciphers (1) : CCMP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
                     IE: Unknown: 0B0504000D127A 
                     IE: Unknown: DD07000C4303000000 
           Cell 03 - Address: CC:35:40:42:D9:11 
                     Channel:11 
                     Frequency:2.462 GHz (Channel 11) 
                     Quality=17/70  Signal level=-93 dBm   
                     Encryption key:on 
                     ESSID:"HOME-D911" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                               24 Mb/s; 36 Mb/s; 54 Mb/s 
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                     Mode:Master 
                     Extra:tsf=000002abfdf27185 
                     Extra: Last beacon: 268ms ago 
                     IE: Unknown: 0009484F4D452D44393131 
                     IE: Unknown: 010882848B9624B0486C 
                     IE: Unknown: 03010B 
                     IE: Unknown: 050400010000 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 2F0100 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: 32048C129860 
                     IE: Unknown: 2D1AFD181BFFFFFF0000000000000000000000000000000000000000 
                     IE: Unknown: 3D160B081500000000000000000000000000000000000000 
                     IE: Unknown: DD180050F204104A00011010440001021049000600372A000120 
                     IE: Unknown: DD090010180202F03C0000 
                     IE: WPA Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
           Cell 04 - Address: 00:22:75:23:AD:90 
                     Channel:11 
                     Frequency:2.462 GHz (Channel 11) 
                     Quality=20/70  Signal level=-90 dBm   
                     Encryption key:on 
                     ESSID:"SavannahBee" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s 
                               18 Mb/s; 36 Mb/s; 54 Mb/s 
                     Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s 
                     Mode:Master 
                     Extra:tsf=00000158edd1572f 
                     Extra: Last beacon: 340ms ago 
                     IE: Unknown: 000B536176616E6E6168426565 
                     IE: Unknown: 010882848B961224486C 
                     IE: Unknown: 03010B 
                     IE: Unknown: 2A0104 
                     IE: Unknown: 32040C183060 
                     IE: Unknown: 2D1AEE110FFFFF0000010000000000000000000000000C0000000000 
                     IE: Unknown: 3D160B070500000000000000000000000000000000000000 
                     IE: Unknown: 3E0100 
                     IE: WPA Version 1 
                         Group Cipher : CCMP 
                         Pairwise Ciphers (1) : CCMP 
                         Authentication Suites (1) : PSK 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : CCMP 
                         Pairwise Ciphers (1) : CCMP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 
                     IE: Unknown: 7F0101 
                     IE: Unknown: DD07000C4304000000 
                     IE: Unknown: DD1E00904C33EE110FFFFF0000010000000000000000000000000C0000000000 
                     IE: Unknown: DD1A00904C340B070500000000000000000000000000000000000000 
                     IE: Unknown: DD9F0050F204104A0001101044000102103B000103104700102880288028801880A88000227523AD901021001242656C6B696E20436F72706F726174696F6E1023001642656C6B696E20576972656C65737320526F75746572102400034635441042000C3131313131313131313131311054000800060050F20400011011001642656C6B696E20576972656C65737320526F75746572100800020084103C000101 
           Cell 05 - Address: CC:35:40:9C:F9:17 
                     Channel:11 
                     Frequency:2.462 GHz (Channel 11) 
                     Quality=22/70  Signal level=-88 dBm   
                     Encryption key:on 
                     ESSID:"HOME-F917" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                               24 Mb/s; 36 Mb/s; 54 Mb/s 
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                     Mode:Master 
                     Extra:tsf=00000001b5d911a3 
                     Extra: Last beacon: 296ms ago 
                     IE: Unknown: 0009484F4D452D46393137 
                     IE: Unknown: 010882848B9624B0486C 
                     IE: Unknown: 03010B 
                     IE: Unknown: 050400010000 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 2F0100 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: 32048C129860 
                     IE: Unknown: 2D1AFD181BFFFFFF0000000000000000000000000000000000000000 
                     IE: Unknown: 3D160B081100000000000000000000000000000000000000 
                     IE: Unknown: DD180050F204104A00011010440001021049000600372A000120 
                     IE: Unknown: DD090010180200F03C0000 
                     IE: WPA Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
           Cell 06 - Address: 02:1D:D4:17:38:D0 
                     Channel:11 
                     Frequency:2.462 GHz (Channel 11) 
                     Quality=17/70  Signal level=-93 dBm   
                     Encryption key:on 
                     ESSID:"" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s 
                               18 Mb/s; 36 Mb/s; 54 Mb/s 
                     Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s 
                     Mode:Master 
                     Extra:tsf=000000f62821bbac 
                     Extra: Last beacon: 488ms ago 
                     IE: Unknown: 0000 
                     IE: Unknown: 010882848B961224486C 
                     IE: Unknown: 03010B 
                     IE: Unknown: 32048C98B060 
                     IE: Unknown: 0706555320010B14 
                     IE: Unknown: 050400010000 
                     IE: Unknown: 2A0104 
                     IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000 
                     IE: Unknown: 3D160B070500000000000000000000000000000000000000 
                     IE: Unknown: 4A0E14000A002C01C800140005001900 
                     IE: Unknown: 7F0101 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : CCMP 
                         Pairwise Ciphers (1) : CCMP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 
                     IE: Unknown: 0B05010021127A 
                     IE: Unknown: DD07000C4303000000 
           Cell 07 - Address: B0:77:AC:06:C2:70 
                     Channel:11 
                     Frequency:2.462 GHz (Channel 11) 
                     Quality=18/70  Signal level=-92 dBm   
                     Encryption key:on 
                     ESSID:"ATT3g3P7t2" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                               24 Mb/s; 36 Mb/s; 54 Mb/s 
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                     Mode:Master 
                     Extra:tsf=000000f77a1d2183 
                     Extra: Last beacon: 336ms ago 
                     IE: Unknown: 000A41545433673350377432 
                     IE: Unknown: 010882848B962430486C 
                     IE: Unknown: 03010B 
                     IE: Unknown: 050402030000 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 2F0100 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: 32040C121860 
                     IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000 
                     IE: Unknown: 3D160B080000000000000000000000000000000000000000 
                     IE: Unknown: DD090010180200F02C0000 
                     IE: WPA Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
           Cell 08 - Address: 00:1D:D4:17:38:D0 
                     Channel:11 
                     Frequency:2.462 GHz (Channel 11) 
                     Quality=19/70  Signal level=-91 dBm   
                     Encryption key:on 
                     ESSID:"Abaco Life" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s 
                               18 Mb/s; 36 Mb/s; 54 Mb/s 
                     Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s 
                     Mode:Master 
                     Extra:tsf=000000f62824d14d 
                     Extra: Last beacon: 284ms ago 
                     IE: Unknown: 000A416261636F204C696665 
                     IE: Unknown: 010882848B961224486C 
                     IE: Unknown: 03010B 
                     IE: Unknown: 32048C98B060 
                     IE: Unknown: 0706555320010B14 
                     IE: Unknown: 05040001003C 
                     IE: Unknown: DD310050F204104A0001101044000102104700102880288028801880A880001DD41738D0103C0001011049000600372A000120 
                     IE: Unknown: 2A0104 
                     IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000 
                     IE: Unknown: 3D160B070500000000000000000000000000000000000000 
                     IE: Unknown: 4A0E14000A002C01C800140005001900 
                     IE: Unknown: 7F0101 
                     IE: WPA Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : TKIP CCMP 
                         Authentication Suites (1) : PSK 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : TKIP CCMP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 
                     IE: Unknown: 0B05010021127A 
                     IE: Unknown: DD07000C4303000000 
           Cell 09 - Address: 74:9D:DC:55:B3:01 
                     Channel:2 
                     Frequency:2.417 GHz (Channel 2) 
                     Quality=23/70  Signal level=-87 dBm   
                     Encryption key:on 
                     ESSID:"2WIRE299" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                               9 Mb/s; 12 Mb/s; 18 Mb/s 
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     Extra:tsf=000001d31372a181 
                     Extra: Last beacon: 28224ms ago 
                     IE: Unknown: 00083257495245323939 
                     IE: Unknown: 010882848B960C121824 
                     IE: Unknown: 030102 
                     IE: Unknown: 050400010004 
                     IE: Unknown: 0706555320010B1B 
                     IE: Unknown: 2A0100 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: WPA Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: 32043048606C 
           Cell 10 - Address: 94:C1:50:43:B0:F1 
                     Channel:6 
                     Frequency:2.437 GHz (Channel 6) 
                     Quality=25/70  Signal level=-85 dBm   
                     Encryption key:on 
                     ESSID:"2WIRE420" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                               9 Mb/s; 12 Mb/s; 18 Mb/s 
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     Extra:tsf=000001aa6b1477e4 
                     Extra: Last beacon: 26020ms ago 
                     IE: Unknown: 00083257495245343230 
                     IE: Unknown: 010882848B960C121824 
                     IE: Unknown: 030106 
                     IE: Unknown: 05040001000E 
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
           Cell 11 - Address: 2C:B0:5D:44:3E:EC 
                     Channel:6 
                     Frequency:2.437 GHz (Channel 6) 
                     Quality=25/70  Signal level=-85 dBm   
                     Encryption key:on 
                     ESSID:"SPENCER1" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                               24 Mb/s; 36 Mb/s; 54 Mb/s 
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                     Mode:Master 
                     Extra:tsf=000008922484d183 
                     Extra: Last beacon: 4684ms ago 
                     IE: Unknown: 00085350454E43455231 
                     IE: Unknown: 010882848B962430486C 
                     IE: Unknown: 030106 
                     IE: Unknown: 050401020000 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 2F0100 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : CCMP 
                         Pairwise Ciphers (1) : CCMP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: 32040C121860 
                     IE: Unknown: 2D1AFD191BFFFFFF0000000000000000000000000000000000000000 
                     IE: Unknown: 3D1606081100000000000000000000000000000000000000 
                     IE: Unknown: 4A0E14000A002C01C800140005001900 
                     IE: Unknown: 7F0101 
                     IE: Unknown: DD270050F204104A000110104400010210470010A51366D01B71042412F642066E92671B103C000103 
                     IE: Unknown: DD090010180200F03C0000 
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
  
 lo        Interface doesn't support scanning. 
  
 eth0      Interface doesn't support scanning. 
 

  
```

```
                         laptop@laptop-Pavilion-dv5000-EP411UA-ABA:~$ lspci -nnk | grep -iA2 net 
 06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02) 
     Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:1355] 
     Kernel driver in use: b43-pci-bridge 
 06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10) 
     Subsystem: Hewlett-Packard Company Device [103c:30a4] 
     Kernel driver in use: 8139too 
  
```

Any help appreciated!!!
Thanks.

---

### Post by bryantarrington on 2014-04-29
I did the following and fixed it:

   sudo apt-get remove --purge bcmwl-kernel-source
 sudo apt-get install b43-fwcutter firmware-b43-installer
 sudo modprobe b43
restarted

---

