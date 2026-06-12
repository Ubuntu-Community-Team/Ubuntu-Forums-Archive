---
title: "Dell xps 14z intel Advanced-N 6230 bad connection"
date: 2014-10-21
forum: Networking &amp; Wireless
---

### Post by madm on 2014-10-21
Hey, i got a really bad wireless connection. 
Right now my laptop is 30 cm away of the router and has got 65% (Link Quality=50/70).
 With my mobilephone and other devices the connection is fine. The strange thing is, that before i get connected to the router it says "100%" but right after i am connected it falls down to 50-70%.
  I turned the power-option off, it didnt help Would be nice if someone could help me!   
```


########## wireless info START ##########

Report from: 21 Oct 2014 18:23 CEST +0200

Booted last: 21 Oct 2014 18:02 CEST +0200

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Cinnamon (Software Rendering)

##### lspci #############################

07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: Dell Device [1028:0522]
    Kernel driver in use: atl1c

08:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6230 [Rainbow Peak] [8086:0091] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6230 AGN [8086:5221]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 001 Device 004: ID 8086:0189 Intel Corp. 
Bus 001 Device 003: ID 174f:143f Syntek 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                232285  0 
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
mac80211              630653  1 iwldvm
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
mxm_wmi                13021  1 nouveau
wmi                    19177  3 dell_wmi,mxm_wmi,nouveau

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
          inet addr:10.0.40.67  Bcast:10.0.41.255  Mask:255.255.254.0
          inet6 addr: fe80::8a53:2eff:fe59:fa2e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48798 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3806 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12017018 (12.0 MB)  TX bytes:565158 (565.1 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"wlank"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: <MAC 'wlank' [AC1]>   
          Bit Rate=48 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:70   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.40.1       0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        10.0.40.1       255.255.0.0     UG    0      0        0 wlan0
10.0.40.0       0.0.0.0         255.255.254.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 127.0.1.1
search dhcp.ewt.ruhr-uni-bochum.de

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Automatisch wlank] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
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
    belkin.e89:      Infra, <MAC 'belkin.e89' [AC4]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    *madu:           Infra, <MAC 'madu' [AC1]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 62 WPA2
    imoedh:          Infra, <MAC 'imoedh' [AN3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    RUB:             Infra, <MAC 'RUB' [AN4]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 45 WPA2
    internetsarah:   Infra, <MAC 'internetsarah' [AN5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Ankh Morpork:    Infra, <MAC 'Ankh Morpork' [AN6]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    DrosteWL:        Infra, <MAC 'DrosteWL' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    dlink:           Infra, <MAC 'dlink' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45
    make-your-own-wifi: Infra, <MAC 'make-your-own-wifi' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2

  IPv4 Settings:
    Address:         10.0.40.67
    Prefix:          23 (255.255.254.0)
    Gateway:         10.0.40.1

    DNS:             10.0.0.130
    DNS:             10.0.0.10

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
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

[[/etc/NetworkManager/system-connections/Automatisch wlanK]] (600 root)
[connection] id=Automatisch wlanK | type=802-11-wireless
[802-11-wireless] ssid=Madu | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Art]] (600 root)
[connection] id=Art | type=802-11-wireless
[802-11-wireless] ssid=Art | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Automatisch DrosteWL]] (600 root)
[connection] id=Automatisch DrosteWL | type=802-11-wireless
[802-11-wireless] ssid=DrosteWL | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Automatisch wlank]] (600 root)
[connection] id=Automatisch madu | type=802-11-wireless | permissions=user:madu:; | autoconnect=false
[802-11-wireless] ssid=madu | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Automatisch dlink]] (600 root)
[connection] id=Automatisch dlink | type=802-11-wireless
[802-11-wireless] ssid=dlink | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Automatisch WLAN]] (600 root)
[connection] id=Automatisch WLAN | type=802-11-wireless
[802-11-wireless] ssid=WLAN | bssid=<MAC address> | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

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
          Current Frequency:2.457 GHz (Channel 10)

##### iwlist scan #######################

Channel occupancy:

      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.467 GHz (Channel 12)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'wlank' [AC1]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"wlank"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000018f74fd70b
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 02 - Address: <MAC 'DrosteWL' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"DrosteWL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000525b9068dd
                    Extra: Last beacon: 6532ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'make-your-own-wifi' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"make-your-own-wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000043e25219c
                    Extra: Last beacon: 19720ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'belkin.e89' [AC4]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"belkin.e89"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b9f672eb1
                    Extra: Last beacon: 84ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     CC4D1BA11C1EF73A6ABDE53
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
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
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     C2D0F3DFCA289585C100E36
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[iwlwifi]
11n_disable: 1
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1

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
options iwlwifi 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1083 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0091 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 1234.777318] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:91:eb:d3:08:00 SRC=10.0.40.30 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=29979 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1235.802722] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:f0:bf:97:11:9a:6b:08:00 SRC=10.0.41.155 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16600 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1236.837844] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:c4:54:44:83:1e:59:08:00 SRC=10.0.41.170 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28302 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1237.955749] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:ec:55:f9:c7:53:56:08:00 SRC=10.0.41.127 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=2105 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1238.776994] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:ec:55:f9:c7:53:56:08:00 SRC=10.0.41.127 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=2188 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1239.803755] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:ec:55:f9:c7:53:56:08:00 SRC=10.0.41.127 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=2230 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1240.830610] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:2c:27:d7:c2:e8:e2:08:00 SRC=10.0.40.243 DST=10.0.41.255 LEN=153 TOS=0x00 PREC=0x00 TTL=128 ID=4506 PROTO=UDP SPT=17500 DPT=17500 LEN=133 
[ 1241.851828] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:ec:55:f9:c7:53:56:08:00 SRC=10.0.41.127 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=2501 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1242.774547] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:d8:9d:67:c9:d7:40:08:00 SRC=10.0.40.86 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=29169 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1243.799582] IN-world:IN=wlan0 OUT= MAC=01:00:5e:00:00:01:10:fe:ed:45:89:6c:08:00 SRC=10.0.41.249 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1244.825088] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:f5:d9:41:69:08:00 SRC=10.0.40.210 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=7110 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1245.850342] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:f0:4d:a2:5c:10:4e:08:00 SRC=10.0.41.236 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=29935 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1247.090767] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:f5:d9:41:69:08:00 SRC=10.0.40.210 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=7129 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1247.801089] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:f5:d9:41:69:08:00 SRC=10.0.40.210 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=7236 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1248.829957] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:20:89:84:fd:0a:02:08:00 SRC=10.0.40.127 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=23881 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1249.848954] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:ec:55:f9:c7:53:56:08:00 SRC=10.0.41.127 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=2579 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1250.792217] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:88:ae:1d:da:81:7f:08:00 SRC=10.0.41.245 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18341 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1251.797032] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:c8:60:00:06:f1:19:08:00 SRC=10.0.41.161 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=20453 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1253.232448] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:c8:60:00:06:f1:19:08:00 SRC=10.0.41.161 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=20455 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1253.848599] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:54:76:da:81:08:00 SRC=10.0.41.42 DST=255.255.255.255 LEN=68 TOS=0x00 PREC=0x00 TTL=128 ID=1934 PROTO=UDP SPT=52234 DPT=1947 LEN=48 
[ 1255.080426] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:91:eb:d3:08:00 SRC=10.0.40.30 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30103 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1255.799945] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:91:eb:d3:08:00 SRC=10.0.40.30 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30104 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1256.802579] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:7e:8a:c9:08:00 SRC=10.0.41.119 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=19284 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1257.793180] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:ec:55:f9:c7:53:56:08:00 SRC=10.0.41.127 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=2848 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1258.871993] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:b8:ac:6f:51:65:d4:08:00 SRC=10.0.40.245 DST=255.255.255.255 LEN=143 TOS=0x00 PREC=0x00 TTL=128 ID=173 PROTO=UDP SPT=17500 DPT=17500 LEN=123 
[ 1259.796007] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:e8:40:f2:c7:a1:d4:08:00 SRC=10.0.41.149 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=20921 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1260.922019] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:91:eb:d3:08:00 SRC=10.0.40.30 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30125 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1261.958442] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:f0:de:f1:d3:28:07:08:00 SRC=10.0.40.104 DST=255.255.255.255 LEN=164 TOS=0x00 PREC=0x00 TTL=64 ID=5090 DF PROTO=UDP SPT=17500 DPT=17500 LEN=144 
[ 1263.286443] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:30:85:a9:71:1a:52:08:00 SRC=10.0.41.35 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=27900 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1263.934891] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:30:85:a9:71:1a:52:08:00 SRC=10.0.41.35 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=27921 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1265.025107] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:91:eb:d3:08:00 SRC=10.0.40.30 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30167 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1266.052502] IN-world:IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:d4:3d:7e:1f:fb:d0:08:00 SRC=10.0.40.197 DST=224.0.0.251 LEN=85 TOS=0x00 PREC=0x00 TTL=255 ID=23316 PROTO=UDP SPT=5353 DPT=5353 LEN=65 
[ 1266.868577] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:f0:4d:a2:5c:10:4e:08:00 SRC=10.0.41.236 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30771 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1267.997608] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:26:6c:4c:c5:91:08:00 SRC=10.0.41.47 DST=10.0.41.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=24079 PROTO=UDP SPT=138 DPT=138 LEN=209 
[ 1268.818070] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:f0:4d:a2:5c:10:4e:08:00 SRC=10.0.41.236 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=31316 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1270.047042] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:91:eb:d3:08:00 SRC=10.0.40.30 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30187 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1270.867221] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:91:eb:d3:08:00 SRC=10.0.40.30 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30200 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1271.995041] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:20:1a:06:35:0f:6f:08:00 SRC=10.0.41.10 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=23798 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1272.918925] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:25:64:9c:58:5a:08:00 SRC=10.0.40.150 DST=255.255.255.255 LEN=161 TOS=0x00 PREC=0x00 TTL=128 ID=19086 PROTO=UDP SPT=17500 DPT=17500 LEN=141 
[ 1274.045602] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:80:c1:6e:55:de:69:08:00 SRC=10.0.40.241 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18524 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1275.173520] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:91:eb:d3:08:00 SRC=10.0.40.30 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30225 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1275.892673] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:91:eb:d3:08:00 SRC=10.0.40.30 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30247 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1278.659270] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:68:6b:a5:ae:08:00 SRC=10.0.40.142 DST=10.0.41.255 LEN=72 TOS=0x00 PREC=0x00 TTL=128 ID=21448 PROTO=UDP SPT=57621 DPT=57621 LEN=52 
[ 1279.481162] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:20:89:84:ea:3a:61:08:00 SRC=10.0.40.199 DST=255.255.255.255 LEN=136 TOS=0x00 PREC=0x00 TTL=128 ID=14239 PROTO=UDP SPT=49439 DPT=1228 LEN=116 
[ 1280.181269] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:91:eb:d3:08:00 SRC=10.0.40.30 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30255 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1280.510277] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:3c:07:71:61:e7:57:08:00 SRC=10.0.40.179 DST=255.255.255.255 LEN=142 TOS=0x00 PREC=0x00 TTL=128 ID=16859 PROTO=UDP SPT=17500 DPT=17500 LEN=122 
[ 1281.017500] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:91:eb:d3:08:00 SRC=10.0.40.30 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30267 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1282.247830] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:fc:aa:e7:08:00 SRC=10.0.41.248 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=4743 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1282.862760] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:32:de:65:f0:08:00 SRC=10.0.40.43 DST=10.0.41.255 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=63637 PROTO=UDP SPT=54750 DPT=8612 LEN=24 
[ 1283.990748] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:88:ae:1d:da:81:7f:08:00 SRC=10.0.41.245 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18944 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1285.323768] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:66:58:ef:b8:08:00 SRC=10.0.41.69 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=7877 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1286.042761] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:fc:aa:e7:08:00 SRC=10.0.41.248 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=4748 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1286.861662] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:91:eb:d3:08:00 SRC=10.0.40.30 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30302 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1287.886876] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:f4:6d:04:94:9b:6c:08:00 SRC=10.0.41.88 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30987 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1289.431722] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:b8:ac:6f:51:65:d4:08:00 SRC=10.0.40.245 DST=255.255.255.255 LEN=143 TOS=0x00 PREC=0x00 TTL=128 ID=236 PROTO=UDP SPT=17500 DPT=17500 LEN=123 
[ 1289.937193] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:32:de:65:f0:08:00 SRC=10.0.40.43 DST=10.0.41.255 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=1952 PROTO=UDP SPT=60590 DPT=8612 LEN=24 
[ 1291.176143] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:91:eb:d3:08:00 SRC=10.0.40.30 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30328 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1291.899153] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:91:eb:d3:08:00 SRC=10.0.40.30 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30329 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1293.015280] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:dc:0e:a1:f0:d4:ad:08:00 SRC=10.0.40.191 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=25873 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1294.038585] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:dc:0e:a1:f0:d4:ad:08:00 SRC=10.0.40.191 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=25947 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1294.858791] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:dc:0e:a1:f0:d4:ad:08:00 SRC=10.0.40.191 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=26009 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1295.884626] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:20:6a:8a:00:82:3f:08:00 SRC=10.0.40.192 DST=255.255.255.255 LEN=143 TOS=0x00 PREC=0x00 TTL=128 ID=16184 PROTO=UDP SPT=17500 DPT=17500 LEN=123 
[ 1297.012913] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:91:eb:d3:08:00 SRC=10.0.40.30 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30368 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1298.652596] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:f0:bf:97:11:9a:6b:08:00 SRC=10.0.41.155 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18105 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1298.960417] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:20:1a:06:a0:ae:19:08:00 SRC=10.0.41.17 DST=255.255.255.255 LEN=132 TOS=0x00 PREC=0x00 TTL=64 ID=25589 DF PROTO=UDP SPT=17500 DPT=17500 LEN=112 
[ 1300.087760] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:f0:bf:97:11:9a:6b:08:00 SRC=10.0.41.155 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18145 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1301.118242] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:f4:6d:04:94:9b:6c:08:00 SRC=10.0.41.88 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=31021 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1301.933300] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:f4:6d:04:94:9b:6c:08:00 SRC=10.0.41.88 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=31024 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1302.856145] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:20:1a:06:35:0f:6f:08:00 SRC=10.0.41.10 DST=10.0.41.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=9083 PROTO=UDP SPT=137 DPT=137 LEN=76 
[ 1303.985136] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:90:f6:52:ae:4a:0c:08:00 SRC=10.0.40.106 DST=10.0.41.255 LEN=237 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=217 
[ 1305.111756] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:20:1a:06:35:0f:6f:08:00 SRC=10.0.41.10 DST=10.0.41.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=9089 PROTO=UDP SPT=137 DPT=137 LEN=76 
[ 1306.278547] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:e8:9a:8f:ea:65:b3:08:00 SRC=10.0.41.226 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=10678 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1306.957140] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:e8:9a:8f:ea:65:b3:08:00 SRC=10.0.41.226 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=10679 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1307.882505] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:90:f5:d9:41:69:08:00 SRC=10.0.40.210 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=8226 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1308.913953] IN-world:IN=wlan0 OUT= MAC=01:00:5e:00:00:01:50:7e:5d:17:67:a9:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=45398 PROTO=2 
[ 1309.964462] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:e8:9a:8f:ea:65:b3:08:00 SRC=10.0.41.226 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=10682 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1310.861646] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:19:66:58:ef:b8:08:00 SRC=10.0.41.69 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=10373 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1312.223210] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:91:eb:d3:08:00 SRC=10.0.40.30 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30470 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1313.114043] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:26:9e:8b:11:14:08:00 SRC=10.0.40.212 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=13246 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1313.941736] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:e8:40:f2:c7:a1:d4:08:00 SRC=10.0.41.149 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=22667 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1315.058685] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:20:6a:8a:00:82:3f:08:00 SRC=10.0.40.192 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16507 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1315.877053] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:20:6a:8a:00:82:3f:08:00 SRC=10.0.40.192 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16509 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1317.107351] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:20:6a:8a:00:82:3f:08:00 SRC=10.0.40.192 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16522 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1318.132688] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:7e:8a:c9:08:00 SRC=10.0.41.119 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=19444 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1318.868725] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:68:6b:a5:ae:08:00 SRC=10.0.40.142 DST=10.0.41.255 LEN=72 TOS=0x00 PREC=0x00 TTL=128 ID=21475 PROTO=UDP SPT=57621 DPT=57621 LEN=52 
[ 1319.916865] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:5c:51:4f:62:b6:6e:08:00 SRC=10.0.40.239 DST=255.255.255.255 LEN=153 TOS=0x00 PREC=0x00 TTL=128 ID=14313 PROTO=UDP SPT=17500 DPT=17500 LEN=133 
[ 1320.902171] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:91:eb:d3:08:00 SRC=10.0.40.30 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30514 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1322.028849] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:f0:bf:97:11:9a:6b:08:00 SRC=10.0.41.155 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18896 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1323.054136] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:26:9e:9f:2b:8d:08:00 SRC=10.0.40.93 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30747 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1323.874889] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:26:9e:9f:2b:8d:08:00 SRC=10.0.40.93 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30783 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1325.412272] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:3c:97:0e:d2:b3:5c:08:00 SRC=10.0.41.158 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18587 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1326.130551] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:10:dd:b1:e0:66:f5:08:00 SRC=10.0.40.60 DST=255.255.255.255 LEN=164 TOS=0x00 PREC=0x00 TTL=64 ID=10564 PROTO=UDP SPT=17500 DPT=17500 LEN=144 
[ 1326.950179] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:3c:97:0e:d2:b3:5c:08:00 SRC=10.0.41.158 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18589 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1327.878961] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:bc:5f:f4:91:eb:d3:08:00 SRC=10.0.40.30 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30557 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1329.000708] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:ec:55:f9:c7:53:56:08:00 SRC=10.0.41.127 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4114 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1329.936224] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:ec:55:f9:c7:53:56:08:00 SRC=10.0.41.127 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4128 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1330.948651] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1d:09:55:98:68:08:00 SRC=10.0.40.160 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=12999 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1331.888055] IN-world:IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:ec:55:f9:c7:53:56:08:00 SRC=10.0.41.127 DST=10.0.41.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4377 PROTO=UDP SPT=137 DPT=137 LEN=58 

########## wireless info END ############


```

---

### Post by papibe on 2014-10-21
Hi madm. Welcome to the forum ):P

I would be more concern about transfer speeds. Do you have another machine in the network, preferable wired, so you can test transfer speeds?

For instance, if you have another Linux machine, you could do a 'rsync' using the '--progress'  option so you can measure the current transfer speed. 

Let us know if you need more directions for accomplish that.
Regards.

---

### Post by madm on 2014-10-21
Hey thanks for your answer!
I am new on Ubuntu, could you give me an example with rsync? (but i dont got another linux-machine in my network)
My wired connection is pretty good and didnt changed since i connected the router.

So right now im connected via wlan and the speed is good, but the connection is just about 60% although my router is standing right next to my laptop

---

### Post by jeremy31 on 2014-10-21
You have deleted part of iwlwifi.conf
```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```
And paste this in, replace everything in that file
```
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=8
```

The 11n_disable=8 should improve the speed

---

### Post by papibe on 2014-10-21
If you have a good speed (say N speeds instead of G speeds), I wouldn't worry about the signal level.

Nevertheless, do you have a NAS or another computer in the house? Something that can share a folder over the network?

Regards.

---

### Post by madm on 2014-10-21
Hey, yes the problem is that i want to use the laptop in another room. Right sitting next to the router is no problem. I just got ~65%, but the speed is fine. But when I move to like 2 meters away from the router it is ~30% or disconnected. I just have this problem with my laptop, with other devices - for example mobilephone - the connection is very good. I had yesterday the same problem with the wlan-connection in another network.  I dont think i can share a a folder over the network, because its the network of my university. But i had the same problem in another network, so i think its not a network/router-issue. I could disconnect my router from the university-network/internet and create a network with my router and a windows & ubuntu PC   edit:// @jeremy31: i just saw your post.. thx! i changed the file und rebooted.. but it didnt help :(

---

### Post by jeremy31 on 2014-10-21
If it is that bad, I wonder if your antenna wires are still connected to the card, I hope your Dell model is more user friendly when it comes to accessing the wifi card.  I had to remove Dvd, bunch of screws, and even the keyboard......never again

---

