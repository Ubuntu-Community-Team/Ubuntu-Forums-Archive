---
title: "ubuntu 12.10, broadcom4313 &quot;device not ready&quot;"
date: 2013-10-19
forum: Networking &amp; Wireless
---

### Post by learst on 2013-10-19
Hello,

I've been using ubuntu12.10 for a few months, and everything seems to be working fine. Bout a week ago, I started having some problems with my wireless network. The connection keeps dropping for some reason, and I changed the MTU, disconnect/reconnect etc, and changing the network manager to wicd (have since reverted back to gnome-network manager).

Recently though, after disconnecting the wireless (of if it gets disconnected by itself),  I can't reconnect. Right-clicking on the wireless icon - it says "device not ready". If I reboot the computer, it's automatically connected. I don't want the hassle to restart my laptop each time it gets disconnected or if I want to reconnect/disconnect.

*I have to note that just this morning it got disconnected, and "device not ready" appearead. I was about to restart my laptop but noticed the website finished loading. So apparently it reconnected by itself, though the wireless icon looks like it is turned off.

Here's some info and things I've tried:
```
lspci
03:00.0 Network controller: Broadcom Corporation BCM4331 802.11a/b/g/n (rev 02)
04:00.0 FireWire (IEEE 1394): LSI Corporation FW643 [TrueFire] PCIe 1394b Controller (rev 08)

```

```
sudo apt-get install linux-firmware-nonfree
[sudo] password for jeremy:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  gir1.2-unique-3.0 libunique-3.0-0 python-wicd wicd-daemon
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```
dmesg | grep -e b43 -e bcma
[   18.536511] bcma: Found chip with id 0x4331, rev 0x02 and package 0x09
[   18.536563] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[   18.536605] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1D, class 0x0)
[   18.536706] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x13, class 0x0)
[   18.626851] bcma: Bus registered
[   18.727317] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[   18.750296] Registered led device: b43-phy0::tx
[   18.750314] Registered led device: b43-phy0::rx
[   18.750331] Registered led device: b43-phy0::radio
[   19.998192] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)

```

```
sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  gir1.2-unique-3.0 libunique-3.0-0 python-wicd wicd-daemon
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

And oh, I'm running ubuntu 12.10 on a macbook pro. Thanks for your help!

---

### Post by praseodym on 2013-10-19
Please show:
```

uname -a
lsmod
iwconfig
rfkill list
sudo iwlist scan

```

---

### Post by learst on 2013-10-19
-uname a
```

Linux junhoe-UbuntuSSD 3.5.0-41-generic #64-Ubuntu SMP Wed Sep 11 15:36:42 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

lsmod
```

Module                  Size  Used by
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_cirrus    23807  1 
coretemp               13401  0 
kvm_intel             132760  0 
kvm                   414111  1 kvm_intel
ghash_clmulni_intel    13221  0 
aesni_intel            51038  1 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
arc4                   12530  2 
b43                   370021  0 
mac80211              535936  1 b43
cfg80211              206797  2 b43,mac80211
ssb                    52275  1 b43
joydev                 17458  0 
applesmc               19315  0 
input_polldev          13897  1 applesmc
microcode              22804  0 
snd_hda_intel          33492  3 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
bcm5974                17316  0 
parport_pc             32689  0 
rfcomm                 46620  12 
bnep                   18141  2 
ppdev                  17074  0 
btusb                  22475  0 
bluetooth             209438  22 rfcomm,bnep,btusb
bcma                   35657  1 b43
lpc_ich                17062  0 
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17501  1 
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
i915                  520925  3 
drm_kms_helper         49113  1 i915
mei                    40691  0 
drm                   288972  4 i915,drm_kms_helper
i2c_algo_bit           13414  1 i915
nls_iso8859_1          12714  1 
apple_gmux             13413  0 
video                  19391  2 i915,apple_gmux
apple_bl               13674  1 apple_gmux
mac_hid                13206  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usb_storage            48839  2 
hid_apple              13238  0 
usbhid                 46987  0 
hid                   100411  3 hid_generic,hid_apple,usbhid
sdhci_pci              18617  0 
sdhci                  32646  1 sdhci_pci
firewire_ohci          40402  0 
ahci                   25721  1 
libahci                31192  1 ahci
tg3                   148928  0 
firewire_core          64369  1 firewire_ohci
crc_itu_t              12708  1 firewire_core

```

iwconfig
```

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"TicTacToe"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: 9C:C7:A6:D0:2C:B7   
          Bit Rate=9 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:21  Invalid misc:2   Missed beacon:0

```

rfkill list
```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

sudo iwlist scan
```

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 9C:C7:A6:D0:2C:B7
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"TicTacToe"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000035249428fe
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 0009546963546163546F65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010D
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAE011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331AAE011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160D071700000000000000000000000000000000000000
                    IE: Unknown: 34160D071700000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: Unknown: DD650050F204104A0001101044000102103B00010310470010E6C0404A5045C55D27CA9CC7A6D02C101021000341564D1023000446426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800020188103C000103
          Cell 02 - Address: C0:25:06:BE:8F:DE
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Sender ALK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000263a547d180
                    Extra: Last beacon: 2824ms ago
                    IE: Unknown: 000A53656E64657220414C4B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1602051100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: Unknown: DD270050F204104A0001101044000102104700100296783DC29219924840875F7557F710103C000103
          Cell 03 - Address: BC:05:43:B9:4F:63
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 6360 Cable"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000038a52c180
                    Extra: Last beacon: 1044ms ago
                    IE: Unknown: 0014465249545A21426F782036333630204361626C65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603051300000000000000000000000000000000000000
                    IE: Unknown: 341603051300000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0C00040E010102000000000000
                    IE: Unknown: DD650050F204104A0001101044000102103B00010310470010A0DE57746F764B5E56DA96B3C6C15E101021000341564D1023000446426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800020188103C000103
          Cell 04 - Address: F4:EC:38:B3:F7:AA
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Oxytocin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000016908d80
                    Extra: Last beacon: 980ms ago
                    IE: Unknown: 00084F7879746F63696E
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
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34040D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16040D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000
                    IE: Unknown: DD850050F204104A0001101044000102103B0001031047001000000000000010000000F4EC38B3F7AA1021000754502D4C494E4B1023000B544C2D5752313034334E4410240003312E3010420003312E301054000800060050F20400011011001B576972656C65737320526F7574657220544C2D5752313034334E44100800020086103C000101
          Cell 05 - Address: 00:15:0C:F6:25:F3
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"ADA2013"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001516857c236
                    Extra: Last beacon: 892ms ago
                    IE: Unknown: 000741444132303133
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0107
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0A0800280101000200FF0F
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: CC:B2:55:F2:CA:8A
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"3erWG"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000867e5f838
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 00053365725747
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000101104700102880288028801880A880CCB255F2CA8A103C000101
                    IE: Unknown: 05040001001C
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160D000400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010014127A
                    IE: Unknown: DD07000C4307000000
          Cell 07 - Address: 00:24:01:2D:0A:8E
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"KD_4311"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000007148065dd3a
                    Extra: Last beacon: 404ms ago
                    IE: Unknown: 00074B445F34333131
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030108
                    IE: Unknown: 2A0102
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340807050000000F000000000000000000000000000000
                    IE: Unknown: 2D1A4E101FFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D160807110000000F000000000000000000000000000000
                    IE: Unknown: DD790050F204104A0001101044000102103B0001031047001060BB35B73CED33A69444C7F36DEB2EB61021000E442D4C696E6B2053797374656D73102300074449522D363135102400024232104200046E6F6E651054000800060050F204000110110011576972656C657373204E20526F7574657210080002008C
          Cell 08 - Address: F8:D1:11:60:8F:9A
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_608F9A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f2c30eed80
                    Extra: Last beacon: 292ms ago
                    IE: Unknown: 000E54502D4C494E4B5F363038463941
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD850050F204104A0001101044000101103B0001031047001000000000000010000000F8D111608F9A1021000754502D4C494E4B10230009544C2D57523834314E10240007362E302F372E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523834314E100800020086103C000101
                    IE: Unknown: DD050050F20500
          Cell 09 - Address: 9C:C7:A6:0E:F8:FC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"weitewelt"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000772641e1c1
                    Extra: Last beacon: 180ms ago
                    IE: Unknown: 0009776569746577656C74
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331AEE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B071500000000000000000000000000000000000000
                    IE: Unknown: 34160B071500000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD650050F204104A0001101044000102103B00010310470010EE516F94F2625D29D85A9CC7A60EF8101021000341564D1023000446426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800020188103C000103
          Cell 10 - Address: 9C:C7:A6:6B:A8:B7
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7360 SL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000760c54b180
                    Extra: Last beacon: 204ms ago
                    IE: Unknown: 001A465249545A21426F7820466F6E20574C414E203733363020534C
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331AEE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B071500000000000000000000000000000000000000
                    IE: Unknown: 34160B071500000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: Unknown: DD650050F204104A0001101044000102103B00010310470010299461D5A22BD0F1C0249CC7A66BA8101021000341564D1023000446426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800020188103C000103
          Cell 11 - Address: C0:25:06:95:43:D8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7112"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000060ca9342
                    Extra: Last beacon: 196ms ago
                    IE: Unknown: 0017465249545A21426F7820466F6E20574C414E2037313132
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0107
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0A0800280101000200FF0F
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 12 - Address: 00:26:5B:AD:33:08
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"HITRON-3300"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000206e041fd09
                    Extra: Last beacon: 1204ms ago
                    IE: Unknown: 000B484954524F4E2D33333030
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
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
                    IE: Unknown: 0B0502002B127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706444520010D10
                    IE: Unknown: DD9D0050F204104A0001101044000101103B000103104700102880288028801880A88000265BAD33081021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B41505310080002210C103C000101
          Cell 13 - Address: 84:C9:B2:C3:CC:45
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"dlink2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002bf2e083176
                    Extra: Last beacon: 1004ms ago
                    IE: Unknown: 0006646C696E6B32
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A88084C9B2C3CC45103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1603000700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05060048127A
                    IE: Unknown: DD07000C4307000000

```

Hope this information helps. Thanks!

---

### Post by praseodym on 2013-10-19
Change the encryption mode to pure WPA2-AES (CCMP) in you router interface. Also a fixed channel and 20MHz bandwidth instead of 20/40MHz.

---

### Post by learst on 2013-10-19
Thing is I lived in a shared apartment, so it's not easy to make those changes to router.
h m
Anyway, how does that solve the problem of the "device not ready" after disconnected? Isn't that a problem with my Ubuntu?

---

### Post by praseodym on 2013-10-19
No, its coming from mixed encryption. Try Wicd instead of the network-manager:
```

wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
Choose **wlan0** as interface name and **wext** as driver

---

### Post by learst on 2013-10-19
> **praseodym said:**
> No, its coming from mixed encryption. Try Wicd instead of the network-manager:
```

wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
Choose **wlan0** as interface name and **wext** as driver


Well I managed to change the encryption mode to pure WPA2 (CCMP), but could not find any settings change to 20 Mhz bandwidth. Hopefully my connection is more stable now.

I also reinstalled wicd as suggested above. I have no idea though how to set the **wlan0** and** wext** thing?

Using wicd, I could disconnect and reconnect now. Thanks!

---

### Post by learst on 2013-10-23
Well, the wicd didn't last very long. In fact it feels worse now.

Although I remain "connected", after a while  I can't load any web pages. And this can be fixed just by disconnecting/reconnecting. This could happen after a few hours, or just within minutes.

It shouldn't be a problem with my connection as I don't have a problem on Mac OS on the same macbook that I'm running ubuntu with.

---

