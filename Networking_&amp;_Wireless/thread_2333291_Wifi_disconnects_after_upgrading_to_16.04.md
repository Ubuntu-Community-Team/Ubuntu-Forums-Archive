---
title: "Wifi disconnects after upgrading to 16.04"
date: 2016-08-08
forum: Networking &amp; Wireless
---

### Post by cofkocof on 2016-08-08
A few days ago I upgraded from 14.04 to 16.04 and now my wireless network is disconnecting every few minutes. I usually need to reboot the computer in order to get it working again. Sometimes disabling the network, removing the remembered network and then reconnecting helps, but again only for a few minutes.

I ran the wireless script, here are the details:

```
########## wireless info START ##########


Report from: 06 Aug 2016 22:29 CEST +0200


Booted last: 06 Aug 2016 00:00 CEST +0200


Script from: 30 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169


05:04.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
    Subsystem: ASUSTeK Computer Inc. RT2561/RT61 802.11g PCI [1043:837e]
    Kernel driver in use: rt61pci


##### lsusb #############################


Bus 002 Device 002: ID 058f:6377 Alcor Micro Corp. AU6375 4-LUN card reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 006: ID 0f39:0671 TG3 Electronics 
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 046d:c317 Logitech, Inc. Wave Corded Keyboard
Bus 005 Device 002: ID 046d:c069 Logitech, Inc. M-U0007 [Corded Mouse M500]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


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
mac80211              737280  2 rt2x00lib,rt2x00pci
cfg80211              565248  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt61pci
crc_itu_t              16384  1 rt61pci
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau


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
          RX packets:15534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14688 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11826693 (11.8 MB)  TX bytes:2745823 (2.7 MB)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


nameserver 127.0.1.1


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT2561/RT61 802.11g PCI
GENERAL.DRIVER:                         rt61pci
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               0.8
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          50 (connecting (configuring))
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:05:04.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     MyWifi
GENERAL.CON-UUID:                       553f0b2b-5a2d-47e7-bda2-aa3de6f506e7
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/8
GENERAL.METERED:                        unknown
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   553f0b2b-5a2d-47e7-bda2-aa3de6f506e7 | MyWifi


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl_nic/rtl8168d-2.fw
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
MyWifi  <MAC 'MyWifi' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
MyWifi  <MAC 'MyWifi' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2  no        


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


[[/etc/NetworkManager/system-connections/MyWifi]] (600 root)
[connection] id=MyWifi | type=wifi | permissions=user:mitja:;
[wifi] mac-address=<MAC 'wlan0' [IF]> | mac-address-blacklist= | ssid=MyWifi
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Ljubljana (based on set time zone)


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


lo        no frequency information.


eth0      no frequency information.


wlan0     14 channels in total; available frequencies :
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


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'MyWifi' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"MyWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c43d4e180
                    Extra: Last beacon: 1364ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rt61pci]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     147116748700BC2C93D5888
depends:        rt2x00lib,rt2x00mmio,rt2x00pci,eeprom_93cx6,crc-itu-t
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00pci]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     543B84557258F153AC267F0
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[rt2x00mmio]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     ADBE279820CFD0A1081C682
depends:        rt2x00lib
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
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


rescuetime


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x0301 (rt61pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 2660.604080] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2660.767961] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2661.208058] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2661.372081] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2661.540057] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2661.700152] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2662.136156] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2662.300023] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2662.476241] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2662.636132] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2663.076170] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2663.236135] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2663.400131] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2663.564137] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2664.008129] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2664.168126] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2664.336232] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2664.496226] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2664.572668] wlan0: deauthenticated from <MAC 'MyWifi' [AN1]> (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[ 2664.820211] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2664.984295] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2665.013695] wlan0: authenticate with <MAC 'MyWifi' [AN1]>
[ 2665.025513] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 1/3)
[ 2665.228238] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 2/3)
[ 2665.436279] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 3/3)
[ 2665.640207] wlan0: authentication with <MAC 'MyWifi' [AN1]> timed out
[ 2665.832395] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2665.996286] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2667.025451] wlan0: authenticate with <MAC 'MyWifi' [AC1]>
[ 2667.184407] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2667.352425] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2667.361209] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[ 2667.564366] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 2/3)
[ 2667.768358] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 3/3)
[ 2667.972328] wlan0: authentication with <MAC 'MyWifi' [AC1]> timed out
[ 2668.180419] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2668.348397] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2668.608442] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2668.776432] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2668.948376] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2669.108469] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2670.196803] wlan0: authenticate with <MAC 'MyWifi' [AN1]>
[ 2670.368480] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2670.532466] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2670.541605] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 1/3)
[ 2670.744536] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 2/3)
[ 2670.948529] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 3/3)
[ 2671.152576] wlan0: authentication with <MAC 'MyWifi' [AN1]> timed out
[ 2671.344572] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2671.508531] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2676.704851] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2676.864867] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2681.279730] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2681.509135] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2681.673110] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2681.836988] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2682.001381] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2683.065839] wlan0: authenticate with <MAC 'MyWifi' [AC1]>
[ 2683.249175] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2683.417062] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2683.425807] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[ 2683.629096] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 2/3)
[ 2683.833170] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 3/3)
[ 2684.037179] wlan0: authentication with <MAC 'MyWifi' [AC1]> timed out
[ 2684.229164] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2684.393155] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2689.557461] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2689.721444] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2689.881457] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2690.045461] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2691.281618] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2691.441621] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2696.277749] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2696.441880] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2696.605782] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2696.777855] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2697.854282] wlan0: authenticate with <MAC 'MyWifi' [AN1]>
[ 2698.029924] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2698.201895] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2698.210431] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 1/3)
[ 2698.413864] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 2/3)
[ 2698.617886] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 3/3)
[ 2698.821902] wlan0: authentication with <MAC 'MyWifi' [AN1]> timed out
[ 2699.017916] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2699.181906] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2700.798042] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2700.962016] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2701.126003] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2701.290079] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush


########## wireless info END ############


[/QUOTE]

I noticed that the Power managment is almost always on, I have tried disabling it with sudo iwconfig wlan0 power off as soon as I connect to the network it is set back on.

[QUOTE] IEEE 802.11bg  ESSID: removed          Mode:Managed  Frequency:2.412 GHz  Access Point: removed   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:19  Invalid misc:141   Missed beacon:0
```

---

### Post by wildmanne39 on 2016-08-08
What error and tell us the exact step you were at.
Thanks

---

### Post by wildmanne39 on 2016-08-08
The kernel appears to have a bug between it and your driver, I am researching where to get the kernel upgrade from, it will take me a little while to find it and write directions to install it if there is a new one.

Also there is a bug in network manager that my be causing an issue not every one is effected by it though.

It looks like you upgraded to 16.04 instead of doing a clean install is the right? You network names should not be etho and wlan0 anymore and udev rules shows your rules for both connections and in 16.04 that file is empty now.

Did you rename your connections to keep the old way?
Thanks

---

### Post by wildmanne39 on 2016-08-08
Hello, we are going to upgrade the kernel and see if it works better and gets rid of these error.

It is suggested that you disable secure boot before installing the new kernel.
Click on the following links and download them to your computer then drag and drop them on your desktop.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-yakkety/linux-image-4.6.0-040600-generic_4.6.0-040600.201606100558_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-yakkety/linux-image-4.6.0-040600-generic_4.6.0-040600.201606100558_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-yakkety/linux-headers-4.6.0-040600-generic_4.6.0-040600.201606100558_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-yakkety/linux-headers-4.6.0-040600-generic_4.6.0-040600.201606100558_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-yakkety/linux-headers-4.6.0-040600_4.6.0-040600.201606100558_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-yakkety/linux-headers-4.6.0-040600_4.6.0-040600.201606100558_all.deb)
Then install them by coping and pasting one line at a time:
```
cd ~/Desktop
sudo dpkg -i linux*.deb
sudo update-grub
sudo reboot
```
Let us know if it connects better, there are some other settings we can change to help get a better connection but we need to get rid of those errors first.
Thanks

---

### Post by Geoffrey_Arndt on 2016-08-09
Apparently the *standard online upgrade retains the old network names* (as on my Sys76 Galago with Intel wifi (name is still wlan0).   On a new Sys76 Sable AIO Desktop preloaded with 16.04 it's (wlp4s0).

---

### Post by cofkocof on 2016-08-09
> **Wild Man said:**
> It looks like you upgraded to 16.04 instead of doing a clean install is the right? You network names should not be etho and wlan0 anymore and udev rules shows your rules for both connections and in 16.04 that file is empty now.

Did you rename your connections to keep the old way?


Yes, I did an upgrade. I did not rename any connections, so I guess it must be that the names were retained like [COLOR=#000000]Geoffrey_Arndt pointed out.

I think the computer does not support the secure boot at all. I tried the "[/COLOR][COLOR=#333333][FONT=monospace][ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" command and it told me that it uses the Legacy boot, so I guess that should be fine?[/FONT][/COLOR][COLOR=#000000]

[/COLOR]I'll be back at the computer later in the day and I'll try the suggested kernel upgrade. I'll let you know how it goes. 

Thanks for now.

---

### Post by cofkocof on 2016-08-09
EDIT: I have managed to get the login working, I have removed all the nvidia drivers and reinstalled ubuntu-desktop. I was able to login. Now I'll be able to test the wireless with the new kernel.

Now I can't even login to my account anymore. At the login screen I enter my password and the screen blinks a couple of times and I'm just show the login screen again.

This explains my problem:
[http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop)

The first scenario occurs for me
```
-rw------- 1 root root 53 Nov 29 10:19 .Xauthority
```

I have thried chowning the file but it does not seem to help. 

The .xsession-errors says:
Xlib: extension "GLX" missing on display ":0.0".
upstart: gnome-session (Unity) main process (4668) terminated with status 1

Any help would be appreciated.

---

### Post by wildmanne39 on 2016-08-09
Please post the output of:
```
lspci | grep VGA
```
do you have hybrid graphic cards?
Thanks

---

### Post by cofkocof on 2016-08-10
Like I wrote above I managed to solve the issues with the logging in by removing nvidia drivers. The network issues still remain even after the kernel update:
```


########## wireless info START ##########


Report from: 10 Aug 2016 17:28 CEST +0200


Booted last: 10 Aug 2016 00:00 CEST +0200


Script from: 30 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.6.0-040600-generic #201606100558 SMP Fri Jun 10 10:01:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
	Kernel driver in use: r8169


05:04.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
	Subsystem: ASUSTeK Computer Inc. RT2561/RT61 802.11g PCI [1043:837e]
	Kernel driver in use: rt61pci


##### lsusb #############################


Bus 002 Device 002: ID 058f:6377 Alcor Micro Corp. AU6375 4-LUN card reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 010: ID 0f39:0671 TG3 Electronics 
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 046d:c317 Logitech, Inc. Wave Corded Keyboard
Bus 007 Device 002: ID 046d:c069 Logitech, Inc. M-U0007 [Corded Mouse M500]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


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
mac80211              745472  2 rt2x00lib,rt2x00pci
cfg80211              581632  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt61pci
led_class              16384  2 rt2x00lib,input_leds
crc_itu_t              16384  1 rt61pci
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau


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
          RX packets:34112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20606 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45565860 (45.5 MB)  TX bytes:2634153 (2.6 MB)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


nameserver 127.0.1.1


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT2561/RT61 802.11g PCI
GENERAL.DRIVER:                         rt61pci
GENERAL.DRIVER-VERSION:                 4.6.0-040600-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          50 (connecting (configuring))
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:05:04.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     MyWifi
GENERAL.CON-UUID:                       c0ca35ae-5a9d-4360-a70d-a557ed130a9b
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/6
GENERAL.METERED:                        unknown
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c0ca35ae-5a9d-4360-a70d-a557ed130a9b | MyWifi


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
MyWifi  <MAC 'MyWifi' [AN1]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
MyWifi  <MAC 'MyWifi' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2       no        


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


[[/etc/NetworkManager/system-connections/MyWifi]] (600 root)
[connection] id=MyWifi | type=wifi | permissions=user:mitja:;
[wifi] mac-address=<MAC 'wlan0' [IF]> | mac-address-blacklist= | ssid=MyWifi
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Ljubljana (based on set time zone)


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


lo        no frequency information.


eth0      no frequency information.


wlan0     14 channels in total; available frequencies :
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


Channel occupancy:


      1   APs on   Frequency:2.437 GHz (Channel 6)


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'MyWifi' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"MyWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000003552180
                    Extra: Last beacon: 784ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rt61pci]
filename:       /lib/modules/4.6.0-040600-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     23B4B39F49B254EF4D15A4A
depends:        rt2x00lib,rt2x00mmio,rt2x00pci,eeprom_93cx6,crc-itu-t
intree:         Y
vermagic:       4.6.0-040600-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00pci]
filename:       /lib/modules/4.6.0-040600-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D25E084B43855FB0A6A69C9
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.6.0-040600-generic SMP mod_unload modversions 


[rt2x00mmio]
filename:       /lib/modules/4.6.0-040600-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7CB5AF83BE06CFF91038528
depends:        rt2x00lib
intree:         Y
vermagic:       4.6.0-040600-generic SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.6.0-040600-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     42B76BA472046ADFA0EEBE1
depends:        mac80211,led-class,cfg80211
intree:         Y
vermagic:       4.6.0-040600-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.6.0-040600-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0F85316D3D74DC638291862
depends:        cfg80211
intree:         Y
vermagic:       4.6.0-040600-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.6.0-040600-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     64D16DD2A026E169A36027A
depends:        
intree:         Y
vermagic:       4.6.0-040600-generic SMP mod_unload modversions 
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


rescuetime
sleep 10
iwconfig wlan0 power off
exit 0


##### pm-utils ##########################


[/etc/pm/power.d/wifi_pwr_off] (755 root)
/sbin/iwconfig wlan0 power off


[/etc/pm/power.d/wireless] (755 root)
/sbin/iwconfig wlan0 power off


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x0301 (rt61pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  278.770262] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  279.838720] wlan0: authenticate with <MAC 'MyWifi' [AC1]>
[  280.006405] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  280.174274] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  280.183610] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  280.386348] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 2/3)
[  280.590360] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 3/3)
[  280.794368] wlan0: authentication with <MAC 'MyWifi' [AC1]> timed out
[  280.990367] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  281.150342] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  289.798808] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  289.958788] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  296.442189] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[  296.623040] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
Please file bug report to http://rt2x00.serialmonkey.com
[  301.206587] wlan0: authenticate with <MAC 'MyWifi' [AC1]>
[  301.216439] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  301.419476] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 2/3)
[  301.623238] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 3/3)
[  301.827284] wlan0: authentication with <MAC 'MyWifi' [AC1]> timed out
[  303.043865] wlan0: authenticate with <MAC 'MyWifi' [AC1]>
[  303.064592] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  303.267379] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 2/3)
[  303.471370] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 3/3)
[  303.675390] wlan0: authentication with <MAC 'MyWifi' [AC1]> timed out
[  305.255832] wlan0: authenticate with <MAC 'MyWifi' [AC1]>
[  305.276167] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  305.479390] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 2/3)
[  305.683488] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 3/3)
[  305.887497] wlan0: authentication with <MAC 'MyWifi' [AC1]> timed out
[  307.996067] wlan0: authenticate with <MAC 'MyWifi' [AN1]>
[  308.016251] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 1/3)
[  308.219661] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 2/3)
[  308.423629] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 3/3)
[  308.627644] wlan0: authentication with <MAC 'MyWifi' [AN1]> timed out
[  316.792323] wlan0: authenticate with <MAC 'MyWifi' [AN1]>
[  316.813279] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 1/3)
[  317.016074] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 2/3)
[  317.220138] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 3/3)
[  317.424152] wlan0: authentication with <MAC 'MyWifi' [AN1]> timed out
[  326.127758] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  327.189002] wlan0: authenticate with <MAC 'MyWifi' [AN1]>
[  327.209799] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 1/3)
[  327.412467] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 2/3)
[  327.616466] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 3/3)
[  327.820471] wlan0: authentication with <MAC 'MyWifi' [AN1]> timed out
[  353.035769] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[  353.217738] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
Please file bug report to http://rt2x00.serialmonkey.com
[  354.299708] wlan0: authenticate with <MAC 'MyWifi' [AN1]>
[  354.310589] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 1/3)
[  354.513895] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 2/3)
[  354.717730] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 3/3)
[  354.921804] wlan0: authentication with <MAC 'MyWifi' [AN1]> timed out
[  355.074042] wlan0: authenticate with <MAC 'MyWifi' [AC1]>
[  355.086411] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  355.289874] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 2/3)
[  355.493718] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 3/3)
[  355.697731] wlan0: authentication with <MAC 'MyWifi' [AC1]> timed out
[  356.878264] wlan0: authenticate with <MAC 'MyWifi' [AN1]>
[  356.903005] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 1/3)
[  357.105875] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 2/3)
[  357.309875] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 3/3)
[  357.513919] wlan0: authentication with <MAC 'MyWifi' [AN1]> timed out
[  358.586103] wlan0: authenticate with <MAC 'MyWifi' [AC1]>
[  358.595221] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  358.797886] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 2/3)
[  359.001995] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 3/3)
[  359.205925] wlan0: authentication with <MAC 'MyWifi' [AC1]> timed out
[  361.286464] wlan0: authenticate with <MAC 'MyWifi' [AN1]>
[  361.310656] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 1/3)
[  361.513935] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 2/3)
[  361.718122] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 3/3)
[  361.921979] wlan0: authentication with <MAC 'MyWifi' [AN1]> timed out
[  371.982935] wlan0: authenticate with <MAC 'MyWifi' [AC1]>
[  371.995889] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  372.198570] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 2/3)
[  372.402588] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 3/3)
[  372.606589] wlan0: authentication with <MAC 'MyWifi' [AC1]> timed out
[  379.130075] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  380.191197] wlan0: authenticate with <MAC 'MyWifi' [AN1]>
[  380.211742] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 1/3)
[  380.414990] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 2/3)
[  380.618900] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 3/3)
[  380.822904] wlan0: authentication with <MAC 'MyWifi' [AN1]> timed out
[  390.879885] wlan0: authenticate with <MAC 'MyWifi' [AN1]>
[  390.888095] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 1/3)
[  391.091352] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 2/3)
[  391.295391] wlan0: send auth to <MAC 'MyWifi' [AN1]> (try 3/3)
[  391.499466] wlan0: authentication with <MAC 'MyWifi' [AN1]> timed out


########## wireless info END ############



```

---

### Post by wildmanne39 on 2016-08-10
The output says, that is a new bug.
> ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
Please file bug report to [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
I still see the error message but there are some settings that need changed so lets do that:
Please set all your settings in network manager to match the screenshots. IPV6 is still having issues with ubuntu so as the screenshot says set it to ignore. 

I do not see in the information that IPV4 is trying to connect at all so if you have that set to ignore change it to match the screenshot and all other setting too then reboot.

If it is still unstable we may have to work on network manager it has a bug in 16.04 but for most people it is working now.

---

### Post by cofkocof on 2016-08-11
It is still disconnecting. But not it is at least trying to reconnect, before it just disconnected and didn't even try to reconnect.
```



########## wireless info START ##########


Report from: 11 Aug 2016 18:57 CEST +0200


Booted last: 11 Aug 2016 00:00 CEST +0200


Script from: 30 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.6.0-040600-generic #201606100558 SMP Fri Jun 10 10:01:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
	Kernel driver in use: r8169


05:04.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
	Subsystem: ASUSTeK Computer Inc. RT2561/RT61 802.11g PCI [1043:837e]
	Kernel driver in use: rt61pci


##### lsusb #############################


Bus 005 Device 002: ID 058f:6377 Alcor Micro Corp. AU6375 4-LUN card reader
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 006: ID 0f39:0671 TG3 Electronics 
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 002: ID 046d:c069 Logitech, Inc. M-U0007 [Corded Mouse M500]
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 046d:c317 Logitech, Inc. Wave Corded Keyboard
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


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
mac80211              745472  2 rt2x00lib,rt2x00pci
cfg80211              581632  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt61pci
led_class              16384  2 rt2x00lib,input_leds
crc_itu_t              16384  1 rt61pci
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau


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
          RX packets:34091 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19085 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41713475 (41.7 MB)  TX bytes:2052876 (2.0 MB)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


nameserver 127.0.1.1


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT2561/RT61 802.11g PCI
GENERAL.DRIVER:                         rt61pci
GENERAL.DRIVER-VERSION:                 4.6.0-040600-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          50 (connecting (configuring))
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:05:04.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     MyWifi
GENERAL.CON-UUID:                       58a7300b-a4ed-4f83-a677-c37bf26e1f41
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        unknown
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   58a7300b-a4ed-4f83-a677-c37bf26e1f41 | MyWifi


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
MyWifi  <MAC 'MyWifi' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  94      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
MyWifi  <MAC 'MyWifi' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2       no        
MyWifi  <MAC 'MyWifi' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  no        
Jamsek        <MAC 'Jamsek' [AN4]>  Infra  3     2422 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2  no        
Tenda         <MAC 'Tenda' [AN5]>  Infra  6     2437 MHz  54 Mbit/s  34      &#9602;&#9604;__  --         no        


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


[[/etc/NetworkManager/system-connections/MyWifi]] (600 root)
[connection] id=MyWifi | type=wifi | permissions=user:mitja:;
[wifi] mac-address=<MAC 'wlan0' [IF]> | mac-address-blacklist= | ssid=MyWifi
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: Europe/Ljubljana (based on set time zone)


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


lo        no frequency information.


eth0      no frequency information.


wlan0     14 channels in total; available frequencies :
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


Channel occupancy:


      2   APs on   Frequency:2.437 GHz (Channel 6)


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'MyWifi' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"MyWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000033110c180
                    Extra: Last beacon: 1176ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'MyWifi' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"MyWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001d8b3ee34
                    Extra: Last beacon: 788ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rt61pci]
filename:       /lib/modules/4.6.0-040600-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     23B4B39F49B254EF4D15A4A
depends:        rt2x00lib,rt2x00mmio,rt2x00pci,eeprom_93cx6,crc-itu-t
intree:         Y
vermagic:       4.6.0-040600-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00pci]
filename:       /lib/modules/4.6.0-040600-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D25E084B43855FB0A6A69C9
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.6.0-040600-generic SMP mod_unload modversions 


[rt2x00mmio]
filename:       /lib/modules/4.6.0-040600-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7CB5AF83BE06CFF91038528
depends:        rt2x00lib
intree:         Y
vermagic:       4.6.0-040600-generic SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.6.0-040600-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     42B76BA472046ADFA0EEBE1
depends:        mac80211,led-class,cfg80211
intree:         Y
vermagic:       4.6.0-040600-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.6.0-040600-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0F85316D3D74DC638291862
depends:        cfg80211
intree:         Y
vermagic:       4.6.0-040600-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.6.0-040600-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     64D16DD2A026E169A36027A
depends:        
intree:         Y
vermagic:       4.6.0-040600-generic SMP mod_unload modversions 
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


rescuetime
sleep 10
iwconfig wlan0 power off
exit 0


##### pm-utils ##########################


[/etc/pm/power.d/wifi_pwr_off] (755 root)
/sbin/iwconfig wlan0 power off


[/etc/pm/power.d/wireless] (755 root)
/sbin/iwconfig wlan0 power off


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x0301 (rt61pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  149.130666] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  149.290668] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  149.462716] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  149.902791] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  150.066760] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  150.242696] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  150.406650] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  150.487487] wlan0: deauthenticated from <MAC 'MyWifi' [AC1]> (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[  150.714661] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  150.882849] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  150.899024] wlan0: authenticate with <MAC 'MyWifi' [AC1]>
[  150.907994] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  151.110814] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 2/3)
[  151.314946] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 3/3)
[  151.522880] wlan0: authentication with <MAC 'MyWifi' [AC1]> timed out
[  151.714714] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  151.874820] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  152.903221] wlan0: authenticate with <MAC 'MyWifi' [AC2]>
[  153.074826] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  153.251033] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  153.259384] wlan0: send auth to <MAC 'MyWifi' [AC2]> (try 1/3)
[  153.462869] wlan0: send auth to <MAC 'MyWifi' [AC2]> (try 2/3)
[  153.666879] wlan0: send auth to <MAC 'MyWifi' [AC2]> (try 3/3)
[  153.870835] wlan0: authentication with <MAC 'MyWifi' [AC2]> timed out
[  154.062949] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  154.222930] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  154.486888] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  154.651003] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  154.811026] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  154.971030] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  156.027418] wlan0: authenticate with <MAC 'MyWifi' [AC1]>
[  156.203098] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  156.375001] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  156.383566] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  156.590981] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 2/3)
[  156.795038] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 3/3)
[  156.998890] wlan0: authentication with <MAC 'MyWifi' [AC1]> timed out
[  157.190977] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  157.359185] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  162.559109] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  162.723266] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  167.093486] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  167.371387] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  167.539441] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  167.699203] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  167.859461] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  169.087346] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  169.247250] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  170.043367] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  170.207330] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  170.367335] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  170.535382] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  171.588020] wlan0: authenticate with <MAC 'MyWifi' [AC1]>
[  171.759350] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  171.923350] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  171.932043] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  171.932114] wlan0: authenticated
[  171.935315] wlan0: associate with <MAC 'MyWifi' [AC1]> (try 1/3)
[  172.139503] wlan0: associate with <MAC 'MyWifi' [AC1]> (try 2/3)
[  172.343426] wlan0: associate with <MAC 'MyWifi' [AC1]> (try 3/3)
[  172.547540] wlan0: association with <MAC 'MyWifi' [AC1]> timed out
[  172.751336] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  172.923490] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  182.956100] wlan0: authenticate with <MAC 'MyWifi' [AC2]>
[  183.115574] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  183.283666] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  183.292380] wlan0: send auth to <MAC 'MyWifi' [AC2]> (try 1/3)
[  183.495681] wlan0: send auth to <MAC 'MyWifi' [AC2]> (try 2/3)
[  183.699740] wlan0: send auth to <MAC 'MyWifi' [AC2]> (try 3/3)
[  183.903661] wlan0: authentication with <MAC 'MyWifi' [AC2]> timed out
[  184.103715] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  184.271706] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  193.267847] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  193.431803] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  193.595738] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  193.755854] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  194.820325] wlan0: authenticate with <MAC 'MyWifi' [AC1]>
[  194.987875] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  195.151817] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  195.160647] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  195.363923] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 2/3)
[  195.567829] wlan0: send auth to <MAC 'MyWifi' [AC1]> (try 3/3)
[  195.771830] wlan0: authentication with <MAC 'MyWifi' [AC1]> timed out
[  195.963875] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  196.123893] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  206.160360] wlan0: authenticate with <MAC 'MyWifi' [AC2]>
[  206.319958] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  206.483982] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  206.496602] wlan0: send auth to <MAC 'MyWifi' [AC2]> (try 1/3)
[  206.497225] wlan0: authenticated
[  206.500090] wlan0: associate with <MAC 'MyWifi' [AC2]> (try 1/3)
[  206.703962] wlan0: associate with <MAC 'MyWifi' [AC2]> (try 2/3)
[  206.908129] wlan0: associate with <MAC 'MyWifi' [AC2]> (try 3/3)
[  207.111991] wlan0: association with <MAC 'MyWifi' [AC2]> timed out
[  207.316127] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  207.487984] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  207.967983] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  208.135970] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  208.296075] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  208.459980] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush


########## wireless info END ############



```

---

### Post by ubuser4 on 2016-09-03
I had a problem similar to yours except I didn't experience disconnections and the "queue X failed to flush" messages sometimes started appearing right after the Wifi connection was established. According to lspci, my card is Ralink corp. RT3290. The connection was okay and the messages didn't appear in 16.04. **The problem started when I upgraded to 16.04.1**, so I think there may be a bug somewhere in the point release.


**I found two possible solutions:**

**1.** Enter the MAC address of the router to the BSSID field on your network settings screen and add irqpoll to the boot options, as suggested by Codemonkey on Ask Ubuntu: [http://askubuntu.com/a/813965](http://askubuntu.com/a/813965). **NOTE:** To my knowledge, there is no way to undo this change.

**2.** Turn off Wifi power management. As it has been mentioned several times, the temporary way to do this is to type "sudo iwconfig wlan0 power off" (replace wlan0 with wlo1 in my case) without quotes in terminal. Apparently, there are many permanent ways. Some seem to work for some and others for others.

This one worked for me (based on coolder's post on Raspberry Pi forums; it's the 15th post in this thread: [https://www.raspberrypi.org/forums/viewtopic.php?t=46569&p=647343](https://www.raspberrypi.org/forums/viewtopic.php?t=46569&p=647343) ):
I opened a terminal and entered
```
sudo gedit /etc/network/if-up.d/off-power-manager
```
added the following lines to the blank document that opened:
```
#!/bin/sh
/sbin/iwconfig wlan0 power off
/sbin/iwconfig wlo1 power off
```
saved the file, exited the editor and entered this in the terminal:
```
sudo chmod +x /etc/network/if-up.d/off-power-manager
```
After that, I rebooted and checked the power management status of the Wifi by issuing iwconfig in the terminal. (It was off, just like it should be.)


Both of these solved my problem (I tested different solutions on different user accounts). However, I don't know the long-term effects of either solution, because I took **the third option**: downgraded back to 16.04 (by following the instructions here: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)) for now.


**I noticed that by default the power management is on in 16.04.1 and off in 16.04.** I turned it on in 16.04 to see what would happen (sudo iwconfig wlo1 power on), and the connection speed dropped and "queue X failed to flush" messages started appearing. They didn't stop until I turned the power management off (sudo iwconfig wlo1 power off). After that, the connection went back to normal.

---

### Post by Bill_in_the_UK on 2016-09-30
After upgrading to 16.04 from 14.04 I was having problems with wifi randomly disconnecting and not resuming after suspend.  Various sources on the internet recommended turning wifi power management off but none of the various ways suggested had any effect - every time I rebooted wifi power management was still turned on - checked by running lwconfig.  Nothing worked.  I then found a file that specifically set the wifi power management state:

sudo gedit /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

The above file had two lines:

[connection]
wifi.powersave = 3

I changed the 3 to 0:

[connection]
wifi.powersave = 0

After rebooting wifi power management is off by default, the random disconnects have stopped and wifi resumes after suspend.

Hopefully someone else will find this useful.

---

### Post by jayadm on 2016-10-13
Thanks for this post guys. After a few hours of frustration, following a process of elimination, I arrived at this post. I had recently upgraded my 14.04.5 LTS install to 16.04.1 .
My Desktop's wireless card , an 'N" class Ralink RT3062 still drops 30% of it's TX packets but it's approaching 4 years old now and possibly about to croak, so it's given me a good excuse to order an Intel based 'ac' replacement. In the mean time, no dropouts so far :)

---

### Post by bobsmith5002@gmail.com on 2016-11-01
Bill_in_the_UK

- thank you so much for documenting this issue
- i have been working to resolve this for days now
- your recommendation for changing the power management has fixed this
- it was pushing me right to the edge
- 'thank you' is not enough

---

### Post by jeremy31 on 2016-11-01
While changing ```
wifi.powersave = 0

```
Has worked for some people, I found the better option is to change it to 
```
wifi.powersave = 2
```
After seeing some source code for network manager

---

### Post by ubuser4 on 2017-03-09
> **jeremy31 said:**
> While changing ```
wifi.powersave = 0

```
Has worked for some people, I found the better option is to change it to 
```
wifi.powersave = 2
```
After seeing some source code for network manager

Is this because 0 is for using global/default value and 2 is for disabling power save entirely (at least according to [https://github.com/igorpecovnik/lib/issues/505#issuecomment-269632904;](https://github.com/igorpecovnik/lib/issues/505#issuecomment-269632904;) I haven't seen the source code)?

---

### Post by jeremy31 on 2017-03-10
If you need to have power save enabled for some connections, you can use 0 for global and then edit your connections in /etc/NetworkManager/system-connections and add powersave=0 under the [wifi] section to disable powermanagent or use powersave=1 to enable

---

