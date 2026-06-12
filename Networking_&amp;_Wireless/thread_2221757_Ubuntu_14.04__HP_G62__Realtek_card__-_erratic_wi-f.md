---
title: "Ubuntu 14.04 / HP G62 / Realtek card  - erratic wi-fi behaviour"
date: 2014-05-03
forum: Networking &amp; Wireless
---

### Post by c-nick on 2014-05-03
Hello

I have a clean install of 14.04 and have issues with wi-fi. It worked fine for a few days, then it would fail to connect on resume, and now it won't connect at all. It can see the router, it just won't connect to it.

I have tried to install the correct Realtek drivers, but I think I may have made it worse. Some diagnostics:

> lshw


 *-network
                description: Wireless interface
                product: RTL8191SEvA Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 10
                serial: 1c:65:9d:74:de:aa
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192se driverversion=3.13.0-24-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn


> wpconfig

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

Any help much appreciated - it was fine with 12.04 and has worked with 14.04. 

Thanks

---

### Post by c-nick on 2014-05-03
Results of the script in the sticky:


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux nick-HP-G62-Notebook-PC 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 athlon i686 GNU/Linux

##### lspci #####

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:143b]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:1467]
    Kernel driver in use: rtl8192se

##### lsusb #####

Bus 002 Device 002: ID 5986:0149 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
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

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [VM160156-2G] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    VM160156-2G:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2

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
    Address:         192.168.0.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

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

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"VM160156-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013802558f3
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000B564D3136303135362D3247
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD011BFFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AAD011BFFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 34160B080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8A0050F204104A00011010440001021057000101103B000103104700100CCF92356B07591C9942CFEAD25C3E72102100074E65746765617210230007564D444734383510240007564D44473438351042000D334257333338555830303133391054000800060050F204000110110007564D444734383510080002210C103C0001011049000600372A000120
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"VM160156-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000138026a180
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000B564D3136303135362D3247
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD011BFFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD220050F204104A00011010440001021057000101103C0001011049000600372A000120

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

##### lsmod #####

rtl8192se              58091  0 
rtl_pci                26314  1 rtl8192se
rtlwifi                52835  2 rtl_pci,rtl8192se
mac80211              545990  3 rtl_pci,rtlwifi,rtl8192se
cfg80211              409394  2 mac80211,rtlwifi

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B9B9518158623D8BAB67493
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B6B8AA929B5F982954A6DE1
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     C21FC2F90947540319DE390
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512

##### modules #####

lp

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

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8171 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   14.963596] rtl8192se: FW Power Save off (module option)
[   14.963664] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   14.963664] Loading firmware rtlwifi/rtl8192sefw.bin
[   14.998043] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   18.013629] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.016425] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.962310] wlan0: authenticate with <MAC address removed>
[   18.972655] wlan0: send auth to <MAC address removed> (try 1/3)
[   19.074334] wlan0: send auth to <MAC address removed> (try 2/3)
[   19.178725] wlan0: send auth to <MAC address removed> (try 3/3)
[   19.282496] wlan0: authentication with <MAC address removed> timed out
[   19.443086] wlan0: authenticate with <MAC address removed>
[   19.453114] wlan0: direct probe to <MAC address removed> (try 1/3)
[   19.654876] wlan0: direct probe to <MAC address removed> (try 2/3)
[   19.859051] wlan0: direct probe to <MAC address removed> (try 3/3)
[   20.063208] wlan0: authentication with <MAC address removed> timed out
[   21.039449] wlan0: authenticate with <MAC address removed>
[   21.056683] wlan0: direct probe to <MAC address removed> (try 1/3)
[   21.260186] wlan0: direct probe to <MAC address removed> (try 2/3)
[   21.464318] wlan0: direct probe to <MAC address removed> (try 3/3)
[   21.668527] wlan0: authentication with <MAC address removed> timed out
[   47.180989] wlan0: authenticate with <MAC address removed>
[   47.191262] wlan0: send auth to <MAC address removed> (try 1/3)
[   47.295083] wlan0: send auth to <MAC address removed> (try 2/3)
[   47.399191] wlan0: send auth to <MAC address removed> (try 3/3)
[   47.503315] wlan0: authentication with <MAC address removed> timed out
[   57.576926] wlan0: authenticate with <MAC address removed>
[   57.587810] wlan0: direct probe to <MAC address removed> (try 1/3)
[   57.788758] wlan0: direct probe to <MAC address removed> (try 2/3)
[   57.993099] wlan0: direct probe to <MAC address removed> (try 3/3)
[   58.197366] wlan0: authentication with <MAC address removed> timed out
[   75.224325] wlan0: authenticate with <MAC address removed>
[   75.241301] wlan0: send auth to <MAC address removed> (try 1/3)
[   75.343890] wlan0: send auth to <MAC address removed> (try 2/3)
[   75.448012] wlan0: send auth to <MAC address removed> (try 3/3)
[   75.552134] wlan0: authentication with <MAC address removed> timed out
[   85.621833] wlan0: authenticate with <MAC address removed>
[   85.631873] wlan0: direct probe to <MAC address removed> (try 1/3)
[   85.837724] wlan0: direct probe to <MAC address removed> (try 2/3)
[   86.041947] wlan0: direct probe to <MAC address removed> (try 3/3)
[   86.246251] wlan0: authentication with <MAC address removed> timed out
[  103.268819] wlan0: authenticate with <MAC address removed>
[  103.279737] wlan0: send auth to <MAC address removed> (try 1/3)
[  103.380781] wlan0: send auth to <MAC address removed> (try 2/3)
[  103.484767] wlan0: send auth to <MAC address removed> (try 3/3)
[  103.589005] wlan0: authentication with <MAC address removed> timed out
[  113.654864] wlan0: authenticate with <MAC address removed>
[  113.664890] wlan0: direct probe to <MAC address removed> (try 1/3)
[  113.866467] wlan0: direct probe to <MAC address removed> (try 2/3)
[  114.070774] wlan0: direct probe to <MAC address removed> (try 3/3)
[  114.275011] wlan0: authentication with <MAC address removed> timed out
[  374.188935] wlan0: authenticate with <MAC address removed>
[  374.208319] wlan0: send auth to <MAC address removed> (try 1/3)
[  374.312424] wlan0: send auth to <MAC address removed> (try 2/3)
[  374.416585] wlan0: send auth to <MAC address removed> (try 3/3)
[  374.520763] wlan0: authentication with <MAC address removed> timed out
[  384.594730] wlan0: authenticate with <MAC address removed>
[  384.604939] wlan0: direct probe to <MAC address removed> (try 1/3)
[  384.806253] wlan0: direct probe to <MAC address removed> (try 2/3)
[  385.010478] wlan0: direct probe to <MAC address removed> (try 3/3)
[  385.214704] wlan0: authentication with <MAC address removed> timed out
[  699.894788] wlan0: authenticate with <MAC address removed>
[  699.911916] wlan0: direct probe to <MAC address removed> (try 1/3)
[  700.116097] wlan0: direct probe to <MAC address removed> (try 2/3)
[  700.320430] wlan0: direct probe to <MAC address removed> (try 3/3)
[  700.524604] wlan0: authentication with <MAC address removed> timed out
[  727.094710] wlan0: authenticate with <MAC address removed>
[  727.105985] wlan0: send auth to <MAC address removed> (try 1/3)
[  727.207729] wlan0: send auth to <MAC address removed> (try 2/3)
[  727.311776] wlan0: send auth to <MAC address removed> (try 3/3)
[  727.415979] wlan0: authentication with <MAC address removed> timed out
[  737.489532] wlan0: authenticate with <MAC address removed>
[  737.503272] wlan0: direct probe to <MAC address removed> (try 1/3)
[  737.705407] wlan0: direct probe to <MAC address removed> (try 2/3)
[  737.909718] wlan0: direct probe to <MAC address removed> (try 3/3)
[  738.113980] wlan0: authentication with <MAC address removed> timed out
[  755.122311] wlan0: authenticate with <MAC address removed>
[  755.132499] wlan0: send auth to <MAC address removed> (try 1/3)
[  755.236453] wlan0: send auth to <MAC address removed> (try 2/3)
[  755.340567] wlan0: send auth to <MAC address removed> (try 3/3)
[  755.444722] wlan0: authentication with <MAC address removed> timed out
[  765.522419] wlan0: authenticate with <MAC address removed>
[  765.533415] wlan0: direct probe to <MAC address removed> (try 1/3)
[  765.734294] wlan0: direct probe to <MAC address removed> (try 2/3)
[  765.938510] wlan0: direct probe to <MAC address removed> (try 3/3)
[  766.142760] wlan0: authentication with <MAC address removed> timed out
[  783.168889] wlan0: authenticate with <MAC address removed>
[  783.178957] wlan0: send auth to <MAC address removed> (try 1/3)
[  783.281236] wlan0: send auth to <MAC address removed> (try 2/3)
[  783.385489] wlan0: send auth to <MAC address removed> (try 3/3)
[  783.489618] wlan0: authentication with <MAC address removed> timed out
[  793.607732] wlan0: authenticate with <MAC address removed>
[  793.617819] wlan0: direct probe to <MAC address removed> (try 1/3)
[  793.819170] wlan0: direct probe to <MAC address removed> (try 2/3)
[  794.023329] wlan0: direct probe to <MAC address removed> (try 3/3)
[  794.227684] wlan0: authentication with <MAC address removed> timed out
[ 1109.371840] wlan0: authenticate with <MAC address removed>
[ 1109.385200] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1109.489284] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1109.593244] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1109.697391] wlan0: authentication with <MAC address removed> timed out
[ 1119.766343] wlan0: authenticate with <MAC address removed>
[ 1119.776447] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1119.977785] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1120.182007] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1120.386160] wlan0: authentication with <MAC address removed> timed out
[ 1136.570837] wlan0: authenticate with <MAC address removed>
[ 1136.580966] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1136.683337] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1136.787379] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1136.891439] wlan0: authentication with <MAC address removed> timed out
[ 1146.956029] wlan0: authenticate with <MAC address removed>
[ 1146.966054] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1147.167864] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1147.372118] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1147.576143] wlan0: authentication with <MAC address removed> timed out
[ 1164.562834] wlan0: authenticate with <MAC address removed>
[ 1164.573581] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1164.678134] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1164.782178] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1164.886328] wlan0: authentication with <MAC address removed> timed out
[ 1174.951280] wlan0: authenticate with <MAC address removed>
[ 1174.961353] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1175.162645] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1175.370773] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1175.575016] wlan0: authentication with <MAC address removed> timed out
[ 1192.597404] wlan0: authenticate with <MAC address removed>
[ 1192.610694] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1192.712876] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1192.817064] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1192.921151] wlan0: authentication with <MAC address removed> timed out
[ 1202.986176] wlan0: authenticate with <MAC address removed>
[ 1202.997904] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1203.201542] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1203.405626] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1203.609722] wlan0: authentication with <MAC address removed> timed out
[ 1438.136284] wlan0: authenticate with <MAC address removed>
[ 1438.146933] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1438.248627] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1438.352716] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1438.456832] wlan0: authentication with <MAC address removed> timed out
[ 1448.538381] wlan0: authenticate with <MAC address removed>
[ 1448.548475] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1448.749150] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1448.953336] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1449.157545] wlan0: authentication with <MAC address removed> timed out
[ 1764.843974] wlan0: authenticate with <MAC address removed>
[ 1764.863788] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1764.967275] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1765.071296] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1765.175236] wlan0: authentication with <MAC address removed> timed out
[ 1775.235494] wlan0: authenticate with <MAC address removed>
[ 1775.245587] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1775.446471] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1775.650502] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1775.854665] wlan0: authentication with <MAC address removed> timed out
[ 1792.011182] wlan0: authenticate with <MAC address removed>
[ 1792.022207] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1792.123717] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1792.227733] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1792.331794] wlan0: authentication with <MAC address removed> timed out
[ 1802.395405] wlan0: authenticate with <MAC address removed>
[ 1802.405462] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1802.607056] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1802.811081] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1803.015158] wlan0: authentication with <MAC address removed> timed out
[ 1820.047182] wlan0: authenticate with <MAC address removed>
[ 1820.060448] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1820.164402] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1820.268515] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1820.372553] wlan0: authentication with <MAC address removed> timed out
[ 1830.440580] wlan0: authenticate with <MAC address removed>
[ 1830.450718] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1830.651827] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1830.855834] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1831.059886] wlan0: authentication with <MAC address removed> timed out
[ 1848.059682] wlan0: authenticate with <MAC address removed>
[ 1848.069826] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1848.173287] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1848.277394] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1848.381307] wlan0: authentication with <MAC address removed> timed out
[ 1858.437564] wlan0: authenticate with <MAC address removed>
[ 1858.447662] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1858.648847] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1858.852875] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1859.057015] wlan0: authentication with <MAC address removed> timed out

########## wireless info END ############

---

### Post by c-nick on 2014-05-03
Not sure if I've fixed this myself or not - but thought I'd post in case it helps others as my wifi is working now.

I went back to running 14.04 of a USB stick to check if it worked then, as it had done at first install, and it did the same thing - tried to connect but failed.

I then turned my attention to the router (not sure of the model but it's branded as a Virgin Superhub 2) The laptop seems so far to connect without issue if the 5GHz braodcast is turned off (2.4 and 5 are on by default)

So far this seems to be working well, although it worked well with it turned on for a few days, and also worked fine with both turned on in earlier versions.

---

### Post by c-nick on 2014-05-04
Scratch my previous reply - it doesn't work again now, sadly.

I'd suspect interference, except all the other devices (ipone, android tablet, blackberry playbook) all connect without any problems.

Any help much appreciated. As I've said, it tries to connect to the network, but does not. Except sometimes it does. Thanks in advance.

---

