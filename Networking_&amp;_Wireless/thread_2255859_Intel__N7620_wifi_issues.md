---
title: "Intel  N7620 wifi issues"
date: 2014-12-08
forum: Networking &amp; Wireless
---

### Post by mkaryakin1 on 2014-12-08
Hello.
I'm having lenovo Z710 laptop with intel N7620 wifi card. I've got fresh 14.04 installation and for the first few days everything was fine. But now speed drops dramatically after few minutes of usage or connection just freezes. I had similiar problems on Debian Jessie before, on Win 8 everything works fine. 

```

########## wireless info START ##########

Report from: 08 Dec 2014 11:55 MSK +0300

Booted last: 08 Dec 2014 11:10 MSK +0300

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:53:56 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 73)
    Subsystem: Intel Corporation Wireless-N 7260 [8086:4262]
    Kernel driver in use: iwlwifi

08:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 10)
    Subsystem: Qualcomm Atheros Device [1969:1091]
    Kernel driver in use: alx

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 8087:07dc Intel Corp. 
Bus 003 Device 004: ID 062a:4101 Creative Labs 
Bus 003 Device 003: ID 5986:0295 Acer, Inc 
Bus 003 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: ideapad_3g: Wireless WAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                189813  0 
mac80211              626557  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
mxm_wmi                13021  1 nouveau
ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop
wmi                    19177  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::56be:f7ff:fe61:a5cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

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
    Address:         192.168.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ASUS:            Infra, <MAC 'ASUS' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    mannet 20-78:    Infra, <MAC 'mannet 20-78' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    resurs:          Infra, <MAC 'resurs' [AN3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Dixy:            Infra, <MAC 'Dixy' [AC3]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 19 WPA2 Enterprise
    beeline-router:  Infra, <MAC 'beeline-router' [AN5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA
    UPVEL UR-315BN:  Infra, <MAC 'UPVEL UR-315BN' [AC4]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 20 WEP
    TP-LINK_A59C36:  Infra, <MAC 'TP-LINK_A59C36' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70
    Olga:            Infra, <MAC 'Olga' [AN8]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    mannet-21-201114:Infra, <MAC 'mannet-21-201114' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    52:              Infra, <MAC '52' [AN10]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Igors:           Infra, <MAC 'Igors' [AN11]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    city-asus:       Infra, <MAC 'city-asus' [AN12]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 19 WPA2
    XPEH BAM:        Infra, <MAC 'XPEH BAM' [AN13]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 19 WPA2
    TP-LINK_85672E:  Infra, <MAC 'TP-LINK_85672E' [AN14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    ASUS!:           Infra, <MAC 'ASUS!' [AN15]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2
    Rostelecom:      Infra, <MAC 'Rostelecom' [AC5]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 29 WPA

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

[[/etc/NetworkManager/system-connections/TP-LINK_A59C36]] (600 root)
[connection] id=TP-LINK_A59C36 | type=802-11-wireless
[802-11-wireless] ssid=TP-LINK_A59C36 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TP-LINK_A59C36 1]] (600 root)
[connection] id=TP-LINK_A59C36 1 | type=802-11-wireless
[802-11-wireless] ssid=TP-LINK_A59C36 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: Europe/Moscow (based on set time zone)

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

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'TP-LINK_A59C36' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_A59C36"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000009aefe1a8
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ASUS' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"ASUS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001297d6fb1b
                    Extra: Last beacon: 724ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Dixy' [AC3]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Dixy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006202472f6f2
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
          Cell 04 - Address: <MAC 'UPVEL UR-315BN' [AC4]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"UPVEL UR-315BN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000035b8a2907f5
                    Extra: Last beacon: 420ms ago
          Cell 05 - Address: <MAC 'Rostelecom' [AC5]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Rostelecom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000000a266c72
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'mannet 20-78' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"mannet 20-78"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000008ba0a673
                    Extra: Last beacon: 324ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'dlink' [AC7]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001cffbb168
                    Extra: Last beacon: 88ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     7AF85C9FBD17AD993F1CC33
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        35:72:8C:DB:88:AA:70:FD:D3:AC:D1:53:A3:7B:51:31:92:A4:7F:D8
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.13.0-40-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     123C230E7AC85A31E4CA28B
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        35:72:8C:DB:88:AA:70:FD:D3:AC:D1:53:A3:7B:51:31:92:A4:7F:D8
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     32519C773C87BE82120EF0D
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        35:72:8C:DB:88:AA:70:FD:D3:AC:D1:53:A3:7B:51:31:92:A4:7F:D8
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
filename:       /lib/modules/3.13.0-40-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        35:72:8C:DB:88:AA:70:FD:D3:AC:D1:53:A3:7B:51:31:92:A4:7F:D8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
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
# PCI device 0x1969:0x10a1 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b2 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    6.302901] wlan0: authenticate with <MAC address>
[    6.304920] wlan0: send auth to <MAC address> (try 1/3)
[    6.368971] wlan0: send auth to <MAC address> (try 2/3)
[    6.431854] wlan0: send auth to <MAC address> (try 3/3)
[    6.487308] wlan0: authentication with <MAC address> timed out
[    6.642367] wlan0: authenticate with <MAC 'TP-LINK_A59C36' [AC1]>
[    6.643839] wlan0: direct probe to <MAC 'TP-LINK_A59C36' [AC1]> (try 1/3)
[    6.845432] wlan0: direct probe to <MAC 'TP-LINK_A59C36' [AC1]> (try 2/3)
[    7.049339] wlan0: direct probe to <MAC 'TP-LINK_A59C36' [AC1]> (try 3/3)
[    7.252910] wlan0: authentication with <MAC 'TP-LINK_A59C36' [AC1]> timed out
[    7.358290] iwlwifi 0000:07:00.0: No association and the time event is over already...
[    9.099204] wlan0: Connection to AP <MAC address> lost
[    9.948654] wlan0: authenticate with <MAC 'TP-LINK_A59C36' [AC1]>
[    9.950206] wlan0: direct probe to <MAC 'TP-LINK_A59C36' [AC1]> (try 1/3)
[   10.152356] wlan0: direct probe to <MAC 'TP-LINK_A59C36' [AC1]> (try 2/3)
[   10.356028] wlan0: direct probe to <MAC 'TP-LINK_A59C36' [AC1]> (try 3/3)
[   10.559597] wlan0: authentication with <MAC 'TP-LINK_A59C36' [AC1]> timed out
[   35.047848] wlan0: authenticate with <MAC 'TP-LINK_A59C36' [AC1]>
[   35.048571] wlan0: direct probe to <MAC 'TP-LINK_A59C36' [AC1]> (try 1/3)
[   35.252211] wlan0: direct probe to <MAC 'TP-LINK_A59C36' [AC1]> (try 2/3)
[   35.456344] wlan0: direct probe to <MAC 'TP-LINK_A59C36' [AC1]> (try 3/3)
[   35.659903] wlan0: authentication with <MAC 'TP-LINK_A59C36' [AC1]> timed out
[   63.071456] wlan0: authenticate with <MAC 'TP-LINK_A59C36' [AC1]>
[   63.072191] wlan0: direct probe to <MAC 'TP-LINK_A59C36' [AC1]> (try 1/3)
[   63.274842] wlan0: direct probe to <MAC 'TP-LINK_A59C36' [AC1]> (try 2/3)
[   63.479012] wlan0: direct probe to <MAC 'TP-LINK_A59C36' [AC1]> (try 3/3)
[   63.682516] wlan0: authentication with <MAC 'TP-LINK_A59C36' [AC1]> timed out
[   91.105299] wlan0: authenticate with <MAC address>
[   91.106032] wlan0: send auth to <MAC address> (try 1/3)
[   91.185700] wlan0: send auth to <MAC address> (try 2/3)
[   91.246636] wlan0: send auth to <MAC address> (try 3/3)
[   91.324979] wlan0: authentication with <MAC address> timed out
[  118.922627] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S (repeated 2 times)
[  118.934891] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############


```

P.s.: i tried 11n_disable, first it seemed to work better, but after some time problem returned

---

