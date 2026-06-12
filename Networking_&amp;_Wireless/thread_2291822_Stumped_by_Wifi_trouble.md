---
title: "Stumped by Wifi trouble"
date: 2015-08-23
forum: Networking &amp; Wireless
---

### Post by erik25 on 2015-08-23
Hi guys,
Firstly, please excuse any my ignorance of both correct procedure on the forums and also with the OS, I've never used either of these before.

Ok, to the misuse; I've recently come over to Ubuntu from Windows 8.1 as I got sick and tired of paying for bugs and inefficiency. I've never before used a Linux system but am slowly coming to grips with the terminal system, etc. 
I seem to have everything running to my liking but my wifi connection is horrific; I can connect with no problem but the download speed is incredibly. I've down a bit of searching around to try and rectify the issue but nothing has worked. I recently stumbled onto a wifi script that will diagnose the issue and have saved the results, I'm hoping someone can take a look at it and help me out.

```

########## wireless info START ##########

Report from: 23 Aug 2015 14:50 AEST +1000

Booted last: 23 Aug 2015 14:02 AEST +1000

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-26-generic #28~14.04.1-Ubuntu SMP Wed Aug 12 14:09:17 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 13)
    Subsystem: Acer Incorporated [ALI] Device [1025:080f]
    Kernel driver in use: alx

04:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6621]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 004 Device 002: ID 04f2:b3f6 Chicony Electronics Co., Ltd 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath3k                  20480  0 
ath9k                 147456  0 
ath9k_common           32768  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
bluetooth             491520  12 bnep,ath3k,btusb,rfcomm
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              708608  1 ath9k
cfg80211              524288  4 ath,ath9k_common,ath9k,mac80211
acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
wmi                    20480  1 acer_wmi
video                  20480  1 acer_wmi

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
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24011 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17950 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26864437 (26.8 MB)  TX bytes:2174697 (2.1 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Belkin.5B2D"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Belkin.5B2D' [AC1]>   
          Bit Rate=144.4 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:12  Invalid misc:108   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search Belkin

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root      1152     1  0 14:02 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Belkin.5B2D] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           104 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Belkin.5B2D_5GHz:Infra, <MAC 'Belkin.5B2D_5GHz' [AC5]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 90 WPA WPA2
    Belkin.5B2D_5GHz_5GEXT: Infra, <MAC 'Belkin.5B2D_5GHz_5GEXT' [AC6]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 57 WPA2
    Belkin.5B2D_2GEXT: Infra, <MAC 'Belkin.5B2D_2GEXT' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA2
    OPTUS_021DD6:    Infra, <MAC 'OPTUS_021DD6' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    *Belkin.5B2D:    Infra, <MAC 'Belkin.5B2D' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    DODOE328:        Infra, <MAC 'DODOE328' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA
    MANICARO:        Infra, <MAC 'MANICARO' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    homewireless:    Infra, <MAC 'homewireless' [AN8]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    NETGEAR46:       Infra, <MAC 'NETGEAR46' [AN9]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 52 WPA2
    DODOD290:        Infra, <MAC 'DODOD290' [AN10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA

  IPv4 Settings:
    Address:         192.168.2.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
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

Sorry, try again.
Sorry, try again.
Sorry, try again.
sudo: 3 incorrect password attempts

Acquisition of admin privileges failed.

##### iw reg get ########################

Region: Australia/Melbourne (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Sorry, try again.
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.745 GHz

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Belkin.5B2D' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Belkin.5B2D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002469806950
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'DODOE328' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"DODOE328"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002806158f161
                    Extra: Last beacon: 192ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Belkin.5B2D_2GEXT' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Belkin.5B2D_2GEXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001c2c233d5
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'MANICARO' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"MANICARO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000023530836189
                    Extra: Last beacon: 224ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Belkin.5B2D_5GHz' [AC5]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Belkin.5B2D_5GHz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002469867729
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Belkin.5B2D_5GHz_5GEXT' [AC6]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Belkin.5B2D_5GHz_5GEXT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000024695d7b39
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'OPTUS_021DD6' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"OPTUS_021DD6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000389f468e28
                    Extra: Last beacon: 68ms ago
          Cell 08 - Address: <MAC '' [AC8]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:""
                    Mode:Master

##### module infos ######################

[ath3k]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     C77B8A018F5C738ABC4CA47
depends:        bluetooth
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512

[ath9k]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DFC03DD607884E899C8398C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8836292C9539A29CB162A5D
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C1A24C37619ED65AB1240B9
depends:        ath
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     DF4E06FB15FF0707074A816
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
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
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1

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

[/etc/modprobe.d/rtl8192ce.conf]
sudo modprobe -rfv rtl18192ce
sudo medprobe -v rtl18192ce

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x10a1 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0034 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   95.080255] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   99.728592] wlan0: authenticate with <MAC 'Belkin.5B2D' [AC1]>
[   99.738824] wlan0: send auth to <MAC 'Belkin.5B2D' [AC1]> (try 1/3)
[   99.741017] wlan0: authenticated
[   99.743660] wlan0: associate with <MAC 'Belkin.5B2D' [AC1]> (try 1/3)
[   99.747721] wlan0: RX AssocResp from <MAC 'Belkin.5B2D' [AC1]> (capab=0x411 status=0 aid=2)
[   99.747824] wlan0: associated
[   99.747839] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############ 
```

---

### Post by QIII on 2015-08-23
*Moved to **Networking & Wireless***

Hello and welcome to the Forums.

Your question is more likely to get attention in this sub-forum.

Cheers!

---

### Post by Hadaka on 2015-08-23
Hi, from a working internet connection
 please open a terminal ctrl/alt/t then copy and paste
these commands, one at a time.
```
echo "blacklist acer-wmi" | sudo tee -a  /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv acer_wmi
sudo modprobe -rfv ath9k
sudo modprobe ath9k nohwcrypt=1
```
then do..
```
sudo iw reg set AU
sudo sed -i 's/^REG.*=$/&AU/' /etc/default/crda
```
boot and test
thanks.

---

### Post by erik25 on 2015-08-23
Thanks for the help guys.

Hakada, I’m unsure if the codes actually worked as I saw "ERROR ignoring bad line starting with sudo" appear. I did restart and run speedtest.net and the speed matches my wired connection, but loading other web pages or downloading apps is still slow.

---

### Post by weatherman2 on 2015-08-23
Which line failed?

---

### Post by Hadaka on 2015-08-23
i suspect it was this one..
```
sudo sed -i 's/^REG.*=$/&AU/' /etc/default/crda
```
i made a correction to it about 4 hours ago, sorry.
please copy and paste again.
thanks.

---

### Post by erik25 on 2015-08-23
```
sudo modprobe -rfv acer_wmi
sudo modprobe -rfv ath9k
```

It was these two lines

---

### Post by Hadaka on 2015-08-23
those 2 lines are valid and you should get no response from them when ran.
please copy and paste to avoid typo's
please re-run all lines 
```
sudo modprobe -rfv acer_wmi
sudo modprobe -rfv ath9k
echo "blacklist acer-wmi" | sudo tee -a  /etc/modprobe.d/blacklist.conf 
echo "modprobe ath9k nohwcrypt=1" | *sudo tee -a * /etc/*modprobe*.d/ath9k.conf 
```
then do..
```
sudo iw reg set AU 
sudo sed -i 's/^REG.*=$/&AU/' /etc/default/crda
```
boot and test

---

### Post by Hadaka on 2015-08-23
those lines qre valis and you should get no response from them when ran.
please copy and past to avoid typo's
please re-run all lines 
```
sudo modprobe -rfv acer_wmi
sudo modprobe -rfv ath9k
echo "blacklist acer-wmi" | sudo tee -a  /etc/modprobe.d/blacklist.conf sudo
 modprobe ath9k nohwcrypt=1
```
then do..
```
sudo iw reg set AU 
sudo sed -i 's/^REG.*=$/&AU/' /etc/default/crda
```

---

### Post by erik25 on 2015-08-23
Ok, I've re-run the lines and attached the screen print for you to look over while I boot

---

### Post by Hadaka on 2015-08-23
are you in the guest mode? and what is 
[h=2]RTL8192ce[/h]did you used to have this card and replaced it?

---

### Post by erik25 on 2015-08-23
No not in guest mode and that's the card that came with the laptop. I haven't replaced it

---

### Post by Hadaka on 2015-08-23
something is odd with the sudo modprobe command..
please do and post the output,,
```
cat /etc/modprobe.d/rt8192ce.conf
```
I think its suppose to be ..so please do..
```
echo "blacklist r8192ce" | sudo tee -a /etc/modprobe.d/rt8192ce.conf
```

this was in your info text file...
```
#### NetworkManager profiles ###########

Sorry, try again.
Sorry, try again.
Sorry, try again.
sudo: 3 incorrect password attempts

Acquisition of admin privileges failed.

``` but it only seems to be with the modprobe command
looking for answers
thanks,.

---

### Post by erik25 on 2015-08-23
I've run the code again and attached the output. I appreciate the assistance

---

### Post by Hadaka on 2015-08-24
Ok, reboot your computer then do and post,,
```
sudo modprobe -rfv acer_wmi 
sudo modprobe -rfv ath9k 
sudo modprobe ath9k nohwcrypt=1
```
then delete the last wireless info text file in your
home directory then run and post a new one
thanks

---

### Post by erik25 on 2015-08-24
Ok, so I did everything you asked in the last reply and here are the results ( I also attached a picture of the terminal feedback before I ran the wifi script)



```

########## wireless info START ##########

Report from: 24 Aug 2015 16:24 AEST +1000

Booted last: 24 Aug 2015 16:20 AEST +1000

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-26-generic #28~14.04.1-Ubuntu SMP Wed Aug 12 14:09:17 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 13)
    Subsystem: Acer Incorporated [ALI] Device [1025:080f]
    Kernel driver in use: alx

04:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6621]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 004 Device 002: ID 04f2:b3f6 Chicony Electronics Co., Ltd 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 04ca:3006 Lite-On Technology Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                 147456  0 
ath9k_common           32768  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              708608  1 ath9k
cfg80211              524288  4 ath,ath9k_common,ath9k,mac80211
ath3k                  20480  0 
bluetooth             491520  23 bnep,ath3k,btusb,rfcomm
wmi                    20480  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:121.210.210.15  Bcast:121.210.211.255  Mask:255.255.254.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:690 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:186497 (186.4 KB)  TX bytes:100593 (100.5 KB)
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         121.210.210.1   0.0.0.0         UG    0      0        0 eth0
121.210.210.0   0.0.0.0         255.255.254.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search vi.bigpond.net.au

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root      1328     1  0 16:20 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Belkin.5B2D_5GHz] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Belkin.5B2D:     Infra, <MAC 'Belkin.5B2D' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Belkin.5B2D_2GEXT: Infra, <MAC 'Belkin.5B2D_2GEXT' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA2
    DODOD290:        Infra, <MAC 'DODOD290' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA
    OPTUS_021DD6:    Infra, <MAC 'OPTUS_021DD6' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Belkin.5B2D_5GHz_5GEXT: Infra, <MAC 'Belkin.5B2D_5GHz_5GEXT' [AC6]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 34 WPA2
    Telstra2A01B5:   Infra, <MAC 'Telstra2A01B5' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    Belkin.5B2D_5GHz:Infra, <MAC 'Belkin.5B2D_5GHz' [AC7]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         121.210.210.15
    Prefix:          23 (255.255.254.0)
    Gateway:         121.210.210.1

    DNS:             61.9.134.49
    DNS:             61.9.133.193

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

[[/etc/NetworkManager/system-connections/Belkin.5B2D]] (600 root)
[connection] id=Belkin.5B2D | type=802-11-wireless
[802-11-wireless] ssid=Belkin.5B2D | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Belkin.5B2D_2GEXT]] (600 root)
[connection] id=Bedroom | type=802-11-wireless
[802-11-wireless] ssid=Belkin.5B2D_2GEXT | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Belkin.5B2D_5GHz]] (600 root)
[connection] id=Belkin.5B2D_5GHz | type=802-11-wireless
[802-11-wireless] ssid=Belkin.5B2D_5GHz | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Australia/Melbourne (based on set time zone)

country AU:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (3, 23)
    (5250 - 5330 @ 40), (3, 23), DFS
    (5735 - 5835 @ 40), (3, 30)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     26 channels in total; available frequencies :
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
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.437 GHz (Channel 6)
      4   APs on   Frequency:2.462 GHz (Channel 11)
      2   APs on   Frequency:5.2 GHz (Channel 40)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Belkin.5B2D' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-5 dBm  
                    Encryption key:on
                    ESSID:"Belkin.5B2D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000028113c7d8
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Telstra2A01B5' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Telstra2A01B5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000eb87be7fb7f
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'DODOD290' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"DODOD290"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000122f63b16d
                    Extra: Last beacon: 1580ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Belkin.5B2D_2GEXT' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Belkin.5B2D_2GEXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000280c32c90
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'OPTUS_021DD6' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"OPTUS_021DD6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ec33a9908
                    Extra: Last beacon: 1548ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Belkin.5B2D_5GHz_5GEXT' [AC6]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Belkin.5B2D_5GHz_5GEXT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002809a6739
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Belkin.5B2D_5GHz' [AC7]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"Belkin.5B2D_5GHz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000028112908f
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'DODOE328' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"DODOE328"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000295ca0de142
                    Extra: Last beacon: 1956ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DFC03DD607884E899C8398C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8836292C9539A29CB162A5D
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C1A24C37619ED65AB1240B9
depends:        ath
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     DF4E06FB15FF0707074A816
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ath3k]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     C77B8A018F5C738ABC4CA47
depends:        bluetooth
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512

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
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/8192cu-disable-power-management.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0

[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1
modprobe ath9k nohwcrypt=1

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
blacklist acer-wmi
blacklist acer-wmi
blacklist acer-wmi
blacklist acer-wmi
blacklist acer-wmi
blacklist acer-wmi

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

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

[/etc/modprobe.d/rt8192ce.conf]
blacklist r8192ce

[/etc/modprobe.d/rtl8192ce.conf]
sudo modprobe -rfv rtl18192ce
sudo medprobe -v rtl18192ce

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x10a1 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0034 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  236.691572] wlan0: deauthenticating from <MAC 'Belkin.5B2D_2GEXT' [AC4]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  236.793109] ath9k: ath9k: Driver unloaded
[  247.999097] ath: phy0: ASPM enabled: 0x42
[  247.999103] ath: EEPROM regdomain: 0x6a
[  247.999106] ath: EEPROM indicates we should expect a direct regpair map
[  247.999109] ath: Country alpha2 being used: 00
[  247.999111] ath: Regpair used: 0x6a
[  248.021484] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  258.109539] wlan0: authenticate with <MAC 'Belkin.5B2D_5GHz' [AC7]>
[  258.124318] wlan0: direct probe to <MAC 'Belkin.5B2D_5GHz' [AC7]> (try 1/3)
[  258.328167] wlan0: send auth to <MAC 'Belkin.5B2D_5GHz' [AC7]> (try 2/3)
[  258.329544] wlan0: authenticated
[  263.134437] wlan0: aborting authentication with <MAC 'Belkin.5B2D_5GHz' [AC7]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  273.264712] wlan0: authenticate with <MAC 'Belkin.5B2D_5GHz' [AC7]>
[  273.275915] wlan0: send auth to <MAC 'Belkin.5B2D_5GHz' [AC7]> (try 1/3)
[  273.277127] wlan0: authenticated
[  278.281112] wlan0: aborting authentication with <MAC 'Belkin.5B2D_5GHz' [AC7]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  288.808784] wlan0: authenticate with <MAC 'Belkin.5B2D_5GHz' [AC7]>
[  288.823692] wlan0: send auth to <MAC 'Belkin.5B2D_5GHz' [AC7]> (try 1/3)
[  288.825104] wlan0: authenticated
[  293.833791] wlan0: aborting authentication with <MAC 'Belkin.5B2D_5GHz' [AC7]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  304.868400] wlan0: authenticate with <MAC 'Belkin.5B2D_5GHz' [AC7]>
[  304.883236] wlan0: send auth to <MAC 'Belkin.5B2D_5GHz' [AC7]> (try 1/3)
[  304.884750] wlan0: authenticated
[  309.890130] wlan0: aborting authentication with <MAC 'Belkin.5B2D_5GHz' [AC7]> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############
```

---

### Post by Hadaka on 2015-08-24
hi please show me the output of..
```
cat /etc/modprobe.d/rtl8192ce.conf
cat /etc/modprobe.d/ath9k.conf
```
also instead of doing a screen shot for the error messages just copy
and paste them in your reply here, it makes it easier to copy and paste
information to do searches with,
thanks

---

### Post by erik25 on 2015-08-24
As requested
```
erik@BigE-Laptop:~$ cat /etc/modprobe.d/rtl8192ce.conf

sudo modprobe -rfv rtl18192ce
sudo medprobe -v rtl18192ce

```

---

### Post by Hadaka on 2015-08-24
ok please do..and post the output of..
```
sudo rm /etc/modprobe.d/rtl8192ce.conf
sudo rm /etc/modprobe.d/ath9k.conf
```
then boot
thanks.

---

### Post by erik25 on 2015-08-24
Here is all that was in terminal

```
erik@BigE-Laptop:~$ sudo rm /etc/modprobe.d/rtl8192ce.conf
[sudo] password for erik: 
erik@BigE-Laptop:~$ sudo rm /etc/modprobe.d/ath9k.conf
erik@BigE-Laptop:~$ 


```

---

### Post by Hadaka on 2015-08-24
good thats all it should say..
please do and post the output of..
```
*echo* "*options ath9k nohwcrypt*=*1*" | sudo tee -a /etc/modprobe.d/ath9k.conf
cat /etc/modprobe.d/ath9k.conf
```
thanks.

---

### Post by erik25 on 2015-08-25
Here you go:
```
erik@BigE-Laptop:~$ echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
[sudo] password for erik: 
options ath9k nohwcrypt=1
erik@BigE-Laptop:~$ cat /etc/modprobe.d/ath9k.conf
options ath9k nohwcrypt=1
erik@BigE-Laptop:~$ 

```

---

### Post by Hadaka on 2015-08-25
ok, you should be seeing some improvement..yes/...no?

---

### Post by erik25 on 2015-08-25
Yes there is slight improvement but still very slow. Connection information is saying 110mb/s, but during browsing and downloads I'm no where near that

---

### Post by Hadaka on 2015-08-25
do you still have windows on that machine? run 
speedtest.net with windows then ubuntu and see how
they compare. post a fresh wireless info text as well.
ath9k doenst have alot of tweaks.
I just noticed you have network manager and wcid installed
you cant have both. Let's unload wcid..please do...
```
sudo apt-get remove --purge wicd
sudo apt-get autoremove wicd
```
BOOT
thanks.

---

### Post by erik25 on 2015-08-25
No, I’m running only Ubuntu from this machine. I unloaded wcid like you suggested.

As a reference I ran sppedtest.net on my wired connection and I’m downloading at 21.6mb/s as opposed to my wifi which struggles so bad I can't even load the test properly.

Here is the fresh info text
```
########## wireless info START ##########

Report from: 26 Aug 2015 11:06 AEST +1000

Booted last: 26 Aug 2015 10:52 AEST +1000

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-26-generic #28~14.04.1-Ubuntu SMP Wed Aug 12 14:09:17 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 13)
    Subsystem: Acer Incorporated [ALI] Device [1025:080f]
    Kernel driver in use: alx

04:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6621]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 004 Device 002: ID 04f2:b3f6 Chicony Electronics Co., Ltd 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 04ca:3006 Lite-On Technology Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

ath3k                  20480  0 
bluetooth             491520  23 bnep,ath3k,btusb,rfcomm
ath9k                 147456  0 
ath9k_common           32768  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              708608  1 ath9k
cfg80211              524288  4 ath,ath9k_common,ath9k,mac80211
wmi                    20480  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:121.210.210.15  Bcast:121.210.211.255  Mask:255.255.254.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1682 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1253426 (1.2 MB)  TX bytes:209955 (209.9 KB)
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7358 errors:0 dropped:1 overruns:0 frame:0
          TX packets:6955 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5806923 (5.8 MB)  TX bytes:877238 (877.2 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Belkin.5B2D"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Belkin.5B2D' [AC1]>   
          Bit Rate=240 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-27 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         121.210.210.1   0.0.0.0         UG    0      0        0 eth0
121.210.210.0   0.0.0.0         255.255.254.0   U     1      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search vi.bigpond.net.au Belkin

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1318     1  0 10:52 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Belkin.5B2D] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           240 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Belkin.5B2D_5GHz:Infra, <MAC 'Belkin.5B2D_5GHz' [AC6]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    Belkin.5B2D_5GHz_5GEXT: Infra, <MAC 'Belkin.5B2D_5GHz_5GEXT' [AC7]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 49 WPA2
    OPTUS_021DD6:    Infra, <MAC 'OPTUS_021DD6' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    DODOD290:        Infra, <MAC 'DODOD290' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA
    Belkin.5B2D_2GEXT: Infra, <MAC 'Belkin.5B2D_2GEXT' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    Telstra2A01B5:   Infra, <MAC 'Telstra2A01B5' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA2
    DODOE328:        Infra, <MAC 'DODOE328' [AN7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA
    TPG 7503:        Infra, <MAC 'TPG 7503' [AN8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    wlan-ap:         Infra, <MAC 'wlan-ap' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    *Belkin.5B2D:    Infra, <MAC 'Belkin.5B2D' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 95 WPA WPA2
    Blake 1_2GEXT:   Infra, <MAC 'Blake 1_2GEXT' [AN11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2

  IPv4 Settings:
    Address:         192.168.2.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         121.210.210.15
    Prefix:          23 (255.255.254.0)
    Gateway:         121.210.210.1

    DNS:             61.9.134.49
    DNS:             61.9.133.193

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

[[/etc/NetworkManager/system-connections/Belkin.5B2D]] (600 root)
[connection] id=Belkin.5B2D | type=802-11-wireless
[802-11-wireless] ssid=Belkin.5B2D | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Belkin.5B2D_2GEXT]] (600 root)
[connection] id=Bedroom | type=802-11-wireless
[802-11-wireless] ssid=Belkin.5B2D_2GEXT | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Australia/Melbourne (based on set time zone)

country AU:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (3, 23)
    (5250 - 5330 @ 40), (3, 23), DFS
    (5735 - 5835 @ 40), (3, 30)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     26 channels in total; available frequencies :
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
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)
      4   APs on   Frequency:2.462 GHz (Channel 11)
      2   APs on   Frequency:5.2 GHz (Channel 40)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Belkin.5B2D' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"Belkin.5B2D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000014f34cd252
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'DODOD290' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"DODOD290"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000035f8e1e146
                    Extra: Last beacon: 192ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'OPTUS_021DD6' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"OPTUS_021DD6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000328eed4e74
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Belkin.5B2D_2GEXT' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Belkin.5B2D_2GEXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000014f3214086
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Telstra2A01B5' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Telstra2A01B5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000edc4525d089
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Belkin.5B2D_5GHz' [AC6]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"Belkin.5B2D_5GHz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014f3532a6d
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Belkin.5B2D_5GHz_5GEXT' [AC7]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Belkin.5B2D_5GHz_5GEXT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014f2efd25a
                    Extra: Last beacon: 4ms ago

##### module infos ######################

[ath3k]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     C77B8A018F5C738ABC4CA47
depends:        bluetooth
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512

[ath9k]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DFC03DD607884E899C8398C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8836292C9539A29CB162A5D
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C1A24C37619ED65AB1240B9
depends:        ath
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     DF4E06FB15FF0707074A816
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
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
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/8192cu-disable-power-management.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0

[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1

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
blacklist acer-wmi
blacklist acer-wmi
blacklist acer-wmi
blacklist acer-wmi
blacklist acer-wmi
blacklist acer-wmi

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

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

[/etc/modprobe.d/rt8192ce.conf]
blacklist r8192ce

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x10a1 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0034 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  377.721324] wlan0: authenticate with <MAC 'Belkin.5B2D' [AC1]>
[  377.736423] wlan0: send auth to <MAC 'Belkin.5B2D' [AC1]> (try 1/3)
[  377.738938] wlan0: authenticated
[  377.740280] wlan0: associate with <MAC 'Belkin.5B2D' [AC1]> (try 1/3)
[  377.744637] wlan0: RX AssocResp from <MAC 'Belkin.5B2D' [AC1]> (capab=0x411 status=0 aid=2)
[  377.745154] wlan0: associated
[  381.709558] wlan0: authenticate with <MAC 'Belkin.5B2D' [AC1]>
[  381.725260] wlan0: send auth to <MAC 'Belkin.5B2D' [AC1]> (try 1/3)
[  381.727399] wlan0: authenticated
[  381.728129] wlan0: associate with <MAC 'Belkin.5B2D' [AC1]> (try 1/3)
[  381.732275] wlan0: RX AssocResp from <MAC 'Belkin.5B2D' [AC1]> (capab=0x411 status=0 aid=2)
[  381.732385] wlan0: associated
[  387.703206] wlan0: authenticate with <MAC 'Belkin.5B2D' [AC1]>
[  387.717726] wlan0: send auth to <MAC 'Belkin.5B2D' [AC1]> (try 1/3)
[  387.719854] wlan0: authenticated
[  387.721933] wlan0: associate with <MAC 'Belkin.5B2D' [AC1]> (try 1/3)
[  387.726078] wlan0: RX AssocResp from <MAC 'Belkin.5B2D' [AC1]> (capab=0x411 status=0 aid=2)
[  387.726191] wlan0: associated
[  391.714938] wlan0: authenticate with <MAC 'Belkin.5B2D' [AC1]>
[  391.729654] wlan0: send auth to <MAC 'Belkin.5B2D' [AC1]> (try 1/3)
[  391.741531] wlan0: authenticated
[  391.745936] wlan0: associate with <MAC 'Belkin.5B2D' [AC1]> (try 1/3)
[  391.750140] wlan0: RX AssocResp from <MAC 'Belkin.5B2D' [AC1]> (capab=0x411 status=0 aid=2)
[  391.750320] wlan0: associated
[  401.748650] wlan0: authenticate with <MAC 'Belkin.5B2D' [AC1]>
[  401.763462] wlan0: send auth to <MAC 'Belkin.5B2D' [AC1]> (try 1/3)
[  401.765625] wlan0: authenticated
[  401.767449] wlan0: associate with <MAC 'Belkin.5B2D' [AC1]> (try 1/3)
[  401.771538] wlan0: RX AssocResp from <MAC 'Belkin.5B2D' [AC1]> (capab=0x411 status=0 aid=2)
[  401.771649] wlan0: associated

########## wireless info END ############

```

---

### Post by chili555 on 2015-08-26
> eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:[COLOR="#FF0000"][COLOR="#FF0000"]121.210.210.15[/COLOR][/COLOR]  Bcast:121.210.211.255  Mask:255.255.254.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1682 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1253426 (1.2 MB)  TX bytes:209955 (209.9 KB)
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:[COLOR="#FF0000"]192.168.2.4[/COLOR]  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7358 errors:0 dropped:1 overruns:0 frame:0
          TX packets:6955 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5806923 (5.8 MB)  TX bytes:877238 (877.2 KB)My colleague Hadaka and I would like to understand why the ethernet and wireless are connected at the same time *and to different networks!!!* I'm sure Network Manager is quite confused as, in fact, am I!

---

