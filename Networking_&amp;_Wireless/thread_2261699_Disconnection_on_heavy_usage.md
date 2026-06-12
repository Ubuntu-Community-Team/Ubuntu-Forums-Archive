---
title: "Disconnection on heavy usage"
date: 2015-01-20
forum: Networking &amp; Wireless
---

### Post by Sam_Nicholson on 2015-01-20
Freshly installed Ubuntu 14.04.1 LTS today. I have to use wireless so I used ndswrapper to load my wireless card driver (Netgear A6200).

Now, I can browse around websites ok, but if I try and install an app from the software center or watch netflix I instantly loose connection. My wifi icon doesn't change but I can't do anything until I re-insert my wi-fi adapter. I've also found that after maybe 1 hour it will just disconnect...

I ran the wireless script that I found on this site when my internet was working fine, I then loaded a netflix movie (internet instantly went down) and ran the script again.

**Working Internet Wireless Script**

```



########## wireless info START ##########


Report from: 20 Jan 2015 20:46 GMT +0000


Booted last: 20 Jan 2015 20:35 GMT +0000


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
	Kernel driver in use: atl1c


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 1038:1384 Ideazon, Inc. 
Bus 001 Device 004: ID 0665:6000 Cypress Semiconductor 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0846:9050 NetGear, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


cfg80211              484040  0 
ndiswrapper           283985  0 


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
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::22e5:2aff:fe29:c1ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1855 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1227916 (1.2 MB)  TX bytes:298850 (298.8 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"VM920213-2G"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'VM920213-2G' [AC1]>   
          Bit Rate=144 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:100  Invalid misc:87605   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.25    0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [VM920213-2G] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           144 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    virginmedia3120836_2GEXT: Infra, <MAC 'virginmedia3120836_2GEXT' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    BTHub5-G72Q:     Infra, <MAC 'BTHub5-G72Q' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA2
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2 Enterprise
    VM852460-2G:     Infra, <MAC 'VM852460-2G' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    VM891553-2G:     Infra, <MAC 'VM891553-2G' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2 Enterprise
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34
    *VM920213-2G:    Infra, <MAC 'VM920213-2G' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60
    BTHub4-H6CG:     Infra, <MAC 'BTHub4-H6CG' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.25


    DNS:             192.168.0.25


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


[[/etc/NetworkManager/system-connections/VM920213-2G]] (600 root)
[connection] id=VM920213-2G | type=802-11-wireless
[802-11-wireless] ssid=VM920213-2G | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


Region: Europe/London (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'VM920213-2G' [AC1]>
                    ESSID:"VM920213-2G"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: <MAC 'BTHub5-G72Q' [AC2]>
                    ESSID:"BTHub5-G72Q"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'BTWifi-with-FON' [AC3]>
                    ESSID:"BTWifi-with-FON"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:20/100  Signal level:-83 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: <MAC 'BTWifi-X' [AC4]>
                    ESSID:"BTWifi-X"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC 'virginmedia3120836_2GEXT' [AC5]>
                    ESSID:"virginmedia3120836_2GEXT"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'VM852460-2G' [AC6]>
                    ESSID:"VM852460-2G"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'VM891553-2G' [AC7]>
                    ESSID:"VM891553-2G"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E786D076B61F97809B04B64
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ndiswrapper]
filename:       /lib/modules/3.13.0-32-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]


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


[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v0846p9050d*dc*dsc*dp*ic*isc*ip* ndiswrapper


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1083 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  132.380868] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008931f00, 32000, 9
[  132.380871] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008939c00, 32000, 9
[  132.380873] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008941900, 32000, 9
[  132.380876] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008949600, 32000, 9
[  132.380879] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008951300, 32000, 8
[  132.380881] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008959000, 32000, 8
[  132.380884] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008960d00, 32000, 9
[  132.380887] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008968a00, 32000, 9
[  132.380890] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008970700, 32000, 9
[  132.380893] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008978400, 32000, 9
[  132.380895] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008980100, 32000, 8
[  132.380898] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008987e00, 32000, 9
[  132.380900] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000898fb00, 32000, 9
[  132.380903] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008997800, 32000, 9
[  132.380905] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000899f500, 32000, 9
[  132.380908] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900089a7200, 32000, 8
[  132.380911] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900089aef00, 32000, 9
[  132.380913] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900089b6c00, 32000, 9
[  132.380916] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900089be900, 32000, 9
[  132.380919] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900089c6600, 32000, 9
[  132.380922] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900089ce300, 32000, 8
[  132.380924] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900089d6000, 32000, 8
[  132.380927] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900089ddd00, 32000, 9
[  132.396440] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[  132.659720] wlan0: ethernet device <MAC 'wlan0' [IF]> using NDIS driver: bcmwlhigh5, version: 0x61e3d15, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9050.F.conf
[  132.660621] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  132.672738] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  153.682965] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  224.165303] ndiswrapper: device wlan0 removed
[  225.210497] ndiswrapper: driver bcmwlhigh5 (NETGEAR,Inc.,08/01/2012, 6.30.61.21) loaded
[  225.504461] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000927a000, 32000, 8
[  225.504467] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009281d00, 32000, 9
[  225.504471] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009289a00, 32000, 9
[  225.504473] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009291700, 32000, 9
[  225.504476] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009299400, 32000, 9
[  225.504479] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092a1100, 32000, 8
[  225.504481] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092a8e00, 32000, 9
[  225.504484] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092b0b00, 32000, 9
[  225.504487] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092b8800, 32000, 9
[  225.504489] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092c0500, 32000, 9
[  225.504492] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092c8200, 32000, 8
[  225.504494] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092cff00, 32000, 9
[  225.504497] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092d7c00, 32000, 9
[  225.504499] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092df900, 32000, 9
[  225.504502] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092e7600, 32000, 9
[  225.504505] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092ef300, 32000, 8
[  225.504507] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092f7000, 32000, 8
[  225.504510] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092fed00, 32000, 9
[  225.504513] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009306a00, 32000, 9
[  225.504516] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000930e700, 32000, 9
[  225.504518] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009316400, 32000, 9
[  225.504521] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000931e100, 32000, 8
[  225.504523] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009325e00, 32000, 9
[  225.504526] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000932db00, 32000, 9
[  225.504528] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009335800, 32000, 9
[  225.504531] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000933d500, 32000, 9
[  225.504534] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009345200, 32000, 8
[  225.504536] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000934cf00, 32000, 9
[  225.504539] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009354c00, 32000, 9
[  225.504542] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000935c900, 32000, 9
[  225.504544] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009364600, 32000, 9
[  225.504547] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000936c300, 32000, 8
[  225.504549] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009374000, 32000, 8
[  225.504552] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000937bd00, 32000, 9
[  225.504555] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009383a00, 32000, 9
[  225.504557] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000938b700, 32000, 9
[  225.504560] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009393400, 32000, 9
[  225.504563] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000939b100, 32000, 8
[  225.504566] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093a2e00, 32000, 9
[  225.504568] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093aab00, 32000, 9
[  225.504571] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093b2800, 32000, 9
[  225.504574] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093ba500, 32000, 9
[  225.504576] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093c2200, 32000, 8
[  225.504579] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093c9f00, 32000, 9
[  225.504582] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093d1c00, 32000, 9
[  225.504584] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093d9900, 32000, 9
[  225.504588] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093e1600, 32000, 9
[  225.504590] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093e9300, 32000, 8
[  225.504593] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093f1000, 32000, 8
[  225.504596] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093f8d00, 32000, 9
[  225.520797] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[  225.783415] wlan0: ethernet device <MAC 'wlan0' [IF]> using NDIS driver: bcmwlhigh5, version: 0x61e3d15, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9050.F.conf
[  225.784540] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  225.802774] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  246.809920] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

[B]Broken Internet Wireless Script
[/B]
```



########## wireless info START ##########


Report from: 20 Jan 2015 20:46 GMT +0000


Booted last: 20 Jan 2015 20:35 GMT +0000


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
	Kernel driver in use: atl1c


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 1038:1384 Ideazon, Inc. 
Bus 001 Device 004: ID 0665:6000 Cypress Semiconductor 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0846:9050 NetGear, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


cfg80211              484040  0 
ndiswrapper           283985  0 


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
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::22e5:2aff:fe29:c1ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17895923 (17.8 MB)  TX bytes:922468 (922.4 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"VM920213-2G"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'VM920213-2G' [AC1]>   
          Bit Rate=144 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:122  Invalid misc:101701   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.25    0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [VM920213-2G] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           144 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    virginmedia3120836_2GEXT: Infra, <MAC 'virginmedia3120836_2GEXT' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    BTHub5-G72Q:     Infra, <MAC 'BTHub5-G72Q' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA2
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2 Enterprise
    VM852460-2G:     Infra, <MAC 'VM852460-2G' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    VM891553-2G:     Infra, <MAC 'VM891553-2G' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34
    *VM920213-2G:    Infra, <MAC 'VM920213-2G' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60
    BTHub4-H6CG:     Infra, <MAC 'BTHub4-H6CG' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.25


    DNS:             192.168.0.25


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


[[/etc/NetworkManager/system-connections/VM920213-2G]] (600 root)
[connection] id=VM920213-2G | type=802-11-wireless
[802-11-wireless] ssid=VM920213-2G | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


Region: Europe/London (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


Channel occupancy:


      3   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'VM920213-2G' [AC1]>
                    ESSID:"VM920213-2G"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: <MAC 'BTHub5-G72Q' [AC2]>
                    ESSID:"BTHub5-G72Q"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'BTWifi-with-FON' [AC3]>
                    ESSID:"BTWifi-with-FON"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: <MAC 'BTWifi-X' [AC4]>
                    ESSID:"BTWifi-X"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC 'virginmedia3120836_2GEXT' [AC5]>
                    ESSID:"virginmedia3120836_2GEXT"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'VM852460-2G' [AC6]>
                    ESSID:"VM852460-2G"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:20/100  Signal level:-83 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'VM891553-2G' [AC7]>
                    ESSID:"VM891553-2G"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'BTHub4-H6CG' [AC8]>
                    ESSID:"BTHub4-H6CG"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'BTWifi-with-FON' [AC9]>
                    ESSID:"BTWifi-with-FON"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


##### module infos ######################


[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E786D076B61F97809B04B64
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ndiswrapper]
filename:       /lib/modules/3.13.0-32-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]


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


[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v0846p9050d*dc*dsc*dp*ic*isc*ip* ndiswrapper


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1083 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  132.380868] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008931f00, 32000, 9
[  132.380871] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008939c00, 32000, 9
[  132.380873] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008941900, 32000, 9
[  132.380876] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008949600, 32000, 9
[  132.380879] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008951300, 32000, 8
[  132.380881] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008959000, 32000, 8
[  132.380884] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008960d00, 32000, 9
[  132.380887] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008968a00, 32000, 9
[  132.380890] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008970700, 32000, 9
[  132.380893] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008978400, 32000, 9
[  132.380895] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008980100, 32000, 8
[  132.380898] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008987e00, 32000, 9
[  132.380900] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000898fb00, 32000, 9
[  132.380903] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90008997800, 32000, 9
[  132.380905] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000899f500, 32000, 9
[  132.380908] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900089a7200, 32000, 8
[  132.380911] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900089aef00, 32000, 9
[  132.380913] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900089b6c00, 32000, 9
[  132.380916] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900089be900, 32000, 9
[  132.380919] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900089c6600, 32000, 9
[  132.380922] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900089ce300, 32000, 8
[  132.380924] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900089d6000, 32000, 8
[  132.380927] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900089ddd00, 32000, 9
[  132.396440] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[  132.659720] wlan0: ethernet device <MAC 'wlan0' [IF]> using NDIS driver: bcmwlhigh5, version: 0x61e3d15, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9050.F.conf
[  132.660621] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  132.672738] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  153.682965] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  224.165303] ndiswrapper: device wlan0 removed
[  225.210497] ndiswrapper: driver bcmwlhigh5 (NETGEAR,Inc.,08/01/2012, 6.30.61.21) loaded
[  225.504461] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000927a000, 32000, 8
[  225.504467] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009281d00, 32000, 9
[  225.504471] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009289a00, 32000, 9
[  225.504473] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009291700, 32000, 9
[  225.504476] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009299400, 32000, 9
[  225.504479] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092a1100, 32000, 8
[  225.504481] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092a8e00, 32000, 9
[  225.504484] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092b0b00, 32000, 9
[  225.504487] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092b8800, 32000, 9
[  225.504489] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092c0500, 32000, 9
[  225.504492] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092c8200, 32000, 8
[  225.504494] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092cff00, 32000, 9
[  225.504497] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092d7c00, 32000, 9
[  225.504499] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092df900, 32000, 9
[  225.504502] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092e7600, 32000, 9
[  225.504505] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092ef300, 32000, 8
[  225.504507] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092f7000, 32000, 8
[  225.504510] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900092fed00, 32000, 9
[  225.504513] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009306a00, 32000, 9
[  225.504516] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000930e700, 32000, 9
[  225.504518] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009316400, 32000, 9
[  225.504521] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000931e100, 32000, 8
[  225.504523] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009325e00, 32000, 9
[  225.504526] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000932db00, 32000, 9
[  225.504528] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009335800, 32000, 9
[  225.504531] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000933d500, 32000, 9
[  225.504534] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009345200, 32000, 8
[  225.504536] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000934cf00, 32000, 9
[  225.504539] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009354c00, 32000, 9
[  225.504542] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000935c900, 32000, 9
[  225.504544] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009364600, 32000, 9
[  225.504547] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000936c300, 32000, 8
[  225.504549] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009374000, 32000, 8
[  225.504552] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000937bd00, 32000, 9
[  225.504555] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009383a00, 32000, 9
[  225.504557] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000938b700, 32000, 9
[  225.504560] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90009393400, 32000, 9
[  225.504563] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000939b100, 32000, 8
[  225.504566] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093a2e00, 32000, 9
[  225.504568] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093aab00, 32000, 9
[  225.504571] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093b2800, 32000, 9
[  225.504574] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093ba500, 32000, 9
[  225.504576] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093c2200, 32000, 8
[  225.504579] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093c9f00, 32000, 9
[  225.504582] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093d1c00, 32000, 9
[  225.504584] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093d9900, 32000, 9
[  225.504588] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093e1600, 32000, 9
[  225.504590] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093e9300, 32000, 8
[  225.504593] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093f1000, 32000, 8
[  225.504596] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900093f8d00, 32000, 9
[  225.520797] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[  225.783415] wlan0: ethernet device <MAC 'wlan0' [IF]> using NDIS driver: bcmwlhigh5, version: 0x61e3d15, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9050.F.conf
[  225.784540] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  225.802774] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  246.809920] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```


Please, please, please someone help me.

---

