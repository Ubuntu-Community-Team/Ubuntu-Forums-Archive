---
title: "Ubuntu 15.04 Wireless Disconnects"
date: 2015-06-17
forum: Networking &amp; Wireless
---

### Post by TheVolamoot on 2015-06-17
After a recent update pushed to the repos, my wireless randomly disconnects and only a reboot will fix it (sometimes not for very long such as only being up for 10 mins.) I am getting very very impatient and being interrupted from work every 15 mins or so to reboot is just plain annoying. I'll be glad to help in any way possible to solve this issue.

---

### Post by wildmanne39 on 2015-06-17
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by TheVolamoot on 2015-06-17
The output of the script is as follows.
```


########## wireless info START ##########


Report from: 17 Jun 2015 20:35 CDT -0500


Booted last: 17 Jun 2015 14:26 CDT -0500


Script from: 21 May 2015 09:10 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 15.04
Release:	15.04
Codename:	vivid


##### kernel ############################


Linux 3.19.0-21-generic #21-Ubuntu SMP Sun Jun 14 18:31:11 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, vesafb.invalid=1, splash, quiet, nopat, vt.handoff=7


##### desktop ###########################


GNOME


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
	Subsystem: Lenovo Device [17aa:2153]
	Kernel driver in use: e1000e


03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)
	Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1311]
	Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 002 Device 003: ID 1004:631c LG Electronics, Inc. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


iwldvm                237568  0 
mac80211              724992  1 iwldvm
iwlwifi               196608  1 iwldvm
cfg80211              540672  3 iwlwifi,mac80211,iwldvm
mxm_wmi                16384  1 nouveau
wmi                    20480  3 toshiba_acpi,mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7677 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8012 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4577803 (4.5 MB)  TX bytes:1557219 (1.5 MB)
          Interrupt:20 Memory:f8500000-f8520000 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:115078 errors:0 dropped:6608 overruns:0 frame:0
          TX packets:22224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:153043251 (153.0 MB)  TX bytes:3442354 (3.4 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       694     1  1 19:27 ?        00:00:57 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Advanced-N 6200 (2x2 AGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 3.19.0-21-generic
GENERAL.FIRMWARE-VERSION:               9.221.4.1 build 25532
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{5}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   09e276f6-15b5-4aaf-a4af-7d2cdb44e0d0 | LoudCedar
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82577LM Gigabit Network Connection
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 2.3.2-k
GENERAL.FIRMWARE-VERSION:               0.12-1
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off


SSID                BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
--                  <MAC '--' [AN1]>  Infra  9     2452 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
LoudCedar           <MAC 'LoudCedar' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA2       no        
CenturyLink6840     <MAC 'CenturyLink6840' [AN3]>  Infra  6     2437 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2  no        
Cisco_EC88DDA3      <MAC 'Cisco_EC88DDA3' [AN4]>  Infra  44    5220 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
CenturyLink2841     <MAC 'CenturyLink2841' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  30      &#9602;___  WPA2       no        
MyCharterWiFifd-2G  <MAC 'MyCharterWiFifd-2G' [AN6]>  Infra  10    2457 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2       no        
MyCharterWiFi73-2G  <MAC 'MyCharterWiFi73-2G' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  25      &#9602;___  WPA2       no        
NETGEAR58           <MAC 'NETGEAR58' [AC5]>  Infra  8     2447 MHz  54 Mbit/s  30      &#9602;___  WPA2       no        
Oynes               <MAC 'Oynes' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  no        


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


[[/etc/NetworkManager/system-connections/k0rsl]] (600 root)
[connection] id=k0rsl | type=wifi
[wifi] ssid=k0rsl | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/k0rsl_Mobile]] (600 root)
[connection] id=k0rsl_Mobile | type=wifi
[wifi] ssid=k0rsl_Mobile | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/LoudCedar]] (600 root)
[connection] id=LoudCedar | type=wifi
[wifi] ssid=LoudCedar | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Target Guest Wi-Fi]] (600 root)
[connection] id=Target Guest Wi-Fi | type=wifi
[wifi] ssid=Target Guest Wi-Fi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Linksys09925-guest]] (600 root)
[connection] id=Linksys09925-guest | type=wifi
[wifi] ssid=Linksys09925-guest | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Library]] (600 root)
[connection] id=Library | type=wifi
[wifi] ssid=Library | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


Region: America/Chicago (based on set time zone)


country 00: DFS-UNSET
	(2402 - 2472 @ 40), (3, 20), (N/A)
	(2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
	(5735 - 5835 @ 40), (3, 20), (N/A), NO-IR


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


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'k0rsl' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"k0rsl"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000a069fb29
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'CenturyLink2841' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink2841"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000014513b2f001
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Oynes' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Oynes"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000d75434a230b
                    Extra: Last beacon: 2736ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'LoudCedar' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"LoudCedar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000b75629a5bc5
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'NETGEAR58' [AC5]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR58"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000bcb1eff0ca2
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwldvm]
filename:       /lib/modules/3.19.0-21-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     E3CBEE01463DF37AB9C5AB1
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        33:3A:84:CC:97:05:DD:B2:6E:1C:DC:E3:88:AF:CE:DC:2D:EF:F7:61
sig_hashalgo:   sha512
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)


[mac80211]
filename:       /lib/modules/3.19.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     88CC41451370601B0D885E4
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        33:3A:84:CC:97:05:DD:B2:6E:1C:DC:E3:88:AF:CE:DC:2D:EF:F7:61
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.19.0-21-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265D-10.ucode
firmware:       iwlwifi-7265-10.ucode
firmware:       iwlwifi-3165-10.ucode
firmware:       iwlwifi-3160-10.ucode
firmware:       iwlwifi-7260-10.ucode
firmware:       iwlwifi-8000-10.ucode
srcversion:     97E94F4448EBBA00BC45455
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        33:3A:84:CC:97:05:DD:B2:6E:1C:DC:E3:88:AF:CE:DC:2D:EF:F7:61
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)


[cfg80211]
filename:       /lib/modules/3.19.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E61EB836E1B33C2A2918485
depends:        
intree:         Y
vermagic:       3.19.0-21-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        33:3A:84:CC:97:05:DD:B2:6E:1C:DC:E3:88:AF:CE:DC:2D:EF:F7:61
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwldvm]
force_cam: Y


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
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1


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


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x10ea (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4239 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl8187)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[ 3496.296046] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 3496.296261] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1
[ 3496.511204] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 3496.511414] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1
[ 3561.592017] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 3561.592234] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1
[ 3561.806383] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 3561.806596] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1
[ 3657.883546] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 3657.883762] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1
[ 3658.097347] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 3658.097557] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1
[ 3712.914755] wlan0: authenticate with <MAC 'k0rsl' [AC1]>
[ 3712.945611] wlan0: send auth to <MAC 'k0rsl' [AC1]> (try 1/3)
[ 3712.948376] wlan0: authenticated
[ 3712.949804] wlan0: associate with <MAC 'k0rsl' [AC1]> (try 1/3)
[ 3712.953507] wlan0: RX AssocResp from <MAC 'k0rsl' [AC1]> (capab=0x411 status=0 aid=6)
[ 3712.955943] wlan0: associated
[ 3841.343498] wlan0: deauthenticated from <MAC 'k0rsl' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 3841.373490] wlan0: authenticate with <MAC 'k0rsl' [AC1]>
[ 3841.376022] wlan0: send auth to <MAC 'k0rsl' [AC1]> (try 1/3)
[ 3841.379184] wlan0: authenticated
[ 3841.381006] wlan0: associate with <MAC 'k0rsl' [AC1]> (try 1/3)
[ 3841.384675] wlan0: RX AssocResp from <MAC 'k0rsl' [AC1]> (capab=0x411 status=0 aid=2)
[ 3841.386964] wlan0: associated
[ 3886.711318] wlan0: deauthenticated from <MAC 'k0rsl' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 3886.738726] wlan0: authenticate with <MAC 'k0rsl' [AC1]>
[ 3886.741045] wlan0: send auth to <MAC 'k0rsl' [AC1]> (try 1/3)
[ 3886.743791] wlan0: authenticated
[ 3886.746022] wlan0: associate with <MAC 'k0rsl' [AC1]> (try 1/3)
[ 3886.749755] wlan0: RX AssocResp from <MAC 'k0rsl' [AC1]> (capab=0x411 status=0 aid=2)
[ 3886.752352] wlan0: associated
[ 3940.989993] wlan0: deauthenticated from <MAC 'k0rsl' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 3941.024467] wlan0: authenticate with <MAC 'k0rsl' [AC1]>
[ 3941.027212] wlan0: send auth to <MAC 'k0rsl' [AC1]> (try 1/3)
[ 3941.030037] wlan0: authenticated
[ 3941.032290] wlan0: associate with <MAC 'k0rsl' [AC1]> (try 1/3)
[ 3941.035966] wlan0: RX AssocResp from <MAC 'k0rsl' [AC1]> (capab=0x411 status=0 aid=2)
[ 3941.038728] wlan0: associated
[ 3996.339995] wlan0: deauthenticated from <MAC 'k0rsl' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)


########## wireless info END ############



```

---

### Post by TheVolamoot on 2015-06-18
I found that starting monitor mode with ```
sudo airmon-ng start wlan0
``` makes mon0 startup and able to connect just fine for a long period of time. However if I reboot I have to manually execute the command again. I also found that it was ```
wpa_supplicant
``` that updated right as my issues came up. Not sure if this will help solve any issues, but at least i have a semi temp solution.

---

### Post by wildmanne39 on 2015-06-18
Hi, anything to do with airmon-ng is not allowed on the forum, the best place to get help is at the aircrack or Kali forum!
Thread closed!
From the CoC.> Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

---

