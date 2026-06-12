---
title: "wifi connects but there is no internet"
date: 2013-11-09
forum: Networking &amp; Wireless
---

### Post by vidnyanszkyz on 2013-11-09
Dear All, 

I am using Ubuntu 12.10 and my problem is that sometimes it cannot access the internet. It can always connect and not surprisingly I can ping the router. 

It is also strange that usually there is internet at the first try, but after rebooting it disappears. 

I tried to follow this guide
[http://ubuntuforums.org/showthread.php?t=1985079&highlight=wifi+connects+internet](http://ubuntuforums.org/showthread.php?t=1985079&highlight=wifi+connects+internet)
but it didn't work.

Sorry for the stupid question and thanks in advance for the answer.
```
bottyan@bottyan-VPCW21M1E:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux bottyan-VPCW21M1E 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:41:11 UTC 2013 i686 i686 i686 GNU/Linux
bottyan@bottyan-VPCW21M1E:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Sony Corporation Device [104d:9066]
    Kernel driver in use: atl1c
--
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Foxconn International, Inc. T77H126.00 802.11bgn Wireless Half-size Mini PCIe Card [105b:e017]
    Kernel driver in use: ath9k
bottyan@bottyan-VPCW21M1E:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"TP-LINK"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:E0:65:D7:DE   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:36  Invalid misc:57   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

bottyan@bottyan-VPCW21M1E:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
bottyan@bottyan-VPCW21M1E:~$ lsmod
Module                  Size  Used by
iwlwifi               348584  0 
bnep                   17708  2 
rfcomm                 37277  12 
parport_pc             31969  0 
ppdev                  12818  0 
snd_hda_codec_realtek    63496  1 
snd_hda_intel          32516  3 
joydev                 17162  0 
snd_hda_codec         111548  2 snd_hda_codec_realtek,snd_hda_intel
uvcvideo               71278  0 
coretemp               13169  0 
videobuf2_core         32071  1 uvcvideo
videodev               95842  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
microcode              18210  0 
videobuf2_memops       13213  1 videobuf2_vmalloc
snd_hwdep              13273  1 snd_hda_codec
arc4                   12474  2 
snd_pcm                80235  2 snd_hda_intel,snd_hda_codec
psmouse                84878  0 
snd_seq_midi           13133  0 
btusb                  17987  0 
serio_raw              13032  0 
ath9k                 116588  0 
lpc_ich                16926  0 
snd_rawmidi            25383  1 snd_seq_midi
bluetooth             183270  22 bnep,rfcomm,btusb
sony_laptop            64258  1 
mac80211              461203  2 iwlwifi,ath9k
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
ath9k_common           13784  1 ath9k
i915                  457247  3 
ath9k_hw              376193  2 ath9k,ath9k_common
ath                    19188  3 ath9k,ath9k_common,ath9k_hw
drm_kms_helper         47304  1 i915
mac_hid                13038  0 
cfg80211              175574  4 iwlwifi,ath9k,mac80211,ath
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   238811  4 i915,drm_kms_helper
i2c_algo_bit           13198  1 i915
video                  18848  1 i915
snd                    62146  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
sdhci_pci              18156  0 
sdhci                  27831  1 sdhci_pci
atl1c                  36176  0 



```

---

### Post by praseodym on 2013-11-09
Hi,

deactivate the hardware encryption of your Atheros driver and its power management. Finally, blacklist the Intel driver iwlwifi:
```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
sudo iwconfig wlan0 power off
echo "blacklist iwlwifi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by vidnyanszkyz on 2013-11-09
Thanks for the quick reply, but it still doesn't work. 
```
bottyan@bottyan-VPCW21M1E:~$ echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf[sudo] password for bottyan: options ath9k nohwcrypt=1
bottyan@bottyan-VPCW21M1E:~$ sudo modprobe -rfv iwlwifi
bottyan@bottyan-VPCW21M1E:~$ sudo modprobe -rfv ath9k
rmmod /lib/modules/3.5.0-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
rmmod /lib/modules/3.5.0-22-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.5.0-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
rmmod /lib/modules/3.5.0-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
rmmod /lib/modules/3.5.0-22-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.5.0-22-generic/kernel/net/wireless/cfg80211.ko
bottyan@bottyan-VPCW21M1E:~$ sudo modprobe -v ath9k
insmod /lib/modules/3.5.0-22-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.5.0-22-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.5.0-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.5.0-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.5.0-22-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1 nohwcrypt=1 nohwcrypt=1
bottyan@bottyan-VPCW21M1E:~$ sudo iwconfig wlan0 power off
bottyan@bottyan-VPCW21M1E:~$ echo "blacklist iwlwifi" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist iwlwifi







```

---

### Post by praseodym on 2013-11-10
Lets see
```

route -n
cat /etc/resolv.conf
iwlist chan
sudo iwlist scan
dmesg | grep ath9k
ifconfig wlan0
iwconfig wlan0
```

---

### Post by vidnyanszkyz on 2013-11-21
Hi, 

Sorry for not responding. 
Now I am trying to connect another network, which worked before and it can't connect.  
Many thanks.

---

### Post by praseodym on 2013-11-22
Please show the outputs mentioned above

---

### Post by vidnyanszkyz on 2013-11-23
Ok.
```
bottyan@bottyan-VPCW21M1E:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
bottyan@bottyan-VPCW21M1E:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
bottyan@bottyan-VPCW21M1E:~$ iwlist chan
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
lo        no frequency information.


eth0      no frequency information.


bottyan@bottyan-VPCW21M1E:~$ sudo iwlist scan
[sudo] password for bottyan: 
wlan0     Scan completed :
          Cell 01 - Address: 4C:72:B9:20:27:F0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"UPC974621"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000156ab5c8184
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 0009555043393734363231
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 20:CF:30:CE:0D:79
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"pszibu"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002fff2eb8fb3
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 000670737A696275
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD9B0050F204104A0001101044000102103B00010310470010DE7B1C8A2DC7F6E3C163B0891DF2DABF102100154153555354654B20436F6D707574657220496E632E1023001C57692D46692050726F74656374656420536574757020526F757465721024000652542D4E31361042000234351054000800060050F20400011011000652542D4E3136100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: F8:D1:11:24:FF:48
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"tutisanyi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000fc9e84c8
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 00097475746973616E7969
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 04 - Address: 00:25:9C:B6:01:EC
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001ee9cca2
                    Extra: Last beacon: 576ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD930050F204104A00011010440001021041000100103B000103104700100000000000000001100000259CB601EC102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30371042000C4A555430304A4143323237391054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
          Cell 05 - Address: 00:23:CD:FD:2B:F8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"GIANNIS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000d173e720
                    Extra: Last beacon: 564ms ago
                    IE: Unknown: 00074749414E4E4953
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555349010B1B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406071900000000000000000000000000000000000000
                    IE: Unknown: 3D1606071900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD830050F204104A0001101044000102103B00010310470010000000000000100000000023CDFD2BF81021000754502D4C494E4B10230009544C2D57523834314E10240003352E3010420003312E301054000800060050F20400011011001B576972656C657373204E20526F7574657220544C2D57523834314E100800020086103C000101
          Cell 06 - Address: 00:18:39:D3:E5:5F
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"private"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009fbe88186
                    Extra: Last beacon: 504ms ago
                    IE: Unknown: 000770726976617465
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030108
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020104
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 00:1C:A2:FD:EB:AC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Pannika WIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000039b24b51c1
                    Extra: Last beacon: 240ms ago
                    IE: Unknown: 000C50616E6E696B612057494649
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: 44:32:C8:2F:3C:31
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"UPC0962924"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000311f42fe18f
                    Extra: Last beacon: 264ms ago
                    IE: Unknown: 000A55504330393632393234
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: 38:22:9D:16:75:D2
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"torzi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000098fbc898c0
                    Extra: Last beacon: 600ms ago
                    IE: Unknown: 0005746F727A69
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: DD930050F204104A00011010440001021041000100103B000103104700100000000000000001100038229D1675D21021000C506972656C6C6920436F72701023000941525634353038505710240007312E3338532D4D1042000D313538303159303032313831341054000800060050F204000110110018506972656C6C692069616461622D706972656C6C692D7A7A100800020084
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
          Cell 10 - Address: C8:BE:19:AA:94:84
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"gugika"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004cbf3b3702
                    Extra: Last beacon: 804ms ago
                    IE: Unknown: 0006677567696B61
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1602000000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD8A0050F204104A0001101044000102103B0001031047001063041253101920061228C8BE19AA94841021000E442D4C696E6B2053797374656D73102300084449522D3630354C102400084449522D3630354C1042000D32303037303431332D303030311054000800060050F2040001101100084449522D3630354C1008000226881049000600372A000120
                    IE: Unknown: DD1E00904C332C181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 11 - Address: 00:1B:11:F6:28:9E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"samsung"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000378081a1c92
                    Extra: Last beacon: 636ms ago
                    IE: Unknown: 000773616D73756E67
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: 00:19:5B:95:44:BC
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"aisepy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001767849d19b
                    Extra: Last beacon: 19768ms ago
                    IE: Unknown: 0006616973657079
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
          Cell 13 - Address: F8:D1:11:41:CD:42
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"MAFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000036b6bd180
                    Extra: Last beacon: 19512ms ago
                    IE: Unknown: 00044D414649
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606071100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD3F0050F204104A00011010440001021047001000000000000010000000F8D11141CD10103C000101104900140024E26002000101600000020001600100020001
          Cell 14 - Address: 00:22:2D:05:31:E3
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"PLAN9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000d739b54813c
                    Extra: Last beacon: 19468ms ago
                    IE: Unknown: 0005504C414E39
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010002
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 15 - Address: 00:13:F7:79:93:1F
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Mcsere"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002a40927b181
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 00064D6373657265
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010D
                    IE: Unknown: 050400010000
                    IE: Unknown: 07064E4C20010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F03010000000013F779931F0213F779931F64002C010808
          Cell 16 - Address: F8:D1:11:A8:C9:04
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"czeges"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001229e2e6b0f
                    Extra: Last beacon: 624ms ago
                    IE: Unknown: 0006637A65676573
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706485520010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606071500000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD3F0050F204104A00011010440001021047001000000000000010000000F8D111A8C910103C000101104900140024E26002000101600000020001600100020001


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


bottyan@bottyan-VPCW21M1E:~$ dmesg | grep ath9k
[    8.400270] Modules linked in: videobuf2_vmalloc snd_pcm videobuf2_memops ath9k_common ath9k_hw psmouse snd_seq_midi pcspkr snd_rawmidi i2c_i801(+) btusb ath snd_seq_midi_event lpc_ich(+) serio_raw bluetooth snd_seq sony_laptop(+) snd_timer snd_seq_device cfg80211 snd i915(+) evbug mac_hid drm_kms_helper soundcore snd_page_alloc drm i2c_algo_bit video lp parport sdhci_pci sdhci atl1c
[    9.301801] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    9.303968] Registered led device: ath9k-phy0
bottyan@bottyan-VPCW21M1E:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 78:dd:08:cf:0f:3c  
          inet6 addr: fe80::7add:8ff:fecf:f3c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1968 (1.9 KB)  TX bytes:28105 (28.1 KB)


bottyan@bottyan-VPCW21M1E:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on





```

---

### Post by praseodym on 2013-11-23
You need nameservers
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo iwconfig wlan0 power off
sudo service network-manager restart
```
Which of the "Cells" is yours?

---

### Post by vidnyanszkyz on 2013-11-23
It is Cell 01.

```

bottyan@bottyan-VPCW21M1E:~$ echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
nameserver 8.8.8.8
nameserver 8.8.4.4
bottyan@bottyan-VPCW21M1E:~$ sudo iwconfig wlan0 power off
bottyan@bottyan-VPCW21M1E:~$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 6742

```

---

### Post by praseodym on 2013-11-24
The encryption looks weired. Change it to pure WPA2-AES (CCMP) instead of TKIP.

---

### Post by vidnyanszkyz on 2013-11-24
Thank you very much!

Strangely it is working, although I have never changed the configuration of the router before.

---

