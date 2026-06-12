---
title: "Wireless keeps disconnecting"
date: 2015-06-07
forum: Networking &amp; Wireless
---

### Post by dcentore on 2015-06-07
Hello,

My wireless connection keeps disconnecting for a second or so, and then reconnecting.

Every time this occurs, my dmesg looks like this:

```


[ 8384.767108] wlan0: deauthenticating from c2:9f:db:1f:b9:91 by local choice (reason=3)
[ 8384.770198] cfg80211: Calling CRDA to update world regulatory domain
[ 8384.772255] cfg80211: World regulatory domain updated:
[ 8384.772257] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 8384.772258] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8384.772259] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8384.772260] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 8384.772261] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8384.772262] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8388.407855] wlan0: authenticate with c2:9f:db:1f:b9:91
[ 8388.409912] wlan0: send auth to c2:9f:db:1f:b9:91 (try 1/3)
[ 8388.513469] wlan0: send auth to c2:9f:db:1f:b9:91 (try 2/3)
[ 8388.564333] wlan0: authenticated
[ 8388.568540] wlan0: associate with c2:9f:db:1f:b9:91 (try 1/3)
[ 8388.572365] wlan0: RX AssocResp from c2:9f:db:1f:b9:91 (capab=0x431 status=0 aid=4)
[ 8388.575429] wlan0: associated

```

Here is the output from the wireless script:

```


########## wireless info START ##########


Report from: 07 Jun 2015 21:19 EDT -0400


Booted last: 07 Jun 2015 18:56 EDT -0400


Script from: 21 May 2015 09:10 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-53-generic #89-Ubuntu SMP Wed May 20 10:34:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro


##### desktop ###########################


Ubuntu


##### lspci #############################


07:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
    Kernel driver in use: iwlwifi


0d:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:fa72]
    Kernel driver in use: alx


##### lsusb #############################


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04f2:b41a Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 8087:07dc Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


iwlmvm                189852  0 
mac80211              630728  1 iwlmvm
iwlwifi               169932  1 iwlmvm
mxm_wmi                13021  1 nouveau
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  3 toshiba_acpi,mxm_wmi,nouveau


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
          Interrupt:19 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.11.135  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: 2002:4575:cf82:0:a426:b590:94d6:4a63/64 Scope:Global
          inet6 addr: 2002:4575:cf82:0:ae7b:a1ff:fe9a:f67d/64 Scope:Global
          inet6 addr: fe80::ae7b:a1ff:fe9a:f67d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1673284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:665377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2413099887 (2.4 GB)  TX bytes:71045381 (71.0 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"HAL9001"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'HAL9001' [AC1]>   
          Bit Rate=39 Mb/s   Tx-Power=22 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:60   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.11.1    0.0.0.0         UG    0      0        0 wlan0
192.168.11.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root      1152     1  0 18:56 ?        00:00:05 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


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


- Device: wlan0  [HAL9001] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           39 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    ldar_EXT:        Infra, <MAC 'ldar_EXT' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    F68F32:          Infra, <MAC 'F68F32' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Livigs:          Infra, <MAC 'Livigs' [AC6]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 35 WPA2
    ldar:            Infra, <MAC 'ldar' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    optimumwifi:     Infra, <MAC 'optimumwifi' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45
    Livigs-guest:    Infra, <MAC 'Livigs-guest' [AC5]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 39
    optimumwifi:     Infra, <MAC 'optimumwifi' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20
    HP-Print-62-Photosmart 7520: Infra, <MAC 'HP-Print-62-Photosmart 7520' [AC9]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 19
    KingsburyWireless: Infra, <MAC 'KingsburyWireless' [AN9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    CableWiFi:       Infra, <MAC 'CableWiFi' [AN10]>, Freq 5805 MHz, Rate 54 Mb/s, Strength 0
    *HAL9001:        Infra, <MAC 'HAL9001' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 68 WPA WPA2


  IPv4 Settings:
    Address:         192.168.11.135
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.11.1


    DNS:             167.206.10.178
    DNS:             167.206.10.179
    DNS:             192.168.11.1


  IPv6 Settings:
    Address:         2002:4575:cf82:0:a426:b590:94d6:4a63
    Prefix:          64
    Gateway:         fe80::c2c1:c0ff:fe38:8652


    Address:         2002:4575:cf82:0:ae7b:a1ff:fe9a:f67d
    Prefix:          64
    Gateway:         fe80::c2c1:c0ff:fe38:8652


    Address:         fe80::ae7b:a1ff:fe9a:f67d
    Prefix:          64
    Gateway:         fe80::c2c1:c0ff:fe38:8652


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
managed=true


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/centek]] (600 root)
[connection] id=centek | type=802-11-wireless
[802-11-wireless] ssid=centek | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Chuma]] (600 root)
[connection] id=Chuma | type=802-11-wireless
[802-11-wireless] ssid=Chuma | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/rpi_wpa2]] (600 root)
[ipv6] method=auto
[connection] id=rpi_wpa2 | type=802-11-wireless | permissions=user:drdanielfc:;
[802-11-wireless] ssid=rpi_wpa2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/HAL9001]] (600 root)
[connection] id=HAL9001 | type=802-11-wireless
[802-11-wireless] ssid=HAL9001 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Holiday Inn5]] (600 root)
[connection] id=Holiday Inn5 | type=802-11-wireless
[802-11-wireless] ssid=Holiday Inn5 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/rpi_netreg]] (600 root)
[connection] id=rpi_netreg | type=802-11-wireless
[802-11-wireless] ssid=rpi_netreg | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.452 GHz (Channel 9)
      2   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'HAL9001' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"HAL9001"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f4a259b155
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ldar_EXT' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"ldar_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000fe7dda6d5
                    Extra: Last beacon: 4508ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'ldar' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"ldar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000febc219e7
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'optimumwifi' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:off
                    ESSID:"optimumwifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000febc2f918
                    Extra: Last beacon: 76ms ago
          Cell 05 - Address: <MAC 'Livigs-guest' [AC5]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"Livigs-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000fd0a8f05f3
                    Extra: Last beacon: 76ms ago
          Cell 06 - Address: <MAC 'Livigs' [AC6]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Livigs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000fd0a8f0e30
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'F68F32' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"F68F32"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001bf96dbfee
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'optimumwifi' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"optimumwifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001bf96dcdec
                    Extra: Last beacon: 76ms ago
          Cell 09 - Address: <MAC 'HP-Print-62-Photosmart 7520' [AC9]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-62-Photosmart 7520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000fd09ab4a6c
                    Extra: Last beacon: 4312ms ago


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.13.0-53-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     2ED88DF9FE06B5CF295C51A
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-53-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9A:AC:90:0A:BD:02:20:FB:93:C8:BE:10:F2:0D:69:73:DA:B8:29:F5
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.13.0-53-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     BF4F6788BCD3848D1F2F4BF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-53-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9A:AC:90:0A:BD:02:20:FB:93:C8:BE:10:F2:0D:69:73:DA:B8:29:F5
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.13.0-53-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     A45BAACCAD263355629DB7A
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-53-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9A:AC:90:0A:BD:02:20:FB:93:C8:BE:10:F2:0D:69:73:DA:B8:29:F5
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
filename:       /lib/modules/3.13.0-53-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     22618C9A8AD682CBE73FFF2
depends:        
intree:         Y
vermagic:       3.13.0-53-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9A:AC:90:0A:BD:02:20:FB:93:C8:BE:10:F2:0D:69:73:DA:B8:29:F5
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


[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


##### rc.local ##########################


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
# PCI device 0x1969:0x1091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 8230.637458] wlan0: associate with <MAC 'HAL9001' [AC1]> (try 1/3)
[ 8230.641282] wlan0: RX AssocResp from <MAC 'HAL9001' [AC1]> (capab=0x431 status=0 aid=4)
[ 8230.644335] wlan0: associated
[ 8242.105628] wlan0: deauthenticating from <MAC 'HAL9001' [AC1]> by local choice (reason=3)
[ 8251.093466] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[ 8251.106540] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8258.395157] wlan0: authenticate with <MAC 'HAL9001' [AC1]>
[ 8258.396972] wlan0: send auth to <MAC 'HAL9001' [AC1]> (try 1/3)
[ 8258.410140] wlan0: authenticated
[ 8258.411807] wlan0: associate with <MAC 'HAL9001' [AC1]> (try 1/3)
[ 8258.415516] wlan0: RX AssocResp from <MAC 'HAL9001' [AC1]> (capab=0x431 status=0 aid=4)
[ 8258.418363] wlan0: associated
[ 8258.418407] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8258.429319] wlan0: deauthenticating from <MAC 'HAL9001' [AC1]> by local choice (reason=2)
[ 8258.432779] wlan0: authenticate with <MAC 'HAL9001' [AC1]>
[ 8258.434496] wlan0: send auth to <MAC 'HAL9001' [AC1]> (try 1/3)
[ 8258.436327] wlan0: authenticated
[ 8258.439820] wlan0: associate with <MAC 'HAL9001' [AC1]> (try 1/3)
[ 8258.443539] wlan0: RX AssocResp from <MAC 'HAL9001' [AC1]> (capab=0x431 status=0 aid=4)
[ 8258.446610] wlan0: associated
[ 8291.189718] wlan0: deauthenticating from <MAC 'HAL9001' [AC1]> by local choice (reason=3)
[ 8294.826606] wlan0: authenticate with <MAC 'HAL9001' [AC1]>
[ 8294.828535] wlan0: send auth to <MAC 'HAL9001' [AC1]> (try 1/3)
[ 8294.830393] wlan0: authenticated
[ 8294.833091] wlan0: associate with <MAC 'HAL9001' [AC1]> (try 1/3)
[ 8294.836816] wlan0: RX AssocResp from <MAC 'HAL9001' [AC1]> (capab=0x431 status=0 aid=4)
[ 8294.847244] wlan0: associated
[ 8384.767108] wlan0: deauthenticating from <MAC 'HAL9001' [AC1]> by local choice (reason=3)
[ 8388.407855] wlan0: authenticate with <MAC 'HAL9001' [AC1]>
[ 8388.409912] wlan0: send auth to <MAC 'HAL9001' [AC1]> (try 1/3)
[ 8388.513469] wlan0: send auth to <MAC 'HAL9001' [AC1]> (try 2/3)
[ 8388.564333] wlan0: authenticated
[ 8388.568540] wlan0: associate with <MAC 'HAL9001' [AC1]> (try 1/3)
[ 8388.572365] wlan0: RX AssocResp from <MAC 'HAL9001' [AC1]> (capab=0x431 status=0 aid=4)
[ 8388.575429] wlan0: associated
[ 8485.847989] wlan0: deauthenticating from <MAC 'HAL9001' [AC1]> by local choice (reason=3)
[ 8489.491267] wlan0: authenticate with <MAC 'HAL9001' [AC1]>
[ 8489.492982] wlan0: send auth to <MAC 'HAL9001' [AC1]> (try 1/3)
[ 8489.598776] wlan0: send auth to <MAC 'HAL9001' [AC1]> (try 2/3)
[ 8489.612935] wlan0: authenticated
[ 8489.613930] wlan0: associate with <MAC 'HAL9001' [AC1]> (try 1/3)
[ 8489.617796] wlan0: RX AssocResp from <MAC 'HAL9001' [AC1]> (capab=0x431 status=0 aid=4)
[ 8489.620759] wlan0: associated
[ 8592.300354] wlan0: deauthenticating from <MAC 'HAL9001' [AC1]> by local choice (reason=3)
[ 8595.857395] wlan0: authenticate with <MAC 'HAL9001' [AC1]>
[ 8595.859357] wlan0: send auth to <MAC 'HAL9001' [AC1]> (try 1/3)
[ 8595.861257] wlan0: authenticated
[ 8595.863630] wlan0: associate with <MAC 'HAL9001' [AC1]> (try 1/3)
[ 8595.867507] wlan0: RX AssocResp from <MAC 'HAL9001' [AC1]> (capab=0x431 status=0 aid=4)
[ 8595.870523] wlan0: associated


########## wireless info END ############



```

I have found several similar threads referencing the "deauthenticating from c2:9f:db:1f:b9:91 by local choice (reason=3)" problem, but none of the suggested remedies worked for me.

---

