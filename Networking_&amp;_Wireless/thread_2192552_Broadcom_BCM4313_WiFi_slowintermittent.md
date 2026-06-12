---
title: "Broadcom BCM4313: WiFi slow/intermittent"
date: 2013-12-08
forum: Networking &amp; Wireless
---

### Post by tpeaton on 2013-12-08
Hi All,

I've searched high and low, tried many of the things I've found on ubuntuforums as well as other sites, but have not found anything that works yet, so hopefully someone can help here.

I bought a new Lenovo G500 laptop and installed Xubuntu 13.10.  Everything appears to be working normally except my wifi, which connects and works, but in a very limited way.  The network seems to slow to a crawl, pause for 10-30 seconds, then pick back up again.  If I can't get it working in the next couple days, I'll have to return the laptop, which I hope not to have to do.

Any help would be greatly appreciated!  Here's what I know so far:

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
02:00.0 0280: 14e4:4727 (rev 01)

---

### Post by praseodym on 2013-12-08
Did you install the package **linux-firmware-nonfree**?

Please show the outputs of
```
lsmod
iwconfig
cat /etc/resolv.conf
sudo iwlist scan
```

---

### Post by tpeaton on 2013-12-08
linux-firmware-nonfree is installed.

Here are the results of those commands:

lsmod
```

Module                  Size  Used by
dm_crypt               22728  1 
rts5139               331166  0 
joydev                 17377  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
thinkpad_acpi          80701  0 
nvram                  14362  1 thinkpad_acpi
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  4 
bnep                   19564  2 
bluetooth             371880  10 bnep,rfcomm
snd_hda_codec_hdmi     41117  1 
snd_hda_codec_conexant    56990  1 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
snd_hda_intel          48171  3 
kvm                   431315  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
snd_hda_codec         188738  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
aesni_intel            55624  39975 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20329  19989 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
microcode              23518  0 
psmouse                97626  0 
serio_raw              13413  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
lpc_ich                21080  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
ideapad_laptop         18342  0 
sparse_keymap          13948  1 ideapad_laptop
snd                    69141  18 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
mei_me                 18421  0 
mei                    77692  1 mei_me
soundcore              12680  1 snd
mac_hid                13205  0 
arc4                   12608  2 
brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
bcma                   46670  2 brcmsmac
mac80211              596969  1 brcmsmac
cfg80211              479757  2 brcmsmac,mac80211
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
i915                  655752  2 
i2c_algo_bit           13413  1 i915
drm_kms_helper         52651  1 i915
drm                   296739  3 i915,drm_kms_helper
alx                    32255  0 
ahci                   25819  2 
libahci                31898  1 ahci
mdio                   13807  1 alx
video                  19318  1 i915

```


iwconfig
```

eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Double Buck"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 28:C6:8E:15:07:FE   
          Bit Rate=43.3 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:67   Missed beacon:0

```


cat /etc/resolv.conf
```

nameserver 192.168.1.1

```


sudo iwlist scan
```

eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 28:C6:8E:15:07:FE
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d3fc8f9180
                    Extra: Last beacon: 168ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6F1003FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1604001500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336F1003FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: DD1A00904C3404001500000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 28:C6:8E:15:07:FE
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"Double Buck"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d3eeac3777
                    Extra: Last beacon: 232700ms ago
                    IE: Unknown: 000B446F75626C65204275636B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6F1003FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1604001500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336F1003FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: DD1A00904C3404001500000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:22:A4:C4:04:A9
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"2WIRE680"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000db873f51c
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00083257495245363830
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 04 - Address: 60:C3:97:B6:38:31
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"2WIRE043"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001189dfa5a11
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00083257495245303433
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
          Cell 05 - Address: 60:C3:97:26:43:F9
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"2WIRE480"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000430f8bbff7
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00083257495245343830
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030105
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
          Cell 06 - Address: 00:21:7C:39:1B:E1
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"2WIRE746"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017244731d9
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00083257495245373436
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030108
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
          Cell 07 - Address: 98:2C:BE:9B:85:E1
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"2WIRE757"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004c5c93addb2
                    Extra: Last beacon: 19500ms ago
                    IE: Unknown: 00083257495245373537
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030107
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
          Cell 08 - Address: B8:E6:25:31:03:01
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"2WIRE302"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003d96d9e95c9
                    Extra: Last beacon: 19500ms ago
                    IE: Unknown: 00083257495245333032
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030107
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
          Cell 09 - Address: 64:0F:28:9B:1C:51
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Barbour"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009e5e38092f
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 0007426172626F7572
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010A
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
          Cell 10 - Address: 60:C3:97:90:42:79
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"2WIRE952"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000b3b640
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00083257495245393532
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030108
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
          Cell 11 - Address: 00:1B:5B:B3:7A:C9
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"2WIRE161"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000049568fcb181
                    Extra: Last beacon: 20656ms ago
                    IE: Unknown: 00083257495245313631
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0102
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 12 - Address: 00:25:3C:28:B5:A1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"2WIRE205"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f42f3c3b8b
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00083257495245323035
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
          Cell 13 - Address: 64:0F:28:CE:17:6A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"ATT226"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000014686bbe0ec
                    Extra: Last beacon: 660ms ago
                    IE: Unknown: 0006415454323236
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 14 - Address: 20:C9:D0:23:95:7D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:" Wi-Fi Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d2a0c4d186
                    Extra: Last beacon: 2188ms ago
                    IE: Unknown: 000E2057692D4669204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050402030004
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAD511BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301750320
                    IE: Unknown: DD0E0017F2070001010620C9D023957D
                    IE: Unknown: DD0B0017F20100010100000007

```

---

### Post by praseodym on 2013-12-09
A lot of networks around...Try a fixed channel, not hiding the network and change the bandwidth to 20MHz instead of 20/40MHz. Check the router manual

---

### Post by tpeaton on 2013-12-09
I'll try all of that, but I'll also note that I plugged in a usb wifi adapter and everything worked fine.  I have many devices on this network and this laptop with ubuntu is the only one that has an issue.  The same laptop booted to windows does just fine.  I strongly suspect this is a client side config or driver issue.

---

### Post by tpeaton on 2013-12-10
Any advice for fixing my ubuntu issue?  Changing the config on the router seems unreasonable when all other devices perform as expected.

---

### Post by praseodym on 2013-12-11
Try Wicd:
```

sudo apt-get install wicd 
sudo service network-manager stop
sudo killall wpa_supplicant 
sudo service wicd restart
```
Choose there **wlan0** as interface name and **wext** as driver.

---

### Post by tpeaton on 2013-12-12
Switched over to wicd successfully, but had the same issue.  I've returned the laptop and will buy something with an Intel wifi chip to make life easier.  Thanks for your help.

---

