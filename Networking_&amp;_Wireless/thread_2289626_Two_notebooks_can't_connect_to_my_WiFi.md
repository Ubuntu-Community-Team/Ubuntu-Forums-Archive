---
title: "Two notebooks can't connect to my WiFi"
date: 2015-08-05
forum: Networking &amp; Wireless
---

### Post by pavelexpertov on 2015-08-05
I have received two notebooks (each with atom processor and 1 gig ram), for making productive work with them. However, I have noticed an odd behaviour on them. 
Even though these laptops come from HP and Acer individually, they can't connect to my wifi.
I typed in the ifconfig and I see both of the wlan0 data (even though network manager did show other wifi spots).
I installed lubuntu 15.04 32-bit recently and no updates were made.
My other linux laptop can connect to my wifi (it runs linux mint).
Does anyone have solution to this odd behaviour?

ps. notebooks are acer aspire one and hp mini.

---

### Post by pavelexpertov on 2015-08-05
Hello, I found this shell script in the sticky and I got some info about my notebooks.
Aspire:
```


########## wireless info START ##########

Report from: 05 Aug 2015 21:06 BST +0100

Booted last: 05 Aug 2015 21:03 BST +0100

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:01 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Acer Incorporated [ALI] Device [1025:0349]
    Kernel driver in use: atl1c

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e016]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 001 Device 003: ID 0402:9665 ALi Corp. Gateway Webcam
Bus 001 Device 002: ID 0781:5580 SanDisk Corp. SDCZ80 Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                 135168  0 
ath9k_common           32768  1 ath9k
acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
ath9k_hw              442368  2 ath9k_common,ath9k
ath                    24576  3 ath9k_common,ath9k,ath9k_hw
mac80211              626688  1 ath9k
cfg80211              462848  4 ath,ath9k_common,ath9k,mac80211
wmi                    20480  1 acer_wmi
video                  20480  2 i915,acer_wmi

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
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       507     1  0 21:04 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9285 Wireless Network Adapter (PCI-Express)
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 3.19.0-15-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   cd60d782-59cf-4116-82d3-32dbedbdcae3 | TALKTALK-40B874
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8152 v1.1 Fast Ethernet
GENERAL.DRIVER:                         atl1c
GENERAL.DRIVER-VERSION:                 1.0.1.1-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off

SSID                             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
TALKTALK-40B874                  <MAC 'TALKTALK-40B874' [AC5]>  Infra  7     2442 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA1 WPA2         no        
BTWifi-X                         <MAC 'BTWifi-X' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2 802.1X  no        
SKY6EEE7                         <MAC 'SKY6EEE7' [AC7]>  Infra  11    2462 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2              no        
BTHub5-3Q86                      <MAC 'BTHub5-3Q86' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2              no        
HP-Print-B3-Deskjet 2540 series  <MAC 'HP-Print-B3-Deskjet 2540 series' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2              no        
SKY5CF4D                         <MAC 'SKY5CF4D' [AC6]>  Infra  6     2437 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2         no        
BTWifi-with-FON                  <MAC 'BTWifi-with-FON' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  --                no        

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

[[/etc/NetworkManager/system-connections/TALKTALK-40B874]] (600 root)
[connection] id=TALKTALK-40B874 | type=wifi
[wifi] ssid=TALKTALK-40B874 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'BTHub5-3Q86' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-3Q86"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000de47f474f
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'HP-Print-B3-Deskjet 2540 series' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-B3-Deskjet 2540 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001292bf137b0
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'BTWifi-with-FON' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000de4808943
                    Extra: Last beacon: 12ms ago
          Cell 04 - Address: <MAC 'BTWifi-X' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000de4802de7
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC 'TALKTALK-40B874' [AC5]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-40B874"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ac22b67dc
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'SKY5CF4D' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"SKY5CF4D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003cb1358dfa
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'SKY6EEE7' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"SKY6EEE7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000027d3df092d
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     6D1C555B730584789ECF3D1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     A56979050039F8CEE854254
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     B939F479DFC4E7D2480150B
depends:        ath
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-15-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F518BE1BD732F328C9E430B
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-15-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     268045EBCFAFDADD136DCF6
depends:        
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0

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
# PCI device 0x1969:0x2060 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   18.380979] ath: phy0: Enable LNA combining
[   18.383572] ath: phy0: ASPM enabled: 0x42
[   18.383581] ath: EEPROM regdomain: 0x65
[   18.383585] ath: EEPROM indicates we should expect a direct regpair map
[   18.383592] ath: Country alpha2 being used: 00
[   18.383595] ath: Regpair used: 0x65

########## wireless info END ############



```

HP mini:

```


########## wireless info START ##########

Report from: 05 Aug 2015 21:11 BST +0100

Booted last: 05 Aug 2015 21:10 BST +0100

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:01 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:148a]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:145c]
    Kernel driver in use: bcma-pci-bridge

##### lsusb #############################

Bus 001 Device 002: ID 04f2:b1eb Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0781:5580 SanDisk Corp. SDCZ80 Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

brcmsmac              540672  0 
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
b43                   401408  0 
mac80211              626688  2 b43,brcmsmac
cfg80211              462848  3 b43,brcmsmac,mac80211
ssb                    57344  1 b43
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
bcma                   49152  3 b43,brcmsmac
wmi                    20480  1 hp_wmi

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
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       534     1  0 21:10 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4313 802.11bgn Wireless Network Adapter
GENERAL.DRIVER:                         brcmsmac
GENERAL.DRIVER-VERSION:                 3.19.0-15-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/bcma0:1/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   fdecd007-74b3-46d5-a6d6-ff5b5dcd1733 | TALKTALK-40B874
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off

SSID                             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
BTHub5-3Q86                      <MAC 'BTHub5-3Q86' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2              no        
BTWifi-X                         <MAC 'BTWifi-X' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2 802.1X  no        
SKY6EEE7                         <MAC 'SKY6EEE7' [AC6]>  Infra  11    2462 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA2              no        
SKY73B2C                         <MAC 'SKY73B2C' [AC9]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2         no        
VM910497-2G                      <MAC 'VM910497-2G' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  24      &#9602;___  WPA1 WPA2         no        
SKY5CF4D                         <MAC 'SKY5CF4D' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2         no        
BTWifi-with-FON                  <MAC 'BTWifi-with-FON' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  52      &#9602;&#9604;__  --                no        
TALKTALK-40B874                  <MAC 'TALKTALK-40B874' [AC10]>  Infra  7     2442 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2         no        
HP-Print-B3-Deskjet 2540 series  <MAC 'HP-Print-B3-Deskjet 2540 series' [AC7]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2              no        
BTWifi-X                         <MAC 'BTWifi-X' [AC8]>  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2 802.1X  no        
BTWifi-with-FON                  <MAC 'BTWifi-with-FON' [AN11]>  Infra  11    2462 MHz  54 Mbit/s  24      &#9602;___  --                no        
BTWifi-with-FON                  <MAC 'BTWifi-with-FON' [AN12]>  Infra  6     2437 MHz  54 Mbit/s  22      &#9602;___  --                no        
BTHub5-TSTP                      <MAC 'BTHub5-TSTP' [AN13]>  Infra  6     2437 MHz  54 Mbit/s  22      &#9602;___  WPA2              no        
BTWifi-X                         <MAC 'BTWifi-X' [AN14]>  Infra  11    2462 MHz  54 Mbit/s  24      &#9602;___  WPA1 WPA2 802.1X  no        
SKY97DE1                         <MAC 'SKY97DE1' [AC11]>  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WPA2              no        

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

Sorry, try again.
[[/etc/NetworkManager/system-connections/TALKTALK-40B874]] (600 root)
[connection] id=TALKTALK-40B874 | type=wifi
[wifi] ssid=TALKTALK-40B874 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country US: DFS-FCC
    (2402 - 2472 @ 40), (3, 27), (N/A)
    (5170 - 5250 @ 40), (3, 17), (N/A)
    (5250 - 5330 @ 40), (3, 20), (0 ms), DFS
    (5490 - 5600 @ 40), (3, 20), (0 ms), DFS
    (5650 - 5710 @ 40), (3, 20), (0 ms), DFS
    (5735 - 5835 @ 40), (3, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     11 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'BTHub5-3Q86' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-3Q86"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000df9296107
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'BTWifi-with-FON' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000df92a9abb
                    Extra: Last beacon: 36ms ago
          Cell 03 - Address: <MAC 'BTWifi-X' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000df92a3f4d
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC 'VM910497-2G' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"VM910497-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000312ee08591
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'SKY5CF4D' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"SKY5CF4D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003cc5de9786
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'SKY6EEE7' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"SKY6EEE7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000027e88844e9
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'HP-Print-B3-Deskjet 2540 series' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-B3-Deskjet 2540 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000129409b9a4d
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'BTWifi-X' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c0e847180
                    Extra: Last beacon: 364ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 09 - Address: <MAC 'SKY73B2C' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"SKY73B2C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000255bff1538
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'TALKTALK-40B874' [AC10]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-40B874"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ad6d4a028
                    Extra: Last beacon: 36ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'SKY97DE1' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"SKY97DE1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001dcdece8adc
                    Extra: Last beacon: 8688ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[brcmsmac]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     5F866C1008CB05E51B96C2E
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512

[brcmutil]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     A2434DDD5B2051715F2E908
depends:        
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512

[b43]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     25A88E97301A6821E663814
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[mac80211]
filename:       /lib/modules/3.19.0-15-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F518BE1BD732F328C9E430B
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-15-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     268045EBCFAFDADD136DCF6
depends:        
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     551AE4C23939F7FBED9DA61
depends:        
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512

[bcma]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F17244FFF75F9BDF92327ED
depends:        
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

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
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   11.048509] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   11.048529] b43: probe of bcma0:1 failed with error -524
[   11.665367] brcmsmac bcma0:1: mfg 4bf core 812 rev 24 class 0 irq 17
[   11.868081] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 499
[   23.342795] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   23.342819] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
[   57.518973] wlan0: authenticate with <MAC 'TALKTALK-40B874' [AC10]>
[   57.521050] wlan0: send auth to <MAC 'TALKTALK-40B874' [AC10]> (try 1/3)
[   57.628056] wlan0: send auth to <MAC 'TALKTALK-40B874' [AC10]> (try 2/3)
[   57.732057] wlan0: send auth to <MAC 'TALKTALK-40B874' [AC10]> (try 3/3)
[   57.836061] wlan0: authentication with <MAC 'TALKTALK-40B874' [AC10]> timed out
[   58.570421] wlan0: authenticate with <MAC 'TALKTALK-40B874' [AC10]>
[   58.570665] wlan0: send auth to <MAC 'TALKTALK-40B874' [AC10]> (try 1/3)
[   58.672058] wlan0: send auth to <MAC 'TALKTALK-40B874' [AC10]> (try 2/3)
[   58.776056] wlan0: send auth to <MAC 'TALKTALK-40B874' [AC10]> (try 3/3)
[   58.880058] wlan0: authentication with <MAC 'TALKTALK-40B874' [AC10]> timed out
[   60.010675] wlan0: authenticate with <MAC 'TALKTALK-40B874' [AC10]>
[   60.010923] wlan0: send auth to <MAC 'TALKTALK-40B874' [AC10]> (try 1/3)
[   60.116055] wlan0: send auth to <MAC 'TALKTALK-40B874' [AC10]> (try 2/3)
[   60.220048] wlan0: send auth to <MAC 'TALKTALK-40B874' [AC10]> (try 3/3)
[   60.324107] wlan0: authentication with <MAC 'TALKTALK-40B874' [AC10]> timed out
[   61.958367] wlan0: authenticate with <MAC 'TALKTALK-40B874' [AC10]>
[   61.958617] wlan0: send auth to <MAC 'TALKTALK-40B874' [AC10]> (try 1/3)
[   62.060053] wlan0: send auth to <MAC 'TALKTALK-40B874' [AC10]> (try 2/3)
[   62.164073] wlan0: send auth to <MAC 'TALKTALK-40B874' [AC10]> (try 3/3)
[   62.268055] wlan0: authentication with <MAC 'TALKTALK-40B874' [AC10]> timed out
[   73.537566] wlan0: authenticate with <MAC 'TALKTALK-40B874' [AC10]>
[   73.537987] wlan0: send auth to <MAC 'TALKTALK-40B874' [AC10]> (try 1/3)
[   73.640058] wlan0: send auth to <MAC 'TALKTALK-40B874' [AC10]> (try 2/3)
[   73.744050] wlan0: send auth to <MAC 'TALKTALK-40B874' [AC10]> (try 3/3)
[   73.848061] wlan0: authentication with <MAC 'TALKTALK-40B874' [AC10]> timed out

########## wireless info END ############



```

---

### Post by jeremy31 on 2015-08-05
I would change the wifi router encryption setting to WPA2 only, WPA2-AES, or WPA2-PSK with no mixed mode, WEP or TKIP

And with both computers do
```
sudo iw reg set GB
```

Then edit another file ```
gksudo gedit /etc/default/crda
```
Find the line that is normally REGDOMAIN=00 and make it ```
REGDOMAIN=GB
``` Save, exit program, and reboot

---

### Post by pavelexpertov on 2015-08-06
Hello, unfortunately I can't get access to the router, so I am thinking to make my main laptop as a wifi hotspot. HOWEVER, it backfired because i realised the laptop is not connected to my router after hotspot is set up. Is there any other way to make the laptop as a wifi hotspot without disconnecting to the router?

---

### Post by jeremy31 on 2015-08-06
You could use 2 wifi cards to do this as Ubuntu doesn't have the capability of using just one.  Or if your main laptop isn't moved you could use something like [http://www.linksys.com/us/support-product?pid=01t80000003KXWAAA4](http://www.linksys.com/us/support-product?pid=01t80000003KXWAAA4) to get internet access from and then use the internal wifi card to use as a hotspot

---

### Post by him610 on 2015-08-06
Hello,

> **pavelexpertov said:**
> Hello, unfortunately I can't get access to the router, ...

It is possible the individual controlling the router has set the MAC filter.

---

### Post by pavelexpertov on 2015-08-07
Well, for the router, I forgot to mention I haven't got details for user account and password (already tried admin with no password, doesn't work). 
However, an irony has happened. I happen to have a belkin usb adapter and hp notebook managed to connect to my wifi. XD
I am updating it now, but I will post results later.

---

### Post by pavelexpertov on 2015-08-07
Hooray, belkin saved my day. After installing tonnes of updates, my two notebooks finally work with the wifi. This thread is done.

---

