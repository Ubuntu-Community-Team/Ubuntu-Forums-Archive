---
title: "RTL8723BE wifi dropping connection on Ubuntu 14.04"
date: 2014-09-12
forum: Networking &amp; Wireless
---

### Post by pawe3pl on 2014-09-12
Hi. Just like i wrote in the title my wifi connection keeps dropping, but let me tell you the whole story.
After 14.04.1 installation on my Lenovo G50-30 laptop, wifi was hardware blocked, but i've made it work by:
```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
```
and the wifi was on. But when connection is dorpped I can't re-connect. I have to reboot to get my wifi work, but after some time i lose connection again.

I download and ran wireless-script and these are the results:
```


########## wireless info START ##########


Report from: 12 Sep 2014 18:05 CEST +0200


Script from: 05 Sep 2014 22:42 UTC +0000


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop #####


Ubuntu


##### lspci #####


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3816]
    Kernel driver in use: r8169


##### lsusb #####


Bus 001 Device 006: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 5986:0652 Acer, Inc 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 8087:07e6 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info #####


##### rfkill #####


2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #####


rtl8723be              75735  0 
btcoexist              49432  1 rtl8723be
rtl8723_common         22417  1 rtl8723be
rtl_pci                26314  1 rtl8723be
rtlwifi                52835  2 rtl_pci,rtl8723be
mac80211              546051  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              409394  2 mac80211,rtlwifi


##### interfaces #####


auto lo
iface lo inet loopback


##### ifconfig #####


eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2ad2:44ff:fe98:585b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13539 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12056 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8628678 (8.6 MB)  TX bytes:2451401 (2.4 MB)


wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          inet6 addr: fe80::9248:9aff:fe1b:113d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:20263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10941 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28213348 (28.2 MB)  TX bytes:1158074 (1.1 MB)


##### iwconfig #####


lo        no wireless extensions.


eth0      no wireless extensions.


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


- Device: eth0  [Po&#322;&#261;czenie przewodowe 1] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             78.31.136.10
    DNS:             79.124.106.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    NETIASPOT-665F10:Infra, <MAC addr NETIASPOT-665F10>, Freq 2467 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    FON_NETIA_FREE_INTERNET: Infra, <MAC addr FON_NETIA_FREE_INTERNET>, Freq 2467 MHz, Rate 54 Mb/s, Strength 34
    TP-LINK_EF5808:  Infra, <MAC addr TP-LINK_EF5808>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    pawe3:           Infra, <MAC addr pawe3>, Freq 2437 MHz, Rate 54 Mb/s, Strength 78 WPA2
    dlink:           Infra, <MAC addr dlink>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2


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


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels #####


lo        no frequency information.


eth0      no frequency information.


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


##### iwlist scan #####


Channel occupancy:


     1   WLAPs on   Frequency:2.412 GHz (Channel 1)
     2   WLAPs on   Frequency:2.437 GHz (Channel 6)
     2   WLAPs on   Frequency:2.467 GHz (Channel 12)


wlan0     Scan completed :
          Cell 01 - Address: <MAC addr FON_NETIA_FREE_INTERNET>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"FON_NETIA_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000d79a1001
                    Extra: Last beacon: 104ms ago
          Cell 02 - Address: <MAC addr NETIASPOT-665F10>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"NETIASPOT-665F10"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000d79ba007
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC addr pawe3>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"pawe3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000d90da165
                    Extra: Last beacon: 440ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC addr dlink>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000d772b15c
                    Extra: Last beacon: 16088ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC addr TP-LINK_EF5808>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_EF5808"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000d91571e9
                    Extra: Last beacon: 3056ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


##### module infos #####


[rtl8723be]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     0D59E0301AAA6E5A93400BB
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl8723_common]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     D1807280DBDC9B8A7EBDAB7
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512


[rtl_pci]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512


##### module parameters #####


[rtl8723be]
debug: 0
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N


##### /etc/modules #####


lp


##### blacklists #####


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


##### rc.local #####


exit 0


##### udev rules #####


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   13.677060] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   13.917015] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.917362] rtlwifi: wireless switch is on
[   15.810781] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  849.896156] wlan0: authenticate with <MAC addr pawe3>
[  849.916156] wlan0: send auth to <MAC addr pawe3> (try 1/3)
[  849.917691] wlan0: authenticated
[  849.919081] wlan0: associate with <MAC addr pawe3> (try 1/3)
[  849.922575] wlan0: RX AssocResp from <MAC addr pawe3> (capab=0x411 status=0 aid=1)
[  849.922764] wlan0: associated
[  849.922777] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1108.124011] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 1133.053540] wlan0: authenticate with <MAC addr pawe3>
[ 1137.876454] wlan0: send auth to <MAC addr pawe3> (try 1/3)
[ 1137.878912] wlan0: authenticated
[ 1137.882259] wlan0: associate with <MAC addr pawe3> (try 1/3)
[ 1139.051752] wlan0: associate with <MAC addr pawe3> (try 2/3)
[ 1140.065084] wlan0: associate with <MAC addr pawe3> (try 3/3)
[ 1141.066398] wlan0: association with <MAC addr pawe3> timed out
[ 1145.900781] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 1156.454616] wlan0: authenticate with <MAC addr pawe3>
[ 1161.275158] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 1161.275517] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 1191.843256] wlan0: authenticate with <MAC addr pawe3>
[ 1196.665626] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 1196.867637] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 1197.071947] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 1197.276172] wlan0: authentication with <MAC addr pawe3> timed out
[ 1202.110593] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 1213.061628] wlan0: authenticate with <MAC addr pawe3>
[ 1217.885472] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 1217.886256] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 1233.156099] wlan0: authenticate with <MAC addr pawe3>
[ 1237.984260] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 1238.185850] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 1238.390176] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 1238.594405] wlan0: authentication with <MAC addr pawe3> timed out
[ 1243.420828] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 1254.868619] wlan0: authenticate with <MAC addr pawe3>
[ 1259.696326] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 1259.697590] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 1274.962984] wlan0: authenticate with <MAC addr pawe3>
[ 1279.786775] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 1279.988706] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 1280.193038] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 1280.397251] wlan0: authentication with <MAC addr pawe3> timed out
[ 1285.227661] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 1302.324682] wlan0: authenticate with <MAC addr pawe3>
[ 1305.520477] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 1305.722479] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 1305.926745] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 1306.131014] wlan0: authentication with <MAC addr pawe3> timed out
[ 1310.961422] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 1627.775056] wlan0: authenticate with <MAC addr pawe3>
[ 1627.959806] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 1628.161829] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 1628.365987] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 1628.570216] wlan0: authentication with <MAC addr pawe3> timed out
[ 1633.400732] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 1655.804185] wlan0: authenticate with <MAC addr pawe3>
[ 1658.688704] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 1658.890112] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 1659.094326] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 1659.298802] wlan0: authentication with <MAC addr pawe3> timed out
[ 1664.136995] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 1684.597931] wlan0: authenticate with <MAC addr pawe3>
[ 1689.424560] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 1689.626428] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 1689.830723] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 1690.034981] wlan0: authentication with <MAC addr pawe3> timed out
[ 1694.869446] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 1715.334388] wlan0: authenticate with <MAC addr pawe3>
[ 1720.157971] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 1720.358662] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 1720.563713] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 1720.767196] wlan0: authentication with <MAC addr pawe3> timed out
[ 1725.601606] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 2040.179121] wlan0: authenticate with <MAC addr pawe3>
[ 2042.396672] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 2042.598570] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 2042.802754] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 2043.006968] wlan0: authentication with <MAC addr pawe3> timed out
[ 2047.835254] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 2068.289474] wlan0: authenticate with <MAC addr pawe3>
[ 2073.110255] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 2073.311769] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 2073.515903] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 2073.719883] wlan0: authentication with <MAC addr pawe3> timed out
[ 2078.556275] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 2099.016636] wlan0: authenticate with <MAC addr pawe3>
[ 2103.839171] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 2104.040733] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 2104.244726] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 2104.448949] wlan0: authentication with <MAC addr pawe3> timed out
[ 2109.284873] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 2129.734145] wlan0: authenticate with <MAC addr pawe3>
[ 2134.555636] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 2134.757421] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 2134.961619] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 2135.165745] wlan0: authentication with <MAC addr pawe3> timed out
[ 2139.993772] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 2454.541941] wlan0: authenticate with <MAC addr pawe3>
[ 2456.725534] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 2456.927289] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 2457.131420] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 2457.335624] wlan0: authentication with <MAC addr pawe3> timed out
[ 2462.163577] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 2482.622810] wlan0: authenticate with <MAC addr pawe3>
[ 2487.442398] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 2487.644234] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 2487.848447] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 2488.052606] wlan0: authentication with <MAC addr pawe3> timed out
[ 2492.880542] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 2513.334388] wlan0: authenticate with <MAC addr pawe3>
[ 2518.155323] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 2518.357206] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 2518.561438] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 2518.765569] wlan0: authentication with <MAC addr pawe3> timed out
[ 2523.597535] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 2544.050906] wlan0: authenticate with <MAC addr pawe3>
[ 2548.878411] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 2549.082172] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 2549.286411] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 2549.490584] wlan0: authentication with <MAC addr pawe3> timed out
[ 2554.317355] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 2868.845016] wlan0: authenticate with <MAC addr pawe3>
[ 2871.062532] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 2871.264117] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 2871.468224] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 2871.672438] wlan0: authentication with <MAC addr pawe3> timed out
[ 2876.492515] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 2896.941543] wlan0: authenticate with <MAC addr pawe3>
[ 2901.771108] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 2901.973028] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 2902.177181] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 2902.381323] wlan0: authentication with <MAC addr pawe3> timed out
[ 2907.217320] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 2927.667371] wlan0: authenticate with <MAC addr pawe3>
[ 2932.488083] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 2932.689954] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 2932.894148] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 2933.098294] wlan0: authentication with <MAC addr pawe3> timed out
[ 2937.926257] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 2958.393736] wlan0: authenticate with <MAC addr pawe3>
[ 2963.205166] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 2963.406941] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 2963.611236] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 2963.815291] wlan0: authentication with <MAC addr pawe3> timed out
[ 2968.643295] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 3283.190562] wlan0: authenticate with <MAC addr pawe3>
[ 3285.399489] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 3285.600873] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 3285.804990] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 3286.009163] wlan0: authentication with <MAC addr pawe3> timed out
[ 3290.837144] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 3311.296646] wlan0: authenticate with <MAC addr pawe3>
[ 3316.108562] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 3316.309784] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 3316.513976] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 3316.718124] wlan0: authentication with <MAC addr pawe3> timed out
[ 3321.547202] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 3352.147925] wlan0: authenticate with <MAC addr pawe3>
[ 3356.969130] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 3357.171004] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 3357.375163] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 3357.579330] wlan0: authentication with <MAC addr pawe3> timed out
[ 3362.411304] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)
[ 3382.860371] wlan0: authenticate with <MAC addr pawe3>
[ 3387.682048] wlan0: direct probe to <MAC addr pawe3> (try 1/3)
[ 3387.883955] wlan0: direct probe to <MAC addr pawe3> (try 2/3)
[ 3388.088117] wlan0: direct probe to <MAC addr pawe3> (try 3/3)
[ 3388.292289] wlan0: authentication with <MAC addr pawe3> timed out
[ 3393.116549] wlan0: deauthenticating from <MAC addr pawe3> by local choice (reason=3)


########## wireless info END ############
```

Sorry for my bad english. It is not my native language. I looke forward to your help and advice.

---

### Post by varunendra on 2014-09-12
Hello pawel-juchnowski, Welcome to the forums!

Please try a couple of driver parameters available for your driver. In a terminal (can be opened with Ctrl-Alt-T), please run this code (you may copy-paste) to try them -
```
echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot and reconnect. Does it make the connection stable?

And which country you are in? We may have to explicitly set your country code for regdomain settings.

---

### Post by pawe3pl on 2014-09-14
> **varunendra said:**
> 
```
echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

I ran this comman yesterday and connection is stable so far. I can disconnect  manually and reconnect without any problem. So I think that this problem is solved for now. Thanks for help, I appreciate it.

---

### Post by varunendra on 2014-09-14
Thanks for the precious feedback, it makes for two solved threads for this driver so far. :)

---

### Post by pawe3pl on 2014-09-15
I've got another issue. My download transfers are sometimes very high, and sometimes very-very low. On speedtest.net one time my dl speed is at 35mb, and another time is 0.45mb/s. My wifi security settings are WPA2 Personal with AES.

```


########## wireless info START ##########


Report from: 15 Sep 2014 17:32 CEST +0200


Booted last: 15 Sep 2014 17:17 CEST +0200


Script from: 15 Sep 2014 03:40 UTC +0000


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop #####


Ubuntu


##### lspci #####


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Lenovo Device [17aa:b736]
	Kernel driver in use: rtl8723be


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:3816]
	Kernel driver in use: r8169


##### lsusb #####


Bus 001 Device 006: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 5986:0652 Acer, Inc 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 8087:07e6 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info #####


##### rfkill #####


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #####


rtl8723be              75735  0 
btcoexist              49432  1 rtl8723be
rtl8723_common         22417  1 rtl8723be
rtl_pci                26314  1 rtl8723be
rtlwifi                52835  2 rtl_pci,rtl8723be
mac80211              546051  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              409394  2 mac80211,rtlwifi


##### interfaces #####


auto lo
iface lo inet loopback


##### ifconfig #####


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::9248:9aff:fe1b:113d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:493694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:303134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:616922929 (616.9 MB)  TX bytes:123115749 (123.1 MB)


##### iwconfig #####


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"pawe3"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'pawe3' [AP4]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:25   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.1.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [pawe3] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           150 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    NETIASPOT-665F10:Infra, <MAC 'NETIASPOT-665F10' [AP1]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    jmj:             Infra, <MAC 'jmj' [AP2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2
    FON_NETIA_FREE_INTERNET: Infra, <MAC 'FON_NETIA_FREE_INTERNET' [AP3]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 40
    *pawe3:          Infra, <MAC 'pawe3' [AP4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA2
    TP-LINK_F455BE:  Infra, <MAC 'TP-LINK_F455BE' [AP5]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    ShiDek:          Infra, <MAC 'ShiDek' [AP6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    Del siec:        Infra, <MAC 'Del siec' [AP7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2
    barton-net.pl_0: Infra, <MAC 'barton-net.pl_0' [AP8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20
    TP-LINK:         Infra, <MAC 'TP-LINK' [AP9]>, Freq 2437 MHz, Rate 11 Mb/s, Strength 34 WEP
    Marcin:          Infra, <MAC 'Marcin' [AP10]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             78.31.136.10
    DNS:             79.124.106.1


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


##### NetworkManager profiles #####


##### iw reg get #####


Region: Europe/Warsaw (based on set timezone)


country CN:
	(2402 - 2482 @ 40), (N/A, 20)
	(5735 - 5835 @ 40), (N/A, 30)
	(57240 - 59400 @ 2160), (N/A, 28)
	(59400 - 63720 @ 2160), (N/A, 44)
	(63720 - 65880 @ 2160), (N/A, 28)


##### iwlist channels #####


lo        no frequency information.


eth0      no frequency information.


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
          Current Frequency=2.437 GHz (Channel 6)


##### iwlist scan #####


wlan0     Interface doesn't support scanning : Device or resource busy


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


##### module infos #####


[rtl8723be]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     0D59E0301AAA6E5A93400BB
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl8723_common]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     D1807280DBDC9B8A7EBDAB7
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512


[rtl_pci]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #####


[rtl8723be]
debug: 0
fwlps: N
ips: N
msi: N
swenc: N
swlps: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules #####


lp


##### modprobe options #####


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


[/etc/modprobe.d/blacklist-ideapad.conf]
blacklist ideapad_laptop


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=N ips=N


##### rc.local #####


exit 0


##### pm-utils #####


##### udev rules #####


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   13.850672] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   14.042039] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   14.042364] rtlwifi: wireless switch is on
[   16.946401] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   18.760495] wlan0: authenticate with <MAC 'pawe3' [AP4]>
[   18.780049] wlan0: send auth to <MAC 'pawe3' [AP4]> (try 1/3)
[   18.782142] wlan0: authenticated
[   18.783582] wlan0: associate with <MAC 'pawe3' [AP4]> (try 1/3)
[   18.787181] wlan0: RX AssocResp from <MAC 'pawe3' [AP4]> (capab=0x411 status=0 aid=1)
[   18.787273] wlan0: associated
[   18.787309] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   19.140449] wlan0: authenticate with <MAC 'TP-LINK_F455BE' [AP5]>
[   19.151660] wlan0: send auth to <MAC 'TP-LINK_F455BE' [AP5]> (try 1/3)
[   19.153124] wlan0: authenticated
[   19.155895] wlan0: associate with <MAC 'TP-LINK_F455BE' [AP5]> (try 1/3)
[   19.161350] wlan0: RX AssocResp from <MAC 'TP-LINK_F455BE' [AP5]> (capab=0x431 status=0 aid=1)
[   19.161444] wlan0: associated
[   22.168848] wlan0: deauthenticated from <MAC 'TP-LINK_F455BE' [AP5]> (Reason: 2)
[   23.144150] wlan0: authenticate with <MAC 'pawe3' [AP4]>
[   23.164737] wlan0: send auth to <MAC 'pawe3' [AP4]> (try 1/3)
[   23.168262] wlan0: authenticated
[   23.171155] wlan0: associate with <MAC 'pawe3' [AP4]> (try 1/3)
[   23.174735] wlan0: RX AssocResp from <MAC 'pawe3' [AP4]> (capab=0x411 status=0 aid=1)
[   23.174832] wlan0: associated


########## wireless info END ############
```

---

### Post by varunendra on 2014-09-15
Since signal strength and encryption type both are good, power-management also doesn't seem to be an issue anymore, I think there are only two things that may help improving the speed -

**1)** Make sure "IPv6" is set to "Ignore" in Network Manager.

**2)** Try 'swenc=Y' parameter, appending it with the existing ones -
```
sudo sed -i 's/^options.*/& swenc=Y/' /etc/modprobe.d/rtl8723be.conf
```

Some people have reported that the 'swenc' type options actually made their connection worse. So if that happens with you too, remove it with -
```
sudo sed -i 's/ swenc=Y//' /etc/modprobe.d/rtl8723be.conf
```

---

### Post by pawe3pl on 2014-09-18
> **varunendra said:**
> Since signal strength and encryption type both are good, power-management also doesn't seem to be an issue anymore, I think there are only two things that may help improving the speed -

**1)** Make sure "IPv6" is set to "Ignore" in Network Manager.

**2)** Try 'swenc=Y' parameter, appending it with the existing ones -
```
sudo sed -i 's/^options.*/& swenc=Y/' /etc/modprobe.d/rtl8723be.conf
```

Some people have reported that the 'swenc' type options actually made their connection worse. So if that happens with you too, remove it with -
```
sudo sed -i 's/ swenc=Y//' /etc/modprobe.d/rtl8723be.conf
```

1) It did not help.
2) Just like You said, it made my connection worse.

---

### Post by varunendra on 2014-09-19
Which country you currently are in? Your regdomain settings are set to 'CN' (China). If you are not there, we may try setting it to your actual country code so there are no doubts there.

Please also try channels 1 or 11 (or 13, if the router supports that) in the router. Just for a test. Make sure to reboot the router after saving changes in it.

Let us have a fresh wireless-info report after applying the changes.

**PS:**
If the overall current performance is problematic again, I think you should remove the [SOLVED] prefix. It is supposed to indicate at least a 'satisfactory' solution.


--

---

### Post by pawe3pl on 2014-09-20
> **varunendra said:**
> Which country you currently are in? Your regdomain settings are set to 'CN' (China). If you are not there, we may try setting it to your actual country code so there are no doubts there.

I live in Poland. I have changed the crda file:
```
REGDOMAIN=PL
```
But when i run wireless-scritp my country is still CN. Can you tell me how to properly change it please.

BTW: I also changed channels in the router settings. Now it is set on channel 1.

---

### Post by jeremy31 on 2014-09-20
> **pawel-juchnowski said:**
> I live in Poland. I have changed the crda file:
```
REGDOMAIN=PL
```
But when i run wireless-scritp my country is still CN. Can you tell me how to properly change it please.

BTW: I also changed channels in the router settings. Now it is set on channel 1.

You will also need to run ```
sudo iw reg set PL
```

Varunendra, there is some talk on the Linux Mint forum about some of the RTL8723BE problems being fixed in kernel 3.16, so the backports might be a solution

---

### Post by pawe3pl on 2014-09-21
> **jeremy31 said:**
> You will also need to run ```
sudo iw reg set PL
```

I ran this command, but country says 98.

```


########## wireless info START ##########


Report from: 21 Sep 2014 10:25 CEST +0200


Booted last: 21 Sep 2014 10:20 CEST +0200


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Lenovo Device [17aa:b736]
	Kernel driver in use: rtl8723be


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:3816]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 001 Device 006: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 5986:0652 Acer, Inc 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 8087:07e6 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rtl8723be              75735  0 
btcoexist              49432  1 rtl8723be
rtl8723_common         22417  1 rtl8723be
rtl_pci                26314  1 rtl8723be
rtlwifi                52835  2 rtl_pci,rtl8723be
mac80211              546051  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              409394  2 mac80211,rtlwifi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::9248:9aff:fe1b:113d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26927 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:98643117 (98.6 MB)  TX bytes:7594732 (7.5 MB)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"pawe3"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'pawe3' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-20 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [pawe3] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           150 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Kraina:          Infra, <MAC 'Kraina' [AC2]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    NETIASPOT-665F10:Infra, <MAC 'NETIASPOT-665F10' [AC4]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    Maryla:          Infra, <MAC 'Maryla' [AN3]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 37 WPA2
    Daria:           Infra, <MAC 'Daria' [AN4]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 34 WPA2
    FON_NETIA_FREE_INTERNET: Infra, <MAC 'FON_NETIA_FREE_INTERNET' [AC5]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 57
    *pawe3:          Infra, <MAC 'pawe3' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    NETIASPOT-A90A70:Infra, <MAC 'NETIASPOT-A90A70' [AN7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    TP-LINK_F455BE:  Infra, <MAC 'TP-LINK_F455BE' [AC3]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


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


[[/etc/NetworkManager/system-connections/DeltaNet Boguszowice 1]] (600 root)
[connection] id=DeltaNet Boguszowice 1 | type=802-11-wireless
[802-11-wireless] ssid=DeltaNet Boguszowice | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/TP-LINK_8B63EA]] (600 root)
[connection] id=TP-LINK_8B63EA | type=802-11-wireless
[802-11-wireless] ssid=TP-LINK_8B63EA | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/pawe3]] (600 root)
[connection] id=pawe3 | type=802-11-wireless
[802-11-wireless] ssid=pawe3 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/DeltaNet Boguszowice]] (600 root)
[connection] id=DeltaNet Boguszowice | type=802-11-wireless
[802-11-wireless] ssid=DeltaNet Boguszowice | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


Region: Europe/Warsaw (based on set time zone)


country 98:
	(2402 - 2482 @ 40), (N/A, 20)
	(57240 - 59400 @ 2160), (N/A, 28), NO-OUTDOOR
	(59400 - 63720 @ 2160), (N/A, 40), NO-OUTDOOR
	(63720 - 65880 @ 2160), (N/A, 28), NO-OUTDOOR


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


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
          Current Frequency=2.412 GHz (Channel 1)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.467 GHz (Channel 12)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'pawe3' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-20 dBm  
                    Encryption key:on
                    ESSID:"pawe3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000138ce3f4
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Kraina' [AC2]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Kraina"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000143eb7a6b
                    Extra: Last beacon: 2072ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'TP-LINK_F455BE' [AC3]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_F455BE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003662a17d6c
                    Extra: Last beacon: 3136ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'NETIASPOT-665F10' [AC4]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"NETIASPOT-665F10"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000af7535938b
                    Extra: Last beacon: 368ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


eth0      Interface doesn't support scanning.


6F676965731023000F4F70656E524720506C6174666F726D1024000433342E351042000B4E443530303934333831341054000800060050F2040001101100094E4554494153504F54100800020084103C000101
          Cell 05 - Address: <MAC 'FON_NETIA_FREE_INTERNET' [AC5]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"FON_NETIA_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000af75350a09
                    Extra: Last beacon: 364ms ago


##### module infos ######################


[rtl8723be]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     0D59E0301AAA6E5A93400BB
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl8723_common]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     D1807280DBDC9B8A7EBDAB7
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512


[rtl_pci]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8723be]
debug: 0
fwlps: N
ips: N
msi: N
swenc: N
swlps: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp


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


[/etc/modprobe.d/blacklist-ideapad.conf]
blacklist ideapad_laptop


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=N ips=N


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   12.469692] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   12.470033] rtlwifi: wireless switch is on
[   15.162178] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   16.962604] wlan0: authenticate with <MAC 'pawe3' [AC1]>
[   16.982658] wlan0: send auth to <MAC 'pawe3' [AC1]> (try 1/3)
[   16.984108] wlan0: authenticated
[   16.986024] wlan0: associate with <MAC 'pawe3' [AC1]> (try 1/3)
[   16.989515] wlan0: RX AssocResp from <MAC 'pawe3' [AC1]> (capab=0x411 status=0 aid=1)
[   16.989608] wlan0: associated
[   16.989621] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   17.970707] wlan0: deauthenticating from <MAC 'pawe3' [AC1]> by local choice (reason=2)
[   18.001232] wlan0: authenticate with <MAC 'pawe3' [AC1]>
[   18.011471] wlan0: send auth to <MAC 'pawe3' [AC1]> (try 1/3)
[   18.014613] wlan0: authenticated
[   18.018868] wlan0: associate with <MAC 'pawe3' [AC1]> (try 1/3)
[   18.022501] wlan0: RX AssocResp from <MAC 'pawe3' [AC1]> (capab=0x411 status=0 aid=1)
[   18.022596] wlan0: associated


########## wireless info END ############



```

---

### Post by varunendra on 2014-09-23
pawel-juchnowski,

Please show us the outputs of -
```
grep -v $# /etc/default/crda
iw reg get
```
..after running "**sudo iw reg set PL**"

Our friend Hadaka told me once that setting the RegDomain code in the /etc/default/crda file alone was not working as expected, we couldn't find the reason why. But "98" is weird. Do you get some reference to it in the "/usr/share/zoneinfo/zone.tab" file? That is -
```
grep 98 /usr/share/zoneinfo/zone.tab
```

> **jeremy31 said:**
> Varunendra, there is some talk on the Linux Mint forum about some of the RTL8723BE problems being fixed in kernel 3.16, so the backports might be a solution

Thanks for the precious update jeremy, could you give me some links to any such discussion please? No problem if you are busy, I may be able to search this evening.

Just checked the backports-3.16.2-1, and "rtl8723be" does exist in it (it didn't upto backports-3.15.1-1). I'd be very curious to check it out if the crda thing doesn't help.

---

### Post by pawe3pl on 2014-09-24
```
~$ grep -v $# /etc/default/crda
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.


REGDOMAIN=PL
~$ iw reg get
country 98:
	(2402 - 2482 @ 40), (N/A, 20)
	(57240 - 59400 @ 2160), (N/A, 28), NO-OUTDOOR
	(59400 - 63720 @ 2160), (N/A, 40), NO-OUTDOOR
	(63720 - 65880 @ 2160), (N/A, 28), NO-OUTDOOR

```

```
[COLOR=#000000][FONT=Ubuntu Mono]grep 98 /usr/share/zoneinfo/zone.tab[/FONT][/COLOR]
```
This command do nothing.

---

### Post by varunendra on 2014-09-24
Interesting! Looks like something new in 14.04.

Assuming you ran the "iw reg get" command AFTER running "sudo iw reg set PL" as suggested, this can be a problem. But let's first try to search another place to see if this "98" country code exists there.

Does this have the settings pertaining to country code "98"? -
```
regdbdump /lib/crda/regulatory.bin | grep -A6 98
```
Without the "| grep..." part, the above command will show the entire list contained in "regulatory.bin" file.

I know only one more way to force a country code for regdomain settings, but I always thought the "iw reg set" command is the more effective way. I guess we'll figure out soon.

---

### Post by pawe3pl on 2014-09-24
> **varunendra said:**
> Interesting! Looks like something new in 14.04.

Assuming you ran the "iw reg get" command AFTER running "sudo iw reg set PL" as suggested, this can be a problem. 
Yes I was.

> Does this have the settings pertaining to country code "98"? -
```
regdbdump /lib/crda/regulatory.bin | grep -A6 98
```

```
pawel@pawel-laptop:~$ regdbdump /lib/crda/regulatory.bin | grep -A6 98    (5470.000 - 5725.000 @ 40.000), (N/A, 26.98), DFS
    (57240.000 - 65880.000 @ 2160.000), (N/A, 40.00), NO-OUTDOOR


country DE:
    (2400.000 - 2483.500 @ 40.000), (N/A, 20.00)
    (5150.000 - 5250.000 @ 40.000), (N/A, 20.00), NO-OUTDOOR
    (5250.000 - 5350.000 @ 40.000), (N/A, 20.00), NO-OUTDOOR, DFS
    (5470.000 - 5725.000 @ 40.000), (N/A, 26.98), DFS
    (57240.000 - 65880.000 @ 2160.000), (N/A, 40.00), NO-OUTDOOR


country DK:
    (2402.000 - 2482.000 @ 40.000), (N/A, 20.00)
    (5170.000 - 5250.000 @ 40.000), (N/A, 20.00)
    (5250.000 - 5330.000 @ 40.000), (N/A, 20.00), DFS
--
    (5470.000 - 5725.000 @ 40.000), (N/A, 26.98), DFS
    (57240.000 - 65880.000 @ 2160.000), (N/A, 40.00), NO-OUTDOOR


country EU:
    (2402.000 - 2482.000 @ 40.000), (N/A, 20.00)
    (5170.000 - 5250.000 @ 40.000), (N/A, 20.00)
    (5250.000 - 5330.000 @ 40.000), (N/A, 20.00), DFS

```
Does it mean something? :D

---

### Post by varunendra on 2014-09-24
> **pawel-juchnowski said:**
> Does it mean something? :D

Only that even the "regulatory.bin" file doesn't contain any reference to regdomain code "98", so it still remains a mystery where those settings are coming from :confused:

For now, I think it would be a good idea to take jeremy31's advice, and move on to the backported driver.

Please install the kernel headers and build-essential beforehand -
```
sudo apt-get install linux-headers-generic build-essential
```

Then follow these steps to download and install the backported driver -

[INDENT]**1)** Download the "backports-3.16.2-1" package from here : [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)

**2)** Copy the downloaded archive to your Desktop > Right-Click > Extract here.

**3)** Open a terminal (Ctrl-Alt-T) and run these commands to build and install the driver -
```
cd Desktop/backports-3.16.2-1
make defconfig-rtlwifi
make
sudo make install
```
Watch out for errors, and report back if there are any. You may have to reboot for the newer driver to load and work properly.[/INDENT]

Let us know if it is working any better. If not, please post a fresh report of the wireless_script with your comments on the performance.

---

### Post by pawe3pl on 2014-10-05
I have installed the backported driver, but the problem is not solved entirely. Yes, my connection is better. For most of the time it's stable, but sometimes the problem is still noticeable. I 
would  say that I'm satisfied how wifi works for now.

For your info I'm posting wireless script results.
```


########## wireless info START ##########


Report from: 05 Oct 2014 18:23 CEST +0200


Booted last: 05 Oct 2014 15:18 CEST +0200


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:45 UTC 2014 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3816]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 001 Device 006: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 5986:0652 Acer, Inc 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 8087:07e6 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rtl8723be             115035  0 
btcoexist              49393  1 rtl8723be
rtl8723_common         22696  1 rtl8723be
rtl_pci                35067  1 rtl8723be
rtlwifi                84113  2 rtl_pci,rtl8723be
mac80211              479066  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              430998  2 mac80211,rtlwifi
compat                 13617  5 cfg80211,mac80211,btcoexist,rtlwifi,rtl8723be


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::9248:9aff:fe1b:113d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:399630 errors:0 dropped:0 overruns:0 frame:0
          TX packets:289019 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:513186342 (513.1 MB)  TX bytes:35826489 (35.8 MB)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"pawe3"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'pawe3' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-26 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:177   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [pawe3] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           150 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    WirelessNet:     Infra, <MAC 'WirelessNet' [AC4]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    *pawe3:          Infra, <MAC 'pawe3' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 94 WPA2
    FON_NETIA_FREE_INTERNET: Infra, <MAC 'FON_NETIA_FREE_INTERNET' [AC5]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 34
    Asmax:           Infra, <MAC 'Asmax' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    TP-LINK_F455BE:  Infra, <MAC 'TP-LINK_F455BE' [AN5]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Daria:           Infra, <MAC 'Daria' [AN6]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 24 WPA2
    NETIASPOT-72BD80:Infra, <MAC 'NETIASPOT-72BD80' [AN7]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             78.31.136.10
    DNS:             79.124.106.1


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


[[/etc/NetworkManager/system-connections/DeltaNet Boguszowice 1]] (600 root)
[connection] id=DeltaNet Boguszowice 1 | type=802-11-wireless
[802-11-wireless] ssid=DeltaNet Boguszowice | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/TP-LINK_8B63EA]] (600 root)
[connection] id=TP-LINK_8B63EA | type=802-11-wireless
[802-11-wireless] ssid=TP-LINK_8B63EA | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/pawe3]] (600 root)
[connection] id=pawe3 | type=802-11-wireless
[802-11-wireless] ssid=pawe3 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/DeltaNet Boguszowice]] (600 root)
[connection] id=DeltaNet Boguszowice | type=802-11-wireless
[802-11-wireless] ssid=DeltaNet Boguszowice | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


Region: Europe/Warsaw (based on set time zone)


country CN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5735 - 5835 @ 40), (N/A, 30)
    (57240 - 59400 @ 2160), (N/A, 28)
    (59400 - 63720 @ 2160), (N/A, 44)
    (63720 - 65880 @ 2160), (N/A, 28)


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


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
          Current Frequency=2.462 GHz (Channel 11)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      3   APs on   Frequency:2.467 GHz (Channel 12)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'pawe3' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"pawe3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000299f2acdb
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'NETIASPOT-665F10' [AC2]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"NETIASPOT-665F10"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001cfc1087d45
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'FON_NETIA_FREE_INTERNET' [AC3]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"FON_NETIA_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001cfc107ecc3
                    Extra: Last beacon: 80ms ago
          Cell 04 - Address: <MAC 'WirelessNet' [AC4]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"WirelessNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000950277bf16
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'FON_NETIA_FREE_INTERNET' [AC5]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"FON_NETIA_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000027c8b0002
                    Extra: Last beacon: 472ms ago
                    IE: Unknowlo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


n: 0017464F4E5F4E455449415F465245455F494E5445524E4554


##### module infos ######################


[rtl8723be]
filename:       /lib/modules/3.13.0-36-generic/updates/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
version:        backported from Linux (v3.16.2-0-g62de88e) using backports v3.16.2-1-0-g9d017dd
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     C94095C986767A931B924EF
depends:        rtlwifi,rtl8723-common,rtl_pci,compat,btcoexist,mac80211
vermagic:       3.13.0-36-generic SMP mod_unload modversions 686 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl8723_common]
filename:       /lib/modules/3.13.0-36-generic/updates/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
vermagic:       3.13.0-36-generic SMP mod_unload modversions 686 


[rtl_pci]
filename:       /lib/modules/3.13.0-36-generic/updates/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     2A841709EF6A38E777CCD34
depends:        mac80211,rtlwifi
vermagic:       3.13.0-36-generic SMP mod_unload modversions 686 


[rtlwifi]
filename:       /lib/modules/3.13.0-36-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
version:        backported from Linux (v3.16.2-0-g62de88e) using backports v3.16.2-1-0-g9d017dd
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     AEDBFD2C2F64D9D545BF951
depends:        mac80211,compat,cfg80211
vermagic:       3.13.0-36-generic SMP mod_unload modversions 686 


[mac80211]
filename:       /lib/modules/3.13.0-36-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v3.16.2-0-g62de88e) using backports v3.16.2-1-0-g9d017dd
srcversion:     15791DA6391E3692639BAB5
depends:        cfg80211,compat
vermagic:       3.13.0-36-generic SMP mod_unload modversions 686 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.16.2-0-g62de88e) using backports v3.16.2-1-0-g9d017dd
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     67813FD63FE30A8DC22E6B7
depends:        compat
vermagic:       3.13.0-36-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8723be]
debug: 0
fwlps: N
ips: N
msi: N
swenc: N
swlps: N


[mac80211]
beacon_loss_count: 7
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp


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


[/etc/modprobe.d/blacklist-ideapad.conf]
blacklist ideapad_laptop


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=N ips=N


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 5707.434837] wlan0: deauthenticating from <MAC 'pawe3' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 5710.676336] rtlwifi: wireless switch is on
[ 5714.927711] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5715.880353] wlan0: authenticate with <MAC 'pawe3' [AC1]>
[ 5715.890629] wlan0: send auth to <MAC 'pawe3' [AC1]> (try 1/3)
[ 5715.893307] wlan0: authenticated
[ 5715.893575] wlan0: associate with <MAC 'pawe3' [AC1]> (try 1/3)
[ 5715.897180] wlan0: RX AssocResp from <MAC 'pawe3' [AC1]> (capab=0x411 status=0 aid=1)
[ 5715.897270] wlan0: associated
[ 5715.897303] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############

```

And the country line is still CN. :D

---

### Post by varunendra on 2014-10-05
Based on a recent confirmation by one of our forums members 'Martin' [here]("http://ubuntuforums.org/showthread.php?t=2244758&p=13135507#post13135507"), please try "msi=Y" option -
```
sudo sed -i 's/options.*/& msi=Y/' /etc/modprobe.d/rtl8723be.conf
```
..and let us know if it really works. Reboot after doing this.

---

### Post by pawe3pl on 2014-10-09
> **varunendra said:**
> Based on a recent confirmation by one of our forums members 'Martin' [here]("http://ubuntuforums.org/showthread.php?t=2244758&p=13135507#post13135507"), please try "msi=Y" option -
```
sudo sed -i 's/options.*/& msi=Y/' /etc/modprobe.d/rtl8723be.conf
```
..and let us know if it really works. Reboot after doing this.

That command broke my wifi :D, so I had to remove it.

---

### Post by regaladys on 2014-11-12
> **varunendra said:**
> Hello pawel-juchnowski, Welcome to the forums!

Please try a couple of driver parameters available for your driver. In a terminal (can be opened with Ctrl-Alt-T), please run this code (you may copy-paste) to try them -
```
echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot and reconnect. Does it make the connection stable?

And which country you are in? We may have to explicitly set your country code for regdomain settings.

Hi there! What do these commands mean?

---

### Post by regaladys on 2014-11-12
I also have the same driver running on Ubuntu Gnome 14.04, Lenovo G4070.

Here is the output after I ran the recommended network diagnostics from: [URL="http://ubuntuforums.org/showthread.php?t=370108"]http://ubuntuforums.org/showthread.php?t=370108

```


########## wireless info START ##########

Report from: 12 Nov 2014 16:11 PHT +0800

Booted last: 12 Nov 2014 15:33 PHT +0800

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380a]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 5986:014f Acer, Inc 
Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 006: ID 1bbb:2026 T & A Mobile Phones 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be              85118  0 
btcoexist              50304  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                63475  2 rtl_pci,rtl8723be
mac80211              630653  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              484040  2 mac80211,rtlwifi
ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
          inet addr:192.168.42.181  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::b8bd:33ff:fef7:d11b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15962 errors:1 dropped:0 overruns:0 frame:1
          TX packets:17811 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12070822 (12.0 MB)  TX bytes:2343032 (2.3 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.0.1.118  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::162d:27ff:fe6f:657b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5143974 (5.1 MB)  TX bytes:745523 (745.5 KB)

##### iwconfig ##########################

usb0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"murphy's law"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'murphy's law' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-26 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
10.0.1.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: usb0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            cdc_eem
  State:             connected
  Default:           yes
  HW Address:        <MAC 'usb0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.181
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129

- Device: wlan0  [murphy's law] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Charlie Whisky Romeo: Infra, <MAC 'Charlie Whisky Romeo' [AC3]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    bayanDSLWiFi_1660: Infra, <MAC 'bayanDSLWiFi_1660' [AC2]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    *murphy's law:   Infra, <MAC 'murphy's law' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2

  IPv4 Settings:
    Address:         10.0.1.118
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.1.1

    DNS:             10.0.1.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/SFDPH_10]] (600 root)
[connection] id=SFDPH_10 | type=802-11-wireless
[802-11-wireless] ssid=SFDPH_10 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/VISSERF105_24G]] (600 root)
[connection] id=VISSERF105_24G | type=802-11-wireless
[802-11-wireless] ssid=VISSERF105_24G | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/murphy's law]] (600 root)
[connection] id=murphy's law | type=802-11-wireless
[802-11-wireless] ssid=murphy's law | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Eat Katipunan]] (600 root)
[connection] id=Eat Katipunan | type=802-11-wireless
[802-11-wireless] ssid=Eat Katipunan | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/csrclab]] (600 root)
[connection] id=csrclab | type=802-11-wireless
[802-11-wireless] ssid=csrclab | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/bayanDSLWiFi_1660]] (600 root)
[connection] id=bayanDSLWiFi_1660 | type=802-11-wireless
[802-11-wireless] ssid=bayanDSLWiFi_1660 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Delta]] (600 root)
[connection] id=Delta | type=802-11-wireless
[802-11-wireless] ssid=Delta | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/VISSER_2G]] (600 root)
[connection] id=VISSER_2G | type=802-11-wireless
[802-11-wireless] ssid=VISSER_2G | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/csrc_minibar]] (600 root)
[connection] id=csrc_minibar | type=802-11-wireless
[802-11-wireless] ssid=csrc_minibar | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/PLDTMyDSL]] (600 root)
[connection] id=PLDTMyDSL | type=802-11-wireless
[802-11-wireless] ssid=PLDTMyDSL | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/serverthepeople]] (600 root)
[connection] id=serverthepeople | type=802-11-wireless
[802-11-wireless] ssid=serverthepeople | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NIP]] (600 root)
[connection] id=NIP | type=802-11-wireless
[802-11-wireless] ssid=NIP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Manila (based on set time zone)

country PH:
    (2402 - 2482 @ 40), (N/A, 20)
    (5735 - 5835 @ 40), (N/A, 30)

##### iwlist channels ###################

usb0      no frequency information.

eth0      no frequency information.

lo        no frequency information.

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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)

usb0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'murphy's law' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"murphy's law"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000cc69ec7cc1
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'bayanDSLWiFi_1660' [AC2]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"bayanDSLWiFi_1660"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004df441884
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Charlie Whisky Romeo' [AC3]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Charlie Whisky Romeo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004df1b6176
                    Extra: Last beacon: 1080ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     0D59E0301AAA6E5A93400BB
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8723_common]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     D1807280DBDC9B8A7EBDAB7
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  249.127712] wlan0: authenticated
[  249.127946] wlan0: associate with <MAC 'bayanDSLWiFi_1660' [AC2]> (try 1/3)
[  249.131963] wlan0: RX AssocResp from <MAC 'bayanDSLWiFi_1660' [AC2]> (capab=0x411 status=0 aid=3)
[  249.132089] wlan0: associated
[  320.349775] wlan0: Connection to AP <MAC 'bayanDSLWiFi_1660' [AC2]> lost
[  321.790749] wlan0: authenticate with <MAC 'bayanDSLWiFi_1660' [AC2]>
[  321.809754] wlan0: send auth to <MAC 'bayanDSLWiFi_1660' [AC2]> (try 1/3)
[  321.812587] wlan0: authenticated
[  321.813334] wlan0: associate with <MAC 'bayanDSLWiFi_1660' [AC2]> (try 1/3)
[  321.834340] wlan0: RX AssocResp from <MAC 'bayanDSLWiFi_1660' [AC2]> (capab=0x411 status=0 aid=3)
[  321.834495] wlan0: associated
[  325.904485] wlan0: deauthenticated from <MAC 'bayanDSLWiFi_1660' [AC2]> (Reason: 15)
[  441.284387] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  444.657083] wlan0: authenticate with <MAC 'murphy's law' [AC1]>
[  445.130376] wlan0: send auth to <MAC 'murphy's law' [AC1]> (try 1/3)
[  445.134336] wlan0: authenticated
[  445.135060] wlan0: associate with <MAC 'murphy's law' [AC1]> (try 1/3)
[  445.139108] wlan0: RX AssocResp from <MAC 'murphy's law' [AC1]> (capab=0x431 status=0 aid=2)
[  445.139270] wlan0: associated
[  445.139330] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2032.661744] wlan0: deauthenticating from <MAC 'murphy's law' [AC1]> by local choice (reason=3)
[ 2034.224851] wlan0: authenticate with <MAC 'murphy's law' [AC1]>
[ 2034.240567] wlan0: send auth to <MAC 'murphy's law' [AC1]> (try 1/3)
[ 2034.243196] wlan0: authenticated
[ 2034.244166] wlan0: associate with <MAC 'murphy's law' [AC1]> (try 1/3)
[ 2034.248286] wlan0: RX AssocResp from <MAC 'murphy's law' [AC1]> (capab=0x431 status=0 aid=2)
[ 2034.248446] wlan0: associated

########## wireless info END ############



```
[/URL]

---

### Post by chili555 on 2014-11-12
> **regaladys said:**
> Hi there! What do these commands mean?They mean:> parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
There are several reports that the technique Varun suggests cures instability. I recommend you try it and reboot.

I suspect that the instability comes about when a faulty power saving scheme kicks in, reduces the power and the connection drops. Changing these parameters in the driver seems to help. It is easily undone if it's ineffective.

---

### Post by regaladys on 2014-11-26
Thank you very much! This worked for me as well. I was initially hesitating to use the fix because I didn't understand it. Your explanation made me more confident to push "Enter". :)

> **chili555 said:**
> They mean:There are several reports that the technique Varun suggests cures instability. I recommend you try it and reboot.

I suspect that the instability comes about when a faulty power saving scheme kicks in, reduces the power and the connection drops. Changing these parameters in the driver seems to help. It is easily undone if it's ineffective.

---

### Post by vardharajan-kanthe on 2015-04-25
Hey Mr.Genius. This helped me. Thnk you :)

---

### Post by Jean-Francois_Bour on 2015-05-03
I also tried the command suggested c. SInce I did it, no  wireless at all  How may I reverse that command ?  TKS !  I had for now to use another card (USB)  I am using a HP stream 11
echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf

---

### Post by jeremy31 on 2015-05-03
> **Jean-Francois_Bour said:**
> I also tried the command suggested c. SInce I did it, now wireless at all :-)   How may I reverse that command ?  TKS !  I had for now to use another card (USB)  I am using a HP stream 11
echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf

To remove it ```
sudo rm /etc/modprobe.d/rtl8723be.conf
```

Then either reboot or ```
sudo modprobe -r rtl8723be
``````
sudo modprobe rtl8723be
```

---

### Post by Jean-Francois_Bour on 2015-05-03
Tks Jeremy
Removing the file solved my problem

I am still trying to find a more stable driver but at least not I have internet

JF

---

### Post by jeremy31 on 2015-05-03
There are instructions @ [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new) that should be more stable

---

### Post by Jean-Francois_Bour on 2015-05-04
Tks [[COLOR=#000000]jeremy31[/COLOR]]("http://ubuntuforums.org/member.php?u=1924242")[COLOR=#000000]     I will take a look at your link
JF

[/COLOR]

---

### Post by Jean-Francois_Bour on 2015-05-04
Someone could guide me on  how I can use that ???
[https://github.com/lwfinger/rtlwifi_new/commit/85c04eefb705b0b97d32c074e997cfddae6230bd](https://github.com/lwfinger/rtlwifi_new/commit/85c04eefb705b0b97d32c074e997cfddae6230bd)

I come from the WIndows World and I am not a programmer..  ALthough I am a former IT guy

JF
my card is : 
jeff@jeff-HP-Stream-Notebook-PC-11 ~ $ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Hewlett-Packard Company Device [103c:2231]
	Kernel driver in use: rtl8723

---

### Post by Jean-Francois_Bour on 2015-05-04
When using the USB wifi card, cisco,   i am experience same problems
WiFi drop after a while and i can't see wifu networks


JF

---

### Post by chili555 on 2015-05-04
> **Jean-Francois_Bour said:**
> Someone could guide me on  how I can use that ???
[https://github.com/lwfinger/rtlwifi_new/commit/85c04eefb705b0b97d32c074e997cfddae6230bd](https://github.com/lwfinger/rtlwifi_new/commit/85c04eefb705b0b97d32c074e997cfddae6230bd)

I come from the WIndows World and I am not a programmer..  ALthough I am a former IT guy

JF
my card is : 
jeff@jeff-HP-Stream-Notebook-PC-11 ~ $ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Hewlett-Packard Company Device [103c:2231]
	Kernel driver in use: rtl8723I believe the process is:```
sudo apt-get install build-essential linux-headers-generic git
git clone https://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install
sudo depmod -a
```Reboot.

---

### Post by Martin_Heinemann on 2015-06-08
Hello everybody,

I'm quite new to Ubuntu and also to this forum. I bought a Lenovo ThinkPad e555 with a RTL8723BE some days ago and installed Ubuntu 14.04. Everything worked fine, except the WiFi. I tried everything in this post to fix it but nothing helped. I also ran the wifi-info script.

```


########## wireless info START ##########

Report from: 08 Jun 2015 11:39 CEST +0200

Booted last: 08 Jun 2015 11:36 CEST +0200

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:5110]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b444 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be             125222  0 
rtl8723_common         23914  1 rtl8723be
btcoexist              54531  1 rtl8723be
rtl_pci                39740  1 rtl8723be
rtlwifi               105619  2 rtl_pci,rtl8723be
mac80211              627590  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              527699  2 mac80211,rtlwifi
compat                 22752  5 cfg80211,mac80211,btcoexist,rtlwifi,rtl8723be
wmi                    19193  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.178.31  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::6af7:28ff:fe44:b5bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:322567 (322.5 KB)  TX bytes:65422 (65.4 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::7629:afff:fe53:867b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:720 errors:0 dropped:0 overruns:0 frame:0
          TX packets:997 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:368774 (368.7 KB)  TX bytes:147931 (147.9 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 eth0
192.168.178.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search fritz.box

##### network managers ##################

Installed:

    NetworkManager

Running:

root       877     1  0 11:36 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Anmeldefehler:   Infra, <MAC 'Anmeldefehler' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    ALICE-WLAN30:    Infra, <MAC 'ALICE-WLAN30' [AC8]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 87 WPA2
    o2-WLAN58:       Infra, <MAC 'o2-WLAN58' [AC12]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 77 WPA2
    Arcor-89B048:    Infra, <MAC 'Arcor-89B048' [AC14]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    niewiederfranze2:Infra, <MAC 'niewiederfranze2' [AC17]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 67 WPA2
    WLAN-038591:     Infra, <MAC 'WLAN-038591' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA2
    EasyBox-40F062:  Infra, <MAC 'EasyBox-40F062' [AC23]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    WLAN-412513:     Infra, <MAC 'WLAN-412513' [AC15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA2
    EasyBox-360008:  Infra, <MAC 'EasyBox-360008' [AC2]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    Spinnennetz:     Infra, <MAC 'Spinnennetz' [AC22]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 47 WPA2
    I slept with your WiFi.: Infra, <MAC 'I slept with your WiFi.' [AC20]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    Telekom_FON:     Infra, <MAC 'Telekom_FON' [AC11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64
    SETUP:           Ad-Hoc, <MAC 'SETUP' [AC16]>, Freq 2462 MHz, Rate 11 Mb/s, Strength 57
    Bambi & Martin:  Infra, <MAC 'Bambi <MAC 'Bambi <MAC address> Martin' [AN14]> Martin' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    VermuckteKiste:  Infra, <MAC 'VermuckteKiste' [AC29]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    FRITZ!Box 7312:  Infra, <MAC 'FRITZ!Box 7312' [AC26]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    FRITZ!Box Fon WLAN 7270: Infra, <MAC 'FRITZ!Box Fon WLAN 7270' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    KDG-D4DC6:       Infra, <MAC 'KDG-D4DC6' [AC19]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    KD WLAN Hotspot+:Infra, <MAC 'KD WLAN Hotspot+' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47
    KD WLAN Hotspot+:Infra, <MAC 'KD WLAN Hotspot+' [AC32]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44
    KDG-A3892:       Infra, <MAC 'KDG-A3892' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    FRITZ!Box 7330 SL: Infra, <MAC 'FRITZ!Box 7330 SL' [AC18]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    GoBigOrGoHome:   Infra, <MAC 'GoBigOrGoHome' [AC9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    FRITZ!Box 7272:  Infra, <MAC 'FRITZ!Box 7272' [AC24]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Telekom_FON:     Infra, <MAC 'Telekom_FON' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44
    GoeNet:          Infra, <MAC 'GoeNet' [AN26]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    WLAN-852301:     Infra, <MAC 'WLAN-852301' [AC13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    EasyBox-7C7C38:  Infra, <MAC 'EasyBox-7C7C38' [AC21]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    Frische Vollmilch: Infra, <MAC 'Frische Vollmilch' [AC27]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    alles ohne telekom: Infra, <MAC 'alles ohne telekom' [AC28]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    HP-Print-28-Officejet Pro 8600: Infra, <MAC 'HP-Print-28-Officejet Pro 8600' [AC33]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Dave:            Infra, <MAC 'Dave' [AN32]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 44 WEP
    KD WLAN Hotspot+:Infra, <MAC 'KD WLAN Hotspot+' [AC31]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40
    FRITZ!Box 7490:  Infra, <MAC 'FRITZ!Box 7490' [AC34]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    KD WLAN Hotspot+:Infra, <MAC 'KD WLAN Hotspot+' [AC25]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34

- Device: eth0  [Kabelnetzwerkverbindung 1] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.178.31
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.178.1

    DNS:             192.168.178.1

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

[[/etc/NetworkManager/system-connections/Bambi & Martin]] (600 root)
[connection] id=Bambi & Martin | type=802-11-wireless
[802-11-wireless] ssid=Bambi & Martin | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      16   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      5   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Bambi <MAC 'Bambi <MAC address> Martin' [AN14]> Martin' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"Bambi & Martin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003e8267199b
                    Extra: Last beacon: 640ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'EasyBox-360008' [AC2]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-360008"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004bd7be6a703
                    Extra: Last beacon: 704ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 03 - Address: <MAC 'Anmeldefehler' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"Anmeldefehler"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003e4cb16b18e
                    Extra: Last beacon: 840ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'KD WLAN Hotspot+' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"KD WLAN Hotspot+"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001481b5173
                    Extra: Last beacon: 1292ms ago
          Cell 05 - Address: <MAC 'FRITZ!Box Fon WLAN 7270' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7270"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004c7156180
                    Extra: Last beacon: 1680ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Telekom_FON' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"Telekom_FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000176a1816b50
                    Extra: Last beacon: 1056ms ago
          Cell 07 - Address: <MAC 'KDG-A3892' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"KDG-A3892"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000014816a173
                    Extra: Last beacon: 1648ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'ALICE-WLAN30' [AC8]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"ALICE-WLAN30"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000293378a637f
                    Extra: Last beacon: 696ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 09 - Address: <MAC 'GoBigOrGoHome' [AC9]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"GoBigOrGoHome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000045b1c6882d5
                    Extra: Last beacon: 6448ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'WLAN-038591' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"WLAN-038591"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002aeb59a8286
                    Extra: Last beacon: 488ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'Telekom_FON' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:off
                    ESSID:"Telekom_FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002aeb59aa0e9
                    Extra: Last beacon: 544ms ago
          Cell 12 - Address: <MAC 'o2-WLAN58' [AC12]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"o2-WLAN58"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004dbca0846a5
                    Extra: Last beacon: 336ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 13 - Address: <MAC 'WLAN-852301' [AC13]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"WLAN-852301"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000176a17fd18b
                    Extra: Last beacon: 1160ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'Arcor-89B048' [AC14]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Arcor-89B048"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006e181860d06
                    Extra: Last beacon: 420ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'WLAN-412513' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"WLAN-412513"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000015553083ffc
                    Extra: Last beacon: 252ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'SETUP' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"SETUP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000000503abe3abe
                    Extra: Last beacon: 112ms ago
          Cell 17 - Address: <MAC 'niewiederfranze2' [AC17]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"niewiederfranze2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000097b59d0a17
                    Extra: Last beacon: 104ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'FRITZ!Box 7330 SL' [AC18]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7330 SL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000048c0efb1180
                    Extra: Last beacon: 2308ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'KDG-D4DC6' [AC19]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"KDG-D4DC6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000027840590173
                    Extra: Last beacon: 1176ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'I slept with your WiFi.' [AC20]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"I slept with your WiFi."
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000031c63a2894e
                    Extra: Last beacon: 2432ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'EasyBox-7C7C38' [AC21]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-7C7C38"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000039a3a7ed493
                    Extra: Last beacon: 480ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 22 - Address: <MAC 'Spinnennetz' [AC22]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Spinnennetz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c2a14a2734
                    Extra: Last beacon: 468ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC 'EasyBox-40F062' [AC23]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-40F062"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000238d03323
                    Extra: Last beacon: 156ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 24 - Address: <MAC 'FRITZ!Box 7272' [AC24]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7272"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000072cee97180
                    Extra: Last beacon: 16632ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 25 - Address: <MAC 'KD WLAN Hotspot+' [AC25]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"KD WLAN Hotspot+"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013d9f2b6b6c
                    Extra: Last beacon: 16064ms ago
          Cell 26 - Address: <MAC 'FRITZ!Box 7312' [AC26]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7312"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000026fa2cb2180
                    Extra: Last beacon: 172ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 27 - Address: <MAC 'Frische Vollmilch' [AC27]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Frische Vollmilch"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000031c63b79980
                    Extra: Last beacon: 1040ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 28 - Address: <MAC 'alles ohne telekom' [AC28]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"alles ohne telekom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001292d4869de
                    Extra: Last beacon: 5608ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 29 - Address: <MAC 'VermuckteKiste' [AC29]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"VermuckteKiste"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001152647dea1
                    Extra: Last beacon: 20664ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 30 - Address: <MAC 'khazad-dum' [AC30]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"khazad-dum"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013d9f2b615b
                    Extra: Last beacon: 16064ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 31 - Address: <MAC 'KD WLAN Hotspot+' [AC31]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"KD WLAN Hotspot+"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000025b93168b7d
                    Extra: Last beacon: 15728ms ago
          Cell 32 - Address: <MAC 'KD WLAN Hotspot+' [AC32]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"KD WLAN Hotspot+"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000278404af173
                    Extra: Last beacon: 2044ms ago
          Cell 33 - Address: <MAC 'HP-Print-28-Officejet Pro 8600' [AC33]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-28-Officejet Pro 8600"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002511d815f
                    Extra: Last beacon: 672ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 34 - Address: <MAC 'FRITZ!Box 7490' [AC34]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7490"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000008efcb180
                    Extra: Last beacon: 296ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.16.0-38-generic/updates/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
version:        backported from Linux (v4.1-rc1-0-gb787f68c3) using backports v4.1-rc1-1-0-g3fade66
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     35F1A640DD23340CE249D81
depends:        rtlwifi,rtl8723-common,rtl_pci,compat,btcoexist,mac80211
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)

parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl8723_common]
filename:       /lib/modules/3.16.0-38-generic/updates/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     251C540A2D3AD38CCA85ED9
depends:        
vermagic:       3.16.0-38-generic SMP mod_unload modversions 

[rtl_pci]
filename:       /lib/modules/3.16.0-38-generic/updates/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     4FE1180A786042CFCF0B54B
depends:        mac80211,rtlwifi
vermagic:       3.16.0-38-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.16.0-38-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
version:        backported from Linux (v4.1-rc1-0-gb787f68c3) using backports v4.1-rc1-1-0-g3fade66
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B6420B781E0D8DB92A944C0
depends:        mac80211,compat,cfg80211
vermagic:       3.16.0-38-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.16.0-38-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v4.1-rc1-0-gb787f68c3) using backports v4.1-rc1-1-0-g3fade66
srcversion:     D636902288909D427CE5095
depends:        cfg80211,compat
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-38-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v4.1-rc1-0-gb787f68c3) using backports v4.1-rc1-1-0-g3fade66
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C9F7AC0A46FD718291A15A8
depends:        compat
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
disable_watchdog: N
fwlps: N
ips: N
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=N ips=N

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   11.318758] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   11.328368] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   11.328895] rtlwifi: rtlwifi: wireless switch is on
[   14.577207] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.815802] wlan0: authenticate with <MAC 'Bambi <MAC 'Bambi <MAC address> Martin' [AN14]> Martin' [AC1]>
[   15.849041] wlan0: send auth to <MAC 'Bambi <MAC 'Bambi <MAC address> Martin' [AN14]> Martin' [AC1]> (try 1/3)
[   15.855155] wlan0: authenticated
[   15.860680] wlan0: associate with <MAC 'Bambi <MAC 'Bambi <MAC address> Martin' [AN14]> Martin' [AC1]> (try 1/3)
[   15.872395] wlan0: RX AssocResp from <MAC 'Bambi <MAC 'Bambi <MAC address> Martin' [AN14]> Martin' [AC1]> (capab=0x431 status=0 aid=3)
[   15.886224] wlan0: associated
[   15.886246] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  130.432598] wlan0: deauthenticating from <MAC 'Bambi <MAC 'Bambi <MAC address> Martin' [AN14]> Martin' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############



```

I hope you can help me.

---

### Post by chili555 on 2015-06-08
This is evidently the access point you are attempting to join:```
Cell 01 - Address: <MAC 'Bambi <MAC 'Bambi <MAC address> Martin' [AN14]> Martin' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"Bambi & Martin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003e8267199b
                    Extra: Last beacon: 640ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

I also notice this:> ##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
I recommend that your regulatory domain be set explicitly. If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Reboot. Is the stability improved? If not, we will have some additional steps to try.

---

### Post by Martin_Heinemann on 2015-06-08
It works. I can connect to the router, disconnect and connect again :) The connection is quite slow and has a quite high loss ratio (up to 25% with ping to router) but this is better than no connection.

Thank you very much.

---

### Post by Pilot6 on 2015-06-09
I built a ppa with Realtek wireless drivers in DKMS format. It can be installed by

```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-gt install rtlwifi-new-dkms linux-firmware
```

For rtl8192cu USB dongles a standalone driver is better

```
sudo apt-get install rtl8192cu-dkms
```

from same PPA.

But all related configs with blacklists, etc should be deleted from /etc/modprobe.d/

Bluetooth driver is also there

```
sudo apt-get install [COLOR=#333333][FONT=Ubuntu]rtl8723au-bt-dkms[/FONT][/COLOR]
```

---

### Post by kagashe on 2015-06-09
I don't know whether I should start a new thread or not but this is the driver for my wifi card. At present I am on Ubuntu 14.04.2. I also faced this problem and used following command after reading on askubuntu:
```
echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
``` 

Although connection does not drop but I am not happy with this connection and need further advice. If I am not in the room where the router is installed there is a packet loss between the Laptop and the Router which may be due to neighbors using same cahnnel . Even when I am in the room where router is installed there is low speed (it is 1 Mbps connection) and heavy packet loss which may be due to the ISP (I am not sure)

Today I selected "Ignore" for IPv6 after reading on this thread. There is something for the country also which I could not understand. I am from India.

```
########## wireless info START ##########.

Report from: 09 Jun 2015 17:46 IST +0530

Booted last: 09 Jun 2015 12:01 IST +0530

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.16.0-39-generic #53~14.04.1-Ubuntu SMP Wed May 27 10:03:17 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

LXDE

##### lspci #############################

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Lenovo Device [17aa:b736]
	Kernel driver in use: rtl8723be

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:3812]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 004: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 13d3:5727 IMC Networks 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rtl8723be              85054  0 
btcoexist              50304  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                64255  2 rtl_pci,rtl8723be
mac80211              652777  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              494362  2 mac80211,rtlwifi
ideapad_laptop         18278  0 
sparse_keymap          13948  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3ab1:dbff:fe66:e5e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:108428 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79527 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:85964300 (85.9 MB)  TX bytes:14147005 (14.1 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Tikonawifi@8527141818"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Tikonawifi@8527141818' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-10 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4001   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search domain.name

##### network managers ##################

Installed:

	NetworkManager

Running:

root       808     1  0 12:01 ?        00:00:07 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [Tikonawifi@8527141818] ---------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Tata-Photon-Max-Wi-Fi-9159: Infra, <MAC 'Tata-Photon-Max-Wi-Fi-9159' [AC19]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    CHETNA:          Infra, <MAC 'CHETNA' [AC14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    *Tikonawifi@8527141818: Infra, <MAC 'Tikonawifi@8527141818' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    ADISAN:          Infra, <MAC 'ADISAN' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA
    MTNL_01EE5D_1:   Infra, <MAC 'MTNL_01EE5D_1' [AC15]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WEP
    ankur:           Infra, <MAC 'ankur' [AC17]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WEP
    MTNL:            Infra, <MAC 'MTNL' [AC10]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 40 WEP
    Saahil@222:      Infra, <MAC 'Saahil@222' [AC18]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA
    Ankush:          Infra, <MAC 'Ankush' [AC11]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 84 WPA
    Daksh:           Infra, <MAC 'Daksh' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    MTNL:            Infra, <MAC 'MTNL' [AN11]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 40 WPA
    MTNL_1D36CC_1:   Infra, <MAC 'MTNL_1D36CC_1' [AC13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Viren:           Infra, <MAC 'Viren' [AC25]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA
    appu:            Infra, <MAC 'appu' [AC24]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 34 WEP
    vikram:          Infra, <MAC 'vikram' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA
    pk singh:        Infra, <MAC 'pk singh' [AN16]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WEP
    broadcom:        Infra, <MAC 'broadcom' [AN17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA
    Sapphire2014_MTNL: Infra, <MAC 'Sapphire2014_MTNL' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA
    Tata-Docomo-EC315-FE6E: Infra, <MAC 'Tata-Docomo-EC315-FE6E' [AC21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Futerx:          Infra, <MAC 'Futerx' [AC12]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA
    VARUN:           Infra, <MAC 'VARUN' [AN21]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 34 WEP
    Reliance Pro3-894: Infra, <MAC 'Reliance Pro3-894' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2

  IPv4 Settings:
    Address:         192.168.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             113.193.14.18
    DNS:             113.193.1.14

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

[[/etc/NetworkManager/system-connections/Tikonawifi@8527141818 1]] (600 root)
[connection] id=Tikonawifi@8527141818 1 | type=802-11-wireless
[802-11-wireless] ssid=Tikonawifi@8527141818 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/wifi-hotspot~]] (600 root)
[connection] id=wifi-hotspot | type=802-11-wireless
[802-11-wireless] ssid=wifi-hotspot | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tikonawifi@8527141818]] (600 root)
[connection] id=Tikonawifi@8527141818 | type=802-11-wireless
[802-11-wireless] ssid=Tikonawifi@8527141818 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Test~]] (600 root)
[connection] id=Test | type=802-11-wireless
[802-11-wireless] ssid=MYNET | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      8   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      7   APs on   Frequency:2.437 GHz (Channel 6)
      6   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Tikonawifi@8527141818' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-10 dBm  
                    Encryption key:on
                    ESSID:"Tikonawifi@8527141818"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000544dc4b9c
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Daksh' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Daksh"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000138fcc0c0
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Sapphire2014_MTNL' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Sapphire2014_MTNL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000072167217c
                    Extra: Last beacon: 352ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '**WHITEHOUSE**' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"**WHITEHOUSE**"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000019ee51618c
                    Extra: Last beacon: 220ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Reliance Pro3-894' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Reliance Pro3-894"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000000d40318b
                    Extra: Last beacon: 288ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '' [AC6]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000187f7c960
                    Extra: Last beacon: 204ms ago
          Cell 07 - Address: <MAC 'ADISAN' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"ADISAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a15102486
                    Extra: Last beacon: 180ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC '' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008304f154e
                    Extra: Last beacon: 508ms ago
          Cell 09 - Address: <MAC 'vikram' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"vikram"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a13b3364e
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'MTNL' [AC10]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"MTNL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000029d792b46
                    Extra: Last beacon: 12ms ago
          Cell 11 - Address: <MAC 'Ankush' [AC11]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Ankush"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000187cb04e2
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Futerx' [AC12]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Futerx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000083042904d
                    Extra: Last beacon: 1328ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'MTNL_1D36CC_1' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"MTNL_1D36CC_1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000061117bc3d
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'CHETNA' [AC14]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-20 dBm  
                    Encryption key:on
                    ESSID:"CHETNA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a154f578a
                    Extra: Last beacon: 12ms ago
          Cell 15 - Address: <MAC 'MTNL_01EE5D_1' [AC15]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"MTNL_01EE5D_1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a154d1f18
                    Extra: Last beacon: 1764ms ago
          Cell 16 - Address: <MAC '' [AC16]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000024008bdaf
                    Extra: Last beacon: 2456ms ago
          Cell 17 - Address: <MAC 'ankur' [AC17]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"ankur"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000009f2592ec
                    Extra: Last beacon: 12ms ago
          Cell 18 - Address: <MAC 'Saahil@222' [AC18]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Saahil@222"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000024013a44c
                    Extra: Last beacon: 1744ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'Tata-Photon-Max-Wi-Fi-9159' [AC19]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Tata-Photon-Max-Wi-Fi-9159"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000020b3137
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'MTNL_029916_1' [AC20]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"MTNL_029916_1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012b78184c43
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'Tata-Docomo-EC315-FE6E' [AC21]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Tata-Docomo-EC315-FE6E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000d02084
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC '' [AC22]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a13da48b5
                    Extra: Last beacon: 68ms ago
          Cell 23 - Address: <MAC '' [AC23]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a13d59b66
                    Extra: Last beacon: 376ms ago
          Cell 24 - Address: <MAC 'appu' [AC24]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"appu"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000002fae41c4
                    Extra: Last beacon: 84ms ago
          Cell 25 - Address: <MAC 'Viren' [AC25]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Viren"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a13da44bc
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.16.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     C94095C986767A931B924EF
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.16.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        DA:A3:AA:08:EB:36:D4:5D:92:B3:9A:ED:42:79:8A:18:F6:12:CB:D3
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8723_common]
filename:       /lib/modules/3.16.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
intree:         Y
vermagic:       3.16.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        DA:A3:AA:08:EB:36:D4:5D:92:B3:9A:ED:42:79:8A:18:F6:12:CB:D3
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.16.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        DA:A3:AA:08:EB:36:D4:5D:92:B3:9A:ED:42:79:8A:18:F6:12:CB:D3
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.16.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        DA:A3:AA:08:EB:36:D4:5D:92:B3:9A:ED:42:79:8A:18:F6:12:CB:D3
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     376BFDE8E6207B0AAA6339B
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        DA:A3:AA:08:EB:36:D4:5D:92:B3:9A:ED:42:79:8A:18:F6:12:CB:D3
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        DA:A3:AA:08:EB:36:D4:5D:92:B3:9A:ED:42:79:8A:18:F6:12:CB:D3
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
fwlps: N
ips: Y
msi: N
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=0

##### rc.local ##########################

echo 75 > /sys/class/backlight/radeon_bl0/brightness

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   23.682054] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.016613] wlan0: authenticate with <MAC 'Tikonawifi@8527141818' [AC1]>
[   26.028385] wlan0: send auth to <MAC 'Tikonawifi@8527141818' [AC1]> (try 1/3)
[   26.029978] wlan0: authenticated
[   26.031434] wlan0: associate with <MAC 'Tikonawifi@8527141818' [AC1]> (try 1/3)
[   26.036048] wlan0: RX AssocResp from <MAC 'Tikonawifi@8527141818' [AC1]> (capab=0x411 status=0 aid=1)
[   26.036141] wlan0: associated
[   26.036201] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   26.289784] wlan0: deauthenticating from <MAC 'Tikonawifi@8527141818' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   26.322082] wlan0: authenticate with <MAC 'Tikonawifi@8527141818' [AC1]>
[   26.332523] wlan0: send auth to <MAC 'Tikonawifi@8527141818' [AC1]> (try 1/3)
[   26.335564] wlan0: authenticated
[   26.339453] wlan0: associate with <MAC 'Tikonawifi@8527141818' [AC1]> (try 1/3)
[   26.343920] wlan0: RX AssocResp from <MAC 'Tikonawifi@8527141818' [AC1]> (capab=0x411 status=0 aid=1)
[   26.344002] wlan0: associated

########## wireless info END ############

```

Kamalakar

---

### Post by chili555 on 2015-06-09
> **kagashe said:**
> I don't know whether I should start a new thread or not but this is the driver for my wifi card. At present I am on Ubuntu 14.04.2. I also faced this problem and used following command after reading on askubuntu:
```
echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
``` 

Although connection does not drop but I am not happy with this connection and need further advice. If I am not in the room where the router is installed there is a packet loss between the Laptop and the Router which may be due to neighbors using same cahnnel . Even when I am in the room where router is installed there is low speed (it is 1 Mbps connection) and heavy packet loss which may be due to the ISP (I am not sure)

Today I selected "Ignore" for IPv6 after reading on this thread. There is something for the country also which I could not understand. I am from India.

<snip>

I suggest you read and carefully follow all the recommendations I made above. I'm not quite sure how I can explain them any clearer.

---

### Post by kagashe on 2015-06-22
> **chili555 said:**
> I believe the process is:```
sudo apt-get install build-essential linux-headers-generic git
git clone https://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install
sudo depmod -a
```Reboot.As suggested here I installed rtlwifi_new. Although Wifi worked well Bluetooth was not working. For Bluetooth I installed DKMS driver from ppa of Pilot6 but there was a conflict in Bluetooth driver.

To make Bluetooth work I uninstalled rtlwifi_new but my wifi did not work.

Is there any way to restore the default wifi driver of Ubuntu 14.04 so that both wifi and Bluetooth works.

Kamalakar

---

### Post by Pilot6 on 2015-06-22
To get bluetooth work install both modules from my ppa 

sudo apt-get install [COLOR=#333333][FONT=Ubuntu]rtl8723au-bt-dkms rtlwifi-new-dkms linux-firmware[/FONT][/COLOR]

---

### Post by kagashe on 2015-06-22
> **Pilot6 said:**
> To get bluetooth work install both modules from my ppa 

sudo apt-get install [COLOR=#333333][FONT=Ubuntu]rtl8723au-bt-dkms rtlwifi-new-dkms linux-firmware[/FONT][/COLOR]It works. Thank you.

Kamalakar

---

### Post by piscvau on 2015-11-03
Hello,
I am running Xubuntu on a GigabyteP27G2 and my wireless connection keeps dropping.
I have implemented the suggestions of the post (change parameters and country code). But the connection keeps dropping.

Here is the file after modifications.
```

########## wireless info START ##########

Report from: 03 Nov 2015 18:13 CET +0100

Booted last: 03 Nov 2015 15:19 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-66-generic #108-Ubuntu SMP Wed Oct 7 15:20:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:b729]
    Kernel driver in use: rtl8723be

04:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: CLEVO/KAPOK Computer Device [1558:3501]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 5986:055f Acer, Inc 
Bus 003 Device 003: ID 0bda:b002 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 045e:0737 Microsoft Corp. Compact Optical Mouse 500
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be              85118  0 
btcoexist              50304  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                63475  2 rtl_pci,rtl8723be
mac80211              630728  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              484040  2 mac80211,rtlwifi
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.45  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29572722 (29.5 MB)  TX bytes:7597115 (7.5 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.24  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9847 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7649924 (7.6 MB)  TX bytes:1808189 (1.8 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Livebox-0b18"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Livebox-0b18' [AC1]>   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:300   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       913     1  0 15:19 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Ethernet automatique] -----------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.45
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: wlan0  [Livebox-0b18] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Livebox-0b18:   Infra, <MAC 'Livebox-0b18' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 63 WPA2
    Livebox-501d:    Infra, <MAC 'Livebox-501d' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.24
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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


[[/etc/NetworkManager/system-connections/Livebox-0b18]] (600 root)
[connection] id=Livebox-0b18 | type=802-11-wireless
[802-11-wireless] ssid=Livebox-0b18 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FDR632]] (600 root)
[connection] id=FDR632 | type=802-11-wireless
[802-11-wireless] ssid=FDR632 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Nordnet-01B7]] (600 root)
[connection] id=Nordnet-01B7 | type=802-11-wireless
[802-11-wireless] ssid=Nordnet-01B7 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/portthru]] (600 root)
[connection] id=portthru | type=802-11-wireless
[802-11-wireless] ssid=portthru | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/wifipass]] (600 root)
[connection] id=wifipass | type=802-11-wireless
[802-11-wireless] ssid=wifipass | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

country FR:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Livebox-0b18' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Livebox-0b18"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009765aaf74
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Livebox-501d' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Livebox-501d"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009a5b6d036c
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.13.0-66-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     0D59E0301AAA6E5A93400BB
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.13.0-66-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:57:C2:FB:ED:0D:9F:B4:61:EF:AD:39:C9:CC:AF:B5:B5:E0:67:90
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8723_common]
filename:       /lib/modules/3.13.0-66-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     D1807280DBDC9B8A7EBDAB7
depends:        
intree:         Y
vermagic:       3.13.0-66-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:57:C2:FB:ED:0D:9F:B4:61:EF:AD:39:C9:CC:AF:B5:B5:E0:67:90
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.13.0-66-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-66-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:57:C2:FB:ED:0D:9F:B4:61:EF:AD:39:C9:CC:AF:B5:B5:E0:67:90
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-66-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     730FEE1A7696EA37A982482
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-66-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:57:C2:FB:ED:0D:9F:B4:61:EF:AD:39:C9:CC:AF:B5:B5:E0:67:90
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-66-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     CD516ABEC909374CB2C52DC
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-66-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:57:C2:FB:ED:0D:9F:B4:61:EF:AD:39:C9:CC:AF:B5:B5:E0:67:90
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-66-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-66-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:57:C2:FB:ED:0D:9F:B4:61:EF:AD:39:C9:CC:AF:B5:B5:E0:67:90
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    9.314817] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[    9.333219] r8169 0000:04:00.1 eth0: link down
[    9.333268] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   10.183853] wlan0: authenticate with <MAC 'Livebox-0b18' [AC1]>
[   10.196521] wlan0: send auth to <MAC 'Livebox-0b18' [AC1]> (try 1/3)
[   10.198745] wlan0: authenticated
[   10.200064] wlan0: associate with <MAC 'Livebox-0b18' [AC1]> (try 1/3)
[   10.205196] wlan0: RX AssocResp from <MAC 'Livebox-0b18' [AC1]> (capab=0x431 status=0 aid=1)
[   10.205385] wlan0: associated
[   10.205392] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  864.602495] r8169 0000:04:00.1 eth0: link up
[  864.602518] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############



```

I do not know how to ignore IPV6 because this link [http://docs.fedoraproject.org/en-US/...pv6-ignore.png]("http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png")

does not correspond to my configuraiton probably because I am running xubuntu.
How should I do to ignore IPV6.


Any help would be welcomed.

---

### Post by jeremy31 on 2015-11-03
I see no sign of the parameter being changed ```
echo "options rtl8723be fwlps=N" | sudo tee /etc/modprobe.d/rtl8723b3.conf
```
Reboot

I haven't used Xubuntu, so I don't know how you could make the change

---

### Post by piscvau on 2015-11-04
Hello,
At last, I installed the new driver rtl_wifinew, and it seems to work. 
Than you .
Piscvau

---

### Post by anacaona on 2015-11-17
Thank you! I just got a Toshiba Radius 11.6" (Satelletie L15W-B1302). At home it worked fine with run of the mill Linksys and Netgear routers; but the Netgear Nighthawk at work was NOT feeling my little baby. This did the trick!

---

### Post by scattermonster on 2015-12-28
I tried to disable the power saving option by:
```
echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot and reconnect. 

but this only worked after I updated to the latest ubuntu.
Seems stable so far.
thanks

---

### Post by Mihai_Domokos on 2016-01-29
Hello,I am new with Ubuntu and I have the same problem with the wifi and the same network card.
I have tryed everithing what's here but still disconectig after 2 minutes.I have runned this code:
wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
chmod +x wireless-info && \
./wireless-info

---

### Post by Mihai_Domokos on 2016-01-29
And  I get this info:


mihai@mihai-HP-250-G4-Notebook-PC:~$ wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
> chmod +x wireless-info && \
> ./wireless-info
--2016-01-29 13:33:55--  [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info)
Resolving github.com (github.com)... 192.30.252.129
Connecting to github.com (github.com)|192.30.252.129|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) [following]
--2016-01-29 13:33:55--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.31.17.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.31.17.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15868 (15K) [text/plain]
Saving to: ‘wireless-info’

100%[======================================>] 15,868      --.-K/s   in 0s     

Last-modified header missing -- time-stamps turned off.
2016-01-29 13:33:56 (130 MB/s) - ‘wireless-info’ saved [15868/15868]

[sudo] password for mihai:

Results saved in "/home/mihai/wireless-info.txt".

What should I do to get wireles working on my new laptop HP 250 G4 Notebook PC

---

### Post by chili555 on 2016-01-29
> Results saved in "/home/mihai/wireless-info.txt".I suggest you find it and post it here so we can read the diagnostics in order to help you.

Thanks.

---

### Post by Mihai_Domokos on 2016-01-29
> **chili555 said:**
> I suggest you find it and post it here so we can read the diagnostics in order to help you.

Thanks.

########## wireless info START ##########


Report from: 29 Jan 2016 13:33 CET +0100


Booted last: 29 Jan 2016 12:47 CET +0100


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.19.0-47-generic #53~14.04.1-Ubuntu SMP Mon Jan 18 16:09:14 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company Device [103c:8136]
    Kernel driver in use: r8169


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:804c]
    Kernel driver in use: rtl8723be


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b52d Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 1ea7:0066  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
rtl8723be              94208  0 
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                73728  2 rtl_pci,rtl8723be
mac80211              708608  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              524288  2 mac80211,rtlwifi
wmi                    20480  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7531 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12316692 (12.3 MB)  TX bytes:808421 (808.4 KB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1951 errors:0 dropped:0 overruns:0 frame:0
          TX packets:878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:268083 (268.0 KB)  TX bytes:123423 (123.4 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"ARRIS-B992"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'ARRIS-B992' [AN1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       827     1  0 12:47 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [ARRIS-B992] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *ARRIS-B992:     Infra, <MAC 'ARRIS-B992' [AN1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA2


  IPv4 Settings:
    Address:         192.168.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             88.84.0.30
    DNS:             88.84.0.60


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             88.84.0.30
    DNS:             88.84.0.60


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


[[/etc/NetworkManager/system-connections/ARRIS-B992]] (600 root)
[connection] id=ARRIS-B992 | type=802-11-wireless
[802-11-wireless] ssid=ARRIS-B992 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Zurich (based on set time zone)


country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


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


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


wlan0     Failed to read scan data : Resource temporarily unavailable


lo        Interface doesn't support scanning.


##### module infos ######################


[rtl8723be]
filename:       /lib/modules/3.19.0-47-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     B60F970654516A3D2F6FC24
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.19.0-47-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        83:35:C3:0C:F4:5A:C8:87:4B:83:81:61:92:BF:33:DD:DC:B5:32:B6
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)


[rtl8723_common]
filename:       /lib/modules/3.19.0-47-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     251C540A2D3AD38CCA85ED9
depends:        
intree:         Y
vermagic:       3.19.0-47-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        83:35:C3:0C:F4:5A:C8:87:4B:83:81:61:92:BF:33:DD:DC:B5:32:B6
sig_hashalgo:   sha512


[rtl_pci]
filename:       /lib/modules/3.19.0-47-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     A25DC6D8C53D55DA133BC49
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.19.0-47-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        83:35:C3:0C:F4:5A:C8:87:4B:83:81:61:92:BF:33:DD:DC:B5:32:B6
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.19.0-47-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     35016235A31CEB1854418E1
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-47-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        83:35:C3:0C:F4:5A:C8:87:4B:83:81:61:92:BF:33:DD:DC:B5:32:B6
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.19.0-47-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     47672A7084D52DFBE51E2D2
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-47-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        83:35:C3:0C:F4:5A:C8:87:4B:83:81:61:92:BF:33:DD:DC:B5:32:B6
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-47-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-47-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        83:35:C3:0C:F4:5A:C8:87:4B:83:81:61:92:BF:33:DD:DC:B5:32:B6
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8723be]
debug: 0
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N


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


lp
rtc


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   15.716572] r8169 0000:02:00.0 eth0: link down (repeated 2 times)
[   15.716626] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.286382] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.200512] wlan0: authenticate with <MAC 'ARRIS-B992' [AN1]>
[   17.212975] wlan0: send auth to <MAC 'ARRIS-B992' [AN1]> (try 1/3)
[   17.215602] wlan0: authenticated
[   17.219045] wlan0: associate with <MAC 'ARRIS-B992' [AN1]> (try 1/3)
[   17.235597] wlan0: RX AssocResp from <MAC 'ARRIS-B992' [AN1]> (capab=0xc11 status=0 aid=3)
[   17.236442] wlan0: associated
[   17.236450] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   19.440004] r8169 0000:02:00.0 eth0: link up
[   19.440012] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


########## wireless info END ############

---

### Post by chili555 on 2016-01-29
Please open the terminal and copy and paste this command:```
echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```Reboot and tell us if connectivity is improved.

---

### Post by Mihai_Domokos on 2016-01-30
Hello,it looks to be ok,is not dropping anymore,if it will dropp again i let you know.
Thank you very much for your help.

---

### Post by lapicero2 on 2016-02-05
I installed the ppa but i received this answer:  No se ha podido localizar el paquete rtl8723au-bt-dkms   (could not find) 
and  when I tried to get bluetooth  I received this system error : executable path usb/bin/marco....

I added repository but received a message: No se ha podido localizar el paquete rtl8723au-bt-dkms
could not find the packet, any help? and thanks a lot

---

### Post by Pilot6 on 2016-02-05
Did you run 

sudo apt-get update

?

---

