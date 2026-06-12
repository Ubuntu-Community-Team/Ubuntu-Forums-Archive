---
title: "Wifi Autoconnect Issue"
date: 2014-03-11
forum: Networking &amp; Wireless
---

### Post by smdubinsky on 2014-03-11
When I resume from suspend or turn my computer on, the wifi will no longer autoconnect.  I have to manually select a network to connect to.  The "automatically connect to this network" box is checked on the networks.  I just upgraded to 13.10 from 13.04.

---

### Post by Hadaka on 2014-03-11
Hi, let's take a look at some stuff and see if we can fix this.
please do and post..
```
lspci -nnk | egrep '0200|0280'
```
thanks

---

### Post by smdubinsky on 2014-03-11
output: "00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 05)"

Thanks!

---

### Post by varunendra on 2014-03-11
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by smdubinsky on 2014-03-11
```



*************** info trace ***************


***** uname -a *****


Linux deus-ex 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy


***** lspci *****


00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 05)
    Subsystem: Dell Latitude E6410 [1028:040a]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
    Subsystem: Dell Wireless 1520 Half-size Mini PCIe Card [1028:000e]
    Kernel driver in use: bcma-pci-bridge


***** lsusb *****


Bus 002 Device 004: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 002 Device 003: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:1814 Ricoh Co., Ltd HD Webcam
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11abgn  ESSID:"umd-secure"  
          Mode:Managed  Frequency:5.2 GHz  Access Point: <MAC address removed>   
          Bit Rate=86.7 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:14   Missed beacon:0




***** rfkill *****


1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
13: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no


***** iw reg get *****


country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)


***** route -n *****


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.108.64.1     0.0.0.0         UG    0      0        0 wlan0
10.108.64.0     0.0.0.0         255.255.240.0   U     9      0        0 wlan0


***** lsmod *****


brcmsmac              550698  0 
cordic                 12574  1 brcmsmac
brcmutil               14755  1 brcmsmac
mac80211              606457  1 brcmsmac
cfg80211              510937  2 brcmsmac,mac80211
bcma                   41051  1 brcmsmac


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [umd-secure] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           86 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    umd-dev:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    umd-dev:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    umd-secure:      Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2 Enterprise
    umd-dev:         Infra, <MAC address removed>, Freq 5240 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    eduroam:         Infra, <MAC address removed>, Freq 5240 MHz, Rate 54 Mb/s, Strength 47 WPA2 Enterprise
    umd-dev:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    umd-dev:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    umd-dev:         Infra, <MAC address removed>, Freq 5200 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    WillWifi:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WEP
    umd:             Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60
    SETUP:           Ad-Hoc, <MAC address removed>, Freq 2462 MHz, Rate 11 Mb/s, Strength 65
    umd:             Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 50
    umd:             Infra, <MAC address removed>, Freq 5240 MHz, Rate 54 Mb/s, Strength 47
    umd:             Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60
    umd:             Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54
    umd:             Infra, <MAC address removed>, Freq 5200 MHz, Rate 54 Mb/s, Strength 44
    HP08C1F0:        Ad-Hoc, <MAC address removed>, Freq 2457 MHz, Rate 11 Mb/s, Strength 20
    eduroam:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    hpsetup:         Ad-Hoc, <MAC address removed>, Freq 2437 MHz, Rate 11 Mb/s, Strength 25
    umd-secure:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2 Enterprise
    umd-secure:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2 Enterprise
    umd-dev:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    eduroam:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    HP-Print-73-Photosmart 5520: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    umd-secure:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2 Enterprise
    umd-dev:         Infra, <MAC address removed>, Freq 5200 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    eduroam:         Infra, <MAC address removed>, Freq 5200 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    umd-dev:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    umd-secure:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 5200 MHz, Rate 54 Mb/s, Strength 60 WPA2 Enterprise
    umd-dev:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    eduroam:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 52 WPA2 Enterprise
    Haley's Chromecast: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24
    eduroam:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2 Enterprise
    umd-dev:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA2 Enterprise
    umd:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39
    umd-secure:      Infra, <MAC address removed>, Freq 5200 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2 Enterprise
    umd:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52
    umd:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39
    umd:             Infra, <MAC address removed>, Freq 5200 MHz, Rate 54 Mb/s, Strength 30
    umd:             Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52
    umd-secure:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2 Enterprise
    umd-dev:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    eduroam:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    umd-secure:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA2 Enterprise
    umd-secure:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2 Enterprise
    umd:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22
    umd-dev:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    eduroam:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2 Enterprise
    umd-secure:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2 Enterprise
    umd-secure:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA2 Enterprise
    umd:             Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24
    eduroam:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 WPA2 Enterprise
    umd-secure:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2 Enterprise
    umd-secure:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2 Enterprise
    umd-secure:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2 Enterprise
    umd-secure:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2 Enterprise
    umd-dev:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    umd:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22
    umd-secure:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2 Enterprise
    umd-dev:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    umd-dev:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    umd-secure:      Infra, <MAC address removed>, Freq 5240 MHz, Rate 54 Mb/s, Strength 46 WPA WPA2 Enterprise
    *umd-secure:     Infra, <MAC address removed>, Freq 5200 MHz, Rate 54 Mb/s, Strength 53 WPA WPA2 Enterprise
    umd:             Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19


  IPv4 Settings:
    Address:         10.108.66.170
    Prefix:          20 (255.255.240.0)
    Gateway:         10.108.64.1


    DNS:             128.8.76.2
    DNS:             128.8.74.2




- Device: eth3 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         off






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f714920b2
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 0107129824B048606C
                    IE: Unknown: 071255532024041134041864051884031895051E
                    IE: Unknown: 0B050600138D5B
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D1628080400000000000000000000000000000000000000
                    IE: Unknown: 851E04008F000F00FF0359003939362D33612D61703134303500000006000035
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 02 - Address: <MAC address removed>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"umd-dev"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f71494d68
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0007756D642D646576
                    IE: Unknown: 0107129824B048606C
                    IE: Unknown: 071255532024041134041864051884031895051E
                    IE: Unknown: 0B050600138D5B
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3D1628080400000000000000000000000000000000000000
                    IE: Unknown: 851E04008F000F00FF0359003939362D33612D61703134303500000006000035
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 03 - Address: <MAC address removed>
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"umd-secure"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f638522b2
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000A756D642D736563757265
                    IE: Unknown: 0107129824B048606C
                    IE: Unknown: 071255532024041134041864051884031895051E
                    IE: Unknown: 0B050400058D5B
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D1630080400000000000000000000000000000000000000
                    IE: Unknown: 851E03008F000F00FF0359003939362D33612D61703133303700000004000035
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 04 - Address: <MAC address removed>
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"umd-dev"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f6384f4c7
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0007756D642D646576
                    IE: Unknown: 0107129824B048606C
                    IE: Unknown: 071255532024041134041864051884031895051E
                    IE: Unknown: 0B050400058D5B
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3D1630080400000000000000000000000000000000000000
                    IE: Unknown: 851E03008F000F00FF0359003939362D33612D61703133303700000004000035
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"umd-secure"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f638ec46c
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000A756D642D736563757265
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050A00778D5B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 851E05008F000F00FF0359003939362D33612D6170313330370000000A000036
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 06 - Address: <MAC address removed>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"umd-secure"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f7147e306
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000A756D642D736563757265
                    IE: Unknown: 0107129824B048606C
                    IE: Unknown: 071255532024041134041864051884031895051E
                    IE: Unknown: 0B050600138D5B
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D1628080400000000000000000000000000000000000000
                    IE: Unknown: 851E04008F000F00FF0359003939362D33612D61703134303500000006000035
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 07 - Address: <MAC address removed>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"umd"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f714840ea
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0003756D64
                    IE: Unknown: 0107129824B048606C
                    IE: Unknown: 071255532024041134041864051884031895051E
                    IE: Unknown: 0B050600138D5B
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1628080400000000000000000000000000000000000000
                    IE: Unknown: 851E04008F000F00FF0359003939362D33612D61703134303500000006000035
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 08 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"SETUP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000002b69d87a834
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00055345545550
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 06020000
                    IE: Unknown: DD09001018020000010000
          Cell 09 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f715408a7
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050A008E8D5B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 851E08008F000F00FF0359003939362D33612D6170313430350000000A000036
                    IE: Unknown: 9606004096000E00
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 10 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"umd-dev"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f71543492
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0007756D642D646576
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050A008E8D5B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 851E08008F000F00FF0359003939362D33612D6170313430350000000A000036
                    IE: Unknown: 9606004096000E00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 11 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"umd-secure"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f71545ab6
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000A756D642D736563757265
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050A008E8D5B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 851E08008F000F00FF0359003939362D33612D6170313430350000000A000036
                    IE: Unknown: 9606004096000E00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 12 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"Haley's Chromecast"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f470db142
                    Extra: Last beacon: 17736ms ago
                    IE: Unknown: 001248616C65792773204368726F6D6563617374
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0C1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1601000100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 13 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"umd-secure"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f4a5d1dde
                    Extra: Last beacon: 13496ms ago
                    IE: Unknown: 000A756D642D736563757265
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B051500538D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D1601000F00000000000000000000000000000000000000
                    IE: Unknown: 851E07008F000F00FF0359003939362D33612D6170313130350000001500003A
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 14 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f4b2a4b5b
                    Extra: Last beacon: 4228ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B0515009F8D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D1601000F00000000000000000000000000000000000000
                    IE: Unknown: 851E0D008F000F00FF0359003939362D33612D6170313130350000001500003A
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 15 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"umd-dev"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f62e278d9
                    Extra: Last beacon: 17704ms ago
                    IE: Unknown: 0007756D642D646576
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B0511006A8D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 851E03008F000F00FF0359003939362D33612D61703132303500000011000036
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 16 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f52d298d8
                    Extra: Last beacon: 17692ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050700010000000000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B0510004F8D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 851E09008F000F00FF0359003939362D33612D61703135303300000010000036
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 17 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"umd"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f47dc0640
                    Extra: Last beacon: 4208ms ago
                    IE: Unknown: 0003756D64
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050700010000000000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B051F00898D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 851E0E008F000F00FF0359003939362D33622D6170313430390000001F000036
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 18 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:off
                    ESSID:"umd"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f649bf2ac
                    Extra: Last beacon: 3960ms ago
                    IE: Unknown: 0003756D64
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 050700010000000000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B051300C08D5B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000700000000000000000000000000000000000000
                    IE: Unknown: 851E10008F000F00FF0359003939362D33612D61703135303700000013000036
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 19 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"umd-secure"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f649bf190
                    Extra: Last beacon: 3936ms ago
                    IE: Unknown: 000A756D642D736563757265
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B051400CE8D5B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D1606000700000000000000000000000000000000000000
                    IE: Unknown: 851E10008F000F00FF0359003939362D33612D61703135303700000014000036
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 20 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"WillWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000002e965c2
                    Extra: Last beacon: 17304ms ago
                    IE: Unknown: 000857696C6C57696669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 070C55532001021B0307140A021B
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 21 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:off
                    ESSID:"umd"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f638d70dc
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0003756D64
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050A00778D5B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 851E05008F000F00FF0359003939362D33612D6170313330370000000A000036
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 22 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f64977b01
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 0107129824B048606C
                    IE: Unknown: 071255532024041134041864051884031895051E
                    IE: Unknown: 0B0503000B8D5B
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D1624080400000000000000000000000000000000000000
                    IE: Unknown: 851E05008F000F00FF0359003939362D33612D61703135303700000003000035
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 23 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"umd-secure"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f6497d5d9
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000A756D642D736563757265
                    IE: Unknown: 0107129824B048606C
                    IE: Unknown: 071255532024041134041864051884031895051E
                    IE: Unknown: 0B0503000B8D5B
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D1624080400000000000000000000000000000000000000
                    IE: Unknown: 851E05008F000F00FF0359003939362D33612D61703135303700000003000035
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 24 - Address: <MAC address removed>
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"umd"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f638580ab
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0003756D64
                    IE: Unknown: 0107129824B048606C
                    IE: Unknown: 071255532024041134041864051884031895051E
                    IE: Unknown: 0B050400058D5B
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1630080400000000000000000000000000000000000000
                    IE: Unknown: 851E03008F000F00FF0359003939362D33612D61703133303700000004000035
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 25 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"umd-dev"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f6fc33f69
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0007756D642D646576
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050A00C28D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 851E2D008F000F00FF03590031362D30632D617033313037000000000A000036
                    IE: Unknown: 9606004096001100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 26 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"hpsetup"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000078ea2987170
                    Extra: Last beacon: 3968ms ago
                    IE: Unknown: 000768707365747570
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 27 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"umd"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f7050264d
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0003756D64
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050E00618D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 851E0C008F000F00FF0359003939362D33612D6170313330300000000E000036
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 28 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"umd-secure"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f704fc8c6
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000A756D642D736563757265
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050E00618D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 851E0C008F000F00FF0359003939362D33612D6170313330300000000E000036
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 29 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"umd-dev"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f70513db1
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0007756D642D646576
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050E00618D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 851E0C008F000F00FF0359003939362D33612D6170313330300000000E000036
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 30 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f70511150
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050E00618D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 851E0C008F000F00FF0359003939362D33612D6170313330300000000E000036
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 31 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"HP08C1F0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000013319075cc1
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00084850303843314630
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010A
                    IE: Unknown: 06020000
                    IE: Unknown: 0706555320010B14
          Cell 32 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:off
                    ESSID:"umd"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f71549017
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0003756D64
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050A008E8D5B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 851E08008F000F00FF0359003939362D33612D6170313430350000000A000036
                    IE: Unknown: 9606004096000E00
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 33 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"umd-dev"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f638e9749
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0007756D642D646576
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050A00778D5B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 851E05008F000F00FF0359003939362D33612D6170313330370000000A000036
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 34 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f638e6ed0
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050A00778D5B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 851E05008F000F00FF0359003939362D33612D6170313330370000000A000036
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 35 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"umd"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f6498339f
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0003756D64
                    IE: Unknown: 0107129824B048606C
                    IE: Unknown: 071255532024041134041864051884031895051E
                    IE: Unknown: 0B0503000B8D5B
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624080400000000000000000000000000000000000000
                    IE: Unknown: 851E05008F000F00FF0359003939362D33612D61703135303700000003000035
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 36 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"umd-dev"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f6497a837
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0007756D642D646576
                    IE: Unknown: 0107129824B048606C
                    IE: Unknown: 071255532024041134041864051884031895051E
                    IE: Unknown: 0B0503000B8D5B
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3D1624080400000000000000000000000000000000000000
                    IE: Unknown: 851E05008F000F00FF0359003939362D33612D61703135303700000003000035
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 37 - Address: <MAC address removed>
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f6384c70f
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 0107129824B048606C
                    IE: Unknown: 071255532024041134041864051884031895051E
                    IE: Unknown: 0B050400058D5B
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D1630080400000000000000000000000000000000000000
                    IE: Unknown: 851E03008F000F00FF0359003939362D33612D61703133303700000004000035
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400




***** resolv.conf *****


nameserver 127.0.1.1
search umd.edu


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** modinfo *****


filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DCFCFF03DB5656E4F6EBB6F
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 


filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     91AD18A369EC5A3CB1923DE
depends:        
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 


filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F7A1658A8CB1D58E3D347C1
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"


***** dmesg *****


[52316.491427] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 8
[52473.171937] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[52473.171951] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[52473.171956] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[52473.174882] wlan0: authenticate with <MAC address removed>
[52473.174980] wlan0: send auth to <MAC address removed> (try 1/3)
[52473.177124] wlan0: authenticated
[52473.180991] wlan0: associate with <MAC address removed> (try 1/3)
[52473.184698] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=194)
[52473.185224] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[52473.185235] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[52473.185241] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[52473.186306] wlan0: associated
[52913.190274] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[53021.961680] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[53021.961693] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[53021.961696] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[53021.962272] wlan0: authenticate with <MAC address removed>
[53021.962365] wlan0: send auth to <MAC address removed> (try 1/3)
[53021.963929] wlan0: authenticated
[53021.966427] wlan0: associate with <MAC address removed> (try 1/3)
[53021.969831] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=16)
[53021.970405] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[53021.970411] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[53021.970414] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[53021.971427] wlan0: associated
[53137.217174] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[54232.644439] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 36
[54232.644612] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 36
[54232.644681] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 36
[54791.266318] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[54791.550711] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[54791.550727] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[54791.550732] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[54797.550519] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[54797.550539] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[54797.552431] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[54850.460918] wlan0: authenticate with <MAC address removed>
[54850.481409] wlan0: send auth to <MAC address removed> (try 1/3)
[54850.682282] wlan0: send auth to <MAC address removed> (try 2/3)
[54850.682955] wlan0: authenticated
[54850.686287] wlan0: associate with <MAC address removed> (try 1/3)
[54850.688330] wlan0: RX AssocResp from <MAC address removed> (capab=0x111 status=0 aid=4)
[54850.688850] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[54850.688858] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[54850.688862] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[54850.688875] wlan0: associated
[54850.688887] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[54858.020332] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[54886.892058] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[54886.892073] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[54886.892078] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[54886.892615] wlan0: authenticate with <MAC address removed>
[54886.904946] wlan0: send auth to <MAC address removed> (try 1/3)
[54886.906308] wlan0: authenticated
[54886.913529] wlan0: associate with <MAC address removed> (try 1/3)
[54886.917166] wlan0: RX AssocResp from <MAC address removed> (capab=0x31 status=0 aid=45)
[54886.917694] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[54886.917700] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[54886.917703] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[54886.918720] wlan0: associated
[55124.526102] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[55124.526115] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[55124.526118] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[55124.526670] wlan0: authenticate with <MAC address removed>
[55124.528545] wlan0: send auth to <MAC address removed> (try 1/3)
[55124.532441] wlan0: authenticated
[55124.534091] wlan0: associate with <MAC address removed> (try 1/3)
[55124.537585] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=31)
[55124.538136] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[55124.538143] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[55124.538146] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[55124.539158] wlan0: associated
[55173.965317] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[55173.965607] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[55179.171888] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[55179.171901] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[55179.171904] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[55179.173534] wlan0: authenticate with <MAC address removed>
[55179.175457] wlan0: send auth to <MAC address removed> (try 1/3)
[55179.181079] wlan0: authenticated
[55179.183913] wlan0: associate with <MAC address removed> (try 1/3)
[55179.190159] wlan0: RX AssocResp from <MAC address removed> (capab=0x31 status=0 aid=53)
[55179.190708] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[55179.190714] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[55179.190717] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[55179.191723] wlan0: associated
[55192.215599] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 104
[55192.215686] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 104
[55447.542487] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 2
[55620.590870] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[55620.590883] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[55620.590888] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[55620.591458] wlan0: authenticate with <MAC address removed>
[55620.593365] wlan0: send auth to <MAC address removed> (try 1/3)
[55620.598387] wlan0: authenticated
[55620.599193] wlan0: associate with <MAC address removed> (try 1/3)
[55620.606316] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=36)
[55620.607085] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[55620.607091] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[55620.607094] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[55620.608206] wlan0: associated
[55770.410034] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[58100.392841] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[58100.392990] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[58100.407355] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[58100.407367] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[58100.407371] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[58106.091258] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[58106.091283] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[58106.092628] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[58142.362874] wlan0: authenticate with <MAC address removed>
[58142.383422] wlan0: send auth to <MAC address removed> (try 1/3)
[58142.384003] wlan0: authenticated
[58142.395834] wlan0: associate with <MAC address removed> (try 1/3)
[58142.398582] wlan0: RX AssocResp from <MAC address removed> (capab=0x111 status=0 aid=1)
[58142.399104] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[58142.399110] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[58142.399113] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[58142.399127] wlan0: associated
[58142.399139] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[58153.137658] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[58167.595316] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[58167.595327] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[58167.595329] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[58167.595901] wlan0: authenticate with <MAC address removed>
[58167.608332] wlan0: send auth to <MAC address removed> (try 1/3)
[58167.612533] wlan0: authenticated
[58167.619935] wlan0: associate with <MAC address removed> (try 1/3)
[58167.624058] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=9)
[58167.624599] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[58167.624605] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[58167.624608] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[58167.625625] wlan0: associated
[61199.355301] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[61199.356182] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[61199.368869] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[61199.368883] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[61199.368888] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[61205.285167] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[61205.285193] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[61205.286549] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[65268.187870] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[65268.187892] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[65268.189873] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[65304.011838] wlan0: authenticate with <MAC address removed>
[65304.020992] wlan0: send auth to <MAC address removed> (try 1/3)
[65304.052774] wlan0: authenticated
[65304.056058] wlan0: associate with <MAC address removed> (try 1/3)
[65304.080030] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=126)
[65304.080670] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[65304.080677] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[65304.080680] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[65304.080693] wlan0: associated
[65304.080737] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[65315.143404] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[65324.818017] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[65372.619014] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[65372.619029] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[65372.619034] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[65372.620744] wlan0: authenticate with <MAC address removed>
[65372.622699] wlan0: send auth to <MAC address removed> (try 1/3)
[65372.667174] wlan0: authenticated
[65372.669954] wlan0: associate with <MAC address removed> (try 1/3)
[65372.676980] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=92)
[65372.677965] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[65372.677976] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[65372.677980] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[65372.678997] wlan0: associated
[65407.203736] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[65407.203749] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[65407.203752] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[65407.204521] wlan0: authenticate with <MAC address removed>
[65407.206558] wlan0: send auth to <MAC address removed> (try 1/3)
[65407.211907] wlan0: authenticated
[65407.215999] wlan0: associate with <MAC address removed> (try 1/3)
[65407.865657] wlan0: associate with <MAC address removed> (try 2/3)
[65407.872770] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=130)
[65407.873500] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[65407.873508] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[65407.873512] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[65407.873526] wlan0: associated
[65520.755893] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[65616.464697] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[65736.316917] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[65736.316990] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[65773.637533] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[65773.637691] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[65774.839794] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 10
[65848.127836] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[66221.838385] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[66221.838399] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[66221.838404] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[66221.839784] wlan0: authenticate with <MAC address removed>
[66221.841872] wlan0: send auth to <MAC address removed> (try 1/3)
[66221.850479] wlan0: authenticated
[66221.852741] wlan0: associate with <MAC address removed> (try 1/3)
[66221.862836] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=40)
[66221.863909] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[66221.863915] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[66221.863917] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[66221.865012] wlan0: associated
[66459.571042] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[66459.571055] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[66459.571060] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[66459.573372] wlan0: authenticate with <MAC address removed>
[66459.575317] wlan0: send auth to <MAC address removed> (try 1/3)
[66459.585836] wlan0: authenticated
[66459.586929] wlan0: associate with <MAC address removed> (try 1/3)
[66459.593283] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=153)
[66459.594162] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[66459.594166] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[66459.594168] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[66459.595238] wlan0: associated
[66523.960294] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[66523.960308] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[66523.960313] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[66524.621189] wlan0: authenticate with <MAC address removed>
[66524.634284] wlan0: send auth to <MAC address removed> (try 1/3)
[66524.834423] wlan0: send auth to <MAC address removed> (try 2/3)
[66524.835106] wlan0: authenticated
[66524.838397] wlan0: associate with <MAC address removed> (try 1/3)
[66524.841778] wlan0: RX AssocResp from <MAC address removed> (capab=0x111 status=0 aid=17)
[66524.842428] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[66524.842437] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[66524.842447] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[66524.842466] wlan0: associated
[66577.070638] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 40
[66577.070761] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 40
[66577.070781] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 40
[66681.990400] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[66681.990412] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[66681.990416] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[66681.992017] wlan0: authenticate with <MAC address removed>
[66682.005495] wlan0: send auth to <MAC address removed> (try 1/3)
[66682.006727] wlan0: authenticated
[66682.011376] wlan0: associate with <MAC address removed> (try 1/3)
[66682.023149] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=51)
[66682.024136] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[66682.024142] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[66682.024145] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[66682.025149] wlan0: associated
[66798.103160] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[67157.096506] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[67157.096520] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[67157.096524] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[67157.097298] wlan0: authenticate with <MAC address removed>
[67157.109820] wlan0: send auth to <MAC address removed> (try 1/3)
[67157.110761] wlan0: authenticated
[67157.116243] wlan0: associate with <MAC address removed> (try 1/3)
[67157.120270] wlan0: RX AssocResp from <MAC address removed> (capab=0x111 status=0 aid=11)
[67157.120801] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[67157.120808] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[67157.120811] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[67157.120823] wlan0: associated
[67215.657563] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 36
[67294.034651] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 36
[67294.034711] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 36
[67294.034800] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 36
[67299.151569] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[67299.151588] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[67299.151595] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[67299.152182] wlan0: authenticate with <MAC address removed>
[67299.164574] wlan0: send auth to <MAC address removed> (try 1/3)
[67299.168981] wlan0: authenticated
[67299.171317] wlan0: associate with <MAC address removed> (try 1/3)
[67299.179314] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=61)
[67299.179862] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[67299.179868] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[67299.179871] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[67299.180887] wlan0: associated
[67537.979749] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[67537.979761] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[67537.979764] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[67537.980324] wlan0: authenticate with <MAC address removed>
[67537.992520] wlan0: send auth to <MAC address removed> (try 1/3)
[67538.537799] wlan0: send auth to <MAC address removed> (try 2/3)
[67538.626624] wlan0: authenticated
[67538.877683] wlan0: authenticate with <MAC address removed>
[67538.889622] wlan0: send auth to <MAC address removed> (try 1/3)
[67538.892808] wlan0: authenticated
[67538.894024] wlan0: associate with <MAC address removed> (try 1/3)
[67538.899921] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=61)
[67538.900782] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[67538.900790] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[67538.900794] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[67538.900807] wlan0: associated
[67603.326987] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[67603.327054] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[67603.327165] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[67896.868955] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[67896.868968] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[67896.868973] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[67896.870555] wlan0: authenticate with <MAC address removed>
[67896.882836] wlan0: send auth to <MAC address removed> (try 1/3)
[67897.243098] wlan0: send auth to <MAC address removed> (try 2/3)
[67897.243869] wlan0: authenticated
[67897.594351] wlan0: authenticate with <MAC address removed>
[67897.607682] wlan0: send auth to <MAC address removed> (try 1/3)
[67897.611884] wlan0: authenticated
[67897.615512] wlan0: associate with <MAC address removed> (try 1/3)
[67897.630515] wlan0: RX AssocResp from <MAC address removed> (capab=0x31 status=0 aid=148)
[67897.631033] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[67897.631039] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[67897.631042] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[67897.631055] wlan0: associated
[67929.990587] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 2
[67929.990802] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 2
[67929.991011] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 2
[67931.135153] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 10
[67933.392039] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 100
[67933.392274] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 100
[67933.392428] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 100
[67933.392559] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 100
[67940.335625] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 2
[67940.335885] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 2
[67940.336063] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 2
[67940.336083] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 2
[67940.336121] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 2
[67940.336153] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 2
[67941.461958] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 6
[67941.462033] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 6
[67942.216129] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 7
[67942.216674] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 7
[67942.216898] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 7
[67942.216983] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 7
[67942.970687] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 8
[67942.970884] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 8
[67942.970904] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 8
[67953.203767] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[67953.203781] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[67953.203786] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[67953.205357] wlan0: authenticate with <MAC address removed>
[67953.205433] wlan0: direct probe to <MAC address removed> (try 1/3)
[67953.557042] wlan0: direct probe to <MAC address removed> (try 2/3)
[67953.841175] wlan0: direct probe to <MAC address removed> (try 3/3)
[67954.126193] wlan0: authentication with <MAC address removed> timed out
[67954.127590] wlan0: authenticate with <MAC address removed>
[67954.140004] wlan0: direct probe to <MAC address removed> (try 1/3)
[67954.373187] wlan0: direct probe to <MAC address removed> (try 2/3)
[67954.597054] wlan0: direct probe to <MAC address removed> (try 3/3)
[67954.819691] wlan0: authentication with <MAC address removed> timed out
[67955.034532] wlan0: authenticate with <MAC address removed>
[67955.055777] wlan0: direct probe to <MAC address removed> (try 1/3)
[67955.256166] wlan0: send auth to <MAC address removed> (try 2/3)
[67955.459794] wlan0: send auth to <MAC address removed> (try 3/3)
[67955.466998] wlan0: authenticated
[67955.467765] wlan0: associate with <MAC address removed> (try 1/3)
[67955.671486] wlan0: associate with <MAC address removed> (try 2/3)
[67955.875046] wlan0: associate with <MAC address removed> (try 3/3)
[67956.078698] wlan0: association with <MAC address removed> timed out
[67956.702768] wlan0: authenticate with <MAC address removed>
[67956.704795] wlan0: direct probe to <MAC address removed> (try 1/3)
[67956.905278] wlan0: direct probe to <MAC address removed> (try 2/3)
[67957.108916] wlan0: direct probe to <MAC address removed> (try 3/3)
[67957.312573] wlan0: authentication with <MAC address removed> timed out
[67957.470053] wlan0: authenticate with <MAC address removed>
[67957.473291] wlan0: direct probe to <MAC address removed> (try 1/3)
[67957.675979] wlan0: direct probe to <MAC address removed> (try 2/3)
[67957.879599] wlan0: direct probe to <MAC address removed> (try 3/3)
[67958.083257] wlan0: authentication with <MAC address removed> timed out
[67958.212628] wlan0: authenticate with <MAC address removed>
[67958.212715] wlan0: direct probe to <MAC address removed> (try 1/3)
[67958.414724] wlan0: direct probe to <MAC address removed> (try 2/3)
[67958.618344] wlan0: direct probe to <MAC address removed> (try 3/3)
[67958.821973] wlan0: authentication with <MAC address removed> timed out
[67962.629698] wlan0: authenticate with <MAC address removed>
[67962.640962] wlan0: send auth to <MAC address removed> (try 1/3)
[67962.642969] wlan0: authenticated
[67962.647383] wlan0: associate with <MAC address removed> (try 1/3)
[67962.653652] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=139)
[67962.654294] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[67962.654299] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[67962.654301] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[67962.654308] wlan0: associated
[68016.698647] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[68016.698657] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[68016.698660] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[68016.700642] wlan0: authenticate with <MAC address removed>
[68016.702694] wlan0: send auth to <MAC address removed> (try 1/3)
[68016.704103] wlan0: authenticated
[68016.710187] wlan0: associate with <MAC address removed> (try 1/3)
[68016.713740] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=178)
[68016.714266] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[68016.714272] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[68016.714276] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[68016.715291] wlan0: associated
[68046.673574] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[68046.676519] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[68116.401216] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[68116.401411] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[68167.317119] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[68237.069119] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 2
[68239.008945] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 36
[68239.956543] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 48
[68476.011915] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 10
[68476.766301] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 11
[68477.527433] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 36
[68478.292434] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 40
[68912.845233] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[68912.845247] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[68912.845252] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[68913.522270] wlan0: authenticate with <MAC address removed>
[68913.524323] wlan0: send auth to <MAC address removed> (try 1/3)
[68913.526669] wlan0: authenticated
[68913.528103] wlan0: associate with <MAC address removed> (try 1/3)
[68913.537246] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=83)
[68913.537794] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[68913.537806] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[68913.537813] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[68913.537830] wlan0: associated
[69613.549084] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[69613.549100] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[69613.549106] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[69613.550727] wlan0: authenticate with <MAC address removed>
[69613.550831] wlan0: send auth to <MAC address removed> (try 1/3)
[69613.553719] wlan0: authenticated
[69613.557153] wlan0: associate with <MAC address removed> (try 1/3)
[69613.561123] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=164)
[69613.561747] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[69613.561754] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[69613.561757] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[69613.562778] wlan0: associated
[69695.680843] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[69695.680856] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[69695.680858] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[69695.681405] wlan0: authenticate with <MAC address removed>
[69695.681479] wlan0: send auth to <MAC address removed> (try 1/3)
[69695.686577] wlan0: authenticated
[69695.687395] wlan0: associate with <MAC address removed> (try 1/3)
[69695.691432] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=93)
[69695.691986] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[69695.691992] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[69695.691994] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[69695.693006] wlan0: associated
[69725.655226] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[69725.655337] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 1
[69726.855009] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 10
[69728.402682] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 36
[69728.403112] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 36
[69728.403183] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 36
[69728.403209] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 36
[69728.403230] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 36
[69729.212139] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 40
[69730.729274] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 48
[69730.729516] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 48
[69739.864358] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[69739.864370] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[69739.864373] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[69739.864843] wlan0: authenticate with <MAC address removed>
[69739.864913] wlan0: send auth to <MAC address removed> (try 1/3)
[69739.874266] wlan0: authenticated
[69739.875222] wlan0: associate with <MAC address removed> (try 1/3)
[69739.939557] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=172)
[69739.939986] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[69739.939994] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[69739.939998] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[69739.940497] wlan0: associated
[69770.592255] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[69770.889812] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[69770.889830] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[69770.889837] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[69773.939450] wlan0: authenticate with <MAC address removed>
[69773.947136] wlan0: direct probe to <MAC address removed> (try 1/3)
[69774.148100] wlan0: direct probe to <MAC address removed> (try 2/3)
[69774.351763] wlan0: direct probe to <MAC address removed> (try 3/3)
[69774.555450] wlan0: authentication with <MAC address removed> timed out
[69775.000010] wlan0: authenticate with <MAC address removed>
[69775.011309] wlan0: send auth to <MAC address removed> (try 1/3)
[69775.018628] wlan0: authenticated
[69775.022653] wlan0: associate with <MAC address removed> (try 1/3)
[69775.044552] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[69775.045637] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[69775.045645] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[69775.045648] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[69775.045662] wlan0: associated
[69796.479332] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[69796.497737] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[69796.497755] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[69796.497762] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[69800.856530] wlan0: authenticate with <MAC address removed>
[69800.864799] wlan0: send auth to <MAC address removed> (try 1/3)
[69800.872818] wlan0: authenticated
[69800.874048] wlan0: associate with <MAC address removed> (try 1/3)
[69800.902677] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[69800.903182] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[69800.903186] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[69800.903188] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[69800.903198] wlan0: associated
[69821.438187] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[69821.466544] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[69821.466563] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[69821.466570] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[69826.316227] wlan0: authenticate with <MAC address removed>
[69826.337485] wlan0: direct probe to <MAC address removed> (try 1/3)
[69826.537800] wlan0: send auth to <MAC address removed> (try 2/3)
[69826.538473] wlan0: authenticated
[69826.541829] wlan0: associate with <MAC address removed> (try 1/3)
[69826.543949] wlan0: RX AssocResp from <MAC address removed> (capab=0x111 status=0 aid=25)
[69826.544506] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[69826.544514] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[69826.544518] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[69826.544531] wlan0: associated
[69835.772513] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[69848.280172] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 40
[69848.282225] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 40
[69848.282305] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 40
[69884.266106] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[69884.266120] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[69884.266125] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[69884.266682] wlan0: authenticate with <MAC address removed>
[69884.279079] wlan0: direct probe to <MAC address removed> (try 1/3)
[69884.835746] wlan0: send auth to <MAC address removed> (try 2/3)
[69884.843302] wlan0: authenticated
[69885.222261] wlan0: authenticate with <MAC address removed>
[69885.224432] wlan0: send auth to <MAC address removed> (try 1/3)
[69885.333426] wlan0: authenticated
[69885.335756] wlan0: associate with <MAC address removed> (try 1/3)
[69885.367280] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=95)
[69885.367747] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[69885.367759] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[69885.367765] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[69885.367777] wlan0: associated
[69892.206996] wlan0: deauthenticated from <MAC address removed> (Reason: 7)
[69892.236372] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[69892.236385] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[69892.236388] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[69892.772866] wlan0: authenticate with <MAC address removed>
[69892.785723] wlan0: send auth to <MAC address removed> (try 1/3)
[69892.786294] wlan0: authenticated
[69892.787563] wlan0: associate with <MAC address removed> (try 1/3)
[69892.789566] wlan0: RX AssocResp from <MAC address removed> (capab=0x111 status=0 aid=14)
[69892.790210] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[69892.790215] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[69892.790217] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[69892.790226] wlan0: associated
[69988.198967] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[69988.198981] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[69988.198986] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[69988.199516] wlan0: authenticate with <MAC address removed>
[69988.201380] wlan0: send auth to <MAC address removed> (try 1/3)
[69988.201991] wlan0: authenticated
[69988.206797] wlan0: associate with <MAC address removed> (try 1/3)
[69988.209856] wlan0: RX AssocResp from <MAC address removed> (capab=0x111 status=0 aid=24)
[69988.210392] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[69988.210403] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[69988.210410] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[69988.210429] wlan0: associated


****************** done ******************

```

---

### Post by smdubinsky on 2014-03-13
Did that help at all?

---

### Post by varunendra on 2014-03-14
There are plenty of error messages in dmesg which look like a bug, although the messages seem to be harmless. But apart from that, your udev rules file shows that you had tried (or probably were using previously) the proprietary "sta" driver.

For now, the only things I can suggest is to -

**1)** Delete your current udev rules file, it will be automatically regenerated, with only relevant entries this time -
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```

**2)** Delete all saved connections (the ones that you are having difficulty with) in Network Manager, and let them be automatically created again when you reconnect.

Your card is supported by all three variants of b43 driver, and the current one is what we usually recommend in this situation. Although seeing the errors, we may try any of the two other ones ("b43" or "wl"), but I'll refrain from doing that as long as possible.

---

### Post by smdubinsky on 2014-03-14
That worked, thanks!

---

