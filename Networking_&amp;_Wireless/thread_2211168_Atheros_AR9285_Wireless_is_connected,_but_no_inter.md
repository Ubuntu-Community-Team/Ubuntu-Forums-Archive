---
title: "Atheros AR9285: Wireless is connected, but no internet acces"
date: 2014-03-14
forum: Networking &amp; Wireless
---

### Post by DorelXD on 2014-03-14
Hello, guys! I've just installed Xubuntu 13.10 on my laptop. If I connect via cable, the internet works perfectly! But if I try to use the wireless netwrok, it shows that it's connected, but the web pages don't load at all! what can I do? I'm a newbie, so I don't know too much. Please, can somebody help me? Thank you!

---

### Post by varunendra on 2014-03-16
Welcome to the forums DorelXD!

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by DorelXD on 2014-03-19
Thank you for answering me! Here's the result I got:

```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux dorel-Satellite-C660D 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:39:31 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:fdc0]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7173]
    Kernel driver in use: ath9k

##### lsusb #####

Bus 002 Device 002: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 004 Device 003: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:"dlink"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=1 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.0.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [dlink] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TP-LINK_FLM:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA2
    dlink_one:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    MirchucK:        Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    simona_petcut:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA
    Bubico:          Infra, <MAC address removed>, Freq 2442 MHz, Rate 11 Mb/s, Strength 24 WPA
    dlink:           Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    POLLY:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA2
    GUDSIM:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    *dlink:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             193.231.252.1
    DNS:             213.154.124.1

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             193.231.252.1
    DNS:             213.154.124.1

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000508ce77650
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1116FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000600000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0502000D127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DDA30050F204104A0001101044000102103B000103104700102880288028801880A880C8BE19B4FB7A10210012442D4C696E6B20436F72706F726174696F6E1023000D442D4C696E6B20526F757465721024000A474F2D52542D4E313530104200044E6F6E651054000800060050F20400011011001A576972656C657373204E20313530204561737920526F7574657210080002278C103C0001011049000600372A000120
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706474220010D10
          Cell 02 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"MirchucK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002acad1bcca6
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 00084D6972636875634B
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030102
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 200100
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
                    IE: Unknown: DD750050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210004415355531023000652542D473332102400043132333410420004353637381054000800060050F20400011011000741535553204150100800020084103C000101
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"simona_petcut"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000022bb500
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 000D73696D6F6E615F706574637574
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b4470511ec
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1604001300000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD810050F204104A0001101044000101103B0001031047001063041253101920061228FC75169F56941021000010230011576972656C657373204E20526F75746572102400074449522D3530311042000D32303037303431332D303030311054000800060050F20400011011000F576972656C65737320526F75746572100800020086
                    IE: Unknown: DD1E00904C332C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3404001300000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 05 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_FLM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000895f8c433
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 000B54502D4C494E4B5F464C4D
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000002586D688FC022586D688FC64002C010808
          Cell 06 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"POLLY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008dba04a433
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 0005504F4C4C59
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD700050F204104A00011010440001021041000100103B00010310470010F3745F7870182DAF27182CE18A983A50102100035A5445102300035A54451024000631323334353610420004313233341054000800060050F2040001101100095A544520483231384E100800020080103C000101
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F202010100000364000027A4000042435E0062322F00

##### iwlist channel #####

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
          Current Frequency:2.462 GHz (Channel 11)

##### lsmod #####

ath3k                  13368  0 
ath9k                 161996  0 
mac80211              619465  1 ath9k
ath9k_common           13859  1 ath9k
ath9k_hw              457667  2 ath9k,ath9k_common
ath                    24123  3 ath9k,ath9k_common,ath9k_hw
cfg80211              499466  3 ath9k,mac80211,ath
bluetooth             391726  25 ath3k,btusb,bnep,rfcomm

##### modinfo #####

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     247033A5A2EF74BAFEF2634
alias:          usb:v0489pE036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE02Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3121d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3402d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04C5p1330d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3393d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE057d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0219d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3362d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3375d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03F0p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0215d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3000d*dc*dsc*dp*ic*isc*ip*in*
depends:        bluetooth
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     9960BB0B644BE14E4A2F42B
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     2DB88A2876852DC1D8C5A1D
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     57A1E15BE088B8A5C4BE74F
depends:        ath
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

##### modules #####

lp
rtc

##### blacklist #####

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

##### udev rules #####

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:05.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   23.689977] ath: phy0: ASPM enabled: 0x42
[   23.689982] ath: EEPROM regdomain: 0x65
[   23.689983] ath: EEPROM indicates we should expect a direct regpair map
[   23.689987] ath: Country alpha2 being used: 00
[   23.689988] ath: Regpair used: 0x65
[   28.673867] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.674763] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.858948] wlan0: authenticate with <MAC address removed>
[   34.890434] wlan0: send auth to <MAC address removed> (try 1/3)
[   34.895095] wlan0: authenticated
[   34.898474] wlan0: associate with <MAC address removed> (try 1/3)
[   34.902645] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=2)
[   34.902730] wlan0: associated
[   34.902787] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############

```

---

### Post by varunendra on 2014-03-19
> **DorelXD said:**
> ```

  Wireless Access Points (* = current AP)
    ....
    *dlink:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 80 **[COLOR="#FF0000"]WPA WPA2[/COLOR]**

  IPv4 Settings:
    Address:         192.168.0.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             **[COLOR="#FF0000"]193.231.252.1[/COLOR]**
    DNS:             213.154.124.1

```
As highlighted above, you are using WPA/WPA2 mixed mode encryption in the router which should be avoided. Plus, your first DNS address looks weird to me. Please try these for now -

[indent]**1)** Please change the encryption type in your router to pure WPA2-PSK with AES (CCMP). No mixed mode, no TKIP. Reboot the router after saving the change.

**2)** In network Manager settings, try using **8.8.8.8** or **8.8.4.4** as your DNS server(s). If you are using *"Automatic (DHCP)"* method in the settings, you'll have to choose *"Automatic (DHCP) address only"* to be able to define your own the DNS servers.

**3)** If the above two don't seem to help, open a terminal (Ctrl-Alt-T) and run the following command in it -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
This will create a file "ath9k.conf" in your /etc/modprobe.d directory that will cause your wireless card's driver "ath9k" to always load with a parameter "nohwcrypt=1". It often helps with this driver.

**4)** You may also try disabling "N" channel in the router (set it to b/g only mode if it is currently in b/g/n mode) if the router allows changing that. Refer to your router's manual to see if it does and how to change that. Try this only if the above changes don't seem to help.[/indent]

Also, you may not be able to use wireless as long as the Ethernet (cable) is plugged in. So keep the cable disconnected while you are trying to connect via wireless.

Let me know how it goes, and we'll try something else if required.

---

### Post by DorelXD on 2014-03-20
Hello again! I tried everything. I followed the steps exactly and I had no problem doing it. I've managed to do esaily all the modifications you suggested but nothing worked. What's next? I have two laptops. The other one is working perefectly fine. What can I do? Thank you for your help so far!

---

### Post by varunendra on 2014-03-21
Hmm.. I was already anticipating a "no-success" with this one. Let's try a newer driver which has been reported to be working nicely.

With the wired connection, please install the basic packages first -
```
sudo apt-get install linux-headers-generic build-essential
```

Then -

[indent]**1)** Download the "backports-3.13.2-1" package from here : [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)

**2)** Right-click the downloaded package > click "Extract here". This will extract the contents into a directory of same name.

**3)** Open a terminal (Ctrl-Alt-T), and assuming the above extracted directory is in the "**Downloads**" directory in your Home, run the following commands to compile and install the driver -
```
cd Downloads/backports-3.13.2-1
make defconfig-ath9k
make
sudo make install
```
Watch out for errors and report back if there are any, although there shouldn't be.[/indent]

Reboot after the installation is successfully finished, and try to connect. Test the connectivity and performance, and let us know how good (or not) it is.

**PS:**
You will have to recompile the driver with above steps whenever you kernel is upgraded. That's why it is not as good a solution as getting the default one working would have been.

---

### Post by DorelXD on 2014-03-21
Thank you, man! You are amazing! I've installed that driver. The first time I tried to open a webpage like [www.google.com](www.google.com) it didn't work. But then I tried to acces 192.168.0.1, which is the configuration page for my router, and surprisingly the page loaded. My common sense told me that if this page is accessible then it should work! Then I remebered that I set  **8.8.8.8**  as my DNS server, and  thought that this may have something to do with it. So I went to network manager and reverted the setting back to: "Automatic DHCP". That did the trick! Now it works like a charm! Thank you again! Your explanations and instructions were very clear and easy to follow.

---

### Post by varunendra on 2014-03-21
I'm as happy as you are, so pleasant is the sound of the word "success"! :D

Hope you have tested it long enough. When 14.04 LTS will be released, it will come with kernel 3.13 and hence the same driver by default. So you won't have to manually compile the driver after each kernel upgrade if you upgrade to it.

(However, it is always recommended to test a release in Live mode first, and only install/upgrade if fully satisfied with its performance :p)

---

