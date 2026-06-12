---
title: "WiFi is successfuly connected but it isn't working 12.04"
date: 2013-12-01
forum: Networking &amp; Wireless
---

### Post by Thrashard on 2013-12-01
I use Ubuntu 12.04 (alongside with Windows 8.1) on my Toshiba Satellite L855. Everything had been working fine 'till today. Now it successfuly connects to wifi connection but it just isn't working. No settings were changed. On win 8.1 wifi works well. It would be nice if you help me. 

```
arnas@arnas-L855:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Internetas"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:33:F4:76:96   
          Bit Rate=18 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:65   Missed beacon:0
```

```
arnas@arnas-L855:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"Internetas"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:33:F4:76:96   
          Bit Rate=18 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:65   Missed beacon:0
```

---

### Post by praseodym on 2013-12-01
Please show
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig wlan0
rfkill list
```

---

### Post by Thrashard on 2013-12-01
```
arnas@arnas-L855:~$ lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
 Subsystem: Toshiba America Info Systems Device [1179:ff1e]
 Kernel driver in use: alx
--
08:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
 Subsystem: Askey Computer Corp. Device [144f:7193]
 Kernel driver in use: ath9k
arnas@arnas-L855:~$ 
arnas@arnas-L855:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0930:0219 Toshiba Corp. 
Bus 001 Device 004: ID 10f1:1a43 Importek 
arnas@arnas-L855:~$ 
arnas@arnas-L855:~$ lsmod
Module                  Size  Used by
bnep                   18258  2 
rfcomm                 47864  0 
parport_pc             28284  0 
ppdev                  17113  0 
ath3k                  12968  0 
btusb                  22431  0 
bluetooth             247165  15 bnep,rfcomm,ath3k,btusb
nls_iso8859_1          12713  1 
coretemp               13596  0 
joydev                 17613  0 
kvm_intel             137899  0 
kvm                   455932  1 kvm_intel
radeon                965260  3 
snd_hda_codec_hdmi     37463  1 
snd_hda_codec_realtek    79916  1 
ghash_clmulni_intel    13259  0 
aesni_intel            55495  0 
uvcvideo               82214  0 
snd_hda_intel          44339  5 
snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
ttm                    84051  1 radeon
rts5139               351018  0 
ablk_helper            13597  1 aesni_intel
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hwdep              13668  1 snd_hda_codec
lrw                    13294  1 aesni_intel
videobuf2_core         40785  1 uvcvideo
drm_kms_helper         49597  1 radeon
psmouse                97873  0 
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videodev              130053  2 uvcvideo,videobuf2_core
alx                    73230  0 
drm                   287564  5 radeon,ttm,drm_kms_helper
mei                    41820  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
aes_x86_64             17255  1 aesni_intel
arc4                   12573  2 
xts                    12922  1 aesni_intel
ath9k                 100942  0 
mdio                   13807  1 alx
toshiba_bluetooth      12852  0 
gf128mul               14951  2 lrw,xts
mac80211              557615  1 ath9k
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
mac_hid                13253  0 
i2c_algo_bit           13564  1 radeon
video                  19652  0 
serio_raw              13215  0 
ath9k_common           13858  1 ath9k
ath9k_hw              409885  2 ath9k,ath9k_common
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
microcode              23017  0 
lpc_ich                17144  0 
cfg80211              540735  3 ath9k,mac80211,ath
snd                    69533  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
compat                 15085  5 ath9k,mac80211,ath9k_common,ath9k_hw,cfg80211
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_generic            12540  0 
usbhid                 47346  0 
hid                   105826  2 hid_generic,usbhid
ahci                   25879  4 
libahci                31606  1 ahci
arnas@arnas-L855:~$ 
arnas@arnas-L855:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 24:ec:99:d5:e6:a2  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::26ec:99ff:fed5:e6a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:92326 (92.3 KB)  TX bytes:11010 (11.0 KB)

arnas@arnas-L855:~$ 
arnas@arnas-L855:~$ rfkill list
0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: no
1: hci0: Bluetooth
 Soft blocked: yes
 Hard blocked: noarnas@arnas-L855:~$ lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
 Subsystem: Toshiba America Info Systems Device [1179:ff1e]
 Kernel driver in use: alx
--
08:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
 Subsystem: Askey Computer Corp. Device [144f:7193]
 Kernel driver in use: ath9k
arnas@arnas-L855:~$ 
arnas@arnas-L855:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0930:0219 Toshiba Corp. 
Bus 001 Device 004: ID 10f1:1a43 Importek 
arnas@arnas-L855:~$ 
arnas@arnas-L855:~$ lsmod
Module                  Size  Used by
bnep                   18258  2 
rfcomm                 47864  0 
parport_pc             28284  0 
ppdev                  17113  0 
ath3k                  12968  0 
btusb                  22431  0 
bluetooth             247165  15 bnep,rfcomm,ath3k,btusb
nls_iso8859_1          12713  1 
coretemp               13596  0 
joydev                 17613  0 
kvm_intel             137899  0 
kvm                   455932  1 kvm_intel
radeon                965260  3 
snd_hda_codec_hdmi     37463  1 
snd_hda_codec_realtek    79916  1 
ghash_clmulni_intel    13259  0 
aesni_intel            55495  0 
uvcvideo               82214  0 
snd_hda_intel          44339  5 
snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
ttm                    84051  1 radeon
rts5139               351018  0 
ablk_helper            13597  1 aesni_intel
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hwdep              13668  1 snd_hda_codec
lrw                    13294  1 aesni_intel
videobuf2_core         40785  1 uvcvideo
drm_kms_helper         49597  1 radeon
psmouse                97873  0 
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videodev              130053  2 uvcvideo,videobuf2_core
alx                    73230  0 
drm                   287564  5 radeon,ttm,drm_kms_helper
mei                    41820  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
aes_x86_64             17255  1 aesni_intel
arc4                   12573  2 
xts                    12922  1 aesni_intel
ath9k                 100942  0 
mdio                   13807  1 alx
toshiba_bluetooth      12852  0 
gf128mul               14951  2 lrw,xts
mac80211              557615  1 ath9k
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
mac_hid                13253  0 
i2c_algo_bit           13564  1 radeon
video                  19652  0 
serio_raw              13215  0 
ath9k_common           13858  1 ath9k
ath9k_hw              409885  2 ath9k,ath9k_common
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
microcode              23017  0 
lpc_ich                17144  0 
cfg80211              540735  3 ath9k,mac80211,ath
snd                    69533  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
compat                 15085  5 ath9k,mac80211,ath9k_common,ath9k_hw,cfg80211
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_generic            12540  0 
usbhid                 47346  0 
hid                   105826  2 hid_generic,usbhid
ahci                   25879  4 
libahci                31606  1 ahci
arnas@arnas-L855:~$ 
arnas@arnas-L855:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 24:ec:99:d5:e6:a2  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::26ec:99ff:fed5:e6a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:92326 (92.3 KB)  TX bytes:11010 (11.0 KB)

arnas@arnas-L855:~$ 
arnas@arnas-L855:~$ rfkill list
0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: no
1: hci0: Bluetooth
 Soft blocked: yes
 Hard blocked: no
```

---

### Post by praseodym on 2013-12-01
Deactivate the hardware encryption of the driver
```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by Thrashard on 2013-12-01
```
options ath9k nohwcrypt=1
```

Did it but nothing changed

P.S.: I have just tried to connect through Wired lan. It doesn't work too. Says that Connection Established but there are no internet.

---

### Post by praseodym on 2013-12-01
Ok, now lets see:

```
iwlist chan
sudo iwlist scan
route -n
cat /etc/resolv.conf
```

---

### Post by Thrashard on 2013-12-01
```
arnas@arnas-L855:~$ iwlist chan
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
          Current Frequency:2.437 GHz (Channel 6)

arnas@arnas-L855:~$ 
arnas@arnas-L855:~$ sudo iwlist scan
[sudo] password for arnas: 

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:22:33:F4:76:96
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"Internetas"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001b28353e9
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 000A496E7465726E65746173
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:22:33:39:DE:6F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"TEO-39DE6E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000096549e918
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 000A54454F2D333944453645
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180203F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 64:87:D7:8E:1C:2F
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"xinternetx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001451694fdb
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 000A78696E7465726E657478
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
```

---

### Post by praseodym on 2013-12-01
Can you change from WPA to pure WPA2-AES encryption in your router? Check the manual

---

