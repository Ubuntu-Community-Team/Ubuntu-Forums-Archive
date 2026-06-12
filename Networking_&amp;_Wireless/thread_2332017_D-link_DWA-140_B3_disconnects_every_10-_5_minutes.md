---
title: "D-link DWA-140 B3 disconnects every 10- 5 minutes"
date: 2016-07-27
forum: Networking &amp; Wireless
---

### Post by Karolina.K on 2016-07-27
Hello,

my dlink dwa 140 wireless adapter disconnects every 10 - 5 minutes sometimes it lasts longer, but then it disconnects. very annoying, with windows running on the same computer and same network card it works without any problem. (now i only have ubuntu 16.04 though )

what should i do to fix this? i have tried searching other threads but havent found anything since most are very old.

/karolina

---

### Post by QDR06VV9 on 2016-07-27
See if you have seen this yet..But it will not work with DWA-140 B1 this is an older thread but i have heard it still works.
[http://askubuntu.com/questions/131768/dlink-wireless-dwa-140-speeds-are-crippled-on-12-04](http://askubuntu.com/questions/131768/dlink-wireless-dwa-140-speeds-are-crippled-on-12-04)

---

### Post by Karolina.K on 2016-07-27
it doesn't seem to work :(

---

### Post by QDR06VV9 on 2016-07-27
Well sorry about that:(..Hang in here, we have a couple of networking gurus that will assist If they can.
Cheers and good luck.

---

### Post by Karolina.K on 2016-07-28
anyone know what to do? :)

---

### Post by praseodym on 2016-07-29
Lets check
```

lsusb
lsmod
iwconfig
ifconfig -a
iwlist chan
sudo iwlist scan
```

---

### Post by Karolina.K on 2016-07-29
Hej

thanks :) Okej this is what the different commands show :) 

```
$ lsusb
Bus 002 Device 006: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 005: ID 045e:0719 Microsoft Corp. Xbox 360 Wireless Adapter
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 2001:3c15 D-Link Corp. DWA-140 RangeBooster N Adapter(rev.B3) [Ralink RT5372]
Bus 001 Device 003: ID 13fd:2040 Initio Corporation 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```
$ lsmod
Module                  Size  Used by
nls_iso8859_1          16384  0
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  2
ccm                    20480  2
arc4                   16384  2
rt2800usb              28672  0
rt2x00usb              24576  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              737280  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              565248  2 mac80211,rt2x00lib
crc_ccitt              16384  1 rt2800lib
nvidia_uvm            696320  0
uvcvideo               90112  0
nvidia_modeset        745472  4
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
snd_usb_audio         176128  1
media                  24576  2 uvcvideo,videodev
snd_usbmidi_lib        36864  1 snd_usb_audio
xpad                   24576  0
joydev                 20480  0
input_leds             16384  0
ff_memless             16384  1 xpad
gpio_ich               16384  0
snd_hda_codec_hdmi     53248  4
nvidia              10076160  77 nvidia_modeset,nvidia_uvm
snd_hda_codec_realtek    86016  1
intel_powerclamp       16384  0
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
coretemp               16384  0
snd_seq_midi           16384  0
snd_hda_intel          36864  5
snd_seq_midi_event     16384  1 snd_seq_midi
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_rawmidi            32768  2 snd_usbmidi_lib,snd_seq_midi
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
kvm                   536576  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_hwdep              16384  2 snd_usb_audio,snd_hda_codec
snd_pcm               106496  5 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
irqbypass              16384  1 kvm
snd_timer              32768  2 snd_pcm,snd_seq
drm                   360448  3 nvidia
serio_raw              16384  0
snd                    81920  25 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
wmi                    20480  0
soundcore              16384  1 snd
lpc_ich                24576  0
shpchp                 36864  0
mei_me                 36864  0
mei                    98304  1 mei_me
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
uas                    24576  0
hid_logitech_hidpp     20480  0
hid_logitech_dj        20480  0
usbhid                 49152  0
hid                   118784  5 usbhid,hid_logitech_dj,hid_logitech_hidpp
usb_storage            69632  1 uas
psmouse               126976  0
firewire_ohci          40960  0
firewire_core          65536  1 firewire_ohci
crc_itu_t              16384  1 firewire_core
r8169                  81920  0
ahci                   36864  2
mii                    16384  1 r8169
libahci                32768  1 ahci
fjes                   28672  0
```
```
$ iwconfig
enp2s0    no wireless extensions.


lo        no wireless extensions.


wlxbcf685ae35cd  IEEE 802.11bgn  ESSID:"GACKT"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: F8:32:E4:43:CA:38   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=33/70  Signal level=-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:3   Missed beacon:0
```
```
$ ifconfig -a
enp2s0    Link encap:Ethernet  HWaddr 6c:62:6d:03:02:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:9920 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9920 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1347219 (1.3 MB)  TX bytes:1347219 (1.3 MB)


wlxbcf685ae35cd Link encap:Ethernet  HWaddr bc:f6:85:ae:35:cd  
          inet addr:192.168.1.141  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::35f9:ed97:29d4:9bbe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:693144 errors:0 dropped:2 overruns:0 frame:0
          TX packets:462955 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:837854773 (837.8 MB)  TX bytes:59863439 (59.8 MB)


```
```
$ iwlist chan
enp2s0    no frequency information.


lo        no frequency information.


wlxbcf685ae35cd  14 channels in total; available frequencies :
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


```
```
$ sudo iwlist scan
[sudo] password for karolina: 
enp2s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlxbcf685ae35cd  Scan completed :
          Cell 01 - Address: F8:32:E4:43:CA:38
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"GACKT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000123bcd136b5f
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00054741434B54
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DDAE0050F204104A0001101044000102103B00010310470010FF9E0699EBB8B041622CAD1370023A9E102100154153555354654B20436F6D707574657220496E632E1023001C57692D46692050726F74656374656420536574757020526F757465721024000852542D4E313244311042001166383A33323A65343A34333A63613A33381054000800060050F20400011011000852542D4E31324431100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180207F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 30:91:8F:EF:F5:EB
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"TN_24GHz_EFF5EB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004dadd52428
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000F544E5F323447487A5F454646354542
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C121860
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 46053208010000
                    IE: Unknown: 2D1A1C081BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: 7F080400080000000040
                    IE: Unknown: DD950050F204104A0001101044000102103B00010310470010E334EA88DFEF5C2C90E855CC882654441021000B546563686E69636F6C6F721023000E4D65646961416363657373205447102400073738346E207633104200093135323053414E414E1054000800060050F204000110110015546563686E69636F6C6F722054473738346E20763310080002200C1049000600372A000120
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
          Cell 03 - Address: C8:BE:19:5F:0D:32
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"dlink-0D32"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000087aa90c1d47
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000A646C696E6B2D30443332
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1013FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601000600000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020028127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706444520010D10
                    IE: Unknown: DD8C0050F204104A00011010440001021057000101103B00010310470010BC329E001DD811B28601C8BE195F0D3210210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400084449522D3633364C1042000830303030303030301054000800060050F2040001101100084449522D3633364C10080002208C103C0001011049000600372A000120
          Cell 04 - Address: 20:4E:7F:78:11:06
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"LillenBa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001e1bcd80
                    Extra: Last beacon: 204ms ago
                    IE: Unknown: 00084C696C6C656E4261
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322FDD
                    IE: Unknown: DD1E00904C33CE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406051900000000000000000000000000000000000000
                    IE: Unknown: 3D1606051900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD270050F204104A00011010440001021047001000000000000010000000204E7F781106103C000103
          Cell 05 - Address: 94:44:52:EA:77:B7
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"belkin.57b7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000047a4f11bf9
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000B62656C6B696E2E35376237
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16060D0400000000000000000000000000000000000000
                    IE: Unknown: DD9D0050F204104A00011010440001021041000100103B00010310470010E544CEFF71AF0CC48B8C9FB51BC3F63F1021001442656C6B696E20496E7465726E6174696F6E616C1023000A4637443433303120763110240007312E30302E33301042000E31323130353047343130333939361054000800060050F204000110110018506C6179204D617820576972656C65737320526F75746572100800020084
                    IE: Unknown: DD090010180204F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060D0400000000000000000000000000000000000000
          Cell 06 - Address: FA:8F:CA:70:73:7D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000123bcd3d2142
                    Extra: Last beacon: 176ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: F4:F2:6D:D7:2F:90
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"bahnhof-376650"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000424148eebc
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000E6261686E686F662D333736363530
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1603050500000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010034127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706534520010D10
          Cell 08 - Address: C0:3F:0E:10:B6:EC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"6120"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000017c74f5c127
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000436313230
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: 30:46:9A:82:13:92
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"ASUSJOD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000e5f322f65ca
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0007415355534A4F44
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B0001031047001084726F8869E6045EC3374D338A99500F1021000D4E4554474541522C20496E632E10230009574E5232303030763210240009574E523230303076321042000230311054000800060050F2040001101100074A4F4455505045100800020084103C000101
                    IE: Unknown: DD090010180207F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081500000000000000000000000000000000000000
          Cell 10 - Address: B8:A3:86:55:3E:DB
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000011b0d3314358
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160D070500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501000C127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C33EE1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340D070500000000000000000000000000000000000000
                    IE: Unknown: DD940050F204104A0001101044000102103B000103104700102880288028801880A880B8A386553EDB10210006442D4C696E6B10230020506F7765726C696E6520415620576972656C657373204E20457874656E6465721024000A4448502D5733303641561042000831323334353637381054000800060050F20400011011000A4448502D573330364156100800020084103C000101
```

---

### Post by praseodym on 2016-07-29
Try deactivating the power management:
```

sudo iwconfig wlxbcf685ae35cd power off
```
Which country do you live? Adjust the country code settings, too.

For example, for Germany (DE):

```
sudo sed -i "s/REGDOMAIN=/REGDOMAIN=[COLOR="#FF0000"]DE[/COLOR]/g" /etc/default/crda 
```
Reboot

---

### Post by Karolina.K on 2016-07-29
i live in sweden , so i guess i just substitute with SE ?

---

### Post by praseodym on 2016-07-29
Exactly:

[https://en.wikipedia.org/wiki/ISO_3166-1](https://en.wikipedia.org/wiki/ISO_3166-1)

---

### Post by Karolina.K on 2016-07-29
Okay :) did the commands, hope it works, i guess only time will tell :)

---

### Post by Karolina.K on 2016-07-29
unfortunately it doesnt work :( now it started disconnecting again all the time :/

---

### Post by praseodym on 2016-07-29
Deactivate the hardware encryption:
```

echo "options rt2800usb nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800usb.conf
```
Reboot

---

### Post by Karolina.K on 2016-07-30
Okay I tried it, while it is better (now only disconnecting every other hour or so, ) it is still disconnecting :(

---

### Post by praseodym on 2016-07-31
You may also try to reduce the bandwidth in the router from 20/40MHz to 20MHz, could be too much traffic, i.e. interferences.

---

### Post by Karolina.K on 2016-07-31
Ah okay how do I do this?

---

### Post by praseodym on 2016-07-31
Enter the router interface, see the manual for this

---

