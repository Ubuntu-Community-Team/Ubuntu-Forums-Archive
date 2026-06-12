---
title: "No connection from suspend"
date: 2013-12-15
forum: Networking &amp; Wireless
---

### Post by Alan_Dean on 2013-12-15
I have no problem at all connecting to the internet from booting. However when starting from suspend (which I use a lot) it won't connect. Is this a bug in 13.10? - didn't have this issue with 12.04

Thanks

Alan

---

### Post by varunendra on 2013-12-15
Welcome to the forums Alan ! :)

Looking at your card and driver may give us more clue to be able to tell if it is some known bug or not. A detailed report would be much better.

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by Alan_Dean on 2013-12-15
Thank you for replying.As I said starting from Suspend Ubuntu loads but sometimes freezes and everytime will not pick up the internet connection

Components:
NVIDIA GeForce 9400 GT 
AMD Phenom(tm) II X4 955 Processor 
Edimax Wireless EW-11g

```


*************** info trace ***************

***** uname -a *****

Linux alan-System-Product-Name 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:07:40 UTC 2013 i686 athlon i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

03:05.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
    Subsystem: Ralink corp. EW-7108PCg/EW-7128g [1814:2561]
    Kernel driver in use: rt61pci
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: r8169

***** lsusb *****

Bus 003 Device 002: ID 1e3d:8246 Chipsbank Microelectronics Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 059b:007e Iomega Corp. Mini 256MB/512MB Flash Drive [IOM2D5]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 04f9:0027 Brother Industries, Ltd HL-2030 Laser Printer
Bus 004 Device 002: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bg  ESSID:"SKY2ED89"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:87   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rt61pci                27249  0 
rt2x00pci              13111  1 rt61pci
rt2x00mmio             13395  1 rt61pci
rt2x00lib              48854  3 rt61pci,rt2x00pci,rt2x00mmio
mac80211              513247  2 rt2x00lib,rt2x00pci
cfg80211              401436  2 mac80211,rt2x00lib
eeprom_93cx6           13168  1 rt61pci
crc_itu_t              12627  2 rt61pci,firewire_core

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [SKY2ED89] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt61pci
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Orange-c32fc5:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    TP-LINK51:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    brian&terry:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WEP
    BTHomeHub-2DCC:  Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 30 WEP
    BTOpenzone-H:    Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 30
    BTWiFi:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27
    *SKY2ED89:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA2
    BTHub3-CTNH:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    BTWiFi-with-FON: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30

  IPv4 Settings:
    Address:         192.168.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1



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
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"SKY2ED89"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009586b966c
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 0008534B593245443839
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: DD800050F204104A0001101044000102103B00010310470010F82E373765F1972552AAEB958E8758E81021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D415010080002200C103C0001011049000600372A000120
                    IE: Unknown: DD090010180202F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK51"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004591118713
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 000954502D4C494E4B3531
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050000157A12
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C336E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401000100000000000000000000000000000000000000
                    IE: Unknown: DD9F0050F204104A0001101044000102103B00010310470010BC329E001DD811B28601F8D1119540FD1021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000B5472656E64436869704150100800020084103C000100
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"brian&terry"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000351a143ac22
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 000B627269616E267465727279
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD06001018010001
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-CTNH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009c3be618d
                    Extra: Last beacon: 232ms ago
                    IE: Unknown: 000B4254487562332D43544E48
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001500000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180204F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009c3a89026
                    Extra: Last beacon: 1664ms ago
                    IE: Unknown: 000F4254576946692D776974682D464F4E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001500000000000000000000000000000000000000
                    IE: Unknown: DD090010180204F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Orange-c32fc5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000ba3281fa
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 000D4F72616E67652D633332666335
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706444520010D14
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
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4E1003FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606051800000000000000000000000000000000000000
                    IE: Unknown: DD970050F204104A0001101044000102103B00010310470010824FF22B8C7D41C5A13144F534E12555102100074E455447454152102300164E4554474541522044474E3130303020526F757465721024000A312E30302E33395F52471042000831323334353637381054000800060050F2040001101100164E4554474541522044474E3130303020526F757465721008000201AA103C000103
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 07 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub-2DCC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000028a576ed18e
                    Extra: Last beacon: 1792ms ago
                    IE: Unknown: 000E4254486F6D654875622D32444343
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 08 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone-H"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000028a576f5169
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 000C42544F70656E7A6F6E652D48
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009c3bffa12
                    Extra: Last beacon: 128ms ago
                    IE: Unknown: 0006425457694669
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001500000000000000000000000000000000000000
                    IE: Unknown: DD090010180204F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


***** resolv.conf *****

nameserver 127.0.1.1
search Home

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

filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CF4BCBAB2D8E09C275F85E4
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00mmio,rt2x00pci,eeprom_93cx6,crc-itu-t
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     BD4DED63CAE52A1875B21D1
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     2C5ADAF564EF1DAD569D9C3
depends:        rt2x00lib
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     8AE9D454A710B1C25F9F518
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:0x0301 (rt61pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   14.250800] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2561, rf: 0003, rev: 000c
[   22.086587] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2561s.bin'
[   22.121965] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.8
[   22.162213] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.162417] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.135146] wlan0: authenticate with <MAC address removed>
[   25.150943] wlan0: send auth to <MAC address removed> (try 1/3)
[   25.153847] wlan0: authenticated
[   25.154897] wlan0: associate with <MAC address removed> (try 1/3)
[   25.159661] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[   25.159819] wlan0: associated
[   25.159826] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  365.332767] ieee80211 phy0: rt61pci_txdone: Warning - TX status report missed for entry 24

****************** done ******************

```

Thanks

Alan

---

### Post by varunendra on 2013-12-15
Hmm.. please do (after a suspend --> resume) -
```
cat /var/log/pm-suspend.log > alan.txt
echo -e "\n\n\n====syslog====\n" >> alan.txt
cat /var/log/syslog | egrep -i 'rt2|rt61|wlan|network|avahi' >> alan.txt
```
then find the file "alan.txt" in your home directory and paste its contents to [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/) and give us the URL of the paste it gives you.

And.... did this start with a fresh install of 13.10 or after an update?

---

### Post by Alan_Dean on 2013-12-16
Thank you for the reply Varunendra. Yes the issue is with 13.10 after fresh install (in fact 2 fresh installs) there is no problem with 12.04 LTS

[http://pastebin.ubuntu.com/6582762/](http://pastebin.ubuntu.com/6582762/)

Thanks

Alan

---

### Post by Alan_Dean on 2013-12-16
Tried it again still blanks 

[http://pastebin.ubuntu.com/6583104/](http://pastebin.ubuntu.com/6583104/)

---

### Post by varunendra on 2013-12-18
Since you don't seem to be using IPv6, I suggest completely using method suggested in this post : [http://ubuntuforums.org/showpost.php?p=12640479](http://ubuntuforums.org/showpost.php?p=12640479)

Restart networking (sudo service networking restart && sudo service network-manager restart) or simply reboot after that.

If that makes no difference, try this (copy-paste exactly as below) -
```
echo "SUSPEND_MODULES=\"\$SUSPEND_MODULES rt61pci rt2x00pci rt2x00lib\"" | sudo tee -a /etc/pm/config.d/modules
```
This will create a file "modules" in /etc/pm/config.d/ directory with a single line as echoed in the terminal. This specifically unloads the specified modules before going to sleep (suspend) and reloads them after resuming.

Let us see if that fixes the issue. If not, I guess the next thing to try would be to install a newer, backported driver.

---

### Post by nilarimogard2 on 2013-12-18
This is what worked for me, for both wireless and wired networks: [http://www.webupd8.org/2013/01/fix-wireless-or-wired-network-not.html](http://www.webupd8.org/2013/01/fix-wireless-or-wired-network-not.html)

---

