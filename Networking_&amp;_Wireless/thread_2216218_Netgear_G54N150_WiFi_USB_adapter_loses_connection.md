---
title: "Netgear G54/N150 WiFi USB adapter loses connection"
date: 2014-04-10
forum: Networking &amp; Wireless
---

### Post by pproets on 2014-04-10
Hi there !
I have a problem with my USB WiFi adapter, that seems to lose its network connection, but the symbol on the upper right corner doesn't indicate any problem. lan connection works perfectly fine. After a few minutes I cannot surf anymore until I disconnect and reconnect the wifi connection. hope you can help me. 

Thanks for your precious time and patience in advance !
greetings

---

### Post by varunendra on 2014-04-12
Welcome to Ubuntu Forums pproets!

While the USB adapter is plugged in and connected, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by pproets on 2014-05-15
```


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux phil-ThinkPad-R60 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express [14e4:167d] (rev 21)
    Subsystem: Lenovo ThinkPad R60e [17aa:2081]
    Kernel driver in use: tg3


##### lsusb #####


Bus 001 Device 004: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


##### rfkill #####


1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


auto lo
iface lo inet loopback


##### iwconfig #####


wlan1 IEEE 802.11bgn ESSID:"UPC1380874" 
Mode:Managed Frequency:2.462 GHz Access Point: <MAC address removed> 
Bit Rate=72.2 Mb/s Tx-Power=20 dBm 
Retry long limit:7 RTS thr=2347 B Fragment thr: off
Power Management: off
Link Quality=48/70 Signal level=-62 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:4 Missed beacon:0


##### route #####


Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 192.168.0.1 0.0.0.0 UG 0 0 0 wlan1
192.168.0.0 0.0.0.0 255.255.255.0 U 9 0 0 wlan1


##### resolv.conf #####


nameserver 127.0.1.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan1 [home] --------------------------------------------------------
Type: 802.11 WiFi
Driver: rtl8192cu
State: connected
Default: yes
HW Address: <MAC address removed>


Capabilities:
Speed: 72 Mb/s


Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes


Wireless Access Points (* = current AP)
xXJoKaHXx: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
UPC011877: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
Annie: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA
UPC010961: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
PBS-103421: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA
UPC0040294: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
UPC007484: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
Rabiata: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA
*UPC1380874: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 56 WPA WPA2
NETGEAR: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27
retep: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA


IPv4 Settings:
Address: 192.168.0.17
Prefix: 24 (255.255.255.0)
Gateway: 192.168.0.1


DNS: 195.34.133.21
DNS: 212.186.211.21


- Device: eth0 -----------------------------------------------------------------
Type: Wired
Driver: tg3
State: unavailable
Default: no
HW Address: <MAC address removed>


Capabilities:
Carrier Detect: yes


Wired Properties
Carrier: off


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


wlan1 Scan completed :
Cell 01 - Address: <MAC address removed>
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=46/70 Signal level=-64 dBm 
Encryption key: on
ESSID:"UPC1380874"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=000007c8b964fd56
Extra: Last beacon: 4ms ago
IE: Unknown: 000A55504331333830383734
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
IE: Unknown: 3D160B081500000000000000000000000000000000000000
IE: Unknown: DD090010180203F02C0000
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
Cell 02 - Address: <MAC address removed>
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=26/70 Signal level=-84 dBm 
Encryption key: on
ESSID:"UPC007484"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000009f0debdcf8
Extra: Last beacon: 4ms ago
IE: Unknown: 0009555043303037343834
IE: Unknown: 010882848B962430486C
IE: Unknown: 030101
IE: Unknown: 2A0104
IE: Unknown: 2F0104
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 32040C121860
IE: Unknown: DD090010180204F0000000
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
Cell 03 - Address: <MAC address removed>
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=26/70 Signal level=-84 dBm 
Encryption key: on
ESSID:"UPC0040294"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=000003545deb84ea
Extra: Last beacon: 4ms ago
IE: Unknown: 000A55504330303430323934
IE: Unknown: 010882848B962430486C
IE: Unknown: 030101
IE: Unknown: 2A0100
IE: Unknown: 2F0100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 32040C121860
IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1601081100000000000000000000000000000000000000
IE: Unknown: DD090010180200F02C0000
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
Cell 04 - Address: <MAC address removed>
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=30/70 Signal level=-80 dBm 
Encryption key: on
ESSID:"UPC011877"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000003100f39374
Extra: Last beacon: 4ms ago
IE: Unknown: 0009555043303131383737
IE: Unknown: 010882848B962430486C
IE: Unknown: 03010B
IE: Unknown: 2A0104
IE: Unknown: 2F0104
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 32040C121860
IE: Unknown: DD090010180204F0000000
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
Cell 05 - Address: <MAC address removed>
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=30/70 Signal level=-80 dBm 
Encryption key: on
ESSID:"Annie"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=000000718e1d7d32
Extra: Last beacon: 4ms ago
IE: Unknown: 0005416E6E6965
IE: Unknown: 010882848B962430486C
IE: Unknown: 03010B
IE: Unknown: 0706415420010D14
IE: Unknown: 2A0100
IE: Unknown: 2F0100
IE: Unknown: 32040C121860
IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D160B081100000000000000000000000000000000000000
IE: Unknown: DD090010180200F02C0000
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
Cell 06 - Address: <MAC address removed>
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=58/70 Signal level=-52 dBm 
Encryption key: on
ESSID:"xXJoKaHXx"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=000000c5aab84fef
Extra: Last beacon: 4ms ago
IE: Unknown: 000978584A6F4B61485878
IE: Unknown: 010882840B162430486C
IE: Unknown: 030106
IE: Unknown: 2A0100
IE: Unknown: 2F0100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 32040C121860
IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
IE: Unknown: 3D1606081500000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: Unknown: 7F0101
IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010AF1174D038605415C4B8870B6626344F1021000D4E4554474541522C20496E632E10230009574E5231303030763310240009574E523130303076331042000538333235381054000800060050F204000110110009574E52313030307633100800020084
IE: Unknown: DD090010180203F0050000
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3406081500000000000000000000000000000000000000
Cell 07 - Address: <MAC address removed>
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=32/70 Signal level=-78 dBm 
Encryption key: on
ESSID:"PBS-103421"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=00000011211b47c3
Extra: Last beacon: 4ms ago
IE: Unknown: 000A5042532D313033343231
IE: Unknown: 010882848B962430486C
IE: Unknown: 030106
IE: Unknown: 2A0104
IE: Unknown: 2F0104
IE: Unknown: 32040C121860
IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1606080000000000000000000000000000000000000000
IE: Unknown: DD720050F204104A00011010440001021041000100103B0001031047001077BD1B6BFF0DA258DC706842FB58F9AA10210007506972656C6C69102300064469736375731024000630303030303110420004303030311054000800060050F204000110110009506972656C6C694150100800020080
IE: Unknown: DD090010180202F0050000
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3406080000000000000000000000000000000000000000


##### iwlist channel #####


wlan1 11 channels in total; available frequencies :
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
Current Frequency:2.462 GHz (Channel 11)


##### lsmod #####


rtl8192cu 67723 0 
rtl_usb 18448 1 rtl8192cu
rtlwifi 63475 2 rtl_usb,rtl8192cu
rtl8192c_common 53172 1 rtl8192cu
mac80211 626489 3 rtl_usb,rtlwifi,rtl8192cu
cfg80211 484040 2 mac80211,rtlwifi


##### modinfo #####


filename: /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware: rtlwifi/rtl8192cufw_TMSC.bin
firmware: rtlwifi/rtl8192cufw_B.bin
firmware: rtlwifi/rtl8192cufw_A.bin
firmware: rtlwifi/rtl8192cufw.bin
description: Realtek 8192C/8188C 802.11n USB wireless
license: GPL
author: Larry Finger    <Larry.Finger@lwfinger.net>
author: Ziv Huang    <ziv_huang@realtek.com>
author: Georgia        <georgia@realtek.com>
srcversion: 7CF9B14C5E7812D872691FA
alias: usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v2357p0100d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v20F4p624Dd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0E66p0019d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DF6p0061d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0BDAp8186d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0B05p17ABd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0846pF001d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0846p9021d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v050Dp2103d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v050Dp2102d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v050Dp1004d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v2019p1201d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v04F2pAFFCd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v04F2pAFFBd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v04F2pAFF8d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v04F2pAFFAd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v04F2pAFF9d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v04F2pAFF7d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0BDAp317Fd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v9846p9041d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v4855p0091d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v4855p0090d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v13D3p3359d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v13D3p3358d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v2019pAB2Ed*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v2019p4902d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v13D3p3357d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v4856p0091d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DF6p0077d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DF6p005Cd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0BDAp5088d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v050Dp11F2d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0BDAp8178d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0BDAp819Ad*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0BDAp818Ad*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0BDAp817Fd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0BDAp018Ad*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*in*
depends: rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree: Y
vermagic: 3.13.0-24-generic SMP mod_unload modversions 
signer: Magrathea: Glacier signing key
sig_key: <MAC address removed>: D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo: sha512
parm: swenc:Set to 1 for software crypto (default 0)
(bool)
parm: debug:Set debug level (0-5) (default 0) (int)


filename: /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description: USB basic driver for rtlwifi
license: GPL
author: Larry Finger    <Larry.FInger@lwfinger.net>
author: Realtek WlanFAE    <wlanfae@realtek.com>
author: lizhaoming    <chaoming_li@realsil.com.cn>
srcversion: CE332F200EA30B201483F4F
depends: rtlwifi,mac80211
intree: Y
vermagic: 3.13.0-24-generic SMP mod_unload modversions 
signer: Magrathea: Glacier signing key
sig_key: <MAC address removed>: D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo: sha512


filename: /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description: Realtek 802.11n PCI wireless core
license: GPL
author: Larry Finger    <Larry.FInger@lwfinger.net>
author: Realtek WlanFAE    <wlanfae@realtek.com>
author: lizhaoming    <chaoming_li@realsil.com.cn>
srcversion: C21FC2F90947540319DE390
depends: mac80211,cfg80211
intree: Y
vermagic: 3.13.0-24-generic SMP mod_unload modversions 
signer: Magrathea: Glacier signing key
sig_key: <MAC address removed>: D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo: sha512


filename: /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description: Realtek 8192C/8188C 802.11n PCI wireless
license: GPL
author: Larry Finger    <Larry.Finger@lwfinger.net>
author: Ziv Huang    <ziv_huang@realtek.com>
author: Georgia        <georgia@realtek.com>
author: Realtek WlanFAE    <wlanfae@realtek.com>
author: lizhaoming    <chaoming_li@realsil.com.cn>
srcversion: 32F826C623BC49F764F7974
depends: 
intree: Y
vermagic: 3.13.0-24-generic SMP mod_unload modversions 
signer: Magrathea: Glacier signing key
sig_key: <MAC address removed>: D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo: sha512


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


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x050d:0x705a (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x0846:0x9041 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"


##### dmesg #####


[ 8.962618] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[ 20.883184] thinkpad_acpi: WARNING: This firmware may be missing critical bug fixes and/or important features
[ 333.271411] rtl8192cu: Chip version 0x10
[ 333.355266] rtl8192cu: MAC address: <MAC address removed>
[ 333.355274] rtl8192cu: Board Type 0
[ 333.355510] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 333.355552] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 333.438948] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 333.439629] rtlwifi: wireless switch is on
[ 333.452257] systemd-udevd[2100]: renamed network interface wlan0 to wlan1
[ 333.470886] rtl8192cu: MAC auto ON okay!
[ 333.515286] rtl8192cu: Tx queue select: 0x05
[ 333.889213] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 333.889849] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 357.762290] wlan1: authenticate with <MAC address removed>
[ 357.774099] wlan1: send auth to <MAC address removed> (try 1/3)
[ 357.776791] wlan1: authenticated
[ 357.780051] wlan1: associate with <MAC address removed> (try 1/3)
[ 357.796678] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 357.796727] wlan1: associated
[ 357.796793] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 736.833925] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 737.965055] wlan1: authenticate with <MAC address removed>
[ 737.977546] wlan1: send auth to <MAC address removed> (try 1/3)
[ 737.984924] wlan1: authenticated
[ 737.988060] wlan1: associate with <MAC address removed> (try 1/3)
[ 738.011531] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 738.011594] wlan1: associated
[ 742.122685] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 742.184444] rtl8192cu: MAC auto ON okay!
[ 742.217281] rtl8192cu: Tx queue select: 0x05
[ 742.586598] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 742.921975] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 743.732327] wlan1: authenticate with <MAC address removed>
[ 743.744482] wlan1: send auth to <MAC address removed> (try 1/3)
[ 743.749179] wlan1: authenticated
[ 743.752076] wlan1: associate with <MAC address removed> (try 1/3)
[ 743.773913] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 743.773963] wlan1: associated
[ 743.774634] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 748.444505] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 748.501761] rtl8192cu: MAC auto ON okay!
[ 748.534636] rtl8192cu: Tx queue select: 0x05
[ 748.908069] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 749.345119] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 750.019122] rtl8192cu: MAC auto ON okay!
[ 750.055390] rtl8192cu: Tx queue select: 0x05
[ 750.437785] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 753.617053] wlan1: authenticate with <MAC address removed>
[ 753.630247] wlan1: send auth to <MAC address removed> (try 1/3)
[ 753.642883] wlan1: authenticated
[ 753.644077] wlan1: associate with <MAC address removed> (try 1/3)
[ 753.670454] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 753.670501] wlan1: associated
[ 753.670556] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1028.143313] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1028.229757] rtl8192cu: MAC auto ON okay!
[ 1028.268738] rtl8192cu: Tx queue select: 0x05
[ 1028.633110] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1030.771117] rtl8192cu: MAC auto ON okay!
[ 1030.803878] rtl8192cu: Tx queue select: 0x05
[ 1031.181225] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1031.261741] rtl8192cu: MAC auto ON okay!
[ 1031.294503] rtl8192cu: Tx queue select: 0x05
[ 1031.673317] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1032.883819] rtl8192cu: MAC auto ON okay!
[ 1032.916678] rtl8192cu: Tx queue select: 0x05
[ 1033.289423] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1034.820767] wlan1: authenticate with <MAC address removed>
[ 1034.834161] wlan1: send auth to <MAC address removed> (try 1/3)
[ 1034.837997] wlan1: authenticated
[ 1034.840089] wlan1: associate with <MAC address removed> (try 1/3)
[ 1034.865642] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 1034.865715] wlan1: associated
[ 1034.865789] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1034.913255] wlan1: deauthenticating from <MAC address removed> by local choice (reason=2)
[ 1034.925924] wlan1: authenticate with <MAC address removed>
[ 1034.937914] wlan1: send auth to <MAC address removed> (try 1/3)
[ 1034.939560] wlan1: authenticated
[ 1034.944075] wlan1: associate with <MAC address removed> (try 1/3)
[ 1034.976814] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 1034.976880] wlan1: associated
[ 1035.409892] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1059.027488] rtl8192cu: MAC auto ON okay!
[ 1059.075964] rtl8192cu: Tx queue select: 0x05
[ 1059.446850] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1060.196627] wlan1: authenticate with <MAC address removed>
[ 1060.210130] wlan1: send auth to <MAC address removed> (try 1/3)
[ 1060.249555] wlan1: authenticated
[ 1060.252079] wlan1: associate with <MAC address removed> (try 1/3)
[ 1060.267543] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 1060.267609] wlan1: associated
[ 1060.267679] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 2248.592108] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2248.592443] rtl_usb: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x5881
[ 2248.592454] rtl_usb: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x80740
[ 2248.592464] rtl_usb: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x8080740
[ 2248.592475] rtl_usb: reg 0x608, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xd3c000
[ 2399.134776] rtl8192cu: Chip version 0x10
[ 2399.218289] rtl8192cu: MAC address: <MAC address removed>
[ 2399.218298] rtl8192cu: Board Type 0
[ 2399.218533] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 2399.218590] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 2399.453740] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[ 2399.454262] rtlwifi: wireless switch is on
[ 2399.676341] systemd-udevd[11656]: renamed network interface wlan0 to wlan1
[ 2399.682252] rtl8192cu: MAC auto ON okay!
[ 2399.744182] rtl8192cu: Tx queue select: 0x05
[ 2400.121509] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 2400.121957] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 2401.633020] wlan1: authenticate with <MAC address removed>
[ 2401.659135] wlan1: send auth to <MAC address removed> (try 1/3)
[ 2401.664679] wlan1: authenticated
[ 2401.668054] wlan1: associate with <MAC address removed> (try 1/3)
[ 2401.679711] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 2401.679781] wlan1: associated
[ 2401.679853] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 3471.290445] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3473.393072] rtl8192cu: MAC auto ON okay!
[ 3473.425958] rtl8192cu: Tx queue select: 0x05
[ 3473.798317] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3478.251937] wlan1: authenticate with <MAC address removed>
[ 3478.270420] wlan1: send auth to <MAC address removed> (try 1/3)
[ 3478.272597] wlan1: authenticated
[ 3478.276059] wlan1: associate with <MAC address removed> (try 1/3)
[ 3478.291123] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 3478.291179] wlan1: associated
[ 3478.292064] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready


########## wireless info END ############
```

sry for not answering for so long.

---

### Post by varunendra on 2014-05-15
You have used 'Quote' tags to post the output, please edit you post and use '**Code**' tag instead, as asked originally in my first post.

And my first recommendation is to change the encryption type in the router/access-point to pure WPA2-PSK with AES (CCMP). Currently it is set to WPA/WPA2 mixed mode with TKIP, avoid the mixed mode and TKIP at all cost! Reboot the router after saving the change.

Secondly, if the above change alone doesn't help, try this temporary parameter (will be lost at next boot, so try connectivity without rebooting) -
```
sudo modprobe -rv rtl8192cu
sudo modprobe -v rtl8192cu swenc=1
```
If this seems to help, we can make it permanent.

---

### Post by pproets on 2014-05-16
unfortunately, this didn't do the trick.

---

### Post by varunendra on 2014-05-16
Did you change the encryption in the router? Just for a test, please also try disabling N channel in the router if it gives you the option to set mode (set it to 'g-only' or b/g only mode).

And which country you are in? Try explicitly declaring your country code for 'regdomain' (Wireless Regulatory Domain) settings. For example, if you are in USA, the regdomain code for it is 'US', and it can be forced with command -
```
sudo iw reg set **US**
```
To look up your country code, please refer to this table : [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table)

This is also a temporary change, which can be made permanent if helps.

---

### Post by pproets on 2014-05-16
yes I did change the encryption as you told me. 
I am now at my grandparents house and there doesn't seem to be any problem with the wifi connection and it doesn't seem to be lost over time. however, I have the problem of losing the connection at home and in university. therefore it would be nice to find a solution disregarding my router since I cannot change the router setting in my university. If you think this problem cannot be solved like this, then I have to install windows and try that.

---

### Post by varunendra on 2014-05-17
Apart from declaring regdomain code, there is a patched version of this driver which needs to be downloaded from github and compiled/installed manually.

Here are the instructions (commands copy-pasted from the **[source github page]("https://github.com/pvaret/rtl8192cu-fixes")**) -

[indent]**1)** Open a terminal (Ctrl-Alt-T) and install the pre-requisites by running the following commands (while being connected to internet by any means) in it -
```
sudo apt-get install linux-headers-generic build-essential dkms git
```

**2)** Afterwards, run the following commands to download and compile/install the patched driver -
```
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
[COLOR="#000080"]cd rtl8192cu-fixes[/COLOR]
sudo dkms install 8192cu/1.[COLOR="#000080"]9[/COLOR]
sudo depmod -a
```
[COLOR="#000080"](Edited commands based on feedback from user 'wjwh' in post #10 below. Please see the post for details.)[/COLOR]

**3)** Blacklist the native driver so it doesn't conflict with the newly installed one -
```
sudo cp ./rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/
```[/indent]
Watch out the outputs of the entire process closely, and report back if there are any. If everything went okay, reboot, and see if the connection is good now.

---

### Post by pproets on 2014-05-19
It seems as if this solved my problem. I only had to install git, but that was no problem. thank you so much for your help :) I will observe the wlan connection and post back if anything happens, but for now it seems to be fixed :)
have fun, good luck !

---

### Post by wjwh on 2014-06-24
I tried this method without success until I made a couple of small changes.  I needed to change directory to rtl8192cu-fixes before running the install command.  It must be run from within this directory.  I also needed to change 8192cu/1.8 to 8192cu/1.9. So, step 2 finished up as being:

```
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
cd rtl8192cu-fixes
sudo dkms install 8192cu/1.9
sudo depmod -a

```
This worked fine.  Many thanks for this!

---

### Post by varunendra on 2014-06-25
Thanks for the heads up wjwh, I'm going to edit my post to include this change in version number.

---

### Post by Entheo on 2015-02-17
Wow i am so happy that i found this thread. I have had the same problem (Netgear G54 loses connection) as the OP for the past three months and have tried so many ways to sort it out and it has really done my head in. I almost gave up hope but then found this thread and followed Varunendra's advice on post #8 and it worked! 

Kudos Varunendra and good karma to you for providing the answer to this problem.

---

