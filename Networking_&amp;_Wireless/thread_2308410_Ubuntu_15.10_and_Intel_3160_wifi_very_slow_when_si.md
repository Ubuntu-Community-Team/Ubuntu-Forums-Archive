---
title: "Ubuntu 15.10 and Intel 3160: wifi very slow when signal below 45%"
date: 2016-01-02
forum: Networking &amp; Wireless
---

### Post by TuxManRemove on 2016-01-02
Hello,
Several people who have installed Ubuntu 2 or 3 weeks ago, and have told me that when they connect to wireless networks and extent of this is shown below 45%, the connection is very slow.
They are all the same notebook model with the same hardware, and they have put Ubuntu 15.10, and have also updated after install. They are laptops with Intel 3160 cards.
I also updated the driver to the latest version (the December 23, 2015)
[https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi)

The iwconfig command displays a bitrate of 1Mbs when wifi is less than 40% and therefore it is impossible to navigate the Internet well.
I tried to install Windows and navigation is possible, is not so slow.

Now I'm home and I've noticed the same thing happens to me, I had not realized that I have the computer in the same room as the router. But I went to another room and the same thing happens.
Though I'm with Linux Mint and wifi not is Intel, WiFi is Atheros.
Is it normal when the WiFi signal 40% signal can not surf the Internet? the bitrate is too low?

Get  information from my laptop now, tomorrow will put the customer laptops  with Ubuntu 15.10 and Intel 3160, because I not have now one of those  laptops.

**Latptop 1:**
```

########## wireless info START ##########
##### kernel ############################

Linux 3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### lspci #############################

01:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7167]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 002 Device 003: ID 090c:037c Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                 137283  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              652777  1 ath9k
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18479 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14276991 (14.2 MB)  TX bytes:2746787 (2.7 MB)

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ONO9EA1Pat"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'ONO9EA1Pat' [AC8]>   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=25/70  Signal level=-85 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:46  Invalid misc:33   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root      1035     1  0 23:32 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [ONO9EA1Pat automática] --------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    ONOD432:         Infra, <MAC 'ONOD432' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    _AUTO_ONOWiFi:   Infra, <MAC '_AUTO_ONOWiFi' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2 Enterprise
    _AUTO_ONOWiFi:   Infra, <MAC '_AUTO_ONOWiFi' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    vodafone98DD:    Infra, <MAC 'vodafone98DD' [AC5]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 45 WPA2
    _ONOWiFi:        Infra, <MAC '_ONOWiFi' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47
    _ONOWiFi:        Infra, <MAC '_ONOWiFi' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32
    _AUTO_ONOWiFi:   Infra, <MAC '_AUTO_ONOWiFi' [AN7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    ONO8AE0:         Infra, <MAC 'ONO8AE0' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Orange-b610:     Infra, <MAC 'Orange-b610' [AN9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    F60_1594:        Infra, <MAC 'F60_1594' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 61 WPA2
    *ONO9EA1Pat:     Infra, <MAC 'ONO9EA1Pat' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 36 WPA2
    _AUTO_ONOWiFi:   Infra, <MAC '_AUTO_ONOWiFi' [AN7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2 Enterprise
    Orange-0179:     Infra, <MAC 'Orange-0179' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             62.81.16.164
    DNS:             62.81.16.213

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=<MAC address>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

............cut for privacity..................

[[/etc/NetworkManager/system-connections/ONO9EA1Pat automática]] (600 root)
[connection] id=ONO9EA1Pat automática | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=ONO9EA1Pat | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

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

lo        Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      5   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'F60_1594' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"F60_1594"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000012136e301
                    Extra: Last beacon: 2100ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ONOD432' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"ONOD432"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e248354d8
                    Extra: Last beacon: 3036ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '_AUTO_ONOWiFi' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"_AUTO_ONOWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e24835e35
                    Extra: Last beacon: 3032ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC '_ONOWiFi' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:off
                    ESSID:"_ONOWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e24836fd3
                    Extra: Last beacon: 3032ms ago
          Cell 05 - Address: <MAC 'vodafone98DD' [AC5]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"vodafone98DD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000053b00ad9f8
                    Extra: Last beacon: 11764ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '_ONOWiFi' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"_ONOWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b2e1652c83
                    Extra: Last beacon: 764ms ago
          Cell 07 - Address: <MAC '_AUTO_ONOWiFi' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"_AUTO_ONOWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b2e164ec78
                    Extra: Last beacon: 1268ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 08 - Address: <MAC 'ONO9EA1Pat' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"ONO9EA1Pat"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b2e1649dd4
                    Extra: Last beacon: 1068ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Orange-0179' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Orange-0179"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ba90ff4c42
                    Extra: Last beacon: 13208ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'ONOA163' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"ONOA163"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000925266565
                    Extra: Last beacon: 3280ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.16.0-38-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5C1878F185424DB0329389D
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:84:ED:AC:CF:0B:47:36:52:C3:4D:23:BE:C3:56:94:42:36:E6:3B
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/3.16.0-38-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     265A5990B1258ECC29235FC
depends:        cfg80211,ath9k_hw,ath
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:84:ED:AC:CF:0B:47:36:52:C3:4D:23:BE:C3:56:94:42:36:E6:3B
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.16.0-38-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     0D1161FC3B202FBE214F25D
depends:        ath
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:84:ED:AC:CF:0B:47:36:52:C3:4D:23:BE:C3:56:94:42:36:E6:3B
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.16.0-38-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     165C1DF76AF8C8B6A45DA4F
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:84:ED:AC:CF:0B:47:36:52:C3:4D:23:BE:C3:56:94:42:36:E6:3B
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-38-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     376BFDE8E6207B0AAA6339B
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:84:ED:AC:CF:0B:47:36:52:C3:4D:23:BE:C3:56:94:42:36:E6:3B
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-38-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:84:ED:AC:CF:0B:47:36:52:C3:4D:23:BE:C3:56:94:42:36:E6:3B
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
options iwlwifi 11n_disable=1 power_save=0 power_level=5 bt_coex_active=0

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

##### rc.local ##########################

mount -a

exit 0

##### pm-utils ##########################

[/etc/pm/sleep.d/00_check_touchpad_status] (644 root)
LOGFILE="/var/log/sleep.log"
case "$1" in
        resume|thaw)
                echo "Resumed from suspend at `date`" >> "$LOGFILE"
                /usr/bin/python3 /opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/check_touchpad_status.py
                echo "Touchpad enabled"
                ;;
esac

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# USB device 0x:0x (dm9601)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #############################

[ 1145.850096] wlan0: deauthenticating from <MAC 'F60_1594' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1146.728756] wlan0: authenticate with <MAC 'ONO9EA1Pat' [AC8]>
[ 1146.741449] wlan0: send auth to <MAC 'ONO9EA1Pat' [AC8]> (try 1/3)
[ 1146.759035] wlan0: authenticated
[ 1146.759798] wlan0: associate with <MAC 'ONO9EA1Pat' [AC8]> (try 1/3)
[ 1146.771985] wlan0: RX AssocResp from <MAC 'ONO9EA1Pat' [AC8]> (capab=0x411 status=0 aid=10)
[ 1146.772047] wlan0: associated
[ 1146.772064] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1186.909156] wlan0: deauthenticating from <MAC 'ONO9EA1Pat' [AC8]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1188.318541] wlan0: authenticate with <MAC 'F60_1594' [AC1]>
[ 1188.331842] wlan0: send auth to <MAC 'F60_1594' [AC1]> (try 1/3)
[ 1188.337345] wlan0: authenticated
[ 1188.337989] wlan0: associate with <MAC 'F60_1594' [AC1]> (try 1/3)
[ 1188.362066] wlan0: RX AssocResp from <MAC 'F60_1594' [AC1]> (capab=0x8431 status=0 aid=2)
[ 1188.362125] wlan0: associated
[ 1188.362135] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1484.304920] wlan0: deauthenticating from <MAC 'F60_1594' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1512.572379] wlan0: authenticate with <MAC 'F60_1594' [AC1]>
[ 1512.589823] wlan0: send auth to <MAC 'F60_1594' [AC1]> (try 1/3)
[ 1512.601829] wlan0: authenticated
[ 1512.603471] wlan0: associate with <MAC 'F60_1594' [AC1]> (try 1/3)
[ 1512.622958] wlan0: RX AssocResp from <MAC 'F60_1594' [AC1]> (capab=0x8431 status=0 aid=3)
[ 1512.623017] wlan0: associated
[ 1512.623044] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1556.889541] wlan0: deauthenticating from <MAC 'F60_1594' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1585.609595] wlan0: authenticate with <MAC 'F60_1594' [AC1]>
[ 1585.627120] wlan0: send auth to <MAC 'F60_1594' [AC1]> (try 1/3)
[ 1585.634343] wlan0: authenticated
[ 1585.635448] wlan0: associate with <MAC 'F60_1594' [AC1]> (try 1/3)
[ 1585.654703] wlan0: RX AssocResp from <MAC 'F60_1594' [AC1]> (capab=0x8431 status=0 aid=4)
[ 1585.654761] wlan0: associated
[ 1585.654789] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1591.386106] wlan0: deauthenticating from <MAC 'F60_1594' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1591.394405] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1596.807310] wlan0: authenticate with <MAC 'ONO9EA1Pat' [AC8]>
[ 1596.820202] wlan0: send auth to <MAC 'ONO9EA1Pat' [AC8]> (try 1/3)
[ 1596.974324] wlan0: authenticated
[ 1596.974847] wlan0: associate with <MAC 'ONO9EA1Pat' [AC8]> (try 1/3)
[ 1597.059336] wlan0: RX AssocResp from <MAC 'ONO9EA1Pat' [AC8]> (capab=0x411 status=0 aid=10)
[ 1597.059386] wlan0: associated
[ 1599.346804] wlan0: authenticate with <MAC 'ONO9EA1Pat' [AC8]>
[ 1599.359788] wlan0: send auth to <MAC 'ONO9EA1Pat' [AC8]> (try 1/3)
[ 1599.603937] wlan0: authenticated
[ 1599.606405] wlan0: associate with <MAC 'ONO9EA1Pat' [AC8]> (try 1/3)
[ 1599.613999] wlan0: RX AssocResp from <MAC 'ONO9EA1Pat' [AC8]> (capab=0x411 status=0 aid=10)
[ 1599.614056] wlan0: associated

########## wireless info END ############


```

Thank you
Best regards

---

### Post by Hadaka on 2016-01-03
Hi,you have a few items in your wireless report that are likely
responsible for your slow internet.
First is this..
```
##### network managers ##################
Installed:
    NetworkManager
    Wicd
```

You can only have one network manager.Remove one.

Please open a terminal then with a working wired connection 
copy and paste one line at a time,
```
sudo apt-get update
sudo modprobe -rf ath9k
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -v ath9k
```
then do..
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
sudo iw reg set ES
sudo sed -i 's/^REG.*=$/&ES/' /etc/default/crda
```
remove the wired connection,boot and test wireless
thanks.

---

### Post by TuxManRemove on 2016-01-03
Hello Hadaka!
I test it now, when laptop restart.
(i install wicd testing slow, but i remove it now)

I put here code of other laptop, with intel 3160.[B]

LAPTOP 2:[/B]
```


########## wireless info START ##########

Report from: 03 Jan 2016 17:35 CET +0100

Booted last: 03 Jan 2016 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-22-generic #27-Ubuntu SMP Thu Dec 17 22:57:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8070]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1e4e:0110 Cubeternet 
Bus 001 Device 002: ID 8087:07dc Intel Corp. 
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

iwlmvm                294912  0
mac80211              733184  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          200704  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          inet addr:192.168.0.233  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp2s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47643 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18487 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68084755 (68.0 MB)  TX bytes:2375209 (2.3 MB)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:"WLAN_8287"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'WLAN_8287' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       632     1  0 17:10 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 3160 (Dual Band Wireless AC 3160)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.2.0-22-generic
GENERAL.FIRMWARE-VERSION:               25.30.13.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     WLAN_8287
GENERAL.CON-UUID:                       1530d27c-aef1-4ba9-a891-9be6aad71ec8
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1530d27c-aef1-4ba9-a891-9be6aad71ec8 | WLAN_8287
IP4.ADDRESS[1]:                         192.168.0.233/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1451838217
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.0.1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 4294967295
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       ip_address = 192.168.0.233
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_netbios_scope = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp2s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
JRC              <MAC 'JRC' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2         no        
_AUTO_ONOWiFi    <MAC '_AUTO_ONOWiFi' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2 802.1X  no        
NETGEAR_GUEST_2  <MAC 'NETGEAR_GUEST_2' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2         no        
Orange-89C0      <MAC 'Orange-89C0' [AC7]>  Infra  11    2462 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
Nodo3            <MAC 'Nodo3' [AN5]>  Infra  6     2437 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2         no        
ONO 45           <MAC 'ONO 45' [AN6]>  Infra  11    2462 MHz  54 Mbit/s  30      &#9602;___  WPA1 WPA2    no        
_ONOWiFi         <MAC '_ONOWiFi' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  --           no        
WLAN_8287        <MAC 'WLAN_8287' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA1 WPA2    yes     * 

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

[[/etc/NetworkManager/system-connections/WLAN_8287]] (600 root)
[connection] id=WLAN_8287 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=WLAN_8287
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

country DE: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
    (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp1s0    no frequency information.

wlp2s0    32 channels in total; available frequencies :
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
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.462 GHz (Channel 11)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'WLAN_8287' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"WLAN_8287"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000004e81d1b9
                    Extra: Last beacon: 80ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'JRC' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"JRC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b53331f825
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '_AUTO_ONOWiFi' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"_AUTO_ONOWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b5332f9654
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC '_ONOWiFi' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"_ONOWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b5332f9efb
                    Extra: Last beacon: 80ms ago
          Cell 05 - Address: <MAC 'NETGEAR_GUEST_2' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR_GUEST_2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b5332fa6a1
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '_AUTO_ONOWiFi' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"_AUTO_ONOWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006afb9457d3
                    Extra: Last beacon: 3308ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC 'Orange-89C0' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Orange-89C0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000168d48280e1
                    Extra: Last beacon: 3172ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.2.0-22-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     3BBD88D7E8252B90136F463
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.2.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     065F4A11FE84275F51A59F2
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.2.0-22-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-12.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     A1A0F5F0F10EE9DA45CFC38
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.2.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    4.940517] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    4.942090] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    4.942284] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[    5.060266] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[  183.191241] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.
[  185.796015] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
[  185.800333] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  185.929094] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[  189.375183] wlp2s0: authenticate with <MAC 'WLAN_8287' [AC1]>
[  189.379971] wlp2s0: send auth to <MAC 'WLAN_8287' [AC1]> (try 1/3)
[  189.457302] wlp2s0: authenticated
[  189.460896] wlp2s0: associate with <MAC 'WLAN_8287' [AC1]> (try 1/3)
[  189.464776] wlp2s0: RX AssocResp from <MAC 'WLAN_8287' [AC1]> (capab=0x431 status=0 aid=1)
[  189.465920] wlp2s0: associated
[  189.465947] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[  770.914967] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.
[  770.915507] wlp2s0: deauthenticating from <MAC 'WLAN_8287' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  773.418620] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
[  773.420178] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  773.555346] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[  776.986815] wlp2s0: authenticate with <MAC 'WLAN_8287' [AC1]>
[  776.990386] wlp2s0: send auth to <MAC 'WLAN_8287' [AC1]> (try 1/3)
[  777.074772] wlp2s0: authenticated
[  777.077978] wlp2s0: associate with <MAC 'WLAN_8287' [AC1]> (try 1/3)
[  777.083383] wlp2s0: RX AssocResp from <MAC 'WLAN_8287' [AC1]> (capab=0x431 status=0 aid=1)
[  777.086878] wlp2s0: associated
[  777.086905] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready

########## wireless info END ############


```

Thank you very much!

---

### Post by TuxManRemove on 2016-01-03
Hello, 
Hello I reboot the laptop 1 and connexion is well, but i test it better.

About laptop 2, I just realized that the wired network does not, not connect, and Network Manager show: "disconected". But this computer does not have done anything, I format and install Ubuntu two days ago. I not install any software.

I do the test with the laptop number 3, which is the same as the computer 2, Intel 3160 .
The computer 3 that operates the cable network and WiFi, but it's the same,  next the router never is 100% connection, and when I go to another room, and the signal is less than 50 or 45 % , the connection is very slow !
Are laptops with SSD, intel i5 5th generation.

Thanks!

**LAPTOP 3:**
```

########## wireless info START ##########

Report from: 03 Jan 2016 18:01 CET +0100

Booted last: 03 Jan 2016 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-22-generic #27-Ubuntu SMP Thu Dec 17 22:57:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, i8042.nomux=1, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8070]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1e4e:0110 Cubeternet 
Bus 001 Device 002: ID 8087:07dc Intel Corp. 
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

iwlmvm                294912  0
mac80211              733184  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          200704  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4407 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5089017 (5.0 MB)  TX bytes:545781 (545.7 KB)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          inet addr:192.168.0.228  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp2s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:644 errors:0 dropped:0 overruns:0 frame:0
          TX packets:555 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:171508 (171.5 KB)  TX bytes:68534 (68.5 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:"WLAN_8287"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'WLAN_8287' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:42   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       664     1  0 17:50 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 3160 (Dual Band Wireless AC 3160)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.2.0-22-generic
GENERAL.FIRMWARE-VERSION:               25.30.13.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     WLAN_8287
GENERAL.CON-UUID:                       69eafab0-a058-4246-ac23-5525a71c7df0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     5 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   69eafab0-a058-4246-ac23-5525a71c7df0 | WLAN_8287
IP4.ADDRESS[1]:                         192.168.0.228/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1451839864
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.0.1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 4294967295
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       ip_address = 192.168.0.228
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_netbios_scope = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp2s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
WLAN_8287        <MAC 'WLAN_8287' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA1 WPA2    yes     * 
JRC              <MAC 'JRC' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2         no        
_AUTO_ONOWiFi    <MAC '_AUTO_ONOWiFi' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
NETGEAR_GUEST_2  <MAC 'NETGEAR_GUEST_2' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2         no        
Orange-89C0      <MAC 'Orange-89C0' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA1 WPA2    no        
ONO990494        <MAC 'ONO990494' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2    no        
Nodo3            <MAC 'Nodo3' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2         no        
_ONOWiFi         <MAC '_ONOWiFi' [AN8]>  Infra  1     2412 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  --           no        

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

[[/etc/NetworkManager/system-connections/Mi Phone]] (600 root)
[connection] id=Mi Phone | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Mi Phone
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WLAN_8287]] (600 root)
[connection] id=WLAN_8287 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=WLAN_8287
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

country DE: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
    (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp1s0    no frequency information.

wlp2s0    32 channels in total; available frequencies :
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
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.462 GHz (Channel 11)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'WLAN_8287' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"WLAN_8287"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000aae803ff
                    Extra: Last beacon: 96ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'JRC' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"JRC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b58f96416d
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Nodo3' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Nodo3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003a1f23dc57
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'ONO990494' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"ONO990494"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002b63977bde
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Orange-89C0' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Orange-89C0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000016930e681dc
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'ONOD7E0' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"ONOD7E0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c8d4bb6160
                    Extra: Last beacon: 3264ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.2.0-22-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     3BBD88D7E8252B90136F463
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.2.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     065F4A11FE84275F51A59F2
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.2.0-22-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-12.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     A1A0F5F0F10EE9DA45CFC38
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.2.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    3.683970] iwlwifi 0000:02:00.0: Unsupported splx structure
[    3.686550] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-3160-15.ucode failed with error -2
[    3.686570] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-3160-14.ucode failed with error -2
[    3.688474] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.0.1.2d.d.bseq
[    3.695854] iwlwifi 0000:02:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
[    3.732155] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[    3.733607] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[    3.808593] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    3.872095] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.874125] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[    5.078484] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    5.078684] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[    5.212488] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    5.214105] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    5.399147] r8169 0000:01:00.0 enp1s0: link down (repeated 2 times)
[    5.399190] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    5.465389] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    6.978940] r8169 0000:01:00.0 enp1s0: link up
[    6.978978] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready
[    8.852673] wlp2s0: authenticate with <MAC 'WLAN_8287' [AC1]>
[    8.857597] wlp2s0: send auth to <MAC 'WLAN_8287' [AC1]> (try 1/3)
[    9.053477] wlp2s0: authenticated
[    9.055939] wlp2s0: associate with <MAC 'WLAN_8287' [AC1]> (try 1/3)
[    9.069425] wlp2s0: RX AssocResp from <MAC 'WLAN_8287' [AC1]> (capab=0x431 status=0 aid=2)
[    9.070596] wlp2s0: associated
[    9.070619] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[  518.982235] r8169 0000:01:00.0 enp1s0: link down

########## wireless info END ############

```

---

### Post by TuxManRemove on 2016-01-03
**LAPTOP 3, router in the next room:**
```

########## wireless info START ##########

Report from: 03 Jan 2016 18:50 CET +0100

Booted last: 03 Jan 2016 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-22-generic #27-Ubuntu SMP Thu Dec 17 22:57:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, i8042.nomux=1, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8070]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1e4e:0110 Cubeternet 
Bus 001 Device 002: ID 8087:07dc Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                294912  0
mac80211              733184  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          200704  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4407 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5089017 (5.0 MB)  TX bytes:545781 (545.7 KB)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          inet addr:192.168.0.228  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp2s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33724946 (33.7 MB)  TX bytes:4086660 (4.0 MB)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:"WLAN_8287"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'WLAN_8287' [AN5]>   
          Bit Rate=1 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       664     1  0 17:50 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 3160 (Dual Band Wireless AC 3160)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.2.0-22-generic
GENERAL.FIRMWARE-VERSION:               25.30.13.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     WLAN_8287
GENERAL.CON-UUID:                       69eafab0-a058-4246-ac23-5525a71c7df0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     58 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   69eafab0-a058-4246-ac23-5525a71c7df0 | WLAN_8287
IP4.ADDRESS[1]:                         192.168.0.228/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1451843255
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.0.1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 4294967295
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       ip_address = 192.168.0.228
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_netbios_scope = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp2s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
NETGEAR_GUEST_2  <MAC 'NETGEAR_GUEST_2' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2         no        
_AUTO_ONOWiFi    <MAC '_AUTO_ONOWiFi' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2 802.1X  no        
JRC              <MAC 'JRC' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2         no        
_ONOWiFi         <MAC '_ONOWiFi' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  --           no        
WLAN_8287        <MAC 'WLAN_8287' [AN5]>  Infra  11    2462 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2    yes     * 
Orange-89C0      <MAC 'Orange-89C0' [AN6]>  Infra  11    2462 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2    no        
WLAN_BBA4        <MAC 'WLAN_BBA4' [AN7]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA1         no        
vodafone9AB2     <MAC 'vodafone9AB2' [AN8]>  Infra  4     2427 MHz  54 Mbit/s  24      &#9602;___  WPA2         no        
Orange-749D      <MAC 'Orange-749D' [AN9]>  Infra  1     2412 MHz  54 Mbit/s  25      &#9602;___  WPA2         no        
ONOD7E0          <MAC 'ONOD7E0' [AN10]>  Infra  11    2462 MHz  54 Mbit/s  30      &#9602;___  WPA1 WPA2    no        
ONO990494        <MAC 'ONO990494' [AN11]>  Infra  6     2437 MHz  54 Mbit/s  24      &#9602;___  WPA1 WPA2    no        

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

[[/etc/NetworkManager/system-connections/Mi Phone]] (600 root)
[connection] id=Mi Phone | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Mi Phone
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WLAN_8287]] (600 root)
[connection] id=WLAN_8287 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=WLAN_8287
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

country DE: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
    (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp1s0    no frequency information.

wlp2s0    32 channels in total; available frequencies :
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
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

wlp2s0    Interface doesn't support scanning : Device or resource busy

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.2.0-22-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     3BBD88D7E8252B90136F463
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.2.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     065F4A11FE84275F51A59F2
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.2.0-22-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-12.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     A1A0F5F0F10EE9DA45CFC38
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.2.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[ 2422.635214] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
[ 2422.820084] r8169 0000:01:00.0 enp1s0: link down
[ 2423.999868] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.0.1.2d.d.bseq
[ 2424.133000] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[ 2424.149443] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 2424.149709] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[ 2424.281103] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 2424.281938] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[ 2424.473562] r8169 0000:01:00.0 enp1s0: link down
[ 2424.473602] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[ 2424.523834] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 2427.920670] wlp2s0: authenticate with <MAC 'WLAN_8287' [AN5]>
[ 2427.924414] wlp2s0: send auth to <MAC 'WLAN_8287' [AN5]> (try 1/3)
[ 2427.964392] wlp2s0: authenticated
[ 2427.966283] wlp2s0: associate with <MAC 'WLAN_8287' [AN5]> (try 1/3)
[ 2427.970193] wlp2s0: RX AssocResp from <MAC 'WLAN_8287' [AN5]> (capab=0x431 status=0 aid=1)
[ 2427.972164] wlp2s0: associated
[ 2427.972200] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready

########## wireless info END ############


```

---

### Post by Hadaka on 2016-01-03
Hi,for laptop 2 , please do..
```
sudo iw reg set ES 
sudo sed -i 's/^REG.*=$/&ES/' /etc/default/crda
``` 
```
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
echo "options mac80211 probe_wait_ms=1000" | sudo tee -a /etc/modprobe.d/mac80211.conf
sudo modprobe -v iwlwifi
```

---

### Post by TuxManRemove on 2016-01-03
> **Hadaka said:**
> Hi,for laptop 2 , please do..
```
sudo iw reg set ES 
sudo sed -i 's/^REG.*=$/&ES/' /etc/default/crda
``` 
```
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
echo "options mac80211 probe_wait_ms=1000" | sudo tee -a /etc/modprobe.d/mac80211.conf
sudo modprobe -v iwlwifi
```

Hello Hadaka!
I had tried two hours ago and I put this in iwlwifi.conf:

options iwlwifi 11n_disable=1 power_save=0 power_level=5 bt_coex_active=0 wd_disable=1
 
 Should I remove these options?
PS: I edited my previous posts stating in bold, that laptops is each test result

---

### Post by Hadaka on 2016-01-03
hi just edit the file and change the one line, please do..
```
gksudo gedit  /etc/modprobe.d/iwlwifi.conf
```

replace```
 options iwlwifi 11n_disable=1
#with
options iwlwifi 11n_disable=8
```

---

### Post by TuxManRemove on 2016-01-04
Thank you,
 I have not noticed improvement when the signal is 40 cloves or 45% Internet browsing is very slow, impossible ...

Thanks

```

########## wireless info START ##########

Report from: 04 Jan 2016 14:51 CET +0100

Booted last: 04 Jan 2016 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-22-generic #27-Ubuntu SMP Thu Dec 17 22:57:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, i8042.nomux=1, vt.handoff=7

##### desktop ###########################

Ubuntu (from ~/.dmrc)

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8070]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1e4e:0110 Cubeternet 
Bus 001 Device 002: ID 8087:07dc Intel Corp. 
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

iwlmvm                294912  0
mac80211              733184  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          200704  1 snd_soc_rt5640
snd_pcm               106496  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          inet addr:192.168.0.228  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp2s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22424535 (22.4 MB)  TX bytes:2138990 (2.1 MB)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:"WLAN_8287"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'WLAN_8287' [AN10]>   
          Bit Rate=14.4 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=34/70  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:343   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       558     1  0 14:28 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 3160 (Dual Band Wireless AC 3160)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.2.0-22-generic
GENERAL.FIRMWARE-VERSION:               25.30.13.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     WLAN_8287
GENERAL.CON-UUID:                       69eafab0-a058-4246-ac23-5525a71c7df0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     14 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   795b4714-8f95-4f34-87db-a1150635563d | HP-Print-58-Deskjet 2540 series
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   69eafab0-a058-4246-ac23-5525a71c7df0 | WLAN_8287
IP4.ADDRESS[1]:                         192.168.0.228/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1451915231
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.0.1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 4294967295
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       ip_address = 192.168.0.228
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_netbios_scope = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp2s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Orange-89C0                      <MAC 'Orange-89C0' [AN1]>  Infra  11    2462 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no        
PELUQUERIA MARIA                 <MAC 'PELUQUERIA MARIA' [AN2]>  Infra  6     2437 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2  no        
ONO7693                          <MAC 'ONO7693' [AN3]>  Infra  3     2422 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA1 WPA2  no        
JRC                              <MAC 'JRC' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2       no        
ONODE52                          <MAC 'ONODE52' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
HP-Print-58-Deskjet 2540 series  <MAC 'HP-Print-58-Deskjet 2540 series' [AN6]>  Infra  1     2412 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2       no        
Orange-A4DC                      <MAC 'Orange-A4DC' [AN7]>  Infra  3     2422 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2  no        
VodafoneC92F                     <MAC 'VodafoneC92F' [AN8]>  Infra  11    2462 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1       no        
_ONO_WiFiGRATIS                  <MAC '_ONO_WiFiGRATIS' [AN9]>  Infra  1     2412 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  --         no        
WLAN_8287                        <MAC 'WLAN_8287' [AN10]>  Infra  11    2462 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  yes     * 
TP-LINK_A48C54                   <MAC 'TP-LINK_A48C54' [AN11]>  Infra  3     2422 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        

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

[[/etc/NetworkManager/system-connections/Mi Phone]] (600 root)
[connection] id=Mi Phone | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Mi Phone
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HP-Print-58-Deskjet 2540 series]] (600 root)
[connection] id=HP-Print-58-Deskjet 2540 series | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=HP-Print-58-Deskjet 2540 series
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WLAN_8287]] (600 root)
[connection] id=WLAN_8287 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=WLAN_8287
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

country DE: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
    (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp1s0    no frequency information.

wlp2s0    32 channels in total; available frequencies :
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
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

wlp2s0    Interface doesn't support scanning : Device or resource busy

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.2.0-22-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     3BBD88D7E8252B90136F463
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.2.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     065F4A11FE84275F51A59F2
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.2.0-22-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-12.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     A1A0F5F0F10EE9DA45CFC38
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.2.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 1000

[iwlwifi]
11n_disable: 8
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: N
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 5
power_save: N
swcrypto: 0
uapsd_disable: Y

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=8 power_save=0 power_level=5 bt_coex_active=0 wd_disable=1

[/etc/modprobe.d/mac80211.conf]
options mac80211 probe_wait_ms=1000

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[  527.161242] wlp2s0: deauthenticating from <MAC 'WLAN_8287' [AN10]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  531.116131] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  534.356794] wlp2s0: authenticate with <MAC 'WLAN_8287' [AN10]>
[  534.359920] wlp2s0: send auth to <MAC 'WLAN_8287' [AN10]> (try 1/3)
[  534.383581] wlp2s0: authenticated
[  534.384570] wlp2s0: associate with <MAC 'WLAN_8287' [AN10]> (try 1/3)
[  534.391413] wlp2s0: RX AssocResp from <MAC 'WLAN_8287' [AN10]> (capab=0x431 status=0 aid=3)
[  534.396497] wlp2s0: associated
[  534.396528] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[  535.398265] wlp2s0: deauthenticating from <MAC 'WLAN_8287' [AN10]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  538.074120] wlp2s0: authenticate with <MAC 'WLAN_8287' [AN10]>
[  538.077191] wlp2s0: send auth to <MAC 'WLAN_8287' [AN10]> (try 1/3)
[  538.102057] wlp2s0: authenticated
[  538.105482] wlp2s0: associate with <MAC 'WLAN_8287' [AN10]> (try 1/3)
[  538.109359] wlp2s0: RX AssocResp from <MAC 'WLAN_8287' [AN10]> (capab=0x431 status=0 aid=3)
[  538.110892] wlp2s0: associated
[ 1133.985022] wlp2s0: deauthenticating from <MAC 'WLAN_8287' [AN10]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1135.879290] wlp2s0: authenticate with <MAC 'WLAN_8287' [AN10]>
[ 1135.882737] wlp2s0: send auth to <MAC 'WLAN_8287' [AN10]> (try 1/3)
[ 1135.906432] wlp2s0: authenticated
[ 1135.907495] wlp2s0: associate with <MAC 'WLAN_8287' [AN10]> (try 1/3)
[ 1135.911423] wlp2s0: RX AssocResp from <MAC 'WLAN_8287' [AN10]> (capab=0x431 status=0 aid=3)
[ 1135.912486] wlp2s0: associated

########## wireless info END ############


```

---

### Post by TuxManRemove on 2016-01-04
I saw that although I move from room when I throw the iwconfig command, the bitrate unchanged, remains 14.4
 If I restart the computer, it does change, but then not changing but stay away from the router.

 While this is not important, the important thing is that I can not surf the Internet, when the wireless signal is less than 45%. And that greatly reduces the coverage, only the room where the router  ...
:(

---

### Post by Hadaka on 2016-01-04
Hi try this..
```
sudo modprobe -r iwldvm
sudo modprobe -r iwlwif
echo "options iwlwifi btcoex_enable=1 | sudo tee -a /etc/modprobe.d/iwlwifi.conf
sudo modprobe -v iwlwifi
```
thanks.

---

### Post by TuxManRemove on 2016-01-05
Sorry Hadaka, the second command is missing a letter i 
(iwlwifi)

 But still the problem persists.

 What is the difference between "bt_coex_active" and "btcoex_enable"?
because I have 2
but with or without, the problem continues...

:cry:

---

### Post by TuxManRemove on 2016-01-06
You think that should change the cables? You know from laptop internal cables or antennas?

 Or should I change the cards wireless of 2 laptops?
 In case of changing the wifi cards what is the best? you recommend me for Ubuntu and with bluetooth

Thanks

Edit post: my actual wifi card: [http://ark.intel.com/es-es/products/75442/Intel-Dual-Band-Wireless-AC-3160](http://ark.intel.com/es-es/products/75442/Intel-Dual-Band-Wireless-AC-3160)

---

### Post by TuxManRemove on 2016-02-28
Hello,
Although the connection has never been perfect, she had noticed improvement.
 But from a week ago it does not work well, in fact it is worse than before.
 Would you happen to more people?
Tnaks

---

### Post by chili555 on 2016-02-28
My esteemed colleague Hadaka has asked me to give him a hand on this thread. In his message to me, he says, "I'm lost." I don't doubt it. You titled the thread Intel 3160 and then posted a wireless_script for an Atheros. Throughout the thread are references to laptop 1, 2 and 3. What, exactly, are we working on here? 

Please pick one and only one case and let's solve it. If you have other computers with similar problems, and if the steps here don't solve it, please start a new thread and Hadaka and I will be very, very happy to help. Whichever computer will be the subject of this thread, after you address some issues I noticed, post a new wireless script and we will proceed.

Many Linux wireless drivers are sensitive to the access point settings. First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Hadaka and I look forward to your next report.

---

### Post by TuxManRemove on 2016-02-29
Hi chili555,
 In this case the problem is the Intel 3160.
 I'll do what you say and then write.
 Thank you.

---

### Post by TuxManRemove on 2016-02-29
Hello,
Sorry for late response. I erased the hard drive on laptop. I installed Ubuntu 15.10 and then I did an upgrade and restarted.
 I reset the router. I have put only 20Hz and have tried several channels, 6 11 and 13.
 I have limited the speed b / g 54Mbps.
And of course, region IS.

Thanks,

```
########## wireless info START ##########

Report from: 29 Feb 2016 21:25 CET +0100

Booted last: 29 Feb 2016 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-30-generic #36-Ubuntu SMP Fri Feb 26 00:58:07 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8070]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1e4e:0110 Cubeternet 
Bus 001 Device 002: ID 8087:07dc Intel Corp. 
Bus 001 Device 004: ID 0781:556b SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                294912  0
mac80211              733184  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          200704  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp2s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13266 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10715 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11412985 (11.4 MB)  TX bytes:1668122 (1.6 MB)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:"Orange-AB1A"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: <MAC 'Orange-AB1A' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:95   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       654     1  0 21:10 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 3160 (Dual Band Wireless AC 3160)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.2.0-30-generic
GENERAL.FIRMWARE-VERSION:               25.30.13.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Orange-AB1A
GENERAL.CON-UUID:                       27fd841c-7634-4541-a58b-83ee1fc9adf5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     9 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   66400c2d-f969-41a9-82c8-d27d81d38cec | WLAN1057
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   27fd841c-7634-4541-a58b-83ee1fc9adf5 | Orange-AB1A
IP4.ADDRESS[1]:                         192.168.1.105/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1456776658
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.1.1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 4294967295
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       ip_address = 192.168.1.105
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_netbios_scope = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp2s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
JRC              <MAC 'JRC' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2         no        
_AUTO_ONOWiFi    <MAC '_AUTO_ONOWiFi' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2 802.1X  no        
WLAN1057         <MAC 'WLAN1057' [AN3]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2    no        
_ONOWiFi         <MAC '_ONOWiFi' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  52      &#9602;&#9604;__  --           no        
Orange-AB1A      <MAC 'Orange-AB1A' [AC1]>  Infra  13    2472 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2         yes     * 
ONOD7E0          <MAC 'ONOD7E0' [AN6]>  Infra  11    2462 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA1 WPA2    no        
vodafone34D8     <MAC 'vodafone34D8' [AN7]>  Infra  3     2422 MHz  54 Mbit/s  30      &#9602;___  WPA2         no        
_ONOWiFi         <MAC '_ONOWiFi' [AN8]>  Infra  11    2462 MHz  54 Mbit/s  17      &#9602;___  --           no        
NETGEAR_GUEST_2  <MAC 'NETGEAR_GUEST_2' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2         no        

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

[[/etc/NetworkManager/system-connections/Orange-AB1A]] (600 root)
[connection] id=Orange-AB1A | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Orange-AB1A
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WLAN1057]] (600 root)
[connection] id=WLAN1057 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=WLAN1057
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WLAN_8287]] (600 root)
[connection] id=WLAN_8287 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=WLAN_8287
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

country ES: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 23), (N/A), NO-OUTDOOR
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
    (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp1s0    no frequency information.

wlp2s0    32 channels in total; available frequencies :
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
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.472 GHz (Channel 13)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.472 GHz (Channel 13)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'Orange-AB1A' [AC1]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Orange-AB1A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000e954b094
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 02 - Address: <MAC 'JRC' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"JRC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bb52b140a1
                    Extra: Last beacon: 6508ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '_AUTO_ONOWiFi' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"_AUTO_ONOWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bb53138e81
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC '_ONOWiFi' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"_ONOWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bb52b1657f
                    Extra: Last beacon: 6508ms ago
          Cell 05 - Address: <MAC 'NETGEAR_GUEST_2' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR_GUEST_2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bb52b175b9
                    Extra: Last beacon: 6508ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     AB0A216C6A2C8AD07166628
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.2.0-30-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     292BCC26A10EA884DF6B5FF
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-12.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     2AFF7BF1EB0D33D3ACDC867
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.2.0-30-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    3.613872] iwlwifi 0000:02:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
[    3.636527] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[    3.636746] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[    3.721397] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    3.767185] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.768138] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[    4.985846] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    4.986031] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[    5.116227] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    5.117537] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    5.304945] r8169 0000:01:00.0 enp1s0: link down
[    5.304982] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    5.367017] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    8.035991] wlp2s0: authenticate with <MAC 'Orange-AB1A' [AC1]>
[    8.039748] wlp2s0: send auth to <MAC 'Orange-AB1A' [AC1]> (try 1/3)
[    8.081013] wlp2s0: authenticated
[    8.081203] wlp2s0: associating with AP with corrupt beacon and probe response
[    8.084305] wlp2s0: associate with <MAC 'Orange-AB1A' [AC1]> (try 1/3)
[    8.086553] wlp2s0: RX AssocResp from <MAC 'Orange-AB1A' [AC1]> (capab=0x421 status=0 aid=18)
[    8.087995] wlp2s0: associated
[    8.088017] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready

########## wireless info END ############
```

---

### Post by chili555 on 2016-02-29
It appears that you are connected and iwconfig says you are connected at 54 Mbps. Your readings look fine to me. May I assume the problem is solved?

I do notice this:> wlp2s0: associating with AP with corrupt beacon and probe responseThat, to me, sounds like a problem with the router, not the wireless card in the computer. Do other Ubuntu computers connected to the same router produce the same message?

---

### Post by TuxManRemove on 2016-02-29
Hello,
I do not have here the router. I can try tomorrow.
 Initially the problem was with another router.
 I did a test near the router:
 [http://ubuntuforums.org/showthread.php?t=2308410&p=13416903#post13416903](http://ubuntuforums.org/showthread.php?t=2308410&p=13416903#post13416903)
 And another test in the room next to the router:
[http://ubuntuforums.org/showthread.php?t=2308410&p=13416923#post13416923](http://ubuntuforums.org/showthread.php?t=2308410&p=13416923#post13416923)
 Not really the problem, but I get the impression that when the signal is below 45 or 50% the driver has serious problems. Wifi in college or library is also switched off. I've already changed the Intel 3160 wireless card for the same model.
I've thought about changing it for another model from another manufacturer....
Thanks

---

### Post by chili555 on 2016-02-29
> I've already changed the Intel 3160 wireless card for the same model.For another 3160?

---

### Post by TuxManRemove on 2016-02-29
> **chili555 said:**
> For another 3160?

Yes, I have two wifi card Intel 3160 AC

---

### Post by chili555 on 2016-02-29
Again, you connected at 54 Mbps and I see no disconnect in the log. Unless you have something more concrete than this, I see nothing that's wrong and therefore fixable:> but I get the impression ... One thing that may be useful is the latest firmware:```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/OpenELEC/iwlwifi-firmware.git
cd iwlwifi-firmware/firmware
sudo cp iwlwifi-3160*  /lib/firmware
```Reboot.

---

### Post by TuxManRemove on 2016-03-03
Hello Chili555,
Thank you very much, internet is no power off.
 Forgive it has been slow to respond. I did a test and I wanted to try some days.

I put this otopns:
```
options iwlwifi 11n_disable=8 power_save=0 power_level=5
```

 I do test from the next room:

```
########## wireless info START ##########

Report from: 01 Mar 2016 15:09 CET +0100

Booted last: 01 Mar 2016 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-30-generic #36-Ubuntu SMP Fri Feb 26 00:58:07 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8070]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1e4e:0110 Cubeternet 
Bus 001 Device 002: ID 8087:07dc Intel Corp. 
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

iwlmvm                294912  0
mac80211              733184  1 iwlmvm
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
iwlwifi               200704  1 iwlmvm
snd_soc_core          200704  1 snd_soc_rt5640
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp2s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1959 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2584680 (2.5 MB)  TX bytes:235018 (235.0 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:"Orange-AB1A"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: <MAC 'Orange-AB1A' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=33/70  Signal level=-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:36   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       636     1  0 15:03 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 3160 (Dual Band Wireless AC 3160)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.2.0-30-generic
GENERAL.FIRMWARE-VERSION:               15.195093.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Orange-AB1A
GENERAL.CON-UUID:                       27fd841c-7634-4541-a58b-83ee1fc9adf5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     6 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3,2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   09f79abb-a818-4b64-9990-c944bd8ed079 | ONO0DB5
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   27fd841c-7634-4541-a58b-83ee1fc9adf5 | Orange-AB1A
IP4.ADDRESS[1]:                         192.168.1.105/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1456841038
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.1.1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 4294967295
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       ip_address = 192.168.1.105
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_netbios_scope = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp2s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
_AUTO_ONOWiFi                    <MAC '_AUTO_ONOWiFi' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2 802.1X  no        
NETGEAR_GUEST_2                  <MAC 'NETGEAR_GUEST_2' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2         no        
JRC                              <MAC 'JRC' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA2         no        
Orange-37C0                      <MAC 'Orange-37C0' [AC11]>  Infra  11    2462 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
VodafoneC92F                     <MAC 'VodafoneC92F' [AC9]>  Infra  11    2462 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1         no        
Orange-89C0                      <MAC 'Orange-89C0' [AC10]>  Infra  11    2462 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
PELUQUERIA MARIA                 <MAC 'PELUQUERIA MARIA' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2    no        
HP-Print-58-Deskjet 2540 series  <MAC 'HP-Print-58-Deskjet 2540 series' [AC8]>  Infra  6     2437 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2         no        
PACO                             <MAC 'PACO' [AC6]>  Infra  2     2417 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2    no        
_AUTO_ONOWiFi                    <MAC '_AUTO_ONOWiFi' [AC14]>  Infra  13    2472 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2 802.1X  no        
_ONOWiFi                         <MAC '_ONOWiFi' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  52      &#9602;&#9604;__  --           no        
_ONOWiFi                         <MAC '_ONOWiFi' [AC15]>  Infra  13    2472 MHz  54 Mbit/s  45      &#9602;&#9604;__  --           no        
ONO                              <MAC 'ONO' [AN13]>  Infra  9     2452 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2    no        
_AUTO_ONOWiFi                    <MAC '_AUTO_ONOWiFi' [AN14]>  Infra  9     2452 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2 802.1X  no        
_ONOWiFi                         <MAC '_ONOWiFi' [AN15]>  Infra  9     2452 MHz  54 Mbit/s  50      &#9602;&#9604;__  --           no        
ONO0DB5                          <MAC 'ONO0DB5' [AC13]>  Infra  13    2472 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1 WPA2    no        
Orange-AB1A                      <MAC 'Orange-AB1A' [AC1]>  Infra  13    2472 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2         yes     * 
ASUS                             <MAC 'ASUS' [AC12]>  Infra  13    2472 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2         no        

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

[[/etc/NetworkManager/system-connections/Orange-AB1A]] (600 root)
[connection] id=Orange-AB1A | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Orange-AB1A
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WLAN1057]] (600 root)
[connection] id=WLAN1057 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=WLAN1057
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WLAN_8287]] (600 root)
[connection] id=WLAN_8287 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=WLAN_8287
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/ONO0DB5]] (600 root)
[connection] id=ONO0DB5 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ONO0DB5
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

country ES: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 23), (N/A), NO-OUTDOOR
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
    (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp1s0    no frequency information.

wlp2s0    32 channels in total; available frequencies :
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
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.472 GHz (Channel 13)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.462 GHz (Channel 11)
      5   APs on   Frequency:2.472 GHz (Channel 13)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'Orange-AB1A' [AC1]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Orange-AB1A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000fc46e414c
                    Extra: Last beacon: 43904ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 02 - Address: <MAC 'JRC' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"JRC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ca30d0503f
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '_AUTO_ONOWiFi' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"_AUTO_ONOWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ca30d05c9a
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC '_ONOWiFi' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"_ONOWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ca30d06ce4
                    Extra: Last beacon: 52ms ago
          Cell 05 - Address: <MAC 'NETGEAR_GUEST_2' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR_GUEST_2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ca30d0745d
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'PACO' [AC6]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"PACO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005d3de28d7
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'PELUQUERIA MARIA' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"PELUQUERIA MARIA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000066bc3a46067
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'HP-Print-58-Deskjet 2540 series' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-58-Deskjet 2540 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000592136d1b
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'VodafoneC92F' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"VodafoneC92F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000028682b34c68
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'Orange-89C0' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Orange-89C0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000036245ef3a57
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'Orange-37C0' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Orange-37C0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000058db67ed5
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'ASUS' [AC12]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"ASUS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000005214a1cd4
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'ONO0DB5' [AC13]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"ONO0DB5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001c2e13fd4
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC '_AUTO_ONOWiFi' [AC14]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"_AUTO_ONOWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001c2e147d2
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 15 - Address: <MAC '_ONOWiFi' [AC15]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"_ONOWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001c2e14ec7
                    Extra: Last beacon: 52ms ago

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     AB0A216C6A2C8AD07166628
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.2.0-30-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     292BCC26A10EA884DF6B5FF
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-12.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     2AFF7BF1EB0D33D3ACDC867
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.2.0-30-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 1000

[iwlwifi]
11n_disable: 8
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 5
power_save: N
swcrypto: 0
uapsd_disable: Y

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=8 power_save=0 power_level=5 #bt_coex_active=1 #wd_disable=1

[/etc/modprobe.d/mac80211.conf]
options mac80211 probe_wait_ms=1000

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    3.720146] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.721014] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[    5.007100] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    5.192775] r8169 0000:01:00.0 enp1s0: link down
[    5.192826] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    5.194240] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    5.194423] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[    5.320118] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[   34.238341] wlp2s0: authenticate with <MAC 'Orange-AB1A' [AC1]>
[   34.240982] wlp2s0: direct probe to <MAC 'Orange-AB1A' [AC1]> (try 1/3)
[   34.442653] wlp2s0: send auth to <MAC 'Orange-AB1A' [AC1]> (try 2/3)
[   34.444273] wlp2s0: authenticated
[   34.444471] wlp2s0: associating with AP with corrupt beacon and probe response
[   34.445491] wlp2s0: associate with <MAC 'Orange-AB1A' [AC1]> (try 1/3)
[   34.447822] wlp2s0: RX AssocResp from <MAC 'Orange-AB1A' [AC1]> (capab=0x421 status=0 aid=18)
[   34.449253] wlp2s0: associated
[   34.449280] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[   36.799018] wlp2s0: deauthenticating from <MAC 'Orange-AB1A' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[   40.680670] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   43.273116] wlp2s0: authenticate with <MAC 'Orange-AB1A' [AC1]>
[   43.276118] wlp2s0: send auth to <MAC 'Orange-AB1A' [AC1]> (try 1/3)
[   43.277659] wlp2s0: authenticated
[   43.277785] wlp2s0: associating with AP with corrupt beacon and probe response
[   43.280597] wlp2s0: associate with <MAC 'Orange-AB1A' [AC1]> (try 1/3)
[   43.282843] wlp2s0: RX AssocResp from <MAC 'Orange-AB1A' [AC1]> (capab=0x421 status=0 aid=18)
[   43.283913] wlp2s0: associated
[   43.283935] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready

########## wireless info END ############
```


 Internet work well, although not as well as other laptop. 
 I would like to continue testing, I am willing to buy another wifi cand and do new test. Then I put you here.
I want to find the best card for Linux ultrabook wifi and check here.

 What wireless card you recommend?
Thak you very much!

---

### Post by chili555 on 2016-03-04
> I do test from the next room:And the result is:> wlp2s0    IEEE 802.11abgn  ESSID:"Orange-AB1A"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: <MAC 'Orange-AB1A' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=[COLOR="#FF0000"]33/70[/COLOR]  Signal level=-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:36   Missed beacon:0
I am puzzled by this:> Cell 11 - Address: <MAC 'Orange-37C0' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=[COLOR="#FF0000"]51/70[/COLOR]  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Orange-37C0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000058db67ed5
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSKWhat is puzzling to me is that there is another SSID with much higher signal strength nearby. But how could it be closer to you than the next room?

Is there a power setting in your router? Can you increase it?  [http://www.techerator.com/wp-content/uploads/tomatotransmit.png](http://www.techerator.com/wp-content/uploads/tomatotransmit.png)

---

### Post by TuxManRemove on 2016-03-04
Hello,
I can not increase power, I do not have that option in the configuration.

The other signal .... I talk to my neighbor.

I am willing to buy another wireless card and do the same test.
What wireless card you recommend?

Thanks

---

### Post by chili555 on 2016-03-04
All of my laptops have Intels. May I see:```
dmesg | grep iwl
```

---

### Post by TuxManRemove on 2016-03-04
What models?

Ok:
```
[    3.852579] iwlwifi: unknown parameter '#bt_coex_active' ignored
[    3.852583] iwlwifi: unknown parameter '#wd_disable' ignored
[    3.854023] iwlwifi 0000:02:00.0: Unsupported splx structure
[    3.887059] iwlwifi 0000:02:00.0: loaded firmware version 15.195093.0 op_mode iwlmvm
[    3.915322] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[    3.915479] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.915803] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.048753] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.050084] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[    5.375963] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    5.376292] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    5.485729] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    5.486051] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
```

---

