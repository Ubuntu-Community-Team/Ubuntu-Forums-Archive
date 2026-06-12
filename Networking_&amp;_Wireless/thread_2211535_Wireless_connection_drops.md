---
title: "Wireless connection drops"
date: 2014-03-16
forum: Networking &amp; Wireless
---

### Post by Korkel on 2014-03-16
Hello,

My Wireless connection goes away time from time, when I reboot it is most of the time back, but sometimes my whole WiFi isn't working anymore, how can I resolve this?

---

### Post by praseodym on 2014-03-16
Pleas open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lapci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
```
What kind of computer is it?

---

### Post by Korkel on 2014-03-16
> **praseodym said:**
> Pleas open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lapci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
```
What kind of computer is it?
mark@Team-Korkel:~$ uname-a
uname-a: opdracht niet gevonden
mark@Team-Korkel:~$ clear
mark@Team-Korkel:~$ uname -a
Linux Team-Korkel 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
mark@Team-Korkel:~$ lapci -nnk | grep -iA2 net
Opdracht ‘lapci’ niet gevonden, bedoelde u:
 Opdracht ‘lspci’ uit pakket ‘pciutils’ (main)
lapci: opdracht niet gevonden
mark@Team-Korkel:~$ lsusb
Bus 002 Device 025: ID 1bcf:0005 Sunplus Innovation Technology Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:d20c Suyin Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mark@Team-Korkel:~$ lsmod
Module                  Size  Used by
bbswitch               13943  0 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69130  0 
bnep                   19704  2 
bluetooth             372041  10 bnep,rfcomm
snd_hda_codec_hdmi     41154  1 
snd_hda_codec_realtek    56475  1 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138567  0 
kvm                   431754  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  1 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
snd_hda_intel          52267  5 
arc4                   12608  2 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
ath9k                 155779  0 
ath9k_common           13859  1 ath9k
microcode              23656  0 
ath9k_hw              444732  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              597268  1 ath9k
snd                    69141  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i915                  661339  3 
psmouse                97655  0 
serio_raw              13413  0 
drm_kms_helper         52710  1 i915
cfg80211              480503  3 ath,ath9k,mac80211
lpc_ich                21080  0 
mei_me                 18421  0 
drm                   297056  4 i915,drm_kms_helper
mei                    77782  1 mei_me
soundcore              12680  1 snd
i2c_algo_bit           13413  1 i915
joydev                 17377  0 
acer_wmi               32522  0 
mxm_wmi                13021  0 
sparse_keymap          13948  1 acer_wmi
wmi                    19070  2 acer_wmi,mxm_wmi
video                  19318  2 i915,acer_wmi
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101762  2 hid_generic,usbhid
tg3                   162318  0 
sdhci_pci              18981  0 
ahci                   25819  2 
ptp                    18580  1 tg3
libahci                32009  1 ahci
sdhci                  42898  1 sdhci_pci
pps_core               19057  1 ptp
mark@Team-Korkel:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"zo4cg0"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 4C:AC:0A:23:67:F1   
          Bit Rate=130 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:588   Missed beacon:0


mark@Team-Korkel:~$ sudo iwlist scan
[sudo] password for mark: 
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 4C:AC:0A:23:67:F1
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"zo4cg0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004eed94781
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 00067A6F34636730
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080400000000000000000000000000000000000000
                    IE: Unknown: DD6D0050F204104A00011010440001021041000100103B00010310470010DF4C795BCA0FCF304CC5FF1410E06AA5102100035A544510230005483232304E1024000631323334353610420004313233341054000800060050F2040001101100095A544520483232304E100800020088
                    IE: Unknown: DD090010180207F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3407080400000000000000000000000000000000000000
          Cell 02 - Address: 88:03:55:91:3D:B0
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"VGV7519913DB0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e95d0c6129
                    Extra: Last beacon: 1828ms ago
                    IE: Unknown: 000D56475637353139393133444230
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0017FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1602000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020006127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD910050F204104A00011010440001021041000100103B0001031047001000000000000000030000880355913DB01021000B436F72706F726174696F6E1023000B564756373531394B5732321024000B30322E30302E31333157341042000A413333313030343831381054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: 07064E4C20010D10
          Cell 03 - Address: 00:13:F7:12:6D:12
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"SMC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000025a90451ea5
                    Extra: Last beacon: 836ms ago
                    IE: Unknown: 0003534D43
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 04 - Address: 50:67:F0:CC:F1:6C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Zy_private_U39994"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e2ed419e7f
                    Extra: Last beacon: 1008ms ago
                    IE: Unknown: 00115A795F707269766174655F553339393934
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050002397A12
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 07064E4C20010D10
                    IE: Unknown: DD1E00904C336E1017FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000500000000000000000000000000000000000000
          Cell 05 - Address: 10:FE:ED:DD:2A:6C
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"rene net"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006a17a63318
                    Extra: Last beacon: 212ms ago
                    IE: Unknown: 000872656E65206E6574
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D16070F0000000000000000000000000000000000000000
                    IE: Unknown: 3416070F0000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD990050F204104A0001101044000102103B00010310470010000102030405060708090A0B0C0D0E0F1021000754502D4C494E4B10230009544C2D57523834314E10240003382E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523834314E100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 06 - Address: 24:65:11:F7:BC:56
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7270"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000045e05072
                    Extra: Last beacon: 872ms ago
                    IE: Unknown: 0017465249545A21426F7820466F6E20574C414E2037323730
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201018F0003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1ACE131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160A0F0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: DD6A0050F204104A0001101044000102103B00010010470010351AE24A3CA807D99A9115EBC0198DAD1021000341564D10230009465249545A21426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800020188103C000103


mark@Team-Korkel:~$ 


It's an Acer Aspire, no idea what number.

---

### Post by praseodym on 2014-03-16
Deactivate the hardware encryption of the driver:
```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Additionally, change the encryption mode to pure WPA2_AES (CCMP) and a fixed channel, e.g. channel 1. Check the router manual.

---

### Post by Korkel on 2014-03-16
Channel is 7, output of command:
options ath9k nohwcrypt=1

---

### Post by praseodym on 2014-03-16
Changed the encryption?

---

### Post by Korkel on 2014-03-16
That option is not avaibole... :(

---

### Post by praseodym on 2014-03-16
Router firmware is up to date? Maybe then it works

---

### Post by Korkel on 2014-03-17
Yes that is.

---

### Post by praseodym on 2014-03-17
Screenshots?

---

### Post by Korkel on 2014-03-17
Running that script you given above is helping. ;) Thanks.

---

