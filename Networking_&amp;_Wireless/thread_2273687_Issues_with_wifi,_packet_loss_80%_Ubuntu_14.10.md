---
title: "Issues with wifi, packet loss 80% Ubuntu 14.10"
date: 2015-04-14
forum: Networking &amp; Wireless
---

### Post by Jose_Tomas on 2015-04-14
Hi, i'm having issues with WIFI in my home, suddenly it started to fail. I have a W7 partition and the wifi there works great, so no HW problems but in Ubuntu 14.10 really slow connection, sometimes no connection at all and a LOT of packet loss. My notebook is an Acer Aspire S3-391 the script is below where you can see more...
please help I tried a lot of "fixes" but no luck at all.
Thanks a lot!

```


########## wireless info START ##########


Report from: 14 Apr 2015 20:50 CLST -0300


Booted last: 14 Apr 2015 20:44 CLST -0300


Script from: 06 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic


##### kernel ############################


Linux 3.16.0-23-generic #31-Ubuntu SMP Tue Oct 21 17:56:17 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e058]
    Kernel driver in use: ath9k


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e056 Foxconn / Hon Hai 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04f2:b33b Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
ath3k                  13331  0 
ath9k                 136984  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446568  2 ath9k_common,ath9k
ath                    29052  3 ath9k_common,ath9k,ath9k_hw
mac80211              660592  1 ath9k
bluetooth             446190  23 bnep,ath3k,btusb,rfcomm
cfg80211              510218  4 ath,ath9k_common,ath9k,mac80211
wmi                    19193  1 acer_wmi
video                  20128  2 i915,acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6a94:23ff:fe7e:5ff9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17987 (17.9 KB)  TX bytes:23254 (23.2 KB)


##### iwconfig ##########################


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"REY MONO"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'REY MONO' [AC1]>   
          Bit Rate=5.5 Mb/s   Tx-Power=19 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-4 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:44  Invalid misc:5   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no


  Capabilities:


- Device: wlan0  [REY MONO] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           5 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    ESTER:           Infra, <MAC 'ESTER' [AC5]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    claudia:         Infra, <MAC 'claudia' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2
    EDUARDO:         Infra, <MAC 'EDUARDO' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Movistar:        Infra, <MAC 'Movistar' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    -Makita-:        Infra, <MAC '-Makita-' [AC2]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Fernando:        Infra, <MAC 'Fernando' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    correcatacorre:  Infra, <MAC 'correcatacorre' [AN7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Alberto:         Infra, <MAC 'Alberto' [AN8]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 60 WPA2
    MonicaCR:        Infra, <MAC 'MonicaCR' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    *REY MONO:       Infra, <MAC 'REY MONO' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    Fernando Casa Wiffi: Infra, <MAC 'Fernando Casa Wiffi' [AN11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    Fortiwifi LBM GROUP: Infra, <MAC 'Fortiwifi LBM GROUP' [AN12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2


  IPv4 Settings:
    Address:         192.168.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             190.160.0.15
    DNS:             200.83.1.5


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


[[/etc/NetworkManager/system-connections/REY MONO]] (600 root)
[connection] id=REY MONO | type=802-11-wireless
[802-11-wireless] ssid=REY MONO | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: America/Santiago (based on set time zone)


country US: DFS-UNSET
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)


##### iwlist channels ###################


lo        no frequency information.


wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.422 GHz (Channel 3)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'REY MONO' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-20 dBm  
                    Encryption key:on
                    ESSID:"REY MONO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000010971339c5
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '-Makita-' [AC2]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"-Makita-"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011cfb586708
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'claudia' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"claudia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000019b1e331044
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
lo        Interface doesn't support scanning.


          Cell 04 - Address: <MAC 'Movistar' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Movistar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000dcac26ca4e
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'ESTER' [AC5]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"ESTER"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006a3e156c6
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath3k]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     41893A93E7CB53C4981D0FD
depends:        bluetooth
intree:         Y
vermagic:       3.16.0-23-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D1:20:C4:7C:14:BE:B6:2E:AD:67:03:D4:17:12:CC:11:05:75:D2:97
sig_hashalgo:   sha512


[ath9k]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F1B005F210401E25BEA4125
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.16.0-23-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D1:20:C4:7C:14:BE:B6:2E:AD:67:03:D4:17:12:CC:11:05:75:D2:97
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     50297023DA06CB0C907A2CA
depends:        cfg80211,ath9k_hw,ath
intree:         Y
vermagic:       3.16.0-23-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D1:20:C4:7C:14:BE:B6:2E:AD:67:03:D4:17:12:CC:11:05:75:D2:97
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     765883F7BDCD751661973EB
depends:        ath
intree:         Y
vermagic:       3.16.0-23-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D1:20:C4:7C:14:BE:B6:2E:AD:67:03:D4:17:12:CC:11:05:75:D2:97
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     165C1DF76AF8C8B6A45DA4F
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-23-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D1:20:C4:7C:14:BE:B6:2E:AD:67:03:D4:17:12:CC:11:05:75:D2:97
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.16.0-23-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0D5DBE66E4CC44B010DB516
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-23-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D1:20:C4:7C:14:BE:B6:2E:AD:67:03:D4:17:12:CC:11:05:75:D2:97
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.16.0-23-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-23-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D1:20:C4:7C:14:BE:B6:2E:AD:67:03:D4:17:12:CC:11:05:75:D2:97
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 1
ps_enable: 0
use_chanctx: 0


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


##### modprobe options ##################


[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1
blink=1 btcoex_enable=1


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


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x168c:0x0034 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  178.300635] wlan0: authenticate with <MAC 'REY MONO' [AC1]>
[  178.309674] wlan0: send auth to <MAC 'REY MONO' [AC1]> (try 1/3)
[  178.311652] wlan0: authenticated
[  178.315281] wlan0: associate with <MAC 'REY MONO' [AC1]> (try 1/3)
[  178.331597] wlan0: RX AssocResp from <MAC 'REY MONO' [AC1]> (capab=0xc11 status=0 aid=1)
[  178.331676] wlan0: associated
[  178.369590] ath: EEPROM regdomain: 0x8348
[  178.369599] ath: EEPROM indicates we should expect a country code
[  178.369604] ath: doing EEPROM country->regdmn map search
[  178.369608] ath: country maps to regdmn code: 0x3a
[  178.369611] ath: Country alpha2 being used: US
[  178.369614] ath: Regpair used: 0x3a
[  178.369619] ath: regdomain 0x8348 dynamically updated by country IE
[  183.272252] wlan0: authenticate with <MAC 'REY MONO' [AC1]>
[  183.281806] wlan0: send auth to <MAC 'REY MONO' [AC1]> (try 1/3)
[  183.283888] wlan0: authenticated
[  183.287220] wlan0: associate with <MAC 'REY MONO' [AC1]> (try 1/3)
[  183.303565] wlan0: RX AssocResp from <MAC 'REY MONO' [AC1]> (capab=0xc11 status=0 aid=1)
[  183.303641] wlan0: associated
[  183.338414] ath: EEPROM regdomain: 0x8348
[  183.338421] ath: EEPROM indicates we should expect a country code
[  183.338424] ath: doing EEPROM country->regdmn map search
[  183.338426] ath: country maps to regdmn code: 0x3a
[  183.338429] ath: Country alpha2 being used: US
[  183.338431] ath: Regpair used: 0x3a
[  183.338434] ath: regdomain 0x8348 dynamically updated by country IE
[  188.264705] wlan0: authenticate with <MAC 'REY MONO' [AC1]>
[  188.273595] wlan0: send auth to <MAC 'REY MONO' [AC1]> (try 1/3)
[  188.275824] wlan0: authenticated
[  188.279140] wlan0: associate with <MAC 'REY MONO' [AC1]> (try 1/3)
[  188.295485] wlan0: RX AssocResp from <MAC 'REY MONO' [AC1]> (capab=0xc11 status=0 aid=1)
[  188.295558] wlan0: associated
[  188.332528] ath: EEPROM regdomain: 0x8348
[  188.332537] ath: EEPROM indicates we should expect a country code
[  188.332541] ath: doing EEPROM country->regdmn map search
[  188.332545] ath: country maps to regdmn code: 0x3a
[  188.332549] ath: Country alpha2 being used: US
[  188.332552] ath: Regpair used: 0x3a
[  188.332557] ath: regdomain 0x8348 dynamically updated by country IE


########## wireless info END ############



```

---

### Post by jeremy31 on 2015-04-15
Change the router encryption settings to WPA2-AES or WPA2 only and ```
sudo iw reg set CL
``` if you are in Chile

Reboot

---

