---
title: "Ralink RT2561/RT61 WiFi card authentication issue"
date: 2016-02-26
forum: Networking &amp; Wireless
---

### Post by safire on 2016-02-26
I can connect to APs without authentication. But when i try to connect AP protected by WPA/WPA2, the association with AP times out.

Long time before i have upgraded this PC to 15.10 it used to work fine. I have a similar problem on another PC with another wifi adapter. It worked fine under 12.10, but after upgrade to 14.04 LTS it got to the same 'association timed out' error.

Here is the wireless-info output:

```


########## wireless info START ##########

Report from: 26 Feb 2016 10:10 MSK +0300

Booted last: 26 Feb 2016 00:00 MSK +0300

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily

##### kernel ############################

Linux 4.2.0-30-generic #35-Ubuntu SMP Fri Feb 19 13:52:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
	Kernel driver in use: r8169

07:02.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
	Subsystem: ASUSTeK Computer Inc. Device [1043:837e]
	Kernel driver in use: rt61pci

##### lsusb #############################

Bus 002 Device 005: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 002 Device 004: ID 04f3:0103 Elan Microelectronics Corp. ActiveJet K-2024 Multimedia Keyboard
Bus 002 Device 003: ID 1b20:0501 MStar Semiconductor, Inc. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rt61pci                32768  0
rt2x00pci              16384  1 rt61pci
rt2x00mmio             16384  1 rt61pci
rt2x00lib              57344  3 rt61pci,rt2x00pci,rt2x00mmio
mac80211              733184  2 rt2x00lib,rt2x00pci
cfg80211              548864  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt61pci
crc_itu_t              16384  2 rt61pci,firewire_core

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF]>  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13769 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9545 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8213463 (8.2 MB)  TX bytes:3979415 (3.9 MB)

wlp7s2    Link encap:Ethernet  HWaddr <MAC 'wlp7s2' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp7s2    IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
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

root      7709     1  0 09:59 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (M4A785TD Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl_nic/rtl8168d-2.fw
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         39 (Device disconnected by user or client)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.7/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    no
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         wlp7s2
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT2561/RT61 802.11g PCI
GENERAL.DRIVER:                         rt61pci
GENERAL.DRIVER-VERSION:                 4.2.0-30-generic
GENERAL.FIRMWARE-VERSION:               0.8
GENERAL.HWADDR:                         <MAC 'wlp7s2' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:07:02.0/net/wlp7s2
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   68345eb1-ab7c-4510-9182-2cc7562cad8f | HiB0XW!F!

SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
HWF             <MAC 'HWF' [AC1]>  Infra  10    2457 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2  no        
MGTS_GPON_2070  <MAC 'MGTS_GPON_2070' [AC3]>  Infra  5     2432 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2       no        
DIR-615         <MAC 'DIR-615' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  --         no        
HiB0XW!F!       <MAC 'HiB0XW!F!' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA1       no        
--              <MAC '' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  --         no        
Onlime64        <MAC 'Onlime64' [AC6]>  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2       no        
Beeline_WiFi    <MAC 'Beeline_WiFi' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  --         no        

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

[[/etc/NetworkManager/system-connections/HiB0XW!F!]] (600 root)
[connection] id=HiB0XW!F! | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp7s2' [IF]> | mac-address-blacklist= | ssid=HiB0XW!F!
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Moscow (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

wlp7s2    14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)

wlp7s2    Scan completed :
          Cell 01 - Address: <MAC 'HWF' [AC1]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"HWF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ebea55edc
                    Extra: Last beacon: 424ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'DIR-615' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:off
                    ESSID:"DIR-615"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008cb4ba4836
                    Extra: Last beacon: 1008ms ago
          Cell 03 - Address: <MAC 'MGTS_GPON_2070' [AC3]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"MGTS_GPON_2070"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008cb2c97c0a
                    Extra: Last beacon: 756ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000960f0871d3
                    Extra: Last beacon: 29668ms ago
          Cell 05 - Address: <MAC 'Beeline_WiFi' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"Beeline_WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003a6b1d6483
                    Extra: Last beacon: 29644ms ago
          Cell 06 - Address: <MAC 'Onlime64' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Onlime64"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008cb2c1921c
                    Extra: Last beacon: 29628ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'HiB0XW!F!' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"HiB0XW!F!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000008a24f5ce
                    Extra: Last beacon: 692ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rt61pci]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7E76DAA1CD3464C02EEA47D
depends:        rt2x00lib,rt2x00mmio,rt2x00pci,eeprom_93cx6,crc-itu-t
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        EA:CD:95:F9:2B:6B:16:E6:02:12:45:08:8F:73:4C:91:6F:CE:43:B3
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00pci]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     F2A3F87D3DBCA573A6F6E05
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        EA:CD:95:F9:2B:6B:16:E6:02:12:45:08:8F:73:4C:91:6F:CE:43:B3
sig_hashalgo:   sha512

[rt2x00mmio]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     879F1B5CBAAA72A33F68B51
depends:        rt2x00lib
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        EA:CD:95:F9:2B:6B:16:E6:02:12:45:08:8F:73:4C:91:6F:CE:43:B3
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D31088D761A4CE666692F67
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        EA:CD:95:F9:2B:6B:16:E6:02:12:45:08:8F:73:4C:91:6F:CE:43:B3
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-30-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     292BCC26A10EA884DF6B5FF
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        EA:CD:95:F9:2B:6B:16:E6:02:12:45:08:8F:73:4C:91:6F:CE:43:B3
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

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
sig_key:        EA:CD:95:F9:2B:6B:16:E6:02:12:45:08:8F:73:4C:91:6F:CE:43:B3
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt61pci]
nohwcrypt: Y

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

[ 3581.798930] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 3582.003112] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 2/3)
[ 3582.207221] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 3/3)
[ 3582.411329] wlp7s2: association with <MAC 'HiB0XW!F!' [AC7]> timed out
[ 3652.759733] IPv6: ADDRCONF(NETDEV_UP): wlp7s2: link is not ready (repeated 3 times)
[ 3688.339869] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC7]>
[ 3688.355697] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 3688.360486] wlp7s2: authenticated
[ 3688.360751] rt61pci 0000:07:02.0 wlp7s2: disabling HT/VHT due to WEP/TKIP use
[ 3688.360757] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[ 3688.360761] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[ 3688.363235] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 3688.567339] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 2/3)
[ 3688.771386] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 3/3)
[ 3688.975553] wlp7s2: association with <MAC 'HiB0XW!F!' [AC7]> timed out
[ 3690.145144] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC7]>
[ 3690.164660] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 3690.166411] wlp7s2: authenticated
[ 3690.166568] rt61pci 0000:07:02.0 wlp7s2: disabling HT/VHT due to WEP/TKIP use
[ 3690.166572] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[ 3690.166575] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[ 3690.168168] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 3690.372259] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 2/3)
[ 3690.576396] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 3/3)
[ 3690.780493] wlp7s2: association with <MAC 'HiB0XW!F!' [AC7]> timed out
[ 3692.349892] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC7]>
[ 3692.365702] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 3692.367365] wlp7s2: authenticated
[ 3692.367511] rt61pci 0000:07:02.0 wlp7s2: disabling HT/VHT due to WEP/TKIP use
[ 3692.367515] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[ 3692.367517] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[ 3692.369202] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 3692.573444] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 2/3)
[ 3692.777551] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 3/3)
[ 3692.981660] wlp7s2: association with <MAC 'HiB0XW!F!' [AC7]> timed out
[ 3695.051500] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC7]>
[ 3695.067315] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 3695.068715] wlp7s2: authenticated
[ 3695.068856] rt61pci 0000:07:02.0 wlp7s2: disabling HT/VHT due to WEP/TKIP use
[ 3695.068860] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[ 3695.068863] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[ 3695.070651] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 3695.274815] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 2/3)
[ 3695.478955] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 3/3)
[ 3695.683019] wlp7s2: association with <MAC 'HiB0XW!F!' [AC7]> timed out
[ 3707.822140] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC7]>
[ 3707.837760] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 3707.839156] wlp7s2: authenticated
[ 3707.839307] rt61pci 0000:07:02.0 wlp7s2: disabling HT/VHT due to WEP/TKIP use
[ 3707.839312] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[ 3707.839315] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[ 3707.841345] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 3708.045571] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 2/3)
[ 3708.249685] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 3/3)
[ 3708.453704] wlp7s2: association with <MAC 'HiB0XW!F!' [AC7]> timed out
[ 3726.165125] IPv6: ADDRCONF(NETDEV_UP): wlp7s2: link is not ready
[ 4257.644036] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC7]>
[ 4257.660352] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 4257.661821] wlp7s2: authenticated
[ 4257.661961] rt61pci 0000:07:02.0 wlp7s2: disabling HT/VHT due to WEP/TKIP use
[ 4257.661965] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[ 4257.661968] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[ 4257.663387] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 4257.867505] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 2/3)
[ 4258.071570] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 3/3)
[ 4258.275717] wlp7s2: association with <MAC 'HiB0XW!F!' [AC7]> timed out
[ 4269.358291] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC7]>
[ 4269.373864] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 4269.418326] wlp7s2: authenticated
[ 4269.418489] rt61pci 0000:07:02.0 wlp7s2: disabling HT/VHT due to WEP/TKIP use
[ 4269.418492] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[ 4269.418493] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[ 4269.421457] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 4269.625584] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 2/3)
[ 4269.829618] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 3/3)
[ 4270.033798] wlp7s2: association with <MAC 'HiB0XW!F!' [AC7]> timed out
[ 4293.926824] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC7]>
[ 4293.942480] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 4293.979939] wlp7s2: authenticated
[ 4293.980141] rt61pci 0000:07:02.0 wlp7s2: disabling HT/VHT due to WEP/TKIP use
[ 4293.980144] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[ 4293.980146] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[ 4293.982063] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 4294.186258] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 2/3)
[ 4294.390284] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 3/3)
[ 4294.594460] wlp7s2: association with <MAC 'HiB0XW!F!' [AC7]> timed out
[ 4305.673110] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC7]>
[ 4305.688611] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 4305.693614] wlp7s2: authenticated
[ 4305.693861] rt61pci 0000:07:02.0 wlp7s2: disabling HT/VHT due to WEP/TKIP use
[ 4305.693866] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[ 4305.693869] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[ 4305.696558] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 1/3)
[ 4305.900216] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 2/3)
[ 4306.104403] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC7]> (try 3/3)
[ 4306.308512] wlp7s2: association with <MAC 'HiB0XW!F!' [AC7]> timed out
[ 4323.123285] IPv6: ADDRCONF(NETDEV_UP): wlp7s2: link is not ready

########## wireless info END ############

```

---

### Post by praseodym on 2016-02-27
Try deactivating IPv6 in the network-manager settings.

---

### Post by safire on 2016-02-27
I have tried. No luck.
By the way, I've restored 12.10 on another system, that didn't connect under 14.04. Now it works fine out of the box.
Here is the wireless-info output with IPv6 ignored:
```


########## wireless info START ##########

Report from: 28 Feb 2016 02:13 MSK +0300

Booted last: 28 Feb 2016 00:00 MSK +0300

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily

##### kernel ############################

Linux 4.2.0-30-generic #36-Ubuntu SMP Fri Feb 26 00:58:07 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
	Kernel driver in use: r8169

07:02.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
	Subsystem: ASUSTeK Computer Inc. Device [1043:837e]
	Kernel driver in use: rt61pci

##### lsusb #############################

Bus 002 Device 005: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 002 Device 007: ID 04f3:0103 Elan Microelectronics Corp. ActiveJet K-2024 Multimedia Keyboard
Bus 002 Device 008: ID 1b20:0501 MStar Semiconductor, Inc. 
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

rt61pci                32768  0
rt2x00pci              16384  1 rt61pci
rt2x00mmio             16384  1 rt61pci
rt2x00lib              57344  3 rt61pci,rt2x00pci,rt2x00mmio
mac80211              733184  2 rt2x00lib,rt2x00pci
cfg80211              548864  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt61pci
crc_itu_t              16384  2 rt61pci,firewire_core

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF]>  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp2s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9207757 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12002978 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4755140188 (4.7 GB)  TX bytes:13325760014 (13.3 GB)

wlp7s2    Link encap:Ethernet  HWaddr <MAC 'wlp7s2' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1314 errors:0 dropped:0 overruns:0 frame:0
          TX packets:604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:263182 (263.1 KB)  TX bytes:76559 (76.5 KB)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp7s2    IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       593     1  0 Feb27 ?        00:00:04 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (M4A785TD Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.7/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       22b384ee-2669-4210-93ce-cca1dc236c52
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/6
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   22b384ee-2669-4210-93ce-cca1dc236c52 | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.1.6/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        expiry = 1456701172
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.1.6
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 73440
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp2s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp7s2
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT2561/RT61 802.11g PCI
GENERAL.DRIVER:                         rt61pci
GENERAL.DRIVER-VERSION:                 4.2.0-30-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp7s2' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:07:02.0/net/wlp7s2
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   68345eb1-ab7c-4510-9182-2cc7562cad8f | HiB0XW!F!

SSID              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
DIR-615           <MAC 'DIR-615' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  --                no        
HWF               <MAC 'HWF' [AC1]>  Infra  10    2457 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1 WPA2         no        
Onlime64          <MAC 'Onlime64' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2              no        
MGTS_GPON_2070    <MAC 'MGTS_GPON_2070' [AC3]>  Infra  5     2432 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2              no        
Beeline_WiFi      <MAC 'Beeline_WiFi' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  --                no        
MGTS_GPON_578C    <MAC 'MGTS_GPON_578C' [AC5]>  Infra  5     2432 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2              no        
Beeline_WiFi_WPA  <MAC 'Beeline_WiFi_WPA' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2 802.1X  no        
HiB0XW!F!         <MAC 'HiB0XW!F!' [AC6]>  Infra  6     2437 MHz  54 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA1              no        

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

[[/etc/NetworkManager/system-connections/HiB0XW!F!]] (600 root)
[connection] id=HiB0XW!F! | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp7s2' [IF]> | mac-address-blacklist= | ssid=HiB0XW!F!
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/Moscow (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

wlp7s2    14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)

wlp7s2    Scan completed :
          Cell 01 - Address: <MAC 'HWF' [AC1]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"HWF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b05653230
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'DIR-615' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:off
                    ESSID:"DIR-615"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ae44cbf3f2
                    Extra: Last beacon: 23432ms ago
          Cell 03 - Address: <MAC 'MGTS_GPON_2070' [AC3]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"MGTS_GPON_2070"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ae4426a588
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Onlime64' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Onlime64"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000019ca3b0638
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'MGTS_GPON_578C' [AC5]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"MGTS_GPON_578C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ae428d9176
                    Extra: Last beacon: 24224ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'HiB0XW!F!' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"HiB0XW!F!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002496fe6e0
                    Extra: Last beacon: 88ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rt61pci]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7E76DAA1CD3464C02EEA47D
depends:        rt2x00lib,rt2x00mmio,rt2x00pci,eeprom_93cx6,crc-itu-t
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00pci]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     F2A3F87D3DBCA573A6F6E05
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512

[rt2x00mmio]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     879F1B5CBAAA72A33F68B51
depends:        rt2x00lib
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D31088D761A4CE666692F67
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512

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

[rt61pci]
nohwcrypt: N

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

[ 1910.532805] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 2/3)
[ 1910.736791] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 3/3)
[ 1910.941019] wlp7s2: association with <MAC 'HiB0XW!F!' [AC6]> timed out
[ 1913.010765] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC6]>
[ 1913.026633] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[ 1913.028028] wlp7s2: authenticated
[ 1913.028251] rt61pci 0000:07:02.0 wlp7s2: disabling HT/VHT due to WEP/TKIP use
[ 1913.028257] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[ 1913.028260] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[ 1913.030023] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[ 1913.234248] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 2/3)
[ 1913.438282] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 3/3)
[ 1913.642388] wlp7s2: association with <MAC 'HiB0XW!F!' [AC6]> timed out
[ 1925.785460] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC6]>
[ 1925.801127] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[ 1925.809447] wlp7s2: authenticated
[ 1925.809684] rt61pci 0000:07:02.0 wlp7s2: disabling HT/VHT due to WEP/TKIP use
[ 1925.809689] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[ 1925.809692] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[ 1925.812715] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[ 1926.016768] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 2/3)
[ 1926.220935] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 3/3)
[ 1926.425106] wlp7s2: association with <MAC 'HiB0XW!F!' [AC6]> timed out
[ 1935.181297] IPv6: ADDRCONF(NETDEV_UP): wlp7s2: link is not ready
[ 1936.238766] wlp7s2: authenticate with <MAC 'DIR-615' [AC2]>
[ 1936.254708] wlp7s2: send auth to <MAC 'DIR-615' [AC2]> (try 1/3)
[ 1936.256210] wlp7s2: authenticated
[ 1936.258186] wlp7s2: associate with <MAC 'DIR-615' [AC2]> (try 1/3)
[ 1936.268081] wlp7s2: RX AssocResp from <MAC 'DIR-615' [AC2]> (capab=0x421 status=0 aid=9)
[ 1936.268140] wlp7s2: associated
[ 1936.268172] IPv6: ADDRCONF(NETDEV_CHANGE): wlp7s2: link becomes ready
[ 1941.562072] wlp7s2: deauthenticating from <MAC 'DIR-615' [AC2]> by local choice (Reason: 3=DEAUTH_LEAVING)
[23039.673844] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC6]>
[23039.684832] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[23039.692320] wlp7s2: authenticated
[23039.692556] rt61pci 0000:07:02.0 wlp7s2: disabling HT/VHT due to WEP/TKIP use
[23039.692560] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[23039.692563] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[23039.695559] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[23039.899866] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 2/3)
[23040.103948] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 3/3)
[23040.308002] wlp7s2: association with <MAC 'HiB0XW!F!' [AC6]> timed out
[23047.940614] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC6]>
[23047.956302] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[23047.959410] wlp7s2: authenticated
[23047.959609] rt61pci 0000:07:02.0 wlp7s2: disabling HT/VHT due to WEP/TKIP use
[23047.959613] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[23047.959616] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[23047.959905] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[23048.164109] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 2/3)
[23048.368222] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 3/3)
[23048.572228] wlp7s2: association with <MAC 'HiB0XW!F!' [AC6]> timed out
[23050.646146] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC6]>
[23050.661976] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[23050.664706] wlp7s2: authenticated
[23050.664918] rt61pci 0000:07:02.0 wlp7s2: disabling HT/VHT due to WEP/TKIP use
[23050.664922] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[23050.664925] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[23050.665269] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[23050.869534] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 2/3)
[23051.073541] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 3/3)
[23051.277739] wlp7s2: association with <MAC 'HiB0XW!F!' [AC6]> timed out
[23067.675952] IPv6: ADDRCONF(NETDEV_UP): wlp7s2: link is not ready

########## wireless info END ############

```

---

### Post by praseodym on 2016-02-28
Which is "your" network you want to connect to?

---

### Post by safire on 2016-02-28
HiB0XW!F!

---

### Post by praseodym on 2016-02-29
Change the encryption mode in your router to WPA2-AES (CCMP), not WPA or mixed mode

---

### Post by safire on 2016-03-01
Still the same issue
```


########## wireless info START ##########

Report from: 02 Mar 2016 01:03 MSK +0300

Booted last: 02 Mar 2016 00:00 MSK +0300

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily

##### kernel ############################

Linux 4.2.0-30-generic #36-Ubuntu SMP Fri Feb 26 00:58:07 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
	Kernel driver in use: r8169

07:02.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
	Subsystem: ASUSTeK Computer Inc. Device [1043:837e]
	Kernel driver in use: rt61pci

##### lsusb #############################

Bus 002 Device 004: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 002 Device 003: ID 04f3:0103 Elan Microelectronics Corp. ActiveJet K-2024 Multimedia Keyboard
Bus 002 Device 005: ID 1b20:0501 MStar Semiconductor, Inc. 
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

rt61pci                32768  0
rt2x00pci              16384  1 rt61pci
rt2x00mmio             16384  1 rt61pci
rt2x00lib              57344  3 rt61pci,rt2x00pci,rt2x00mmio
mac80211              733184  2 rt2x00lib,rt2x00pci
cfg80211              548864  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt61pci
crc_itu_t              16384  2 rt61pci,firewire_core

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF]>  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp2s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28675 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43034712 (43.0 MB)  TX bytes:3931158 (3.9 MB)

wlp7s2    Link encap:Ethernet  HWaddr <MAC 'wlp7s2' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp7s2    IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       561     1  0 00:29 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (M4A785TD Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.7/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       22b384ee-2669-4210-93ce-cca1dc236c52
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   22b384ee-2669-4210-93ce-cca1dc236c52 | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.1.3/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        expiry = 1456956167
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.1.3
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 73440
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp2s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp7s2
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT2561/RT61 802.11g PCI
GENERAL.DRIVER:                         rt61pci
GENERAL.DRIVER-VERSION:                 4.2.0-30-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp7s2' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:07:02.0/net/wlp7s2
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   08073b95-86fb-4a8c-8364-dcf7deebbb80 | HiB0XW!F!

SSID              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
Onlime64          <MAC 'Onlime64' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2              no        
DIR-615           <MAC 'DIR-615' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  --                no        
HiB0XW!F!         <MAC 'HiB0XW!F!' [AC6]>  Infra  6     2437 MHz  54 Mbit/s  94      &#9602;&#9604;&#9606;&#9608;  WPA2              no        
MGTS_GPON_2070    <MAC 'MGTS_GPON_2070' [AC4]>  Infra  5     2432 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2              no        
MGTS_GPON_578C    <MAC 'MGTS_GPON_578C' [AC3]>  Infra  5     2432 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2              no        
HWF               <MAC 'HWF' [AC5]>  Infra  10    2457 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2         no        
--                <MAC '' [AC7]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  --                no        
Beeline_WiFi_WPA  <MAC 'Beeline_WiFi_WPA' [AN8]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2 802.1X  no        
Beeline_WiFi      <MAC 'Beeline_WiFi' [AN9]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  --                no        

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

[[/etc/NetworkManager/system-connections/HiB0XW!F!]] (600 root)
[connection] id=HiB0XW!F! | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp7s2' [IF]> | mac-address-blacklist= | ssid=HiB0XW!F!
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Moscow (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

wlp7s2    14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)

wlp7s2    Scan completed :
          Cell 01 - Address: <MAC 'DIR-615' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:off
                    ESSID:"DIR-615"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e9a494e075
                    Extra: Last beacon: 88ms ago
          Cell 02 - Address: <MAC 'Onlime64' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Onlime64"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000055289423d9
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'MGTS_GPON_578C' [AC3]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"MGTS_GPON_578C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e9a1057b6e
                    Extra: Last beacon: 884ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'MGTS_GPON_2070' [AC4]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"MGTS_GPON_2070"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e9a25e7715
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'HWF' [AC5]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"HWF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000adbaa0b93
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'HiB0XW!F!' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"HiB0XW!F!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000087461a4
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 07 - Address: <MAC '' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f3006ab23f
                    Extra: Last beacon: 1108ms ago

##### module infos ######################

[rt61pci]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7E76DAA1CD3464C02EEA47D
depends:        rt2x00lib,rt2x00mmio,rt2x00pci,eeprom_93cx6,crc-itu-t
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00pci]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     F2A3F87D3DBCA573A6F6E05
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512

[rt2x00mmio]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     879F1B5CBAAA72A33F68B51
depends:        rt2x00lib
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D31088D761A4CE666692F67
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512

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

[rt61pci]
nohwcrypt: N

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

[   25.468368] IPv6: ADDRCONF(NETDEV_UP): wlp7s2: link is not ready
[   25.468413] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2561s.bin'
[   25.610787] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.8
[   25.649770] IPv6: ADDRCONF(NETDEV_UP): wlp7s2: link is not ready
[   25.650971] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   25.734615] r8169 0000:02:00.0 enp2s0: link down (repeated 2 times)
[   25.734637] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   26.519715] IPv6: ADDRCONF(NETDEV_UP): wlp7s2: link is not ready
[   27.509653] r8169 0000:02:00.0 enp2s0: link up
[   27.509659] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[ 1978.112511] IPv6: ADDRCONF(NETDEV_UP): wlp7s2: link is not ready (repeated 2 times)
[ 1996.430143] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC6]>
[ 1996.446138] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[ 1996.447580] wlp7s2: authenticated
[ 1996.447737] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[ 1996.447742] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[ 1996.449590] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[ 1996.653661] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 2/3)
[ 1996.857804] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 3/3)
[ 1997.061879] wlp7s2: association with <MAC 'HiB0XW!F!' [AC6]> timed out
[ 1998.231232] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC6]>
[ 1998.246824] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[ 1998.248161] wlp7s2: authenticated
[ 1998.248295] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[ 1998.248299] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[ 1998.250560] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[ 1998.454709] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 2/3)
[ 1998.658710] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 3/3)
[ 1998.862812] wlp7s2: association with <MAC 'HiB0XW!F!' [AC6]> timed out
[ 2000.432372] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC6]>
[ 2000.448011] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[ 2000.449417] wlp7s2: authenticated
[ 2000.449570] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[ 2000.449575] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[ 2000.451609] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[ 2000.655737] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 2/3)
[ 2000.859865] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 3/3)
[ 2001.064019] wlp7s2: association with <MAC 'HiB0XW!F!' [AC6]> timed out
[ 2003.138093] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC6]>
[ 2003.153472] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[ 2003.168110] wlp7s2: authenticated
[ 2003.168295] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[ 2003.168299] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[ 2003.169062] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[ 2003.373185] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 2/3)
[ 2003.577239] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 3/3)
[ 2003.781397] wlp7s2: association with <MAC 'HiB0XW!F!' [AC6]> timed out
[ 2015.916349] wlp7s2: authenticate with <MAC 'HiB0XW!F!' [AC6]>
[ 2015.932031] wlp7s2: send auth to <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[ 2015.933562] wlp7s2: authenticated
[ 2015.933708] rt61pci 0000:07:02.0 wlp7s2: disabling HT as WMM/QoS is not supported by the AP
[ 2015.933712] rt61pci 0000:07:02.0 wlp7s2: disabling VHT as WMM/QoS is not supported by the AP
[ 2015.935635] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 1/3)
[ 2016.139778] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 2/3)
[ 2016.343879] wlp7s2: associate with <MAC 'HiB0XW!F!' [AC6]> (try 3/3)
[ 2016.547985] wlp7s2: association with <MAC 'HiB0XW!F!' [AC6]> timed out
[ 2024.016467] IPv6: ADDRCONF(NETDEV_UP): wlp7s2: link is not ready

########## wireless info END ############

```

---

### Post by safire on 2016-03-01
Also i've tried to remove ! symbols from AP name and it didn't help as well.

---

