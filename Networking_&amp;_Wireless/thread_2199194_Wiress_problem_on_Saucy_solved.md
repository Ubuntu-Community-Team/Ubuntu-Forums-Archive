---
title: "Wiress problem on Saucy solved"
date: 2014-01-12
forum: Networking &amp; Wireless
---

### Post by rezazade on 2014-01-12
Saucy on a Dell laptop. Turned out that broadcom drivers were not included in the Linux installation: [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware)
):P

---

### Post by rezazade on 2014-01-14
No it's not solved! It stopped working. Below is the output of the relevant commands. Wicd says it can't connect to it's d-bis interface. I searched the internet and it is said that  the only was is to go back to the 3.8 kernel. Is that true?

```


**** lsb-release ****




DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.10
DISTRIB_CODENAME=saucy
DISTRIB_DESCRIPTION="Ubuntu 13.10"
-e 


**** lspci ****




08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: Dell Device [1028:02bb]
	Kernel driver in use: r8169
0e:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
	Kernel driver in use: b43-pci-bridge
-e 


**** lsusb ****




Bus 002 Device 002: ID 0c45:63e0 Microdia Sonix Integrated Webcam
Bus 002 Device 006: ID 0bc2:2312 Seagate RSS LLC 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 147e:1000 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 008 Device 014: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 008 Device 013: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 008 Device 012: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 008 Device 011: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
-e 


**** iwconfig ****




wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
-e 


**** rfkill ****




1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
-e 


**** lsmod ****




Module                  Size  Used by
nls_utf8               12557  1 
isofs                  39844  1 
usb_storage            62062  1 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69130  16 
bnep                   19704  2 
binfmt_misc            17468  1 
hid_generic            12548  0 
coretemp               13435  0 
joydev                 17377  0 
kvm                   431720  0 
usbhid                 53014  0 
hid                   105858  2 hid_generic,usbhid
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
arc4                   12608  2 
snd_hda_codec_idt      50341  1 
dell_laptop            17369  0 
dcdbas                 14847  1 dell_laptop
snd_hda_intel          48171  5 
snd_hda_codec         188738  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
microcode              23576  0 
snd_rawmidi            30095  1 snd_seq_midi
b43                   387322  0 
psmouse                97655  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
bcma                   46699  1 b43
serio_raw              13413  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
mac80211              597268  1 b43
snd                    69141  19 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
btusb                  28267  0 
cfg80211              480503  2 b43,mac80211
bluetooth             372041  22 bnep,btusb,rfcomm
lpc_ich                21080  0 
nouveau               943717  2 
mxm_wmi                13021  1 nouveau
wmi                    19070  2 mxm_wmi,nouveau
soundcore              12680  1 snd
ttm                    84169  1 nouveau
drm_kms_helper         52710  1 nouveau
drm                   297056  4 ttm,drm_kms_helper,nouveau
i2c_algo_bit           13413  1 nouveau
mac_hid                13205  0 
video                  19318  1 nouveau
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
ahci                   25819  3 
libahci                31928  1 ahci
firewire_ohci          40327  0 
firewire_core          64534  1 firewire_ohci
sdhci_pci              19014  0 
crc_itu_t              12707  1 firewire_core
sdhci                  42898  1 sdhci_pci
r8169                  67581  0 
ssb                    62057  1 b43
mii                    13934  1 r8169
-e 


**** nm-tool ****






NetworkManager Tool


State: connected (global)


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    Tele2Internet-36067: Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    TeliaGatewayA4-B1-E9-80-09-A5: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    Comviq-Wi-Fi-C6F41D: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 97 WPA
    Joa:             Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 95 WPA2
    Lyra:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA
    TeliaGatewayA4-B1-E9-7E-D0-D3: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    dlink-D886:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    TeliaGatewayA4-B1-E9-7E-DF-C5: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    B2_private_FF:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WEP




- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         46.236.121.102
    Prefix:          27 (255.255.255.224)
    Gateway:         46.236.121.97


    DNS:             80.244.65.130
    DNS:             80.244.65.3




-e 


**** NetworkManager.state ****




[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
-e 


**** NetworkManager.conf ****




[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false
-e 


**** interfaces ****




# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
-e 


**** iwlist ****




wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"dlink-D886"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009bdc251692
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000A646C696E6B2D44383836
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1013FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0502000F127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706444520010D10
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"TeliaGatewayA4-B1-E9-80-09-A5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000da2d5ffe12
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 001D54656C69614761746577617941342D42312D45392D38302D30392D4135
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD900050F204104A0001101044000102103B00010310470010209EE4FB793452D4B1D51243A8F281551021000B546563686E69636F6C6F721023000E546563686E69636F6C6F7220544710240008373939766E207632104200093132343843534A474D1054000800060050F20400011011000A5447373939766E207632100800020004103C0001011049000600372A000120
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"Comviq-Wi-Fi-C6F41D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000381ce5b748
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 0013436F6D7669712D57692D46692D433646343144
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706534500010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD630050F204104A0001101044000102103B00010310470010F4CF283CDAC052C687EAE1C73577916A102100035A544510230006415236303033102400010010420001001054000800060050F2040001101100065A54452D415010080002018C103C000101
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"Joa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000776eedf8ab1
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 00034A6F61
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AF0191BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DDAA0050F204104A0001101044000102103B00010310470010D9B846C9D1AA319149ABCCCA16532CE0102100154153555354654B20436F6D707574657220496E632E1023001C57692D46692050726F74656374656420536574757020526F757465721024000652542D4E31321042001130383A36303A36653A65323A38653A63631054000800060050F20400011011000652542D4E3132100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"Lyra"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000050012c9537a
                    Extra: Last beacon: 17124ms ago
                    IE: Unknown: 00044C797261
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"Tele2Internet-36067"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000041a4eebde6
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 001354656C6532496E7465726E65742D3336303637
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABC191AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609080000000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"TeliaGatewayA4-B1-E9-7E-D0-D3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005b94703dc3e
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 001D54656C69614761746577617941342D42312D45392D37452D44302D4433
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1E181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD900050F204104A0001101044000102103B00010310470010F3298E396A925576ADAD82906A1BFD321021000B546563686E69636F6C6F721023000E546563686E69636F6C6F7220544710240008373939766E207632104200093132343643533845361054000800060050F20400011011000A5447373939766E207632100800020004103C0001011049000600372A000120
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 08 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"B2_private_FF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001f4449521a6
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000D42325F707269766174655F4646
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 09 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"TeliaGatewayA4-B1-E9-7E-DF-C5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000776f09d7ffa
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 001D54656C69614761746577617941342D42312D45392D37452D44462D4335
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: DD900050F204104A0001101044000102103B0001031047001003A338F3823C5EAAB1582A60A8A719651021000B546563686E69636F6C6F721023000E546563686E69636F6C6F7220544710240008373939766E207632104200093132343643534136351054000800060050F20400011011000A5447373939766E207632100800020004103C0001011049000600372A000120
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00


-e 


**** resolv ****




# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
-e 


**** blacklist.conf ****




# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
-e 


**** dmesg ****




[    1.919156] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 9da89dd2daeca3a3cb171fe18502208f132adef8'
[    2.136352] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[    2.136370] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    2.136388] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    2.136401] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    2.136415] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    2.208297] ssb: Sonics Silicon Backplane found on PCI device 0000:0e:00.0
[   13.169531] wmi: Mapper loaded
[   13.385936] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   13.444220] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   25.348265] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   31.041337] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.041580] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3644.040544] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 3649.571079] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6409.820298] b43-phy0: Radio hardware status changed to DISABLED
[21147.840283] b43-phy0: Radio hardware status changed to ENABLED
[21148.032308] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[21153.567035] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
-e 


**************** done ********************





```

---

