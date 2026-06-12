---
title: "Realtek RTL8723AE: Slow and intermittent wifi loss"
date: 2013-12-21
forum: Networking &amp; Wireless
---

### Post by anbuck on 2013-12-21
I am running 13.10 and have a Realtek RTL8723AE PCIe adapter.  I can connect to wifi, but the connection is slow and over drops even when the wifi signal is strong.  This problem happens with all access points.  Thanks for your help.

04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter

---

### Post by PaulBx on 2013-12-22
Get another adapter. They are pretty cheap on ebay. 

I had a similar problem with a Realtek card in my pfsense (FreeBSD) box. I finally gave up on the thing and am getting a couple more.

Or maybe it can be fixed with a firmware load or driver upgrade? Who knows?

Linux has some difficulties with wireless. Take a look at the compatibility list:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by anbuck on 2013-12-22
Thanks for the reply.  If this were a desktop, then I would do just that, but it is an MSI-GE40 laptop.  I assume the NIC is built into the motherboard, but maybe not.  I can open it up and find out.

---

### Post by varunendra on 2013-12-23
The wireless card in laptops is a separate pci card that can be replaced. But that shouldn't be needed with this card. Not super awesome, but it does work with Linux.

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by anbuck on 2013-12-23
```



*************** info trace ***************


***** uname -a *****


Linux CR42-2M-GE40-2OC 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


***** lspci *****


03:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller [1969:e091] (rev 13)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:10e3]
	Kernel driver in use: alx
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
	Subsystem: AzureWave Device [1a3b:2114]
	Kernel driver in use: rtl8723ae


***** lsusb *****


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 002 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 003: ID 13d3:3394 IMC Networks 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:"Lemondrop"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=16/70  Signal level=-94 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0




***** rfkill *****


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


rtl8723ae              86524  0 
rtl_pci                26641  1 rtl8723ae
rtlwifi                63229  2 rtl_pci,rtl8723ae
mac80211              596969  3 rtl_pci,rtlwifi,rtl8723ae
cfg80211              479757  2 mac80211,rtlwifi


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [Lemondrop] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    House Divided:   Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Coyote Den:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 80 WPA2
    rq-wireless:     Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    2WIRE322:        Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Ardeshna Network:Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA2
    2WIRE124:        Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 100 WPA
    *Lemondrop:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2


  IPv4 Settings:
    Address:         10.0.0.20
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1


    DNS:             75.75.75.75
    DNS:             75.75.76.76




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


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
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=14/70  Signal level=-96 dBm  
                    Encryption key:on
                    ESSID:"Lemondrop"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000173f23172c5
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 00094C656D6F6E64726F70
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1AFD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD8C0050F204104A0001101044000102103B000103104700100994CD93ABBB120EB3D309FB2DB9382D1021000B546563686E69636F6C6F721023000B546563686E69636F6C6F721024000631323334353610420007303030303030311054000800060050F20400011011000D546563686E69636F6C6F724150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD09001018020DF03C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Coyote Den"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003a1c6c0774
                    Extra: Last beacon: 324ms ago
                    IE: Unknown: 000A436F796F74652044656E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23021400
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD0B0017F20100010100000007
                    IE: Unknown: DD0700039301780320
                    IE: Unknown: DD0E0017F20700010106881FA12F5DDF
                    IE: Unknown: DD090010180201001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46050200010000
          Cell 03 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"House Divided"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000034c46f58801
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000D486F7573652044697669646564
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030102
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
          Cell 04 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-20 dBm  
                    Encryption key:on
                    ESSID:"rq-wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000350b4cc554a
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000B72712D776972656C657373
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1602050500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3402050500000000000000000000000000000000000000
          Cell 05 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=14/70  Signal level=-96 dBm  
                    Encryption key:on
                    ESSID:"2WIRE124"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006b310d92181
                    Extra: Last beacon: 13784ms ago
                    IE: Unknown: 00083257495245313234
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 06 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"2WIRE322"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000048ffaff3181
                    Extra: Last beacon: 1824ms ago
                    IE: Unknown: 00083257495245333232
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 07 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=24 dBm  
                    Encryption key:on
                    ESSID:"Ardeshna Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000547e4470160
                    Extra: Last beacon: 4356ms ago
                    IE: Unknown: 00104172646573686E61204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050401030000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 33025101
                    IE: Unknown: 33027E95
                    IE: Unknown: 3D1601000000000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: Unknown: DD180050F2020101050003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301710320
                    IE: Unknown: DD0E0017F20700010106109ADD810FD3
                    IE: Unknown: DD0B0017F20100010100000007




***** resolv.conf *****


nameserver 127.0.1.1
search home.network


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


filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
firmware:       rtlwifi/rtl8723fw_B.bin
firmware:       rtlwifi/rtl8723fw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     B27D28DF892890255CCDDBE
alias:          pci:v000010ECd00008723sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     8363D6BED4EF1CF5A92482B
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     13B5FC2521B6DC5AB3F115C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x1969:0xe091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8723 (rtl8723ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[    2.654911] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[    2.658261] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    2.658459] rtlwifi: wireless switch is on
[    3.286890] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.287307] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.804743] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x250f01)
[    5.259400] wlan0: authenticate with <MAC address removed>
[    5.291188] wlan0: send auth to <MAC address removed> (try 1/3)
[    5.293641] wlan0: authenticated
[    5.294893] wlan0: associate with <MAC address removed> (try 1/3)
[    5.298066] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[    5.298315] wlan0: associated
[    5.298323] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  155.719911] wlan0: Connection to AP <MAC address removed> lost
[  157.171753] wlan0: authenticate with <MAC address removed>
[  157.203470] wlan0: send auth to <MAC address removed> (try 1/3)
[  157.205089] wlan0: authenticated
[  157.207008] wlan0: associate with <MAC address removed> (try 1/3)
[  157.210383] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  157.210630] wlan0: associated
[  202.376317] wlan0: Connection to AP <MAC address removed> lost
[  203.477690] wlan0: authenticate with <MAC address removed>
[  203.509685] wlan0: send auth to <MAC address removed> (try 1/3)
[  203.613509] wlan0: send auth to <MAC address removed> (try 2/3)
[  203.717586] wlan0: send auth to <MAC address removed> (try 3/3)
[  203.821719] wlan0: authentication with <MAC address removed> timed out
[  204.879533] wlan0: authenticate with <MAC address removed>
[  204.911194] wlan0: send auth to <MAC address removed> (try 1/3)
[  205.014866] wlan0: send auth to <MAC address removed> (try 2/3)
[  205.119021] wlan0: send auth to <MAC address removed> (try 3/3)
[  205.223071] wlan0: authentication with <MAC address removed> timed out
[  206.284935] wlan0: authenticate with <MAC address removed>
[  206.316595] wlan0: send auth to <MAC address removed> (try 1/3)
[  206.420296] wlan0: send auth to <MAC address removed> (try 2/3)
[  206.422397] wlan0: authenticated
[  206.424326] wlan0: associate with <MAC address removed> (try 1/3)
[  206.427698] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  206.427967] wlan0: associated
[  272.586673] wlan0: Connection to AP <MAC address removed> lost
[  273.684901] wlan0: authenticate with <MAC address removed>
[  273.715966] wlan0: send auth to <MAC address removed> (try 1/3)
[  273.819796] wlan0: send auth to <MAC address removed> (try 2/3)
[  273.923943] wlan0: send auth to <MAC address removed> (try 3/3)
[  274.027970] wlan0: authentication with <MAC address removed> timed out
[  275.085799] wlan0: authenticate with <MAC address removed>
[  275.117606] wlan0: send auth to <MAC address removed> (try 1/3)
[  275.221244] wlan0: send auth to <MAC address removed> (try 2/3)
[  275.325284] wlan0: send auth to <MAC address removed> (try 3/3)
[  275.429361] wlan0: authentication with <MAC address removed> timed out
[  276.487291] wlan0: authenticate with <MAC address removed>
[  276.518975] wlan0: send auth to <MAC address removed> (try 1/3)
[  276.622564] wlan0: send auth to <MAC address removed> (try 2/3)
[  276.625275] wlan0: authenticated
[  276.626564] wlan0: associate with <MAC address removed> (try 1/3)
[  276.629897] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  276.630152] wlan0: associated
[  310.700753] wlan0: Connection to AP <MAC address removed> lost
[  312.150449] wlan0: authenticate with <MAC address removed>
[  312.182440] wlan0: send auth to <MAC address removed> (try 1/3)
[  312.184000] wlan0: authenticated
[  312.186145] wlan0: associate with <MAC address removed> (try 1/3)
[  312.192120] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  312.192504] wlan0: associated
[  359.361565] wlan0: Connection to AP <MAC address removed> lost
[  360.811229] wlan0: authenticate with <MAC address removed>
[  360.843270] wlan0: send auth to <MAC address removed> (try 1/3)
[  360.844969] wlan0: authenticated
[  360.846861] wlan0: associate with <MAC address removed> (try 1/3)
[  360.853144] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  360.853459] wlan0: associated
[  367.902057] wlan0: Connection to AP <MAC address removed> lost
[  369.348232] wlan0: authenticate with <MAC address removed>
[  369.379913] wlan0: send auth to <MAC address removed> (try 1/3)
[  369.381511] wlan0: authenticated
[  369.383433] wlan0: associate with <MAC address removed> (try 1/3)
[  369.386653] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  369.386914] wlan0: associated
[  418.564806] wlan0: Connection to AP <MAC address removed> lost
[  420.018967] wlan0: authenticate with <MAC address removed>
[  420.050646] wlan0: send auth to <MAC address removed> (try 1/3)
[  420.052222] wlan0: authenticated
[  420.054151] wlan0: associate with <MAC address removed> (try 1/3)
[  420.057440] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  420.057691] wlan0: associated
[  431.121320] wlan0: Connection to AP <MAC address removed> lost
[  432.203251] wlan0: authenticate with <MAC address removed>
[  432.234714] wlan0: send auth to <MAC address removed> (try 1/3)
[  432.338476] wlan0: send auth to <MAC address removed> (try 2/3)
[  432.442599] wlan0: send auth to <MAC address removed> (try 3/3)
[  432.546664] wlan0: authentication with <MAC address removed> timed out
[  433.604545] wlan0: authenticate with <MAC address removed>
[  433.636460] wlan0: send auth to <MAC address removed> (try 1/3)
[  433.739937] wlan0: send auth to <MAC address removed> (try 2/3)
[  433.843946] wlan0: send auth to <MAC address removed> (try 3/3)
[  433.948094] wlan0: authentication with <MAC address removed> timed out
[  435.005428] wlan0: authenticate with <MAC address removed>
[  435.037496] wlan0: send auth to <MAC address removed> (try 1/3)
[  435.141301] wlan0: send auth to <MAC address removed> (try 2/3)
[  435.144046] wlan0: authenticated
[  435.145279] wlan0: associate with <MAC address removed> (try 1/3)
[  435.148609] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  435.148844] wlan0: associated
[  451.181412] wlan0: Connection to AP <MAC address removed> lost
[  452.623110] wlan0: authenticate with <MAC address removed>
[  452.655155] wlan0: send auth to <MAC address removed> (try 1/3)
[  452.656747] wlan0: authenticated
[  452.658804] wlan0: associate with <MAC address removed> (try 1/3)
[  452.661993] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  452.662228] wlan0: associated
[  465.734262] wlan0: Connection to AP <MAC address removed> lost
[  467.181752] wlan0: authenticate with <MAC address removed>
[  467.213680] wlan0: send auth to <MAC address removed> (try 1/3)
[  467.215379] wlan0: authenticated
[  467.217372] wlan0: associate with <MAC address removed> (try 1/3)
[  467.220858] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  467.221097] wlan0: associated
[  480.292801] wlan0: Connection to AP <MAC address removed> lost
[  481.756316] wlan0: authenticate with <MAC address removed>
[  481.788236] wlan0: send auth to <MAC address removed> (try 1/3)
[  481.789936] wlan0: authenticated
[  481.791968] wlan0: associate with <MAC address removed> (try 1/3)
[  481.795215] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  481.795437] wlan0: associated
[  506.901215] wlan0: Connection to AP <MAC address removed> lost
[  507.990968] wlan0: authenticate with <MAC address removed>
[  508.022641] wlan0: send auth to <MAC address removed> (try 1/3)
[  508.126367] wlan0: send auth to <MAC address removed> (try 2/3)
[  508.230474] wlan0: send auth to <MAC address removed> (try 3/3)
[  508.334587] wlan0: authentication with <MAC address removed> timed out
[  509.392611] wlan0: authenticate with <MAC address removed>
[  509.424306] wlan0: send auth to <MAC address removed> (try 1/3)
[  509.527735] wlan0: send auth to <MAC address removed> (try 2/3)
[  509.631896] wlan0: send auth to <MAC address removed> (try 3/3)
[  509.735910] wlan0: authentication with <MAC address removed> timed out
[  510.794278] wlan0: authenticate with <MAC address removed>
[  510.825756] wlan0: send auth to <MAC address removed> (try 1/3)
[  510.929216] wlan0: send auth to <MAC address removed> (try 2/3)
[  510.931050] wlan0: authenticated
[  510.933145] wlan0: associate with <MAC address removed> (try 1/3)
[  510.936565] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  510.936817] wlan0: associated
[  593.159532] wlan0: Connection to AP <MAC address removed> lost
[  594.249838] wlan0: authenticate with <MAC address removed>
[  594.281002] wlan0: send auth to <MAC address removed> (try 1/3)
[  594.384706] wlan0: send auth to <MAC address removed> (try 2/3)
[  594.488762] wlan0: send auth to <MAC address removed> (try 3/3)
[  594.592887] wlan0: authentication with <MAC address removed> timed out
[  595.650736] wlan0: authenticate with <MAC address removed>
[  595.682436] wlan0: send auth to <MAC address removed> (try 1/3)
[  595.786087] wlan0: send auth to <MAC address removed> (try 2/3)
[  595.890246] wlan0: send auth to <MAC address removed> (try 3/3)
[  595.994336] wlan0: authentication with <MAC address removed> timed out
[  597.051688] wlan0: authenticate with <MAC address removed>
[  597.083681] wlan0: send auth to <MAC address removed> (try 1/3)
[  597.187558] wlan0: send auth to <MAC address removed> (try 2/3)
[  597.191808] wlan0: authenticated
[  597.195548] wlan0: associate with <MAC address removed> (try 1/3)
[  597.198885] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  597.199135] wlan0: associated
[  611.213666] wlan0: Connection to AP <MAC address removed> lost
[  612.311658] wlan0: authenticate with <MAC address removed>
[  612.343070] wlan0: send auth to <MAC address removed> (try 1/3)
[  612.446817] wlan0: send auth to <MAC address removed> (try 2/3)
[  612.550876] wlan0: send auth to <MAC address removed> (try 3/3)
[  612.655015] wlan0: authentication with <MAC address removed> timed out
[  613.712924] wlan0: authenticate with <MAC address removed>
[  613.744467] wlan0: send auth to <MAC address removed> (try 1/3)
[  613.848130] wlan0: send auth to <MAC address removed> (try 2/3)
[  613.952285] wlan0: send auth to <MAC address removed> (try 3/3)
[  614.056375] wlan0: authentication with <MAC address removed> timed out
[  615.114171] wlan0: authenticate with <MAC address removed>
[  615.145871] wlan0: send auth to <MAC address removed> (try 1/3)
[  615.249564] wlan0: send auth to <MAC address removed> (try 2/3)
[  615.251468] wlan0: authenticated
[  615.253588] wlan0: associate with <MAC address removed> (try 1/3)
[  615.256840] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  615.257066] wlan0: associated
[  631.273791] wlan0: Connection to AP <MAC address removed> lost
[  632.363221] wlan0: authenticate with <MAC address removed>
[  632.395038] wlan0: send auth to <MAC address removed> (try 1/3)
[  632.498893] wlan0: send auth to <MAC address removed> (try 2/3)
[  632.602997] wlan0: send auth to <MAC address removed> (try 3/3)
[  632.707055] wlan0: authentication with <MAC address removed> timed out
[  633.760545] wlan0: authenticate with <MAC address removed>
[  633.792489] wlan0: send auth to <MAC address removed> (try 1/3)
[  633.896225] wlan0: send auth to <MAC address removed> (try 2/3)
[  634.000376] wlan0: send auth to <MAC address removed> (try 3/3)
[  634.104481] wlan0: authentication with <MAC address removed> timed out
[  635.162509] wlan0: authenticate with <MAC address removed>
[  635.193833] wlan0: send auth to <MAC address removed> (try 1/3)
[  635.297685] wlan0: send auth to <MAC address removed> (try 2/3)
[  635.299401] wlan0: authenticated
[  635.301714] wlan0: associate with <MAC address removed> (try 1/3)
[  635.305067] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  635.305313] wlan0: associated
[  643.309793] wlan0: Connection to AP <MAC address removed> lost
[  644.763543] wlan0: authenticate with <MAC address removed>
[  644.795498] wlan0: send auth to <MAC address removed> (try 1/3)
[  644.816716] wlan0: authenticated
[  644.819223] wlan0: associate with <MAC address removed> (try 1/3)
[  644.846467] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  644.846714] wlan0: associated
[  653.860398] wlan0: Connection to AP <MAC address removed> lost
[  655.310059] wlan0: authenticate with <MAC address removed>
[  655.342049] wlan0: send auth to <MAC address removed> (try 1/3)
[  655.343645] wlan0: authenticated
[  655.345707] wlan0: associate with <MAC address removed> (try 1/3)
[  655.351181] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  655.351447] wlan0: associated
[  664.406966] wlan0: Connection to AP <MAC address removed> lost
[  665.496834] wlan0: authenticate with <MAC address removed>
[  665.528314] wlan0: send auth to <MAC address removed> (try 1/3)
[  665.632056] wlan0: send auth to <MAC address removed> (try 2/3)
[  665.736208] wlan0: send auth to <MAC address removed> (try 3/3)
[  665.840267] wlan0: authentication with <MAC address removed> timed out
[  666.898065] wlan0: authenticate with <MAC address removed>
[  666.929926] wlan0: send auth to <MAC address removed> (try 1/3)
[  667.033468] wlan0: send auth to <MAC address removed> (try 2/3)
[  667.137545] wlan0: send auth to <MAC address removed> (try 3/3)
[  667.241664] wlan0: authentication with <MAC address removed> timed out
[  668.299517] wlan0: authenticate with <MAC address removed>
[  668.331061] wlan0: send auth to <MAC address removed> (try 1/3)
[  668.434860] wlan0: send auth to <MAC address removed> (try 2/3)
[  668.436990] wlan0: authenticated
[  668.438867] wlan0: associate with <MAC address removed> (try 1/3)
[  668.442111] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  668.442348] wlan0: associated
[  712.553362] wlan0: Connection to AP <MAC address removed> lost
[  714.001312] wlan0: authenticate with <MAC address removed>
[  714.032874] wlan0: send auth to <MAC address removed> (try 1/3)
[  714.034406] wlan0: authenticated
[  714.036486] wlan0: associate with <MAC address removed> (try 1/3)
[  714.039880] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  714.040134] wlan0: associated
[  721.091651] wlan0: Connection to AP <MAC address removed> lost
[  722.529472] wlan0: authenticate with <MAC address removed>
[  722.561336] wlan0: send auth to <MAC address removed> (try 1/3)
[  722.562939] wlan0: authenticated
[  722.564987] wlan0: associate with <MAC address removed> (try 1/3)
[  722.573897] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  722.574161] wlan0: associated
[  735.638161] wlan0: Connection to AP <MAC address removed> lost
[  736.723655] wlan0: authenticate with <MAC address removed>
[  736.755700] wlan0: send auth to <MAC address removed> (try 1/3)
[  736.859402] wlan0: send auth to <MAC address removed> (try 2/3)
[  736.963425] wlan0: send auth to <MAC address removed> (try 3/3)
[  737.067550] wlan0: authentication with <MAC address removed> timed out
[  738.125334] wlan0: authenticate with <MAC address removed>
[  738.157077] wlan0: send auth to <MAC address removed> (try 1/3)
[  738.260732] wlan0: send auth to <MAC address removed> (try 2/3)
[  738.364913] wlan0: send auth to <MAC address removed> (try 3/3)
[  738.468927] wlan0: authentication with <MAC address removed> timed out
[  739.526855] wlan0: authenticate with <MAC address removed>
[  739.558451] wlan0: send auth to <MAC address removed> (try 1/3)
[  739.662175] wlan0: send auth to <MAC address removed> (try 2/3)
[  739.665001] wlan0: authenticated
[  739.666206] wlan0: associate with <MAC address removed> (try 1/3)
[  739.669482] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  739.669728] wlan0: associated
[  749.680339] wlan0: Connection to AP <MAC address removed> lost
[  750.770180] wlan0: authenticate with <MAC address removed>
[  750.801605] wlan0: send auth to <MAC address removed> (try 1/3)
[  750.905418] wlan0: send auth to <MAC address removed> (try 2/3)
[  751.009537] wlan0: send auth to <MAC address removed> (try 3/3)
[  751.113629] wlan0: authentication with <MAC address removed> timed out
[  752.171059] wlan0: authenticate with <MAC address removed>
[  752.203115] wlan0: send auth to <MAC address removed> (try 1/3)
[  752.306801] wlan0: send auth to <MAC address removed> (try 2/3)
[  752.410923] wlan0: send auth to <MAC address removed> (try 3/3)
[  752.515075] wlan0: authentication with <MAC address removed> timed out
[  753.572614] wlan0: authenticate with <MAC address removed>
[  753.604501] wlan0: send auth to <MAC address removed> (try 1/3)
[  753.708269] wlan0: send auth to <MAC address removed> (try 2/3)
[  753.710763] wlan0: authenticated
[  753.712269] wlan0: associate with <MAC address removed> (try 1/3)
[  753.715655] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  753.715900] wlan0: associated
[  829.920545] wlan0: Connection to AP <MAC address removed> lost
[  831.371075] wlan0: authenticate with <MAC address removed>
[  831.402368] wlan0: send auth to <MAC address removed> (try 1/3)
[  831.403955] wlan0: authenticated
[  831.405987] wlan0: associate with <MAC address removed> (try 1/3)
[  831.410605] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  831.410837] wlan0: associated
[  838.461173] wlan0: Connection to AP <MAC address removed> lost
[  839.919576] wlan0: authenticate with <MAC address removed>
[  839.950948] wlan0: send auth to <MAC address removed> (try 1/3)
[  839.957890] wlan0: authenticated
[  839.958563] wlan0: associate with <MAC address removed> (try 1/3)
[  839.961815] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  839.962060] wlan0: associated
[  849.015774] wlan0: Connection to AP <MAC address removed> lost
[  850.466180] wlan0: authenticate with <MAC address removed>
[  850.497723] wlan0: send auth to <MAC address removed> (try 1/3)
[  850.499251] wlan0: authenticated
[  850.501079] wlan0: associate with <MAC address removed> (try 1/3)
[  850.504344] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  850.504579] wlan0: associated
[  857.552261] wlan0: Connection to AP <MAC address removed> lost
[  859.006579] wlan0: authenticate with <MAC address removed>
[  859.038045] wlan0: send auth to <MAC address removed> (try 1/3)
[  859.039611] wlan0: authenticated
[  859.041619] wlan0: associate with <MAC address removed> (try 1/3)
[  859.044856] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  859.045106] wlan0: associated
[  880.138932] wlan0: Connection to AP <MAC address removed> lost
[  881.589083] wlan0: authenticate with <MAC address removed>
[  881.620721] wlan0: send auth to <MAC address removed> (try 1/3)
[  881.622354] wlan0: authenticated
[  881.624214] wlan0: associate with <MAC address removed> (try 1/3)
[  881.627413] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  881.627649] wlan0: associated
[  930.801661] wlan0: Connection to AP <MAC address removed> lost
[  931.887809] wlan0: authenticate with <MAC address removed>
[  931.918974] wlan0: send auth to <MAC address removed> (try 1/3)
[  932.022788] wlan0: send auth to <MAC address removed> (try 2/3)
[  932.126892] wlan0: send auth to <MAC address removed> (try 3/3)
[  932.230964] wlan0: authentication with <MAC address removed> timed out
[  933.289456] wlan0: authenticate with <MAC address removed>
[  933.320448] wlan0: send auth to <MAC address removed> (try 1/3)
[  933.424175] wlan0: send auth to <MAC address removed> (try 2/3)
[  933.528262] wlan0: send auth to <MAC address removed> (try 3/3)
[  933.632400] wlan0: authentication with <MAC address removed> timed out
[  934.690250] wlan0: authenticate with <MAC address removed>
[  934.721895] wlan0: send auth to <MAC address removed> (try 1/3)
[  934.825600] wlan0: send auth to <MAC address removed> (try 2/3)
[  934.828378] wlan0: authenticated
[  934.829568] wlan0: associate with <MAC address removed> (try 1/3)
[  934.832995] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  934.833289] wlan0: associated
[  970.921849] wlan0: Connection to AP <MAC address removed> lost
[  972.011717] wlan0: authenticate with <MAC address removed>
[  972.043063] wlan0: send auth to <MAC address removed> (try 1/3)
[  972.146931] wlan0: send auth to <MAC address removed> (try 2/3)
[  972.250991] wlan0: send auth to <MAC address removed> (try 3/3)
[  972.355121] wlan0: authentication with <MAC address removed> timed out
[  973.413282] wlan0: authenticate with <MAC address removed>
[  973.444790] wlan0: send auth to <MAC address removed> (try 1/3)
[  973.548363] wlan0: send auth to <MAC address removed> (try 2/3)
[  973.652404] wlan0: send auth to <MAC address removed> (try 3/3)
[  973.756568] wlan0: authentication with <MAC address removed> timed out
[  974.822594] wlan0: authenticate with <MAC address removed>
[  974.854112] wlan0: send auth to <MAC address removed> (try 1/3)
[  974.957681] wlan0: send auth to <MAC address removed> (try 2/3)
[  974.959267] wlan0: authenticated
[  974.961713] wlan0: associate with <MAC address removed> (try 1/3)
[  974.965026] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  974.965274] wlan0: associated
[ 1017.062261] wlan0: Connection to AP <MAC address removed> lost
[ 1018.510331] wlan0: authenticate with <MAC address removed>
[ 1018.541667] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1018.548909] wlan0: authenticated
[ 1018.549288] wlan0: associate with <MAC address removed> (try 1/3)
[ 1018.552511] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[ 1018.552742] wlan0: associated
[ 1059.702670] wlan0: Connection to AP <MAC address removed> lost
[ 1061.148321] wlan0: authenticate with <MAC address removed>
[ 1061.180460] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1061.182208] wlan0: authenticated
[ 1061.184061] wlan0: associate with <MAC address removed> (try 1/3)
[ 1061.187411] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[ 1061.187647] wlan0: associated
[ 1068.239187] wlan0: Connection to AP <MAC address removed> lost
[ 1069.693813] wlan0: authenticate with <MAC address removed>
[ 1069.724926] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1069.726497] wlan0: authenticated
[ 1069.728563] wlan0: associate with <MAC address removed> (try 1/3)
[ 1069.731773] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[ 1069.732007] wlan0: associated
[ 1114.897934] wlan0: Connection to AP <MAC address removed> lost
[ 1115.995394] wlan0: authenticate with <MAC address removed>
[ 1116.027194] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1116.131067] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1116.235211] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1116.339326] wlan0: authentication with <MAC address removed> timed out
[ 1117.397423] wlan0: authenticate with <MAC address removed>
[ 1117.428809] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1117.532510] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1117.636575] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1117.740715] wlan0: authentication with <MAC address removed> timed out
[ 1118.798511] wlan0: authenticate with <MAC address removed>
[ 1118.830183] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1118.933875] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1118.935716] wlan0: authenticated
[ 1118.937922] wlan0: associate with <MAC address removed> (try 1/3)
[ 1118.941204] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[ 1118.941457] wlan0: associated
[ 1134.958014] wlan0: Connection to AP <MAC address removed> lost
[ 1136.404345] wlan0: authenticate with <MAC address removed>
[ 1136.435691] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1136.437282] wlan0: authenticated
[ 1136.439372] wlan0: associate with <MAC address removed> (try 1/3)
[ 1136.442571] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[ 1136.442824] wlan0: associated
[ 1221.731217] wlan0: Connection to AP <MAC address removed> lost
[ 1223.183492] wlan0: authenticate with <MAC address removed>
[ 1223.214742] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1223.216344] wlan0: authenticated
[ 1223.218277] wlan0: associate with <MAC address removed> (try 1/3)
[ 1223.221547] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[ 1223.221792] wlan0: associated


****************** done ******************



```

---

### Post by varunendra on 2013-12-24
If the router/Access Point is under your control, please change the encryption type first. Currently you are using WPA/WPA2 mixed mode with TKIP, which is very inefficient and so is highly discouraged. Change it to pure WPA2-PSK with AES.

If that alone doesn't help, additionally try unloading the driver and reloading it with some available parameters in Ubuntu -
```
sudo modprobe -rv rtl8723ae
sudo modprobe -v rtl8723ae swenc=1 fwlps=0
```
This will be a temporary change and will be lost at next boot. If it seems to help, we can make it permanent.

Another thing you may try (temporarily or permanent) is to disable N-channel in the router and use b/g mode only. Of course try this only if the above suggestions don't make any difference.

Please try these for now and report back about the stability and performance. We may also try a newer or proprietary driver if needed.

---

### Post by anbuck on 2013-12-24
Thank you for these repiles, Varun.  I really appreciate your help.

I do not control the access point, but this problem happens at all access points that I've used.  My access point at home, which is WPS-PSK - AES has the same issues.  I am at work right now and I tried reloading the kernel module with the parameters your specified, but it is no better.  As usual, I have trouble just connecting to the access point here.

If there is a proprietary driver available, I would like to try that.  I had looked in Software & Updates before, but there was no proprietary driver listed.  Do I need to download the driver manually and build it from source?

---

### Post by anbuck on 2013-12-24
Sorry, meant to say that my access point at home is WPA2-PSK

---

### Post by varunendra on 2013-12-26
> **anbuck said:**
> Do I need to download the driver manually and build it from source?
Yes exactly that. But first we'll try the latest open source driver which is usually improved more rapidly.

**EDIT:** Before trying to compile the driver, make sure you have the support packages installed. While being connected to internet, open a terminal (Ctrl-Alt-T) and run this in it -
```
sudo apt-get install linux-headers-generic build-essential
```

1) Please download the latest 'Stable' backported drivers package from here : [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)
2) Copy the downloaded tar.bz2 package on your Desktop > Right-Click > Extract here
3) Open a terminal (Ctrl-Alt-T) and compile and install the required driver (rtl8723ae) with -
```
cd Desktop/*<name of the directory extracted above>*
make defconfig-rtlwifi
make
sudo make install
```
4) Reboot and see if you get any better performance. If not, post back a fresh report of the wireless_script and we may try either some tweaking, or the proprietary driver this time.

---

### Post by anbuck on 2013-12-26
Thanks again for the help.  I installed the new driver, but it seems to be about the same performance.  My connection still drops randomly.  Since I'm compiling this driver manually, will I have to recompile it if/when I upgrade my kernel?  The latest script output is below.

```



*************** info trace ***************


***** uname -a *****


Linux CR42-2M-GE40-2OC 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy


***** lspci *****


03:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller [1969:e091] (rev 13)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:10e3]
    Kernel driver in use: alx
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: AzureWave Device [1a3b:2114]
    Kernel driver in use: rtl8723ae


***** lsusb *****


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 004: ID 13d3:3394 IMC Networks 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:"Lemondrop"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=15/70  Signal level=-95 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0




***** rfkill *****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


rtl8723ae             165269  0 
rtl_pci                35460  1 rtl8723ae
rtlwifi                86374  2 rtl_pci,rtl8723ae
mac80211              523165  3 rtl_pci,rtlwifi,rtl8723ae
cfg80211              483129  2 mac80211,rtlwifi
compat                 13893  4 cfg80211,mac80211,rtlwifi,rtl8723ae


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [Lemondrop] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    2WIRE322:        Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    rq-wireless:     Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    House Divided:   Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Coyote Den:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    Ardeshna Network:Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    2WIRE124:        Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 64 WPA
    *Lemondrop:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2


  IPv4 Settings:
    Address:         10.0.0.20
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1


    DNS:             75.75.75.75
    DNS:             75.75.76.76




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


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
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"House Divided"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000038851945d65
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000D486F7573652044697669646564
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030102
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
          Cell 02 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"rq-wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000038cbebff15c
                    Extra: Last beacon: 3992ms ago
                    IE: Unknown: 000B72712D776972656C657373
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1602050600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3402050600000000000000000000000000000000000000
          Cell 03 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=70/70  Signal level=-16 dBm  
                    Encryption key:on
                    ESSID:"2WIRE124"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006ef1b247181
                    Extra: Last beacon: 15892ms ago
                    IE: Unknown: 00083257495245313234
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-12 dBm  
                    Encryption key:on
                    ESSID:"Coyote Den"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000076278c73ac
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000A436F796F74652044656E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23021400
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD0B0017F20100010100000007
                    IE: Unknown: DD0700039301780320
                    IE: Unknown: DD0E0017F20700010106881FA12F5DDF
                    IE: Unknown: DD090010180201001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46050200010000
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"Lemondrop"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001affcc3b185
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 00094C656D6F6E64726F70
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1AFD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD8C0050F204104A0001101044000102103B000103104700100994CD93ABBB120EB3D309FB2DB9382D1021000B546563686E69636F6C6F721023000B546563686E69636F6C6F721024000631323334353610420007303030303030311054000800060050F20400011011000D546563686E69636F6C6F724150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD09001018020CF03C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00




***** resolv.conf *****


nameserver 127.0.1.1
search home.network


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


filename:       /lib/modules/3.11.0-14-generic/updates/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
version:        backported from Linux (v3.13-rc2-0-gdc1ccc4) using backports v3.13-rc2-1-0-gf69c248
firmware:       rtlwifi/rtl8723fw_B.bin
firmware:       rtlwifi/rtl8723fw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B6E2FEB366372FACD9E82C5
alias:          pci:v000010ECd00008723sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,compat,mac80211
vermagic:       3.11.0-14-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


filename:       /lib/modules/3.11.0-14-generic/updates/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     63EA174CB73E8312913DA80
depends:        mac80211,rtlwifi
vermagic:       3.11.0-14-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-14-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
version:        backported from Linux (v3.13-rc2-0-gdc1ccc4) using backports v3.13-rc2-1-0-gf69c248
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     FFF99CDE1777AA7F6E0E454
depends:        mac80211,compat,cfg80211
vermagic:       3.11.0-14-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x1969:0xe091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8723 (rtl8723ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[    2.199449] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[    2.209739] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    2.209943] rtlwifi: wireless switch is on
[    3.066465] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x250f01)
[    4.645709] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.645952] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.572237] wlan0: authenticate with <MAC address removed>
[    6.604202] wlan0: send auth to <MAC address removed> (try 1/3)
[    6.605867] wlan0: authenticated
[    6.607924] wlan0: associate with <MAC address removed> (try 1/3)
[    6.611021] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=10)
[    6.611261] wlan0: associated
[    6.611267] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   58.804070] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[   58.804112] wlan0: Connection to AP <MAC address removed> lost
[   59.889969] wlan0: authenticate with <MAC address removed>
[   59.921939] wlan0: send auth to <MAC address removed> (try 1/3)
[   60.025795] wlan0: send auth to <MAC address removed> (try 2/3)
[   60.129996] wlan0: send auth to <MAC address removed> (try 3/3)
[   60.234154] wlan0: authentication with <MAC address removed> timed out
[   61.292132] wlan0: authenticate with <MAC address removed>
[   61.324023] wlan0: send auth to <MAC address removed> (try 1/3)
[   61.427891] wlan0: send auth to <MAC address removed> (try 2/3)
[   61.532066] wlan0: send auth to <MAC address removed> (try 3/3)
[   61.636258] wlan0: authentication with <MAC address removed> timed out
[   62.694244] wlan0: authenticate with <MAC address removed>
[   62.726180] wlan0: send auth to <MAC address removed> (try 1/3)
[   62.830046] wlan0: send auth to <MAC address removed> (try 2/3)
[   62.835025] wlan0: authenticated
[   62.838069] wlan0: associate with <MAC address removed> (try 1/3)
[   62.841765] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=10)
[   62.842011] wlan0: associated
[  351.827851] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  351.827910] wlan0: Connection to AP <MAC address removed> lost
[  352.918354] wlan0: authenticate with <MAC address removed>
[  352.949929] wlan0: send auth to <MAC address removed> (try 1/3)
[  353.053623] wlan0: send auth to <MAC address removed> (try 2/3)
[  353.157731] wlan0: send auth to <MAC address removed> (try 3/3)
[  353.261940] wlan0: authentication with <MAC address removed> timed out
[  354.320305] wlan0: authenticate with <MAC address removed>
[  354.351930] wlan0: send auth to <MAC address removed> (try 1/3)
[  354.455733] wlan0: send auth to <MAC address removed> (try 2/3)
[  354.559839] wlan0: send auth to <MAC address removed> (try 3/3)
[  354.664052] wlan0: authentication with <MAC address removed> timed out
[  355.722401] wlan0: authenticate with <MAC address removed>
[  355.754083] wlan0: send auth to <MAC address removed> (try 1/3)
[  355.857800] wlan0: send auth to <MAC address removed> (try 2/3)
[  355.861118] wlan0: authenticated
[  355.861752] wlan0: associate with <MAC address removed> (try 1/3)
[  355.865075] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=10)
[  355.865322] wlan0: associated
[  576.613092] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  576.613153] wlan0: Connection to AP <MAC address removed> lost
[  578.072219] wlan0: authenticate with <MAC address removed>
[  578.103537] wlan0: send auth to <MAC address removed> (try 1/3)
[  578.105077] wlan0: authenticated
[  578.107276] wlan0: associate with <MAC address removed> (try 1/3)
[  578.110485] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=10)
[  578.110710] wlan0: associated
[  585.166030] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  585.166102] wlan0: Connection to AP <MAC address removed> lost
[  586.617935] wlan0: authenticate with <MAC address removed>
[  586.648399] wlan0: send auth to <MAC address removed> (try 1/3)
[  586.649916] wlan0: authenticated
[  586.652084] wlan0: associate with <MAC address removed> (try 1/3)
[  586.655279] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=10)
[  586.655525] wlan0: associated
[  599.722049] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  599.722108] wlan0: Connection to AP <MAC address removed> lost
[  601.182290] wlan0: authenticate with <MAC address removed>
[  601.214332] wlan0: send auth to <MAC address removed> (try 1/3)
[  601.216075] wlan0: authenticated
[  601.217953] wlan0: associate with <MAC address removed> (try 1/3)
[  601.221254] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=10)
[  601.221490] wlan0: associated
[  608.276579] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  608.276607] wlan0: Connection to AP <MAC address removed> lost
[  609.727615] wlan0: authenticate with <MAC address removed>
[  609.759263] wlan0: send auth to <MAC address removed> (try 1/3)
[  609.760983] wlan0: authenticated
[  609.762805] wlan0: associate with <MAC address removed> (try 1/3)
[  609.766140] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=10)
[  609.766387] wlan0: associated
[  829.458635] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  829.458647] wlan0: Connection to AP <MAC address removed> lost
[  830.548655] wlan0: authenticate with <MAC address removed>
[  830.580044] wlan0: send auth to <MAC address removed> (try 1/3)
[  830.683892] wlan0: send auth to <MAC address removed> (try 2/3)
[  830.787992] wlan0: send auth to <MAC address removed> (try 3/3)
[  830.892095] wlan0: authentication with <MAC address removed> timed out
[  831.949388] wlan0: authenticate with <MAC address removed>
[  831.981406] wlan0: send auth to <MAC address removed> (try 1/3)
[  832.085166] wlan0: send auth to <MAC address removed> (try 2/3)
[  832.189328] wlan0: send auth to <MAC address removed> (try 3/3)
[  832.293450] wlan0: authentication with <MAC address removed> timed out
[  833.351339] wlan0: authenticate with <MAC address removed>
[  833.383006] wlan0: send auth to <MAC address removed> (try 1/3)
[  833.486637] wlan0: send auth to <MAC address removed> (try 2/3)
[  833.488544] wlan0: authenticated
[  833.490655] wlan0: associate with <MAC address removed> (try 1/3)
[  833.493976] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=10)
[  833.494226] wlan0: associated
[  971.885269] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  971.885325] wlan0: Connection to AP <MAC address removed> lost
[  973.339197] wlan0: authenticate with <MAC address removed>
[  973.371053] wlan0: send auth to <MAC address removed> (try 1/3)
[  973.474780] wlan0: send auth to <MAC address removed> (try 2/3)
[  973.578946] wlan0: send auth to <MAC address removed> (try 3/3)
[  973.682958] wlan0: authentication with <MAC address removed> timed out
[  974.740553] wlan0: authenticate with <MAC address removed>
[  974.772361] wlan0: send auth to <MAC address removed> (try 1/3)
[  974.876182] wlan0: send auth to <MAC address removed> (try 2/3)
[  974.980347] wlan0: send auth to <MAC address removed> (try 3/3)
[  975.084452] wlan0: authentication with <MAC address removed> timed out
[  976.142399] wlan0: authenticate with <MAC address removed>
[  976.173950] wlan0: send auth to <MAC address removed> (try 1/3)
[  976.277552] wlan0: send auth to <MAC address removed> (try 2/3)
[  976.381734] wlan0: send auth to <MAC address removed> (try 3/3)
[  976.485779] wlan0: authentication with <MAC address removed> timed out
[  977.543261] wlan0: authenticate with <MAC address removed>
[  977.575187] wlan0: send auth to <MAC address removed> (try 1/3)
[  977.678947] wlan0: send auth to <MAC address removed> (try 2/3)
[  977.783113] wlan0: send auth to <MAC address removed> (try 3/3)
[  977.887216] wlan0: authentication with <MAC address removed> timed out
[  978.944658] wlan0: authenticate with <MAC address removed>
[  978.976650] wlan0: send auth to <MAC address removed> (try 1/3)
[  979.080399] wlan0: send auth to <MAC address removed> (try 2/3)
[  979.184557] wlan0: send auth to <MAC address removed> (try 3/3)
[  979.288621] wlan0: authentication with <MAC address removed> timed out
[  980.346699] wlan0: authenticate with <MAC address removed>
[  980.378036] wlan0: send auth to <MAC address removed> (try 1/3)
[  980.481786] wlan0: send auth to <MAC address removed> (try 2/3)
[  980.585913] wlan0: send auth to <MAC address removed> (try 3/3)
[  980.690021] wlan0: authentication with <MAC address removed> timed out
[  981.748240] wlan0: authenticate with <MAC address removed>
[  981.779655] wlan0: send auth to <MAC address removed> (try 1/3)
[  981.883136] wlan0: send auth to <MAC address removed> (try 2/3)
[  981.987340] wlan0: send auth to <MAC address removed> (try 3/3)
[  982.091464] wlan0: authentication with <MAC address removed> timed out
[  983.149676] wlan0: authenticate with <MAC address removed>
[  983.180933] wlan0: send auth to <MAC address removed> (try 1/3)
[  983.284572] wlan0: send auth to <MAC address removed> (try 2/3)
[  983.388731] wlan0: send auth to <MAC address removed> (try 3/3)
[  983.492840] wlan0: authentication with <MAC address removed> timed out
[  984.550789] wlan0: authenticate with <MAC address removed>
[  984.582298] wlan0: send auth to <MAC address removed> (try 1/3)
[  984.686013] wlan0: send auth to <MAC address removed> (try 2/3)
[  984.790169] wlan0: send auth to <MAC address removed> (try 3/3)
[  984.894229] wlan0: authentication with <MAC address removed> timed out
[  985.952111] wlan0: authenticate with <MAC address removed>
[  985.983958] wlan0: send auth to <MAC address removed> (try 1/3)
[  986.087432] wlan0: send auth to <MAC address removed> (try 2/3)
[  986.191571] wlan0: send auth to <MAC address removed> (try 3/3)
[  986.295639] wlan0: authentication with <MAC address removed> timed out
[  987.353005] wlan0: authenticate with <MAC address removed>
[  987.385022] wlan0: send auth to <MAC address removed> (try 1/3)
[  987.488803] wlan0: send auth to <MAC address removed> (try 2/3)
[  987.513335] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  988.486066] wlan0: send auth to <MAC address removed> (try 3/3)
[  988.589918] wlan0: authentication with <MAC address removed> timed out
[ 1016.784053] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1018.705150] wlan0: authenticate with <MAC address removed>
[ 1018.736405] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1018.737919] wlan0: authenticated
[ 1018.740047] wlan0: associate with <MAC address removed> (try 1/3)
[ 1018.743162] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=10)
[ 1018.743395] wlan0: associated
[ 1018.743402] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1068.904770] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1068.904829] wlan0: Connection to AP <MAC address removed> lost
[ 1069.994204] wlan0: authenticate with <MAC address removed>
[ 1070.025662] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1070.129244] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1070.233361] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1070.337425] wlan0: authentication with <MAC address removed> timed out
[ 1071.394401] wlan0: authenticate with <MAC address removed>
[ 1071.426198] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1071.529979] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1071.633974] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1071.738082] wlan0: authentication with <MAC address removed> timed out
[ 1072.795600] wlan0: authenticate with <MAC address removed>
[ 1072.827089] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1072.930689] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1072.933014] wlan0: authenticated
[ 1072.934712] wlan0: associate with <MAC address removed> (try 1/3)
[ 1072.938085] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=10)
[ 1072.938328] wlan0: associated
[ 1080.934825] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1080.934886] wlan0: Connection to AP <MAC address removed> lost
[ 1082.376370] wlan0: authenticate with <MAC address removed>
[ 1082.407887] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1082.409448] wlan0: authenticated
[ 1082.411451] wlan0: associate with <MAC address removed> (try 1/3)
[ 1082.414774] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=10)
[ 1082.415025] wlan0: associated
[ 1245.916853] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1245.916912] wlan0: Connection to AP <MAC address removed> lost
[ 1247.363183] wlan0: authenticate with <MAC address removed>
[ 1247.394693] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1247.396452] wlan0: authenticated
[ 1247.398234] wlan0: associate with <MAC address removed> (try 1/3)
[ 1247.401442] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=10)
[ 1247.401671] wlan0: associated
[ 1306.609657] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1306.609686] wlan0: Connection to AP <MAC address removed> lost
[ 1307.699497] wlan0: authenticate with <MAC address removed>
[ 1307.730955] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1307.834776] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1307.938880] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1308.042986] wlan0: authentication with <MAC address removed> timed out
[ 1309.100812] wlan0: authenticate with <MAC address removed>
[ 1309.132555] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1309.236183] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1309.340286] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1309.444380] wlan0: authentication with <MAC address removed> timed out
[ 1310.502139] wlan0: authenticate with <MAC address removed>
[ 1310.533871] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1310.637543] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1310.639810] wlan0: authenticated
[ 1310.641541] wlan0: associate with <MAC address removed> (try 1/3)
[ 1310.644954] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=10)
[ 1310.645204] wlan0: associated


****************** done ******************

```

---

### Post by varunendra on 2013-12-28
> **anbuck said:**
> Since I'm compiling this driver manually, will I have to recompile it if/when I upgrade my kernel?

I'm not yet sure about the backported driver, but for the proprietary driver, yes, you will have to compile it each time your kernel is upgraded. This is one of the main reasons why we try to always go with native packages first.

Anyway, the detected signal strength is still very weak. As a sanity check, please check the antenna connection on the card if you can. It should be two cables that connect as plugs to two sockets on the wireless card which is located in a user-accessible area in most notebooks (to be accessed by opening some panel at the bottom side of notebook).

If they are good, you may try the proprietary driver as suggested in this post : [http://ubuntuforums.org/showthread.php?p=12770984](http://ubuntuforums.org/showthread.php?p=12770984)

Be aware that of the three users I know who used this method, two didn't reply back about its success or failure, and one replied back with no success (driver compiled and installed, but no performance improvement). I hope you may be the first one to report success and good performance with it (fingers crossed..).

If you want to play safe, you may try both the native driver (with the tweaks) and the proprietary one on a live session.

---

### Post by anbuck on 2013-12-28
Even after the code change you detailed in the linked thread, I was getting compilation errors.  I found this thread: [http://askubuntu.com/questions/367587/unable-to-compile-realtek-rtl8188ce-driver-on-ubuntu-13-10](http://askubuntu.com/questions/367587/unable-to-compile-realtek-rtl8188ce-driver-on-ubuntu-13-10) and I tried using the repo suggested there.  I was able to compile the driver and install it, but when I tried to do modprobe it, I get an error.  I tried rebooting, but when I do an lsmod, I still see the rtl8723ae module listed, not rtl8723e.  Trying modprobe again gave me the same error.

```

insmod /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723e/rtl8723e.ko 
ERROR: could not insert 'rtl8723e': Invalid argument

```

---

### Post by anbuck on 2013-12-28
I forgot to say that I can't open up the laptop to check the antenna connections because I'm not at home right now and I don't have a screwdriver here.  The signal strength fluctuates wildly, so maybe you are right about the connection being poor.  Or maybe the driver is just bad.  I will open it up and check later.

---

### Post by varunendra on 2013-12-28
The method I linked to was personally tested by me on 13.04 live session (kernel 3.8..) and later a user for whom it compiled smoothly, without a single error. I'd be interested in seeing the error you get while compiling it.

But now that you have compiled from a different (apparently authentic) source, let's check its version to see if it is the same one (with modified code) as the one officially available on Realtek's site, or a different version. Please post back the output of -
```
modinfo rtl8723e
```

---

### Post by anbuck on 2013-12-28
Here is the output of make on the original proprietary driver after I added the suggested precompiler logic to that one file:
```

make -C /lib/modules/3.11.0-14-generic/build M=/home/anbuck/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-14-generic'
  CC [M]  /home/anbuck/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
/home/anbuck/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c: In function &#8216;rtl_action_proc&#8217;:
/home/anbuck/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:885:32: error: &#8216;struct ieee80211_conf&#8217; has no member named &#8216;channel&#8217;
       rx_status.freq = hw->conf.channel->center_freq;
                                ^
/home/anbuck/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:886:32: error: &#8216;struct ieee80211_conf&#8217; has no member named &#8216;channel&#8217;
       rx_status.band = hw->conf.channel->band;
                                ^
/home/anbuck/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c: In function &#8216;rtl_send_smps_action&#8217;:
/home/anbuck/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:1451:24: error: &#8216;struct ieee80211_conf&#8217; has no member named &#8216;channel&#8217;
   info->band = hw->conf.channel->band;
                        ^
make[2]: *** [/home/anbuck/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/home/anbuck/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-14-generic'
make: *** [all] Error 2

```

Here is the output of modinfo on the other, apparently authentic (hopefully not malware), version:
```

filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723e/rtl8723e.ko
firmware:       rtlwifi/rtl8723efw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     A6A5D9265D711DA85EEBD47
alias:          pci:v000010ECd00008723sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       3.11.0-14-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)

```

I am confused because it says the license is GPL, but I thought this was a proprietary driver.

---

### Post by varunendra on 2013-12-29
Hmm.. I wasn't aware of those errors, looks like some further changes in the kernel headers caused it for which the patching was needed.

I don't have the iso of versions beyond 13.04, and with my snail-pace gprs connection, I can't even dream of downloading a full ISO. Therefore I currently have no way to test the other source codes or any modifications to them.

However, based on information I could gather from the net, it seems the one you have compiled is our best hope for now. I am not sure what that error is about that you got while trying to load it, but this post on askubuntu has a few answers to it : [http://askubuntu.com/questions/253591/network-card-rtl8723e-not-accepted-anymore-in-ubuntu](http://askubuntu.com/questions/253591/network-card-rtl8723e-not-accepted-anymore-in-ubuntu)

Please try them and let me know if you could load it successfully. Maybe you'd also need to blacklist the native driver to prevent it from loading automatically -
```
echo "blacklist rtl8723ae" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
> **anbuck said:**
> I am confused because it says the license is GPL, but I thought this was a proprietary driver.

I have never been very sure about it either. I believe it is just the firmware (.bin) part that is proprietary for most drivers.

---

### Post by anbuck on 2013-12-29
I tried blacklisting the native driver and also uninstalling the backports version, but I still get the same error when I try to modprobe the proprietary driver.  I really appreciate all your help Varun, but I think I'm just going to have to get a new card.

---

### Post by varunendra on 2013-12-29
Yeah, some cards can be stubborn, and we don't seem to have very promising support for this one yet. Sorry I couldn't be of more help, but this wiki page may help you make a pick : [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

May I advise to search the forums and the net to make sure your pick is well supported in Linux and/or can be easily fixed if there are any known issues.

Also, usually, and naturally, people don't report cards that work smoothly for them. So it would be a great help to the community if you report your both cards (this one and the new one you get) and their performance on that wiki page.

---

### Post by anbuck on 2013-12-30
Thanks again for all your help even though we couldn't find a solution!

That wiki is not easy to edit.  I added my card under Realtek->PCI because there was no miniPCI link for Realtek and I couldn't get it to add the link correctly.  On the edit page, the text is all smashed together.  It's like trying to edit minified javascript.

---

### Post by varunendra on 2013-12-30
Yeah, I don't find the Moin Wiki very intuitive either. Although it seems the format issue you mentioned has been fixed (apparently by yourself :)) : [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI)

By the way, a 'Special' Thanks to you for taking time to add your experience with the card there. It is a great source of help for all of us. I applaud your willingness to contribute even though your experience with the drivers was not so good. =D>

---

### Post by HousieMousie2 on 2013-12-30
Interesting issue with two Realtek cards/drivers I have &#8212; was that they sometimes got cranky if both wired and wireless were enabled.  I had to disable whichever I was not using to get a good connection/good speed on wireless and to keep it from complaining about losing the wireless connection when I was on wired. lol  It was solved for both of my cards in eventual updates (though at different points in time/with different updates) without doing anything special.

Just tossing that out there in case someone else runs into the same strange issue.

---

### Post by aanton on 2014-01-19
I had the same problem with Ubuntu 13.04 and kernel 3.8.X. It now seems fixed after using this modified driver that i found in GitHub:
[https://github.com/vicre/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0516.2013_revison_1](https://github.com/vicre/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0516.2013_revison_1)

And i found a page for new kernels:
[http://blog.83c.org/how-to-compile-the-realtek-8169-driver-with-linux-kernel-3-8/](http://blog.83c.org/how-to-compile-the-realtek-8169-driver-with-linux-kernel-3-8/)

I hope it works for you.

Regards,
Armando

---

### Post by anbuck on 2014-01-20
Hey, aanton.  Thanks for the tip!  I actually already purchased and installed a new card though that is working great, so I won't be able to try your suggestion.  Thanks again and I'm glad that you found a solution!

---

### Post by Tim_Hallett on 2014-01-23
Aanton

Being a newbie with the 8188ee card, and connection issues, I'd love it if you would help {Edited: See next post]

---

### Post by Tim_Hallett on 2014-01-23
Got the tarball, but the make command fails with Error 1 and Error 2
> make -C /lib/modules/3.11.0-12-generic/build M=/home/tim/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0516.2013_revison_1-master modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-12-generic'
  CC [M]  /home/tim/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0516.2013_revison_1-master/base.o
/home/tim/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0516.2013_revison_1-master/base.c: In function &#8216;rtl_action_proc&#8217;:
/home/tim/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0516.2013_revison_1-master/base.c:885:32: error: &#8216;struct ieee80211_conf&#8217; has no member named &#8216;channel&#8217;
       rx_status.freq = hw->conf.channel->center_freq;
                                ^
/home/tim/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0516.2013_revison_1-master/base.c:886:32: error: &#8216;struct ieee80211_conf&#8217; has no member named &#8216;channel&#8217;
       rx_status.band = hw->conf.channel->band;
                                ^
/home/tim/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0516.2013_revison_1-master/base.c: In function &#8216;rtl_send_smps_action&#8217;:
/home/tim/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0516.2013_revison_1-master/base.c:1451:24: error: &#8216;struct ieee80211_conf&#8217; has no member named &#8216;channel&#8217;
   info->band = hw->conf.channel->band;
                        ^
make[2]: *** [/home/tim/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0516.2013_revison_1-master/base.o] Error 1
make[1]: *** [_module_/home/tim/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0516.2013_revison_1-master] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-12-generic'
make: *** [all] Error 2



---

### Post by Tim_Hallett on 2014-01-23
Now I did a make uninstall on my backports package, now no wireless at all: make install on backports did not restore it (yes I rebooted after install)

---

### Post by chili555 on 2014-01-23
> **Tim_Hallett said:**
> Now I did a make uninstall on my backports package, now no wireless at all: make install on backports did not restore it (yes I rebooted after install)Since you have an rtl8188ee, not the subject of this thread, I suggest you start your own new thread. I'll be happy to help.

---

