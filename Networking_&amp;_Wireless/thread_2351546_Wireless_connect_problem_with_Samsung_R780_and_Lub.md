---
title: "Wireless connect problem with Samsung R780 and Lubuntu 14.04"
date: 2017-02-04
forum: Networking &amp; Wireless
---

### Post by nadrach on 2017-02-04
I am trying to make use of several old machines via a USB persistent load of Lubuntu 14.04.  The most promising from a usability view is a Samsung R780. Everything works except the WiFi, which finds a list of connections but cannot connect - keeps asking for the password after timing out. The forums have a lot of past comment about difficulties with drivers and the RealTek RTL8192E/SE wireless chip in this machine, but mostly now old and I keep hitting redundant driver links and package information that is no longer active or extant.  Does anyone have current information as to where I can download a driver/package that will get this combination working? Please note that this is a USB load not an HD, some things are not available because they do not get configured, such as access to partner repositories.

Thank you for any help you can give.

---

### Post by wildmanne39 on 2017-02-04
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by nadrach on 2017-02-05
Script output:
```

########## wireless info START ##########

Report from: 05 Feb 2017 18:52 UTC +0000

Booted last: 05 Feb 2017 18:46 UTC +0000

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.5 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 4.4.0-31-generic #50~14.04.1-Ubuntu SMP Wed Jul 13 01:07:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: file=/cdrom/preseed/lubuntu.seed, boot=casper, quiet, splash, persistent, ---

##### desktop ###########################

Lubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller [10ec:8192] (rev 01)
	Subsystem: Askey Computer Corp. Device [144f:7160]
	Kernel driver in use: rtl819xE

06:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [11ab:4381] (rev 11)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c06a]
	Kernel driver in use: sky2

##### lsusb #############################

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0ac8:c342 Z-Star Microelectronics Corp. 
Bus 001 Device 004: ID 0a5c:219b Broadcom Corp. Bluetooth 2.1 Device
Bus 001 Device 003: ID 13fe:3e00 Kingston Technology Company Inc. Flash Drive
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: samsung-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rtllib_crypt_ccmp      16384  0 
r8192e_pci            135168  0 
rtllib                147456  1 r8192e_pci
lib80211               16384  2 rtllib,rtllib_crypt_ccmp
rtl8192se              65536  0 
rtl_pci                28672  1 rtl8192se
rtlwifi                77824  2 rtl_pci,rtl8192se
mac80211              733184  3 rtl_pci,rtlwifi,rtl8192se
cfg80211              557056  2 mac80211,rtlwifi
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF1]>  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth1' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4950 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3763 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5552217 (5.5 MB)  TX bytes:432755 (432.7 KB)
          Interrupt:19 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3574 (3.5 KB)  TX bytes:2088 (2.0 KB)
          Interrupt:16 Memory:ffffc90000958000-ffffc90000958100 

##### iwconfig ##########################

lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     802.11bgn  ESSID:"PLUSNET-MP7GT3"  Nickname:"rtl8192E"
          Mode:Managed  Frequency=2.452 GHz  Access Point: <MAC 'PLUSNET-MP7GT3' [AC8]>   
          Bit Rate=65 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=89/100  Signal level=-58 dBm  Noise level=-114 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### network managers ##################

Installed:

	NetworkManager

Running:

root      2960     1  0 18:46 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth1  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth1' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

- Device: wlan0  [PLUSNET-MP7GT3] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl819xE
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF2]>

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    VodafoneConnect87890136: Infra, <MAC 'VodafoneConnect87890136' [AC9]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 59 WPA WPA2
    BTHub5-MN3G:     Infra, <MAC 'BTHub5-MN3G' [AC5]>, Freq 2437 MHz, Rate 16 Mb/s, Strength 55 WPA2
    SKY66827:        Infra, <MAC 'SKY66827' [AC2]>, Freq 2412 MHz, Rate 16 Mb/s, Strength 52 WPA2
    SKYD151A:        Infra, <MAC 'SKYD151A' [AC1]>, Freq 2412 MHz, Rate 16 Mb/s, Strength 50 WPA2
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AN5]>, Freq 2437 MHz, Rate 16 Mb/s, Strength 50 WPA WPA2 Enterprise
    SKYA48F3:        Infra, <MAC 'SKYA48F3' [AC6]>, Freq 2437 MHz, Rate 16 Mb/s, Strength 50 WPA2
    TALKTALK-3A47DC: Infra, <MAC 'TALKTALK-3A47DC' [AC7]>, Freq 2437 MHz, Rate 14 Mb/s, Strength 55 WPA WPA2
    TALKTALKCC7BF5:  Infra, <MAC 'TALKTALKCC7BF5' [AC3]>, Freq 2412 MHz, Rate 14 Mb/s, Strength 49 WPA WPA2
    DIRECT-43-HP OfficeJet 4650: Infra, <MAC 'DIRECT-43-HP OfficeJet 4650' [AN9]>, Freq 2412 MHz, Rate 8 Mb/s, Strength 49 WPA2
    TALKTALK03CF6D:  Infra, <MAC 'TALKTALK03CF6D' [AC10]>, Freq 2462 MHz, Rate 2 Mb/s, Strength 59 WPA WPA2
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AC4]>, Freq 2437 MHz, Rate 16 Mb/s, Strength 55
    *PLUSNET-MP7GT3: Infra, <MAC 'PLUSNET-MP7GT3' [AC8]>, Freq 2452 MHz, Rate 16 Mb/s, Strength 89 WPA2
    TALKTALK406C55:  Infra, <MAC 'TALKTALK406C55' [AN13]>, Freq 2412 MHz, Rate 14 Mb/s, Strength 77 WPA WPA2
    TALKTALK9859E8:  Infra, <MAC 'TALKTALK9859E8' [AC11]>, Freq 2412 MHz, Rate 14 Mb/s, Strength 75 WPA WPA2
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AN15]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 65
    BTHub5-SPWG:     Infra, <MAC 'BTHub5-SPWG' [AN16]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 69 WPA2
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AN17]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 72 WPA WPA2 Enterprise

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/PLUSNET-MP7GT3]] (600 root)
[connection] id=PLUSNET-MP7GT3 | type=802-11-wireless
[802-11-wireless] ssid=PLUSNET-MP7GT3 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Etc/UTC (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth1      no frequency information.

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
          Current Frequency:2.452 GHz (Channel 9)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'SKYD151A' [AC1]>
                    ESSID:"SKYD151A"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:144.5 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=74/100  Signal level=-59 dBm  Noise level=-107 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 152ms ago
          Cell 02 - Address: <MAC 'SKY66827' [AC2]>
                    ESSID:"SKY66827"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:144.5 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=71/100  Signal level=-59 dBm  Noise level=-105 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 158ms ago
          Cell 03 - Address: <MAC 'TALKTALKCC7BF5' [AC3]>
                    ESSID:"TALKTALKCC7BF5"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=68/100  Signal level=-59 dBm  Noise level=-104 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 168ms ago
          Cell 04 - Address: <MAC 'BTWifi-with-FON' [AC4]>
                    ESSID:"BTWifi-with-FON"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:144.5 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=63/100  Signal level=-59 dBm  Noise level=-101 dBm
                    Extra: Last beacon: 112ms ago
          Cell 05 - Address: <MAC 'BTHub5-MN3G' [AC5]>
                    ESSID:"BTHub5-MN3G"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:144.5 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=63/100  Signal level=-59 dBm  Noise level=-101 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 112ms ago
          Cell 06 - Address: <MAC 'SKYA48F3' [AC6]>
                    ESSID:"SKYA48F3"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:144.5 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=62/100  Signal level=-59 dBm  Noise level=-101 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 116ms ago
          Cell 07 - Address: <MAC 'TALKTALK-3A47DC' [AC7]>
                    ESSID:"TALKTALK-3A47DC"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=63/100  Signal level=-59 dBm  Noise level=-101 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 102ms ago
          Cell 08 - Address: <MAC 'PLUSNET-MP7GT3' [AC8]>
                    ESSID:"PLUSNET-MP7GT3"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:144.5 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=89/100  Signal level=-59 dBm  Noise level=-114 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 42ms ago
          Cell 09 - Address: <MAC 'VodafoneConnect87890136' [AC9]>
                    ESSID:"VodafoneConnect87890136"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:144.5 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=94/100  Signal level=-59 dBm  Noise level=-117 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 3ms ago
          Cell 10 - Address: <MAC 'TALKTALK03CF6D' [AC10]>
                    ESSID:"TALKTALK03CF6D"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=30/100  Signal level=-59 dBm  Noise level=-85 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 2ms ago
          Cell 11 - Address: <MAC 'TALKTALK9859E8' [AC11]>
                    ESSID:"TALKTALK9859E8"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=63/100  Signal level=-59 dBm  Noise level=-101 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 158ms ago

##### module infos ######################

[rtllib_crypt_ccmp]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/staging/rtl8192e/rtllib_crypt_ccmp.ko
license:        GPL
srcversion:     06930605C9F154555133D4E
depends:        lib80211
staging:        Y
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 

[r8192e_pci]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/staging/rtl8192e/rtl8192e/r8192e_pci.ko
firmware:       RTL8192E/data.img
firmware:       RTL8192E/main.img
firmware:       RTL8192E/boot.img
license:        GPL
version:        0014.0401.2010
author:         Copyright(c) 2008 - 2010 Realsil Semiconductor Corporation <wlanfae@realtek.com>
description:    Linux driver for Realtek RTL819x WiFi cards
srcversion:     6CA8AF3426025342ADBE62E
depends:        rtllib
staging:        Y
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           ifname: Net interface name, wlan%d=default (charp)
parm:           hwwep: Try to use hardware WEP support(default use hw. set 0 to use software security) (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)

[rtllib]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/staging/rtl8192e/rtllib.ko
license:        GPL
srcversion:     9546464B3EDF065B4EA76B5
depends:        lib80211
staging:        Y
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 

[rtl8192se]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     5FB751673BE491FA45BC70B
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 1)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     A96EBF28EBD4603749D5EC3
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     632F2E9C01BF2AC04D0F40A
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[r8192e_pci]
channels: 16383
hwwep: 1
ifname: wlan%d

[rtl8192se]
debug: 0
fwlps: N
ips: Y
swenc: N
swlps: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10de:0x07dc (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x11ab:0x4381 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x10ec:0x8192 (rtl819xE)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   50.084566] sky2 0000:06:00.0 eth1: renamed from eth0
[   50.105953] systemd-udevd[2585]: renamed network interface eth0 to eth1
[   51.136025] rtllib: module is from the staging directory, the quality is unknown, you have been warned.
[   51.278788] r8192e_pci: module is from the staging directory, the quality is unknown, you have been warned.
[   51.279919] rtl819xE 0000:02:00.0: Memory mapped space start: 0xf6800000
[   51.279952] rtl819xE 0000:02:00.0: Adapter(8192 PCI-E) is found - DeviceID=8192
[   51.283162] rtl819xE 0000:02:00.0 wlan0 (uninitialized): _rtl92e_read_eeprom_info(): Invalid EEPROM ID: 4a4
[   53.253383] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   53.266284] sky2 0000:06:00.0 eth1: enabling interface
[   53.266948] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   55.014920] rtl819xE 0000:02:00.0 wlan0: Linking with PLUSNET-MP7GT3,channel:9, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e (repeated 2 times)
[   55.050368] rtl819xE 0000:02:00.0 wlan0: Associated successfully
[   55.050372] rtl819xE 0000:02:00.0 wlan0: normal associate
[   55.050381] rtl819xE 0000:02:00.0 wlan0: Using G rates:108
[   55.050383] rtl819xE 0000:02:00.0 wlan0: Successfully associated, ht enabled
[   55.050764] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   55.064502] rtl819xE 0000:02:00.0 wlan0: RX: IEEE802.1X EAPOL frame! (repeated 2 times)
[   55.085164] rtl819xE 0000:02:00.0 wlan0: alg name:R-CCMP
[   55.100934] rtllib_crypt_ccmp: module is from the staging directory, the quality is unknown, you have been warned.
[   55.102473] rtl819xE 0000:02:00.0 wlan0: alg name:R-CCMP
[   55.254205] rtl819xE 0000:02:00.0 wlan0: _rtl92e_dm_check_edca_turbo():iot peer is broadcom, bssid: <MAC 'PLUSNET-MP7GT3' [AC8]>
[   55.861100] sky2 0000:06:00.0 eth1: Link is up at 100 Mbps, full duplex, flow control rx
[   55.861123] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

########## wireless info END ############


```

---

### Post by praseodym on 2017-02-05
Wow, this card is old ;)

It loads two drivers, try either of them:
```

sudo modprobe -rfv r8192e_pci rtl8192se
```

Load this one:
```

sudo modprobe -v rtl8192se
```
Reconnect. Doesn't work? try the other:
```

sudo modprobe -rfv rtl8192se
sudo modprobe -v r8192e_pci
```

---

### Post by nadrach on 2017-02-06
rtl8192se - no go.
r8192e_pci - works, although on the first time, it degraded service within seconds and connection to the router dropped out. A second halt and restart seems to be working so far (am writing this on that connection).
How/where do I mod the USB setup to start only this driver?

PS ... "Wow, this card is old" ... yup, goes with the age of the machine, but it's not the oldest bit of kit on which I successfully use Lubuntu.
Reuse, recycle and reveal.

Later ... still not right. Although r8192e_pci connects, it can arbitrarily drop out and then fails to reconnect, even while the WiFi data on the task bar network app display shows a valid connection.
Have used Knoppix 7.7.1 successfully on this machine, networking fine, but that comes with LibreOffice 5.2.2 which has a bug regarding Drop Caps that is a nuisance. I prefer Lubuntu, so would rather get it to run in USB form on this machine, with the ability to use on other machines.  Portability is the key intent here.

---

### Post by praseodym on 2017-02-06
No offense, recycling is great :-)

Blacklist the wrong one
```

echo "blacklist rtl8192se" | sudo tee /etc/modprobe.d/blacklist-rtl8192se.conf
```
Reboot

---

### Post by nadrach on 2017-02-14
Blacklisting the rtl8192se driver made no difference.  The WiFi still chokes after a few minutes use, without showing any fault or alarm message or any indication that WiFi is not working, only a lack of access for any download or browser connection. Disconnecting and reconnecting makes no difference, only a reboot clears the situation, and not for very long.
I tested with a Persistent Live USB of Lubuntu 16.04, which showed the same behaviour as the PL USB of Lubuntu 14.04; and also with a PL USB of Knoppix 7.7.1, which seems to work for extended periods, but can also eventually choke (takes 30 minutes +).
Both appear to use the same driver, r8192e_pci.
I ran the wireless_info script on both and got interesting info on both (see below), similar to each other but both very different outputs from running the script on 14.04 (see previous post).
A "diff" on the two latter outputs showed the obvious kernel differences (4.4.0 versus 4.7.9) and some nomenclature (enp2s0/enp6s0 versus eth0/wlan0) but settings otherwise similar (if a little scrambled in order), but one difference was that in Lubuntu the network manager is set > [ifupdown]
managed=false but in Knoppix it is set > [ifupdown]
managed=true
which I presume would affect the way the wireless card is driven.

Script output files attached. The forum did not like them being inserted in tags.[ATTACH]273706[/ATTACH][ATTACH]273707[/ATTACH]

---

