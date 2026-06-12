---
title: "I cannot enable wifi card"
date: 2015-11-03
forum: Networking &amp; Wireless
---

### Post by dim6 on 2015-11-03
Hello! I have OS Ubuntu 15.10 on dell latitude 131l. 
It works perfect except the wifi card (broadcom: BCM4311 82.11b/g WLAN)
I cannot enable it. The hotkey doesn't do anything! 
Who can help me???

---

### Post by praseodym on 2015-11-03
Hi,

install the missing proprietary firmware:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot and check:
```

lsmod
ifconfig -a
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by dim6 on 2015-11-03
The problem is here...

code:
```
lsmod
Module                  Size  Used by
drbg                   28672  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
arc4                   16384  2
rt2800usb              28672  0
rt2x00usb              20480  1 rt2800usb
rt2800lib              90112  1 rt2800usb
rt2x00lib              49152  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              659456  3 rt2x00lib,rt2x00usb,rt2800lib
crc_ccitt              16384  1 rt2800lib
snd_hda_codec_idt      53248  1
ssb                    57344  1
snd_hda_codec_generic    69632  1 snd_hda_codec_idt
snd_hda_codec_hdmi     49152  1
snd_hda_intel          32768  1
mii                    16384  0
snd_hda_codec         118784  4 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           57344  5 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
wl                   6152192  1
snd_hwdep              16384  1 snd_hda_codec
snd_pcm                90112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
kvm_amd                57344  0
dell_wmi               16384  0
snd_seq_midi           16384  0
sparse_keymap          16384  1 dell_wmi
kvm                   454656  1 kvm_amd
snd_seq_midi_event     16384  1 snd_seq_midi
dell_laptop            24576  0
snd_rawmidi            28672  1 snd_seq_midi
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
dcdbas                 16384  1 dell_laptop
joydev                 20480  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
input_leds             16384  0
cfg80211              483328  3 wl,mac80211,rt2x00lib
snd                    69632  13 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
serio_raw              16384  0
edac_core              49152  0
k8temp                 16384  0
soundcore              16384  1 snd
edac_mce_amd           24576  0
i2c_piix4              20480  0
shpchp                 32768  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2
pata_acpi              16384  0
radeon               1466368  5
i2c_algo_bit           16384  1 radeon
ttm                    86016  1 radeon
drm_kms_helper        114688  1 radeon
drm                   303104  8 ttm,drm_kms_helper,radeon
psmouse               114688  0
sdhci_pci              20480  0
sdhci                  45056  1 sdhci_pci
ahci                   32768  2
pata_atiixp            16384  0
libahci                32768  1 ahci
wmi                    20480  1 dell_wmi
video                  24576  2 dell_wmi,dell_laptop
ati_agp                16384  0
```

```
ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5906 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5906 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:534619 (534.6 KB)  TX bytes:534619 (534.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0c:f6:43:a0:f7  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f6ff:fe43:a0f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1280  Metric:1
          RX packets:38031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33775 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35083185 (35.0 MB)  TX bytes:5189624 (5.1 MB)
```

```
ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5906 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5906 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:534619 (534.6 KB)  TX bytes:534619 (534.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0c:f6:43:a0:f7  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f6ff:fe43:a0f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1280  Metric:1
          RX packets:38031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33775 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35083185 (35.0 MB)  TX bytes:5189624 (5.1 MB)

d@d-Latitude-131L:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"CYTA C10A"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 38:22:9D:C3:C1:0A   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:462  Invalid misc:2962   Missed beacon:0

lo        no wireless extensions.
```

```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

```
sudo iwlist scan
[sudo] password for d: 
wlan0     Scan completed :
          Cell 01 - Address: 38:22:9D:C3:C1:0A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"CYTA C10A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000036a9dbd0c
                    Extra: Last beacon: 236ms ago
                    IE: Unknown: 0009435954412043313041
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
          Cell 02 - Address: 58:98:35:7A:46:17
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"CYTA74CC75"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e1477d92ae
                    Extra: Last beacon: 256ms ago
                    IE: Unknown: 000A43595441373443433735
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD2C0050F204104A0001101044000102105700010010470010739DE4FA85E65D3F8E38E7B0C7D2016B103C000101
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 03 - Address: 14:60:80:DA:0D:08
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"OTEda0d08"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000006a2717a
                    Extra: Last beacon: 3884ms ago
                    IE: Unknown: 00094F5445646130643038
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1602050700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050001257A12
                    IE: Unknown: DD1E00904C336E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3402050700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 04 - Address: 00:26:44:00:C5:60
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"mini"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000180e9df185
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 00046D696E69
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0017FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C330C0017FF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406000100000000000000000000000000000000000000
          Cell 05 - Address: A4:7E:39:F5:6A:D8
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"2oKAPHNIK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000357a9b624f1
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 0009326F4B4150484E494B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1607050000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050000117A12
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: DD1E00904C336E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3407050000000000000000000000000000000000000000

lo        Interface doesn't support scanning.
```

---

### Post by praseodym on 2015-11-03
Did you install the firmware? If yes, uninstall the proprietary driver and blacklist the wrongly loaded rt2800usb (or are you connected via USB-WLAN?).
```

sudo apt-get remove --purge bcmwl-kernel-source
```
Reboot. If no stick is used then run before
```

echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by dim6 on 2015-11-03
I'm now connected via usb-wlan. 
So? What i have to do now?

---

### Post by praseodym on 2015-11-03
Install the firmware and uninstall the bcmwl-package. No need to blacklist the usb driver!

---

### Post by dim6 on 2015-11-03
DID IT!!!
You're genious, 
Thank you very much!!!

---

